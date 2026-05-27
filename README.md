# S.P.A.C.E. SHOOTER

## Demo Video
https://github.com/user-attachments/assets/2854d87e-1af7-4665-b022-fa39ef071a55

## Brief single-paragraph description
-------------------------------
S.P.A.C.E. SHOOTER is a top-down arcade-style Unity prototype where the player pilots a spaceship to survive increasingly difficult waves of enemies, collect orbs (in-game currency), and purchase upgrades between waves. The project demonstrates basic gameplay systems: wave spawning, object pooling, a simple shop, local high-score persistence (JSON), and an assortment of SFX and sprites.

## Project details
---------------
- Unity Editor version: 2019.1.14f1 (see `ProjectSettings/ProjectVersion.txt`).
- Main scene: `Assets/Scenes/SampleScene.unity`.
- Scripts are in `Assets/Resources/Scripts/` and implement gameplay systems: player, enemies, spawner, shop, highscores, UI, and object pooling.

## Playable controls
-----------------
- Movement: WASD (or arrow keys)
- Aim / rotation: Mouse
- Fire bullets: Left mouse button
- Fire rockets: Right mouse button
- Pause / Menu: Escape

## Gameplay summary
----------------
- Players survive timed waves managed by `GameSystem.cs` and `EnemySpawner.cs`.
- Enemies drop `Orb` pickups; orbs are used as currency in the `Shop`.
- Between waves the player can buy upgrades: more rockets, restock rockets, restock lives, increase shield, and decrease shield recharge time.

## Enemy types (implemented scripts)
--------------------------------
- `NormalEnemy` / `NormalEnemyBullet` — basic shooter enemy.
- `ChaserEnemy` — follows the player and explodes on contact.
- `ChargerEnemy` — stronger chaser that performs charge attacks.
- `LaserEnemy` — fires lasers and can hit through space.
- `Asteroid` — free-moving hazards that damage heavily on collision.

## Key systems & scripts
---------------------
- `GameSystem.cs` — Manages game states (MainMenu, Waves, Shop, Highscores).
- `EnemySpawner.cs` — Controls wave composition and spawn timing.
- `ObjectPool.cs` — Pooling for bullets, rockets, enemies, and effects to reduce costly Instantiate/Destroy calls.
- `Player.cs`, `Projectile.cs`, `Rocket.cs` — Player input, shooting, and projectile behavior.
- `Shop.cs`, `ShopItem.cs`, `ShopUpgradeShield.cs`, `ShopUpgradeRockets.cs`, `ShopRestockRockets.cs`, `ShopRechargeLives.cs` — Shop UI and purchase logic.
- `Highscores.cs`, `HighscoresExit.cs` — Local highscores saved in `Assets/highscores.json`.
- `GameLoader.cs`, `MainMenu*.cs` — Menu and scene startup helpers.

## Assets included
---------------
- Sounds: SFX and background music in `Assets/Resources/Sounds/` (e.g., `PlayerBullet1.mp3`, `EnemyExplode.mp3`, `spaceship.mp3`).
- Sprites: player, enemies, bullets, UI icons in `Assets/Resources/Sprites/` (e.g., `coolship.png`, `ChaserEnemy.png`, `orb.png`, `rocket.png`).
- Highscores: `Assets/highscores.json` holds local high score entries.

## How to open and run
-------------------
1. Open the project in Unity Hub and load the project folder. Install Unity 2019.1.14f1 (or a compatible 2019.1.x editor) if you don't have it.
2. In the Editor, open `Assets/Scenes/SampleScene.unity` and press Play to run the prototype in the Editor.
3. To edit scripts, open `S.P.A.C.E. SHOOTER.sln` in Visual Studio, Rider, or your preferred C# IDE.

## Build notes
-----------
- There are no external package dependencies in `Packages/manifest.json` — project uses built-in Unity APIs and standard C#.
- Highscores and some settings are stored locally (JSON). The project does not include online leaderboards or cloud saves.

## Development notes / edge cases
-----------------------------
- Shop prices double after each purchase to escalate cost.
- ObjectPool expands dynamically when required.
- Wave generation mixes hand-authored early waves with more random combinations in later waves.
- Common issues when importing the project into a different machine:
  - Missing serialized references in the Inspector (reassign prefabs/assets if needed).
  - Ensure `Assets/highscores.json` is writable.

## Testing and quick verification
-----------------------------
- Quick smoke test: open `SampleScene.unity` and press Play. Watch the Console for missing references or exceptions.
- Verify highscores: after a play session, inspect `Assets/highscores.json` to see saved entries.

## Credits and assets
------------------
- Sounds and SFX: included under `Assets/Resources/Sounds/` (created by the project author where noted).
- Music referenced in the original project files; check the previous README version or project notes for the original link.
- Sprites were sourced from previous projects and public assets and have been processed with external tools.
