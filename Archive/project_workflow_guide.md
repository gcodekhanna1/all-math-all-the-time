# All Math All The Time — Project Workflow Guide

*Last updated: April 2026*

This document describes the complete setup and workflow for converting the LaTeX textbook
"All Math All The Time" into a web-published MyST Markdown site hosted on GitHub Pages.

---

## 1. Project Overview

The book is authored in LaTeX using Overleaf. The goal is to publish each chapter as a
web page using [MyST Markdown](https://mystmd.org), deployed automatically to GitHub Pages.
The conversion happens chapter by chapter. The LaTeX source remains the content authority —
the `.md` files are faithful renderings of the `.tex`, not paraphrases.

**Live site:** https://gcodekhanna1.github.io/all-math-all-the-time

---

## 2. Folder Structure

### 2.1 Dropbox (Source of Truth)

All source files live in:
```
~/Dropbox/Apps/Overleaf/All Math All The Time/
```

Key contents:

| Item | Description |
|------|-------------|
| `A_All Math All The Time.tex` | Main LaTeX file — defines Part/Chapter order |
| `foundations_*.tex` | Chapter LaTeX source files |
| `foundations_*.md` | Converted MyST Markdown files (live alongside .tex) |
| `myst.yml` | MyST project config — TOC, numbering, site options |
| `index.md` | Book landing page |
| `elegant.cls` | Custom LaTeX class |
| `figures/` | All math diagram assets (PDFs, PNGs, source files) |
| `document_images/` | Decorative images (portraits, chapter headers, etc.) |

**Asset organization rule — no exceptions:**
- `figures/` → all math diagrams (TikZ PDFs, SVGs, EzDraw sources, PNGs)
- `document_images/` → decorative/non-math images
- Root folder → `.tex`, `.md`, `.yml`, `.bib` files only — no loose image files

### 2.2 Git Repository (Publishing Target)

```
~/Dropbox/all-math-all-the-time-git/
```

This is a permanent local clone of the GitHub repo. Never delete or re-clone it.
The publish script syncs files from Dropbox into this folder and pushes.

**GitHub repo:** https://github.com/gcodekhanna1/all-math-all-the-time

The git repo mirrors the Dropbox structure:
```
all-math-all-the-time-git/
  myst.yml
  index.md
  custom.css
  foundations_*.md
  figures/          ← synced from Dropbox/figures/
  document_images/  ← synced from Dropbox/document_images/
  .github/workflows/
  public/
```

### 2.3 Claude Skill

The conversion skill and publish script live at:
```
~/.claude/skills/math-book-myst-migration/
  SKILL.md                    ← conversion rules and guidelines
  scripts/publish.sh          ← publish script
```

Claude's working copy of the skill is maintained in the Cowork session and written to
Dropbox when updated. To install the latest version, Claude will provide the exact
heredoc command to paste into Terminal — this is more reliable than copying from Dropbox
since the Dropbox path for Claude Skills varies by machine setup.

---

## 3. Authoring Environment

| Tool | Role |
|------|------|
| **Overleaf** | Primary LaTeX editor — real-time sync to Dropbox |
| **TeXShop** | Local LaTeX compilation (standalone TikZ figures) |
| **VS Code** | Viewing/editing .md files; browsing project folder |
| **Dropbox** | Sync between Overleaf and local machine |

**Important:** VS Code does not auto-detect external file changes from Overleaf sync.
After editing in Overleaf, refresh VS Code manually:
right-click the Explorer panel → **Refresh Explorer**.

---

## 4. Conversion Process

### 4.1 Overview

```
1. READ      → Read the .tex chapter file from Dropbox (after Overleaf sync)
2. PLAN      → Identify conversion decisions (TikZ, colors, special environments,
               author notes to skip, figures needing placeholders)
3. FIGURES   → Move chapter's figure files into figures/ subfolder in Dropbox
               Create placeholder PDFs for any figures not yet completed
4. ANNOTATE  → Add % MyST: annotations to the .tex in Overleaf for complex constructs
5. CONVERT   → Produce the .md file using the skill's conversion rules
6. SAVE      → Write .md to Dropbox (same folder as .tex)
7. UPDATE    → Add file to myst.yml TOC (uncomment) + update index.md
8. PUBLISH   → Run publish.sh
```

Conversion is done chapter by chapter using a Claude subagent (to avoid context timeouts
on long chapters). The main conversation handles planning and review; the subagent does
the actual conversion.

### 4.2 Frontmatter Template

Every converted `.md` file begins with this frontmatter:

```yaml
---
title: "NN - Chapter Title"
label: chap:label_from_latex
author: Gaurav Khanna, Ph.D.
numbering:
  enumerator: "N.%s"
---
```

- `NN` = zero-padded chapter number (e.g. `01`, `02`, `10`)
- `N` = plain chapter number for the enumerator (e.g. `1`, `2`, `10`)
- The `title` field drives the left-hand nav label
- The `enumerator` drives equation/figure/section numbering (e.g. `(2.4)`, `Fig. 2.1`)

### 4.3 Chapter Number Registry

Update this table each time a new chapter is converted:

| # | File | Nav Title |
|---|------|-----------|
| 1 | `foundations_what_is_the_meaning_of_this` | 01 - Introduction |
| 2 | `foundations_numbers_a_gentle_introduction` | 02 - Numbers - A Gentle Introduction |

**Renumbering:** If a chapter is split, only the `enumerator` and `title` fields in the
affected frontmatter need updating. Prose and cross-reference labels never change.

### 4.4 Figure Handling

All figures referenced in `.md` files must be in the `figures/` subfolder.

**Decision rule for each figure:**
- File exists in `figures/` → reference the `.png` version in the `.md`
- File does not exist yet → create a placeholder PDF (see template below), put it in `figures/`, and reference the `.png` version — the publish script will auto-convert it

**MyST figure directive:**
```markdown
:::{figure} figures/filename.png
:alt: Brief description
Caption text here (if any).
:::
```

**Always reference `.png`, never `.pdf`** — browsers cannot render PDFs inline.
The publish script auto-converts every PDF in `figures/` to PNG using ghostscript (`gs`)
before syncing to the git repo. The PNG is generated only if it is missing or older than
the PDF, so re-running publish.sh is efficient.

**Placeholder figures:** Use `figure_standalone_template.tex` to create a TikZ placeholder
PDF showing the filename. Compile in TeXShop, save as `figurename.pdf` in `figures/`.
The publish script will auto-convert it to PNG.

```latex
\documentclass{standalone}
\usepackage{tikz}
\usepackage[T1]{fontenc}
\begin{document}
\begin{tikzpicture}
  \draw[thick, dashed, gray!50] (0,0) rectangle (8,5);
  \fill[gray!15] (0,4.2) rectangle (8,5);
  \node[font=\small\bfseries\sffamily, text=gray!60] at (4,4.6)
    {FIGURE PLACEHOLDER};
  \node[font=\normalsize\ttfamily, text=gray!70, align=center] at (4,2.3)
    {\detokenize{figurename.pdf}};
  \node[font=\small\sffamily\itshape, text=gray!50] at (4,1.4)
    {Replace with standalone TikZ figure};
\end{tikzpicture}
\end{document}
```

### 4.5 Numbered Equations

Labeled equations in LaTeX become labeled MyST math blocks:

```markdown
$$
E = mc^2
$$ (eq:einstein)
```

Cross-references use `{eq}`eq:label`` — MyST auto-prefixes "Eq." so never write "Eq." before
the reference in prose.

### 4.6 MyST Annotations in .tex Files

For constructs that need special handling, add annotations directly in the `.tex` file
in Overleaf. Format:

```latex
%
% MyST:
% <instruction>
% <optional comment>
%
```

Examples:
```latex
%
% MyST:
% skip
% \pagebreak has no web equivalent
%
\pagebreak
```

```latex
%
% MyST:
% placeholder — heirarchy_of_numbers_1.pdf (TikZ standalone to be created)
% Large inline TikZ showing number set hierarchy; no standalone PDF yet
%
\begin{figure}[htbp]
```

---

## 5. Publishing Process

### 5.1 The Publish Script

Run from Terminal:
```bash
bash ~/.claude/skills/math-book-myst-migration/scripts/publish.sh
```

Or to publish a specific chapter only:
```bash
bash ~/.claude/skills/math-book-myst-migration/scripts/publish.sh foundations_numbers_a_gentle_introduction
```

**What the script does:**
1. Pulls the latest from GitHub (`git pull --rebase`)
2. Copies `myst.yml` and `index.md` from Dropbox to the git repo
3. Copies all `.md` chapter files (or specified chapters) from Dropbox to the git repo
4. Auto-converts any new/updated PDFs in `figures/` to PNG using ghostscript at 200dpi
5. Rsyncs `figures/` from Dropbox to the git repo (`rsync -a --delete`)
6. Rsyncs `document_images/` from Dropbox to the git repo
7. Commits and pushes only if there are actual changes

Note: `custom.css` is **not** managed by publish.sh — it lives directly in the git repo
and must be edited and pushed manually from `~/Dropbox/all-math-all-the-time-git/`.

### 5.2 GitHub Actions

After every push, GitHub Actions automatically builds the MyST site and deploys it
to GitHub Pages. The live site updates in approximately 1 minute.

### 5.3 myst.yml Structure

```yaml
version: 1
project:
  title: All Math All The Time
  authors:
    - name: Gaurav Khanna, Ph.D.
  numbering:
    headings: true
    equations: true
    figures: true
    tables: true
  toc:
    - file: index
    - title: Foundations
      children:
        - file: foundations_what_is_the_meaning_of_this
        - file: foundations_numbers_a_gentle_introduction
        # Add each file here after its .md conversion is complete

site:
  template: book-theme
  options:
    style: custom.css
    nav_title: "Gaurav Khanna, Ph.D."
    logo: "Gaurav Khanna - WSJ Style Image.jpg"
```

**When a new chapter is converted**, uncomment its entry in the TOC.

---

## 6. Custom CSS

`custom.css` lives directly in the git repo (not managed by publish.sh).
Edit it by modifying `~/Dropbox/all-math-all-the-time-git/custom.css` and pushing manually:

```bash
cd ~/Dropbox/all-math-all-the-time-git
git add custom.css
git commit -m "Update custom CSS"
git push
```

Current CSS sets:
- Font: Latin Modern Roman (matching the LaTeX book)
- Font size: 18px body text

---

## 7. Known Issues / Future Work

| Issue | Status | Notes |
|-------|--------|-------|
| "Made with MyST" header | Open | Appears in top bar; `nav_title` doesn't override it |
| Extra section spacing (CSS) | Open | CSS rule added but book-theme specificity wins |
| Section numbers in right-side TOC | Accepted | Book-theme strips numbers from on-page TOC |
| Figures using Option 2 (SVG from lualatex+dvisvgm) | Future | Better quality than PDF→PNG conversion |
| `document_images/` has loose files at root | Future | Migrate remaining root-level assets gradually |

---

## 8. Workflow Quick Reference

**Starting a new chapter conversion:**
1. Edit/finalize `.tex` in Overleaf → wait for Dropbox sync
2. Move chapter's figure files into `figures/`
3. Create placeholder PDFs for any figures not yet completed
4. Ask Claude to convert the chapter (subagent handles the conversion)
5. Review the `.md` output
6. Add `enumerator` and numbered title to frontmatter
7. Add chapter to `myst.yml` TOC
8. Run `publish.sh`
9. Check live site for rendering issues

**Updating an existing chapter:**
1. Make edits in Overleaf → Dropbox syncs
2. Ask Claude to apply the delta to the `.md` (not a full reconversion)
3. Run `publish.sh`

**Adding a new figure to an existing chapter:**
1. Compile TikZ standalone in TeXShop → PDF lands in `figures/`
2. Update the `.md` to reference `figures/filename.png`
3. Run `publish.sh` (auto-converts PDF→PNG and syncs)
