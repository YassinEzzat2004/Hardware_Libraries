# Versioning and Release Policy

## Terms

| Item | Meaning |
|---|---|
| Commit | One individual change (a component added, a footprint fixed). |
| Pull Request | A reviewed contribution, approved with the [Review Checklist](Review_Checklist.md), merged into `main`. |
| GitHub Release | A reviewed and verified library version, published from `main` with a version tag. |
| `.SchLib`, `.PcbLib` | Editable source files. Live in `Components/`. |
| `.IntLib` | Compiled distribution artifact generated from the `.LibPkg`. Not edited by hand. |

## Release Rules

**Mandatory**

- Releases are created only by maintainers, from `main`, after the `.LibPkg` compiles without errors and the included changes have passed review.
- Do not create a release for every component addition. Merged Pull Requests accumulate on `main` until a release is warranted.
- The release publishes the compiled `.IntLib` as a release asset.
- Each release has release notes listing components added, changed and removed.
- Releases use GitHub Releases only. There is no `Releases/` directory.

**Recommended**

- Tag format `vMAJOR.MINOR.PATCH`:
  - **MAJOR**: components removed or renamed, or pin/footprint changes that can break existing designs.
  - **MINOR**: new components or libraries.
  - **PATCH**: corrections that do not change pin or pad compatibility (parameters, silkscreen, 3D alignment).
- List any change that affects pins, pads or Component Names under a separate "Breaking" heading in the release notes.
- Do not commit the `.IntLib` to `main`; attach it to the release.
