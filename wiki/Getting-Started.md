# Getting Started with Multitool Terminal

Multitool Terminal is engineered for immediate, friction-free deployment. There are no build tools to compile, no npm dependencies to install, and no backend servers to configure.

---

## System Requirements

- Any modern web browser with HTML5 and ES2022 support:
  - Google Chrome / Chromium &bull; v90+
  - Mozilla Firefox &bull; v88+
  - Apple Safari &bull; v15+
  - Microsoft Edge &bull; v90+
  - Brave, Opera, Vivaldi &bull; Current versions
- Local storage enabled (`localStorage` is required for profiles, wallet balances, notes, and API keys).
- Internet access is optional. Offline tools (math, hashes, regex, base64, snake, dungeon, trivia) function completely offline.

---

## Launch Options

### Method 1: Direct File Launch (No Server Required)
Simply double-click `index.html` in your file manager or launch it from your operating system shell:

```bash
# Linux
xdg-open index.html

# macOS
open index.html

# Windows
start index.html
```

### Method 2: Local Static Server (Recommended)
Running through a local web server allows all browser Web APIs (including clipboard permissions and Web Workers) to operate without browser file-scheme sandbox restrictions.

```bash
# Python 3
python3 -m http.server 8080

# Node.js
npx serve -l 8080

# PHP CLI
php -S localhost:8080

# Ruby
ruby -run -ehttpd . -p8080
```
Once started, open `http://localhost:8080` in your web browser.

### Method 3: GitHub Pages Deployment
Because Multitool Terminal is packaged as a single static `index.html` file, hosting it on GitHub Pages takes under a minute:
1. Push `index.html` to the root of your GitHub repository.
2. In your repository settings, go to **Settings** &rarr; **Pages**.
3. Under **Build and deployment**, select **Source: Deploy from a branch**.
4. Choose the `main` branch and `/ (root)` folder, then click **Save**.
5. Your terminal will be live at `https://<YOUR-USERNAME>.github.io/<YOUR-REPO>/`.

---

## First Run & Session Authentication

When launching Multitool Terminal for the first time, you will be prompted to create your developer profile:

```
[SYSTEM] No user profile detected.
Enter desired username: dev
Enter password (optional - press Enter to skip for passwordless login): 
```

### Passwordless Auto-Login
- **Skip the Password**: If you leave the password blank during account creation, your profile is configured for seamless passwordless authentication.
- **Persistent Sessions**: Subsequent visits and browser page reloads automatically bypass the login screen and drop you directly at your active terminal prompt (`dev@localhost:~$`).
- **Changing Passwords**: Use the `passwd` command at any time to set, change, or remove a password.
- **Toggling Auto-Login**: Auto-login behavior can be toggled in the configuration menu via `settings` &rarr; `[5] User Profile & Security` or via the CLI command `settings set autoLogin true|false`.
- **Switching Accounts**: To sign out or change users, type `logout`. To log back in under another profile, type `login <username>`.

---

## Command Autocomplete

Typing inside the terminal is accelerated by an inline ghost text autocomplete engine:

1. **Type a Prefix**: As you type (e.g., `slo`), the closest matching command appears in dim grey inline right on the text line (e.g. `slots`).
2. **Accept with Tab**: Press **`[Tab]`** or **`[Right Arrow]`** to accept and complete the suggestion into your input buffer.
3. **Session History Support**: Recent commands from your session history are prioritized for fast recall.
4. **Dismissal**: Press **`[Esc]`** or backspace to clear the suggestion.

---

## Essential First Commands

To get familiar with the terminal, try running these commands in sequence:

```bash
# 1. View the compact dashboard help manual
help

# 2. Check your wallet balance and player title (500 CR initial grant)
bal

# 3. Claim your daily credit allowance (250 CR)
daily

# 4. Open the TUI settings menu
settings

# 5. Launch the live 5-floor Rogue RPG dungeon crawler
dungeon

# 6. Check live system metrics and hardware info
sysinfo
```

Next, proceed to the **[Command Reference](Command-Reference.md)** for detailed coverage of all 75+ utilities.
