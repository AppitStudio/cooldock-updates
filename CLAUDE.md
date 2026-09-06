# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This repository manages the Sparkle auto-update feed for **CoolDock** (https://www.dock.cool), the AppIt Studio macOS dock app (bundle id `com.appit.CoolDock` (Cooldock 1.9.x shipped as `app.Supadock`; 2.0 is a clean cut, no Sparkle path from 1.9.x), app repo `AppitStudio/cooldock`). It has its own appcast, its own EdDSA key (keychain account `CoolDock`), and its own GitHub releases — nothing is shared with the other AppIt feeds.

## Architecture

- **`appcast.xml`** — Production Sparkle feed, served at `https://appitstudio.github.io/cooldock-updates/appcast.xml` (this is the `SUFeedURL` baked into the app).
  - **Append-only history:** newest `<item>` first; never remove or rewrite an older item (beta items included). Update-window licensing compares each item's real `pubDate` with the customer's update expiry, so every item must carry its true release timestamp — never guess or backdate.
  - Stable items carry no channel tag; **beta items carry `<sparkle:channel>beta</sparkle:channel>`** (immediately after `<title>`) — the app is Sparkle 2 and gates betas via `allowedChannels` (user's "Beta" setting), NOT via a separate feed URL.
  - Critical fields per item: `sparkle:version` (the integer build counter from `CURRENT_PROJECT_VERSION` — monotonic, NOT dots-removed; read the current value from the pbxproj, never assume it), `sparkle:shortVersionString` (display version from `MARKETING_VERSION`; betas are `{next}-beta.{n}`, e.g. `2.1.0-beta.1`), `sparkle:minimumSystemVersion` (`14.0`), `pubDate` (RFC 2822 with timezone), `enclosure url` (immutable GitHub release DMG `releases/download/v{version}/CoolDock.dmg`), `sparkle:edSignature`.
  - The feed starts with no items; the first release adds one.
- **`release-notes.html`** — Styled notes page linked via `sparkle:fullReleaseNotesLink`. New `<div data-sparkle-version="X.Y.Z">` blocks go at the top of `<body>`.
- **`version.md`** — Human-readable summary of the latest published version.
- **`dmg/`** — Local staging folder for `generate_appcast` (DMG + generated appcast are gitignored; only root `appcast.xml` is the published feed).
- **`scripts/sync_keyper_releases.py`** + **`.github/workflows/register-keyper-releases.yml`** — validate the retained history (ordering, uniqueness, signatures, timestamps) and register every retained release with Keyper after an `appcast.xml` push to `main`. Requires the `KEYPER_RELEASE_TOKEN` secret (bound to CoolDock's `stable` track); the workflow is a no-op while the feed has no items.

## Publishing

Signing: `generate_appcast --account CoolDock dmg/` (the EdDSA key lives in the keychain under account `CoolDock`; its public key must match `SUPublicEDKey` in the app's Info.plist). Never sign CoolDock with another app's key.

DMG hosting: GitHub Releases on this repo. Stable: tag `v{version}`. Beta: tag `v{version}` (e.g. `v2.0.0-beta.1`) marked pre-release — versioned tags, never a reused `beta` tag, because appcast beta items must have stable URLs.

Before committing a feed change:

```bash
python3 scripts/sync_keyper_releases.py --appcast appcast.xml --validate-only
xmllint --noout appcast.xml
```

The full pipeline is driven by the `/full-publish` skill and `publish.sh` in `/Users/asafmazuz/Documents/MacApps/updates` (app key: `cooldock`, publish name `CoolDock`). The version lives in the Xcode project (`MARKETING_VERSION` / `CURRENT_PROJECT_VERSION` in `CoolDock.xcodeproj`); minimum system version is macOS 14.0.

GitHub Pages must serve the `main` branch root.
