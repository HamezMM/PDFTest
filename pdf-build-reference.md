# PDF Build Reference
## For Claude Code — Design & Drafting Company

This is the complete technical specification for building PDFs in this document system. Read it fully before writing any code. All values here have been validated against rendered output.

---

## 1. Toolchain and Dependencies

All PDFs are built with **Python + ReportLab**.

| Mode | Use when | Key class |
|---|---|---|
| **Canvas-direct** | Fillable forms, precise layout control | `reportlab.pdfgen.canvas.Canvas` |
| **Platypus flowable** | Long-form documents with reflowing text | `reportlab.platypus.BaseDocTemplate` |

Never mix both in a single document.

Install dependencies:
```bash
pip install reportlab fonttools brotli --break-system-packages
npm install @fontsource/jost
```

---

## 2. Font Setup

The document font is **Jost**. It must be loaded from TTF files. Convert from the npm package:

```python
from fontTools.ttLib import TTFont as FTFont

weight_map = {
    'node_modules/@fontsource/jost/files/jost-latin-300-normal.woff2': 'Jost-Light.ttf',
    'node_modules/@fontsource/jost/files/jost-latin-400-normal.woff2': 'Jost-Regular.ttf',
    'node_modules/@fontsource/jost/files/jost-latin-400-italic.woff2': 'Jost-Italic.ttf',
    'node_modules/@fontsource/jost/files/jost-latin-500-normal.woff2': 'Jost-Medium.ttf',
    'node_modules/@fontsource/jost/files/jost-latin-700-normal.woff2': 'Jost-Bold.ttf',
}
for src, dst in weight_map.items():
    tt = FTFont(src)
    tt.flavor = None
    tt.save(dst)
```

Register at the top of every build script before any drawing code:

```python
from reportlab.pdfbase import pdfmetrics
from reportlab.pdfbase.ttfonts import TTFont

pdfmetrics.registerFont(TTFont('Jost',        'Jost-Regular.ttf'))
pdfmetrics.registerFont(TTFont('Jost-Bold',   'Jost-Bold.ttf'))
pdfmetrics.registerFont(TTFont('Jost-Medium', 'Jost-Medium.ttf'))
pdfmetrics.registerFont(TTFont('Jost-Light',  'Jost-Light.ttf'))
pdfmetrics.registerFont(TTFont('Jost-Italic', 'Jost-Italic.ttf'))
pdfmetrics.registerFontFamily(
    'Jost',
    normal='Jost',
    bold='Jost-Bold',
    italic='Jost-Italic',
    boldItalic='Jost-Bold'
)
```

**Critical:** AcroForm interactive fields cannot use Jost. Use `fontName="Helvetica"` inside every `acroForm.textfield()`, `acroForm.choice()`, and `acroForm.checkbox()` call. Static drawn text uses Jost normally.

---

## 3. Page Constants

```python
from reportlab.lib.pagesizes import letter
from reportlab.lib.units import inch

W, H   = letter          # 612.0 × 792.0 points — US Letter only
MARGIN = 0.60 * inch     # forms (0.65 for guides — never below 0.55 or above 0.75)
CW     = W - 2 * MARGIN  # usable content width
HDR_H  = 0.42 * inch     # header bar height
FTR_H  = 0.42 * inch     # footer zone height
BOTTOM = 0.62 * inch     # lowest safe y-coordinate for any content
```

Interior page content area runs from `BOTTOM` to `H - HDR_H - 0.12*inch`. Cover pages are exempt — they draw to absolute coordinates and manage their own space.

---

## 4. Colour Palette

Import and use only these colours. No ad-hoc hex values anywhere in the build script.

```python
from reportlab.lib.colors import HexColor, black, white

# Primary
NAVY   = HexColor("#1A2744")   # headers, banners, strong text
NAVY2  = HexColor("#1E2D50")   # subhead bars, table headers (alt)
AMBER  = HexColor("#D97706")   # accent bars, required field borders, highlights
AMBER2 = HexColor("#FEF3C7")   # required field fill, warning callout fill
AMBER3 = HexColor("#92400E")   # warning callout text

# Semantic
GREEN  = HexColor("#16A34A")   # tip callout stroke
GREEN2 = HexColor("#DCFCE7")   # tip callout fill
BLUE2  = HexColor("#EFF6FF")   # info callout fill
BLUE3  = HexColor("#1E40AF")   # info callout text (sparingly)
RED    = HexColor("#DC2626")   # error callout stroke
RED2   = HexColor("#FEF2F2")   # error callout fill

# Neutral
SLATE  = HexColor("#64748B")   # hint text, secondary labels
MUTED  = HexColor("#94A3B8")   # page numbers, footer text, de-emphasised
LIGHT  = HexColor("#F8F7F4")   # optional field fill, alternating row (warm)
LIGHT2 = HexColor("#F1F5F9")   # block header fill, alternating row (cool)
BORDER = HexColor("#E2E8F0")   # all borders, dividers, table grid lines
TEXT   = HexColor("#1E293B")   # default body text
```

**Colour usage rules:**

| Element | Colour |
|---|---|
| Section banner background | `NAVY` |
| Subhead bar background | `NAVY2` |
| Accent bar (left edge of banners/subheads) | `AMBER` |
| Required field border | `AMBER` |
| Required field fill | `AMBER2` |
| Optional field fill | `LIGHT` |
| Optional field border | `BORDER` |
| Table header row | `NAVY` |
| Alternating row fill | `LIGHT` / `white` |
| Body text | `TEXT` |
| Hint / caption text | `SLATE` |
| Page numbers, footer text | `MUTED` |
| Header document title | `white` |
| Footer rule | `BORDER` |

**Critical:** always pass `HexColor` objects (or `black`/`white`) to AcroForm field parameters. Raw tuples raise `AttributeError` on save.

```python
# Correct
c.acroForm.textfield(..., borderColor=white, fillColor=white, textColor=black)

# Wrong — crashes on canvas.save()
c.acroForm.textfield(..., textColor=(0, 0, 0))
```

---

## 5. Typography Scale

| Role | Font | Size | Colour | Use |
|---|---|---|---|---|
| Banner title | `Jost-Bold` | 11pt | `white` | Section banner text |
| Banner subtitle | `Jost-Italic` | 8.5pt | `MUTED` | Section banner subtitle |
| Subhead | `Jost-Bold` | 9pt | `white` | NAVY2 subhead bar text |
| Label | `Jost-Bold` | 8.5pt | `NAVY` (optional) / `AMBER` (required) | Field labels |
| Hint / caption | `Jost-Italic` | 7.5pt | `SLATE` | Help text below labels |
| Body | `Jost` | 10pt / leading 16pt | `TEXT` | Narrative text |
| Table header | `Jost-Bold` | 8.5–9pt | `white` | Navy table header rows |
| Table body | `Jost` | 8.5–9pt | `TEXT` | Table cell content |
| Page number | `Jost` | 8pt | `MUTED` | Header right / footer centre |
| Footer text | `Jost-Italic` | 7pt | `MUTED` | Footer left and right |
| Cover title | `Jost-Bold` | 26–30pt | `white` | Hero zone title |
| Cover subtitle | `Jost` | 10pt | `MUTED` | Hero zone subtitle |
| Cover series label | `Jost` | 9pt | `MUTED` | Hero zone top label |

---

## 6. Header and Footer

Draw on every interior page. Never draw on the cover page.

```python
def draw_header(c, page_num, title, centre_label=""):
    # Navy bar
    c.setFillColor(NAVY)
    c.rect(0, H - HDR_H, W, HDR_H, fill=1, stroke=0)
    # Amber accent stripe below bar
    c.setFillColor(AMBER)
    c.rect(0, H - HDR_H - 0.04*inch, W, 0.04*inch, fill=1, stroke=0)
    # Left: document title in all caps
    c.setFillColor(white);  c.setFont("Jost-Bold", 9)
    c.drawString(MARGIN, H - 0.27*inch, title.upper())
    # Centre: document type label
    if centre_label:
        c.setFont("Jost", 8);  c.setFillColor(MUTED)
        c.drawCentredString(W / 2, H - 0.27*inch, centre_label)
    # Right: page number
    c.setFont("Jost", 8);  c.setFillColor(MUTED)
    c.drawRightString(W - MARGIN, H - 0.27*inch, f"Page {page_num}")


def draw_footer(c, page_num, left_text, right_tag):
    # Full-width rule
    c.setFillColor(BORDER)
    c.rect(0, FTR_H - 0.02*inch, W, 0.02*inch, fill=1, stroke=0)
    # Left: contextual instruction
    c.setFont("Jost-Italic", 7);  c.setFillColor(MUTED)
    c.drawString(MARGIN, 0.22*inch, left_text)
    # Centre: page number em-dash format
    c.setFillColor(SLATE)
    c.drawCentredString(W / 2, 0.22*inch, f"— {page_num} —")
    # Right: series tag
    c.setFillColor(MUTED)
    c.drawRightString(W - MARGIN, 0.22*inch, right_tag)
```

Page number appears in both header (right-aligned) and footer (centred). This ensures readability on both screen and print.

---

## 7. Page Numbering Convention

The cover page is always physical page 1 and displays no page number. Interior pages are numbered sequentially from 2.

The `Layout` controller (Section 9) initialises `page_num = 1`. `start_interior()` increments to 2 for the first interior page. Each `new_page()` call increments by 1.

**Common mistake:** initialising `page_num = 0` causes the first interior page to display "Page 1" even though it is the second physical page, producing a duplicate when the cover is visible in a PDF viewer.

---

## 8. Spacing Rhythm

All vertical spacing values have been validated against rendered output. Do not reduce them.

| Transition | Gap |
|---|---|
| Section banner bottom → first element | `bh + 14pt` |
| Subhead bar bottom → first element | `18pt bar + 12pt = 30pt total` |
| Block header bottom → first label | `22pt bar + 16pt = 38pt total` |
| Label baseline → top of field box | `15pt` |
| Hint baseline → top of field box | `13pt` |
| Field box bottom → next label | `field_height + 14pt` |
| Callout box bottom → next element | `callout_height + 12pt` |
| Between sub-sections (no subhead) | `14–16pt` |

Every label + optional hint + field box is a single **atomic unit**. Check the combined height before drawing any part of it. Never draw a label and discover there is no room for its field.

```python
# Atomic unit check: label (15) + hint (13) + field (22) + gap (14) = 64pt
label_h = 15 + (13 if hint else 0)
self.check(label_h + field_h + 14)
# Draw label, then field — knowing both will fit
```

---

## 9. Layout Controller Class

All canvas-direct build scripts must use the `Layout` controller. Inline `y -= ...` arithmetic scattered through drawing functions is prohibited.

```python
class Layout:
    def __init__(self, c: canvas.Canvas):
        self.c = c
        self.page_num = 1   # cover is page 1; first interior page increments to 2
        self.y = 0.0
        self._field_log: list[dict] = []   # feeds the post-build validator

    def start_interior(self):
        """Begin the first interior page."""
        self.page_num += 1
        self._reset_y()
        draw_header(self.c, self.page_num)
        draw_footer(self.c, self.page_num)

    def new_page(self):
        """Flush current page and open a fresh interior page."""
        self.c.showPage()
        self.page_num += 1
        self._reset_y()
        draw_header(self.c, self.page_num)
        draw_footer(self.c, self.page_num)

    def _reset_y(self):
        self.y = H - HDR_H - 0.04 * inch - 0.20 * inch

    def check(self, min_height: float):
        """Trigger new_page() if the next element would cross BOTTOM."""
        if self.y - min_height < BOTTOM:
            self.new_page()

    def vs(self, pts: float):
        self.y -= pts

    def label(self, x: float, text: str, required: bool = False, hint: str = ""):
        c = self.c
        c.setFont("Jost-Bold", 8.5)
        c.setFillColor(AMBER if required else NAVY)
        c.drawString(x, self.y, text + (" *" if required else ""))
        if hint:
            c.setFont("Jost-Italic", 7.5);  c.setFillColor(SLATE)
            c.drawString(x, self.y - 13, hint)

    def field(self, name: str, x: float, w: float, h: float,
              required: bool = False, multi: bool = False):
        c = self.c
        if required:
            c.setFillColor(AMBER2);  c.setStrokeColor(AMBER);  c.setLineWidth(1.2)
        else:
            c.setFillColor(LIGHT);   c.setStrokeColor(BORDER); c.setLineWidth(0.7)
        c.roundRect(x, self.y - h, w, h, 3, fill=1, stroke=1)
        c.acroForm.textfield(
            name=name, x=x+3, y=(self.y-h)+3,
            width=w-6, height=h-6,
            borderColor=white, fillColor=white,
            textColor=black, forceBorder=False,
            fontSize=9, fontName="Helvetica",
            fieldFlags='multiline' if multi else '',
            relative=False
        )
        self._field_log.append({'name': name, 'page': self.page_num,
                                'y_bottom': self.y - h})

    def dropdown(self, name: str, x: float, w: float, opts: list):
        c = self.c
        c.setFillColor(LIGHT);  c.setStrokeColor(BORDER);  c.setLineWidth(0.7)
        c.roundRect(x, self.y - 22, w, 22, 3, fill=1, stroke=1)
        c.acroForm.choice(
            name=name, x=x+3, y=(self.y-22)+3,
            width=w-6, height=18,
            options=opts, value=opts[0],   # opts[0] must be a non-empty placeholder
            borderColor=white, fillColor=white,
            textColor=black, forceBorder=False,
            fontSize=8.5, fontName="Helvetica",
            relative=False
        )
        self._field_log.append({'name': name, 'page': self.page_num,
                                'y_bottom': self.y - 22})

    def checkbox_row(self, name: str, x: float, label_text: str):
        c = self.c
        c.acroForm.checkbox(
            name=name, x=x, y=self.y - 10, size=12,
            borderColor=BORDER, fillColor=white,
            textColor=black, forceBorder=True, relative=False
        )
        c.setFont("Jost", 9);  c.setFillColor(TEXT)
        c.drawString(x + 18, self.y - 8, label_text)

    def section_banner(self, number: str, title: str, subtitle: str = ""):
        bh = 46 if subtitle else 36
        self.check(bh + 14 + 40)
        c = self.c
        c.setFillColor(NAVY)
        c.roundRect(MARGIN, self.y - bh, CW, bh, 4, fill=1, stroke=0)
        c.setFillColor(AMBER)
        c.roundRect(MARGIN, self.y - bh, 5, bh, 3, fill=1, stroke=0)
        c.setFillColor(white);  c.setFont("Jost-Bold", 11)
        c.drawString(MARGIN + 16, self.y - 22, f"{number} — {title}")
        if subtitle:
            c.setFont("Jost-Italic", 8.5);  c.setFillColor(MUTED)
            c.drawString(MARGIN + 16, self.y - bh + 9, subtitle)
        self.y -= bh + 14

    def subhead(self, text: str):
        self.check(30 + 40)
        c = self.c
        c.setFillColor(NAVY2)
        c.rect(MARGIN, self.y - 18, CW, 18, fill=1, stroke=0)
        c.setFillColor(AMBER)
        c.rect(MARGIN, self.y - 18, 4, 18, fill=1, stroke=0)
        c.setFillColor(white);  c.setFont("Jost-Bold", 9)
        c.drawString(MARGIN + 12, self.y - 13, text)
        self.y -= 30

    def field_row(self, items: list, h: float = 22, required_flags: list = None):
        """
        items: list of (label, field_name) or (label, field_name, hint)
        Divides CW evenly across n columns with 12pt gaps.
        """
        n = len(items)
        col_w = (CW - (n - 1) * 12) / n
        req = required_flags or [False] * n
        hint_present = any(len(it) > 2 for it in items)
        label_h = 15 + (13 if hint_present else 0)
        self.check(label_h + h + 14)
        for i, it in enumerate(items):
            self.label(MARGIN + i * (col_w + 12), it[0],
                       required=req[i], hint=it[2] if len(it) > 2 else "")
        self.y -= label_h
        for i, it in enumerate(items):
            self.field(it[1], MARGIN + i * (col_w + 12), col_w, h, required=req[i])
        self.y -= h + 14

    def dropdown_row(self, items: list, opts_list: list):
        """items: list of (label, name). opts_list: matching list of option lists."""
        n = len(items)
        col_w = (CW - (n - 1) * 12) / n
        self.check(15 + 22 + 14)
        for i, it in enumerate(items):
            self.label(MARGIN + i * (col_w + 12), it[0])
        self.y -= 15
        for i, it in enumerate(items):
            self.dropdown(it[1], MARGIN + i * (col_w + 12), col_w, opts_list[i])
        self.y -= 22 + 14

    def mixed_row(self, left_label, left_name, left_opts,
                  right_label, right_name, right_required=False):
        """Left column = dropdown, right column = text field."""
        col_w = (CW - 12) / 2
        self.check(15 + 22 + 14)
        self.label(MARGIN, left_label)
        self.label(MARGIN + col_w + 12, right_label, required=right_required)
        self.y -= 15
        self.dropdown(left_name, MARGIN, col_w, left_opts)
        self.field(right_name, MARGIN + col_w + 12, col_w, 22, required=right_required)
        self.y -= 22 + 14

    def signoff_row(self):
        """Three equal columns: Prepared By | Reviewed By | Approval Date."""
        third = (CW - 16) / 3
        self.check(15 + 22 + 14)
        for i, lbl in enumerate(["Prepared By", "Reviewed By", "Approval Date"]):
            self.label(MARGIN + i * (third + 8), lbl)
        self.y -= 15
        for i, name in enumerate(["prepared_by", "reviewed_by", "approval_date"]):
            self.field(name, MARGIN + i * (third + 8), third, 22)
        self.y -= 22 + 14
```

---

## 10. Section Banner Page Rule

Every major section banner **must begin on a fresh interior page**. Call `lyt.new_page()` immediately before drawing the section banner. Do not rely on `check()` alone.

```python
# Correct — explicit new page before every section banner (except the first)
lyt.new_page()
lyt.section_banner("Section 2", "Notes & Sign-off",
                   subtitle="Project brief, constraints, and approval")

# Wrong — check() only fires when space is tight; banner may land mid-page
lyt.check(block_total)
lyt.section_banner(...)
```

**Exception:** the very first section on the first interior page does not call `new_page()` — `start_interior()` already establishes a fresh page. Only sections 2, 3, 4… require the explicit `new_page()` call before their banner.

---

## 11. UI Components Reference

### Section Banner

```
╔═══════════════════════════════════════════════════════════════════╗
║  Section N — Title                                               ║  ← NAVY, 46pt (with subtitle)
║  Subtitle text in muted italic                                   ║     or 36pt (no subtitle)
╚═══════════════════════════════════════════════════════════════════╝
  AMBER left bar, 5pt wide, full height, rounded corners
```

After drawing: `self.y -= bh + 14`

### Subhead Bar

```
╔═══════════════════════════════════════════════════════════════════╗
║  Text                                                            ║  ← NAVY2, 18pt tall
╚═══════════════════════════════════════════════════════════════════╝
  AMBER left bar, 4pt wide
```

After drawing: `self.y -= 30` (18pt bar + 12pt gap)

### Block Header (repeating entries)

```
╔═══════════════════════════════════════════════════════════════════╗
║ | Entry #N    [optional right-aligned hint]                      ║  ← LIGHT2, 22pt tall
╚═══════════════════════════════════════════════════════════════════╝
  AMBER left bar, 3pt wide
```

After drawing: `self.y -= 38` (22pt bar + 16pt gap)

```python
def block_hdr(self, text, hint_right=""):
    self.check(38 + 40)
    c = self.c
    c.setFillColor(LIGHT2)
    c.rect(MARGIN, self.y - 22, CW, 22, fill=1, stroke=0)
    c.setFillColor(AMBER)
    c.rect(MARGIN, self.y - 22, 3, 22, fill=1, stroke=0)
    c.setFont('Jost-Bold', 9);  c.setFillColor(NAVY)
    c.drawString(MARGIN + 10, self.y - 15, text)
    if hint_right:
        c.setFont('Jost-Italic', 7.5);  c.setFillColor(MUTED)
        c.drawRightString(MARGIN + CW - 4, self.y - 15, hint_right)
    self.y -= 38
```

### Field Box — Standard heights

| Type | Height |
|---|---|
| Single-line text | 22pt |
| Two-line area | 36–44pt |
| Multi-paragraph / notes | 52–72pt |
| Grid row (compact) | 20pt |

AcroForm widget placed 3pt inside the visual box on all sides.

### Dropdown

Always use a non-empty placeholder as both the first option and the `value` default. Empty `value=''` crashes ReportLab 4.x with `UnboundLocalError`.

```python
opts = ['Select...', 'Option A', 'Option B']
c.acroForm.choice(..., options=opts, value=opts[0])
```

### Multiline Text Field

Use `fieldFlags='multiline'` — the `multiline=True` keyword argument does not exist in ReportLab 4.x and raises `TypeError`.

```python
c.acroForm.textfield(..., fieldFlags='multiline')   # correct
c.acroForm.textfield(..., multiline=True)            # raises TypeError
```

### Callout Box

| Type | Fill | Stroke | Label colour |
|---|---|---|---|
| Tip | `GREEN2` | `GREEN` | `GREEN` |
| Note / Info | `BLUE2` | `NAVY2` | `NAVY` |
| Warning | `AMBER2` | `AMBER` | `AMBER3` |
| Error / Important | `RED2` | `RED` | `RED` |

Structure: `roundRect` with matching stroke + 4–5pt left accent bar in stroke colour + bold label + body text. After drawing: `self.y -= callout_height + 12`.

### Table (Platypus)

```python
from reportlab.platypus import Table, TableStyle

style = TableStyle([
    ('BACKGROUND',    (0, 0), (-1, 0),  NAVY),
    ('ROWBACKGROUNDS',(0, 1), (-1, -1), [LIGHT, white]),
    ('TOPPADDING',    (0, 0), (-1, -1), 7),
    ('BOTTOMPADDING', (0, 0), (-1, -1), 7),
    ('LEFTPADDING',   (0, 0), (-1, -1), 8),
    ('RIGHTPADDING',  (0, 0), (-1, -1), 8),
    ('GRID',          (0, 0), (-1, -1), 0.4, BORDER),
    ('VALIGN',        (0, 0), (-1, -1), 'TOP'),
])
table = Table(data, colWidths=[...], style=style, repeatRows=1)
```

---

## 12. Cover Page Pattern

```python
def draw_cover(c, hero_split=0.48):
    """
    hero_split: fraction of page height used by hero zone (0.44–0.58).
    Use ~0.44 for forms with many identification fields; ~0.56 for guides.
    """
    HERO_BOTTOM = H * hero_split

    # Hero zone — full bleed navy
    c.setFillColor(NAVY)
    c.rect(0, HERO_BOTTOM, W, H - HERO_BOTTOM, fill=1, stroke=0)
    # Amber accent stripe at hero bottom
    c.setFillColor(AMBER)
    c.rect(0, HERO_BOTTOM - 3, W, 3, fill=1, stroke=0)

    # Series label, divider rule, title, subtitle
    # (draw at absolute y coordinates relative to HERO_BOTTOM)

    # Content zone — identification fields drawn below HERO_BOTTOM
    # Heading label + amber rule
    c.setFont("Jost-Bold", 10);  c.setFillColor(NAVY)
    fy = HERO_BOTTOM - 0.35*inch
    c.drawString(MARGIN, fy, "PROJECT IDENTIFICATION")
    c.setFillColor(AMBER)
    c.rect(MARGIN, fy - 4, CW, 1.5, fill=1, stroke=0)

    # Fields drawn at fy - 22, fy - 74, fy - 126... (52pt per row)

    # Closing amber rule at bottom margin
    c.setFillColor(AMBER)
    c.rect(MARGIN, MARGIN, CW, 2, fill=1, stroke=0)
    # Version string bottom-right
    c.setFont("Jost-Italic", 7);  c.setFillColor(MUTED)
    c.drawRightString(W - MARGIN, MARGIN + 7, "v1.0 · 2025")
```

**Cover identification row layout — standard 3-column first row:**

```python
name_w = CW * 0.50   # Project Name — wide
num_w  = CW * 0.28   # Project Number
rev_w  = CW - name_w - num_w - 24   # Rev — narrow (two 12pt gaps)
```

Always include the Rev field alongside Project Number. It tracks revision status independently.

---

## 13. Platypus Cover Page Isolation

When a Platypus document has a canvas-drawn cover page, use separate `PageTemplate` objects to prevent Platypus from overlapping the cover artwork.

```python
from reportlab.platypus import (
    BaseDocTemplate, PageTemplate, Frame,
    NextPageTemplate, PageBreak, Spacer
)

# Cover frame: 1pt tall — Platypus cannot fit content here
cover_frame = Frame(0, 0, W, 1,
                    leftPadding=0, rightPadding=0,
                    topPadding=0, bottomPadding=0)

interior_frame = Frame(
    MARGIN, BOTTOM,
    CW, H - HDR_H - 0.22*inch - BOTTOM,
    leftPadding=0, rightPadding=0,
    topPadding=0, bottomPadding=0)

def on_cover(canvas, doc):
    canvas.saveState()
    draw_cover(canvas)   # no header or footer
    canvas.restoreState()

def on_interior(canvas, doc):
    draw_header(canvas, doc.page)
    draw_footer(canvas, doc.page)

cover_pt    = PageTemplate(id='Cover',    frames=[cover_frame],    onPage=on_cover)
interior_pt = PageTemplate(id='Interior', frames=[interior_frame], onPage=on_interior)

doc = BaseDocTemplate(out, pagesize=letter)
doc.addPageTemplates([cover_pt, interior_pt])

story = [Spacer(1, 1)]                  # occupies the 1pt cover frame
story.append(NextPageTemplate('Interior'))
story.append(PageBreak())
# ... all real content follows
doc.build(story)   # no keyword arguments — page templates handle everything
```

Never use `doc.build(story, onFirstPage=..., onLaterPages=...)` — those arguments belong to `SimpleDocTemplate` and raise `TypeError` with `BaseDocTemplate`.

---

## 14. Post-Build Field-Bounds Validator

Run immediately after `canvas.save()`. Exit non-zero on failure — do not distribute a PDF that fails validation.

```python
def validate_field_bounds(field_log: list, total_pages: int) -> bool:
    """
    Checks every logged field's bottom edge against BOTTOM.
    Returns True if all pass.
    """
    print("\n── Post-build field-bounds validation ───────────────────────")
    failures = [e for e in field_log if e['y_bottom'] < BOTTOM]

    if not failures:
        print(f"  PASS — all {len(field_log)} fields within safe zone "
              f"(BOTTOM = {BOTTOM:.1f}pt)")
        print(f"  Pages generated: {total_pages}")
    else:
        print(f"  FAIL — {len(failures)} field(s) below BOTTOM ({BOTTOM:.1f}pt):\n")
        for f in failures:
            print(f"    • '{f['name']}'  page={f['page']}  "
                  f"y_bottom={f['y_bottom']:.1f}pt  "
                  f"overflow={(BOTTOM - f['y_bottom']):.1f}pt")
        print("\n  Add check() guards before the affected elements.")

    print("─────────────────────────────────────────────────────────────\n")
    return len(failures) == 0


# Required call pattern at end of every build script
c.save()

passed = validate_field_bounds(lyt._field_log, lyt.page_num)
if not passed:
    raise SystemExit(
        "PDF saved but FAILED bounds validation — fix layout before distributing."
    )

print(f"PDF ready → {OUT}")
```

Every `field()` and `dropdown()` call in the `Layout` class logs to `_field_log`. Grid table fields drawn with raw `acroForm.textfield()` calls must also append to `lyt._field_log` manually:

```python
lyt._field_log.append({
    'name':     field_name,
    'page':     lyt.page_num,
    'y_bottom': lyt.y - row_height,
})
```

---

## 15. Form Field Design Conventions

### Free-text for exact numeric values

Use dropdown range buckets only for estimates (budget, approximate area). Use free-text fields for any value used in downstream calculations — headcount, desk count, exact area, quantities.

```python
# Wrong for calculation inputs — range loses precision
opts = ['Select...', '1–5', '6–15', '16–30']
lyt.dropdown("total_occupancy", ...)

# Correct
lyt.field("total_occupancy", ..., required=True)
```

### Labels are noun phrases

The label names the field. Instructions and explanations go in the hint line below the label.

```python
# Wrong
lyt.label(MARGIN, "Project Brief / Special Instructions")

# Correct
lyt.label(MARGIN, "Project Brief",
          hint="Key constraints, client preferences, and scope clarifications.")
```

---

## 16. Build Checklist

Before delivering any PDF, confirm every item:

**Setup**
- [ ] Jost TTF files converted from woff2 and registered with `registerFontFamily()`
- [ ] Page size `letter` (612 × 792) — no other size
- [ ] `MARGIN`, `CW`, `HDR_H`, `FTR_H`, `BOTTOM` defined as constants
- [ ] All colours imported from palette — no ad-hoc hex values

**Page structure**
- [ ] Cover page is physical page 1, unnumbered, no header or footer
- [ ] `Layout` initialised with `page_num = 1`
- [ ] First interior page starts at `page_num = 2` via `start_interior()`
- [ ] Every section banner (except the first) preceded by explicit `lyt.new_page()`
- [ ] Header and footer drawn on every interior page, never on cover

**Layout guards**
- [ ] Every compound element (label + field) checked as an atomic unit with `self.check(total_height)`
- [ ] No raw `y -= ...` arithmetic outside the `Layout` class
- [ ] `_field_log` populated by every `field()`, `dropdown()`, and manual grid field

**AcroForm**
- [ ] All AcroForm fields use `fontName="Helvetica"` — never Jost
- [ ] All `textColor`, `borderColor`, `fillColor` use `Color` objects — never tuples
- [ ] All `acroForm.choice()` calls use a non-empty string as `value` that exists in `options`
- [ ] All multiline fields use `fieldFlags='multiline'` — not `multiline=True`

**Validation**
- [ ] `validate_field_bounds()` called after `canvas.save()`
- [ ] Script exits non-zero if validation fails
- [ ] Validator output printed to console showing pass/fail and page count

**Final checks**
- [ ] Page numbers in header and footer match on every interior page
- [ ] Rev field present on cover alongside Project Number
- [ ] Dropdown options list begins with a non-empty `'Select...'` placeholder
- [ ] Required fields have amber border and fill; optional fields have grey border and light fill

---

*This reference is paired with `pdf-planning-guide.md`, which covers design decisions and brief-writing for use in Claude Chat.*
