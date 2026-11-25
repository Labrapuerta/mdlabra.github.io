# Tokyo Night Homepage Design

## Intent

Turn the current portfolio front page into a compact academic/research homepage that quickly introduces Manuel, exposes his social profiles, previews current research tooling, and highlights GraphBind.

## Goals

- Use a Tokyo Night-inspired palette for the dark theme and a softer companion light theme.
- Keep the existing static HTML/CSS/JavaScript architecture and shared navigation.
- Show a small portrait, short bio, and direct social links in the hero.
- Reserve the right side of the hero for a clearly labeled visualizer placeholder.
- Replace the homepage project selection with one highlighted GraphBind project, without using the "UwU" suffix.
- Add a Publications & Thesis section with a placeholder for the GraphRAG diffusion retrieval thesis on biomedical knowledge graphs.
- Reuse GraphBind's architecture image and link its report.

## Non-goals and anti-goals

- Do not rebuild this as a JavaScript framework.
- Do not copy unrelated personal content, scripts, or branding from the reference repository.
- Do not pretend the visualizer or thesis is complete; both must be clearly marked as work in progress.
- Do not include the other current homepage projects in this first focused version.

## Constraints

- The site remains dependency-free static HTML, CSS, and JavaScript.
- Existing responsive and accessible patterns must be preserved.
- Theme choice remains persisted in local storage.
- Preview validation must use Docker Compose and `http://localhost:8000`.

## Approach

Extend the existing shared components and retheme the full site rather than styling one page in isolation. The alternative of changing only the homepage would create inconsistent navigation and shared-page styling, while copying the reference site wholesale would introduce unrelated implementation details.

Use the GraphBind architecture PNG as a local asset so the project highlight does not depend on a hotlinked image. Keep the hero visualizer as semantic HTML and CSS for now; its interactive implementation can replace the same region later.

## CV decision

Publish the generated PDF as the primary visitor-facing CV. Keep the LaTeX source in a separate versioned `cv/` source area if Manuel wants reproducible edits, but do not ask visitors to use or download the source instead of the PDF.
