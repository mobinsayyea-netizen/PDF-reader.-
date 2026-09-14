# Mobin PDF Reader

Accessible PDF reader (TalkBack-friendly) with AI-powered features:
- Read PDF pages aloud (System TTS or Gemini Audio)
- Summarize PDF
- Ask questions about the PDF
- Translate pages into 17 languages
- Smart OCR for scanned/image pages

The app runs entirely in the browser (`www/index.html`). Each user enters
their own free Gemini API key in **⚙️ More Options → Set API Key** — the
key is stored only in that browser's local storage and is never included
in this repository.

## Building the APK

This repo is set up with [Capacitor](https://capacitorjs.com/) so GitHub
Actions can build an installable Android APK automatically:

1. Push any change to the `main` branch (or run the workflow manually from
   the **Actions** tab → **Build APK** → **Run workflow**).
2. Wait for the **Build APK** workflow to finish (few minutes).
3. Open the finished run → **Artifacts** → download
   `mobin-pdf-reader-debug-apk`.
4. Unzip it to get `app-debug.apk`, transfer it to an Android phone, and
   install it (allow "install from unknown sources" if asked).

### Building locally instead
```
npm install
npx cap add android
npx @capacitor/assets generate --android
npx cap sync android
cd android
./gradlew assembleDebug
```
The APK will be at `android/app/build/outputs/apk/debug/app-debug.apk`.

## Project structure
```
www/index.html          the entire app (single file)
resources/icon.png       source app icon (1024x1024)
capacitor.config.json    app id, name, web folder
package.json             Capacitor dependencies
.github/workflows/build.yml   auto-builds the APK on every push
```
