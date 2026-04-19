# All Math All The Time — Project: Things To Do

*Last updated: 2026-04-19*

---

## 🟡 Should Do Soon

### 2. Fix "Made with MyST" branding
The MyST book-theme shows "Made with MyST" in two places:
- Top navigation bar (left side)
- Footer (bottom left, with the MyST logo)

The `nav_title` option in `myst.yml` did not remove it. Need to investigate:
- Whether a CSS rule can hide it (e.g., targeting the specific element)
- Whether there is a book-theme template option to disable the attribution
- Whether a custom template override is needed

### 3. Fix CSS section spacing
Added `article h2 { margin-top: 4.5rem; }` to `custom.css` but the rule is not taking
effect — the book-theme's own CSS is winning on specificity.

Next steps:
- Use browser inspector (Cmd+Option+I in Chrome/Safari) to identify the exact CSS
  selector the book-theme uses for h2 margin
- Match or exceed that specificity in `custom.css`

### 4. Add custom.css to publish.sh workflow
Currently `custom.css` lives directly in the git repo and must be edited and pushed
manually. It should live in Dropbox alongside all other source files and be copied
to the git repo by publish.sh on each run.

Steps:
- Move `custom.css` to `~/Dropbox/Apps/Overleaf/All Math All The Time/`
- Add one line to publish.sh: `cp "$DROPBOX/custom.css" "$REPO/"`
- Delete the copy from the git repo root (publish.sh will manage it going forward)

### 5. Expand project_workflow_guide.md
The current guide is thorough on the technical steps but light on the big picture.
Add a higher-level overview section covering:
- Why MyST was chosen (web-first, LaTeX-compatible math, GitHub Pages deployment)
- The overall vision for the finished site
- How the LaTeX book and the web version relate to each other
- A brief description of the book's scope and intended audience
- A note on the long-term roadmap (100 chapters, phased conversion)

---

## 🔵 Future / Lower Priority

### 6. Option 2 figures: SVG via lualatex + dvisvgm
Currently all TikZ figures go through: TeXShop → PDF → ghostscript → PNG.
PNG is lossy and resolution-dependent. A better long-term approach:

- Compile TikZ standalone files with `lualatex` + `dvisvgm` to produce SVG directly
- SVG is vector, scales perfectly at any screen size, no quality loss
- Requires setting up a custom TeXShop engine (one-time setup)
- Revisit when actively creating new standalone figures

### 7. Right-side CONTENTS panel — section numbers
The on-page CONTENTS panel (right sidebar) shows section titles without their numbers
(e.g., "Irrational Numbers" instead of "2.10 Irrational Numbers"). This is a
book-theme display choice. Investigate whether it is configurable via:
- A `myst.yml` site option
- A CSS override
- A book-theme template option

Low priority — the page headings themselves show correct numbers; this is cosmetic.
