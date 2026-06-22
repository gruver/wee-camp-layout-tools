# Wee Camp Layout Tool Build Plan

This document describes the approach for building the local camp layout tool and
the major components of the web interface.

## Product Direction

The tool is a local-only 2D planning app for laying out a Burning Man camp. It
should make it fast to place vehicles, shade, tents, kitchen areas, keepout
zones, and other labeled objects on a scaled site plan, then export the plan and
inventory for review.

The current implementation is intentionally a single static web page. That keeps
the prototype easy to run, easy to share, and free of build tooling while we
learn what layout workflows matter most.

## Current Architecture

- `index.html` contains the complete app: HTML, CSS, JavaScript, canvas drawing,
  state model, import/export, and print/PDF rendering.
- `assets/` contains reusable toolbox JSON files for generic camp pieces and
  year-specific constrained shapes.
- Browser local storage is used for autosave.
- Exported `.json` layout files are the portable source of truth for named
  versions, alternatives, and backups.
- `layouts/index.json` is the static manifest used to populate hosted starting
  layouts.
- The canvas render, inventory panel, and print/PDF output are all generated
  from the same in-memory JSON state.

## Data Model

The layout state is plain JSON:

- `site`: fixed site dimensions, grid, snap distance, service-lane width, and
  editable edge-adjacency labels.
- `placement`: address and orientation metadata such as frontage, mountain
  direction, Man direction, camp bearing, and sun path.
- `items`: every placed object, including geometry, position, rotation, label,
  type, layer, color, keepout status, lock status, group membership, and notes.
- `groups`: logical clusters of item IDs that should move together.
- `options`: user-facing display and editing toggles.
- `view`: current canvas pan and zoom.

Toolbox assets are separate JSON files:

- `assets/GENERIC_CAMP_PIECES.json`: reusable standard object templates.
- `assets/VEHICLE_SHAPES.json`: camp-year-specific constrained object
  templates.

These assets are versioned independently from saved layouts and from the editor
implementation. Saved layouts store placed objects, not links back to toolbox
templates.

## Web Tool Layout

The app is arranged in three primary regions.

Left sidebar:

- Site settings, edge-adjacency labels, and placement note.
- Generic camp-pieces palette, with 12 ft x 20 ft Black Rock shade as the
  primary shade structure preset, loaded from `assets/GENERIC_CAMP_PIECES.json`.
- 2026 constraint-object palette for the specific vehicle, trailer, solar, and
  access assumptions collected this year, loaded from
  `assets/VEHICLE_SHAPES.json`.
- Custom shape form for new rectangles and ellipses.
- JSON import/export and Print / Save PDF commands.
- Starting-layout selector loaded from the layout manifest.

Center workspace:

- Scaled 2D canvas.
- Site boundary, grid, edge labels, service lane, placed objects, keepout
  zones, snap guides, and orientation labels.
- Layered rendering, starting with `ground`, `infrastructure`, and `shade`.
  Ground is for zones such as service lanes, access keepouts, and parking
  circles. Infrastructure is for cars, tents, trailers, racks, generators, and
  camp objects. Shade is the top layer and remains translucent.
- Display toggles for large sun-path and afternoon-wind overlays.
- Toolbar for selection actions, grouping, deletion, zoom, grid, and snap.
- Bottom status readout for current view and selected object position.

Right sidebar:

- Selection inspector for editing one selected object.
- Rotation buttons for coarse 90 degree turns and fine 5 degree adjustments.
- Inventory table with counts, dimensions, and item types.
- Summary metrics for item count, type count, total area, and keepout area.

## Interaction Model

- Drag objects to move them.
- Drag empty canvas space to pan.
- Mouse wheel zooms around the pointer.
- Shift/meta/control click extends selection.
- Selected groups move as a unit.
- Snap uses object edges, object centers, site edges, and site center lines.
- Locked items are selectable but not draggable or rotatable.

## PDF Export

The PDF flow uses the browser print dialog:

- Render a print-only sheet with a high-resolution layout image.
- Include placement metadata, site size, service-lane note, inventory, and
  groups.
- Use the browser's "Save as PDF" capability for output.

This is good enough for the local prototype. If print fidelity becomes a
problem, move PDF generation to a dedicated client-side PDF library.

## Development Roadmap

Near-term:

- Add more realistic default objects and camp-specific presets.
- Add editable orientation controls if placement changes.
- Add collision and keepout warnings.
- Add dimension labels and measuring tools.
- Improve grouping, multi-select editing, and object alignment commands.

Medium-term:

- Add named layout alternatives in the app.
- Add undo/redo.
- Add layers for finalized zones, infrastructure, and personal camp objects.
- Add object templates stored in JSON.
- Add a constraint checklist panel tied to the layout objectives document.

Later:

- Consider splitting the app into separate source files if the single HTML file
  becomes too hard to maintain.
- Consider a lightweight build system only when the complexity justifies it.
- Consider collaborative or cloud storage only if more than one person needs to
  edit the plan.

## Engineering Principles

- Keep the app usable offline and locally.
- Keep layout data human-readable and exportable.
- Favor simple, inspectable interactions over hidden automation.
- Keep constraints visible so layout decisions can be reviewed.
- Avoid adding dependencies until they clearly reduce complexity.
