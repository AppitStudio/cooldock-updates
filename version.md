VERSION: 2.0.3
DETAILS:

new: "Fixed" layout with a six-position Screen Position grid (top or bottom edge, left/center/right)
new: Custom place on every weather widget (Customize Location… → Custom Place), no location permission needed
new: Option to leave a window where you dragged it into the dock band instead of pushing it back out
new: Settings → Screens pane with One Display, Attached Displays and All Displays placement modes
new: Remembered displays with rename/forget, and Identify Displays
improved: Reserve Dock Space reacts to window events instead of scanning every two seconds, never fights the mouse, restores frames when switching back to Overlay, and gives up on stubborn windows
improved: Displays are recognized by hardware identity, so the dock no longer hops on wake, replug or between identical monitors; floating position remembered per display
improved: Claude Code widget reads sign-in like Claude Code itself (no keychain prompts), freshest sign-in wins, session bar stays at rollover, rate limits respected
improved: Codex widget shows Codex's own usage windows and percentages, falls back to the last snapshot, notes paused accounts
improved: Both usage widgets keep their last reading offline instead of "Loading…"
improved: Weather widgets offer help when macOS can't determine a location, retry requests, and stop duplicating network calls
bug fix: Restoring a minimized window from the CoolDock bar no longer shrinks or shifts it
