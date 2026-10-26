# Homepage redesign: design

Date: 2026-10-26 · Site: chadreadey.github.io (static, GitHub Pages, `index.html` + `mlb/`)

## Why

An outside teardown found that the site reads like an expanded résumé. The proof that Chad builds working software sits below four jobs and the education list, the headline ("AI Engineer") doesn't set him apart, and every project is expanded into long Problem / What I built / Evaluation / Stack blocks.

The reader is a hiring manager or senior engineer screening for **AI engineering** (at an investment fund or a startup), **product engineering**, **forward-deployed engineering (FDE)**, or **ML engineering**. They are technical, short on time, and skeptical. After 30 seconds they should think: *"this person clears the technical bar and could fit as an engineer at my company."*

The specific risk to defeat: "former college athlete + finance background + AI engineer" can read as "finance person who prompts LLMs." The page breaks that assumption with shipped systems, real results and evaluation honesty. More credentials won't do it.

## Goals

- Proof of building appears in the first screen: a live product preview, then real projects within one scroll.
- Each featured project shows a short pitch, **one** meaningful result, one visual, and a clear link to the details.
- The work inside funds (Vistria, Crystal) is visible and specific, without revealing anything proprietary.
- The page has a clear, evergreen call to action naming the roles Chad wants.
- The visual identity looks deliberate and personal, not like a template or AI-generated output.

## Non-goals

- Impact numbers for Vistria and Crystal (add later; the layout must allow a one-line addition).
- A new public research-swarm project (possible follow-up).
- Decorative animation. Transitions only where they explain a change.
- Rewriting `mlb/writeup.html` or the NBA write-up.

## Anti-goals (failure even if it "works")

- **Anything shaped like Vistria's internal work.** No output format, sample output, sanitized diagram or fictional example of the research system. Text only. Chad was explicit: "don't want to cause any trouble."
- **Tan, cream or warm-paper backgrounds.** That's the Evidence Gap Mapper's own palette, and a common AI-generated-frontend look.
- **A headline or copy that reads AI-generated:** long hedged sentences, "X that Y, and Z that W" constructions, buzzword stacking.
- **Forced personality.** No "baseball taught me resilience" lines.
- **Dated content.** No "available January 2027" or similar; the page must stay true without edits.

## Decided

### Order of the page

1. **Nav:** name on the left; Work · Funds · About · Contact on the right.
2. **Hero:** two columns on desktop, stacked on mobile.
   - Left: a small mono label `AI ENGINEER · NEW YORK`, then the headline, subhead and actions.
   - Right: a cropped, annotated preview of the Evidence Gap Mapper tamoxifen matrix.
   - **Headline:** "Pitcher turned AI engineer."
   - **Subhead:** "I build AI agents and models for research and investing, shipped inside a private equity firm and a venture fund."
   - **Actions:** primary "See the work" (jumps to the projects), secondary "Get in touch" (jumps to the contact block). Résumé, GitHub and LinkedIn appear as small, quiet text links.
   - **Annotation on the preview:** "Live app: 563 tamoxifen studies mapped; orange cells are evidence gaps."
3. **Credibility strip:** one line of four items with thin rules above and below. Vistria (private equity), Crystal Venture Partners (venture capital), Columbia (M.S. Management Science & Engineering), Northwestern (B.A. Data Science).
4. **Selected work:** three cards in a row on desktop, stacked on mobile.
   - **Evidence Gap Mapper**
     - Pitch: name a drug; it pulls the literature, classifies every study, and shows where evidence is missing.
     - Visual: a focused crop of the matrix.
     - Primary link: the saved real run, `https://egm-production.up.railway.app/?run=94b73e48-3e86-408b-9887-e2a7d78a2e26`. Secondary link: "Start a new analysis" → `https://egm-production.up.railway.app/`.
     - Keep the honesty: the result line must not claim accuracy. The current page says no accuracy figure is measured yet.
   - **NBA forecast audit**
     - Pitch: found leakage behind a 0.35 MAE headline, then built an honest next-season forecast.
     - Visual: a horizontal chart of Δ MAE vs. baseline with 95% CIs and a zero line for the four test windows. 2022–26 must be visible and marked as worse.
     - Result: "Beats the baseline in 3 of 4 periods; the 4th is shown."
     - Link: the repo / README.
     - Data, taken from the current table:
       - 2007–11: −0.195 [−0.25, −0.14]
       - 2012–16: −0.207 [−0.27, −0.15]
       - 2017–21: −0.131 [−0.19, −0.07]
       - 2022–26: +0.067 [+0.00, +0.13]
       - Overall: −0.112 [−0.14, −0.08]
   - **Ball or strike**
     - Pitch: a model of the umpire's call; change the count and watch the zone move.
     - Visual: the same outside-corner pitch shown at 0–2 and 3–0. A side-by-side crop or a simple drawn graphic is fine.
     - Result: "Same corner pitch: 72% strike at 0–2, 92% at 3–0."
     - Links: demo, write-up, code.
5. **Inside funds:** two text blocks side by side, stacked on mobile.
   - **The Vistria Group** (private equity, 2026)
     - Signal research system: from an investment sleeve and a topic, a swarm of agents identifies the main theses and traces which headwinds and tailwinds **causally** drive each one, and why, across macro, micro, market-structure and other lenses. The causal analysis must be stated plainly; it's the point.
     - CRM agent: a natural-language interface over the firm's CRM (banker contacts, relevant CIMs, past financials, deal history). The IR team uses it to prep for fundraising contacts. Keep the existing engineering detail: it validates model-generated intent, builds parameterized queries, and enforces permission gating before touching sensitive data.
   - **Crystal Venture Partners** (venture capital, Dec 2025 – May 2026)
     - xT, a diligence agent that triages inbound deals, analyzes decks, researches companies and founders, and writes partner briefs. It was iterated through human-in-the-loop evaluation with the partners before rollout.
     - One breadth line: a calendar-management agent, classifiers inside the CRM (2,000+ records cleaned and classified), and assorted analyses and automations.
   - Handshake AI and Public Equity Group come off the homepage; they stay on the résumé.
6. **About:** the pitching photo next to one or two plain sentences.
   - Facts available: pitched at Northwestern; Big Ten All-Academic 2023, 2024, 2025; finishing an M.S. at Columbia.
   - Optional wry line, the builder's call: "The strike-zone model above is partly revenge."
   - Photo source: `/private/tmp/claude-501/-Users-chadreadey-portfolio-site/116ea0eb-cf0c-47c3-9ce8-76189e2cbb42/images/1.jpg` (2000×1333). Copy it into `media/`, crop to Chad (he's center frame, mid-follow-through), and compress to about 100–200 KB. Alt text describes him pitching for Northwestern.
7. **Also:** a compact list, one line each with a link.
   - **Childcare deserts (NYS):** a mixed-integer program that eliminates every childcare desert in New York State. The realistic model (candidate sites, spacing rules) is solved at about $445M: 2,343 facilities expanded and 3,513 new ones built. Link to the GitHub repo. That repo is being updated in a separate session; link it regardless.
   - **AI Financial Analyst** (being rebuilt): one line, no link.
   - **Olympic medals dashboard:** one line, with links to the dashboard and code.
   - "More on GitHub."
8. **Contact:** a dark block.
   - Headline: "Hiring for AI, product, forward-deployed, or ML engineering?"
   - Line: "I'd like to hear about it." Then "Based in New York", the email, résumé, LinkedIn and GitHub.
   - No dates.

### Visual system

- **Colors:**
  - Background: pure white `#ffffff`
  - Text: near-black ink `#17171a`
  - Secondary text: `#55555c`
  - Rules: `#e5e5e7`
  - Accent: burgundy `#7a1f35`, used for the primary button, labels and chart highlights
  - Contact block: an ink background
- **Drop:** the purple-to-red gradient and Montserrat.
- **Fonts:** Newsreader (serif) for headlines and card titles, Inter for body text, and JetBrains Mono only for small uppercase labels. All load from Google Fonts.
- Font Awesome icons are optional; text links are fine.
- Charts are crisp SVG, inline, using the same palette.
- Must work with no horizontal scroll at phone width (~375px).
- Keep the existing accessibility basics: skip link, focus-visible outlines, alt text.

### MLB demo (`mlb/index.html`)

- At intermediate widths (roughly 600–1000px), shrink the chart so that the controls and the probability readout stay visible next to it or right below it, without scrolling past the chart.
- Open on the outside-corner pitch preset, not dead center (which shows 99.7%).
- Add a one-click "corner pitch: 0–2 vs 3–0" toggle that sets the outside-corner pitch and flips the existing canvas between the two counts. *(Builder's call: a toggle, not a side-by-side view. It matches the write-up's wording and keeps the mid-width layout fix simple.)*
- Switch the demo's page styling to the new system: header, fonts, buttons and the canvas font at line 165. **Keep the heatmap's green→yellow→red probability scale and the STRIKE/BALL colors.** Those colors encode the data, and keeping them means `media/mlb_demo.jpg` still matches the live demo. *(Builder's call.)*
- `mlb/writeup.html` gets the same styling pass (CSS only; no copy rewrite), and its back-links change from `../#projects` to the new Work anchor. *(Builder's call.)*

### Metadata

- Update `<title>`, the meta description and the OG/Twitter text to match the new positioning.
- `og.jpg` can stay unless the builder has time to regenerate it.

## Left to the builder

- Exact spacing, type sizes, breakpoints, and the precise crops of the matrix and MLB images.
- Whether the MLB card visual is a crop of the demo or a small drawn SVG.
- Hover and focus states, plus small transitions.
- Exact wording of the pitches and the About lines, within the constraints above: short, plain, no AI-sounding constructions. Chad reviews the copy before shipping.

## Reference

- Mockups of the agreed direction (layout A; color option 1 supersedes A's tan): `.superpowers/brainstorm/32094-1793036588/content/` (git-ignored).
