# MYRA on Linux

Package: [`myra-linux`](https://pypi.org/project/myra-linux/) — the same desktop UI as Windows, with Gemini Live voice, plus Linux system tools.
Tested on Ubuntu 24.04 (including WSL2 with WSLg).

## Requirements
- Ubuntu / Debian based distro with a desktop session (X11 or Wayland via XWayland). Python 3.10+ (Ubuntu 24.04 ships 3.12).
- A microphone and speakers (on WSL: WSLg audio)
- A free Gemini API key: <https://aistudio.google.com/apikey>

## Install (copy–paste)

```
sudo apt install -y pipx libportaudio2 libxcb-cursor0 libxkbcommon-x11-0 libxcb-icccm4 libxcb-image0 libxcb-keysyms1 libxcb-render-util0 libxcb-xinerama0 libgl1 libpulse0 libasound2-plugins pulseaudio-utils tesseract-ocr scrot python3-tk xclip libnotify-bin playerctl brightnessctl wmctrl xdotool network-manager
pipx ensurepath
```
Open a new terminal (or `export PATH="$HOME/.local/bin:$PATH"`), then:
```
pipx install myra-linux
myra-linux
```

> **Why pipx?** Ubuntu 24.04 blocks `pip install` into the system Python (PEP 668). `pipx` gives MYRA its own environment. Do not use `--break-system-packages`.

## Everything in one line
```
sudo apt install -y pipx libportaudio2 libxcb-cursor0 libxkbcommon-x11-0 libxcb-icccm4 libxcb-image0 libxcb-keysyms1 libxcb-render-util0 libxcb-xinerama0 libgl1 libpulse0 libasound2-plugins pulseaudio-utils tesseract-ocr scrot python3-tk xclip libnotify-bin playerctl brightnessctl wmctrl xdotool network-manager && pipx ensurepath && export PATH="$HOME/.local/bin:$PATH" && pipx install myra-linux && myra-linux install && myra-linux
```

## Commands

| Command | What it does |
|---|---|
| `myra-linux` | Open MYRA (window + voice) |
| `myra-linux --background` | Only the floating orb |
| `myra-linux install` | Start at login (orb) and start now |
| `myra-linux uninstall` | Stop starting at login |
| `myra-linux status` | Version, autostart, display and audio status |
| `myra-linux deps` | Install the system libraries above with `sudo apt` |
| `myra-linux update` | Update to the newest version |
| `myra-linux remove [--purge]` | Uninstall (`--purge` also deletes settings/data) |

Update manually: `pipx upgrade myra-linux` (add `--pip-args="--no-cache-dir"` if a brand-new release isn't found).
Remove manually: `myra-linux uninstall && pipx uninstall myra-linux`.

## Audio check
```
myra-linux status
```
You should see `Audio : OK (N devices)`. If not: `sudo apt install libasound2-plugins pulseaudio-utils` and run again. MYRA writes a small `~/.asoundrc` that routes ALSA to PulseAudio/PipeWire if you have none.

## What works / what doesn't
- ✅ Voice chat, languages, name, orb, system monitor, apps by name (from `.desktop` files), volume (`pactl`), brightness (`brightnessctl`), lock/sleep, clipboard, notifications, windows (`wmctrl`), screenshots, OCR, notes, PDFs, QR codes, theme/wallpaper/desktop icons (GNOME).
- ⚠️ Camera vision and screen share are included but less tested than on Windows.
- ⚠️ Spotify opens the search (Linux can't auto-play a track). WhatsApp opens WhatsApp Web with your message filled in (you press Send).
- ❌ Windows-only: security mode, reading/replying to WhatsApp chats. MYRA says so honestly.

## WSL2 notes
- Windows 11 with WSLg shows the window and floating orb on your Windows desktop.
- Microphone: Windows *Settings → Privacy → Microphone → Let desktop apps access your microphone* must be on.
- WSL has no window manager protocol, notification daemon, media player or Wi-Fi, so tools like *open windows*, *notifications*, *media keys* and *Wi-Fi passwords* report that clearly.

## Servers / SSH (no desktop)
MYRA's window needs a desktop session. For terminals use the text version: `pipx install myra-termux` → `myra-termux` (see [termux.md](termux.md#text-only-linux-servers)).
