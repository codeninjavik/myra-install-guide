# MYRA on Windows

Package: [`myra-ai-assistant`](https://pypi.org/project/myra-ai-assistant/)

## Requirements
- Windows 10 or 11, 64-bit
- **Python 3.11 (64-bit)** — the published wheel is built for `cp311-win_amd64`. Check with `python --version`.
  If you have several Pythons, use `py -3.11 -m pip ...` in the commands below.
- A microphone and speakers/headphones
- A free Gemini API key: <https://aistudio.google.com/apikey>

## Install and run
```
pip install --upgrade myra-ai-assistant
myra
```
First run: a splash screen loads, then MYRA asks for your Gemini API key and (optionally) your name. Pick your language in **Settings → Language**.

## Everything in one line
```
pip install --upgrade myra-ai-assistant && myra install && myra
```
`myra install` turns on *start with Windows* and launches the floating orb in the background; plain `myra` then brings the window to the front.

## Commands

| Command | What it does |
|---|---|
| `myra` | Open MYRA |
| `myra --background` | Start with only the floating orb |
| `myra install` | Start with Windows (login) and start now |
| `myra uninstall` | Turn off start with Windows |
| `myra status` | Show whether autostart is on |
| `pip install --upgrade myra-ai-assistant` | Update |
| `pip uninstall myra-ai-assistant` | Remove the app |

## Remove completely
```
myra uninstall
pip uninstall myra-ai-assistant
```
Optional: delete the settings folder `%USERPROFILE%\.aria`.

## Useful things to say
- *"Spotify par Kesariya chalao"*, *"Notepad kholo aur ek story likho"*, *"battery kitni hai"*
- *"English mein baat karo"* / *"speak Spanish"* — switches the language for talking
- *"Mera naam Rahul hai"* — MYRA remembers your name
- Settings → **Screen Guardian**: MYRA watches for obvious mistakes on screen and warns you (off by default, never sees password/bank windows)

## Troubleshooting
- **`myra` not recognised** → close and reopen the terminal; or run `python -m myra`.
- **Wheel not found / "No matching distribution"** → you are not on 64-bit Python 3.11. Install it from python.org.
- **Window too big / zoomed** → update to the latest version; it fixes display-scaling.
- **No voice** → check Windows *Settings → Privacy → Microphone* for desktop apps, and the default mic in *Sound settings*.
- More: [troubleshooting.md](troubleshooting.md)
