# Multitool Terminal

[![Architecture](https://img.shields.io/badge/Architecture-Single--File_HTML-blue.svg)](#architecture)
[![Zero Backend](https://img.shields.io/badge/Backend-100%25_Client--Side-brightgreen.svg)](#privacy--storage)
[![AI Engine](https://img.shields.io/badge/AI-Gemini_|_Claude_|_OpenAI_|_OpenRouter-purple.svg)](#ai-performance--model-architecture)
[![Games](https://img.shields.io/badge/Games-Live_RPG_|_Casino_|_Snake-orange.svg)](#terminal-games--entertainment)
[![License](https://img.shields.io/badge/License-MIT-yellow.svg)](#license)

A self-contained, single-file developer terminal interface running entirely inside any modern web browser. Designed as an authentic fullscreen terminal canvas (no faux window frames, 100vw x 100vh) with glowing colored ASCII typography, colored status indicators, an interactive `settings` TUI menu, authentic multi-user authentication with passwordless auto-login, real-time command autocompletion, multi-provider AI integration with Google Gemini Pro priority, a live 5-floor Rogue RPG dungeon crawler, an in-browser casino economy, and 75+ built-in developer and shell utilities.

---

## Table of Contents

- [Quick Start](#quick-start)
- [Key Architectural Highlights](#key-architectural-highlights)
- [Command Autocomplete Engine](#command-autocomplete-engine)
- [Authentication & Auto-Login](#authentication--auto-login)
- [AI Performance & Model Architecture](#ai-performance--model-architecture)
- [Terminal Economy & Shop System](#terminal-economy--shop-system)
- [Casino & Gambling Minigames](#casino--gambling-minigames)
- [Terminal Games & Entertainment](#terminal-games--entertainment)
- [Interactive Configuration Menu (`settings`)](#interactive-configuration-menu-settings)
- [Complete Command Reference](#complete-command-reference)
- [Privacy & Storage](#privacy--storage)
- [GitHub Wiki & Releases](#github-wiki--releases)
- [License](#license)

---

## Quick Start

`Multitool Terminal` requires **zero server installation**, **no npm dependencies**, and **no build steps**.

### 1. Direct Browser Launch
Open `index.html` directly from your file manager or run:
```bash
# Linux
xdg-open index.html

# macOS
open index.html

# Windows
start index.html
```

### 2. Run with Local Static Server
```bash
# Python 3
python3 -m http.server 8080

# Node.js
npx serve -l 8080

# PHP
php -S localhost:8080
```
Then navigate to `http://localhost:8080`.

---

## Key Architectural Highlights

- **Single-File Distribution**: Entire application (HTML, CSS, JavaScript engine, icons, fonts) lives in one portable `index.html` file (~260 KB).
- **100% Zero Backend Required**: Runs client-side. Web APIs, cryptographic hashes, AI streaming, RDAP lookups, and games run directly in browser memory.
- **Authentic Fullscreen Aesthetic**: No window title bars, minimize/maximize buttons, or decorative desktop frames. Full viewport immersion (`100vw` x `100vh`) with customizable CRT scanlines.
- **Strictly Zero Unicode Emojis**: Follows an authentic UNIX terminal aesthetic. Visuals utilize colored ASCII art, brackets (`[7]`, `[$]`, `[BAR]`, `[A S]`), standard status badges, and ANSI-style symbols (`&bull;`, `&gt;`).
- **Offline Resilient**: Core developer utilities, math evaluator, cryptography tools, text processing, shell aliases, and all offline games run without internet access.

---

## Command Autocomplete Engine

Typing inside the terminal features real-time, interactive autocompletion:
- **Live Suggestion Bar**: As you type, matching command chips appear above the prompt line (`Suggest: [slots] [sl] [stopwatch]`).
- **Single-Key Acceptance**: Press **`[Tab]`** or **`[&rarr;]`** (Right Arrow) to instantly accept the highlighted completion.
- **Cycling Suggestions**: Pressing **`[Tab]`**, **`[&darr;]`**, or **`[&uarr;]`** cycles through matched candidates.
- **Clickable Chips**: Click any suggested pill with the mouse to complete it directly into the input buffer.
- **Clean Dismissal**: Press **`[Esc]`**, backspace to empty, or submit a command to dismiss suggestions.

---

## Authentication & Auto-Login

The terminal provides authentic multi-user Unix-like session security right inside the browser:
- **First-Run Profile Setup**: Prompts for a username and optional password on initial launch.
- **Passwordless Support**: Accounts created without a password (or with password removed via `passwd`) skip password entry completely.
- **Seamless Auto-Login**: Once created, browser reloads automatically authenticate and restore user sessions without repetitive login prompts.
- **Session Switching**: Type `logout` to terminate a session; use `login` or `login <user>` to switch accounts.
- **Configuration Toggle**: Auto-login can be toggled via `settings` &rarr; `[5] User Profile & Security` or CLI `settings set autoLogin true|false`.

---

## AI Performance & Model Architecture

### 1. Pro Priority Engine (`[PRO]`)
For users with Google Gemini Pro subscriptions:
- **Default Flagship**: Defaults to **`gemini-2.5-pro`** for deep multimodal reasoning and coding.
- **Resilient Demand & Quota Fallback**: If `gemini-2.5-pro` encounters rate limits (HTTP 429, `RESOURCE_EXHAUSTED`) or high upstream demand spikes (HTTP 503, `UNAVAILABLE`), requests route to priority fallback `gemini-3.8-flash` (and `gemini-2.5-flash`), notifying the user while keeping Pro priority configured for future requests.
- **Defunct Models Purged**: Discontinued models (&le; 3.6) are removed and automatically intercepted/upgraded to active production endpoints (`gemini-2.5-pro` or `gemini-3.8-flash`).

### 2. Reasoning Latency Tuning (`ai thinking`)
- Tune Gemini 2.5 Pro thinking token budget to eliminate pre-computation delays:
  - `ai thinking fast` &bull; 512 tokens for rapid interactive streaming
  - `ai thinking balanced` &bull; 1024 tokens (default) for balanced reasoning and speed
  - `ai thinking deep` &bull; 4096 tokens for complex architectural reasoning
  - `ai thinking off` &bull; 0 tokens for immediate non-thinking responses

### 3. Natural Model Shorthands
Query models directly or switch default targets without menu navigation:
```bash
# Direct single-line prompts
pro 2.5 "Write a concurrent worker pool in Go"
flash 3.8 "Explain quantum key distribution in 2 sentences"
opus 5.5 "Draft an RFC architecture proposal"
gpt-4o "Analyze this PostgreSQL query plan"

# Switch default model
ai model pro 2.5
ai model flash 3.8
ai model opus 5.5
ai model o3-mini

# Interactive arrow-key model picker
ai model
```

---

## Terminal Economy & Shop System

Persistent financial ledger stored in `localStorage` (`multitool_terminal_wallet`):
- **Live Status Bar Counter**: Displays live user credentials and credit balance (e.g. `user@localhost [500cr]`).
- **Starting Bonus**: New accounts receive 500 CR complimentary starting balance.
- **`bal` / `wallet`**: Displays account balance, player title (`Novice Adventurer`, `Terminal Scavenger`, `High Roller`, `Cyber Tycoon`, `Dungeon Conqueror`), inventory perks, and casino win/loss statistics.
- **`daily`**: Claim 250 CR once every 24 hours (+50 bonus CR for Golden VIP).
- **`work` / `mine`**: Complete 30-second cyber-contracts (smart contract auditing, SHA-256 block mining, zero-day patching) for 65-110 CR.
- **`shop` & `shop buy <id>`**:
  - `[1] Lucky Dice Charm` (150 CR) &bull; +5% probability boost in casino gambling games.
  - `[2] Laser Katana` (300 CR) &bull; +14 ATK in Dungeon Crawler RPG.
  - `[3] Nano Shield` (250 CR) &bull; +8 DEF in Dungeon Crawler RPG.
  - `[4] Health Elixir` (100 CR) &bull; Starts dungeon exploration runs with +60 HP and 2 potions.
  - `[5] Cyber Hacker Badge` (500 CR) &bull; Exclusive terminal title and badge.
  - `[6] Golden VIP Pass` (2000 CR) &bull; `[Golden VIP]` title, +50 daily bonus, 10% casino loss rebate.
  - `[7] Cyber Tycoon License` (5000 CR) &bull; Leaderboard prestige title `[Cyber Tycoon]`.
- **`give` / `pay <user> <amount>`**: Transfer credits to other user profiles.

---

## Casino & Gambling Minigames

- **`slots [bet]` / `slot`**: 3-reel cyberpunk slot machine with reel animations and audio chimes:
  - `[7][7][7]` &bull; **Jackpot 777** (30x payout)
  - `[$][$][$]` &bull; **Triple Dollar** (15x payout)
  - `[BAR][BAR][BAR]` &bull; **Triple Bar** (10x payout)
  - Any pair match &bull; 1.5x payout
- **`blackjack [bet]` / `bj` / `21`**: Turn-based Blackjack vs terminal dealer. Supports `[h]it`, `[s]tand`, `[d]ouble down`, or `[q]uit` with soft-17 dealer rules and 2.5x natural blackjack payout.
- **`roulette <bet> <pick>`**: 37-pocket European roulette wheel (0-36). Supports `red`, `black`, `even`, `odd`, `1-18`, `19-36` (2x) and direct numbers (36x).
- **`coinflip <bet> <h|t>` / `cf`**: 50/50 double-or-nothing coin toss (2x payout).
- **`dicebet <bet> <o|u|7>`**: Roll 2d6 dice: Over 7 (2x), Under 7 (2x), Lucky 7 (5x).

---

## Terminal Games & Entertainment

- **`dungeon` / `crawl` / `rpg`**: Live In-Place ASCII Rogue RPG Dungeon Crawler (5 Procedural Floors):
  - **Live In-Place Board**: Runs live in a single reactive container; no repetitive map printing.
  - **Real-Time Keystroke Controls**: Move and attack instantly using **`[W/A/S/D]`** or **`[Arrow Keys]`** (no Enter required), **`[P]`** to drink potions, and **`[Q / Esc]`** to escape safely with loot.
  - **5 Floors**: *The Catacombs* &rarr; *The Crypt* &rarr; *The Armory* &rarr; *The Nether Depths* &rarr; *The Dragon Sanctum*.
  - **Interactive Objects**: Chests (`$`), Potions (`P`), Dungeon Keys (`K`), Locked Vault Doors (`X`), Weapon Shrines (`W`, +4 ATK), Armor Shrines (`A`, +3 DEF), Spike Traps (`^`), and Stairs (`>`).
  - **Bestiary**: Cave Bats (`B`, 20% dodge), Goblins (`G`), Vipers (`V`), Skeletons (`S`), Orcs (`O`), Nether Demons (`N`), and the Floor 5 **Ancient Nether Dragon [BOSS]** (`D`).
  - **Progression**: Leveling system (Lv.1 to Lv.5+ increases Max HP, ATK, DEF). Defeating the Final Boss awards +500 CR bonus and the `[Nether Slayer]` badge!
- **`snake`**: Real-time ASCII Snake game. Control the snake with Arrow keys or WASD, collect food (`*`), and cash out score for credits (`Score * 4 CR`).
- **`trivia` / `quiz`**: 5-question tech, networking, cybersecurity, and Linux quiz (30 CR per correct answer).
- **`guess` / `guesser`**: Interactive number guessing game (1-100) with hot/cold hints and tiered credit rewards.
- **`hangman`**: Classic ASCII gallows word game with computing vocabulary (60 CR reward).
- **Easter Eggs**: `sudo <cmd>`, `sl` (steam locomotive animation), `cowsay <msg>`, `fortune`, `hack` (Hollywood mainframe breach simulation), `konami` code listener (+1,000 CR bonus), `coffee` (HTTP 418 I'm a teapot), `42`, and `xyzzy`.

---

## Interactive Configuration Menu (`settings`)

Type `settings` or `config` to launch the terminal-native TUI menu:

```
================ MULTITOOL TERMINAL CONFIGURATION MENU (TUI) ================
 [1] AI Providers & API Keys      (Gemini, OpenAI, Claude, OpenRouter, Custom, Pro Priority: ON)
 [2] Active Model Selection       (Switch default model for active provider)
 [3] Visual Appearance            (Themes, Font size in px, CRT scanlines toggle)
 [4] Sound & Bell Effects         (Toggle Web Audio chimes on/off)
 [5] User Profile & Security      (Change username, password, auto-login)
 [6] Reset to Defaults            (Factory reset configuration)
 [0] Exit Settings Menu
=============================================================================
```

CLI Configuration Shortcuts:
```bash
settings list
settings set theme dracula         # macos-dark, dracula, matrix, amber, nord, solarized
settings set fontSize 15
settings set scanlines true        # Toggle CRT phosphor scanline overlay
settings set sound false           # Toggle Web Audio alert chimes
settings set autoLogin true
settings set proPriority true
```

---

## Complete Command Reference

| Category | Commands & Aliases | Description |
| :--- | :--- | :--- |
| **Core & Shell** | `settings`, `banner`, `whoami`, `passwd`, `logout`, `login`, `uptime`, `theme`, `clear`, `history`, `alias`, `save` | Session management, appearance, and shell customization. |
| **AI Assistant** | `ai <query>`, `ai chat`, `ai model`, `ai priority`, `ai thinking`, `pro 2.5`, `flash 3.8`, `opus 5.5`, `gpt-4o` | Multi-provider streaming AI, reasoning latency tuning, model switches. |
| **Economy & Shop** | `bal`, `daily`, `work`, `mine`, `shop [buy <id>]`, `give <user> <amt>` | Currency ledger, 24h rewards, contract mining, gear and perk catalog. |
| **Casino Games** | `slots [bet]`, `blackjack [bet]`, `roulette <bet> <pick>`, `coinflip <bet> <h\|t>`, `dicebet <bet> <o\|u\|7>` | Provably fair gambling minigames with credit rewards and audio chimes. |
| **Terminal Games** | `dungeon`, `snake`, `trivia`, `guess`, `hangman` | Live 5-floor RPG crawler, real-time snake, tech quiz, and word guessing. |
| **Feeds & Network** | `weather [city]`, `crypto [sym]`, `ip`, `dns <dom>`, `whois <dom>`, `cidr <ip/mask>`, `ping <host>`, `curl <url>` | Meteorological forecast, crypto tickers, RDAP whois, and CIDR math. |
| **Diagnostics** | `bench`, `sysinfo`, `matrix`, `ascii <text>` | CPU/Crypto benchmark, hardware platform info, digital rain, and banner art. |
| **Tools & Math** | `math <expr>`, `json <str>`, `jwt <tok>`, `hash [algo] <str>`, `base64 [enc\|dec]`, `uuid`, `diff`, `regex`, `csv`, `wc` | Formula evaluator, JSON/JWT decoder, crypto hashes, regex tester, ASCII tables. |
| **Productivity** | `todo [list\|add\|done]`, `notes [list\|add\|view]`, `timer <sec>`, `stopwatch`, `pomodoro` | Persistent task manager, notebook, stopwatch, and pomodoro timer. |
| **Easter Eggs** | `sudo`, `sl`, `cowsay`, `fortune`, `hack`, `konami`, `coffee`, `42`, `xyzzy` | Classic programmer humor, animations, and retro cheat codes. |

---

## Privacy & Storage

- **Local Storage Only**: All API keys, chat memory, user credentials, notes, tasks, and wallet credits remain strictly within your browser's `localStorage`.
- **No Third-Party Analytics**: Zero tracking pixels, zero analytics scripts, zero external telemetry.
- **Direct API Calls**: When querying AI providers or live feeds, network requests travel directly from your browser to the official provider endpoints (Google, Anthropic, OpenAI, Cloudflare DoH, Open-Meteo).

---

## GitHub Wiki & Releases

For detailed documentation manuals and release archives, explore:
- **[GitHub Wiki Documentation](wiki/Home.md)**:
  - [Getting Started & Installation Guide](wiki/Getting-Started.md)
  - [Complete Command Reference Manual](wiki/Command-Reference.md)
  - [AI Integration & Architecture Guide](wiki/AI-Assistant-Guide.md)
  - [Dungeon Crawler RPG Strategy & Bestiary](wiki/Dungeon-Crawler-RPG.md)
  - [Economy & Casino Probability Guide](wiki/Economy-and-Casino.md)
  - [Customization & Themes Guide](wiki/Customization-and-Themes.md)
- **[GitHub Release Notes Archive](RELEASES.md)**: Ready-to-publish release templates and changelogs.

---

## License

Distributed under the [MIT License](LICENSE). Free for personal and commercial use.
