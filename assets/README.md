# Layout Assets

This directory holds reusable toolbox assets for the camp layout editor.

- `GENERIC_CAMP_PIECES.json`: standard reusable camp pieces such as shade,
  tents, vehicles, kitchen, fuel, fire ring, and parking zones.
- `VEHICLE_SHAPES.json`: 2026-specific constrained vehicle, trailer, and
  infrastructure shapes derived from the vehicle constraints notes.

Layouts under `../layouts/` are saved camp configurations. Assets in this
directory are reusable source templates for adding new objects to a layout.

When the app is served over localhost or GitHub Pages, the editor loads these
JSON files at startup. If the app is opened directly from the filesystem and
the browser blocks local JSON loading, the editor falls back to the bundled
defaults in `index.html`.
