VERSION: 2.0.4
DETAILS:

new: More AI Usage Widgets - Cursor Personal, Antigravity, GLM / Z.ai, Grok, OpenCode, GitHub Copilot, Gemini API and Perplexity join the AI usage family - each with its own connection path and honest readings, never an invented quota
new: Smarter Claude Usage - CoolDock now prefers Claude Code's own /usage command and falls back to OAuth, so token and rate-limit states are clearer and there are fewer dead ends
new: Codex Open Finds ChatGPT - Open resolves the unified Codex/ChatGPT app first, then legacy installs, then the web - so a click always lands somewhere useful
new: Click To Refresh - Usage widgets answer a click with real feedback - refreshing, cooling down or connect - instead of doing nothing
improved: Spaces Stay Put - CoolDock checks real Space membership before reshuffling panels, so the dock is far less likely to vanish when you switch desktops or leave Mission Control or fullscreen
improved: Sidecar-Friendly - Fullscreen on one display (an iPad Sidecar, say) no longer hides CoolDock on every display - only on the display that is actually fullscreen
improved: Tighter Top-Edge Reveal - The reveal zone follows the dock's content width, so hovering menus and status items outside the bar won't pop the dock open by accident
improved: All Displays Replicas Recover - If macOS recycles a display's runtime ID, CoolDock recreates that screen's dock copy instead of leaving a ghost
improved: Permissions That Tell The Truth - Widgets seed their real authorization state at launch without prompting, so no more false denied flashes when access was already granted
improved: Calendar And Mail - Mail gating uses the real data-access state, unread scans tolerate damaged messages, and permission warnings deep-link into Settings → Privacy and highlight the right card
improved: Folders And Dock Replace - Folder reorder and remove persist cleanly, and the dock-replace plus auto-hide setups work like before again
bug fix: Add / Move Widgets - Drag-and-drop onto the dock works again, with proper drop targets on tile edges, gaps and bar ends; running-app clusters can no longer steal the insertion, and Escape clears the session
bug fix: Claude Keychain Spam - Background polls no longer spawn a security subprocess, which ends the repeated Keychain prompts after a token rotation
bug fix: Claude Rate Limit / Token Invalid - 401 and 403 are handled separately, rejected tokens are skipped, and rate-limit deadlines survive a relaunch without being hammered by clicks
bug fix: Keychain Unlock Recovery - A locked or unreadable Keychain is treated as locked, and recovery stays available from Claude setup or the Privacy storage modes (file storage path preserved)
bug fix: Claude Code Hooks Check Node - Before writing a Node path into the Claude Code hooks, CoolDock verifies that Node actually launches and falls back to the one your login shell finds - a broken Homebrew Node no longer silently breaks every hook
bug fix: Codex Widget Click - Open and refresh paths are fixed, and unavailable or not-found states show clear feedback instead of silence
bug fix: Running Indicator - Quitting an app from CoolDock (WhatsApp, say) clears the running dot, and a relaunch shows a correct indicator again
