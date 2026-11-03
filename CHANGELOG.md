# Reitz LaTeX — Changelog

## 1.3.2

Checked against a second, richer reference render (the *MentalHealthError*
essay — block quotes, multi-line lists, footnotes). It surfaced one real
divergence and one measurement to tighten.

- **Block quotes now match LaTeX's `quote`.** They were centered italic (a
  house epigraph look); LaTeX sets a blockquote indented from both margins,
  upright roman, justified, no rule. Measured from the render at 2.5em each
  side, and matched. This changes the opening quote on every note from
  centered-italic to indented-roman — the faithful result. To keep the old
  epigraph look, set the blockquote to `font-style: italic; text-align: center`.
- **List indent to the measured 2.5em** (was 1.9em) — LaTeX's `\leftmargini`,
  confirmed against the bullet list's own text column in the render.

## 1.3.1

Presentation polish — craft on top of the 1.3.0 metrics, to make the
typeface look as good as it can rather than merely correct.

- **Optical sizes, the connoisseur's tell.** LaTeX doesn't shrink the body
  font for footnotes; it sets them from *cmr7*, a face cut heavier so small
  text keeps its color. Bundled **LMRoman7** and pointed footnotes and
  superscripts at it. With the title in LMRoman12 and body in LMRoman10, the
  theme now spans three optical sizes, as a real Computer Modern document does.
- **A breath more leading.** 1.20 read a hair tight on screen; nudged to 1.30
  (≈ `\linespread{1.08}`), still firmly booky. Set 1.20 for print-exact.
- **Microtypography**, as far as the browser allows: prettier line breaking
  (`text-wrap: pretty`), no stranded last words (`orphans`/`widows`), LaTeX's
  own hyphenation minimums (words of 5+ may break, 2 before / 3 after), and
  contextual ligatures plus kerning on. Headings balance across lines.
- **Lists set like `itemize`/`enumerate`** — tight column, modest indent,
  hanging labels in full ink — instead of Obsidian's web-loose default. This
  was the biggest visible gap between the theme and a set LaTeX page.
- **Superscripts no longer open the line** (`line-height: 0`), the way
  `\textsuperscript` rides within the leading rather than pushing it apart.
- **Verbatim details:** `\texttt` sized to read at body size (0.95em, past the
  monospace swell), arrow/comparison ligatures off so `->` and `!=` stay
  literal, and code blocks on the 1.2 body leading.
- **Tables:** figures set as lining tabular numerals so numeric columns align
  digit-over-digit, with a little `\addlinespace` opening the body from the
  header rule.
- **Heading rhythm:** the space above a heading is now markedly larger than
  the space below, so it binds to the text it introduces — the LaTeX habit.

## 1.3.0

The theme now matches real LaTeX output, measured against an actual
`pdflatex`/Tectonic render of one of the essays rather than approximated by
eye. `pdffonts` and the PDF's own word-boxes supplied the ground truth.

- **The real fonts.** Dropped Computer Modern Unicode (a faithful clone) for
  **Latin Modern** — the exact faces a modern LaTeX run embeds: LMRoman10 for
  body, bold, and italic; LMRoman12-Bold for the title's optical size;
  LMMono10 for verbatim. Converted straight from the OpenType sources to
  woff2 and inlined. Latin Modern has no Hebrew or Devanagari, so those glyphs
  fall to the serif fallback — exactly as they did under CMU, and as `lmodern`
  itself would.
- **Verbatim is now LM Mono, not IBM Plex.** Reading-view code and inline
  `\texttt` take Latin Modern Mono, the typewriter LaTeX actually sets. The
  source editor keeps IBM Plex Mono (the Reitz Mono workshop) via a new
  `--font-editor`, so the two concerns no longer share one variable.
- **Leading 1.45 → 1.20.** The PDF's baseline-to-baseline was 12pt over a
  10pt body — the classic Computer Modern 1.2 ratio. This was the single
  biggest spacing tell; the old 1.45 read as web, not paper.
- **Heading scale to LaTeX's own.** Measured from the render: the title is
  1.44× body (14.4pt / 10pt), set in LMRoman12-Bold and still centered like
  the default `\maketitle`; `## sections` are 1.2× (12pt), down from the old
  1.5×. Deeper levels taper 1.1 → 1.0. (The reference template left-aligns its
  title; set `h1 { text-align: left }` to match that instead of `\maketitle`.)
- **Paragraph spacing to the measured parskip** — 0.6em (6pt over 10pt),
  block paragraphs, no indent, as before but now to the number.
- **Measure confirmed, not changed.** LaTeX's article `\textwidth` on US
  Letter is 4.81in ≈ 34.6em ≈ 77 characters; at 19px body the existing 41rem
  already lands there, so it stayed.

## 1.2.0

- **Code blocks join the monochrome.** Prism syntax highlighting was the
  last color left on the page — pink keywords, green strings, yellow
  functions, glaring against the paper-and-ink everything else. Rather than
  fight Prism's `.token` specificity, the theme now re-points Obsidian's own
  `--code-*` variables at the `--text-*` palette: keywords, functions, and
  identifiers in normal ink, strings and operators muted, comments faint —
  and, carried on two small reading-view rules that color can't express,
  bold keywords and italic comments. The listings-package look. Because the
  variables resolve through `--text-*`, it flips correctly in dark mode. The
  source editor is untouched; it was already all-mono.
- **Dataview results dress like the article.** Table results already
  inherited the booktabs rules; now the result-count line goes quiet
  typewriter and the error box becomes a hairline `--text-faint` frame
  instead of a red web alert. (Class names verified against the installed
  Dataview 0.5.68: `.small-text`, `.dataview-error-box`, `-message`.)
- **External links get the muted arrow.** Obsidian's background-image link
  icon is dropped for a small `↗` in the faint ink that brightens with its
  link on hover — the treatment Reitz Mono settled on. In print the arrow
  becomes the URL itself, spelled out after the link like `\url` apparatus.
- **`==Highlights==`** now take the same warm-yellow wash as the text
  selection — a highlighter over paper, not a banner. Underlined, not
  filled, in print, since toner is monochrome.
- **Hover previews become slips of paper** — square corners, a hairline ink
  border (the same `--text-normal` every callout and rule uses), a faint
  lift — instead of the default rounded floating card.
- **Canvas cards** get square corners and the body serif, a small nod to
  TikZ. Node and edge colors are deliberately left alone: the System 777
  maps use Obsidian's numbered palette semantically, and a monochrome theme
  doesn't get to overrule meaning.
- **PDF fix.** The 1.1.4 change that made wide tables horizontal scroll
  containers clipped them in export — a scroll region has no second page.
  Print now unrolls tables back to honest `display: table` with wrapping
  cells, so nothing is lost off the right edge on paper.

## 1.1.5

- **Center figures.** The image-centering rule from 1.1.0 didn't cover inline
  `<svg>`, so diagrams like the Tree of Life glyph rendered left-aligned. All
  block-level figures — SVG, images, and `align=center` wrappers — now center
  like a LaTeX figure.

## 1.1.4

- **Wide tables scroll instead of clipping.** Correspondence tables with many
  columns overflowed the pane and were cut off at the right edge, which also
  squeezed cells into three-line stacks. Tables are now scroll containers
  (internal column alignment preserved), short link cells stay on one line,
  and only paragraph-length single-column cells wrap. Quiet 6px scrollbar in
  the faint ink color.

## 1.1.3

- **Mermaid dark mode, third pass.** Stopped chasing Obsidian's shifting
  container classes and re-rooted every figure rule at the rendering
  surfaces (`.markdown-preview-view` / `.markdown-rendered`) plus Mermaid's
  own stable internal classes, with an `svg[id^=mermaid]` fallback. Nodes
  take paper fill with ink hairlines in both modes; edges, arrowheads, and
  edge-label chips take ink-on-paper.

## 1.1.2

- **Mermaid, actually fixed.** A screenshot test showed the entire TikZ
  figure treatment silently failing: current Obsidian renders Mermaid inside
  `.block-language-mermaid`, not the legacy `.mermaid` class the selectors
  were rooted at — so nodes kept Mermaid's default light fill (glaring on
  dark paper) and edges its default dark stroke (invisible on it). All
  figure rules are re-rooted at both containers with an svg-id fallback:
  paper-filled ink-hairline nodes, ink edges and arrowheads, serif labels,
  and edge labels sitting on paper instead of floating as light chips.

## 1.1.1

- **Fixed Mermaid edges invisible in dark mode.** Newer Mermaid renderers
  emit edge and marker classes the original selectors missed, leaving edges
  at Mermaid's default dark-gray stroke — fine on light paper, invisible on
  dark. Edges, arrowheads, and edge labels now take the ink color in both
  modes, with a slightly heavier 1.1px stroke (hairlines read thinner on
  dark ground).

## 1.1.0

Coverage release — extends the LaTeX idiom to elements previously left to
Obsidian defaults. No existing design decisions changed; monochrome holds.

### Callouts
- `[!warning]`, `[!todo]`, and friends now render **amsthm-style**: hairline
  box, small-caps run-in label, no icon, no color coding — a "Remark." block
  in a paper, not a yellow web banner.

### Footnotes
- LaTeX `\footnoterule`: short left-aligned hairline before the notes, small
  type (0.85em) below it, muted backref arrows, undecorated superscripts.

### Tasks
- Checkboxes are plain hairline squares; done items fill the square and mute
  the text — no strikethrough (print doesn't cross things out).

### Figures & embeds
- Images centered like `\begin{figure}[h]\centering`; explicit-width inline
  images stay in the line.
- Transclusions read as quiet quotations: hairline left rule, no title
  chrome, no boxed-widget look.

### Tags
- Rendered `#tags` in typewriter, no pill.

### Print
- `@media print`: full black-on-white, properties hidden, no-break rules for
  headings, tables, figures, callouts, and Mermaid — the theme's whole
  premise, carried through to actual paper.


## 1.0.0

The first release. An Obsidian theme that typesets notes the way LaTeX
would — Computer Modern, justified and hyphenated prose, booktabs tables,
short centered rules, plain typewriter code.

### Typography
- Bundled the full **Computer Modern Unicode (CMU)** family as local WOFF2
  (serif roman/bold/italic/bold-italic, typewriter regular/bold/italic, sans
  regular/bold) — public domain, works offline.
- Body text in CMU Serif, justified with automatic hyphenation, at a booky
  ~41rem measure. Kerning and ligatures on.
- Forced the fonts through every Obsidian variable variant
  (`--font-text` / `-override` / `-theme`, plus monospace and interface) with
  `!important`, so Computer Modern holds in both reading view and the raw
  source editor.

### Layout
- `#` title centered like `\maketitle`; `##`/`###` as left-aligned bold
  `\section` / `\subsection`. Editor heading classes paired for Live Preview
  parity.
- `>` blockquotes rendered as centered italic epigraphs.
- `---` rules become short, centered hairlines.
- Code (inline and blocks) in CMU Typewriter with no boxes or shading.
- Tables in booktabs style: thick top/bottom rules, a thin header rule, no
  vertical lines.
- Hid the inline title — a note's own `#` heading is the document title, so
  the filename above it would be a duplicate.
- Justification applies to rendered prose only; the raw source editor stays
  ragged.

### Color
- Light "paper-and-ink" and dark "dark-paper" variants, both Computer Modern.
- Text selection in the warm yellow inherited from Reitz Mono
  (`rgba(255, 220, 40, …)`), applied in reading view and the editor.

### Type
- Monospace is now **IBM Plex Mono** (from Reitz Mono) instead of CMU
  Typewriter — for both reading-view code and the all-mono editing mode.
  Serif body stays Computer Modern. The three IBM Plex faces (regular, bold,
  italic) are base64-inlined; the CMU Typewriter faces were removed.

### Behavior
- Properties collapsed by default in reading view (as Reitz Mono does): a
  quiet italic `[properties]` label at rest, rows revealed on hover; the
  source/editing view keeps them expanded.
- Editing mode now fully replicates Reitz Mono. The raw source editor becomes
  IBM Plex Mono at 14px/1.8 with ligatures off (so raw markdown like `->`,
  `!=`, `==` renders literally) and tabular slashed-zero figures, a breathing
  colored cursor, a warm active-line glow, a subtle spotlight vignette, faint
  indent guides, a centered 760px measure, and a quiet gutter. Reading view is
  untouched and stays Computer Modern serif.

### Fixes
- Inlined the fonts as base64 data URIs — Obsidian injects theme CSS inline,
  so relative `url('fonts/…')` paths never load.
- Kept the chrome on the system UI font. Computer Modern Sans in the sidebars
  and menus read as a "weird font"; Computer Modern is now content-only, so
  the bundled set is four serif + three typewriter faces (the unused sans
  faces and their `@font-face` blocks were removed).

### Diagrams
- Mermaid rendered like a TikZ figure: hairline dark strokes on a clean fill,
  serif labels in the body font, centered, height-capped, no code-block box.
