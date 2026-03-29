# Building Code Analysis Checklist — Claude Code Brief

> **For use with `pdf-build-reference.md`.**
> Claude Code must read `pdf-build-reference.md` before writing any code.
> Build this as a **canvas-direct fillable PDF** using ReportLab.
> Do not ask clarifying questions — execute this brief as written.

---

## Planning Notes (Steps 1–7 completed)

**Document type:** Canvas-direct fillable form
**Rationale:** Every section contains fields users fill in per project — occupancy class, FRR values, washroom counts, LUB setbacks, etc. Not a flowing narrative.

**Page budget estimate:**
- Cover: 1 page
- Section 1 — Project Identification: 1 page (~280 pt)
- Section 2 — Building Data: 1 page (~610 pt — tight, `check()` will flow)
- Section 3 — Fire Resistance Ratings: 1 page (~220 pt)
- Section 4 — Fire Safety Systems: 1 page (~180 pt)
- Section 5 — Egress & Occupant Load: 1 page (~240 pt)
- Section 6 — Barrier Free: 1 page (~140 pt)
- Section 7 — Washroom Requirements: 1 page (~380 pt)
- Section 8 — Land Use Bylaw 1P2007: 1–2 pages (~680 pt)
- Section 9 — Notes & Sign-Off: 1 page (~200 pt)
- **Estimated total: 10–11 pages**

**Design conventions verified:**
- [x] Every section starts on a new page
- [x] All numeric values used in calculations are free-text, not dropdowns
- [x] All labels are noun phrases; instructions are in hint lines
- [x] Rev field on cover alongside Project Number
- [x] No section opens with a subhead as first element
- [x] Footer left accurately describes the form
- [x] Footer right tag is the series identifier

---

## BRIEF

Build a **canvas-direct fillable form** PDF using the `pdf-build-reference.md` specification.

---

### DOCUMENT IDENTITY

- **Title (header left, all caps):** `BUILDING CODE ANALYSIS CHECKLIST`
- **Centre label (header centre):** `Part 3 Commercial — NBC (AE) 2023`
- **Footer left:** `Amber fields = required.`
- **Footer right tag:** `design-drafting · code analysis`
- **Output file:** `building-code-analysis-checklist.pdf`
- **Version string (cover bottom-right):** `v1.0 · 2025`

---

### COVER PAGE

**Hero zone (navy, top ~52% of page):**
- Series label: `DESIGN & DRAFTING CO.`
- Document title line 1: `BUILDING CODE`
- Document title line 2: `ANALYSIS CHECKLIST`
- Subtitle: `Part 3 Commercial Projects — NBC (AE) 2023 / Alberta Building Code + Calgary 1P2007 Land Use Bylaw`

**Identification fields (content zone, white background):**

Row 1 (3 columns): `Project Name` (required, 50% CW) | `Project Number` (required, 28% CW) | `Rev` (optional, remainder)
Row 2 (2 columns): `Client / Company Name` (required) | `Date` (required)
Row 3 (2 columns): `Project Lead / Designer` (optional) | `Office / Branch` (optional)
Full width: `Project Site Address` (required)

---

### INTERIOR SECTIONS

---

#### Section 1 — Project Identification
Subtitle: General project description for code analysis header block

> No subheads — fields run directly under the section banner.

- `Project Name` | text | required | hint: `Full legal or working name of the project.`
- `Project Scope / Description` | text | required | hint: `e.g. Interior Renovations, New Construction, Change of Occupancy.`
- `Civil Address` | text | required | hint: `Civic street address of the site.`
- `Legal Address` | text | required | hint: `e.g. Lot 5, Block 32, Plan 4263JK`
- `Land Use Designation` | text | required | hint: `From the Land Use Bylaw — e.g. R-CG, C-COR1, I-B.`

---

#### Section 2 — Building Data
Subtitle: Physical and classification data required by NBC (AE) Division B Part 3

Subhead: **Building Height & Areas**
- `Building Height` | text | required | hint: `Measured per NBC (AE) 1.1.3.2 — e.g. 25' 8" or 7.82 m.`
- `Scope of Work Area` | free-text numeric | required | hint: `SF or m² — counting extent of demolition/construction area.`
- `Unit Area` | free-text numeric | optional | hint: `Total gross floor area of the unit or tenant space (SF or m²).`
- `Building Footprint` | free-text numeric | required | hint: `Total building footprint area (SF or m²).`
- `Mezzanine Areas` | free-text numeric | optional | hint: `Total mezzanine floor area if applicable (SF or m²).`

Subhead: **Number of Storeys**
Two-column row: `Above Grade` (free-text numeric, required) | `Below Grade` (free-text numeric, required)

Subhead: **Classification & Occupancy**
- `Building Classification` | text | required | hint: `NBC (AE) 3.2.2 article reference — e.g. 3.2.2.25 – Group A, Division 2, up to 2 Storeys.`
- `Major Occupancy` | dropdown | required | options: `A1 – Assembly (performing arts)`, `A2 – Assembly (worship / food / recreation)`, `A3 – Assembly (arena / pool)`, `A4 – Assembly (open air)`, `B1 – Detention`, `B2 – Care & Treatment`, `B3 – Care`, `C – Residential`, `D – Business & Personal Services`, `E – Mercantile`, `F1 – High Hazard Industrial`, `F2 – Medium Hazard Industrial`, `F3 – Low Hazard Industrial`
- `Minor Occupancy(ies)` | text | optional | hint: `List any secondary occupancies per NBC (AE) 3.1.2.`
- `Number of Streets Facing` | free-text numeric | required | hint: `Number of streets the building faces — affects sprinkler requirements.`

Subhead: **Permitted Construction**
- `Permitted Construction Type` | dropdown | required | options: `Combustible`, `Non-Combustible`, `Combustible or Non-Combustible`

---

#### Section 3 — Fire Resistance Ratings (FRR)
Subtitle: Minimum FRR requirements per NBC (AE) Table 3.2.2.A and applicable articles

> No subheads — render as a two-column grid table (Required | Provided) with the following row labels. All "Required" fields are required; all "Provided" fields are required.

Grid table columns: `Required` | `Provided`
Grid table rows:
- `Floor FRR`
- `Demising Wall FRR`
- `Mezzanine FRR`
- `Roof FRR`
- `Loadbearing Assembly FRR`

Each cell is a free-text field. Standard values: `N/A`, `45 min or Non-Combustible`, `1 hr`, `2 hr`, etc.
Hint below table: `Enter N/A where the element does not exist or no rating is required. Refer to NBC (AE) Table 3.2.2.A.`

---

#### Section 4 — Fire Safety Systems
Subtitle: Fire alarm, sprinkler, and standpipe requirements per NBC (AE) Division B Part 3

> No subheads — render as a three-column grid table (System | Required | Provided).

Grid table columns: `System` | `Required` | `Provided`
Grid table rows (System column is read-only label; Required and Provided are dropdowns: `Yes` / `No` / `N/A`):
- `Fire Alarm`
- `Sprinkler`
- `Standpipe`

Required column: required. Provided column: required.
Hint below table: `Base requirement on NBC (AE) Articles 3.2.4 (alarm), 3.2.5 (sprinkler), 3.2.6 (standpipe).`

---

#### Section 5 — Egress & Occupant Load
Subtitle: Exit count, travel distance, and occupant load per NBC (AE) Section 3.3 and 3.1.17

> No subheads.

Two-column row: `Number of Exits` (free-text numeric, required, hint: `Per NBC (AE) 3.3.1 — minimum exits required in scope of work.`) | `Maximum Exit Path of Travel` (free-text numeric, required, hint: `In metres — per NBC (AE) 3.3.1.4 or Table 3.3.1.1.`)
Two-column row: `Occupant Load` (free-text numeric, required, hint: `Total calculated occupant load for the area.`) | `Load Specified By` (text, required, hint: `Code article used — e.g. NBC (AE) 3.1.17.1.`)

---

#### Section 6 — Barrier Free Construction
Subtitle: Accessibility requirements per NBC (AE) Section 3.8

> No subheads.

- `Barrier Free Construction Required` | dropdown | required | options: `Yes`, `No`, `Partial`
- `Barrier Free Notes` | multiline text | optional | hint: `Describe scope of accessibility provisions or note exemptions.` | field height: 52 pt

---

#### Section 7 — Washroom Requirements & Provision
Subtitle: NBC (AE) 3.7.2.2.(16) — counts based on occupant / staff load

Subhead: **Required by Code**
> Hint line above table: `Per NBC (AE) 3.7.2.2.(16). Washroom counts based on staff load.`

Grid table — 3 data columns: `Men's` | `Women's` | `Universal`
Rows (all free-text numeric, required):
- `Waterclosets`
- `Lavatories`

Subhead: **Provided**

Grid table — 4 data columns: `Men's` | `Women's` | `Universal` | `Unisex`
Rows (all free-text numeric, required):
- `Waterclosets`
- `Urinals`
- `Lavatories`

- `Washroom Notes` | multiline text | optional | hint: `e.g. "Existing universal washroom complies with ABC 2019 3.8 requirements."` | field height: 44 pt

---

#### Section 8 — Land Use Bylaw 1P2007 (City of Calgary)
Subtitle: Site and development standard compliance check under Bylaw 1P2007

Subhead: **Land Use District & Use**
- `Land Use District` | text | required | hint: `As shown on the City of Calgary Land Use Map — e.g. C-COR1, I-B, M-X1.`
- `Contextual District` | dropdown | required | options: `Yes`, `No`
- `Use Classification` | dropdown | required | options: `Permitted Use`, `Discretionary Use`
- `Proposed Use` | text | required | hint: `Describe the proposed use as it appears in the Land Use Bylaw — e.g. "Food Service, Minor".`
- `Use Approved / Confirmed By` | text | optional | hint: `Reference DCA, LOC, or Development Permit number if applicable.`

Subhead: **Site Development Standards**
Two-column row: `Lot Area — Permitted` (free-text numeric, optional, hint: `m²`) | `Lot Area — Proposed` (free-text numeric, optional, hint: `m²`)
Two-column row: `Lot Width — Permitted` (free-text numeric, optional, hint: `m`) | `Lot Width — Proposed` (free-text numeric, optional, hint: `m`)
Two-column row: `Floor Area Ratio (FAR) — Permitted` (free-text numeric, optional, hint: `Max FAR per bylaw.`) | `Floor Area Ratio (FAR) — Proposed` (free-text numeric, optional, hint: `Calculated FAR for this project.`)
Two-column row: `Site Coverage — Permitted` (free-text numeric, optional, hint: `% max per bylaw.`) | `Site Coverage — Proposed` (free-text numeric, optional, hint: `% of lot covered by building.`)

Subhead: **Building Height**
Two-column row: `Maximum Height — Permitted` (text, required, hint: `Storeys or metres per bylaw — some districts use both.`) | `Proposed Building Height` (text, required, hint: `Match value entered in Section 2.`)

Subhead: **Setbacks**

Grid table — 2 data columns: `Required (m)` | `Proposed (m)`
Rows (all free-text numeric, required):
- `Front Yard`
- `Side Yard — North / Left`
- `Side Yard — South / Right`
- `Rear Yard`

Hint below table: `Enter N/A where setback does not apply or where the site is a through-lot. Measurements in metres.`

Subhead: **Parking & Loading**
Two-column row: `Parking Stalls — Required` (free-text numeric, optional, hint: `Per 1P2007 Part 4.`) | `Parking Stalls — Provided` (free-text numeric, optional)
Two-column row: `Accessible Stalls — Required` (free-text numeric, optional) | `Accessible Stalls — Provided` (free-text numeric, optional)
Two-column row: `Loading Stalls — Required` (free-text numeric, optional, hint: `Per 1P2007 Part 4.`) | `Loading Stalls — Provided` (free-text numeric, optional)
- `Parking / Loading Notes` | multiline text | optional | hint: `Note any variances, relaxations, or shared parking agreements.` | field height: 44 pt

Subhead: **Signage & Other LUB Notes**
- `Sign District` | text | optional | hint: `Sign district applicable to this parcel per 1P2007 Part 6.`
- `Additional LUB Notes` | multiline text | optional | hint: `Note any outstanding Land Use Bylaw items, relaxations, or referral comments.` | field height: 52 pt

---

#### Section 9 — Notes & Sign-Off
Subtitle: Project-level notes and document authorization

> No subheads.

- `General Notes` | multiline text | optional | hint: `Any additional code or bylaw notes not captured above.` | field height: 80 pt

Sign-off row (3 equal columns, all optional single-line text):
`Prepared By` | `Reviewed By` | `Approval Date`

---

### VALIDATION

Run the post-build validator after `canvas.save()`.
Exit non-zero if any field is clipped below `BOTTOM`.
Report field name, page number, and overflow amount in pt.
