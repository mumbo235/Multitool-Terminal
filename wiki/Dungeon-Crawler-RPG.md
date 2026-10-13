# Dungeon Crawler RPG Strategy & Bestiary Guide

Multitool Terminal includes a built-in, live in-place ASCII Rogue RPG Dungeon Crawler (`dungeon`, `crawl`, `rpg`). Unlike conventional CLI games that repeatedly print ASCII maps to the scrollback buffer, Multitool Terminal renders the dungeon in a real-time reactive container with instant keystroke processing.

---

## Table of Contents

- [Quick Start & Controls](#quick-start--controls)
- [Procedural Floors](#procedural-floors)
- [Tile Legend](#tile-legend)
- [Complete Bestiary](#complete-bestiary)
- [Player Progression & Leveling](#player-progression--leveling)
- [Shop Equipment Synergies](#shop-equipment-synergies)
- [Strategy Guide & Boss Tactics](#strategy-guide--boss-tactics)

---

## Quick Start & Controls

Launch the dungeon crawler by typing:
```bash
dungeon
# Or use aliases:
crawl
rpg
```

### Real-Time Keystroke Controls
Movement and actions occur instantly upon keypress (no Enter key needed):

| Key | Action |
| :--- | :--- |
| **`[W]`** / **`[Up Arrow]`** | Move Up / Attack North |
| **`[A]`** / **`[Left Arrow]`** | Move Left / Attack West |
| **`[S]`** / **`[Down Arrow]`** | Move Down / Attack South |
| **`[D]`** / **`[Right Arrow]`** | Move Right / Attack East |
| **`[P]`** | Drink Healing Potion (+50 HP recovery) |
| **`[Q]`** / **`[Esc]`** | Safe Extraction (Retreat with accumulated loot and credits) |

*Note: Bumping into an enemy automatically initiates an attack turn!*

---

## Procedural Floors

The dungeon descends through 5 progressively hazardous floors:

1. **Floor 1: The Catacombs**
   - Atmosphere: Damp stone hallways with minor vermin.
   - Enemies: Cave Bats (`B`), Goblin Scavengers (`G`).
   - Objects: Gold Chests (`$`), Healing Potions (`P`), Descent Stairs (`>`).

2. **Floor 2: The Crypt**
   - Atmosphere: Ancient burial vaults and poisonous pits.
   - Enemies: Goblin Scavengers (`G`), Pit Vipers (`V`), Skeleton Warriors (`S`).
   - Objects: Weapon Shrine (`W`, +4 ATK permanent boost), Spike Traps (`^`).

3. **Floor 3: The Armory**
   - Atmosphere: Fortified barracks guarded by heavy combatants.
   - Enemies: Skeleton Warriors (`S`), Orc Berserkers (`O`).
   - Objects: Armor Shrine (`A`, +3 DEF permanent boost), Vault Key (`K`).

4. **Floor 4: The Nether Depths**
   - Atmosphere: Molten cavern fissures and demonic entities.
   - Enemies: Orc Berserkers (`O`), Nether Demons (`N`).
   - Objects: Locked Vault Door (`X`), Relic Gold Chest, Descent Stairs to the Sanctum.

5. **Floor 5: The Dragon Sanctum**
   - Atmosphere: Massive obsidian throne room.
   - Enemies: The Ancient Nether Dragon [BOSS] (`D`).
   - Objects: Slaying the dragon yields +500 CR bonus, dungeon victory, and the prestigious `[Nether Slayer]` badge!

---

## Tile Legend

| Glyph | Name | Description |
| :---: | :--- | :--- |
| `@` | **Player Hero** | Your character's position on the board. |
| `#` | **Stone Wall** | Impassable obsidian dungeon perimeter. |
| `.` | **Corridor Path** | Walkable stone flooring. |
| `$` | **Gold Chest** | Contains between 30 and 80 bonus terminal credits. |
| `P` | **Healing Potion** | Collects a potion into your belt. Press `[P]` to drink for +50 HP. |
| `K` | **Dungeon Key** | Required to unlock reinforced Vault Doors (`X`). |
| `X` | **Vault Door** | Locked door guarding secret relic chambers. Unlocks when carrying Key `K`. |
| `W` | **Weapon Shrine** | Ancient altar granting a permanent **+4 ATK** boost. |
| `A` | **Armor Shrine** | Ancient forge granting a permanent **+3 DEF** boost. |
| `^` | **Spike Trap** | Hidden pressure plate dealing 15 unavoidable puncture damage. |
| `>` | **Descent Stairs** | Descends into the next dungeon floor. |
| `B..D` | **Hostile Monsters** | Monsters roam the corridors. Step into their tile to attack. |

---

## Complete Bestiary

| Glyph | Monster Name | HP | ATK | DEF | Special Trait | XP | Bounty |
| :---: | :--- | :---: | :---: | :---: | :--- | :---: | :---: |
| `B` | **Cave Bat** | 22 | 6 | 1 | 20% chance to dodge player attacks | 15 XP | 25 CR |
| `G` | **Goblin Scavenger** | 35 | 10 | 2 | Aggressive low-level mob | 25 XP | 40 CR |
| `V` | **Pit Viper** | 42 | 14 | 3 | Venomous bite piercing defense | 35 XP | 50 CR |
| `S` | **Skeleton Warrior** | 55 | 17 | 5 | Armored bone shield | 50 XP | 65 CR |
| `O` | **Orc Berserker** | 75 | 22 | 7 | Heavy physical cleave | 70 XP | 85 CR |
| `N` | **Nether Demon** | 100 | 28 | 10 | High armor resistance | 100 XP | 120 CR |
| `D` | **Ancient Nether Dragon [BOSS]** | 220 | 36 | 14 | Massive boss health pool & flame strikes | 250 XP | 500 CR + Title |

---

## Player Progression & Leveling

Every monster defeated awards Experience Points (XP). Leveling up permanently increases your combat potential and fully restores your HP:

| Level | XP Threshold | Max HP | Base ATK | Base DEF |
| :---: | :---: | :---: | :---: | :---: |
| **Lv. 1** | 0 XP | 100 HP | 12 ATK | 4 DEF |
| **Lv. 2** | 50 XP | 120 HP | 16 ATK | 6 DEF |
| **Lv. 3** | 120 XP | 140 HP | 20 ATK | 8 DEF |
| **Lv. 4** | 220 XP | 160 HP | 24 ATK | 10 DEF |
| **Lv. 5+** | 350 XP | 180 HP | 28 ATK | 12 DEF |

Combat Damage Calculation:
$$\text{Damage} = \max\left(1, \, \text{Attacker ATK} - \text{Defender DEF} + \text{random}(-2, \, 3)\right)$$

---

## Shop Equipment Synergies

Before embarking on a dungeon run, purchase persistent equipment from the Terminal Shop (`shop`):

1. **Laser Katana** (`shop buy 2`, 300 CR):
   - Adds **+14 ATK** to all player attacks. Allows 1-shotting Bats and Goblins.
2. **Nano Shield** (`shop buy 3`, 250 CR):
   - Adds **+8 DEF** to all incoming monster attacks. Drastically reduces damage taken on Floors 3 and 4.
3. **Health Elixir** (`shop buy 4`, 100 CR):
   - Starts every expedition with **+60 Bonus HP** (160 starting HP) and **2 extra Healing Potions**.

---

## Strategy Guide & Boss Tactics

1. **Clear Floor 1 & 2 for Level Ups**:
   Do not rush down the stairs immediately. Farm Bats and Goblins on Floor 1 to reach Level 2 before descending to Floor 2.
2. **Prioritize Shrines**:
   Never skip Weapon Shrines (`W`) or Armor Shrines (`A`). Their permanent stat boosts are crucial for surviving Floor 4 Nether Demons.
3. **Save Potions for the Nether Dragon**:
   Try to hoard at least 2 or 3 potions before entering Floor 5. Use them when your HP drops below 40.
4. **Know When to Retreat (`[Q]`)**:
   If your HP is under 20 and you have no potions left, press **`[Q]`** or **`[Esc]`**. Safe extraction preserves all credits, XP, and gold accumulated during the run. Dying in combat forfeits that run's collected chest gold!
