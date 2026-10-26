# Homepage Redesign Implementation Plan

> **For agentic workers:** REQUIRED SUB-SKILL: Use superpowers:subagent-driven-development (recommended) or superpowers:executing-plans to implement this plan task-by-task. Steps use checkbox (`- [ ]`) syntax for tracking.

**Goal:** Rebuild `index.html` and restyle `mlb/` to the approved design, which puts proof first.

**Architecture:** A static single page with inline CSS. There's no build step and no JavaScript on the homepage. Charts are inline SVG. The MLB demo keeps its canvas model code; only its layout, styling and initial state change.

**Tech Stack:** HTML/CSS, inline SVG, vanilla JS canvas (MLB), Google Fonts (Newsreader, Inter, JetBrains Mono), `sips` for images.

**Spec:** `docs/superpowers/specs/2026-10-26-homepage-redesign-design.md`

## Global Constraints

- **Palette:**
  - bg `#ffffff`
  - ink `#17171a`
  - secondary `#55555c`
  - rule `#e5e5e7`
  - accent `#7a1f35`
  - No tan, cream or gradient.
- **Fonts:** Newsreader for headings, Inter for body text, JetBrains Mono only for small uppercase labels. No Montserrat.
- **Fixed copy:**
  - Headline: "Pitcher turned AI engineer."
  - Subhead: "I build AI agents and models for research and investing, shipped inside a private equity firm and a venture fund."
  - Contact headline: "Hiring for AI, product, forward-deployed, or ML engineering?"
- **Content rules:**
  - No dates in the call to action.
  - No Vistria output format or diagrams.
  - No accuracy claim for the Evidence Gap Mapper.
- **Layout:** no horizontal scroll at 375px.
- **Accessibility:** keep the skip link, focus-visible outlines and alt text.

## Review Focus

1. **375px phone width:** the hero, cards, chart and funds must stack with no horizontal scroll. Check with `document.documentElement.scrollWidth <= innerWidth`.
2. **MLB at ~750px:** the probability readout must be visible in the same viewport as the chart without scrolling. Check in the browser at 750×900.
3. **MLB initial state:** on load it must show the outside-corner pitch, not 99.7% at center. With the toggle at 0–2 it shows 72%, and at 3–0 it shows 92%.
4. **Dead anchors:** every in-page `href="#…"` and every `../#…` link in `mlb/` must resolve to an existing id.
5. **NBA chart honesty:** the 2022–26 marker must be drawn on the "worse" side of zero, with its CI shown.

---

### Task 1: Images

**Files:**
- Create: `media/pitch.jpg`, `media/egm_crop.jpg`

- [ ] Crop the source photo (spec §About) to roughly 4:5 around the pitcher, then resize to 800px wide at JPEG quality ~75. Target 100–200 KB.
- [ ] Crop `media/egm_matrix.jpg` to its top table region for the hero and card previews, at 1200px wide.
- [ ] Verify with `ls -l media/` that both files exist at the target sizes.

### Task 2: Homepage rebuild

**Files:**
- Modify: `index.html` (full rewrite)

**Interfaces:**
- Produces these section ids: `#work`, `#funds`, `#about`, `#also`, `#contact`.
- `mlb/` links back to `../#work`.

- [ ] Rewrite `index.html` in spec order: nav, hero, strip, `#work` (three cards), `#funds`, `#about`, `#also`, `#contact`.
- [ ] Add the NBA SVG with this data:
  - 2007–11: −0.195 [−0.25, −0.14]
  - 2012–16: −0.207 [−0.27, −0.15]
  - 2017–21: −0.131 [−0.19, −0.07]
  - 2022–26: +0.067 [+0.00, +0.13]
  - Overall: −0.112 [−0.14, −0.08]
  - Use a linear x scale over [−0.30, +0.15] with a zero line.
- [ ] Set the Evidence Gap Mapper links to the saved run and "Start a new analysis".
- [ ] Update the meta and OG text.
- [ ] Verify Review Focus items 1, 4 and 5 in the browser at 1280, 750 and 375.

### Task 3: MLB demo and write-up

**Files:**
- Modify: `mlb/index.html`, `mlb/writeup.html`

- [ ] Swap the page chrome to the palette and fonts. Change the canvas font (line ~165) to Inter. Keep the heatmap and the STRIKE/BALL colors.
- [ ] Bring the chart height down at 600–1000px so the readout shares the viewport. Either constrain the canvas `max-height` to around 60vh, or keep two columns down to about 640px.
- [ ] Set the initial state to the outside-corner pitch against a right-handed batter, at mid-zone height, as the write-up defines it. Add a "Corner pitch: 0–2 ↔ 3–0" button that sets that location and toggles the count.
- [ ] Repoint `../#projects` to `../#work`.
- [ ] Verify Review Focus items 2 and 3.

### Task 4: Review and commit

- [ ] Run a fresh code review over the diff.
- [ ] Fix the confirmed issues.
- [ ] Commit, and ask before pushing.
