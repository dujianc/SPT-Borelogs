# SPT Borelog

Professional SPT borehole log software for geotechnical engineers —
enter or import field data, get clean template-style borelog sheets and
print-ready PDFs in minutes.

> **This repository distributes ready-to-run builds only.**
> Download the latest version from the
> **[Releases page](https://github.com/geoeq/SPT-Borelogs/releases/latest)**.

---

## Download & install

1. Open the **[latest release](https://github.com/geoeq/SPT-Borelogs/releases/latest)**.
2. Download the Windows package (`SPT-Borelog-<version>-setup.exe` or
   the portable `.zip`).
3. Run the installer (or unzip anywhere and run `SPT Borelog.exe`).

**Requirements:** Windows 10 / 11, 64-bit. No other software needed.

## What it does

- **Project explorer** — one file can hold several projects, each with
  its own boreholes. Right-click anything for actions (settings,
  import, rename, export, delete).
- **Borelog editor** — SPT & samples table (depth, 15 cm blow counts or
  a direct N-value, sample ID, D/UD type, lab results), strata table
  with 7 colored soil-type symbols (Clay, Sand, Silt, Gravel, Fill,
  Organic, Rock), dual X/Y + Lat/Long coordinates, water-table marker
  styles.
- **Live drawn sheet** — template-style borelog with ruler depth scale,
  bold USCS symbols, N-value profile, groundwater marker, automatic
  pagination (~30 m per sheet) and legend. What you see is what prints.
- **Excel / CSV import** — the office BH-xx template imports in one
  click; any other spreadsheet opens a column-assignment window
  (auto-guessed, you confirm) before the data enters the tables.
- **PDF export** — one borelog, or a whole project (every borehole) as
  a single multi-page A4 PDF.
- **Your branding** — company name, address and logo, four header
  styles, custom accent colour; set once, applied to every sheet.

## Getting started

1. Start the app and open **File → Open demo project** to explore a
   ready-made borelog.
2. **File → Company settings** — enter your company name, address and
   logo (drawn on every sheet).
3. Right-click the project in the explorer → **Add borehole** (or
   **Import borehole from Excel / CSV**) and start entering data — the
   sheet redraws live.
4. Right-click the project → **Export project PDF** for a single PDF of
   all boreholes.

## Updates

The app checks this repository for new versions
([`updates/latest.json`](updates/latest.json)). When a newer release is
available you are notified at startup; some releases can be marked
**required**, in which case the app asks you to update before
continuing. You can always download the newest build manually from the
Releases page.

## Support

- Found a problem or have a request? Open an
  [issue](https://github.com/geoeq/SPT-Borelogs/issues).

## License

© GEOTECH ENGINEERING LTD. All rights reserved.
This repository contains compiled builds for end users; the source code
is not published here. Redistribution of the binaries without
permission is not allowed.
