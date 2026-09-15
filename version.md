VERSION: 2.0.7
DETAILS:

new: Custom Media Players And Cider - Now Playing widgets follow any app that publishes to macOS Now Playing (Cider, Pandora clients and similar), keeping that app's own title, artwork, progress and icon; play/pause and supported previous/next go to that exact app, never to Music, Spotify or a browser that happens to be open
new: Player-Aware Menus - Media widget context menus offer only the transport actions the current player actually supports
improved: The Playing Tab Wins - The YouTube tab that is actually playing supplies the title, artwork and timeline; a paused foreground tab, another window or another browser can no longer take it over, and non-YouTube web media no longer picks up YouTube titles or thumbnails
improved: Exact-Tab Transport - Play, pause and seek go to the browser tab that was authorized, and stop cleanly if that tab closes, navigates away or browser Automation is revoked
improved: Video Preview Stays In Sync - The floating YouTube preview follows the source through loading and seeks, applies the latest play/pause state once the player is ready, keeps its position when the timeline is unknown, and resynchronizes small seeks while paused
improved: Starts Right, Recovers Right - Launching CoolDock while Music is already playing, or recovering from an empty system reader, now reaches valid playback data; system media reads are bounded and fall back to another reader when the preferred one fails
improved: Found On Any Output - Custom players are discovered even when the local audio output is idle, such as Bluetooth or remote routes
improved: Clean Song Transitions - Old tracks no longer reappear after quitting or switching players, while explicit changes (previous/next, A to B to A) show immediately
improved: Controls Without Metadata - Transport stays available for an authorized player even while system metadata is temporarily unavailable
bug fix: Dock Comes Back After Fullscreen And Sleep - If the dock went missing from the current desktop after leaving a fullscreen app or waking your Mac, it now re-registers itself on the active Space and reappears on its own; wake recovery rechecks the dock's Space even when macOS sends no Space-change notification
bug fix: Show All Fits For Real - Adaptive fitting measures actual row widths, widget spacing, running-app spacing and the panel's own screen margins, so dense app and folder rows no longer extend past the display; remaining overflow scrolls, including on narrower displays in All Displays mode, and the chosen tile size is preserved in Scroll mode
bug fix: Top-Edge Targets Line Up - A top dock's content frame now accounts for its top margin, so hit targets and expansion anchors match the visible bar instead of sitting 2 points above it
bug fix: Mail Refresh Can't Be Swallowed - A manual Refresh during an older in-progress read now queues a fresh pass, repeated clicks coalesce, and cancelled or replaced work can no longer consume a newer refresh or leave the widget stuck on "unavailable"
