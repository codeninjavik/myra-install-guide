# Troubleshooting

## Installing

| Symptom | Cause | Fix |
|---|---|---|
| `error: externally-managed-environment` | Ubuntu/Debian protect the system Python (PEP 668) | `pipx install myra-linux` (or a venv). Don't use `--break-system-packages` |
| `No matching distribution found for myra-linux==X` right after a release | Package index cache | Wait 1–2 min, then `pipx install --force --pip-args="--no-cache-dir" myra-linux` |
| `myra-linux: command not found` | pipx's folder not on PATH | `pipx ensurepath`, reopen the terminal (or `export PATH="$HOME/.local/bin:$PATH"`) |
| *File exists … points to another venv* | An older package owned the command | `pipx uninstall myra-termux` then `pipx install --force myra-linux` |
| Windows: no matching distribution | Not Python 3.11 64-bit | Install Python 3.11 (64-bit) and use `py -3.11 -m pip install myra-ai-assistant` |
| Termux: `No command myra found` | Alias not loaded yet | `source ~/.bashrc` or restart Termux |

## Voice and audio

| Symptom | Fix |
|---|---|
| Linux: `No mic found`, `PortAudio` errors | `sudo apt install libportaudio2 libasound2-plugins pulseaudio-utils`, then `myra-linux status` → `Audio: OK` |
| Voice cuts out / choppy while tools run | Update to the latest version (tools run in their own thread and the speaker buffer is larger) |
| WSL: no microphone | Windows *Privacy → Microphone → desktop apps* ON; restart WSL (`wsl --shutdown`) |
| Phone: orb stays orange | Check internet; the Live session reconnects automatically — if it doesn't, tap the orb twice |
| Phone: mic permission | Chrome → lock icon → Permissions → Microphone → Allow |
| MYRA hears herself | Use headphones, or keep **Headphones** off (mic is muted while she speaks) |

## Windows/desktop UI

| Symptom | Fix |
|---|---|
| Floating orb sits in a corner / can't be dragged (Linux/WSL) | Update `myra-linux`; overlay windows are placed without the window manager |
| Border glow not on the full screen (Linux) | Same — update |
| UI looks zoomed (Windows) | Update to the latest `myra-ai-assistant` |
| Another copy says "Pehle se chal rahi hai" | MYRA is already running; close it first (`pkill -f myra-linux` on Linux) |

## Phone tools

| Symptom | Fix |
|---|---|
| Alarm/app doesn't open | Tap the button MYRA shows, or enable *Display over other apps* for Termux |
| "Termux:API is not yet available on Google Play" | Install Termux:API from F-Droid/GitHub (same source as Termux) |
| SMS/contacts fail | Open the Termux:API app permissions and allow SMS/Contacts |
| Torch/battery work but app launch fails | Android background-launch rule — see above |

## API key
- Create a key at <https://aistudio.google.com/apikey>. MYRA validates it when you save.
- Free keys have rate limits (a few requests per minute). A `429` error means: wait a minute.
- Keys are stored locally and are never sent anywhere except Google's Gemini API.

## Still stuck?
Open an issue in this repository with: your platform, the command you ran, and the **full** terminal output (remove your API key/tokens first). Telegram: <https://t.me/codeninjavik1>.
