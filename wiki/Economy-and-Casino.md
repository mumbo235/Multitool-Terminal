# Terminal Economy & Casino Guide

Multitool Terminal features an integrated virtual economy system with a persistent credit ledger, daily allowances, cyber-mining contracts, an equipment shop, and provably fair casino minigames.

---

## Table of Contents

- [Wallet Ledger & Starting Bonus](#wallet-ledger--starting-bonus)
- [Player Titles & Status Tiers](#player-titles--status-tiers)
- [Income Methods](#income-methods)
- [Terminal Shop Catalog](#terminal-shop-catalog)
- [Casino Minigames & Probability Tables](#casino-minigames--probability-tables)
- [Audio & Bell Synthesis](#audio--bell-synthesis)

---

## Wallet Ledger & Starting Bonus

All financial transactions are stored in your browser's private `localStorage` under the key `multitool_terminal_wallet`.

- **Complimentary Starting Bonus**: Every newly created user profile receives an automatic **500 CR** starter grant.
- **Status Bar Display**: Your active balance is shown in the persistent status bar and prompt:
  ```
  dev@localhost [500cr] :~$
  ```
- **Checking Account Status**: Run `bal` or `wallet` to inspect your balance, title tier, inventory perks, and casino ledger win/loss statistics:
  ```
  [WALLET] Account: dev
  [STATUS] Title: Terminal Scavenger
  [CREDITS] 1,240 CR
  [PERKS] Lucky Dice Charm (+5% Casino Luck), Laser Katana (+14 ATK)
  [RECORD] Wins: 14 | Losses: 9 | Net Casino Profit: +420 CR
  ```

---

## Player Titles & Status Tiers

Your title automatically progresses as your net worth increases:

| Title | Net Worth Required | Privileges |
| :--- | :---: | :--- |
| `[Novice Adventurer]` | 0 - 499 CR | Standard shell permissions |
| `[Terminal Scavenger]` | 500 - 1,499 CR | Standard shell permissions |
| `[High Roller]` | 1,500 - 4,999 CR | High roller status badge |
| `[Cyber Tycoon]` | 5,000+ CR | Highest wealth status tier |
| `[Nether Slayer]` | Boss Slayed | Awarded by defeating the Floor 5 Dungeon Dragon |
| `[Golden VIP]` | Shop Item #6 | +50 daily bonus, 10% casino loss rebate |

---

## Income Methods

### 1. Daily Allowance (`daily`)
Claim **250 CR** once every 24 hours. If you hold the Golden VIP Pass, you receive an extra +50 CR bonus (300 CR total per day).

### 2. Cyber-Contracts & Mining (`work`, `mine`)
Complete 30-second cyber-contracts to generate credits without risk:
- Types of tasks: SHA-256 block proof-of-work mining, zero-day patching, smart contract auditing.
- Reward: **65 to 110 CR** per successful contract.
- Cooldown: 30 seconds.

### 3. Dungeon RPG Loot (`dungeon`)
- Gold Chests (`$`): Contain **30 to 80 CR** each.
- Monster Bounties: Defeating enemies awards 25 to 120 CR upon victory.
- Nether Dragon Bounty: Defeating the final boss awards **+500 CR**.

### 4. Arcade Games
- `snake`: Cash out your score for credits: `Score * 4 CR`.
- `trivia`: Earn **30 CR** per correct multiple-choice answer.
- `guess`: Earn up to **100 CR** based on how few guesses you need.
- `hangman`: Win **60 CR** upon completing a word puzzle.

### 5. Peer-to-Peer Transfers (`give`, `pay`)
Transfer credits to another user profile on the same machine:
```bash
give alice 200
pay bob 50
```

---

## Terminal Shop Catalog

Browse the catalog by typing `shop`. Purchase items using `shop buy <id>`:

| ID | Item Name | Price | Effect / Advantage |
| :---: | :--- | :---: | :--- |
| `[1]` | **Lucky Dice Charm** | 150 CR | Grants **+5% probability boost** across all casino games. |
| `[2]` | **Laser Katana** | 300 CR | Grants **+14 ATK** in the Dungeon Crawler RPG. |
| `[3]` | **Nano Shield** | 250 CR | Grants **+8 DEF** in the Dungeon Crawler RPG. |
| `[4]` | **Health Elixir** | 100 CR | Starts dungeon runs with **+60 HP** and **2 healing potions**. |
| `[5]` | **Cyber Hacker Badge** | 500 CR | Unlocks the prestigious `[Cyber Hacker]` badge in prompt. |
| `[6]` | **Golden VIP Pass** | 2,000 CR | `[Golden VIP]` title, +50 daily bonus, 10% casino loss rebate. |
| `[7]` | **Cyber Tycoon License** | 5,000 CR | Elite prestige title `[Cyber Tycoon]`. |

---

## Casino Minigames & Probability Tables

### 1. 3-Reel Cyberpunk Slots (`slots [bet]`)
Simulates a classic mechanical 3-reel slot machine with animated reel spinning and audio chimes.

```
+-----+-----+-----+
|  7  |  7  |  7  |  --> JACKPOT 777 (30x Payout!)
+-----+-----+-----+
```

| Match | Combination | Payout Multiplier |
| :--- | :---: | :---: |
| **Jackpot 777** | `[7][7][7]` | **30x** bet |
| **Triple Dollar** | `[$][$][$]` | **15x** bet |
| **Triple Bar** | `[BAR][BAR][BAR]` | **10x** bet |
| **Two Matching** | Any pair | **1.5x** bet |

### 2. Blackjack 21 (`blackjack [bet]`)
A full turn-based implementation of casino Blackjack against the terminal dealer:
- **Dealer Rules**: Dealer must hit on 16 and stand on soft 17.
- **Controls**:
  - `[h]`: Hit (receive 1 card)
  - `[s]`: Stand (end turn)
  - `[d]`: Double Down (double initial bet, draw exactly 1 card, and stand)
  - `[q]`: Surrender / Quit
- **Payouts**:
  - Natural Blackjack (Ace + 10-value card): **2.5x** payout (3:2)
  - Standard Win: **2x** payout (1:1)
  - Push / Tie: Bet returned

### 3. European Roulette (`roulette <bet> <pick>`)
Standard 37-pocket European roulette wheel (numbers 0 to 36):

| Bet Type | Valid Inputs | Payout | Win Probability |
| :--- | :--- | :---: | :---: |
| **Color** | `red`, `black` | 2x | 18/37 (48.6%) |
| **Parity** | `even`, `odd` | 2x | 18/37 (48.6%) |
| **Range** | `1-18`, `19-36` | 2x | 18/37 (48.6%) |
| **Straight Up** | `0` through `36` | 36x | 1/37 (2.7%) |

### 4. Coinflip (`coinflip <bet> <h|t>`)
A pure 50/50 double-or-nothing coin toss:
- Bet options: `h` (Heads) or `t` (Tails)
- Payout: **2x** bet on match

### 5. Dicebet (`dicebet <bet> <o|u|7>`)
Rolls two 6-sided dice (2d6, totals 2 to 12):
- `o` (Over 7: totals 8, 9, 10, 11, 12): **2x** payout (41.7% probability)
- `u` (Under 7: totals 2, 3, 4, 5, 6): **2x** payout (41.7% probability)
- `7` (Lucky Seven: total 7): **5x** payout (16.7% probability)

---

## Audio & Bell Synthesis

Casino wins, slot reels, and timer alerts use the browser's native **Web Audio API** (`AudioContext`) to generate retro synthesized chimes and bells:
- Zero external MP3 or audio asset downloads required.
- Sound can be toggled on or off at any time using:
  ```bash
  settings set sound false
  # Or via TUI settings -> [4] Sound & Bell Effects
  ```
