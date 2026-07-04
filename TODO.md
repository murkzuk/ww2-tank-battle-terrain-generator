# TODO

Ideas for improving this tool, not yet scheduled. Roughly ordered by effort.

## Batch-export all 30 battles
Script through each battle's known bounding box automatically instead of
manual click-drag-export per battle. Big time-saver for building a ready-made
terrain library for all 30 battles at once. Mostly wiring the existing
`generateElevationHeightmap` / export functions in a loop over the battle
database — no new data source needed.

## Slope/gradient map export
We already fetch real per-pixel elevation for every capture, so deriving a
slope-angle map is close to free computationally (just a neighbor-difference
pass over the elevation grid). Useful for tank AI pathfinding/traversability,
not just visual reference.

## Higher resolution ceiling
Capture is now tile-based (real elevation tiles), not a screenshot of the
on-screen map, so we're no longer limited by the rendered map div's pixel
size. Could raise the current 2048 cap, or auto-suggest the resolution that
best matches the selected area's native tile detail instead of a fixed
dropdown.

## Basic splat/texture map
Auto-generate a rock/grass/snow blend texture from slope + elevation — a
common Unity terrain companion asset. Bigger lift than the others; would
need to decide on a blending heuristic (e.g. steep slopes → rock, high
elevation → snow) rather than a fixed threshold.
