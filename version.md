VERSION: 2.0.1
DETAILS:

bug fix: A login keychain that cannot be unlocked (forgotten keychain password after a macOS password reset) no longer cuts CoolDock off from your license
bug fix: Secrets are read without provoking the keychain unlock dialog, so a locked keychain degrades instead of blocking the app
bug fix: The one-time import of secrets left behind by Cooldock 1.9.x is offered once, never for a locked keychain, and reports success only when nothing was left behind
new: Settings > Privacy lets you keep secrets in the macOS Keychain (default) or, if the keychain cannot be unlocked, in an encrypted file on this Mac
