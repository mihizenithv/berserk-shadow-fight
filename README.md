# Berserk: The Eclipse

A dark-fantasy browser game inspired by *Berserk*, built as two single-file HTML5 canvas games with
no build step and no dependencies.

| Page | What it is |
|---|---|
| `index.html` | **Top-down RPG.** Explore a rain-soaked village as Guts with 8-directional movement, wall and triangle collision, a following camera, and rain, ember and light-source effects. Walk into the transition zone to start the fight. |
| `shadow_fight.html` | **Side-view fighting game** in the style of Shadow Fight: a procedurally animated skeleton fighter (no sprite sheets), punch and weapon attacks, jumping, health bars, hit-slow-motion and an AI opponent (the Snake Baron). |

## Play

Any static file server works:

```bash
python -m http.server 8000
# open http://localhost:8000/index.html
```

Or with Docker:

```bash
docker build -t berserk .
docker run --rm -p 8080:80 berserk
# open http://localhost:8080
```

## Controls

| Action | Keys |
|---|---|
| Move (RPG) | `W` `A` `S` `D` or arrow keys |
| Move (fight) | `A` / `D` |
| Jump (fight) | `W` |
| Punch / weapon (fight) | `J` / `L` |

## Technical notes

- Pure HTML, CSS and JavaScript on a `<canvas>`; no framework, bundler or runtime dependencies.
- Fighters are driven by a small skeletal animation system (`Skeleton`) with forward-kinematic
  pose blending, so animation is code, not art.
- The RPG is class-based (`GameEngine`, `Renderer`, `Camera`, `Player`, `CollisionWall`, `CollisionTriangle`, particle systems) with an input manager that tracks per-frame "just pressed" keys and normalises diagonal
  movement.
- `generated_assets/manifest.json` describes AI-generated sprite sheets (frame size and
  animation rows) prepared for a sprite-based version of the fighters.

## Credits

Game design and code by Mihir. Map and character art generated with AI image tools.
*Berserk* is the work of Kentaro Miura; this is an unaffiliated fan project.

## License

MIT (code). Fan-art assets are not covered by this license.
