# Quirks and constraints

Things that behave differently from a plain CSS theme.

## Every class shares one specificity

Classes are written as `section:where(.name)`. The `:where()` wrapper drops the
class from the specificity calculation, so a variant rule weighs the same as a bare
`section` rule. Base rules come first in the file; variants come later and win by
source order.

That has two consequences. A deck-level `<style>` block can override any class
without fighting specificity. A new rule added at the end of the theme can also
override a variant by accident, so place new rules next to the variant they belong
to.

## The band and the lockup

Content pages draw a 34px navy band along the bottom, with the white ALU lockup at
the left. The band is a single SVG image with its navy fill baked in. There is no
separate background colour behind it, so do not add one.

The section reserves 74px at the bottom for the band. Text that reaches that area
overlaps the band and reads badly, so keep content above it.

## Artwork lives inside the CSS

The lockup, the band, the hex texture, and the housekeeping icon are data URIs.
Three custom properties hold the reusable pieces:

| Property | Contents |
| --- | --- |
| `--alu-lockup` | White ALU lockup, transparent background |
| `--alu-band` | 1280×34 band strip with hexagons and navy fill |
| `--alu-hex` | 48×84 hexagon tile for the opener texture |

Replacing artwork means swapping the URI, not adding an image file. The lockup is
transparent, so it sits on any background without a rectangle around it.

## Colours

Every colour is a custom property on `section`, named `--alu-*`. Class rules use
those properties and never hard-code a hex value. To re-theme the deck, edit the
block at the top of the file and leave the rest alone.

## No page numbers

The reference decks have no pagination and the theme does not style `section::after`.
Turning on `paginate: true` brings back the default number in the bottom right,
which collides with the band.

## Code blocks

The dark panel is sized to the code and centred in its column:

```css
pre {
  width: fit-content;
  max-width: 100%;
  margin: 0.7em auto;
}
```

The text inside stays left aligned. The panel stops at the column edge, but a line
wider than the column keeps its width and spills past the panel, so break long
commands by hand.

Auto scaling is off. A code block that runs past the slide is clipped by the
section's `overflow: hidden`.

The highlighted-line rule uses four longhand properties. The shorthand form
`border-image: ... fill 0/ /0 10000vw` renders in browsers but VS Code's CSS
parser rejects it, so keep the longhands.

## Split pages are flex plus an absolute panel

`.split` is a flex column with `justify-content: safe center`, so the title and any
left-column content sit as one centred group. The blockquote is taken out of that
flow and pinned to the right edge.

If the left group grows taller than the slide, it overflows and is clipped. Keep
split headings to three lines and code under roughly twenty lines.

## Sizes

The theme declares two presets: 16:9 at 1280×720 and 4:3 at 960×720. The baked
opener images in `alu-editable.css` are 16:9 and will stretch at 4:3.

Marp treats `size` as a global directive. One `size:` line in the front matter
resizes the whole deck.

## Editable PowerPoint

`--pptx-editable` prints the deck to PDF, then LibreOffice imports that PDF. The
importer drops fills under CSS gradients, cannot tile background images, and loses
ligature glyphs. Multi-line headings also get split into one text box per line,
which then wrap again and overlap.

`alu-editable.css` is the variant for this path. It imports `alu`, so both files
have to be in the theme set. It replaces the openers with baked 1920×1080 WebP
images, uses system fonts, turns ligatures off, and shrinks split headings so each
imported line fits its box.

Do not add `@size 4:3 false` to the variant. It interferes with Marp's size
handling and split titles disappear after import.

## Fonts

Headings use Montserrat, body text uses Open Sans, code uses JetBrains Mono. They
load from Bunny Fonts and fall back to system fonts. The editable variant switches
to Arial or Liberation Sans because font substitution widens imported lines.

## Scope

Marpit wraps theme selectors for the slide container. Write `section`, `h1`, and
`pre` as usual. Adding container selectors of your own will not match anything.

## Local images in decks

Markdown image paths are left alone during conversion. Pass `--allow-local-files`
when the deck points at images on disk and you export to PDF, PPTX, or PNG.
