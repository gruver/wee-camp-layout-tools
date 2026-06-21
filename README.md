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

## Sharing Layouts

For editable layouts, use `Export JSON` and send the exported `.json` file.
Another person can open `index.html`, use `Import JSON`, and continue editing.

For a hosted website, there are two link options:

- Use `Copy Layout Link` for a self-contained URL hash. This works for smaller
  layouts but can become too long for complex plans.
- Commit exported layout files under `layouts/` and link to them with
  `?layout=layouts/name.json`. This is the best option for GitHub Pages.

Example hosted layout link:

```text
https://YOUR_USER.github.io/wee_camp_layout_tools/?layout=layouts/draft-1.json
```

## Current Prototype

- Defaults to the 2026 Burning Man placement: Delphi & 3:45, fixed 150 ft
  frontage x 150 ft depth, mid-block mountain-facing frontage.
- Includes a locked 20 ft service lane keepout by default.
- Shade objects render translucently so tents, shiftpods, and other objects can
  remain visible underneath them.
- Draws orientation labels for street/mountains, The Man, and east-to-west sun
  travel on the canvas and PDF export.
- Draws the typical afternoon wind vector from southwest toward northeast for
  dust, kitchen, fuel, and shade planning.
- Sun and wind overlays can be toggled on/off while editing so they do not
  obscure placed objects.
- Drag, pan, and zoom a scaled 2D site plan.
- Add predefined camp objects from a generic camp-pieces palette.
- Add 2026-specific constraint objects from a separate constraint-object
  palette.
- Generic camp pieces include common vehicles, bike racks, generator areas,
  fire rings, Elephant Mutant Vehicle parking, shade, tents, kitchen, fuel,
  water, and keepout objects.
- Edit label, type, dimensions, position, rotation, color, notes, lock state,
  and keepout/access-zone status.
- Assign objects to named layers. The current layers are `ground`,
  `infrastructure`, and `shade`; ground draws first, infrastructure draws next,
  and shade draws above it translucently.
- Rotate selected objects in 90 degree increments or fine 5 degree increments.
- Duplicate repeated shapes such as tents or shade tarps.
- Group and ungroup selected objects.
- Snap moving object edges/centers to other objects and site edges.
- View a live inventory and area summary.
- Autosave in browser local storage.
- Export/import the editable layout as JSON.
- Use Print / Save PDF to generate a layout and inventory PDF.

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
- `VEHICLE_SHAPES.json`: 2026-specific vehicle shape assumptions used by the
  constraint-object palette.
