# Library Organization

## Folder Roles

| Path | Contents |
|---|---|
| `Components/<Category>/` | Source libraries (`.SchLib`, `.PcbLib`) and their supporting files |
| `LibraryPackages/` | `.LibPkg` project(s) only |
| `Documentation/` | Repository documentation |

## Categories

| Category | Typical content |
|---|---|
| `Sensors/` | Current/voltage monitors, temperature, pressure, IMU, ADCs for sensing |
| `Power/` | Regulators, converters, MOSFETs, power diodes |
| `Connectors/` | Board-to-board, wire-to-board, headers, terminal blocks |
| `Protection/` | TVS, ESD, fuses, reverse-polarity and surge protection |
| `Microcontrollers/` | MCUs, SoCs, modules |
| `Drivers/` | Motor, gate, LED and line drivers |
| `Passives/` | Generic resistors, capacitors, inductors. *Not in the current tree; add it if generic passives are kept in this repository.* |

A component goes in the category of its primary function. Do not place the same component in two categories.

## Supporting Files per Category

**Recommended** layout inside each category folder:

```text
Components/Sensors/
├── Sensors.SchLib
├── Sensors.PcbLib
├── Datasheets/     # <MPN>_Datasheet.pdf
├── 3D/             # <FootprintName>.step
└── Docs/           # <MPN>.md component notes
```

## Source Library Rules

**Mandatory**

- Add new components to an existing suitable `.SchLib` and `.PcbLib`.
- Create a new library only when no suitable existing library is available.
- One contribution may add one component or several.
- Never create a library for a single component.
- Every `.SchLib` has a `.PcbLib` with the same base name.

**Recommended**

- Name a new library `<Category>.SchLib` / `<Category>.PcbLib`, or `<Category>_<Function>` when a category needs a split (for example `Sensors_Current`).

## Library Packages

**Mandatory**

- `LibraryPackages/` contains `.LibPkg` files only. Source libraries are **not** copied there; the `.LibPkg` references them in `Components/` by relative path.
- A new library must be added to the `.LibPkg` in the same Pull Request that creates it.
- Adding a component to a library already in the `.LibPkg` requires **no** `.LibPkg` change.
- Recompile the `.LibPkg` whenever an updated `.IntLib` is needed (a release, or a project that must consume the change).

Compile in Altium: open the `.LibPkg` → **Project → Compile Integrated Library**.

## Releases

Official releases are published with GitHub Releases. There is no `Releases/` directory. See [Versioning and Release Policy](Versioning_and_Release_Policy.md).
