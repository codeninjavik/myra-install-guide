# MYRA on Android (Termux)

Package: [`myra-termux`](https://pypi.org/project/myra-termux/) — a phone UI that opens in your browser, with MYRA's photo, **Gemini Live voice that keeps listening**, tool cards, permission prompts and phone automation.

## Requirements
- Android phone with **Termux** (from [F-Droid](https://f-droid.org/packages/com.termux/) or GitHub releases) and the **Termux:API** app (same source). The Play Store versions are outdated.
- Chrome (recommended) for the UI and the microphone
- A free Gemini API key: <https://aistudio.google.com/apikey>

## Install (copy–paste)
```
pkg update && pkg install -y python termux-api
pip install --upgrade myra-termux
myra-termux alias
source ~/.bashrc
myra
```
A link like `http://localhost:8765/?t=…` is shown and the browser opens. If it does not open, copy the **full link** into Chrome.

## Everything in one line
```
pkg update && pkg install -y python termux-api && pip install --upgrade myra-termux && myra-termux alias && source ~/.bashrc && myra
```

## First run
1. If asked, paste your Gemini API key in the card on the screen (MYRA checks it). Add your name and language in ⚙ Settings.
2. Tap the **orb**. It turns green ("listening"). Allow the microphone for Chrome when asked.
3. Just talk. MYRA answers in her own voice and listens again automatically. Tap the orb again to stop.
4. No headphones? MYRA mutes the mic while she speaks (no echo). With headphones turn on **Headphones** in Settings to interrupt her mid-sentence.

## Commands

| Command | What it does |
|---|---|
| `myra` | Phone UI in your browser (after `myra-termux alias`) |
| `myra-termux` / `myra-termux web` | Same; add `--port 9000` or `--no-open` |
| `myra-termux chat` | Terminal chat |
| `myra-termux --setup` | API key, name, language in the terminal |
| `myra-termux --language Tamil` | Set language (`auto` = Hinglish) |
| `myra-termux --languages` | List all languages |
| `myra-termux --name Rahul` | Set your name |
| `myra-termux --ask "battery kitni hai?"` | One question, then exit |
| `pip install --upgrade myra-termux` | Update |
| `pip uninstall myra-termux` | Remove |

## Phone tools
Apps by name (WhatsApp, Instagram, Spotify, YouTube, Camera, Settings…), YouTube/Spotify search, WhatsApp chat with your message filled in, Google Maps navigation, alarm, timer, dialer, contacts lookup (*"Mummy ko SMS bhejo"*), SMS, calls, camera photo, Wi-Fi panel, torch, volume, brightness, clipboard, location, notifications, share, download, media player.

**SMS, calls and WhatsApp always show an Allow / Deny card first.**

### Android's rules (important)
- Android 10+ does not let a background app open other apps. When Termux is blocked, MYRA shows a big button (e.g. *"Alarm 03:00 set karo"*) — **tap it once** and Chrome opens the alarm/app for you.
  To remove the extra tap: *Settings → Apps → Termux → Display over other apps → ON*.
- No app can tap inside another app without root/ADB: Spotify/YouTube open the search (you tap the result), WhatsApp opens the chat with your message (you press Send).
- Grant Termux:API its permissions (SMS, contacts, camera, location) when Android asks.

## Troubleshooting
| Problem | Fix |
|---|---|
| `No command myra found` | `source ~/.bashrc` or restart Termux, or just run `myra-termux` |
| Browser doesn't open | Copy the full `http://localhost:8765/?t=…` link into Chrome |
| "Link purana hai / expire" | The link changes every run — use the new one from Termux |
| Mic not working | Chrome → lock icon → Permissions → Microphone → Allow |
| No sound | Raise media volume; check Chrome isn't muted |
| `Exec format error` / `InvocationTargetException` | Update to the latest version; use the on-screen button or enable *Display over other apps* |
| New version not found | Wait 1–2 min, then `pip install --upgrade --no-cache-dir myra-termux` |
| Keep it running | Termux keeps a wake-lock while MYRA runs; disable battery optimisation for Termux |

## Text-only Linux servers
```
pipx install myra-termux
myra-termux chat          # terminal chat
myra-termux --ask "disk space kitna hai?"
```
(Termux-only tools like SMS/torch are unavailable on Linux; battery, clipboard, notifications, URLs, volume, brightness work.)
