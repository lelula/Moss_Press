# Moss Press

Lay out your novel for print and save it as a PDF, ready for Amazon KDP or any print-on-demand service. Free, in your browser, nothing to install.

**Try it now:** [lelula.github.io/Moss-Press](https://lelula.github.io/Moss-Press/)

![A chapter opening in Moss Press](screenshot.png)

Pick a trim size and margins, choose your fonts, and set how every chapter opens: label, title, ornament, drop cap and small caps. Moss Press repeats that look through the whole book, mirrors left and right pages, numbers pages from Chapter 1, builds the table of contents, and adds your end matter. The preview shows real two-page spreads as you go.

Made for writers who want a Vellum-style formatter on Windows (or anywhere) without paying for Word.

## Where your books live

The first time you open it, Moss Press asks where your books should live.

- **A folder on this computer** (Chrome or Edge on a computer). Every book is a folder of plain text files you own, and the whole library sits in one folder. Your AI agent can read and update the files, so it can fix a typo across ten books or change your "Also by" page once for all of them. Give it [AGENTS.md](AGENTS.md).
- **Just this browser.** For trying it out. Your books stay inside that one browser. Use **Download everything** or **Save project file** now and then to keep a copy.

You can move from the browser to a folder later; your books come along.

**Works with the [Moss Writing Desk](https://github.com/lelula/Moss-Writing-desk).** Point Moss Press at your Writing Desk folder and your books are already there, chapters and all. Write in the Desk, format in the Press, and never export between them.

**Privacy:** your text never leaves your computer. The page does fetch its fonts from Google Fonts and its page-layout engine ([Paged.js](https://pagedjs.org)) from unpkg, so stay online while you preview and export.

## Making the PDF

1. Press **Export PDF**. Your browser's print dialog opens.
2. Choose **Save as PDF** as the printer.
3. Set **Margins** to **None** and turn **Headers and footers** off.
4. Save. The page size comes from your trim size automatically, and the fonts are embedded, which is what KDP wants.

Moss Press can't run inside a Claude artifact, because artifacts aren't allowed to open the print dialog. Open it as a normal web page.

## What it does

- **Page:** trim sizes 5 × 8, 5.25 × 8, 5.5 × 8.5, 6 × 9 or custom; mirrored margins; running headers; page numbers centered or on the outer corner. It warns you if your inside margin is too small for KDP at your page count.
- **Type:** ten book fonts, size, line spacing, indents, justification and hyphenation.
- **Chapter openings:** "Chapter One", "Chapter 1" or just the title; drop cap and small caps; an ornament; start every chapter on a right-hand page.
- **Scene breaks:** a line of `***` becomes your symbol, or your own drawn ornament image.
- **Front matter:** title page, copyright page, dedication and table of contents, all unnumbered.
- **End matter library:** About the Author, Also by, newsletter pages and so on, written once and reused in any book. Images sit side by side, good for a row of covers.
- **Images:** author photos, covers and ornaments.
- **Import:** one file for the whole book or one per chapter, plain text or Markdown. Chapters split at `# Heading` lines or lines like "Chapter 3" and "Prologue". Coming from Scrivener? Compile to Plain Text or MultiMarkdown with chapter titles on (MultiMarkdown keeps your italics).
- **Library:** all your books in one place, with a book switcher.
- **Backups:** Download everything gives you every book, your end matter and your images as a zip of plain files. A project file carries one book anywhere.

## Which browser?

- **Chrome and Edge** on a computer: everything, including folder saving.
- **Other browsers** (Brave, Firefox, Safari): browser saving, project files and PDF export work; folder saving doesn't, because those browsers don't let web pages open folders.

## Shared as-is

This is a tool I made for my own books and decided to share. It is free and shared as-is. If it breaks, have your AI fix it. It is one HTML file, and AI is good at that.

Made by [LelulaGames](https://lelula.itch.io). If it helps you, a [tip on Ko-fi](https://ko-fi.com/lelulagames) is always appreciated. ♥

## License

MIT. Use it, change it, share it; keep the license and credit with it. See [LICENSE](LICENSE).
