# ALU Marp theme

A Marp theme built from the ALU session slide template (navy/red brand palette,
hexagon band chrome, split layouts and a vocabulary of page classes).

```css
/* @theme alu */
```

## Files

| Path | What it is |
| --- | --- |
| `theme.css` | The theme: palette, typography, chrome and page classes. |
| `template.md` | Page-class menu — one example per class. Copy what you need. |
| `media.png` | Placeholder image used by the template's two-column example. |
| `reference/` | Vendored official Marp/Marpit documents (MIT licensed). |

## Palette

| Token | Value | Use |
| --- | --- | --- |
| `--alu-navy` | `#002e6d` | Brand navy: panels, band, strong titles |
| `--alu-blue` | `#1b5aa6` | Second title tone |
| `--alu-red` | `#cf0c2c` | Accent slash, labels, chips |
| `--alu-teal` | `#0b9bab` | Links |
| `--alu-ink` | `#123a6e` | Body text |

Type: Montserrat for headings, Open Sans for body, JetBrains Mono for code, with
system fallbacks. Slide size is 1280×720 with a 960×720 `4:3` preset.

## Usage

```bash
marp deck.md --theme-set . -w -p      # live preview with this theme
marp deck.md --theme theme.css -o out.html
```

```markdown
---
theme: alu
---

<!-- _class: split -->
# **Activity:** Thank-Share

> Instructions go in the right-hand navy panel.
```

## Page classes

`title`, `banner`, `objectives`, `housekeeping`, `content`, `two-col`, `split`,
`code`, `code-notes`, `statement`, `activity`, `quote`, `references`, plus the
`display` modifier for oversized titles.

Title convention: `# **Label:** rest of the title` renders the label in navy at
weight 800 and the remainder in brand blue.

## Editable PowerPoint

`--pptx-editable` prints the deck to PDF and re-imports it with LibreOffice,
which cannot reproduce CSS gradients, tiled patterns or ligatures, and widens
multi-line headings until they overlap. Use the flat variant for that path:

```bash
marp deck.md --theme-set . --theme ./alu-editable.css --pptx-editable -o deck.pptx
```

It keeps solid surfaces, the band, the lockup, the red slash, tables and code
panels, and switches to system fonts with slightly smaller split titles. The
openers keep their artwork as baked 16:9 backdrops (1920×1080), so the theme
assumes 16:9 for them — the 4:3 preset would stretch the image. Requires
LibreOffice (`soffice`) on `PATH`.

For pixel-exact output use the regular theme and the raster exporter instead:

```bash
marp deck.md --theme-set . --pptx -o deck.pptx      # one image per slide
marp deck.md --theme-set . --pdf -o deck.pdf
```

## Attribution

Theme CSS written for ALU. Documents under `reference/` are MIT-licensed
Marp/Marpit material; see their upstream repositories.
