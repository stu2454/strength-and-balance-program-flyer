# Strength and balance program — website

A small static website making the case for a community-driven, volunteer-delivered falls
prevention program in regional NSW.

Live at <https://stu2454.github.io/strength-and-balance-program-flyer/>

## How to edit it

There is no build step, no framework and nothing to install. Every page is a plain
`.html` file you can open in any text editor. Save the file, commit it, and the live site
updates within a minute or two.

| File | Page |
|---|---|
| `index.html` | Landing |
| `problem.html` | The challenge |
| `how-it-works.html` | The model |
| `evidence.html` | Does it work? |
| `involved.html` | Get involved |
| `paper.html` | Evidence base and downloads |
| `styles.css` | All styling for every page |

The navigation menu and the footer are repeated at the top and bottom of each of the six
HTML files. If you add or rename a page, update it in all six.

## Ground rules for edits

These come from `CLAUDE.md`, which holds the full project brief.

- **Every statistic on the site must appear in the Verified facts table** in `CLAUDE.md`.
  If you need a number that is not on that list, source it and add it there first.
- Australian English. "Program", "organisation", "recognise".
- Calm and factual. No exclamation marks, no promotional language.
- Keep body text at 18px or larger. The audience includes people in their eighties and
  nineties.
- No carousels, popups, chatbots, auto-playing media or cookie banners.
- Do not add Google Fonts, analytics or any external script. The site currently loads
  nothing from any third party, which is why it needs no cookie banner.

## Colours

Defined once, at the top of `styles.css`, as CSS custom properties. Change them there and
they change everywhere, including in the two diagrams.

## The diagrams

Both are inline SVG written directly into the HTML, so they scale cleanly and follow the
palette. Figure 1 (the care continuum) is on `index.html` and `paper.html`. Figure 2 (the
two tiers) is on `how-it-works.html`. `figure1-shift-left-continuum.svg` is a standalone
copy of Figure 1 for sharing and for social media previews.

Figure 1 is an original redrawing adapted from Eric Dishman's care continuum (Figure 3-1
in *The Future of Home Health Care: Workshop Summary*, Institute of Medicine / National
Research Council, 2015). **The attribution line must stay wherever the figure is used.**

## Still to do

- Add the full evidence paper as `falls-prevention-evidence-paper.pdf` in this folder.
  `paper.html` already links to that filename.
- Add outcome figures for A Matter of Balance and FallFitness on `evidence.html`. Both
  are marked with an HTML comment showing where they go.
- Replace the short-form reference list on `paper.html` with full citations.
- Confirm the program name. "Steady Together" is a working title.

## Checking it before you publish

Open the page in a browser and try these four things.

1. Press Tab repeatedly. Every link should show a visible blue outline, in a sensible
   order.
2. Zoom to 200%. Nothing should be cut off and the page should not scroll sideways.
3. Narrow the window to phone width. Text should reflow, not shrink.
4. Read it aloud. If a sentence would only make sense to a health policy specialist,
   rewrite it or move it to the PDF.

## Deployment

GitHub Pages serves the `main` branch from the repository root. The empty `.nojekyll`
file stops GitHub from processing the files through Jekyll. No other configuration is
needed.
