# Wee Camp Layout Tools

Local-only 2D camp layout planner for arranging vehicles, shade structures,
kitchen zones, trailers, vans, fuel storage, keepout zones, and other labeled
camp objects.

## Open

Open `index.html` in a web browser.

If a browser blocks local file behavior, serve this folder locally:

```sh
python3 -m http.server 8765
```

Then open `http://127.0.0.1:8765/`.

Serving locally is recommended when editing toolbox assets, because the editor
loads reusable piece templates from JSON files in `assets/`.

## Sharing Layouts

For editable layouts, use `Export JSON` and send the exported `.json` file.
Another person can open `index.html`, use `Import JSON`, and continue editing.
JSON exports use a timestamped filename by default; add an export filename tag
before exporting when you want a human-readable variant name.

For a non-editable snapshot of only the map, use `Export Layout JPG`. This
downloads a flat image of the layout without the inventory pages used by
Print / Save PDF. Both exports draw a graphic scale bar that stays accurate
at any print size. PDF exports size the map to a fixed printed width on Letter
landscape and state the linear feet that 1 inch represents at that size; JPEG
exports state the feet-per-inch for fit-to-width printing as a labeled
assumption.

Before exporting a JPEG for placement submission, enter the camp and contact
details in the JPEG Submission Details section. Those values are rendered in a
header above the map and intentionally are not saved to browser storage, layout
JSON, shared links, or hosted layouts.

For a hosted website, there are two link options:

- Use `Copy Layout Link` for a self-contained URL hash. This works for smaller
  layouts but can become too long for complex plans.
- Commit exported layout files under `layouts/` and link to them with
  `?layout=layouts/name.json`. This is the best option for GitHub Pages.
- Add committed layout files to `layouts/index.json` so hosted viewers can
  choose them from the Starting Layout dropdown, edit locally, and export their
  modified JSON.

Example hosted layout link:

```text
https://YOUR_USER.github.io/wee_camp_layout_tools/?layout=layouts/draft-1.json
```

## Current Prototype

- Defaults to the 2026 Burning Man placement: Delphi & 3:45, fixed 150 ft
  frontage x 150 ft depth, mid-block mountain-facing frontage.
- Labels the four adjoining edges by default as 150 ft street frontage on the
  frontage side and 150 ft neighbor edges on the other three sides.
- Includes a locked 20 ft service lane keepout by default.
- Shade objects render translucently so tents, shiftpods, and other objects can
  remain visible underneath them.
- Draws orientation labels for street/mountains, The Man, and east-to-west sun
  travel on the canvas and PDF export, with sun travel rotated to the 3:45 camp
  bearing.
- Draws the typical afternoon wind vector from southwest toward northeast for
  dust, kitchen, fuel, and shade planning.
- Sun and wind overlays can be toggled on/off while editing so they do not
  obscure placed objects.
- Drag, pan, and zoom a scaled 2D site plan.
- Add predefined camp objects from a generic camp-pieces palette.
- Add 2026-specific constraint objects from a separate constraint-object
  palette.
- Load both palettes from versioned JSON toolbox files under `assets/` when the
  app is served locally or hosted.
- Generic camp pieces include common vehicles, bike racks, generator areas,
  fire rings, Elephant Mutant Vehicle parking, shade, tents, kitchen, fuel,
  water, and keepout objects.
- Edit label, type, dimensions, position, rotation, color, sleeping capacity,
  notes, lock state, and keepout/access-zone status.
- Assign objects to named layers. The current layers are `ground`,
  `infrastructure`, and `shade`; ground draws first, infrastructure draws next,
  and shade draws above it translucently.
- Rotate selected objects in 90 degree increments or fine 5 degree increments.
- Duplicate repeated shapes such as tents or shade tarps.
- Group and ungroup selected objects.
- Snap moving object edges/centers to other objects and site edges.
- View a live inventory, area summary, shade tarp summary, and sleeping
  capacity total.
- Assign each object an arrival/build time and a departure/strike time, then
  scrub the Time slider to move through build week: objects that have arrived
  render fully colored, not-yet-arrived objects fade out, and struck objects
  fade to a desaturated ghost. Inventory and summary recompute for the
  selected moment; exports always show the full layout.
- Set the camp-wide build start and strike end defaults in the Site section;
  new objects inherit them (or the current scrub time when the slider is
  active).
- Autosave in browser local storage.
- Export/import the editable layout as JSON.
- Export just the layout map as a JPG image with a printed-scale reference and graphic scale bar.
- Use Print / Save PDF to generate a layout and inventory PDF with a fixed-size printed-scale reference and graphic scale bar.
- Load a starting layout from a hosted `layouts/index.json` library.
- New hosted sessions without saved browser state load
  `layouts/camp-layout-2026-08-19-vehicle-tent-refresh.json` by default.

The editable layout data is plain JSON in the browser state, so saved `.json`
files can be versioned and reloaded later.

## Planning Documents

- `BUILD_PLAN.md`: tool architecture, UI layout, roadmap, and implementation
  direction.
- `CAMP_LAYOUT_OBJECTIVES.md`: camp layout goals, assumptions, constraints, and
  review checklist.
- `VEHICLE_RAW_NOTES.md`: paste area for loose vehicle and trailer notes.
- `VEHICLE_CONSTRAINTS.md`: structured vehicle constraints table derived from
  raw notes.
- `TENT_RAW_NOTES.md`: paste area for tent and sleeping-arrangement notes.
- `TENT_CONSTRAINTS.md`: structured tent footprint and sleeping-capacity table
  derived from raw notes.
- `assets/GENERIC_CAMP_PIECES.json`: reusable standard camp pieces used by the
  generic camp-pieces palette.
- `assets/VEHICLE_SHAPES.json`: 2026-specific vehicle shape assumptions used by
  the constraint-object palette.
- `assets/TENT_SHAPES.json`: named tent shapes derived from the tent roster,
  used by the 2026 Tent Shapes palette.
- `layouts/`: saved layout configurations and snapshots.
- `layouts/index.json`: manifest of layouts shown in the Starting Layout
  dropdown when the app is served locally or hosted.
