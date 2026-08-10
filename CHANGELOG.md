# Changelog

All notable changes to GeoEQ SPT Logs are documented here.
Dates use YYYY-MM-DD.

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
