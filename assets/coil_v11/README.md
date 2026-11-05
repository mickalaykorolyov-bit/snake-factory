# SNAKE FACTORY v1.1 — COIL KILL source frames

These are the original pixel-perfect web projectile and wrapping animation PNG frames from Claude's `09_spider_attacks` sprite set. They are embedded directly into `index.html` in the playable release.

* `ball_0..3.png`: 4-frame flying web projectile.
* `wrap_0..1.png`: 2-frame web wrapped around a snake segment.
* `wrap_head_0..1.png`: 2-frame wrapped snake head.
* `break_0..3.png`: 4-frame web breaking animation (available for future gameplay polish).

## Gameplay

- **Body weapons:** 14–23 real physical slots along the snake, with installed BUILD modules mapped to those positions.
- **Web shooters, level 2+:** weave and fire webs at body segments; 40% slow for one hit, 55% for stacked hits, about 3s.
- **COIL KILL, all levels:** touching a distant section of your own body after circling enemies creates a closed polygon. Every enemy center inside dies immediately, including bosses.
- Base movement speed lowered from 108 to 80 units per second. Existing game HP/damage and wave rewards unchanged.

The former version is saved on branch `backup/visual-v10-before-coil`.
