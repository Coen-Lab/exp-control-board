# CLAUDE.md

Open-hardware repo for a lab experiment control board: KiCad electronics, Arduino Nano firmware and a 3D-printable enclosure. Version 3 is current; Versions 1 and 2 are frozen archives. There is no software build system, so work is editing KiCad files, firmware text and Markdown.

## Layout map

| Path | Holds | Go here for |
| --- | --- | --- |
| `README.md` | Repo landing page, feature list, licence badge | Top-level feature list or purchase text |
| `Version3/README.md` | Current usage guide: power, rails, Peltier, photodiode, valves, current drivers, Arduino I/O | Any user-facing description of the board |
| `Version3/Firmware.txt` | Arduino sketch source, stored as `.txt` (about 160 lines, single file) | Pins, PID gains, flipper and sync logic |
| `Version3/Electronics/pipcb.kicad_pro`, `pipcb.kicad_pcb`, `pipcb.kicad_sch` | KiCad project, board layout, root schematic | Layout or top-level schematic changes |
| `Version3/Electronics/{al8861,drivers,lmr33630,power_rails}.kicad_sch` | Hierarchical sub-sheets: `drivers` and `power_rails` hang off the root; `al8861` and `lmr33630` hang off `power_rails` | Circuit changes in a specific block |
| `Version3/Electronics/pipcb.pdf` | Schematic PDF export | Quick read of the circuit without KiCad |
| `Version3/Electronics/Manufacture/` | Fabrication outputs: `bom.csv`, `designators.csv`, `positions.csv`, `netlist.ipc`, `gerber.zip`, `gerber/` | Ordering or checking a manufacturing run |
| `Version3/Enclosure/` | `Enclosure_Base` and `Enclosure_Lid`, each as `.ipt` (Inventor source) and `.stl` (print file) | Enclosure changes |
| `XLegacyVersions/Version1/` | Archive: `Case/`, `Electronics/ExpCB/`, `Firmware.ino`, `Images/`, README | Only when asked about v1 |
| `XLegacyVersions/Version2/` | Archive: `Electronics/`, `Images/`, README (no firmware, no enclosure) | Only when asked about v2 |

## Build, run, test

There is no package.json, Makefile, pyproject, test suite or CI workflow in the repo. Do not invent one. The only documented procedures are in `Version3/README.md`:

- Firmware: copy `Version3/Firmware.txt` into the Arduino IDE as a sketch, target Arduino Nano, and flash over USB. The README says to use the serial logger (the sketch calls `Serial.begin(9600)`) to read temperature and PWM output.
- Libraries the sketch includes: `OneWire`, `DallasTemperature`, `PID_v1`.
- Boards: open `Version3/Electronics/pipcb.kicad_pro` in KiCad. Gerbers and pick and place files are meant for an assembly service (the README names JLCPCB).
- Enclosure: print the `.stl` files; the `.ipt` files need Autodesk Inventor.

## Conventions

- Project and board files keep the name `pipcb` (`pipcb.kicad_*`, gerber prefix `pipcb-`) across all versions, so identical filenames in different version folders are different designs.
- Each design version is self-contained in its own folder; a new revision is a copy of the folder, not an edit in place of the old one.
- KiCad layout is hierarchical: `pipcb.kicad_sch` references `drivers` and `power_rails`, and `power_rails.kicad_sch` references `al8861` and `lmr33630`, all in the same folder. Keep sub-sheet files beside the root sheet.
- `Version3/Electronics/Manufacture/` is generated output. Its `gerber/` folder duplicates `bom.csv`, `designators.csv` and `positions.csv` and is also zipped as `gerber.zip`; all copies must come from the same board revision.
- `bom.csv` has columns `Designator, Footprint, Quantity, Value, LCSC Part #`, one row per grouped value, so the LCSC part number is the sourcing key.
- Version 1 uses older KiCad export extensions (`.gtl`, `.gbl`, `.gm1`, `.g2`, `.g3`); Versions 2 and 3 use `.gbr`.
- `.gitignore` is the standard KiCad ignore list (backups, autosaves, `*.net`, `*.dsn`, `*.ses`, `*.xml`, `fp-info-cache`). Note `*.xml` is ignored, so an exported BOM in XML will not be tracked.

## Traps and gotchas

- Do not hand-edit anything in `Manufacture/` or `gerber/`; regenerate from KiCad and replace the whole set, including `gerber.zip`.
- Do not hand-edit `.kicad_pcb`, `.kicad_sch` or `.kicad_pro` text unless the change is trivial; they are tool-generated S-expressions and an edit can corrupt the file. Prefer the KiCad tooling.
- `.stl`, `.ipt`, `.pdf`, `.zip` and `.png` are binary; do not read them. Changing an enclosure `.stl` without the matching `.ipt` leaves them out of sync.
- The firmware is `Firmware.txt`, not `.ino` (Version 1 is the only one with `Firmware.ino`). It must be renamed or pasted into a sketch to compile.
- Firmware timing and pins are coupled to the hardware: the flipper runs from a Timer1 interrupt (`OCR1A = 1550`, 1024 prescaler, about 10 Hz), pins are `#define`d at the top, `TARGET_TEMP_C` sets the Peltier setpoint, and the PID constants are in the `PID myPID(...)` line. The comment in the file says its constants are a guess; the README says they were tuned for one particular box.
- The firmware's commented-out rail voltage prints use `analogRead(4)` and `analogRead(5)` with a fixed scale factor, and the README mentions rail voltages in the serial log; the active code only prints temperature and PWM.
- The Peltier overheat input (OHT) is described in the README as normally closed, but the firmware does not read an overheat pin; the README suggests modifying the code if that matters.
- Version folders are `XLegacyVersions/VersionN/` with `Images/` capitalised, but the Version 2 README references `images/image1.png` in lowercase. Links break on case-sensitive file systems.
- Feature counts differ by version (v2: two current drivers and three valve drivers; v3: three current drivers and two valve drivers). Do not copy feature text between version READMEs without checking.
- The root README and `Version3/README.md` both carry the feature list and the same hero image; keep them consistent when editing either.
- Images in the READMEs are GitHub-hosted asset URLs, not files in the repo.

## Deeper docs

- `README.md`: overview, feature list, purchasing note, licence (CC BY-NC-SA 4.0; `LICENSE` holds the full text).
- `Version3/README.md`: handling precautions, per-section wiring and operation (power in and out, Peltier, photodiode, valve drivers, constant current drivers, Arduino I/O) and manufacturing notes.
- `XLegacyVersions/Version1/README.md` and `XLegacyVersions/Version2/README.md`: assembly and usage guides for the older boards.
