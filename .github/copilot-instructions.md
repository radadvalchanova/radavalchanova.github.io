# Copilot / AI Agent Instructions

Purpose
- This is a small static portfolio site (user-page repo). Aim: edit `index.html` and `assets/*` only.

Big picture
- Single-page static site: content, styles and behaviour live in `index.html`.
- `assets/` holds images and other static resources (e.g. expected headshot: `assets/portfolio-headshot.jpg`).
- No build tooling, bundlers, or server code present — changes are deployed as static files (GitHub Pages style).

Key files
- `index.html` — single source of truth. Contains inline CSS, HTML structure (sidebar, projects grid) and the small JS filter at the bottom.
- `assets/` — images and other static assets.

Project-specific patterns and conventions
- Avatar: the markup uses an `.avatar-wrapper` and expects an image at `assets/portfolio-headshot.jpg`; keep filename & path consistent.
- Project items: add projects by duplicating a `.project-item` block inside the `.w3-row-padding` sections. Use `data-tags` (comma-separated, lowercase) on the `.project-item` element to enable the JS filter.
  - Example: `<div class="w3-third w3-margin-bottom project-item" data-tags="python,mysql">` will show when filter `python` or `mysql` is active.
- Filters: filter buttons use `data-filter` attributes; values are compared to `data-tags` split by commas. `all` shows everything.
- Styling: CSS is inline in `index.html` and uses a `:root` CSS variable `--sidebar-w`. Prefer editing the inline styles for small tweaks rather than extracting to external CSS unless you add a build system.
- Responsive behavior: two breakpoints are present (900px and 600px); keep changes consistent with those rules.

Local workflows (what to do locally)
- Preview: open `index.html` in a browser (double-click or use an editor Live Preview). Use browser DevTools to debug layout, console, and network issues.
- Add a new project: duplicate an existing `.project-item`, update `data-tags`, `project-title`, `project-desc`, and tags in `.tag-row`. The JS filter will automatically pick it up.

Deployment hints
- Repository name (radavalchanova.github.io) implies GitHub Pages deployment from the repository root. Push to `main` (or whatever default branch) to update the live site.

Searchable patterns for quick edits
- Find the small JS filter: search for `document.querySelectorAll(".filter-btn")` in `index.html`.
- Find how tags are parsed: `item.getAttribute("data-tags").toLowerCase().split(",")`.

What not to assume
- There are no server APIs, tests, or CI files in this repo — do not add runtime server code unless converting this repo to a more complex site.

When in doubt, follow these quick checks
- If layout breaks after edits: check inline CSS at the top of `index.html` and responsive `@media` blocks.
- If a new project doesn't show under a filter: confirm `data-tags` contains the filter value (lowercase, comma-separated, no extra characters).

Contact
- Ask the repo owner to confirm preferred branch for Pages (if not `main`) and naming for the avatar file when proposing changes.

End.
