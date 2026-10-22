# Character sprites

These PNGs are generated procedurally by `npm run gen:sprites`
(`scripts/gen-sprites.mjs`) — original CC0 pixel-art, no external assets. They're
committed so the game looks complete out of the box.

To upgrade any character to hand-made / AI art, just overwrite its file. Anything
missing falls back to a colored placeholder circle, so you can swap one at a time.

Layout guides are in `../templates/` (open the `.svg` files); `character-guide.svg`
is the clean, label-free sheet to feed an image generator.

## Turning an AI sheet into a game asset
Generate against `character-guide.svg`, then slice + downscale + knock out the
background with `scripts/slice-sheet.mjs`:

```
# a 4x4 walk sheet -> player.png
node scripts/slice-sheet.mjs raw.png --out public/assets/sprites/player.png

# just the first pose -> a static NPC
node scripts/slice-sheet.mjs raw.png --single --out public/assets/sprites/npc/toblen.png
```

## Player
- `player.png` — a **32×48 spritesheet**, 4 frames × 4 directions.
- Rows top→bottom: **down, left, right, up**. Column 0 is the idle pose.
- Full sheet is **128×192px**.

## NPCs
- `npc/<id>.png` — a single **32×48 image** (down-facing pose).
- `<id>` is the NPC's id from `src/data/townData.js` / `src/data/interiors.js`.

Ids: `qelline, daran, salesman, salesman2, toblen, elsa, freda, lanar, narth,
pip, elmina, garaele, linene, halia, harbin, sildar`.

Example: `npc/toblen.png`, `npc/garaele.png`.
