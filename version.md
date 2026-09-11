VERSION: 2.0.6
DETAILS:

new: Smart App Menus - Right-click any app - pinned, running, inside a folder or in the Applications gallery - and get actions it actually supports: New Message for any mail client that handles mailto (it composes in that app, not your default client), New Document in TextEdit and Pages, New Spreadsheet in Numbers and New Presentation in Keynote
new: Open Recent, Per App - Document apps gain an Open Recent submenu built from macOS's own recent-file lists - up to eight files, identical names told apart by their folder, missing files filtered out. Reads happen off the main thread when the menu opens and are cached for 30 seconds
new: Connect Apple Music And Spotify - Now Playing widgets get optional Connect controls for Apple Music and Spotify in Settings → Privacy, plus Configure Player Access… in their context menu - for when system Now Playing can't provide the details
improved: Counts And Previews Load Separately - A failed Mail preview no longer wipes your unread count - you'll see "Preview unavailable" instead of a false "No unread mail", and partial counts are marked as partial
improved: One Mail Refresh Pipeline - Automatic, manual and settings-driven refreshes are coalesced, so a stale or abandoned attempt can no longer hide a working widget or throttle it for 90 seconds
improved: Bounded Mail Scripting - Previews fetch at most 50 indexed messages with per-step timeouts, account and mailbox counts survive one bad mailbox with partial results, and a transient failure retries once behind a fresh Automation check
improved: Safer Direct-Store Reads - Mail's database is read through a normal read-only transaction instead of copying live files, read errors fall back to Automation, and the "today" count uses Mail's real timestamps
improved: Mail In Diagnostics - Export Diagnostics now includes a Mail section with backend, access state, failure phase and timing - never message content, mailbox names or accounts
improved: Privacy Pane Feedback - Automation actions show progress while a request is in flight, ignore repeat clicks, and route a denial straight to Automation settings
improved: Steadier Notification Badges - Badge reads are coalesced and bounded, temporary failures keep the last good count instead of clearing it, and an older scan can no longer overwrite newer counts
improved: Weather Location Recovery - Weather discards stale permission checks, retries through its recovery path on polling, and the help text now distinguishes the system-wide Location Services switch from CoolDock's own permission
improved: App Folder Gallery - The first page fills every complete row of the viewport instead of a fixed count
improved: Diagnostics Tell More - Exports now include badge scan health, running-monitor health, per-launcher running/badge flags and configuration-aware Weather state - still with no app names, bundle IDs or values
bug fix: Connect Really Asks macOS - The Finder, Mail, Notes and browser Connect buttons could report success without ever showing a permission prompt. They now request Automation access the proper way, so the macOS consent dialog appears and the grant sticks
bug fix: Stopped Apps Launch First - Connect opens the target app if it isn't running, shares one request when you click repeatedly, honours cancellation, and never fabricates a grant when the app fails to start. Passive reads still never prompt or launch anything
bug fix: Dock Survives Hide Others And Cmd+H - Opt+Cmd-clicking the desktop (Finder's Hide Others) or pressing Cmd+H no longer makes the dock vanish - the dock, its expansion panel and tooltips stay on screen and clickable
bug fix: Running Dots Reconcile - The regular app poll now reconciles the running-app monitor against macOS, so a missed launch or quit event no longer leaves a stale dot
