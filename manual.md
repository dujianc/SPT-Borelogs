# GeoEQ SPT Logs — User Manual

*A [GeoEQ](https://geoeq.org) software · this manual matches version 1.2.*

---

## 1. Installation

1. Download the Windows package from the
   [Releases page](https://github.com/geoeq/SPT-Borelogs/releases/latest).
2. Run the installer, or unzip the portable package anywhere and run
   `GeoEQ SPT Logs.exe`.
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
- **Sheet title** — the wording printed at the top of every sheet:
  BORELOG (default), BORING LOG, BOREHOLE LOG, BORE LOG, SOIL BORING
  LOG, LOG OF BORING, or type your own. *Boring log* is the usual term
  in the United States, *borehole log* in the UK and internationally.
  The body of the sheet follows your choice, so a sheet headed BORING
  LOG says "Boring No:" and "End of boring".
- **Water row label** — Borehole Water RL (default), Water Level, Depth
  to Water, Groundwater Level, Water Table, or your own. The unit is
  added automatically.

## 4. Project settings

Double-click a project (or right-click → Project settings):

- Project name, client, location — auto-pulled into every borelog
  header in that project.
- **Coordinate display**: X/Y, Lat/Long, or both (each borehole stores
  both pairs).
- **Water table marker**: classic symbol + level line (default),
  classic only, filled triangle, triangle + GWT label, or droplet.
- **Units**: Metric (default, m/kPa/mm) or Imperial (ft/tsf/in). This
  changes the **labels** on the input tables and the sheet — values are
  never converted, so enter them in the unit the project uses. Set per
  project, so one office can run a metric job and an imperial job side
  by side.
- **Test interval / first depth** — used by **Generate depths**, which
  fills the depth column down to the borehole depth and leaves rows you
  have already typed alone. Default 1.5 m starting at 1.5 m; set the
  first depth to 0 to start at ground level.
- **Depth ruler interval** — Auto (follows the test interval) or a
  fixed spacing.
- **N-value graph scale** — Fixed (0–70 by default, or your own full
  scale) or Auto-fit to the data.
- **Values past the scale** — Clamp at 50 (version 1.0 behaviour,
  default), Mark as refusal at the edge, or Extend the scale to fit.
- **Refusal shown as** — the notation used in the N column: as recorded
  (`50/75`, default), `>50`, `Ref`, or `R`. Note `R` is also the Rock
  stratum symbol, so it can read two ways on a sheet containing rock.
- About — free notes stored in the file.

## 5. Entering borelog data

Open a borehole (double-click). Four input tabs:

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
- **Rock core** — one row per core run, below refusal: run top and
  bottom, TCR %, SCR %, RQD %, core size (NQ, HQ…) and fractures per
  metre. Leave the tab empty for a soil-only borehole and the sheet
  is drawn exactly as before. See section 6.
- **Header** — per-borehole facts: X/Y and Lat/Long coordinates, dates,
  boring method, water RL (e.g. `(-) 5.0` places the water marker at
  5.0 m), boring dia, classification standard, EGL reduced level.

The sheet on the right redraws with every edit; use the Sheet spinner
for multi-page logs (default ~30 m per sheet).

## 6. Rock coring

When the sampler refuses, the driller pulls the split spoon and picks up
a **core barrel**. Below that depth there are no blow counts: the unit of
measurement is the **core run**, and three percentages measured off the
recovered core.

| | Counts | |
|---|---|---|
| **TCR** | everything recovered, rubble included | total core recovery |
| **SCR** | full-diameter solid cylinders only | solid core recovery |
| **RQD** | sound pieces 100 mm or longer | rock quality designation |

Enter them in the **Rock core** tab, one row per run. Run number, run
length and the rock quality word are worked out for you.

### The sheet follows the data

There is no rock/soil setting to choose. What you enter decides what is
drawn:

| SPT rows | Core runs | Sheet |
|---|---|---|
| yes | none | the ordinary borelog, unchanged |
| yes | yes | N-value graph above the rockhead, core recovery below it |
| none | yes | a rock sheet: the lab columns carry the run figures |

The **rockhead** is the top of your first core run, so the transition
line needs no setting either.

### Reading the recovery bar

RQD can never exceed SCR, which can never exceed TCR, so one bar shows
all three: the palest block is TCR, the middle SCR, the solid block RQD.
The colour is the run's rock quality — red very poor, orange poor,
yellow fair, light green good, green excellent — so a weathered zone is
visible before you read a number. The RQD figure is printed in the bar.

| RQD % | Rock quality |
|---|---|
| 0 – 25 | Very poor |
| 25 – 50 | Poor |
| 50 – 75 | Fair |
| 75 – 90 | Good |
| 90 – 100 | Excellent |

### Checks

Because the three nest, a figure out of order is a typing error, and it
is reported rather than silently corrected — as is a run bottom above
its top, a run that starts above the end of the one before it, and any
value outside 0–100. Look at the badges under the sheet.

## 7. Importing data

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

## 8. Exporting PDFs

- **One borehole**: the Export PDF button in its borelog tab (or
  right-click → Export PDF). Multi-sheet logs export all pages.
- **A whole project**: right-click the project → **Export project
  PDF** — every borehole's sheets, in order, in a **single PDF**.

What you see on screen is exactly what is exported.

## 9. Where your data lives

- **Project files** default to `Documents\GeoEQ SPT Logs\Projects` — the
  Open/Save dialogs start there. Files are plain `.sbl` (JSON), easy to
  back up, share, or sync (the folder follows OneDrive-redirected
  Documents automatically). You can of course save a project anywhere.
- **Settings** (company identity, logo, sheet appearance) live in
  `%APPDATA%\GeoEQ\SPT Logs\company.json`.
- Nothing is stored in the installation folder, so uninstalling or
  updating the app never touches your projects.

## 10. The project file format

A `.sbl` file is plain UTF-8 JSON. It is documented here so you can read
your own data — for a QA script, a bulk check across boreholes, or to
hand a profile to the [`geoeq`](https://geoeq.org) Python package —
without exporting anything first.

### Shape

```jsonc
{
  "version": 2,
  "projects": [
    {
      "id": "b5191c21",
      "name": "ABC Site Investigation",
      "client": "ABC Development LLC",
      "location": "Salt Lake City, Utah, USA",
      "about": "…",

      // presentation choices, all optional
      "units": "metric",            // or "imperial" — labels only, never a conversion
      "coord_display": "both",      // "xy" | "latlong" | "both"
      "water_marker": "classic_line",
      "spt_interval": 1.5,          // test spacing used by Generate depths
      "spt_start": 1.5,             // first test depth
      "ruler_interval": 0.0,        // 0 = Auto (follows spt_interval)
      "n_scale": "fixed",           // or "auto"
      "n_scale_max": 70.0,
      "n_overflow": "clamp",        // "clamp" | "refusal" | "extend"
      "refusal_text": "asrec",      // "asrec" | "gt" | "Ref" | "R"

      "boreholes": [
        {
          "id": "9b1aed49",
          "name": "BH-02",
          "depth": 15.0,            // total depth
          "gwt": 2.5,               // groundwater depth below EGL
          "borelog": {
            "header": {
              "coord_x": "424715", "coord_y": "4512390",
              "coord_lat": "40.7615", "coord_long": "-111.8896",
              "date_started": "2026-05-15", "date_completed": "2026-05-16",
              "method": "Hollow Stem Auger", "water_rl": "(-) 2.5",
              "dia": "100", "standard": "ASTM D-2487 & D-2488",
              "egl_rl": 0.0
            },
            "page_depth": 15.0,     // depth printed per sheet
            "spt": [ /* rows, see below */ ],
            "strata": [ /* rows, see below */ ],
            "core": [ /* core runs, see below; omitted if none */ ]
          }
        }
      ]
    }
  ]
}
```

### Row layout

Table rows are arrays of strings, in column order. Empty cells are `""`.

**`spt` — 12 cells:**

| # | Cell | Notes |
|---|---|---|
| 0 | depth | |
| 1–3 | 15 cm increments, 1st / 2nd / 3rd | `"50/75"` means **refusal**: 50 blows for 75 mm |
| 4 | N | optional; blank means N is taken as 2nd + 3rd |
| 5 | sample ID | |
| 6 | sample type | `D` or `UD` |
| 7–11 | fines %, LL, PI, qu, moisture % | |

**`strata` — 3 cells:** bottom depth, description, soil letter
(`C` clay, `S` sand, `M` silt, `G` gravel, `F` fill, `O` organic,
`R` rock).

**`core` — 7 cells** (present only where there is coring): run top, run
bottom, TCR %, SCR %, RQD %, core size, fractures per metre. Run number,
run length and the rock quality word are derived, not stored.

### Reading a file

```python
import json

with open("ABC Site Investigation.sbl", encoding="utf-8") as f:
    doc = json.load(f)

for project in doc["projects"]:
    for bh in project["boreholes"]:
        print(f"\n{bh['name']} — {bh['depth']} m, water {bh['gwt']} m")
        for row in bh["borelog"]["spt"]:
            depth, b1, b2, b3, n = row[0], row[1], row[2], row[3], row[4]
            if "/" in b3:                       # refusal, e.g. 50/75
                print(f"  {depth:>6}  refusal {b3}")
            elif n or (b2 and b3):
                print(f"  {depth:>6}  N = {n or int(b2) + int(b3)}")
```

### Compatibility

New fields are **added**, never repurposed, and every one is optional —
a reader that ignores what it does not recognise keeps working across
versions. Files written by earlier versions open unchanged and are
upgraded in memory when saved.

## 11. Updates

**Help → Check for updates** compares your version with the latest
release. If a newer version exists you get a download link; releases
marked *required* must be installed before continuing. You can always
download manually from the
[Releases page](https://github.com/geoeq/SPT-Borelogs/releases/latest).

## 12. Tips & FAQ

- **My water marker didn't move** — the marker follows the number in
  the Water RL header field ("(-) 5.0" → 5.0 m below EGL).
- **Two samples at one depth** (a D and a UD): the sheet shows a single
  merged row — the UD identity with the SPT blows and combined lab
  values.
- **Refusal in cemented ground** — type the driller's notation straight
  into the increment cell: `50/75` means 50 blows for 75 mm. The sheet
  prints `8-15-50/75`, the N column shows the notation instead of a
  number nobody measured, and the profile breaks to a refusal marker at
  full scale rather than drawing a point as if the test finished.
- **N greater than the scale** plots capped at 50 by default, as in
  version 1.0; Project settings → *Values past the scale* changes that
  to a refusal marker or an extended scale. The printed value always
  keeps the real number.
- **Old files**: project files from earlier versions open unchanged —
  they are upgraded in memory and saved in the new format.

---

© GeoEQ · [geoeq.org](https://geoeq.org)
