# Welcome to the Multitool Terminal Wiki

Welcome to the official documentation wiki for **Multitool Terminal**, an open-source, client-side developer terminal interface running entirely inside any modern web browser. Packaged as a single standalone `index.html` file (~260 KB), Multitool Terminal delivers an authentic fullscreen UNIX terminal environment without any server dependencies, Node.js runtimes, or external build pipelines.

---

## Wiki Navigation Guide

Explore the documentation sections below:

| Page | Description |
| :--- | :--- |
| **[Getting Started](Getting-Started.md)** | Step-by-step launch guide, local web servers, profile setup, and auto-login workflow. |
| **[Command Reference](Command-Reference.md)** | Encyclopedic reference manual covering all 75+ commands, syntax, options, and examples. |
| **[AI Assistant Guide](AI-Assistant-Guide.md)** | Setting up API keys, Gemini Pro Priority architecture, failover routing, and reasoning latency tuning. |
| **[Dungeon Crawler RPG](Dungeon-Crawler-RPG.md)** | Complete strategy guide for the live in-place 5-floor RPG: controls, tile legend, bestiary, and boss mechanics. |
| **[Economy & Casino](Economy-and-Casino.md)** | Credit wallet ledger, 24h daily bonus, cyber-work contracts, shop upgrades, and casino minigame odds. |
| **[Customization & Themes](Customization-and-Themes.md)** | CRT phosphor scanlines, 6 color palettes, Web Audio bells, shell aliases, and TUI configuration menu. |

---

## Key Architectural Principles

1. **Self-Contained Single-File Delivery**:
   The entire application (HTML structure, CSS styles, JavaScript engine, SVG graphics, Web Audio synthesizer, and typography) is bundled inside a single file: `index.html`. You can store it on a USB flash drive, host it on GitHub Pages, or open it directly off your hard drive.

2. **100% Zero-Backend & Privacy-First**:
   Multitool Terminal never sends your session data, history, notes, tasks, or API keys to any proxy server. All data stays strictly inside your browser's private `localStorage`. External network requests (such as AI completions, weather feeds, and DNS queries) are dispatched directly from your browser to official provider endpoints.

3. **Authentic Fullscreen UNIX Aesthetic**:
   There are no faux window title bars, minimize/maximize buttons, or decorative desktop frames. The terminal occupies the full viewport (`100vw` by `100vh`), rendering crisp glowing text, ANSI status chips, and optional CRT scanlines.

4. **Strictly Zero Unicode Emojis**:
   The interface strictly adheres to clean ASCII and UNIX terminal design. Visual indicators use text badges (`[PRO]`, `[OK]`, `[FAIL]`, `[WARN]`, `[INFO]`), bracketed symbols (`[7]`, `[$]`, `[BAR]`, `[A S]`), and standard ASCII punctuation.

5. **Pro Priority AI Resilience**:
   Built for Google AI Pro subscribers: requests default to `gemini-2.5-pro` with Pro tier priority. If rate limits (HTTP 429) or high demand capacity surges (HTTP 503) occur, requests fail over to `gemini-3.8-flash` without demoting the user's saved configuration. Deprecated endpoints (&le; 3.6) are automatically intercepted and upgraded.

---

## How to Sync This Wiki with GitHub

GitHub projects host their wiki documentation in a dedicated Git repository. If you are maintaining the GitHub repository for Multitool Terminal, you can push these wiki files directly to your repository's wiki:

```bash
# 1. Enable the Wiki tab in your GitHub repository settings
# 2. Clone the repository's wiki submodule:
git clone https://github.com/<YOUR_USER>/<YOUR_REPO>.wiki.git wiki-repo

# 3. Copy all files from this wiki/ directory into your cloned wiki repo:
cp -r wiki/* wiki-repo/

# 4. Commit and push:
cd wiki-repo
git add .
git commit -m "docs: sync complete wiki documentation"
git push origin master
```

---

*Need immediate help inside the terminal? Type `help` or `settings` at any prompt.*
