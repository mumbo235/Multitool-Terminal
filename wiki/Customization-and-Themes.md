# Customization, Themes & Appearance Guide

Multitool Terminal provides deep visual and behavioral customization options. All settings are persistently stored in your browser's `localStorage` and restored across sessions.

---

## Table of Contents

- [The Settings System](#the-settings-system)
- [Color Themes](#color-themes)
- [CRT Scanlines & Retro Effects](#crt-scanlines--retro-effects)
- [Typography & Font Scaling](#typography--font-scaling)
- [Web Audio Synthesis](#web-audio-synthesis)
- [Shell Aliases](#shell-aliases)
- [Profile & Auto-Login Configuration](#profile--auto-login-configuration)
- [Factory Reset](#factory-reset)

---

## The Settings System

You can configure Multitool Terminal through two methods:

### Method 1: The Interactive TUI Menu (`settings`, `config`)
Type `settings` or `config` to open the terminal-native configuration menu:

```
================ MULTITOOL TERMINAL CONFIGURATION MENU (TUI) ================
 [1] AI Providers & API Keys      (Configure Gemini, OpenAI, Claude, OpenRouter)
 [2] Active Model Selection       (Switch default model for active provider)
 [3] Visual Appearance            (Themes, Font size in px, CRT scanlines toggle)
 [4] Sound & Bell Effects         (Toggle Web Audio chimes on/off)
 [5] User Profile & Security      (Change username, password, auto-login)
 [6] Reset to Defaults            (Factory reset configuration)
 [0] Exit Settings Menu
=============================================================================
Select option [0-6]: 
```

### Method 2: CLI Configuration Commands
Inspect and modify preferences directly without entering menus:

```bash
# List all current preferences
settings list

# Set individual configuration keys
settings set theme dracula
settings set scanlines true
settings set fontSize 15
settings set sound false
settings set autoLogin true
settings set proPriority true
```

---

## Color Themes

Multitool Terminal includes 6 carefully balanced monospace color palettes:

| Theme Name | Background | Primary Foreground | Accent Highlights |
| :--- | :---: | :---: | :---: |
| **`macos-dark`** | `#1e1e1e` | `#d4d4d4` Slate | `#3b82f6` Blue & `#10b981` Emerald |
| **`dracula`** | `#282a36` | `#f8f8f2` Cream | `#bd93f9` Purple & `#ff79c6` Pink |
| **`matrix`** | `#0d1117` | `#00ff66` Phosphor | `#39ff14` Neon Green |
| **`amber`** | `#1a1100` | `#ffb000` Amber | `#ffcc00` Bright Gold |
| **`nord`** | `#2e3440` | `#eceff4` Frost White | `#88c0d0` Glacier Teal |
| **`solarized`** | `#002b36` | `#839496` Base00 | `#2aa198` Cyan & `#b58900` Yellow |

### Switching Themes
```bash
# Quick theme switcher
theme dracula
theme matrix
theme amber
theme nord
theme solarized
theme macos-dark

# View available themes
theme
```

---

## CRT Scanlines & Retro Effects

To experience an authentic 1980s phosphor monitor aesthetic, enable the CRT scanlines overlay:

```bash
# Enable CRT phosphor scanlines
settings set scanlines true

# Disable CRT scanlines (clean flat panel display)
settings set scanlines false
```

When enabled:
- A hardware-accelerated SVG scanline raster is overlaid across the entire terminal canvas.
- A subtle radial vignette simulates the curved glass of a vintage cathode-ray tube.
- Terminal text emits a subtle phosphor glow effect.

---

## Typography & Font Scaling

Multitool Terminal renders in high-legibility monospace fonts (`Fira Code`, `JetBrains Mono`, `Cascadia Code`, `Source Code Pro`, `Consolas`, `monospace`).

You can adjust font sizing dynamically without zooming your entire browser window:

```bash
# Set font size to 14 pixels
settings set fontSize 14

# Set font size to 16 pixels
settings set fontSize 16

# Minimum: 11px | Maximum: 24px
```

---

## Web Audio Synthesis

Audio feedback for casino minigames, slot reels, dice rolls, and countdown timers uses the browser's built-in Web Audio API:
- **Zero Audio Assets**: Sounds are procedurally synthesized using oscillators and gain envelopes.
- **Toggle Sound**:
  ```bash
  # Mute all terminal sounds
  settings set sound false

  # Enable sound chimes
  settings set sound true
  ```

---

## Shell Aliases

Create custom command shortcuts to speed up daily workflows:

```bash
# List all active aliases
alias

# Create aliases
alias ll="sysinfo"
alias c="clear"
alias roll="dicebet 50 7"
alias ask="ai"
alias fastai="pro 2.5"
```
Aliases are saved to your user profile and persist across browser reloads.

---

## Profile & Auto-Login Configuration

Manage your local developer account:

### Passwordless Authentication
- When creating an account or updating via `passwd`, leaving the password blank configures passwordless login.
- When `autoLogin` is enabled (default: `true`), refreshing the browser page automatically restores your authenticated session without prompting for credentials.

### Disabling Auto-Login
If sharing a workstation and requiring manual authentication on every reload:
```bash
settings set autoLogin false
# Or via TUI settings -> [5] User Profile & Security -> Auto-Login: OFF
```

---

## Factory Reset

If you wish to wipe local preferences, stored wallets, and chat transcripts:
1. Type `settings` and select `[6] Reset to Defaults`.
2. Confirm the reset prompt.
3. Alternatively, clear your browser's site data / `localStorage` for the application domain.
