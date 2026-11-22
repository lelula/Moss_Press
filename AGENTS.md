# AGENTS.md: working with a Moss Press folder

You are helping a writer prepare books for print with **Moss Press**, a small app that lays out a novel and saves it as a PDF. In folder mode it keeps every book as plain files, so you can read and change them too. This file tells you where everything lives, what the settings mean, and how to make changes the writer can trust.

**These are defaults, not rules.** Your writer's instructions always come first. If they want something done differently, do it their way, and offer to update this file to match.

If your platform has a better way to store or connect to these files (a connector, a synced drive, a project space), suggest it to your user.

## First, ask one question

At the start of a session, ask your user:

> "Should I save changes into the files as we go, or show them to you first and save when you say so?"

Remember the answer. For anything that changes the words of a book (grammar, spelling, wording), **always show the changes first**, whatever the answer was. See "Fixing text across books" below.

## Where things live

The folder the writer picked holds their whole library. It is the **same layout the Moss Writing Desk uses**, so one folder can serve both apps.

```
Library folder/
  My Novel/
    book.json               title and author (shared with the Writing Desk)
    press.json              Moss Press settings for this book
    chapters/
      01 The Storm.md
      02 Morning.md
    trash/                  removed chapters, plus before-last-import/ (the chapters
                            replaced by the most recent import). Leave it alone.
    summaries.md, bible.md, where-i-left-off.md, days.json
                            Writing Desk files: Moss Press ignores them
  Another Book/
    ...
  _press/
    end-matter/             reusable end matter pages, shared by every book
      About the Author.md
      Also by the author.md
    images/                 author photos, covers, ornaments (PNG or JPG)
    library.json            the order of the end matter list
  _backups/                 the Writing Desk's daily backups (leave it alone)
```

Folders starting with `_` or `.` are not books.

## Chapters: `chapters/NN Title.md`

```
# The Storm

The storm came in off the water the way it always did in autumn.

She was out in it *anyway*.

***

The keeper opened the door before she knocked.
```

- First line: `# ` plus the chapter title. Then a blank line, then the text.
- The number at the start of the file name sets the order (`01`, `02`, … three digits past 99 chapters). If you insert or reorder chapters, renumber the files, and if the book has a `summaries.md`, rename its matching `## ` headings too so the Writing Desk keeps each summary with its chapter.
- One paragraph per line (blank lines between paragraphs are fine too).
- `*italic*` and `**bold**` work.
- A line of only `***`, `* * *` or `#` is a scene break.
- `## Heading` inside a chapter makes a small centered subheading.
- `[[image:Name]]` places an image from `_press/images/` (by file name without the extension). `[[image:Name|2in]]` sets its width.
- Never delete a chapter file. Move it into the book's `trash/chapters/` folder.

## Book settings: `press.json`

```json
{
  "app": "Moss Press", "format": 1,
  "subtitle": "", "copyright": "Copyright © 2026 Your Name\n\nAll rights reserved...", "dedication": "",
  "toc": true,
  "endPages": ["About the Author", "Also by the author"],
  "settings": { "trim": "5.5x8.5", "font": "EB Garamond", "size": 11.5, ... }
}
```

- `copyright` and `dedication` are plain text. A blank line starts a new paragraph. An empty dedication skips the page.
- `toc`: include a table of contents.
- `endPages`: which end matter pages this book includes, in order, by their names in `_press/end-matter/`.
- The title and author live in `book.json`, not here.

### The `settings`, and what they mean

| Setting | Meaning | Values |
|---|---|---|
| `trim` | Page size | `"5x8"`, `"5.25x8"`, `"5.5x8.5"`, `"6x9"`, or `"custom"` with `w` and `h` in inches |
| `mt`, `mb`, `mi`, `mo` | Margins in inches: top, bottom, inside (binding edge), outside | numbers |
| `headers` | Running headers at the top of pages | `true` / `false` |
| `hleft`, `hright` | Header text on left / right pages (blank means author / title) | text |
| `numpos` | Page numbers | `"center"` or `"outside"` |
| `font`, `hfont` | Body font, heading font | EB Garamond, Crimson Pro, Libre Baskerville, Lora, Alegreya, Spectral, Cormorant Garamond, Cinzel, IM Fell English, Playfair Display |
| `size`, `lead`, `indent` | Body size (pt), line spacing, paragraph indent (in) | numbers, e.g. 11.5, 1.4, 0.3 |
| `justify`, `hyphen` | Justified text, hyphenation | `true` / `false` |
| `hsize`, `sink` | Chapter title size (pt), space above it (in) | numbers |
| `label` | Chapter label | `"none"`, `"words"` (Chapter One), `"digits"` (Chapter 1), `"number"` (1) |
| `first` | First paragraph of a chapter | `"both"` (drop cap + small caps line), `"dropcap"`, `"smallcaps"`, `"plain"` |
| `orn` | Ornament under the chapter title | `""`, `"❦"`, `"✦"`, `"~"`, or any short symbol |
| `ornimg`, `ornh` | Use an image from `_press/images/` as the ornament instead (by name), and its height in inches | name, number like 0.3 |
| `right` | Start every chapter on a right-hand page | `true` / `false` |
| `scene`, `sceneimg` | Scene break symbol, or an image name to use instead | text |

**Print rules worth knowing (Amazon KDP paperback):** the inside margin must grow with the page count: at least 0.375 in up to 150 pages, 0.5 in up to 300, 0.625 in up to 500, 0.75 in up to 700, and 0.875 in beyond that. The outside, top and bottom margins need at least 0.25 in. Moss Press checks the inside margin and warns on the Page tab. Common novel trims are 5 × 8, 5.25 × 8, 5.5 × 8.5 and 6 × 9 inches; check what the writer's earlier books used before changing a series.

## End matter: `_press/end-matter/<Name>.md`

One file per page, shared by every book. Change it once and every book that includes it updates. A book includes a page by listing its name in `endPages` in its `press.json`.

Blocks are separated by blank lines:

```
# Also by the Author

[[image:Cover One|1.1in]]
**The Lighthouse Keeper**
A storm, a lighthouse, and a stranger the keeper has seen before.

[[image:Cover One|1.1in|The Lighthouse Keeper]] [[image:Cover Two|1.1in|The Winter Road]]

## The Lighthouse Series
- The Lighthouse Keeper
- The Winter Road

> Find all my books at yourwebsite.com
```

- `# Heading`: the page title (the first one only). `## Heading`: a small centered subheading, good for series names.
- `[[image:Name|width]]`: an image from `_press/images/`, by file name without the extension. Width in inches, like `1.1in`.
- **Cover beside a blurb:** an image alone on a line, with the title and a line or two directly under it (no blank line between). It lays out as cover on the left, text on the right.
- **Covers in a row:** several image tags on one line. A third part is a caption under the cover: `[[image:Cover One|1.1in|Book Title]]`. Three covers at 1.1 in fit a 5.5 in wide book.
- `- item`: a list. A line starting with `>`: small italic centered print, for a website or newsletter line.
- Text alignment for the whole page (left or centered) is set in the app and stored in `_press/library.json` under `centered` (a list of page names).
- If an image isn't in the library yet, the preview shows a dashed placeholder naming it, so the writer knows what to add.

## Working alongside the open app

- Moss Press notices changed files when its window comes back into focus, or when the writer presses **Reload from folder** on the Library tab.
- Don't edit the same book's files while the writer is changing that book in the app. The last one to save wins.
- The PDF itself is made by the writer: **Export PDF**, then **Save as PDF** in the print dialog. You can't make it for them, but you can get every book ready.

## Fixing text across books

The writer may ask you to clean up grammar and spelling across one book or many. Do it like this:

1. Work **one chapter at a time**. Don't load a whole library at once.
2. **Show every proposed change before saving it**, marked so it can be skimmed: the old words struck through and the new words highlighted (in red if your platform can show colour, otherwise `~~old~~ **new**`). Number them.
3. Let the writer approve or reject each one ("all except 4 and 9" is a fine answer). Save only what was approved.
4. Fix errors; don't rewrite. Their voice, word choices, dialect and deliberate fragments stay exactly as they are. When unsure whether something is a mistake or a choice, ask.
5. Keep a short list of what you changed in which book, and give it to the writer at the end.

## Common jobs

- **Same look for a whole series:** copy the `settings` block from one book's `press.json` into the others. Confirm with the writer first, and leave `trim` alone unless they ask.
- **Update the "Also by" page:** edit the one file in `_press/end-matter/`. Every book that includes it gets the change.
- **Add a new book:** make a folder with `book.json` (`{"title": "...", "author": "..."}`) and a `chapters/` folder with the chapter files. Moss Press creates `press.json` with default settings the first time it saves the book.
- **Bring in a finished manuscript:** split it into one chapter file per chapter, numbered in order, each starting with `# Title`.

## Keep to the folder

Only work inside the library folder you were given, and only in the books you were asked about. Leave `trash/`, `_backups/` and the Writing Desk's files (`summaries.md`, `bible.md`, `where-i-left-off.md`, `days.json`) alone unless the writer asks.
