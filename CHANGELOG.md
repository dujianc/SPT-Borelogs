# Changelog

All notable changes to GeoEQ SPT Logs are documented here.
Dates use YYYY-MM-DD.

## 1.1.0 — 2026-08-17

Recording what the field actually reports, and letting each office use
its own conventions. Every default reproduces 1.0.0, so a project you
do not edit draws exactly as before.

### Added

- **Refusal and partial penetration.** Type the driller's notation
  straight into a 15 cm increment cell — `50/75` means 50 blows for
  75 mm. The sheet prints `8-15-50/75` and the N column shows the
  notation rather than a number nobody measured. On the N-value graph
  the solid line covers measured points only; dashed connectors run to a
  refusal marker at full scale, with a legend entry.
- **Project settings — SPT and N-value**: graph scale (fixed, custom or
  auto-fit), what happens to values past the scale (clamp at 50 as in
  1.0, mark as refusal, or extend the scale), how refusal reads in the N
  column (`50/75`, `>50`, `Ref` or `R`), the test interval and first
  test depth, and the depth ruler interval.
- **Generate depths** fills the depth column at the project's test
  interval, down to the borehole depth, leaving typed rows alone.
- **Project settings — Units**: metric (default) or imperial, per
  project. Labels only — depth, RL, thickness, qu, boring diameter and
  the end-of-hole note. Values are never converted, so enter them in the
  unit the project uses. Input tables, the Header tab and the sheet
  change together.
- **Company settings — Sheet title**: BORELOG (default), BORING LOG,
  BOREHOLE LOG, BORE LOG, SOIL BORING LOG, LOG OF BORING, or your own.
  The body follows it, so a sheet headed BORING LOG says "Boring No:"
  and "End of boring".
- **Company settings — Water row label**: Borehole Water RL (default),
  Water Level, Depth to Water, Groundwater Level, Water Table, or your
  own; the unit is added automatically.
- **The project file format is documented** in the manual, with the row
  layouts and a short Python example for reading a `.sbl` directly.
- The demo project gains **BH-02**, a shallower hole through a cemented
  layer showing refusal at 50/75 and 50/50.

### Fixed

- **Unreadable input is no longer discarded in silence.** A depth or
  blow count that could not be read was skipped without a message, so a
  typo could remove a test from the drawn sheet and the exported PDF
  while the table still showed it. Those rows are now reported in the
  editor.
- **The depth ruler follows the test interval.** "Auto" previously fell
  back to a fixed 1.5 m spacing whatever the project used, and the ruler
  never printed its zero.
- **Generate depths** uses the borehole depth rather than the per-sheet
  depth, so a 10 m hole on a 30 m sheet setting no longer produces rows
  past the bottom of the hole.

### Notes

- Files written by 1.0.0 open unchanged. Every new field is optional,
  and absent fields mean the 1.0.0 behaviour.

## 1.0.0 — 2026-08-10 — first public release

### Added

- Borelog editor with live sheet preview: SPT & samples table (depth,
  15 cm blow counts or direct N-value, sample ID, D/UD type, lab
  results), strata table, per-borehole header (dual X/Y and Lat/Long
  coordinates, dates, method, water level, boring dia, classification
  standard, EGL).
- Template-style drawn sheet: ruler depth scale, sample symbols,
  seven colored soil-type symbols (Clay, Sand, Silt, Gravel, Fill,
  Organic, Rock), bold USCS group symbols in descriptions, SPT N-value
  profile (0–70 axis, refusal capped at 50), selectable groundwater
  marker with level line, automatic ~30 m pagination, legend.
- Multi-project files: one `.sbl` file holds several projects, each
  with its own boreholes, client, location, and settings.
- Explorer with right-click actions: project settings, add / import /
  rename / delete, single-borelog PDF export, and whole-project export
  — every borehole into one multi-page A4 PDF.
- Excel / CSV import: office BH-xx templates import in one click; any
  other spreadsheet opens a column-assignment window with auto-guessed
  mappings; N-only files supported.
- Company settings shared across projects: name, address, logo image,
  four header styles, accent color, row-lines toggle.
- Data stored per user: projects in `Documents\GeoEQ SPT Logs\Projects`,
  settings in `%APPDATA%\GeoEQ\SPT Logs`; the installation folder holds
  no user data.
- Update notifications at startup (silent, offline-safe) and
  Help → Check for updates; Help → User manual.
- Demo project (File → Open demo project) with generic sample data.
- Windows installer (setup.exe): per-user install without admin
  rights, Start-menu and optional desktop shortcuts, `.sbl` file
  association (double-click a project to open it), clean uninstall.
  A portable `.zip` is also available.
