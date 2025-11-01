# 02 – Game Design (Yekosa Nokosa)

This document expands the **01 – Basic Game Concept** and describes how the game actually works in moment-to-moment gameplay.

---

## 1. Game Goals

### Main goal
Keep **The Mother** alive long enough by defending her from waves of corrupted bug-like enemies.

### Secondary goals
- Collect **shards** from defeated enemies.
- Upgrade weapons.
- Cooperate as two brothers and trigger combo attacks.
- Survive as many waves as possible.

### Win / progression
- Short-term win: survive the current wave.
- Mid-term win: survive several waves in a row (harder enemies, better rewards).
- Long-term win (story): The Mother successfully gives birth to the Savior (end of run).

---

## 2. Player Roles (Co-op Concept)

There are **two brothers**. Both can fight in human form and both can transform.

1. **Brother A(Yekosa) – Runner / Short-range**
   - Stronger at close range and positioning.
   - Can **transform into weapon form**.
   - In weapon form: **can jump and dash, but cannot walk normally**.
   - Can **pick up** the other brother and use him as a weapon.
   - Good for aggressive plays around The Mother.

2. **Brother B(Nokosa) – Gunner / Long-range**
   - Stronger at shooting and covering distance.
   - Can **transform into weapon form**.
   - In weapon form: **can also jump and dash, but cannot walk normally**.
   - In human form, can collect shards and defend too.
   - Some combo attacks are stronger when *he* is the weapon.

> Core co-op idea: **one carries, one empowers** – transformation does not make the player helpless, just tactically limited.

---

## 3. Core Mechanics

### 3.1 Movement
- Human form: classic 2D platformer movement (left / right / jump).
- Transform form: **jump + dash only** (no left/right walk).
- Dash can be used to **reposition quickly** or to get closer to the carrier.
- Gravity-based jumping (Godot default, tuned for action).

### 3.2 Combat
- Basic attack (human): short cooldown, low damage.
- Ranged / special attack (when weapon-brother is equipped): higher damage, cooldown-based or energy-based.
- Combo attack: only possible when one player is carrying the transformed brother.

### 3.3 Transformation Mechanic
- Either player presses the transform key → **enters weapon mode**.
- In weapon mode:
  - movement is **limited to jump and dash**
  - player can still be **picked up**
  - player **provides a weapon** to the carrier
  - player can have **separate upgrades** for weapon mode
- Transformation has a **cooldown** to prevent spamming.
- Design note: limited movement keeps the player active, but still rewards co-op.

### 3.4 Shards & Upgrades
- Every defeated bug has a chance to drop **shards**.
- Shards are the **only currency** in the game.
- Between waves (or at terminals), players can:
  - increase damage
  - unlock new fire modes
  - improve dash / mobility
  - improve defense of The Mother (shields / HP)
  - unlock co-op specific upgrades (e.g. “when carrying your brother, fire rate +20%”)

---

## 4. Core Loop (Moment-to-Moment)

1. **Wave starts** – enemies spawn and head toward The Mother.
2. **Players fight** – move, jump, transform, carry, shoot.
3. **Enemies drop shards** – players collect them.
4. **Wave ends** – short safe phase.
5. **Players buy upgrades** – spend shards.
6. **Next wave starts** – harder enemies / more enemies.

> Loop intention: fast, readable, no long downtime.

---

## 5. Level / Structure

### 5.1 Structure options
For the school version we can keep it **wave-based in one arena**:

- Area 1: tutorial waves (basic bugs, slow)
- Area 2: mix of bugs + flying enemies
- Area 3: elite/boss bug

Later version can be **2D platformer levels** with small arenas.

### 5.2 Difficulty progression
- More enemies per wave
- Faster enemies
- Enemies with shields
- Enemies that attack The Mother from distance
- Enemies that target players first, not The Mother

### 5.3 Boss / Elite idea
- Big corrupted bug that tries to **kill The Mother**
- Players must destroy its weak spot
- Drops a lot of shards
- Good moment to show co-op combo

---

## 6. Enemies

### 6.1 Basic Bug
- Role: cannon fodder
- Behavior: walks straight to The Mother
- Damage: low
- Drop: low shards

### 6.2 Fast Bug
- Role: pressure on players
- Behavior: targets the nearest player
- HP: low
- Drop: medium shards

### 6.3 Ranged Bug
- Role: deny safe spots
- Behavior: stays at distance and shoots corrupt projectiles
- Must be prioritized by players

### 6.4 Corruptor (elite)
- Role: danger for The Mother
- Behavior: tries to infect / drain The Mother
- Needs more DPS → good for co-op combo

(Enemies can be just reskinned / recolored in pixel-art to save time.)

---

## 7. The Mother (Defense Objective)

- Has HP / integrity.
- When HP reaches 0 → **run failed**.
- Can be upgraded (more HP, shield, auto-turret).
- Placed in the middle / back of the level.
- Enemies focus her unless player agro is higher.

---

## 8. UI / HUD

- Top-left: Player 1 HP + current form (human / weapon)
- Top-right: Player 2 HP + current form
- Center-top: wave number / incoming wave
- Shards: shared or per player.
- Bottom: action hints (Press `E` to transform, Press `F` to pick up brother)
- If The Mother is damaged → red warning (“Mother under attack!”)

---

## 9. Controls (PC)

**Player 1 (keyboard + mouse)**
- Move (human): **A / D**
- Jump: **W** or **Space**
- Light attack: **Mouse 1 click**
- Heavy attack / charge: **Mouse 1 hold**
- Transform: **F**
- Interact / Pickup: **E**
- Dash (both forms): **Left Shift**

**Player 2 (controller)**
- Move (human): **Left stick – left/right**
- Jump: **A**
- Light attack: **LT** (or **RB** – to be finalized)
- Heavy attack: **RT**
- Transform: **Y**
- Interact / Pickup: **X**
- Dash (both forms): **B**

> In **weapon form** both players can still **jump** and **dash**, but cannot move left/right normally.  
> This keeps transformed players active and prevents “AFK weapon” gameplay.

---

## 10. Audio & Visual Direction

- **Visuals:** pixel-art, neon, dark background + bright enemies
- **Palette:** purple, magenta, cyan, orange for enemies
- **VFX:** hit flashes, small pixel explosions, screen shake on combo
- **Audio:** synthwave / retrowave loop, short SFX for pickups and shots
- **Feedback:** transformation must have clear sound + effect

---

## 11. Fail States & Restart

- The Mother destroyed → end of run
- Both players dead at the same time → end of run
- After fail → show stats:
  - waves survived
  - shards collected
  - upgrades bought

---

## 12. Future Features (Nice to have)
- Online co-op (not just local)
- More weapon forms per brother
- Skill tree per brother
- Story cutscenes about The Mother
- Endless mode
- Cosmetic unlocks (retro hats, neon capes)

---

## 13. Scope for School Version
- 1 arena
- 3–5 enemy types
- 1 upgrade screen
- local co-op working
- basic Mother HP logic
- simple pixel-art
- Godot 4.5.1, GDScript
