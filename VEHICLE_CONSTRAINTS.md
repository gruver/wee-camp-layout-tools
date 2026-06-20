# Vehicle Constraints

This table is generated and maintained from `VEHICLE_RAW_NOTES.md`. It captures
vehicle footprints, access needs, sleeping assumptions, and layout constraints
so vehicle placement can be reviewed alongside the camp layout.

## Vehicle And Rig Table

| Owner / Group | Vehicle / Rig | Approx Footprint | Sleeps In Vehicle | Can Detach / Move | Arrival / Departure Needs | Placement Preference | Access Constraints | Notes / TBD |
|---|---|---:|---|---|---|---|---|---|
| Loren Rommel | Toyota Tacoma + trailer | 34 ft total length | TBD | TBD | TBD | TBD | Treat as combined 18 ft truck + 16 ft trailer unless detach details are confirmed. | Width TBD. Confirm whether truck and trailer can separate after arrival. |
| Ash | Sprinter van | 20 ft length | TBD | TBD | TBD | TBD | Standard van clearance; avoid boxing in until access needs are confirmed. | Width TBD; use 8 ft typical van width until confirmed. |
| Ryan | Sprinter van + carport | 20 ft x 20 ft | TBD | TBD | TBD | Shade/carport adjacent to van | Needs full 20 ft x 20 ft footprint kept together. | Confirm carport orientation and whether van doors need clearance on a specific side. |
| Aidan | Camper van | 22 ft length | TBD | TBD | TBD | TBD | Standard camper van clearance; avoid boxing in until access needs are confirmed. | Width TBD; use 8 ft typical van width until confirmed. |
| Jeb and Rissa | Solar-oriented vehicle / trailer / camp object | 12 ft x 12 ft | TBD | TBD | TBD | South-facing, lower-shade area | Needs clear sun exposure for solar panels; avoid placing under shade or shadow-heavy zones. | Exact object type TBD. Confirm whether this is a vehicle, trailer, or solar setup footprint. |
| Alice | RV | 30 ft length | TBD | TBD | TBD | TBD | Large vehicle clearance; likely should not be boxed in without confirmation. | Width TBD; confirm slide-outs, awning, door side, and whether it must stay accessible. |
| Eyal | Trailer | 12 ft length | TBD | TBD | TBD | TBD | Trailer access and tow/detach requirements TBD. | Width TBD. Confirm tow vehicle, detached footprint, and whether trailer is slept in. |
| Team | Box truck | 35 ft length | TBD | TBD | TBD | Infrastructure / storage TBD | Large vehicle clearance; consider edge placement and access for loading doors. | Width TBD; confirm whether it is kitchen/storage/public-facing and which side needs access. |
| Team | Cargo trailer with access stairs | 45 ft x 9 ft plus 6 ft stair access | TBD | TBD | TBD | Infrastructure / storage TBD | Reserve 45 ft x 15 ft effective footprint if stairs project from the 9 ft side; keep stair side clear. | Confirm stair side, tow vehicle needs, and whether the 6 ft access is along full length or localized at door. |

## Derived Layout Assumptions

- Current known vehicle/trailer inventory includes at least 9 distinct rigs or
  vehicle-related footprints.
- `VEHICLE_SHAPES.json` converts these rows into map-loadable shapes. Length-only
  entries use placeholder widths until owners confirm exact footprints.
- Several entries only provide length; use conservative placeholder widths in
  the app until confirmed.
- Ryan's van plus carport and Jeb/Rissa's solar footprint have non-vehicle
  adjacency/orientation constraints and should be treated as fixed compound
  footprints during layout.
- The Team cargo trailer should reserve extra access space for stairs, not just
  the trailer body rectangle.
- Unknown exit timing and box-in tolerance should remain `TBD` until owners
  confirm whether they need mid-event access.

## Field Guidance

- `Owner / Group`: Person, household, or group responsible for the vehicle.
- `Vehicle / Rig`: Van, truck, car, trailer, RV, box truck, or combined rig.
- `Approx Footprint`: Use total parked footprint in feet, including trailer if
  attached.
- `Sleeps In Vehicle`: Whether the vehicle is also a sleeping zone.
- `Can Detach / Move`: Whether truck/trailer can separate or vehicle can leave.
- `Arrival / Departure Needs`: Early arrival, late arrival, mid-event exit, or
  must remain accessible.
- `Placement Preference`: Quiet, social, kitchen-adjacent, shade-adjacent,
  frontage, edge, back, etc.
- `Access Constraints`: Cannot be boxed in, needs door-side clearance, trailer
  ramp access, service-lane access, turning clearance, or water/kitchen access.
- `Notes / TBD`: Ambiguity, missing dimensions, assumptions to confirm.

## Review Questions

- Which vehicles must be able to leave without moving other objects?
- Which vehicles are also sleeping spaces?
- Which trailers can detach from tow vehicles?
- Which rigs need door, ramp, awning, or bike access on a specific side?
- Which vehicles are infrastructure, storage, kitchen, or public-facing assets?
- Which vehicles can be deep in camp or boxed in after arrival?
