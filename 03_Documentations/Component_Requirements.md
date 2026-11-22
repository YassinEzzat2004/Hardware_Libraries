# Component Requirements

Every rule here is **Mandatory** unless marked *Recommended*. Naming of fields is covered in [Naming Convention](Naming_Convention.md).

## Schematic Symbols

- Pin numbers and pin names match the datasheet exactly (including overbars for active-low names).
- Every pin has the correct **Electrical Type**.

| Pin function | Electrical type |
|---|---|
| Logic/analog input | Input |
| Push-pull output | Output |
| Bidirectional (e.g. I2C SDA) | I/O |
| Open-drain / open-collector output (e.g. alert) | Open Collector |
| Supply and ground | Power |
| Passive terminals (R, C, L, connector contacts) | Passive |

- Example, INA226: `A0`, `A1`, `SCL`, `VBUS`, `IN+`, `IN-` = Input; `SDA` = I/O; `ALERT` = Open Collector; `VS`, `GND` = Power. Confirm against the datasheet pin table.
- Symbol is readable: inputs left, outputs right, power top, ground bottom where practical; pin names not overlapping; grid-aligned pins.
- Multi-pin power/ground pins are not hidden.
- Designator is the correct prefix with `?` and Comment follows the rules in the naming document.
- Symbols for the same function use the same size and style within a library.

## PCB Footprints

- Pad numbers match the symbol pin numbers; pad sizes, positions, pitch and hole sizes match the datasheet land pattern or are derived from the package drawing by a documented rule (IPC-7351).
- Pin 1 is identifiable on silkscreen and, for polarized parts, polarity is marked (diode cathode, electrolytic positive, connector keying).
- Silkscreen (Top Overlay) stays off pads and does not conflict with the part outline.
- Assembly information is present: component outline and courtyard on mechanical layers.
- The footprint is compared against the manufacturer's package drawing, not only against the 3D model.
- Origin placement: *Recommended* at the body center for SMD parts; at pin 1 or a mounting feature for connectors where that is conventional.
- Mechanical layer assignment (assembly, courtyard, 3D body) is consistent across all footprints in the library. Do not change it per component.

## 3D Models

- Model dimensions and orientation match the physical component and the footprint: correct body size, standoff height, pin 1 position, pins landing on pads.
- Model origin and rotation are set so the model aligns with the footprint without per-use adjustment.
- Check alignment in the 3D view (**View → 3D Layout Mode**) before committing.

**Embedded vs external**

| Mode | Rule |
|---|---|
| Embedded STEP | Allowed. The `.step` source is still committed to the category's `3D/` folder so the model can be regenerated or replaced. |
| Externally linked STEP | The `.step` must be in the repository and referenced by a path **relative** to the `.PcbLib`. No absolute paths (`C:\...`), no files outside the repository. |

- Do not rename or move a linked STEP file without updating every footprint that references it.
- Verify after saving: close and reopen the `.PcbLib` and confirm the model still loads. *Recommended:* also check from a fresh clone in a different directory.
- Model file name follows the footprint name ([Naming Convention](Naming_Convention.md)).
- Do not commit STEP files with unclear licensing; use manufacturer models or models created for this repository.
