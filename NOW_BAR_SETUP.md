# Study Clock — Samsung Now Bar / Android 16 Live Updates

This project now targets Android 16 (API 36) and uses AndroidX Core 1.17.0.
The running timer notification requests promoted ongoing treatment, which is the
Android 16 Live Updates mechanism that Samsung One UI 8 can use for Now Bar surfaces.

## Important device-side requirements

1. Install the APK on a Galaxy device running One UI 8 / Android 16 or later.
2. Allow Study Clock to post notifications.
3. In Samsung/Android notification settings, make sure Live Updates / promoted
   notifications are enabled for Study Clock if the device exposes that option.
4. Start a timer from the app. The foreground-service notification should be
   eligible for promotion and can appear in the Now Bar.

The app still falls back to a normal ongoing foreground-service notification on
older Android versions.

## What changed

- `compileSdk` and `targetSdk`: 36
- AndroidX Core: 1.17.0
- The timer notification calls `NotificationCompat.Builder#setRequestPromotedOngoing(true)`
- The existing `android.requestPromotedOngoing` extra remains as a compatibility fallback.
- The notification remains an ongoing foreground-service notification and uses the
  system chronometer for the countdown, so there is no per-second notification update loop.

## Build

Open the project in current Android Studio, install Android SDK Platform 36, then
use **Build > Make Project** or **Build > Build APK(s)**.
