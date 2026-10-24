# TBSWHP pickem kit

Turns your weekly graphic + a small JSON file into a ready-to-upload page folder (`week7/`, etc.).

## Files
- `make_week.py`: the builder
- `page_template.html`: the page itself (look, font, behavior). Edit this to restyle every future week.
- `week6.json` + `week6.png`: last week's inputs, your example to copy
- `week6/`: the finished Week 6 folder, ready to upload

## One-time setup
1. Install Python 3 and run: `pip install pillow`
2. In `week6.json`, set `siteUrl` to `https://YOUR-USERNAME.github.io/YOUR-REPO` (no trailing slash). Every week's config needs this, or Discord shows no preview image.

## Each week
1. Copy `week6.json` to `week7.json` and put the new graphic next to it as `week7.png`.
2. Edit `week7.json`:
   - `week` and `graphic`
   - the 5 `matchups`, in this order: (1) the MOTW inset, (2) row 2 left, (3) row 2 right, (4) row 3 left, (5) row 3 right
   - for each side: `seed` (the number badge, also used as the rank, e.g. 10 shows "10th"), `name`, and `record` (e.g. `2-3-0`) from your standings screenshot
3. Optional check: `python make_week.py week7.json --check` writes `layout-check.png` with the crop boxes drawn on your graphic. Red boxes should hug each strip and the green line should sit at the "VS" pill.
4. Build: `python make_week.py week7.json`. This creates a `week7/` folder.
5. Put the `week7/` folder in your repo on `main` and push. The page is live at `https://YOUR-USERNAME.github.io/YOUR-REPO/week7/` after a minute or two.

## Tweaks
- **Text colors:** after building, open `week7/week.js` and change any `fill` or `stroke` hex. Or add `"fill"` and `"stroke"` to a team in the JSON so they stick when you rebuild.
- **Crop boxes:** if the graphic's layout ever changes, add a `"layout"` block to the JSON (hero box plus 5 strips, each with `box` and `split`, in pixels of a 1348px-wide graphic). Use `--check` to confirm.
- **Look and feel:** edit `page_template.html`, then rebuild any week.
- **Discord preview stale?** Add `?v=2` to the end of the link.

Picks are saved per week in each person's browser, so weeks never overwrite each other.
