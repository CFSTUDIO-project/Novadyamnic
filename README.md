# NOVA PILL — Live Island

A Dynamic-Island-style pill for Android, drawn natively with Kotlin and Jetpack Compose.
Music with honest lyrics, timers, calls, notification peeks. Black and crimson, no stock Material look.

> **Work in progress README.** The full illustrated README follows in the next drop.

## Build it on GitHub (no Android Studio needed)

1. Create an empty repository on GitHub and upload the contents of this folder (the folder that contains `gradlew`).
2. Open the **Actions** tab, choose **Android build**, press **Run workflow** (it also runs on every push).
3. When the run is green, open it and download **nova-pill-debug-apk** under **Artifacts**.
4. Unzip it, copy `app-debug.apk` to the phone and install it (allow "Install unknown apps" once).

## Honest status

* The pure logic (state machine, lyrics parser, matcher, notification filter, settings codec, layout maths) is covered by unit tests that pass.
* The Android and Compose layers have **not** been compiled or run on a device by the author of this drop. The first GitHub Actions run is the first real compile. If it fails, the log shows the exact line.
* There is no signing key or secret anywhere in this repository.

See `docs/MANUAL_TEST_CHECKLIST.md` for what to check on a real phone.
