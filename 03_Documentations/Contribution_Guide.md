# Contribution Guide

## Workflow

1. **Search first.** In the Components panel (with the latest `.IntLib` installed) and in the repository, search by MPN and by function. Do not add a component that already exists. If it exists with an error, fix it instead of adding a second copy.
2. **Find the library.** Choose the category by primary function ([Library Organization](Library_Organization.md)) and use its existing `.SchLib` and `.PcbLib`. Create a new library only if none is suitable.
3. **Add the component.** Create the symbol, reuse or create the footprint, attach the 3D model, and fill all fields according to the [Naming Convention](Naming_Convention.md). One or several components can be added in the same contribution.
4. **Add supporting files.** Datasheet PDF, STEP model if applicable, and a short component note (`Docs/<MPN>.md`: source of the footprint, any deviations from the datasheet, known limitations).
5. **Verify.** Check symbol pins, footprint, parameters and 3D alignment against [Component Requirements](Component_Requirements.md). Compile the `.LibPkg` and confirm no errors if you added a new library or need an updated `.IntLib`.
6. **Commit and open a Pull Request.**
   - Branch: `add/<MPN>` or `fix/<MPN>` (*Recommended*).
   - Commit message: `Add INA226AIDGSR to Sensors library`.
   - PR description: components added or changed, library file(s) touched, datasheet revision used.
7. **Wait for review.** The reviewer uses the [Review Checklist](Review_Checklist.md). Address comments in the same PR. Do not merge your own PR.

## Editing Binary Libraries

`.SchLib`, `.PcbLib` and `.IntLib` are binary files. Git cannot merge them.

**Mandatory**

- Before editing a `.SchLib` or `.PcbLib`, check open Pull Requests and tell the maintainers (issue or message) which library file you will edit.
- Only one person edits a given library file at a time.
- If two PRs change the same file, the second contributor pulls the merged version and re-adds their components. Do not resolve by overwriting the file.
- Pull the latest `main` before starting and again before opening the PR.

*Recommended:* keep contributions small and short-lived to reduce the blocking window.
