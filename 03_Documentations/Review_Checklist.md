# Review Checklist

All items are **Mandatory**. Details for each item are in the linked documents; this list is not a substitute for them.

## Organization

- [ ] Component is in the correct category and in an existing library, or a new library is justified ([Library Organization](Library_Organization.md)).
- [ ] No duplicate component (searched by MPN and function).
- [ ] New library, if any, is added to the `.LibPkg`; no source libraries copied into `LibraryPackages/`.

## Symbol

- [ ] Pin numbers and names match the datasheet.
- [ ] Electrical types are correct ([Component Requirements](Component_Requirements.md)).
- [ ] Symbol is readable and consistent with the library style.

## Footprint

- [ ] Pad dimensions, positions and numbering match the package drawing / land pattern.
- [ ] Pin 1 and polarity are marked; silkscreen does not overlap pads.
- [ ] Assembly outline and courtyard are present.

## Parameters

- [ ] Designator prefix and Comment are correct ([Naming Convention](Naming_Convention.md)).
- [ ] Component Name, Description, Footprint Name and 3D Model Name follow the format.
- [ ] Manufacturer, Manufacturer Part Number and Datasheet are complete (specific components).
- [ ] Datasheet PDF is committed in `Datasheets/`.

## 3D Model

- [ ] Model dimensions, orientation and alignment with the footprint are correct.
- [ ] Embedded model, or external STEP in the repository with a relative path that loads after reopening the library.

## Build

- [ ] `.LibPkg` compiles without errors when a new library was added or an `.IntLib` update is needed.
- [ ] Pull Request touches only the intended library files.
