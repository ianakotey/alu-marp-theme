# Slide classes

Every class is applied with a spot directive, so it affects one page:

```markdown
<!-- _class: split -->
```

Drop the underscore to keep the class on the following pages as well.

## The title convention

Slide headings use one colour rule everywhere. Plain `h1` text is brand blue.
Text wrapped in `**...**` is navy at weight 800.

```markdown
# **Activity:** Thank-Share     <!-- navy label, blue remainder -->
# **Using apply()**             <!-- all navy -->
# Using apply()                 <!-- all blue -->
```

Most classes read better with a bold label. Plain titles work too; they just come
out blue.

## Class menu

| Class | Use it for |
| --- | --- |
| `title` | Opening slide of a deck |
| `banner` | Full-bleed statement, section break, closing slide |
| `objectives` | Session objectives with the numbered connector |
| `housekeeping` | Expectations and ground rules |
| `content` | Ordinary page with a heading and body |
| `two-col` | Two equal columns |
| `split` | White left column, navy instruction panel on the right |
| `code` | Heading plus a wide code block |
| `code-notes` | Code on the left, notes on the right |
| `statement` | One centred claim |
| `activity` | Exercise instructions in a dashed panel |
| `quote` | Centred quotation with attribution |
| `references` | Numbered source list |
| `display` | Modifier that enlarges a heading |

## title

```markdown
<!-- _class: title -->
Programming in C

# Fundamentals of Function Pointers

**Week 9**

*Session 1*

www.alueducation.com
```

Navy opener with the logo at the top left. `**Week 9**` becomes the red chip and
`*Session 1*` becomes muted blue text.

The last paragraph is positioned as the footer line at the bottom left. Keep the
URL there and put nothing after it.

## banner

```markdown
<!-- _class: banner -->
# Questions?
```

Full-bleed navy page with a large italic heading and the logo at the top right.
Use it between sections, for Q&A, and to close a deck.

## objectives

```markdown
<!-- _class: objectives -->
### Session
## Objectives

1. First outcome
2. Second outcome
3. Third outcome
```

Two columns. The `h3` is the small grey label, the `h2` is the large navy word,
and the ordered list gets numbered circles on a red connector line. The counters
are drawn in CSS, so keep the list items plain.

## housekeeping

```markdown
<!-- _class: housekeeping -->
# HouseKeeping
## Expectations

- Cameras on for online attendees.
- Be ready to share your screen.
- Attendance is monitored.
```

The `h2` turns red and the list moves to the right of a line-art icon. The icon is
drawn at a fixed position by `section::before`, so this class is built for one
list.

## content

The default page. Heading, paragraphs, bullets, tables, images.

```markdown
<!-- _class: content -->
# **Why use function pointers?**

Function pointers store the address of a function.

| Benefit | Explanation |
| --- | --- |
| Dynamic behaviour | Choose the function at runtime |
```

Tables get a navy header row and alternating row fills without extra markup.

## two-col

```markdown
<!-- _class: two-col -->
# Two columns

Text for the left column.

![](media.png)
```

Two equal columns with a 56px gap. The heading spans both. Blocks fill left to
right, so group each column into one block, usually a list or an image, when the
split matters.

## split

```markdown
<!-- _class: split -->
# **Activity:** Thank-Share

> Why might we store the address of a function?
>
> Discuss briefly, then share with the class.
```

White left column, navy panel on the right. The panel is a blockquote: it is
absolutely positioned, 48% wide, and its content is centred vertically.

Put left-column material (a code block, an image) before the blockquote. Use only
one blockquote on the page, since it becomes the panel.

## code

```markdown
<!-- _class: code -->
# **Command**

```bash
sudo nginx -t && sudo systemctl reload nginx
```
```

Heading plus a code block. The dark panel hugs the code and sits centred in the
page; the text inside stays left aligned.

## code-notes

```markdown
<!-- _class: code-notes -->
# **Using apply()**

Intro text that spans both columns.

```c
int apply(int (*operation)(int, int), int x, int y)
{
    return operation(x, y);
}
```

- `int (*operation)(int, int)` points at a function
- `apply()` runs whatever function it receives
```

The heading and paragraphs span the full width. The code block takes the left
column and the list sits on the right.

## statement

```markdown
<!-- _class: statement -->
# One centred claim
```

Centred text with the title chrome removed. Good for a single strong line or a
metric.

## activity

```markdown
<!-- _class: activity -->
# **Class activity**
## Instructions

> 1. Open a terminal.
> 2. Run the command.
```

The blockquote becomes a pink panel with a dashed red border. The `h2` is red.

## quote

```markdown
<!-- _class: quote -->
> Would you send your bank password over public Wi-Fi?
>
> Discussion prompt
```

Centred italic quotation with a large red opening mark. The attribution goes at
the end of the blockquote as a final paragraph.

## references

```markdown
<!-- _class: references -->
# **References**

1. [MDN, HTTP request methods](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Methods)
2. [Nginx documentation](https://nginx.org/en/docs/)
```

Smaller type, teal links, numbered list.

## display

A modifier, not a layout. Combine it with another class:

```markdown
<!-- _class: split display -->
# **Q&A Session**
```

Raises the heading to 3.15em. Use it for Q&A pages and section openers.
