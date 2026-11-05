# Snake Factory v1.0 — Claude visual expansion

## Active in game

The runnable game is `/index.html` (fully self-contained) and already embeds the following sources. The PNGs here are **editable source copies**, so future versions can migrate to external asset loading.

- `pickup.png`: 24x24px cells, 3 rows (module boxes, metal crystals, medkits), 6 idle + 4 spawn + 5 collect frames each.
- `fx.png`: shot directions and impact/death effects (see `sprite_map.json`).
- `arena.png`, `decor.png`, `decals.png`: factory tiles, decorations, pixel blood.
- `wall_*.png`: illuminated walls, industrial columns and corner pieces.
- `tier1.png`, `tier2.png`, `tier3.png`: bronze/silver/gold appearances of the same combat modules, replacing digit labels.
- `logo_*.png`, `heart.png`, `gear.png`, `crystal.png`, `btn_build.png`, `grid_*.png`: reusable interface components. Icons used in the current HUD, other files available for the next UI polish.
- Updated `assets/medium.png`, `assets/heavy.png`, `assets/boss.png` + JSON metadata for richer animation sheets; **only walking/visual damage states are connected**.

## Deliberately deferred

The Claude archive also contains venom projectiles, web snares, boss attacks, land mines, laser weapons, and other mechanics not present in the current game. These are **not enabled**: this release changes presentation only, not combat/damage/balance/timing.

## Pixel rules

Use nearest-neighbor rendering (`imageSmoothingEnabled=false`, `image-rendering: pixelated`) and integer draw positions. Sprite frame rectangles and animation durations are in `sprite_map.json`. Source sprites stay on a transparent integer pixel grid.

## Version recovery

The pre-expansion game is preserved on branch `backup/claude-initial-art`.
