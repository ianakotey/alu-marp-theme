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

## Attribution

Theme CSS written for ALU. Documents under `reference/` are MIT-licensed
Marp/Marpit material; see their upstream repositories.
