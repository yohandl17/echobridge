# EchoBridge

![Status](https://img.shields.io/badge/status-early%20development-orange)
![Platform](https://img.shields.io/badge/platform-Windows-blue)
![Python](https://img.shields.io/badge/python-3.10%2B-blue)
![License](https://img.shields.io/badge/license-MIT-green)
![Local AI](https://img.shields.io/badge/AI-local%20only-success)
![GPU](https://img.shields.io/badge/GPU-CUDA%20accelerated-76B900)

**EchoBridge** is a local, offline tool that enables near real-time transcription and translation of **in-game voice chat** for PC games.

It is designed for players who want to understand teammates speaking other languages, without relying on cloud services, subscriptions, or paid APIs.

The project focuses on **local AI execution**, **low latency**, and **minimal performance impact**, making it suitable for real multiplayer gameplay.

---

## 🎯 Project Goals

- 🔒 **100% local processing** (no cloud, no external APIs)
- 🎮 **Game-agnostic** (works with any game that outputs voice chat audio)
- ⚡ **Low latency** suitable for cooperative multiplayer (≈300–700 ms target)
- 🧠 **GPU-accelerated AI** (optimized for modern NVIDIA GPUs)
- 🪟 **Non-intrusive overlay** compatible with fullscreen exclusive games
- 📦 **Lightweight repository** (models downloaded on demand, not included)

---

## 🚫 Non-Goals

EchoBridge intentionally does **not**:
- Hook into game engines or game memory
- Interact with anti-cheat systems
- Modify or intercept network traffic
- Use paid or cloud-based AI services
- Provide competitive advantages beyond accessibility and communication

---

## 🧩 High-Level Architecture

In-game voice chat audio
↓
System audio capture (WASAPI loopback / virtual cable)
↓
Speech-to-Text (local Whisper, GPU-accelerated)
↓
Intelligent segmentation (short windows + silence detection)
↓
Local translation (NMT or local LLM)
↓
On-screen subtitles (overlay)
↓
(Optional future) Voice playback (TTS)


All stages are designed to run **asynchronously** to minimize stutter and GPU contention with the game.

---

## 🧠 Core Technologies

### 🎙️ Speech-to-Text
- Whisper / Faster-Whisper
- GPU acceleration via CUDA
- Target model for MVP: `medium` (balance of quality and latency)

### 🌍 Translation
- Local NMT models (e.g. NLLB / Marian)
- Optional future support for local LLMs (Qwen, Mistral, etc.)
- Focus on:
  - Direct translations
  - Preserving gamer slang
  - No added explanations or commentary

### 🖥️ Overlay
- Transparent, always-on-top window
- Compatible with fullscreen exclusive
- Minimal UI:
  - 1–3 subtitle lines
  - Fade-out animation
  - Text outline / shadow for readability
- No hooks, no injection

---

## 🕹️ Target Use Cases

- Cooperative multiplayer games with in-game voice chat:
  - ARC Raiders
  - Squad
  - Battlefield
  - Call of Duty
  - Similar titles
- Accessibility support for players who do not speak the team’s language
- Personal use during real gameplay
- Open-source experimentation with local audio AI pipelines

---

## 📦 Repository Philosophy

- **Code only** — no large binaries or models
- AI models are:
  - downloaded automatically on first use
  - stored outside the repository
- Modular design:
  - `audio`
  - `stt`
  - `translation`
  - `overlay`
- Easy to extend:
  - more languages
  - TTS
  - keyword detection
  - per-game profiles

---

## 🚧 Project Status

**Early development / MVP stage**

Current focus:
- Project structure
- Audio capture on Windows
- Basic STT → translation pipeline (console output)

Overlay and real-time optimizations will follow once the core pipeline is stable.

---

## 🗺️ Roadmap (High-Level)

### MVP
- [ ] Capture system audio (in-game voice chat)
- [ ] Transcribe speech locally
- [ ] Translate text locally
- [ ] Display subtitles (initially console, then overlay)

### Post-MVP
- [ ] GPU optimizations and batching
- [ ] Overlay polish (fade, styling, positioning)
- [ ] Configurable languages
- [ ] Optional TTS output
- [ ] Noise filtering / VAD improvements

---

## ⚠️ Disclaimer

EchoBridge is a **passive audio processing tool**.  
It does not interact with games beyond reading system audio output.

Use at your own discretion and always respect the terms of service of the games you play.

---

## 📄 License

MIT License
