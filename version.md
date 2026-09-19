VERSION: 2.0.8
DETAILS:

improved: Hovering No Longer Redraws The Whole Dock - Each tile owns its own hover state, so moving the pointer updates only the tile under it instead of invalidating every widget; the main cause of hover and click lag on large docks
improved: Labels Driven By The Pointer - App, folder and pinned-window labels are resolved from cached tile frames; the pointer is converted once per dock window instead of once per icon, and no tile rebuilds for a label to appear
improved: Labels That Keep Up - Name labels appear the instant you hover and sit exactly over the icon; fast moves across Live Dock icons no longer cancel the pending label or make it chase the pointer; window previews keep their short dwell
improved: No Timer For Plain Labels - The 60 Hz position tracker runs only for interactive window-preview panels; a plain label follows its icon from the cached frame
improved: Labels Remember Their Place - Hover anchors survive a label hide, and pinned-window tiles register a real anchor like app launchers
bug fix: Edge Reveal Reverses In Place - A fixed dock interrupted mid-hide slides back from where it is with a duration scaled to the remaining travel instead of replaying the whole animation
improved: Snappier Slide Timing - The fixed dock slides straight off and on screen (hide 0.18 s, reveal 0.22 s) without the shrink-and-fade that floating placements keep
improved: Edge Reveal Without The Poll - Show and hide fire exactly when the configured delay expires instead of waiting on a 5 Hz timer; pointer moves inside a stable reveal zone no longer trigger a full layout refresh
bug fix: Fullscreen Games Detected - Borderless full-display game surfaces on a normal Space count as fullscreen, so the dock hides over them while maximized windows still do not
bug fix: Click A, Then B, Get B - A delayed restore or launch completion for the first app can no longer steal focus after you moved on; activation happens immediately on click and stale completions are ignored
bug fix: No Surprise New Windows - Clicking a running app whose windows could not all be enumerated in time no longer sends a reopen event
bug fix: Clicks Land Where They Should - Every present and dismiss path updates the click-through gate, so clicks no longer fall through or get swallowed by the empty reserve band after a fast show/hide
improved: A Hung App Can't Stall The Dock - Window scans, launch restores, reserve-space passes and observer registration run with per-element timeouts, a total deadline and window/app caps; heavy apps make progress across passes
improved: Reserve Work Off The Main Thread - The per-window read, write and verify traversal runs on a dedicated worker and results are applied only while still current
bug fix: Windows Always Come Back - Toggling Reserve Dock Space off, on and off again no longer lets an old restoration fight a new reservation; interrupted windows keep their original frames and are retried
improved: Lighter Window Previews - Hovering fetches only that app's windows, refreshes are single-flight, older snapshots cannot overwrite fresher per-app data, and thumbnails are keyed by process
improved: Applications Gallery Off The Render Path - The gallery snapshot is built off the main thread, skips identical requests and loads icons asynchronously behind placeholders; superseded batches are cancelled
bug fix: No Stale Icons - A cancelled icon load can no longer publish an outdated image into the cache or the view
improved: Faster Trash - Trashed folders are no longer sized recursively or re-checked on every render; thumbnail prefetch stays within the visible page plus one
improved: Contacts That Don't Stutter - The chooser no longer decodes every contact photo up front, rows load their own details, deleted contacts are not re-queried on every render, and the Quick Contacts row opens at its final width
improved: Leaner Launch - Live-service sync no longer runs twice on the licensed path, repeated licensed signals no longer re-run the restore sequence, and badge tracking rescans only when the tracked set changed
improved: Media Parsing Off The Main Thread - Now Playing JSON and artwork decoding and the helper's output read no longer hitch media widgets
improved: Smoother Widget Drags - Inserting or reordering widgets on a large dock uses a one-time index map, and the dock bar no longer re-renders on every running-app count change
new: Hover Diagnostics In Exports - Export Diagnostics includes content-free hover counters and dock slide animation timing to tell a missed hover from a slow main thread
