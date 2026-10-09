# Hearth mobile app (Android APK, built in the cloud)

You do NOT need Android Studio. GitHub builds the APK for free.

## Get the APK (about 10 minutes, one time)
1. Make a free account at github.com → **New repository** (any name, Private is fine).
2. Upload everything in this folder (drag the files/folders into the repo page: *Add file → Upload files*).
   Make sure the `.github/workflows/build-apk.yml` file arrived. If the uploader skipped the hidden `.github`
   folder: *Add file → Create new file*, type `.github/workflows/build-apk.yml` as the name, paste that file's text.
3. Open the **Actions** tab → **Build Android APK** → **Run workflow**. Wait ~5–8 minutes for the green tick.
4. Open the finished run → **Artifacts → hearth-apk** → download the zip → unzip → `app-debug.apk`.
5. Send the APK to your phone (Drive, USB, e-mail). Tap it → allow "Install unknown apps" for that app → Install.
   Play Protect may warn about an unrecognised app — that's normal for a self-built APK.

## Use it
Open Hearth → paste the **device key** from the label (or the QR's key) → if `hearth-xxxxxx.local` doesn't connect on your
phone, type the device's IP in the address box (the setup page and Serial Monitor show it).
Join the device's `Hearth-XXXXXX` network first for setup, using the phone camera on the label QR, exactly as before.

## Build it yourself instead
```
npm install
npx cap add android
npx cap sync android
npx cap open android      # Android Studio -> Build > Build APK(s)
```

## iPhone
Needs a Mac with Xcode: `npx cap add ios && npx cap sync ios && npx cap open ios`.
Free Apple IDs can install on your own phone for 7 days at a time; a lasting install needs the $99/yr developer
program. Simplest iPhone option without any of that: open `http://hearth-xxxxxx.local` in Safari →
Share → **Add to Home Screen** (works with the firmware's built-in app).

## Notes
- This is a *debug-signed* APK for personal use. Publishing on Google Play needs a release signing key and a $25 developer account.
- The app talks to the device over your home Wi-Fi with the same signed-command security as the browser version.
- Bluetooth control isn't in this build (it needs a native Bluetooth plugin); Wi-Fi control is.
