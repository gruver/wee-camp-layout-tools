# Tent Constraints

This table is generated and maintained from `TENT_RAW_NOTES.md`. It captures
tent footprints and derived sleeping capacity so tent placement can be
reviewed alongside the camp layout, in the same spirit as
`VEHICLE_CONSTRAINTS.md`.

## Tent Table

| Owner / Group | Label | Approx Footprint | Sleep Capacity (derived from name) | Shade |
|---|---|---:|---:|---|
| Brendan | Brendan tent | 14 ft x 13 ft | 1 | TBD |
| Caley | Caley tent | 12 ft x 12 ft | 1 | Placed beneath a shade tarp. |
| Daniel & Nipul & Brandon | Daniel, Nipul & Brandon tent | 12 ft x 12 ft | 3 | TBD |
| Emily & Colin | Emily & Colin tent | 10 ft x 14 ft | 2 | TBD |
| Garret | Garret tent | 16 ft x 16 ft | 1 | TBD |
| Gene | Gene tent | 8 ft x 8 ft | 1 | TBD |
| Heather & Isaac | Heather & Isaac tent | 10 ft x 10 ft | 2 | TBD |
| Ian | Ian tent | 12 ft x 12 ft | 1 | Placed beneath a shade tarp. |
| Jake | Jake tent | 12 ft x 12 ft | 1 | TBD |
| Jeb & Rissa | Jeb & Rissa tent | 14 ft x 14 ft | 2 | TBD |
| Johnny | Johnny tent | 12 ft x 12 ft | 1 | TBD |
| Matty | Matty tent | 15 ft x 12 ft | 1 | TBD |
| Mike | Mike tent | 10 ft x 10 ft | 1 | TBD |
| Nick & Ellen | Nick & Ellen tent | 9 ft x 10 ft | 2 | TBD |
| Reid | Reid tent | 12 ft x 12 ft | 1 | Placed beneath a shade tarp. |

Total confirmed tent sleeping capacity: **21 people** across
15 tents.

`Sleep Capacity` is derived only by counting `&`-joined names in the owner
field (e.g. "Heather & Isaac" = 2, "Daniel & Nipul & Brandon" = 3). This is a
reasonable capacity estimate for a tent (a tent's purpose is sleeping), but it
is a naming-based inference, not a stated occupancy number, and should be
confirmed with each owner.

## Owners Without A Separate Tent Entry

These owners have a row in `TENT_RAW_NOTES.md` but no tent shape was
generated, either because their vehicle notes suggest they sleep in their
vehicle instead, or because dimensions are entirely unconfirmed.

| Owner / Group | Notes |
|---|---|
| Aidan | No tent listed; owns a camper van (see vehicle notes). |
| Alex & Emma | No tent listed; owns a Tacoma + trailer (see vehicle notes). |
| Ashley | No tent listed; owns a camper van (see vehicle notes). |
| Chloe & Gabriel | No tent listed; owns a camper van (see vehicle notes). |
| JT & Rick | No tent listed; owns a van/truck + dumpster carport (see vehicle notes). |
| Loren | No tent listed; owns a Tacoma + trailer (see vehicle notes). |
| Ryan & Rudy | No tent listed; owns a van/truck + dumpster carport (see vehicle notes). |
| Alice | Tent dimensions not provided in updated notes (row blank), and vehicle also blank. TBD. |

**Important:** the "sleeps in vehicle" inference above is not an explicit
statement in either raw-notes file. It is inferred solely from the absence of
a tent row combined with a vehicle description like "camper van." Treat it as
a working assumption, not a confirmed fact, and do not add these people's
head count to any vehicle's `sleepCapacity` field until confirmed by the
owner. `assets/VEHICLE_SHAPES.json` deliberately leaves `sleepCapacity`
unset/0 on every vehicle shape for this reason.

## Derived Layout Assumptions

- `assets/TENT_SHAPES.json` (version 1) converts the 15 confirmed rows into
  map-loadable shapes, each carrying a `sleepCapacity` derived as described
  above.
- Per `CAMP_LAYOUT_OBJECTIVES.md` ("sleeping areas benefit from... shade but
  should not consume all public shade resources"), only 3 of the camp's 6
  Black Rock shade tarps have a tent placed underneath (Caley, Ian, Reid).
  The other 3 shade tarps remain public/kitchen-adjacent shade with nothing
  placed under them. Shade renders as a translucent top layer, so a tent
  placed under a shade tarp is an intentional overlap, not a layout bug.
- Alice has no tent entry (and no vehicle entry either); her shelter is a
  full open question. See `CAMP_LAYOUT_OBJECTIVES.md` open questions.

## Field Guidance

- `Owner / Group`: Person or household the tent belongs to, as written in
  `TENT_RAW_NOTES.md`.
- `Approx Footprint`: Tent footprint in feet (L x W from the raw notes,
  mapped directly to shape width x height).
- `Sleep Capacity`: See naming-inference caveat above.

## Review Questions

- Confirm actual occupancy per tent versus the naming-derived estimate.
- Confirm whether the 11 vehicle-owner households with no tent entry
  (Aidan, Alex & Emma, Ashley, Chloe & Gabriel, JT & Rick, Loren, Ryan & Rudy)
  actually sleep in their vehicle, and their real sleeping capacity.
- Resolve Alice's shelter situation (both vehicle and tent rows are blank).
- Confirm Ian's and Matty's arrival plan given their vehicle rows are TBD.

## Change Log

- 2026-08-19: Initial tent constraints captured from a new, structured 23-row
  tent roster (`TENT_RAW_NOTES.md`, added alongside the updated vehicle
  roster). 15 rows have confirmed footprints; 8 rows are TBD (no tent, sleeps
  in vehicle per vehicle notes) or otherwise blank (Alice).
