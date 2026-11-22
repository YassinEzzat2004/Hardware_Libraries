# Hardware-Libraries
 
Altium Designer component libraries (schematic symbols, PCB footprints, 3D models) shared across our hardware projects.
 
## Repository Layout
 
```text
Hardware-Libraries/
├── README.md
├── Components/          # Editable source libraries (.SchLib / .PcbLib), by category
│   ├── Sensors/
│   ├── Power/
│   ├── Connectors/
│   ├── Protection/
│   ├── Microcontrollers/
│   └── Drivers/
├── LibraryPackages/     # .LibPkg that compiles the source libraries into .IntLib
└── Documentation/
```
 
| File type | Role |
|---|---|
| `.SchLib`, `.PcbLib` | Editable source. Edited by contributors. |
| `.LibPkg` | Altium project that references the source libraries. |
| `.IntLib` | Compiled distribution artifact. Published with GitHub Releases. |
 
## Using the Libraries
 
1. Download the latest `.IntLib` from the [Releases](../../releases) page.
2. In Altium Designer: **Components panel → ⋮ → File-based Libraries Preferences → Installed → Install**, and select the `.IntLib`.
To work from source instead, clone the repository and open the `.LibPkg` in `LibraryPackages/`.
 
## Contributing
 
Add components to an **existing** library whenever one is suitable, follow the naming rules, and open a Pull Request. Start with the [Contribution Guide](Documentation/Contribution_Guide.md).
 
## Documentation
 
| Document | Content |
|---|---|
| [Library Organization](Documentation/Library_Organization.md) | Folder rules, categories, `.LibPkg` and `.IntLib` handling |
| [Naming Convention](Documentation/Naming_Convention.md) | Altium field rules with examples (INA226, R, C, IC, connector, MOSFET) |
| [Component Requirements](Documentation/Component_Requirements.md) | Symbol, footprint and 3D model requirements |
| [Contribution Guide](Documentation/Contribution_Guide.md) | Step-by-step contribution workflow |
| [Review Checklist](Documentation/Review_Checklist.md) | Checklist used to approve Pull Requests |
| [Versioning and Release Policy](Documentation/Versioning_and_Release_Policy.md) | Commits, PRs, GitHub Releases |
 
Rules are marked **Mandatory** (a Pull Request is not approved without them) or **Recommended**.
 
