# Naming Convention

All examples use the **Texas Instruments INA226** current and power monitor (VSSOP-10, DGS package, orderable part `INA226AIDGSR`).

Levels: **Mandatory** rules are enforced in review. **Recommended** rules are expected unless there is a reason.

## Generic vs Manufacturer-Specific Components

| | Generic | Manufacturer-specific |
|---|---|---|
| Represents | An interchangeable part defined by value and package | One exact orderable part |
| Used for | Resistors, capacitors, inductors, standard LEDs | ICs, MOSFETs, connectors, diodes, anything where substitutes are not equivalent |
| Component Name | `<TYPE>_<PACKAGE>`, e.g. `RES_0603` | Manufacturer Part Number, e.g. `INA226AIDGSR` |
| Comment | `=Value` | Part identifier, e.g. `INA226` |
| Manufacturer / MPN | Left empty (chosen at BOM stage) | **Mandatory** |

Mandatory: a component is either fully generic or fully specific. Do not mix (for example a generic name with a hard-coded MPN).

## Field Reference

### Component Name

- **Purpose:** Unique library identifier (Design Item ID). It is what users search for in the Components panel.
- **Format:** Specific: the exact orderable MPN. Generic: `<TYPE>_<PACKAGE>` with `RES`, `CAP`, `IND`, `LED`. No spaces. One component per MPN; do not duplicate a part for reel/tube variants.
- **Correct:** `INA226AIDGSR`
- **Incorrect:** `INA226 current monitor` (description), `INA226_new` / `INA226_v2` (versioning belongs in Git), `ina226aidgsr` (case differs from datasheet)

### Designator

- **Purpose:** Schematic reference prefix. Altium numbers it on placement (`U1`, `U2`, ...).
- **Format:** Prefix + `?`. Mandatory prefixes:

| Prefix | Type | Prefix | Type |
|---|---|---|---|
| `R?` | Resistor | `Q?` | Transistor / MOSFET |
| `C?` | Capacitor | `U?` | IC / module |
| `L?` | Inductor | `J?` | Connector |
| `D?` | Diode / LED / TVS | `F?` | Fuse |
| `Y?` | Crystal / oscillator | `SW?` | Switch |

- **Correct:** `U?`
- **Incorrect:** `INA226` (part number), `U1` (hard-coded index), `IC?` (non-standard prefix)

### Comment

- **Purpose:** Text displayed beside the symbol on the schematic. It must tell a reader what the part is.
- **Value vs part number:**
  - Show the **value** (`=Value`) when the part is defined by its value: resistors, capacitors, inductors.
  - Show the **part identifier** when the part is defined by what it is: ICs, MOSFETs, diodes, connectors. Use the family or base name without package/packing suffix when variants share one symbol.
- **Format:** Generic: `=Value`. Specific: short part identifier.
- **Correct:** `INA226`; `=Value` (resistor)
- **Incorrect:** `Current and power monitor` (that is the Description), `U?` (that is the Designator), empty, `INA226AIDGSR / Texas Instruments`

### Description

- **Purpose:** Human-readable function summary for search and BOM.
- **Format:** `<Function>, <key specs>, <package>`. One line. No manufacturer name, no MPN.
- **Correct:** `Current/power monitor, I2C/SMBus, 36 V common-mode, 16-bit ADC, VSSOP-10`
- **Incorrect:** `Texas Instruments INA226AIDGSR` (manufacturer data), `INA226` (just the name), `Good chip for current measurement`

### Manufacturer

- **Purpose:** Identifies the part maker for sourcing and BOM.
- **Format:** Full official company name, same spelling in every component.
- **Correct:** `Texas Instruments`
- **Incorrect:** `TI`, `Texas Inst.`, `texas instruments`

### Manufacturer Part Number

- **Purpose:** The exact orderable part; the key for procurement.
- **Format:** As printed in the datasheet ordering table. Parameter name must be exactly `Manufacturer Part Number`.
- **Correct:** `INA226AIDGSR`
- **Incorrect:** `INA226` (family, not orderable), `INA226 (VSSOP)`, a distributor code such as a Digi-Key number

### Datasheet

- **Purpose:** Link from the component to its source document.
- **Format:** Stable manufacturer URL to the PDF. A copy is committed as `Datasheets/<MPN>_Datasheet.pdf` (see [Library Organization](Library_Organization.md)).
- **Correct:** `https://www.ti.com/lit/ds/symlink/ina226.pdf`
- **Incorrect:** `C:\Users\name\Downloads\ina226.pdf`, a distributor product page, empty

### Footprint Name

- **Purpose:** Searchable name of the PCB footprint linked to the component.
- **Format:** `<Package>-<Pins>_<PackageCode>_<Length>x<Width>mm_P<Pitch>mm[_<Variant>]`. Passives: `<R|C|L>_<Size>_<Metric>Metric`. Use IPC-7351 density suffixes only if the library applies them consistently.
- **Correct:** `VSSOP-10_DGS_3.0x3.0mm_P0.50mm`
- **Incorrect:** `INA226` (part name, not package), `VSSOP10`, `footprint_new`

### 3D Model Name

- **Purpose:** Identifies the STEP model attached to the footprint.
- **Format:** Identical to the Footprint Name, plus `.step` for the file. Handling rules are in [Component Requirements](Component_Requirements.md).
- **Correct:** `VSSOP-10_DGS_3.0x3.0mm_P0.50mm.step`
- **Incorrect:** `model1.step`, `INA226.step` (names the part, not the package; breaks reuse across parts sharing a package)

Footprints and 3D models are shared by every part with the same package. Reuse an existing footprint instead of creating a duplicate.

## INA226 Example

| Field | Value |
|---|---|
| Component Name | `INA226AIDGSR` |
| Designator | `U?` |
| Comment | `INA226` |
| Description | `Current/power monitor, I2C/SMBus, 36 V common-mode, 16-bit ADC, VSSOP-10` |
| Manufacturer | `Texas Instruments` |
| Manufacturer Part Number | `INA226AIDGSR` |
| Datasheet | `https://www.ti.com/lit/ds/symlink/ina226.pdf` |
| Footprint Name | `VSSOP-10_DGS_3.0x3.0mm_P0.50mm` |
| 3D Model Name | `VSSOP-10_DGS_3.0x3.0mm_P0.50mm.step` |
| Category / library | `Components/Sensors/` |

## Examples by Component Type

| | Resistor (generic) | Capacitor (specific) | IC | Connector | MOSFET |
|---|---|---|---|---|---|
| Component Name | `RES_0603` | `GRM188R71C104KA01D` | `INA226AIDGSR` | `B4B-PH-K-S` | `IRLML6402TRPBF` |
| Designator | `R?` | `C?` | `U?` | `J?` | `Q?` |
| Comment | `=Value` | `100nF` | `INA226` | `B4B-PH-K-S` | `IRLML6402` |
| Description | `Resistor, 0603` | `Capacitor, 100 nF, 16 V, X7R, 0603` | `Current/power monitor, I2C/SMBus, 16-bit ADC, VSSOP-10` | `Connector, 4-pin, 2.0 mm pitch, vertical, through-hole` | `P-channel MOSFET, -20 V, -3.7 A, SOT-23` |
| Manufacturer | none | `Murata` | `Texas Instruments` | `JST` | `Infineon` |
| MPN | none | `GRM188R71C104KA01D` | `INA226AIDGSR` | `B4B-PH-K-S` | `IRLML6402TRPBF` |
| Footprint Name | `R_0603_1608Metric` | `C_0603_1608Metric` | `VSSOP-10_DGS_3.0x3.0mm_P0.50mm` | `JST_PH_B4B-PH-K-S_1x04_P2.00mm_Vertical` | `SOT-23-3_2.9x1.3mm_P0.95mm` |
| 3D Model Name | `R_0603_1608Metric.step` | `C_0603_1608Metric.step` | `VSSOP-10_DGS_3.0x3.0mm_P0.50mm.step` | `JST_PH_B4B-PH-K-S_1x04_P2.00mm_Vertical.step` | `SOT-23-3_2.9x1.3mm_P0.95mm.step` |

Notes:

- The resistor's value (`10k`, `1%`) is set on placement through the `Value` parameter; for the capacitor the fixed value is the Comment because the component is a specific part.
- Verify every example MPN and package dimension against the manufacturer datasheet before copying it into a library.
