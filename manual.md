# SPT Borelog — User Manual

*A [GeoEQ](https://geoeq.org) software · this manual matches version 1.0.*

---

## 1. Installation

1. Download the Windows package from the
   [Releases page](https://github.com/geoeq/SPT-Borelogs/releases/latest).
2. Run the installer, or unzip the portable package anywhere and run
   `SPT Borelog.exe`.
3. Requirements: Windows 10 / 11, 64-bit.

To try the app immediately, open **File → Open demo project** — a
complete borelog imported from a real field workbook.

## 2. Concepts: file → projects → boreholes

- A **project file** (`.sbl`) can hold **one or more projects**.
- Each **project** carries the shared information: project name, client,
  location, coordinate display, water-marker style, and notes.
- Each project contains **boreholes**; every borehole has one borelog
  (SPT data, strata, header) and draws its sheet live.

The explorer tree on the left shows this hierarchy. **Right-click**
anything for its actions:

| Right-click on… | Actions |
|---|---|
| a **project** | Project settings · Add borehole · Import borehole · **Export project PDF (all boreholes, one file)** · Rename · Delete |
| a **borehole** | Open borelog · Rename · Import data · Export PDF · Delete |
| empty space | Add project |

## 3. One-time setup: Company settings

**File → Company settings** — everything here is drawn on every sheet
of every project:

- Company name and address
- **Logo image** (PNG/JPG)
- **Header style**: Letterhead (default), Blue title bar, Three panels,
  or Boxed logo card
- **Accent colour** (title, rules, borehole number)
- Light horizontal row lines on/off

## 4. Project settings

Double-click a project (or right-click → Project settings):

- Project name, client, location — auto-pulled into every borelog
  header in that project.
- **Coordinate display**: X/Y, Lat/Long, or both (each borehole stores
  both pairs).
- **Water table marker**: classic symbol + level line (default),
  classic only, filled triangle, triangle + GWT label, or droplet.
- About — free notes stored in the file.

## 5. Entering borelog data

Open a borehole (double-click). Three input tabs:

- **SPT & samples** — one row per test/sample: depth, the three 15 cm
  blow counts (N is computed as 2nd + 3rd), or type a direct **N**
  value when blow counts are unknown; sample ID; type D (split spoon) /
  UD (Shelby); lab results (fines %, LL, PI, qu, moisture). The tables
  accept Excel-style copy/paste.
- **Strata** — bottom depth, description, and soil type letter:
  **C** Clay · **S** Sand · **M** Silt · **G** Gravel · **F** Fill ·
  **O** Organic · **R** Rock. The letter is guessed from the
  description ("Sandy SILT" → M) and sets the colored symbol column.
  A USCS symbol at the end of a description ("…SILT,ML") is printed
  bold automatically.
- **Header** — per-borehole facts: X/Y and Lat/Long coordinates, dates,
  boring method, water RL (e.g. `(-) 5.0` places the water marker at
  5.0 m), boring dia, classification standard, EGL reduced level.

The sheet on the right redraws with every edit; use the Sheet spinner
for multi-page logs (default ~30 m per sheet).

## 6. Importing data

**From the office BH-xx Excel template** — right-click a project →
Import borehole: the borehole is created with header, samples, blows
and strata in one click.

**From any other Excel/CSV** — the same menu accepts any tabular file.
An **Assign columns** window opens showing each file column with sample
values and an auto-guessed target field ("Dec" → Strata description,
"SPT N" → N-value…). Correct anything that was guessed wrong, press OK,
and the rows are inserted. Files with only an N column (no blow counts)
work — the N goes into the direct-N column. Consecutive rows with the
same description merge into one stratum automatically.

## 7. Exporting PDFs

- **One borehole**: the Export PDF button in its borelog tab (or
  right-click → Export PDF). Multi-sheet logs export all pages.
- **A whole project**: right-click the project → **Export project
  PDF** — every borehole's sheets, in order, in a **single PDF**.

What you see on screen is exactly what is exported.

## 8. Updates

**Help → Check for updates** compares your version with the latest
release. If a newer version exists you get a download link; releases
marked *required* must be installed before continuing. You can always
download manually from the
[Releases page](https://github.com/geoeq/SPT-Borelogs/releases/latest).

## 9. Tips & FAQ

- **My water marker didn't move** — the marker follows the number in
  the Water RL header field ("(-) 5.0" → 5.0 m below EGL).
- **Two samples at one depth** (a D and a UD): the sheet shows a single
  merged row — the UD identity with the SPT blows and combined lab
  values.
- **N greater than 50** plots capped at 50 (refusal) on the 0–70 axis;
  the printed value keeps the real number.
- **Old files**: project files from earlier versions open unchanged —
  they are upgraded in memory and saved in the new format.

---

© GeoEQ · [geoeq.org](https://geoeq.org)
