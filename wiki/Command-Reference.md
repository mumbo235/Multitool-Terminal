# Multitool Terminal Command Reference Manual

This manual provides the complete, authoritative specification for all commands and built-in utilities available in **Multitool Terminal**.

---

## Table of Contents

- [Core Shell & Session](#core-shell--session)
- [AI Assistant & Reasoning](#ai-assistant--reasoning)
- [Economy & Shop](#economy--shop)
- [Casino Minigames](#casino-minigames)
- [Terminal Games](#terminal-games)
- [Feeds & Network Probes](#feeds--network-probes)
- [Diagnostics & Benchmarking](#diagnostics--benchmarking)
- [Developer Tools & Cryptography](#developer-tools--cryptography)
- [Productivity & Timers](#productivity--timers)
- [Easter Eggs](#easter-eggs)

---

## Core Shell & Session

### `help [category]`
Displays the single-screen dashboard overview or category-specific manual.
- **Syntax**: `help` or `help <core|ai|games|tools|net>`
- **Examples**:
  ```bash
  help
  help ai
  help games
  ```

### `settings [list | set <key> <val>]` (Alias: `config`)
Opens the interactive TUI configuration menu or reads/writes preferences directly from the CLI.
- **Syntax**: `settings` (interactive) or `settings list` or `settings set <key> <val>`
- **Configurable Keys**: `theme`, `fontSize`, `scanlines`, `sound`, `autoLogin`, `proPriority`
- **Examples**:
  ```bash
  settings
  settings list
  settings set theme dracula
  settings set scanlines true
  settings set fontSize 16
  ```

### `banner`
Renders the compact ASCII art startup logo and system version banner.

### `whoami`
Prints the current logged-in username, IP address, and browser platform environment.

### `passwd`
Interactively updates or clears the current user profile's password. Pressing Enter with a blank string enables passwordless login.

### `logout`
Ends the current authenticated session and displays the login screen.

### `login [user]`
Initiates session authentication for the specified username.

### `uptime`
Reports total elapsed time since the current terminal session was initialized in the browser.

### `theme [name]`
Lists all installed color themes or switches to a specified palette.
- **Available Themes**: `macos-dark`, `dracula`, `matrix`, `amber`, `nord`, `solarized`
- **Examples**:
  ```bash
  theme
  theme matrix
  theme amber
  ```

### `clear` (Alias: `cls`)
Clears the active scrollback buffer while preserving session state, aliases, and active background timers.

### `history`
Prints a numbered list of all previously executed command lines in the current session.

### `alias [name=cmd]`
Lists active aliases or creates a new command shortcut.
- **Examples**:
  ```bash
  alias
  alias ll="sysinfo"
  alias roll="dicebet 50 7"
  ```

### `save [filename]`
Exports the entire scrollback buffer as a downloadable plain-text (`.txt`) log file.

---

## AI Assistant & Reasoning

### `ai <query>`
Streams an AI completion from the currently active model provider.
- **Syntax**: `ai <prompt text>`
- **Examples**:
  ```bash
  ai What is the difference between mutexes and semaphores?
  ai Write a Python script to parse access logs using regex.
  ```

### `ai chat`
Enters persistent conversational mode where message context is preserved between consecutive prompts until dismissed with `exit`.

### `ai model [name]`
Opens the interactive arrow-key model selector or directly switches the default target model.
- **Examples**:
  ```bash
  ai model
  ai model gemini-2.5-pro
  ai model gemini-3.8-flash
  ai model claude-3-7-sonnet
  ```

### `ai priority [on|off]`
Toggles Google Gemini Pro priority tier. When enabled, requests automatically prioritize `gemini-2.5-pro` with automatic failover to `gemini-3.8-flash` on HTTP 429/503.

### `ai thinking <fast|balanced|deep|off>`
Adjusts the thinking token budget for Google Gemini 2.5 Pro:
- `fast`: 512 tokens &bull; Instant interactive streaming
- `balanced`: 1024 tokens &bull; Default balance of reasoning depth and speed
- `deep`: 4096 tokens &bull; Full chain-of-thought analysis for complex architecture
- `off`: 0 tokens &bull; Raw direct generation without pre-computation delay

### Model Shorthands (`pro`, `flash`, `opus`, `gpt-4o`)
Directly prompt or target specific models without switching global settings:
```bash
pro 2.5 "Refactor this SQL join"
flash 3.8 "Summarize CAP theorem"
opus 5.5 "Draft an RFC specification"
gpt-4o "Explain zero-knowledge rollups"
```

---

## Economy & Shop

### `bal` (Alias: `wallet`)
Displays your current credit balance, player title, VIP status, inventory perks, and casino ledger win/loss statistics.

### `daily`
Claims the 24-hour credit grant (250 CR, +50 CR bonus for Golden VIP pass holders).

### `work` (Alias: `mine`)
Accepts a 30-second cyber-contract (e.g. SHA-256 block mining, smart contract auditing, vulnerability scanning) to earn 65 to 110 CR.

### `shop [buy <id>]`
Displays the equipment and perk catalog or purchases an item:
- `[1] Lucky Dice Charm` (150 CR) &bull; +5% casino win probability boost
- `[2] Laser Katana` (300 CR) &bull; +14 ATK in Dungeon Crawler RPG
- `[3] Nano Shield` (250 CR) &bull; +8 DEF in Dungeon Crawler RPG
- `[4] Health Elixir` (100 CR) &bull; Start dungeon crawler with +60 HP and 2 healing potions
- `[5] Cyber Hacker Badge` (500 CR) &bull; Grants terminal badge and title `[Cyber Hacker]`
- `[6] Golden VIP Pass` (2000 CR) &bull; Grants `[Golden VIP]` title, +50 daily bonus, 10% casino loss rebate
- `[7] Cyber Tycoon License` (5000 CR) &bull; Grants prestigious status title `[Cyber Tycoon]`

### `give <user> <amount>` (Alias: `pay`)
Transfers credits from your wallet to another registered user account.

---

## Casino Minigames

### `slots [bet]` (Alias: `slot`)
Plays a 3-reel cyberpunk slot machine with reel animations and audio bells.
- **Payout Table**:
  - `[7][7][7]` &bull; Jackpot 777 (30x bet)
  - `[$][$][$]` &bull; Triple Dollar (15x bet)
  - `[BAR][BAR][BAR]` &bull; Triple Bar (10x bet)
  - Any two matching symbols &bull; 1.5x bet

### `blackjack [bet]` (Alias: `bj`, `21`)
Starts an interactive Blackjack game vs the terminal dealer.
- **Controls**:
  - `[h]` &bull; Hit (draw card)
  - `[s]` &bull; Stand (end turn)
  - `[d]` &bull; Double Down (double bet and receive exactly 1 card)
  - `[q]` &bull; Quit / Surrender
- **Rules**: Dealer stands on soft 17. Natural blackjack pays 2.5x.

### `roulette <bet> <pick>`
Plays 37-pocket European roulette (numbers 0 to 36).
- **Available Picks**:
  - `red` / `black` (2x)
  - `even` / `odd` (2x)
  - `1-18` / `19-36` (2x)
  - `0` through `36` (36x)

### `coinflip <bet> <h|t>` (Alias: `cf`)
Flips a provably fair 50/50 double-or-nothing coin toss (2x payout).

### `dicebet <bet> <o|u|7>`
Rolls two 6-sided dice (2d6):
- `o` (Over 7) &bull; 2x payout
- `u` (Under 7) &bull; 2x payout
- `7` (Lucky Seven) &bull; 5x payout

---

## Terminal Games

### `dungeon` (Aliases: `crawl`, `rpg`)
Launches the Live In-Place 5-Floor Rogue RPG Crawler.
- **Live In-Place Rendering**: Operates in a dedicated, reactive screen frame without repeating map output.
- **Real-Time Key Controls**:
  - `[W / Up]` &bull; Move Up
  - `[A / Left]` &bull; Move Left
  - `[S / Down]` &bull; Move Down
  - `[D / Right]` &bull; Move Right
  - `[P]` &bull; Drink Healing Potion (+50 HP)
  - `[Q / Esc]` &bull; Safe Escape (bank earned gold and loot)
- **5 Procedural Floors**:
  - Floor 1: *The Catacombs*
  - Floor 2: *The Crypt*
  - Floor 3: *The Armory*
  - Floor 4: *The Nether Depths*
  - Floor 5: *The Dragon Sanctum* (Boss Battle)
- **Map Tiles**:
  - `@`: Player
  - `#`: Stone Wall
  - `.`: Floor Path
  - `$`: Gold Chest
  - `P`: Healing Potion
  - `K`: Vault Key
  - `X`: Locked Vault Door
  - `W`: Weapon Shrine (+4 ATK)
  - `A`: Armor Shrine (+3 DEF)
  - `^`: Hidden Spike Trap (15 DMG)
  - `>`: Descent Stairs
  - `B`, `G`, `V`, `S`, `O`, `N`, `D`: Enemies

### `snake`
Interactive ASCII Snake arcade game. Steer with WASD or Arrow keys. Cash out score for credits (`Score * 4 CR`).

### `trivia` (Alias: `quiz`)
5-question multiple-choice technical quiz covering networking, cryptography, Linux, and programming. Awards 30 CR per correct answer.

### `guess` (Alias: `guesser`)
Interactive number guessing game between 1 and 100 with hot/cold proximity hints and tiered credit rewards.

### `hangman`
Classic word guessing game with vocabulary drawn from computing and engineering. Awards 60 CR upon victory.

---

## Feeds & Network Probes

### `weather [city]`
Fetches meteorological conditions and multi-day forecasts via Open-Meteo. Defaults to auto-detected IP geolocation.

### `crypto [symbol]`
Retrieves live market prices and 24-hour percentage deltas for cryptocurrencies (BTC, ETH, SOL, DOGE, etc.).

### `ip`
Queries public IP information, ISP details, and geographic coordinates via client-side Web API.

### `dns <domain> [type]`
Performs DNS lookups (A, AAAA, MX, TXT, CNAME) using Cloudflare DNS-over-HTTPS.

### `whois <domain>`
Performs RDAP whois lookups to retrieve registrar, creation dates, and registration status.

### `cidr <ip/mask>`
Calculates subnet network address, broadcast address, netmask, wildcard mask, and usable host count.
- **Example**: `cidr 192.168.1.0/24`

### `ping <host>`
Estimates network round-trip latency to a host via browser fetch timing.

### `curl <url>`
Dispatches a GET request and renders headers, status codes, and response body.

---

## Diagnostics & Benchmarking

### `bench`
Executes an in-browser CPU performance benchmark evaluating floating-point arithmetic, array operations, and cryptographic hashing.

### `sysinfo`
Displays browser platform, user agent, screen resolution, hardware concurrency, and device memory.

### `matrix`
Displays a full-viewport digital rain animation inspired by the Matrix. Press any key or `q` to exit.

### `ascii <text>`
Renders text into an ASCII art banner using a 5-row monospace glyph set.
- **Example**: `ascii CYBER`

---

## Developer Tools & Cryptography

### `math <expression>`
Evaluates mathematical expressions with trigonometric functions, powers, logarithms, and constants.
- **Example**: `math 2^16 * sin(pi/4)`

### `json <string>`
Validates and pretty-prints JSON strings with indentation and syntax highlighting.

### `jwt <token>`
Decodes and formats JSON Web Token header and payload claims without verifying signature.

### `hash [algo] <string>`
Computes cryptographic digests. Supports `sha256` (default), `sha512`, `sha384`, `sha1`, and `md5`.
- **Example**: `hash sha256 password123`

### `base64 <enc|dec> <string>`
Encodes or decodes text to/from Base64.
- **Example**: `base64 enc "Hello World"`

### `uuid`
Generates a random RFC-4122 version 4 UUID.

### `diff <text1> <text2>`
Displays a line-by-line comparison highlighting additions and deletions.

### `regex <pattern> <string>`
Evaluates a regular expression pattern against a string and highlights all matches and capture groups.

### `csv <csv_text>`
Parses comma-separated text and renders it as an aligned ASCII table.

### `wc <text>`
Counts characters, words, and lines in the provided text.

---

## Productivity & Timers

### `todo [list | add <text> | done <id> | clear]`
Persistent task manager stored in `localStorage`.
- **Examples**:
  ```bash
  todo add "Deploy updated index.html"
  todo list
  todo done 1
  ```

### `notes [list | add <title> <body...> | view <id> | clear]`
Persistent scratchpad for code snippets and notes.
- **Examples**:
  ```bash
  notes add "API Keys" "Gemini pro key saved in settings"
  notes list
  notes view 1
  ```

### `timer <seconds>`
Starts a countdown timer with audio chime upon completion.

### `stopwatch`
Interactive stopwatch measuring elapsed time with split lap capability.

### `pomodoro`
25-minute focused work interval timer followed by a 5-minute break chime.

---

## Easter Eggs

- `sudo <cmd>` &bull; Humorous permission error message.
- `sl` &bull; Animated ASCII steam locomotive driving across the screen.
- `cowsay <msg>` &bull; Classic ASCII cow delivering your message in a speech bubble.
- `fortune` &bull; Displays a classic hacker aphorism or programming quote.
- `hack` &bull; Hollywood mainframe breach animation sequence.
- `konami` &bull; Triggers the retro cheat sequence for +1,000 CR bonus.
- `coffee` &bull; Returns HTTP status `418 I'm a teapot`.
- `42` &bull; The Answer to the Ultimate Question of Life, the Universe, and Everything.
- `xyzzy` &bull; Classic text adventure homage ("Nothing happens.").
