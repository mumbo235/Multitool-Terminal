# GitHub Releases & Changelog Archive

This document contains formatted release notes for **Multitool Terminal**. You can copy and paste each section directly into the [GitHub Releases UI](https://github.com/) or publish them via the GitHub CLI (`gh`).

---

## How to Publish via GitHub CLI

To publish any release alongside the standalone single-file distribution:

```bash
# Example: Publishing v2.5.0
gh release create v2.5.0 \
  --title "v2.5.0 - Live Dungeon RPG, Autocomplete Engine & Compact Manual" \
  --notes-file RELEASE_NOTES_v2.5.0.txt \
  index.html
```

---

## Release v2.5.0 (Latest Major Release)

**Tag**: `v2.5.0`  
**Release Title**: `v2.5.0 - Live Dungeon RPG, Autocomplete Engine & Compact Manual`  
**Target Branch**: `main`

### Overview

Multitool Terminal v2.5.0 brings major enhancements to gameplay immersion, command typing speed, and interface polish. This release introduces a live in-place 5-floor Rogue RPG crawler with direct keystroke movement, a real-time command autocompletion pill bar, a high-contrast browser tab favicon, a compact single-screen help manual, and a rebuilt ASCII banner generator.

### What's New in v2.5.0

#### 1. Live In-Place Dungeon RPG Crawler (`dungeon`, `crawl`, `rpg`)
- **Live In-Place Board**: Transformed the dungeon crawler into a real-time reactive canvas container (`#dungeon-session-*`) that updates in-place, eliminating map re-printing and terminal buffer clutter.
- **Direct Keystroke Movement**: Move and strike immediately with **`[W/A/S/D]`** or **`[Arrow Keys]`** (no Enter key needed).
- **5 Procedural Floors**:
  - Floor 1: *The Catacombs* (Bats, Goblins, Chests, Potions)
  - Floor 2: *The Crypt* (Skeletons, Vipers, Weapon Shrine)
  - Floor 3: *The Armory* (Orcs, Armor Shrine, Vault Key)
  - Floor 4: *The Nether Depths* (Nether Demons, Locked Vault Door, Relic Chest)
  - Floor 5: *The Dragon Sanctum* (The Ancient Nether Dragon Boss)
- **Interactive Shrines & Vaults**:
  - Weapon Shrines (`W`) granting permanent +4 ATK.
  - Armor Shrines (`A`) granting permanent +3 DEF.
  - Dungeon Keys (`K`) and Locked Vault Doors (`X`) guarding high-value chests.
  - Spike Traps (`^`) dealing 15 damage upon missteps.
- **Potions & Extraction**: Drink healing potions mid-battle with **`[P]`**; safely escape at any moment with **`[Q]`** or **`[Esc]`** to bank earned loot and credits.
- **Boss Victory Rewards**: Slaying the Floor 5 Dragon awards +500 CR bonus and the permanent title badge `[Nether Slayer]`.

#### 2. Real-Time Command Autocomplete Engine
- **Live Suggestion Pill Bar**: An interactive suggestions bar renders right above the active command prompt as you type.
- **Tab & Arrow Key Acceptance**: Hit **`[Tab]`** or **`[Right Arrow]`** to instantly complete the highlighted suggestion.
- **Cycle Through Matches**: Hit **`[Tab]`**, **`[Down Arrow]`**, or **`[Up Arrow]`** to cycle through multiple matching commands.
- **Click-to-Complete**: Click any suggested pill chip with the mouse to fill the command line immediately.
- **Dismissal Controls**: Press **`[Esc]`**, backspace to empty, or submit the command to clear the pill bar.

#### 3. High-Contrast SVG Browser Tab Favicon
- Added an embedded high-contrast SVG favicon directly in `<head>`.
- Displays an authentic dark terminal window with green CRT border and glowing `>_` prompt icon, providing instant tab recognition in browser tab strips.

#### 4. Squished ASCII Art Startup Banner & Fixed Typography
- Replaced wide header art with an authentic squished, compact terminal banner matching retro BBS aesthetic.
- Fixed the top cap alignment on the letter `l` in `MULTITOOL TERMINAL` banner art.
- Balanced font row heights across all screen resolutions.

#### 5. Compact Dashboard Help Manual (`help`)
- Shrunk the default `help` manual down to a single-screen dashboard overview categorized into clean two-column tables.
- Added deep-dive category syntax:
  - `help core` &bull; Session and terminal environment
  - `help ai` &bull; AI models, reasoning latency, and shorthands
  - `help games` &bull; Live RPG dungeon, casino, and arcade
  - `help tools` &bull; Cryptography, math, and developer parsers
  - `help net` &bull; Network probes, weather, crypto, and feeds

#### 6. ASCII Art Text Generator Fix (`ascii <text>`)
- Fixed row alignment and font glyph spacing in the `ascii` command.
- Double-escaped all backslashes in glyph string tables to prevent browser JavaScript parser stripping.

### Verification & Quality Assurance
- **Strictly Zero Unicode Emojis**: 100% compliant with Unix terminal standards; all graphics rely on ASCII brackets (`[7]`, `[$]`, `[BAR]`, `[OK]`, `[PRO]`) and ANSI symbols.
- **Self-Contained File Size**: 259,925 bytes in a single, zero-dependency `index.html` file.
- **Browser Compatibility**: Fully tested across Chromium (Chrome, Edge, Brave), Firefox, and Safari.

---

## Release v2.0.0

**Tag**: `v2.0.0`  
**Release Title**: `v2.0.0 - Gemini Pro Priority Streaming, TUI Settings & Seamless Auto-Login`  
**Target Branch**: `main`

### Overview

Multitool Terminal v2.0.0 transforms the terminal into a full-fledged intelligent developer workstation with multi-provider AI streaming, Pro tier priority failover, an interactive TUI configuration system, a local credit economy with casino minigames, and seamless session authentication.

### What's New in v2.0.0

#### 1. Pro Priority AI Engine & Upstream Failover
- **Google Gemini Pro Priority**: Defaults to `gemini-2.5-pro` with Pro tier priority for advanced coding and architectural reasoning.
- **Resilient Demand & Quota Fallback**: Seamlessly reroutes requests to `gemini-3.8-flash` on HTTP 429 (`RESOURCE_EXHAUSTED`) or HTTP 503 (`UNAVAILABLE`), keeping the user informed while preserving their default Pro configuration.
- **Defunct Model Purge**: Fully deprecated Gemini <= 3.6 endpoints; incoming requests targeting legacy versions are automatically intercepted and upgraded to active production endpoints (`gemini-2.5-pro` or `gemini-3.8-flash`).
- **Reasoning Latency Tuning**: Added `ai thinking fast|balanced|deep|off` to calibrate thinking token limits (512 to 4096 tokens) to eliminate stream latency.
- **Multi-Provider Hub**: Support for Google Gemini, Anthropic Claude, OpenAI, and OpenRouter with full live markdown streaming.

#### 2. Interactive Terminal Configuration Menu (`settings`, `config`)
- Terminal-native TUI menu supporting menu numbers `[1]` through `[6]` and `[0]`:
  - `[1] AI Providers & API Keys`
  - `[2] Active Model Selection`
  - `[3] Visual Appearance & CRT Scanlines`
  - `[4] Sound & Web Audio Bell Effects`
  - `[5] User Profile & Security`
  - `[6] Factory Reset`
- Added direct CLI shortcuts: `settings list`, `settings set <key> <val>`.

#### 3. Seamless Auto-Login & Passwordless Profile Support
- Automatic session restoration on page reload when user profiles exist in `localStorage`.
- Accounts created with blank passwords skip authentication prompts entirely.
- Added `passwd` command for changing or clearing passwords, and `logout` to terminate sessions.

#### 4. Terminal Economy & Shop System
- Persistent credit ledger stored in `localStorage` (`multitool_terminal_wallet`).
- Starting credit grant of 500 CR for new accounts.
- Daily rewards: `daily` grants 250 CR once every 24 hours (+50 CR for Golden VIP).
- Cyber-contracts: `work` and `mine` grant 65-110 CR for completing background mining tasks.
- Terminal Shop (`shop`): Buy combat equipment, casino probability charms, and VIP status titles.

#### 5. Casino Minigames
- 3-Reel Slot Machine (`slots`): Audio chimes, spinning reel animations, and payouts up to 30x on Jackpot 777.
- Blackjack 21 (`blackjack`): Turn-based game vs terminal dealer with soft-17 rules, double down, and 2.5x natural blackjack payouts.
- European Roulette (`roulette`): 37-pocket wheel with color, odd/even, and direct number betting.
- Coinflip & Dicebet: Instant double-or-nothing games with streak tracking.

---

## Release v1.0.0 (Initial Public Release)

**Tag**: `v1.0.0`  
**Release Title**: `v1.0.0 - Standalone Single-File Developer Terminal & Shell Suite`  
**Target Branch**: `main`

### Overview

Initial public release of Multitool Terminal: a self-contained, client-side developer environment packaged entirely in a single `index.html` file.

### Key Features

- **Zero-Dependency Architecture**: Runs in any modern browser without npm packages, Node.js servers, or build tools.
- **Authentic Fullscreen Aesthetic**: Clean 100vw x 100vh canvas with 6 color themes (`macos-dark`, `dracula`, `matrix`, `amber`, `nord`, `solarized`) and optional CRT phosphor scanlines.
- **70+ Developer & Network Utilities**:
  - Cryptography: SHA-1, SHA-256, SHA-384, SHA-512, MD5, Base64 encode/decode, UUID v4 generator.
  - Data & Formatting: JSON formatter, JWT decoder, Regex tester, CSV tabular viewer, Diff viewer, Word count (`wc`).
  - Network Probes: DNS lookup via Cloudflare DoH, RDAP Whois lookup, CIDR subnet calculator, live Weather via Open-Meteo, Crypto ticker via Binance, HTTP test via `curl`.
  - Diagnostics: Browser hardware info (`sysinfo`), multi-threaded CPU benchmark (`bench`).
- **Arcade & Productivity Tools**:
  - ASCII Snake with score cashout.
  - Trivia quiz, Hangman word game, Number guesser.
  - Persistent task manager (`todo`), notebook (`notes`), stopwatch, and Pomodoro timer.
  - Classic terminal easter eggs: `sudo`, `sl`, `cowsay`, `fortune`, `hack`, `konami`, `coffee`.

---

## Release Asset Distribution

All releases distribute the portable standalone file:

| File | Type | Description |
| :--- | :--- | :--- |
| `index.html` | Application Bundle | Full terminal application, CSS styles, JavaScript runtime, and graphics. |
| `README.md` | Documentation | Repository overview, quick start, and feature guide. |
| `wiki/` | Documentation Archive | Offline copy of complete GitHub Wiki manual. |

---

## Verification & Integrity

To verify your local copy of `index.html`:

```bash
# Calculate SHA-256 checksum
sha256sum index.html
```
