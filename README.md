# Peak of Despair — Cave Climber

Vertical platforming game with dynamic power‑ups, enemy AI, and procedural level generation in Unity/C#.

[![Unity](https://img.shields.io/badge/Unity-6000.0.34f1-black?logo=unity)](https://unity.com/releases/editor/whats-new/6000-0) [![License: GPL v3](https://img.shields.io/badge/License-GPLv3-blue.svg)](LICENSE)

## Table of Contents
- Overview
- Highlights
- Requirements
- Quick Start
- Controls
- Gameplay Details
- Scenes
- Build
- Tech Stack
- Project Structure
- Key Scripts
- License

## Overview
Leap from platform to platform, avoid enemies, collect power‑ups, and climb as high as you can. Score increases with height; fall below the camera and it's game over.

## Highlights
- Procedural level generation with height‑based difficulty scaling
- Multiple platform types (basic, moving, breaking, single‑use, variants)
- Enemies: cavemen on platforms and roaming bats with spawn logic tied to player progress
- Power‑ups: Jump Boost, Speed Boost, Slow Effect, Bat Wings (rapid ascent with animated wings)
- Screen‑wrap horizontal movement, auto‑jump on landing, responsive 2D feel
- Built‑in SFX and music

## Requirements
- Unity Editor: 6000.0.34f1 (Unity 6)
  - See `ProjectSettings/ProjectVersion.txt` for the exact version
- Desktop keyboard controls work out of the box

## Quick Start
1. Clone this repository.
2. Open Unity Hub, add the project folder, and open it with Unity `6000.0.34f1`.
3. Open `Assets/Scenes/MainMenu.unity` and press Play.

## Controls
- Move: A/D or Left/Right Arrow keys
- Attack: Spacebar
- Restart (after Game Over): Enter/Return or Spacebar

Notes:
- The player auto‑jumps upon landing on most platforms.
- Attacking or stomping a caveman defeats it; bats collide physically and can be attacked.
- The camera follows once gameplay starts (first land/bounce).

## Gameplay Details
- Procedural Generation: `Assets/Scripts/LevelGenerator.cs` spawns platforms, enemies, and power‑ups; spacing and spawn rates scale with height for balanced difficulty.
- Enemy AI and Spawning:
  - Cavemen (`EnemyController`) occupy platforms; knockback and bounce logic handled in `PlayerController`.
  - Bats (`BatEnemyController`) are spawned at height intervals with a difficulty‑scaled chance.
- Power‑ups (via `PowerUpManager` and `PlayerController`):
  - Jump Boost: higher bounce for a duration
  - Speed Boost: faster horizontal movement
  - Slow Effect: slows enemies, visual tint applied
  - Bat Wings: animated wings attach and rapidly lift the player
- Scoring (`Assets/Scripts/GameManager.cs`): Height climbed (scaled) plus bonus points for events like defeating enemies.

## Scenes
- `Assets/Scenes/MainMenu.unity` (entry)
- `Assets/Scenes/MainScene.unity` (gameplay)

Both are included in Build Settings by default.

## Build
1. File → Build Settings.
2. Ensure `MainMenu` and `MainScene` are present (default).
3. Select Windows/macOS/Linux and click Build.

## Tech Stack
- Unity 6 (Editor 6000.0.34f1)
- C# (MonoBehaviour‑based gameplay code)
- Packages: 2D feature set, UGUI, Timeline, Visual Scripting, Input System (project still uses `Input.GetAxis`/`GetKeyDown` for desktop play)

## Project Structure
```text
Assets/
  Scenes/               # MainMenu, MainScene
  Scripts/              # Gameplay code (player, enemies, platforms, level gen, UI)
  Prefabs/              # Platforms, enemies, power‑ups
  Art/                  # Visual assets
  SFX/                  # Sounds and music
  Sprite Sheets/        # Sprite sheets and animations
  TextMesh Pro/         # Fonts, materials, and TMP assets
```

## Key Scripts (selected)
- `PlayerController.cs`: Movement, auto‑jump, combat, power‑up visuals/timers, screen wrap
- `GameManager.cs`: Scoring, game over/restart flow, player spawn, menu return
- `LevelGenerator.cs`: Procedural platforms, enemies, power‑ups, difficulty scaling
- `EnemyController.cs`, `BatEnemyController.cs`: Enemy behavior and interactions
- `PlatformManager.cs` and platform scripts: Moving/breaking/single‑use platform logic
- `CameraFollow.cs`: Starts following when gameplay begins
- `PowerUpManager.cs`: Central power‑up state and timers

## License
This project is licensed under the GNU GPL v3.0 — see `LICENSE`.

Note: Third‑party art/audio may have separate licenses. Verify asset licenses in their folders before redistribution.

