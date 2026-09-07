# Phyrexian Keyboard (Android)

A custom system keyboard (IME) for Samsung Galaxy A51 / Android that:
- Draws every key cap using your `PhyrexiaNeue-Transliteration.otf` font, so the whole keyboard reads as Phyrexian glyphs.
- Shows a live preview strip above the keys, rendering the word you're typing in the Phyrexian font.
- Works inside ANY app — WhatsApp, Messenger, Notes, browser, anything with a text field — because it's installed as a real Android input method, not tied to one app.
- English settings screen. App icon is a stylized Magic-card frame with an emblem.

## ⚠️ Important limitation — read this first
The font is a *transliteration* font: it re-skins normal Latin letters (a, b, c…) as Phyrexian shapes. That means:
- **What this keyboard actually sends to other apps is plain English text.** It has to — a keyboard can't force WhatsApp/Instagram/etc. to render text in a font they don't have.
- You (the sender) can see it as Phyrexian in the preview strip and on the key caps while typing.
- The **person receiving your message will see normal English**, unless they also have the Phyrexia Neue font applied on their end, or you send a screenshot of the preview strip instead of the text itself.
- Samsung's One UI does let you set a font system-wide (Settings → Display → Font size and style), which *can* make more apps render text in a custom font — but many apps (WhatsApp, Instagram, etc.) ignore the system font and use their own, so this isn't guaranteed either.

If your real goal is "the other person also sees Phyrexian," the reliable way is to screenshot the preview bar and send that as an image.

## Project structure
```
PhyrexianKeyboard/
  app/src/main/java/com/phyrexian/keyboard/
    MainActivity.kt          - onboarding screen (enable + switch keyboard)
    PhyrexianIME.kt           - the InputMethodService (the actual keyboard service)
    PhyrexianKeyboardView.kt  - custom-drawn keyboard, keys labeled in the Phyrexian font
  app/src/main/assets/fonts/PhyrexiaNeue-Transliteration.otf
  app/src/main/res/...        - layouts, strings, card-shaped adaptive icon
```

## Get a ready APK — no Android Studio, no USB debugging, no computer needed
This project includes a GitHub Actions workflow (`.github/workflows/build.yml`) that builds the APK for you in the cloud. All you need is a free GitHub account, and you can do every step from your phone's browser.

1. Go to **github.com** → sign up (free) if you don't have an account.
2. Tap **+** → **New repository** → give it any name (e.g. `phyrexian-keyboard`) → **Create repository**.
3. On the new repo page, tap **Add file → Upload files**, then upload the *entire contents* of the unzipped `PhyrexianKeyboard` folder (drag the folder in, or select all files/subfolders) → **Commit changes**.
4. Go to the **Actions** tab of your repo. A workflow run should start automatically (or tap **Build APK → Run workflow** if it didn't).
5. Wait a few minutes until it shows a green checkmark ✅.
6. Open that workflow run → scroll to **Artifacts** → download **PhyrexianKeyboard-apk** (it's a zip containing `app-debug.apk`).
7. On your phone, open the downloaded zip, extract `app-debug.apk`, and tap it to install.
   - Android will ask permission once to "install unknown apps" for whichever app you used to open the file (Files, Chrome, etc.) — this is a normal one-time toggle, not developer mode, and only affects apps installed outside the Play Store.

That's the whole thing — no Android Studio, no cable, no Developer Options.

### If you'd rather build it yourself on a computer
You'll need Android Studio (free, from developer.android.com):
1. Open Android Studio → **Open** → select the `PhyrexianKeyboard` folder → let Gradle sync.
2. **Build → Build Bundle(s)/APK(s) → Build APK(s)**.
3. Transfer the resulting `app-debug.apk` to your phone and tap it to install.

## How to use it on the phone
1. Open the app → tap **Open Keyboard Settings** → toggle on "Phyrexian Keyboard".
2. Tap into any text field (WhatsApp, Notes, etc.) → tap **Choose Input Method** (or long-press the space bar / tap the keyboard icon in the nav bar) → pick **Phyrexian Keyboard**.
3. Type normally — the keys and the preview strip show the Phyrexian glyphs; the actual text sent is standard English.
