# Sourccey Electrical

Open-source hardware design files for the Sourccey electrical system.

This repository is intended to contain the complete KiCad design source,
component data, and documentation needed to inspect, modify, manufacture,
and assemble the hardware.

## Status

This repository contains the Sourccey v1.3.8 electrical design release.
Always review the release notes and complete your own manufacturing and safety
validation before building hardware.

## Repository layout

The repository is organized by editable design sources, manufacturing outputs,
and supporting documentation:

```text
.
├── pcb/
│   ├── <board-name>.kicad_pro
│   ├── <board-name>.kicad_sch
│   ├── <board-name>.kicad_pcb
│   ├── symbols/             # Project-specific KiCad symbols
│   └── footprints/          # Project-specific KiCad footprints
├── bom/
│   ├── bom.csv              # Human/reviewable bill of materials
│   └── pos.csv              # Pick-and-place / centroid data
├── fab/                     # Released Gerbers and drill files, if tracked
├── docs/                    # Design notes, assembly, and test instructions
└── README.md
```

The generic layout above describes the intended convention for additional
boards. The current checked-in release is organized as follows:

```text
.
|-- pcb/sourccey-v1.3.8/
|   |-- *.kicad_pro       # KiCad project
|   |-- *.kicad_sch       # Main and hierarchical schematics
|   |-- *.kicad_pcb       # PCB layout
|   |-- symbols/           # Project-specific KiCad symbols
|   |-- footprints/        # Project-specific KiCad footprints
|   `-- models/            # Optional 3D model references
|-- manufacturing/sourccey-v1.3.8/
|   |-- gerbers/           # Gerbers, drill files, and Gerber archive
|   |-- bom/               # Bill of materials exports
|   `-- cpl/               # Pick-and-place / component placement exports
|-- docs/                  # Design notes, assembly, and test instructions
`-- README.md
```

Each board should keep its `.kicad_pro`,
`.kicad_sch`, and `.kicad_pcb` files together. Do not commit KiCad lock files,
personal project settings, or backup files.

## Opening the design

The current design is Sourccey v1.3.8 and was saved with KiCad 9.0.

1. Install [KiCad 9](https://www.kicad.org/download/), including the standard
   symbol, footprint, and 3D-model libraries.
2. Clone this repository.
3. Open
   `pcb/sourccey-v1.3.8/sourccey_pcb.kicad_pro`.
4. Review the schematic before opening or editing the PCB.
5. Update the project libraries only with care: project-local symbols and
   footprints should be stored in this repository so the design remains
   reproducible.

The project includes its hierarchical `Power Electronics.kicad_sch` sheet and
the custom DRV8874 symbol and footprint. See the README under the version's
`models/` directory for two optional STEP models that are not yet included.

## BOM and POS data

The `manufacturing/sourccey-v1.3.8/` directory contains the files needed to
order and assemble the board:

- Gerbers for copper, solder mask, solder paste, silkscreen, and the board
  outline, plus the Gerber job file and packaged archive.
- PTH and NPTH drill files for plated and non-plated holes.
- A KiCad BOM export and a vendor-formatted BOM for purchasing.
- KiCad and vendor-formatted CPL (component placement / pick-and-place) data.

These are manufacturing outputs, not the editable source of truth. Regenerate
them from the released KiCad project whenever the design changes.

The BOM should identify at least:

- Reference designators
- Quantity
- Value and footprint
- Manufacturer and manufacturer part number, when known
- Distributor part number, when known
- Designator exclusions or DNP status

The POS file should identify each populated reference, X/Y position, rotation,
side, and the coordinate origin used for the export. BOM and POS exports are
manufacturing inputs: regenerate them from the released KiCad sources and
record the KiCad version and export settings in the release notes.

## Manufacturing components

Manufacturing outputs are generated from the released PCB source. A release
should include, or link to, the corresponding Gerber, drill, drawing, BOM, and
POS package. Keep generated outputs in `fab/` or a release artifact rather than
mixing them with editable KiCad source files.

The checked-in v1.3.8 outputs are under
`manufacturing/sourccey-v1.3.8/`, including original and vendor-formatted BOM
and CPL files, Gerbers, drill files, and the Gerber archive.

The PCB uses 2 oz copper on the copper layers. Confirm the fabricator's stackup
and copper-weight capabilities before ordering.

Before manufacturing, check at minimum:

- Schematic and PCB annotations are synchronized.
- Electrical rules and design rules pass.
- Board outline, mounting holes, clearances, and layer stack are correct.
- Footprints and 3D/component orientations are correct.
- BOM substitutions, DNP parts, polarity, and assembly side are reviewed.
- Gerbers and drill files are inspected in a separate viewer.

## Documentation

See the [Vulcan Robotics documentation](https://vulcanrobotics.ai/docs) for the
broader Sourccey project. This repository is the electrical reference for
wiring and board-level build details. The documentation site also links to the
related hardware, software, and LeRobot-compatible repositories. Software setup
and hardware-kit assembly instructions are currently listed there as coming
soon.

## Release notes

See [RELEASE_NOTES.md](RELEASE_NOTES.md) for the v1.3.8 release summary,
manufacturing package details, and validation record.

## Contributing

Please open an issue before making a substantial design change. Pull requests
should explain the motivation, identify affected boards, and include updated
schematic/PCB files and regenerated BOM/POS or manufacturing outputs when
applicable. Include screenshots or test results for changes that affect layout,
assembly, or electrical behavior.

## Licensing

Unless stated otherwise in a subdirectory, this project is released under the
[CERN Open Hardware Licence Version 2 - Strongly Reciprocal
(CERN-OHL-S-2.0)](https://gitlab.com/ohwr/project/cernohl/-/wikis/uploads/819d71bea3458f71fba6cf4fb0f2de6b/cern_ohl_s_v2.txt).
This license permits personal, educational, commercial, and manufacturing use.
If you distribute a modified design or a product based on it, you must preserve
the notices, make the corresponding source available, and license the modified
covered source under CERN-OHL-S-2.0. Private modifications do not need to be
published unless they are distributed.

Add the full license text as `LICENSE` before publishing the repository.

Third-party symbols, footprints, models, and datasheets may have separate
licenses. Preserve their notices and verify redistribution rights before
committing them.

## Disclaimer

This hardware is provided without warranty. You are responsible for reviewing
the design, complying with applicable laws and safety requirements, and
validating any manufactured or modified hardware before use.
