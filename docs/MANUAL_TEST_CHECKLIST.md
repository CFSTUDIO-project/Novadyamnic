# Manual test checklist

Run this on a real phone after the first successful build. Tick what passes, note what does not, and
include the Android version and phone model when you report a problem.

Device: ______________________  Android: ______  Build: ______________________

## 1. Install and first run
- [ ] APK installs. App opens to the intro, then the welcome screen. The intro never shows a fake progress bar.
- [ ] "Get Started" opens the permission wizard. Each permission has its own card.
- [ ] Display over other apps: "Grant Access" opens the right system page; coming back flips the badge from yellow to green without restarting the app.
- [ ] Notification access: same behaviour. On Android 13+, if the toggle is greyed out, "Open App info" -> menu -> "Allow restricted settings" works.
- [ ] "Next" works even when nothing is granted.
- [ ] Dashboard shows the right state for every permission.

## 2. Start and stop
- [ ] START ISLAND without overlay permission opens the permission wizard instead of failing silently.
- [ ] START ISLAND with permission shows the pill at the top, under the status bar or camera cutout.
- [ ] A foreground notification "NOVA PILL is running" appears with a Stop action.
- [ ] STOP ISLAND removes the pill and the notification completely.
- [ ] Stop from the notification action does the same.
- [ ] Force-stop the app, reopen it: with "Restore island on launch" on, the island comes back; with it off, it does not.

## 3. Placement
- [ ] Portrait on a phone with a centre punch-hole: the pill clears the hole (compact content splits left/right when it has to).
- [ ] Portrait on a phone without a cutout.
- [ ] Rotate to landscape: the pill moves, shrinks if "Compact cards in landscape" is on, and never sits under the cutout.
- [ ] Appearance sliders (width, height, top, horizontal, corner, border, opacity) change the preview and the real pill.
- [ ] Long-press to reposition: drag, Done saves, Reset restores.

## 4. Music
- [ ] Spotify: play a track. Compact pill shows artwork, title/artist, visualizer bars.
- [ ] Tap opens the card: artwork, title, artist, progress, prev / play-pause / next, volume.
- [ ] Play/pause, next and previous act on the player that is shown, never another one.
- [ ] Seeking works where the player allows it and is disabled (not hidden) where it does not.
- [ ] A second player (YouTube Music, a local player): the card follows the preferred player, or Spotify first on Automatic.
- [ ] Pausing: the pill follows "When paused" (Keep / Collapse / Hide) after the grace time.
- [ ] The visualizer is described as decorative in Settings -> Music.

## 5. Lyrics
- [ ] Lyrics button with no source: "Lyrics unavailable for this track" plus Retry and Import .LRC.
- [ ] Import a line-synced .lrc: lines follow the song; the footer says "Line sync - Imported file".
- [ ] Import a file with word timestamps: words highlight; the footer says "Word sync".
- [ ] Plain text lyrics are shown as "Unsynced lyrics" and are not scrolled as if they were synced.
- [ ] Offset - / + / Reset work in 50 ms steps within +-1500 ms, per track and globally.
- [ ] LRCLIB off (default): nothing is requested over the network.
- [ ] LRCLIB on: a lookup happens for the playing track; an ambiguous match shows a picker.

## 6. Notifications and calls
- [ ] A message notification peeks for the chosen length (2 / 3 / 4 / 6 s) showing app name and short summary only.
- [ ] Privacy levels App name / Summary / Full behave as described; the lock screen always shows the app name only.
- [ ] Muted apps, muted categories, and "Only allowed" mode filter as expected.
- [ ] Several notifications queue (or keep only the latest) as set.
- [ ] Incoming call: the peek shows Decline (red) and Accept (green) with 48 dp targets; both act on the real call notification.
- [ ] Tapping a normal peek opens the app that sent it.

## 7. Timer, stopwatch, tools
- [ ] Start a timer from the tools card; it appears as a card/badge, pauses, resumes, resets.
- [ ] Timer finishing shows the finished state and posts "Timer finished" even if the screen was off.
- [ ] Stopwatch start / pause / resume / reset.
- [ ] Flashlight toggles the real torch; the app never asks for the camera permission.
- [ ] Volume slider changes media volume.
- [ ] Weather: set a city in Settings -> Utilities; the tools card shows temperature and the Open-Meteo credit exists in Settings.
- [ ] Battery shows level and charging state.

## 8. Record indicator
- [ ] Android 15+: start the system screen recorder; the card is labelled OS only when Android reported it.
- [ ] Manual Start / Pause / Stop / Reset work; the label says Manual.
- [ ] Android 14 or older: the card says Unsupported for OS detection and offers only the manual timer.

## 9. Motion and battery
- [ ] Reduce motion replaces springs with short fades.
- [ ] Turning Android's animations off makes the pill calm automatically.
- [ ] Battery saver on + "Reduce motion in battery saver": same calm behaviour.

## 10. Settings and privacy
- [ ] Every settings page opens, changes persist after force-stop.
- [ ] Reset all settings restores defaults and keeps imported lyrics.
- [ ] Privacy page: statuses are right; the three Clear buttons work.
- [ ] About & Debug: versions, screen, orientation, states and last error look right; Export diagnostics contains no titles, lyrics or notification text.

## 11. Robustness
- [ ] Reboot with "Start after reboot" on: the island returns (some phones need auto-start allowed; note which).
- [ ] Open a fullscreen video: the pill hides (setting on) and returns afterwards.
- [ ] Open the keyboard: the pill hides (setting on).
- [ ] Revoke "Display over other apps" while running: the app reports it and does not crash.
- [ ] Revoke Notification access while running: music and peeks stop cleanly.
