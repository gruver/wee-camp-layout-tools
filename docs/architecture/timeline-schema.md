# Timeline Schema And Arrival/Departure Design

Durable knowledge for the camp layout planner (`index.html`, single-file app).
Written 2026-08-21 when progressive arrival/build and departure/strike became
first-class.

## Data Model

- Every item carries `arrivesAt` and `departsAt` as datetime-local strings
  (`"2026-08-24T12:00"`, local time, no offset). Empty string means
  unconstrained: the item is always present.
- Layout-level `timeline: { buildStart, strikeEnd }` bounds are the defaults
  for new objects and contributors to the time slider range. The slider spans
  the union of the bounds and all item timestamps, so bounds edits never move
  an existing scrub position or change present-counts. Editable in the Site
  section; normalized with `TIMELINE_DEFAULTS` (defined BEFORE the
  `let state = loadState()` initializer — see TDZ note below).
- `state.options.timeScrub` (bool) + `state.options.timeValue` (ISO string)
  persist the slider state through autosave and JSON export.

## Presence Semantics

`presenceAt(entry, at)` returns one of:

- `"departed"` — `departsAt <= at`. Renders desaturated (`desaturateColor`,
  75% toward luminance gray) at alpha 0.32. Still clickable so strike times
  stay editable.
- `"future"` — `arrivesAt > at`. Full color at alpha 0.25.
- `"present"` — otherwise, including when scrubbing is off or either field is
  empty. Existing per-type alpha rules (shade 0.42, keepout 0.78) multiply on
  top.

Inventory and summary recompute over present items while scrubbing; JPG/PDF
exports always render the full layout (print path draws items independently).

## Version Migration Pattern

Layout `version` gates one-time backfills. Version 5 backfills missing/
invalid timestamps from timeline bounds for pre-timeline layouts; v5+
layouts keep deliberately cleared fields. This mirrors the version-3 layer
migration. Bump `Math.max(N, previousVersion)` AND any hardcoded
`version:` in `newEmptyLayout` together.

## Lessons (do not relearn)

1. **TDZ during boot:** `let state = loadState()` runs `loadState` before the
   `state` binding initializes. Anything reachable from `normalizeLayout`
   (e.g. `ensureServiceLane`, default-timeline helpers) must be pure — take
   `layout` as a parameter, never touch global `state`, and declare consts
   they need ABOVE the initializer.
2. **ensureServiceLane overwrites:** it `Object.assign`s a freshly built lane
   onto the existing one on every normalize. Any new item field must be
   preserved across that assign or it gets wiped each load.
3. **Slider/state invariant:** after every `syncTimeControls`,
   `Number(slider.value) === new Date(state.options.timeValue).getTime()`.
   Set min/max/step AND value, clamping out-of-range stored values (bounds can
   move under a saved scrub time).
4. **Creation paths:** all item creation goes through `addFromTemplate`,
   `loadConstraintVehicles`, roster import, and duplicate. Duplicates copy
   times; the other three call `applyDefaultTimeline(entry, state,
   selectedScrubTime())` so no object exists without both timestamps.
5. **localStorage wins over hosted JSON** on reload. When changing the seeded
   default layout's schema, old autosaves need a versioned migration, not just
   a patched JSON file.
