---
name: alu-marp-theme
description: Author or edit ALU-branded Marp decks with the alu theme. Use when creating session slides, converting an existing ALU deck to Markdown, or changing the theme, its page classes, or its exports.
---

# ALU Marp theme

This repository holds one Marp theme, `theme.css`, plus a variant for editable
PowerPoint. Decks are Markdown files that select the theme with `theme: alu` and
mark each page with a class.

## Setup

```bash
marp deck.md --theme-set . -w -p     # preview from the repo root
marp deck.md --theme-set . -o deck.html
```

The theme name is `alu`. The `--theme-set .` flag registers the CSS file and its
images.

## Page skeleton

```markdown
---
theme: alu
size: 16:9
---

<!-- _class: title -->
# Session title
```

Use `_class` for one page and `class` for that page and the pages after it.

## Classes

| Class | Page type |
| --- | --- |
| `title` | Deck opener |
| `banner` | Full-bleed statement or closing page |
| `objectives` | Session objectives with a numbered connector |
| `housekeeping` | Expectations |
| `content` | Standard heading and body page |
| `two-col` | Two equal columns |
| `split` | Left column plus a navy instruction panel |
| `code` | Heading and a wide code block |
| `code-notes` | Code left, notes right |
| `statement` | One centred line |
| `activity` | Exercise in a dashed panel |
| `quote` | Quotation with attribution |
| `references` | Source list |
| `display` | Modifier that enlarges a heading |

Full markup for each class is in `docs/classes.md`.

## Authoring rules

Titles are two-tone. Plain `h1` text renders blue. A bold run renders navy.

```markdown
# **Activity:** Thank-Share
# **Using apply()**
```

The `split` panel is a blockquote. Put anything for the left column before it,
then one blockquote for the right panel. Only one blockquote per split page.

```markdown
<!-- _class: split -->
# **Activity:** Thank-Share

```c
int add(int a, int b) { return a + b; }
```

> Work in pairs.
>
> - First task
> - Second task
```

Code blocks size themselves to the code and centre in the column. Break long lines
by hand; the theme does not wrap or shrink code.

On the `title` page the last paragraph becomes the footer at the bottom left. Keep
the URL last.

## Exports

```bash
marp deck.md --theme-set . --pdf -o deck.pdf
marp deck.md --theme-set . --pptx -o deck.pptx      # one image per slide
```

For an editable PowerPoint file, use the flat variant:

```bash
marp deck.md --theme-set . --theme ./alu-editable.css --pptx-editable -o deck.pptx
```

That path needs LibreOffice on `PATH`. It keeps text editable but bakes the opener
artwork into images, so the result is not pixel-identical to the HTML.

Add `--allow-local-files` when the deck references images on disk and you export
to PDF, PPTX, or PNG.

## Checking a deck

Render it and read the pages before calling it done. Look for:

- a heading that runs under the right panel, which means the title is too long for
  the column;
- code that reaches the band at the bottom;
- a split page where the left group is clipped at the top or bottom;
- `theme: alu` spelled correctly in the front matter.

## Changing the theme

Read `docs/quirks.md` first. The points that cause the most damage:

- Colours live in `--alu-*` properties at the top of `theme.css`. Change them there.
- Class rules use `section:where(.class)`, so they weigh the same as a bare
  `section` rule. Place a new rule after the variant it should override.
- Keep gradients out of the shared chrome and the split page. They break the
  editable export.
- Keep the highlighted-line rule as four longhand properties. The shorthand is
  rejected by VS Code's CSS parser.
- Do not add `@size 4:3 false` to the editable variant. Split titles disappear after
  import when it is present.
- The lockup, band, hex tile, and housekeeping icon are data URIs. Replace the URI
  when the artwork changes.
