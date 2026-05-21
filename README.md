# Mahavir Decor — Carpet Fitter

A single-file, offline web tool for planning how to cut and lay carpets across multiple floor
areas with the least waste and fewest seams. Built for [Mahavir Decor](#).

## Use it

**Live:** https://nikeshvora1.github.io/carpet-fitter/

Or open **`index.html`** locally in any browser (double-click — no install, works offline). Either
way, your data is saved in that browser between sessions.

1. **Carpets you have** — enter each roll/remnant's width × length and quantity. Untick **Rotate?**
   for directional-pile or patterned carpet that must keep its direction.
2. **Areas to cover** — enter each room's width × length and quantity.
3. Click **Compute layout**.

## What you get

- **Summary** — area needed, carpet used, offcut waste %, and how many rooms need seaming.
- **🏠 Room view** — each room drawn to scale, coloured by which carpet feeds each part; white
  lines mark seams, grey hatching marks any uncovered area.
- **✂️ Cutting sheets** — each carpet drawn to scale, coloured by destination room; dashed areas
  are leftover offcuts.
- **Cut list** — a printable table of every cut. Use **Print plan** for the workshop.

## How it works

The classic **2D cutting-stock / nesting** problem:

- Rooms are placed **whole** first (largest first) using the **MaxRects** free-rectangle packer
  with a best-area-fit score, so large offcuts get filled before small ones.
- A room that won't fit whole anywhere falls back to **guillotine corner-fill**, tiling it from
  offcuts (the seamed pieces).
- Per-carpet rotation is respected — directional carpets are never turned.

It's a fast heuristic, not a guaranteed mathematical optimum, but it gets close for typical jobs.

### Not yet modelled

Cut/kerf allowance, seam-placement preferences (e.g. keeping seams away from doorways), and
pile-direction matching across seamed pieces.
