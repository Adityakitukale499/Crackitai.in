# CrackitAI

A Windows desktop suite for privacy and AI-assisted meetings. Two binaries, one workspace.

## Binaries

### CrackitAI (injector crate)
Hides specific windows from screen sharing, screenshots, and optionally from the taskbar and Alt+Tab. Uses DLL injection to set `WDA_EXCLUDEFROMCAPTURE` on target processes.

### MeetAssist (assistant crate)
Real-time AI meeting assistant. Captures system audio, transcribes via OpenAI Whisper, and streams AI-generated responses in an overlay window — invisible to screen-share viewers.

---

## Features

**Window Hiding**
- Hide any window from screen capture/sharing
- Optionally hide from taskbar and Alt+Tab
- Live desktop preview to verify what others see
- GUI window list + CLI for scripting

**AI Assistance**
- Real-time audio transcription (OpenAI Whisper)
- Streaming AI answers from OpenAI, OpenRouter, Anthropic Claude, or Google Gemini
- Push-to-Talk (Ctrl+Space) and auto-detect voice modes
- Screen capture vision analysis (Ctrl+R)
- Manual question input
- Upload PDF resume/docs as AI context
- Custom system prompt instructions

**Privacy**
- MeetAssist can hide itself from screen capture
- License-gated access via device-bound keys

---

## Hotkeys (MeetAssist)

| Shortcut | Action |
|----------|--------|
| Ctrl+Space | Push-to-talk |
| Ctrl+R | Capture screen for vision analysis |
| Ctrl+← / → | Move overlay window |
| Ctrl+↑ / ↓ | Adjust opacity |
| Ctrl+Shift+S/M/L | Set window size (Small/Medium/Large) |

**AutoHotkey script** (`hide.ahk`) for CrackitAI window hiding:

| Shortcut | Action |
|----------|--------|
| Ctrl+J | Hide active window |
| Ctrl+K | Unhide active window |
| Ctrl+Q | Exit script |

---

## Tech Stack

- **Language**: Rust (nightly, Edition 2024)
- **GUI**: egui + eframe + wgpu
- **Win32**: `windows` crate, DLL injection via `dll-syringe`
- **AI**: OpenAI Whisper (STT), multi-provider LLM streaming
- **Audio**: `cpal` (loopback capture)

---

## Build from Source

**Prerequisites:** Windows 10+, Rust nightly toolchain

```bash
git clone https://github.com/Adityakitukale499/Interview-AI-Assistance.git
cd Interview-AI-Assistance
cargo build --release
```

Binaries output to `target/release/`. For a Windows installer, use `Misc/inno.iss` with Inno Setup.

---

## CLI Usage (CrackitAI)

```bash
CrackitAI.exe --hide notepad.exe
CrackitAI.exe --unhide 1234
```

---

## Configuration (MeetAssist)

Config stored at `%APPDATA%\meetassist\config.toml`. Set via the Settings page:
- AI provider + API key + model
- Whisper API key
- Audio device (loopback)
- Overlay size and theme
- License key

---
