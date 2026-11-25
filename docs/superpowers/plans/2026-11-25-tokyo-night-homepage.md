# Tokyo Night Homepage Implementation Plan

> **For agentic workers:** REQUIRED SUB-SKILL: Use superpowers:subagent-driven-development (recommended) or superpowers:executing-plans to implement this plan task-by-task. Steps use checkbox (`- [ ]`) syntax for tracking.

**Goal:** Rebuild the homepage around a Tokyo Night-inspired profile, research visualizer placeholder, GraphBind highlight, and thesis placeholder while keeping the static site coherent.

**Architecture:** Update the existing static homepage and shared style sheet, add one local GraphBind image, and align the projects page with the same single-project focus. Keep the visualizer as semantic HTML/CSS so a future tool can replace it without changing the page architecture.

**Tech Stack:** HTML5, CSS custom properties, vanilla JavaScript, Docker Compose/Nginx preview, GitHub Pages.

**Spec:** `docs/superpowers/specs/2026-11-25-tokyo-night-homepage-design.md`

## Global Constraints

- The site remains dependency-free static HTML, CSS, and JavaScript.
- Existing responsive and accessible patterns must be preserved.
- Theme choice remains persisted in local storage.
- The visualizer and thesis are explicitly labeled as work in progress.
- GraphBind appears without an "UwU" suffix.
- Preview validation must use Docker Compose and `http://localhost:8000`.

## Review Focus

- Narrow mobile widths: hero, graph, and project panels must stack without horizontal overflow.
- Dark/light mode: all text, borders, images, and controls must remain legible in both themes.
- Asset availability: the GraphBind architecture image must load from the local site path.
- Link clarity: repository, PDF, and social destinations must identify where they lead.
- Placeholder honesty: visualizer and thesis copy must not imply finished functionality.

---

### Task 1: Add GraphBind Asset and Homepage Structure

**Files:**
- Create: `assets/graphbind-architecture.png`
- Modify: `index.html`
- Test: Docker-served homepage and asset URL

**Interfaces:**
- Consumes: GraphBind repository architecture image and the existing header/footer conventions.
- Produces: stable `#research`, `#projects`, and `#publications` sections; a local asset path reused by Task 2.

- [ ] **Step 1: Add a content assertion script for the requested sections**

  Check with `grep` that `index.html` includes `id="research"`, `id="projects"`, and `id="publications"`, the local GraphBind image path, and no visible "UwU" copy. Confirm this check fails before editing.

- [ ] **Step 2: Download GraphBind's `images/Architecture.png` as the local image asset**

  Preserve the source image unchanged at `assets/graphbind-architecture.png`.

- [ ] **Step 3: Rework the homepage content**

  Replace the current oversized hero and three-card project grid with the compact profile/social layout, right-side visualizer placeholder, one GraphBind project highlight, and Publications & Thesis placeholder. Keep links to GitHub, LinkedIn, email, CV, GraphBind repository, and GraphBind PDF.

- [ ] **Step 4: Run the homepage content assertions**

  Run the same `grep` assertions and verify that all required section IDs and links are present and `UwU` is absent from user-visible homepage copy.

### Task 2: Apply Tokyo Night Responsive Styling

**Files:**
- Modify: `assets/styles.css`
- Modify: `projects.html`

**Interfaces:**
- Consumes: section and class names produced by Task 1.
- Produces: a shared responsive visual system for the homepage and project page.

- [ ] **Step 1: Define failing visual checks**

  Start the Docker preview after Task 1 and confirm the new classes are still unstyled and the page renders without request failures. Record that baseline before adding their CSS.

- [ ] **Step 2: Replace the shared color tokens**

  Set light and dark custom properties to accessible Tokyo Night-inspired palettes. Preserve the existing persisted theme toggle behavior in `assets/site.js`.

- [ ] **Step 3: Style the new homepage components**

  Add focused styles for the compact identity block, social pills, visualizer canvas, graph nodes and labels, featured GraphBind media, status badges, and thesis/publication entry. Add `800px` and `580px` responsive rules.

- [ ] **Step 4: Align the projects page**

  Replace the existing multi-project list with one GraphBind entry so the site no longer presents unrelated or older work as the selected focus.

- [ ] **Step 5: Verify local preview responses**

  Run `docker compose up -d --wait`, then `curl --fail --silent` against `/`, `/projects.html`, `/assets/styles.css`, and `/assets/graphbind-architecture.png`. Verify all return HTTP success.

### Task 3: Accessibility and Completion Review

**Files:**
- Test: `index.html`
- Test: `projects.html`
- Test: `assets/styles.css`

**Interfaces:**
- Consumes: completed homepage and shared styles.
- Produces: a verified, responsive static change ready for handoff.

- [ ] **Step 1: Validate page semantics**

  Check that every image has useful `alt` text, heading order is coherent, the visualizer placeholder has an accessible label, and external PDF/repository links state their destination where useful.

- [ ] **Step 2: Validate both themes**

  Confirm `assets/site.js` still initializes from saved/system theme and that the light/dark Tokyo Night token pairs provide readable foreground/background contrast.

- [ ] **Step 3: Inspect the final diff**

  Run `git diff --stat`, `git diff --check`, and review `index.html`, `projects.html`, and `assets/styles.css` for unrelated changes, missing responsive rules, and accidental "UwU" copy.

- [ ] **Step 4: Stop preview and report result**

  Run `docker compose down` after verification and report the implemented sections plus the local preview URL sequence for future use.
