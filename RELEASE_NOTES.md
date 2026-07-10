# Sourccey Electrical v1.3.8

## Release summary

This release contains the Sourccey v1.3.8 electrical design files and the
corresponding manufacturing package.

## Design sources

- KiCad version: 9.0
- Project: `pcb/sourccey-v1.3.8/`
- Main project: `sourccey_pcb.kicad_pro`
- Copper: 2 oz copper on the copper layers
- Includes the main schematic, hierarchical `Power Electronics.kicad_sch`
  sheet, custom DRV8874 symbol, and custom DRV8874 footprint.

## Manufacturing package

The manufacturing outputs are in `manufacturing/sourccey-v1.3.8/` and include:

- Gerber copper, solder mask, solder paste, silkscreen, and outline files
- PTH and NPTH drill files
- Gerber job file and packaged Gerber archive
- KiCad and vendor-formatted BOM files
- KiCad and vendor-formatted CPL / pick-and-place files

The BOM and placement exports should be regenerated from the released KiCad
source whenever the design changes.

## Validation

The maintainer has completed the pre-release validation checklist documented in
the README, including electrical/design-rule review, board geometry and
mounting review, component orientation review, BOM and assembly review, and
independent Gerber and drill-file inspection.

## Known limitations

- Optional STEP models referenced by the project are not included.
- Software setup and hardware-kit assembly documentation are maintained on
  the [Vulcan Robotics documentation site](https://vulcanrobotics.ai/docs) and
  may be completed separately.
