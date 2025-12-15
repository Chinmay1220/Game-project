# Ashen Bonds

Ashen Bonds is a top-down action-adventure game built in **Unreal Engine**, focused on fast-paced melee combat, enemy waves, and a boss reveal system. The project is implemented entirely using **Blueprints**, emphasizing modular gameplay systems and animation-driven combat.

---

## 🎮 Game Overview

Ashen Bonds follows a young boy whose life is shattered by a mysterious and violent force. Left alone amid destruction, he embarks on a path of revenge, fighting through hostile dojos and enemies. Each level challenges the player to defeat all enemies before progressing, culminating in a boss encounter that tests mastery of combat mechanics.

---

## 🛠️ Setup Instructions

### Requirements
- Unreal Engine **5.6**
- Windows 10 / 11
- DirectX 12–compatible GPU
- Minimum 8 GB RAM (16 GB recommended)

### Running the Project
1. Clone or download the project repository.
2. Open **Unreal Engine 5.6**.
3. Click **Browse** and select the project folder.
4. Open the main level (e.g., `LVL_TopDown`).
5. Press **Play** in the editor or package the project for Windows.

---

## 🎹 Controls

| Action  | Input |
|-------|------|
| Move | WASD / Arrow Keys |
| Attack / Punch | Left Mouse Button |
| Kick | Secondary Attack Key |
| Camera | Fixed Top-Down |
| Interaction | Automatic (collision-based) |

---

## ⚔️ Core Gameplay Features

### Player
- Health system with UI health bar
- Melee combat using animation montages
- Timed attack hitbox for accurate damage detection
- Blueprint-based input handling

### Enemies
- Health-based enemies (default: 3 hits)
- `TakeHit(Damage)` custom event
- Automatic destruction when health reaches zero
- Each enemy notifies the spawner on death

### Boss System
- Enemies are counted at level start
- Boss spawns **only after all enemies are defeated**
- Boss appears at a predefined spawn point
- Boss class is configurable via Blueprint variables

---

## 🧩 Blueprint Architecture

### BP_TopDownCharacter
- Handles movement and player input
- Plays attack animations using montages
- Enables/disables attack hitbox during animations
- Communicates damage through collision overlaps

### BP_Enemy
- Contains Health variable
- Implements `TakeHit(Damage)` custom event
- Calls `EnemyDied` on the boss spawner before destroying itself

### BP_BossSpawner
- Counts enemies on BeginPlay
- Tracks remaining enemies (`EnemiesLeft`)
- Spawns the boss when `EnemiesLeft <= 0`
- Uses a Scene Component (`BossSpawnPoint`) for spawn location

### Animation System
- Uses Animation Blueprints for locomotion
- Attack animations are played via Montages
- Slot (`DefaultSlot`) is added in AnimGraph to allow montage playback
- Combat animations are synchronized with hitbox collision windows

---

## 📦 Dependencies

- Unreal Engine 5.6
- Unreal Engine Blueprint system
- Default UE skeletal mesh and animation framework

Optional:
- Unreal Marketplace assets
- Free environment and character packs

---

## 📁 Project Structure (Simplified)

