# Project brief — community falls prevention website

## What this is

A small static website making the case for a community-driven, volunteer-delivered falls
prevention program in regional NSW, and recruiting the three groups whose participation
makes the program viable.

It supports a grant application. It is **not** the grant application, and it is not the
full evidence paper rendered as HTML. The full paper exists separately and is linked as
a PDF download.

## Audiences, in priority order

1. **Community organisations** who might host a program (COTA, neighbourhood centres,
   Men's Sheds, service clubs, ACCHOs, local government community services)
2. **Older people** who might join a class or train as a volunteer leader
3. **Clinicians** (physiotherapists, GPs, exercise physiologists) deciding whether to
   support the program
4. **Grant reviewers** — secondary. They may follow a link from the application.

Every page should be legible to audience 2 without loss of credibility with audience 3.
If a sentence would only land with a health policy specialist, rewrite it or move it to
the PDF.

## Tech stack — keep it boring

- **Plain HTML, CSS and minimal vanilla JS.** No React, no build step, no bundler,
  no framework, no npm dependencies.
- Reason: this site must still work in five years with no maintenance, must be
  editable by a non-developer, and must load fast on rural connections.
- Multi-page static site. One `.html` file per page.
- One shared `styles.css`. CSS custom properties for the palette.
- Deployed via GitHub Pages from the repo root or `/docs`.
- Include an empty `.nojekyll` file at repo root so GitHub serves files starting with
  underscores correctly.

## Non-negotiable constraints

### Accessibility — WCAG 2.2 AA minimum

The audience includes people in their seventies, eighties and nineties. A falls
prevention site that is hard to use is self-defeating.

- Base font size **18px minimum**; body copy 19–20px is better
- Line length 60–75 characters; line height 1.6+
- Contrast ratio 4.5:1 minimum for body text, 3:1 for large text. No light grey on white.
- Tap/click targets 44×44px minimum, generously spaced
- Fully keyboard navigable, visible focus indicators (do not remove outlines)
- Works at 200% browser zoom without horizontal scrolling
- Semantic HTML: real `<h1>`–`<h3>` hierarchy, `<nav>`, `<main>`, `<footer>`,
  landmark roles where needed
- All images have meaningful `alt` text; decorative images `alt=""`
- Respect `prefers-reduced-motion`
- Never convey information by colour alone
- Test: the site must be fully usable with CSS disabled

### Things this site must NOT have

- Carousels, sliders, parallax, scroll-jacking
- Auto-playing video or audio
- Chatbots or popups of any kind
- Cookie banners (do not add analytics that require one)
- Hamburger-only navigation on desktop
- Animated counters that make numbers hard to read
- Stock photography of frightened elderly people near staircases, or of
  improbably athletic silver-haired couples on beaches. Both are alienating.

### Tone

Calm, plain, factual, warm. Short sentences. Australian English and spelling
("program" not "programme" — Australian health usage; "organisation", "recognise").
Never breathless or promotional. Do not use exclamation marks. Do not describe the
program as "revolutionary", "innovative" or "world-class".

## Site structure

```
index.html          Landing
problem.html        The challenge
how-it-works.html   The model
evidence.html       Does it work?
involved.html       Get involved
paper.html          Evidence base / downloads
```

### index.html — Landing

- One-sentence proposition above the fold
- The shift-left continuum figure as hero image (`figure1-shift-left-continuum.svg`,
  inline the SVG so it inherits the palette and scales cleanly)
- Three headline figures (see Verified facts below — use exactly these):
  - 41,000 — NSW fall hospitalisations each year
  - 4.3 years — average time participants stay in a peer-led program in New Zealand
  - A$12,800 vs A$98,300 — cost per quality-adjusted life year, volunteer-led vs
    professionally delivered group exercise
- Three clear paths into the site, matching the three audiences
- No more than two screens of content

### problem.html — The challenge

Two sections, roughly a screen each:
1. **The scale of falls** — NSW burden, cost, projected growth
2. **Why prevention doesn't reach regional communities** — the workforce constraint

Critical framing: this is a **design problem, not a performance problem.** Rural
clinicians already carry heavier caseloads with less support. Nothing on this page may
read as criticism of clinicians. State this explicitly.

### how-it-works.html — The model

The page that answers "is this safe and who is responsible?"

- The two-tier structure: volunteers deliver, clinicians govern
- What a class actually looks like (weekly, one hour, ongoing, local hall)
- The four points of clinical input: content design, leader training, periodic
  progression review, escalation and referral
- Governance, insurance and indemnity, stated plainly
- A simple diagram of the two tiers — build as inline SVG, not an image file

### evidence.html — Does it work?

Plain-language summaries of: Steady As You Go (NZ), A Matter of Balance (US),
FallFitness (Sweden), Stepping On (NSW).

**Include the limitations section.** A page that only sells reads as marketing.
State honestly that no trial has directly compared volunteer-led with clinician-led
delivery on falls outcomes, and explain why the relevant comparison in most regional
communities is with no program at all.

### involved.html — Get involved

Three distinct paths, three distinct asks. This is the conversion page.

- **Host a program** — what a host organisation provides, what it receives
- **Become a leader** — what training involves, what the commitment is, who it suits
- **Support as a clinician** — state the time commitment up front and precisely:
  roughly 10–15 hours in the establishment year, 4–8 hours annually thereafter.
  Vagueness loses clinicians.

Contact method: a `mailto:` link, or a form via Formspree/Netlify Forms if a backend
is needed. Do not build a custom form handler.

### paper.html — Evidence base

Download link for the full PDF paper, the reference list, and attribution for Figure 1.

## Design system

Palette is inherited from the continuum figure so the site and the diagram cohere.

```css
:root {
  --amber:      #F0921E;  /* community & home / the left of the continuum */
  --blue:       #29ABE2;  /* residential care */
  --green:      #8CC63F;  /* acute care */
  --deep-blue:  #1064A8;  /* axis arrows, primary accent */
  --heading:    #1F4E5F;  /* headings */
  --ink:        #24292E;  /* body text */
  --muted:      #58595B;  /* secondary text — do not go lighter */
  --paper:      #FFFFFF;
  --tint:       #F7F9FA;  /* section backgrounds */
}
```

Typography: one serif for headings, one sans for body — or a single well-chosen sans
throughout. Use system font stacks or self-host; **do not** load Google Fonts (privacy,
and it is a render-blocking dependency on slow connections).

Layout: single column, generous whitespace, max content width ~70ch. Mobile-first.
Content must reflow cleanly from 320px to 1600px.

Imagery: until real photographs of actual classes exist, use restrained illustration,
typography and the SVG diagrams. Bad stock photography is worse than none.

## Verified facts — use these exact figures, do not invent others

Every number below is sourced in the full paper. If content calls for a statistic not
on this list, flag it rather than inventing one.

| Fact | Figure | Source |
|---|---|---|
| NSW fall hospitalisations per year | ~41,000 | NSW Clinical Excellence Commission (2021) |
| NSW fall deaths per year | >1,200 | NSW Clinical Excellence Commission (2021) |
| Australian health system cost of falls | A$4.3–5 billion/year | AIHW |
| NSW projected growth in fall hospitalisations by 2051 | ~3× on demographics alone; >10× if current trends persist | Watson et al. |
| NSW projected growth in aged care transfers by 2051 | 3.2× | Watson et al. |
| Average participation, peer-led NZ program (SAYGO) | 4.3 years (range 1–10) | Age Concern Otago cohort |
| Cost per QALY, peer-led group exercise | ≈ A$12,800 | Deverall et al., converted |
| Cost per QALY, professionally delivered group exercise | ≈ A$98,300 | UK economic evaluation, converted |
| Return per dollar invested, community falls program | A$1.97–A$7.43 | Staying Steady (UK) evaluation |
| Fall reduction, Stepping On original trial | 31% | Clemson et al. |
| Stepping On NSW scale-up | 1,077 sites, 10,096 participants, 2009–2014 | Paul et al. |
| Rural NSW fall patients, 30-day mortality | 5.0% vs 4.9% urban | Sukumar et al. |
| Rural NSW fall patients, 28-day readmission | 18.9% vs 17.0% urban | Sukumar et al. |
| Clinician commitment, establishment year | 10–15 hours | Author's estimate — label as an estimate |
| Clinician commitment, steady state | 4–8 hours/year | Author's estimate — label as an estimate |

Currency note: AUD conversions are nominal, at £1 = A$1.91, from source figures with
2010–2011 price bases. Do not present them as current-dollar precision.

## Attribution requirements

Figure 1 is an original redrawing adapted from Eric Dishman's care continuum
(Figure 3-1 in *The Future of Home Health Care: Workshop Summary*, Institute of
Medicine / National Research Council, 2015). The attribution line must appear wherever
the figure is used. Do not reproduce the original figure.

## Deployment

- GitHub Pages, `main` branch, root or `/docs`
- Add `.nojekyll` at root
- Custom domain: add a `CNAME` file containing the bare domain, and set the DNS
  A records / CNAME at the registrar
- Enable "Enforce HTTPS" in repo settings
- Add `robots.txt` and a `sitemap.xml`
- Meta tags on every page: description, Open Graph title/description/image
  (use the continuum figure as the OG image)

## Definition of done

- Lighthouse accessibility score 100
- Passes axe DevTools with no violations
- Fully usable by keyboard alone
- Readable at 200% zoom with no horizontal scroll
- Total page weight under 500KB per page
- No console errors
- Every statistic on the site appears in the Verified facts table above
