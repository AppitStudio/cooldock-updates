# CoolDock Updates

Sparkle update feed and release distribution for [CoolDock](https://www.dock.cool) by AppIt Studio.

- **Appcast:** https://appitstudio.github.io/cooldock-updates/appcast.xml
- **Release notes:** https://appitstudio.github.io/cooldock-updates/release-notes.html
- **Downloads:** hosted on this repo's GitHub Releases. Stable builds are tagged `v{version}`;
  betas are pre-releases also tagged `v{version}` (e.g. `v2.0.0-beta.1`).

Beta builds are delivered through the same appcast using Sparkle 2 channels
(`<sparkle:channel>beta</sparkle:channel>`); users opt in via the app's update-channel setting.
Stable users ignore channel-tagged items.

GitHub Pages for this repository must serve the `main` branch root (`/`) — that is where
`appcast.xml` and `release-notes.html` are published from.

## Append-only release history

`appcast.xml` is append-only: add each new `<item>` above the existing items (newest first) and
never remove an older release — including beta items once the matching stable ships.
Update-window licensing compares each item's `pubDate` with the customer's server-issued update
expiry, so every item must carry the real release timestamp. Never guess or backdate a release.

Every item must use an immutable, version-specific download asset
(`releases/download/v{version}/CoolDock.dmg`), never a reused tag.

Before committing a feed change, run:

```bash
python3 scripts/sync_keyper_releases.py --appcast appcast.xml --validate-only
xmllint --noout appcast.xml
```

## Keyper release registration

The GitHub Actions workflow validates pull requests. After `appcast.xml` changes on `main`, it
idempotently posts every retained version and `pubDate` to Keyper's `/api/releases` endpoint.
It can also be run manually (`workflow_dispatch`). While the appcast has no `<item>` yet, the
workflow skips validation and registration.

Repository configuration required before the first registration:

- Secret `KEYPER_RELEASE_TOKEN`: the dedicated Keyper write token bound to CoolDock's `stable`
  release track. Never use the API key shipped inside the app.
- Optional variable `KEYPER_RELEASE_ENDPOINT`: override for the complete HTTPS endpoint.
  It defaults to `https://keyper.appitstudio.com/api/releases`.

The workflow has read-only repository permissions and never prints the token.
