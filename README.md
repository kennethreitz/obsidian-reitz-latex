<div align="center">

# Reitz LaTeX

### Write like iA Writer. Read like a LaTeX paper.

*An Obsidian theme for people who believe the medium is the message.*

`v1.3.2` · light & dark · fonts embedded · works offline · MIT

<!-- screenshots/hero.png: editing view beside reading view -->

</div>

---

Your notes are drafts while you write them. When you read them back, they should look like they matter.

Reitz LaTeX gives Obsidian two modes of mind. **Editing** is a quiet, monospaced room in the spirit of iA Writer, where you're alone with the words. **Reading** turns the same note into a typeset academic paper: Latin Modern, justified and hyphenated text, real heading hierarchy, booktabs tables and figures, all set the way TeX would set them.

## The thinking behind it

### The medium is the message

McLuhan was right. How a thing looks isn't decoration on top of the content. It changes what the content *is*. The same paragraph reads as a scribble in one typeface and as an argument in another. Set your thinking like a scratchpad and you'll treat it like one. Set it like a paper and you'll start writing papers.

So this theme takes a deliberate position: aesthetics come first. The look is the point, not a finish applied at the end.

### Writing and reading are different acts

**Editing, inspired by iA Writer.** The source editor is set entirely in IBM Plex Mono, with headings, bold and italic all in one honest monospace. There's a centered 760px measure, a warm active-line glow, a breathing cursor, faint indent guides and a soft spotlight vignette behind the text. Markdown stays visible and plain. Nothing is justified or hyphenated, so the text never shifts under your cursor. It's a workshop.

**Reading, inspired by the LaTeX article.** Reading view becomes the finished document. The body is set in Latin Modern Roman at a LaTeX-faithful scale. The title is centered like `\maketitle` in its own optical face, and section headings follow LaTeX's measured size ratios. Paragraphs are justified and hyphenated. The measure, about 41rem, is tuned to the `\textwidth` of a LaTeX article on US Letter.

Going from one to the other should feel like a change of state: from draft to document.

### Information architecture is the real feature

Typography is how structure becomes visible. A good page tells you, before you read a word, what's a title, a section, an aside, a citation or a figure. Reitz LaTeX treats every Obsidian element as part of a document hierarchy, the way a paper would: callouts become theorem environments, embeds become quotations, footnotes drop below a rule, and Dataview results become tables in the body. Each element gets one clear typographic role, so the shape of your thinking is legible at a glance.

## Typefaces

All embedded as WOFF2, so there are no network calls and nothing to install.

| Role | Face | Why |
|---|---|---|
| Body (reading) | **Latin Modern Roman** | The modern descendant of Knuth's Computer Modern, the face of TeX itself |
| Title | **Latin Modern Roman Caps** / 12pt optical size | `\maketitle` uses the larger optical cut |
| Footnotes & superscripts | **Latin Modern Roman 7** | LaTeX sets `\footnotesize` from cmr7, cut heavier to stay readable small |
| Code (reading) | **Latin Modern Mono** | LaTeX's `\texttt`, set at body size, ligatures off |
| Editor | **IBM Plex Mono** | A warm, precise monospace for the iA Writer-style workshop |
| Interface | System UI font | LaTeX has no interface chrome, so the app chrome stays native |

Inline and display math are already rendered by MathJax in Computer Modern, so they match the body with no extra work.

## Built-in features

**Typography**
- The body uses LaTeX's 10pt/12pt leading ratio, adapted for screens.
- Rendered paragraphs are justified and auto-hyphenated, while headings, tables, code and callouts never stretch.
- Microtypography approximates the `microtype` package.
- Paragraphs are separated by space with no first-line indent, in the `parskip` style.
- Bold and italic use the serif's own true faces.
- Table figures use lining tabular numerals, so numeric columns line up.
- The inline filename title is hidden, so your H1 is the title.

**Document structure**
- **Callouts:** `amsthm`-style, with a hairline box and a small-caps run-in label. Foldable callouts keep a quiet triangle.
- **Footnotes:** a short left-aligned hairline like `\footnoterule`, set in the 7pt optical face.
- **Blockquotes:** justified and indented like a quotation environment.
- **Embeds and transclusions:** a quiet quotation, not a boxed widget.
- **Lists:** LaTeX `itemize`/`enumerate` spacing, with a tight column and hanging markers.
- **Task lists:** a plain hairline square, filled when done.
- **Figures:** images and SVGs centered like `\begin{figure}\centering`, with tiny inline icons left in the line.
- **Tables:** in the `booktabs` style, centered at the measure. Wide tables scroll instead of clipping, and internal links in cells never break.
- **Display math:** centered, with LaTeX's own vertical spacing.

**Code**
- Monochrome syntax highlighting in the `listings` style: bold ink keywords, faint italic comments and muted strings.
- Literal verbatim with ligatures off, so `->` and `>=` never fuse.
- The copy-code button is quieted so it doesn't compete with the content.

**Diagrams**
- **Mermaid as TikZ:** paper-filled nodes, ink hairlines, serif labels and visible arrowheads, in both modes and across Obsidian's changing renderers.
- **Canvas:** square cards in the body serif, as a nod to TikZ.

**The rest of Obsidian, made printerly**
- Links get a printerly treatment, with external-link icons quieted.
- Tags render as typewriter text, not pills.
- `==Highlights==` and text selection share one warm yellow wash.
- Hover previews look like a slip of paper, with square corners and a hairline ink border.
- Dataview results are treated as content and match the article.
- Collapsible properties sit quietly as a "+" at rest and flip to "−" on hover.

**Print and PDF export**
- Exports look like a real paper, which is the whole point of looking like LaTeX.
- External URLs appear after their link text, the way they do in print.

**Modes**
- **Light:** ink on paper.
- **Dark:** the same Latin Modern on dark paper, with diagrams and edges kept at full contrast.
- Live Preview headings follow the reading-view scale but stay left-aligned, so the cursor never jumps.

## Installation

### From Obsidian *(once listed in Community Themes)*
1. Open **Settings → Appearance → Themes → Manage**.
2. Search for **Reitz LaTeX** and click **Install and use**.

### Manually
1. Download `theme.css` and `manifest.json` from the [latest release](https://github.com/kennethreitz/obsidian-reitz-latex/releases/latest).
2. Create the folder `<your vault>/.obsidian/themes/Reitz LaTeX/` and put both files in it.
3. In Obsidian, open **Settings → Appearance → Themes** and pick **Reitz LaTeX**.

### From source
```bash
git clone https://github.com/kennethreitz/obsidian-reitz-latex.git \
  "<your vault>/.obsidian/themes/Reitz LaTeX"
```
Then pick it in **Settings → Appearance → Themes**. Run `git pull` to update.

> **Tip:** for the full effect, write in **Source mode** and read in **Reading view**. You can toggle between them with `⌘E` / `Ctrl+E`.

## Changelog

See [CHANGELOG.md](CHANGELOG.md).

## License

The theme CSS is MIT-licensed, © Kenneth Reitz.
The bundled fonts are Latin Modern ([GUST Font License](fonts/licenses/GUST-FONT-LICENSE.txt)) and IBM Plex Mono ([SIL Open Font License 1.1](fonts/licenses/IBM-Plex-OFL.txt)).

<div align="center"><sub>Made by <a href="https://kennethreitz.org">Kenneth Reitz</a>, for humans.</sub></div>
