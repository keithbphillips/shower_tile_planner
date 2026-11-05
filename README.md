# Shower tile planner

A single-page tool for laying out wall tile in a shower. Enter the shower's
size, mark which sides have walls, and set your tile size, grout joint, edge
gap, and floor buildup. It draws each wall to scale with full and cut tiles
(in 2D or as a 3D model you can turn), shows the ledger board height, and
lists end cuts and cut rows for every wall.

## Use

Open `index.html` in any browser. No build step or server needed. Settings
are saved in the browser, so they're still there next time you open it.
Settings from the first version (four separate walls) carry over.

The 3D view loads three.js from cdnjs the first time you switch to it, so it
needs an internet connection. Everything else works offline.

In 3D, **Finish** switches from layout colors (cut tiles highlighted, ledger
shown) to a finished look in Carrara, Calacatta or Nero marble, with a choice
of grout color. The marble is generated in the browser, and each tile gets its
own patch of stone, so it's a preview of the look, not of a specific product.

Sizes accept fractions (`70 1/2`, `70-1/2`, `9/16`) or decimals (`70.5`).

## Walls

- **Width** is the back wall, **depth** is the side walls, both measured
  between the backer boards before tile. **Tile + thinset** is how far the
  tile face sits off the backer.
- Tap a side in the top view (or use the **Tiled** checkbox) to add or remove
  a wall. The entry is at the bottom.
- Leave **Length** blank for a full wall, or enter a length for a short return
  and pick which end it **starts at**. Leave **Height** blank for full height,
  or enter one for a knee wall.
- Corners: the back wall runs through to both side backers. Side walls butt
  into the back wall's tile face and run through to the front. A front wall
  butts into the side walls' tile. Tiled widths are worked out from that.
- Edge gaps go at corners only. Open ends (no wall meeting them) get no gap.
- A wall with a length typed in still makes a corner at its far end if it's
  long enough to reach the next wall (within 1/16").
- Each wall is drawn as seen from inside the shower, and the labels under it
  say what each end meets. Facing the front wall, its left end is the
  shower's right side.
- Where another wall's tile butts into a wall's end, part of that end piece is
  covered (tile + thinset minus the edge gap). The 2D drawing hatches that
  strip, and the table lists the cut size plus how much of it shows.
- **Check these** lists layout problems: a tile that stops short of a corner
  or open edge (leaving a wider joint), a cut under 1" that's too thin to cut
  cleanly, or an end piece that shows less than 1" past the next wall's tile.
  Those tiles are outlined in red, and the wall's tab gets a red dot.
- **Niche**: tick "Niche in this wall" on any wall and give the rough opening
  (the hole in the backer): width, height, depth, bottom (measured up from the
  pan) and left edge (blank centers it). The tile is cut around it: tiles beside,
  above or below come out as trimmed pieces, and a tile the niche only bites into
  is marked as a notch. The card shows the finished opening after tile and the
  nearest grout line for the bottom ("Snap to grout" moves it there), and
  suggests a height that puts the top on a grout line too. Strips under 1"
  around the niche show up in **Check these**. One niche per wall; the tile
  inside the niche isn't laid out, but its area is counted.
- **Area**: the table gives each wall's tiled area in square feet, and the
  line under it gives the wall total (plus 10% for cuts and breakage) and the
  floor. Floor area is shown inside the finished wall tile and to the backer
  boards. The exposed end of a short wall, a curb, and anything outside the
  shower aren't included.

## How it lays out tile

- **Width:** tries both centering a tile and centering a grout joint on each
  wall, and keeps whichever leaves larger end pieces.
- **Rows** are the same on every wall, worked out from the ceiling height, so
  grout lines run level around the corners. Knee walls are cut off at their
  top.
- **Balanced cuts:** one less full row, with equal cut rows at the floor and
  ceiling.
- **Full row at floor:** full rows from the finished floor up, with a cut
  strip at the ceiling.
- **1/3 offset:** each course shifts one third of a tile length.
- **Ledger:** height of the ledger's top edge above the pan (mud bed), which
  is where the first row above the bottom cut row starts. Floor buildup is
  the floor tile plus thinset.
