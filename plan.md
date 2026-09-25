# Website Redesign Plan (`gchure.bio` × `brianhie.com`)

*References: [GitHub Issue #1](https://github.com/igorsdub/igorsdub.github.io/issues/1), [GitHub Issue #2](https://github.com/igorsdub/igorsdub.github.io/issues/2), [GitHub Issue #3](https://github.com/igorsdub/igorsdub.github.io/issues/3)*

## Vision & Architecture

Transform the personal academic website of **Igors Dubanevics** into a clean, minimalist, human-centered portfolio inspired by:
- **[Griffin Chure (`gchure.bio`)](https://gchure.bio/)**: Centered narrow column (`max-width: 580px`), crisp monochrome typography (`Geist` / `Geist Mono` at `12px` ultra-compact scale), and a `180px` left profile column with photo, circular social links, and experience list.
- **[Brian Hie (`brianhie.com/bookshelf`)](https://brianhie.com/bookshelf)**: Stripped-down aesthetic shelves displaying personal culture (books, music, movies) using a clean 4-column hairline grid.
- **[Dr. Gang He's Quarto Academic Template](https://github.com/drganghe/quarto-academic-website-template)**: Solid academic foundation with structured listings, publications, and teaching entries.

---

## Roadmap & Milestones

- [x] **Phase 1: Implementation Planning & Issue #1 Specification**
  - Establish design requirements: 740px container, Geist typography, clean navigation, profile column, and multi-media shelf.
- [x] **Phase 2: Configuration & Workflow Updates**
  - Update `_quarto.yml`: remove duplicate brand title, streamline navbar right to GitHub source repository, add `Beyond Lab` nav item, update footer attribution and HTML theme (`cosmo` + `custom.scss`).
  - Update `.github/workflows/publish.yml`: set `tinytex: false` for ultra-fast GitHub Pages deployments.
- [x] **Phase 3: Minimalist Styling System (`custom.scss` & `styles.css`)**
  - Define SCSS defaults: Geist + Geist Mono font imports, typography variables, monochrome color palette.
  - Constrain `.navbar-container`, `#quarto-content`, and `.nav-footer` to `max-width: 740px`.
  - Implement `.about-grid`, `.profile-section`, `.social-button`, and `.experience-section` styles.
  - Implement `.snapshot-strip` 4-image grid below the homepage bio.
  - Implement `.shelf-grid`, `.shelf-cell`, and `.shelf-cover-wrap` with aspect ratios (`2:3` for books/movies, `1:1` for music).
  - Scope title block suppression so only `index.qmd` hides the header block while subpages display clean page titles.
- [x] **Phase 4: Homepage Profile & Snapshot Redesign (`index.qmd`)**
  - Replace Trestles about layout with custom two-column `.about-grid`.
  - Left column: Portrait image, circular social icons (GitHub, Google Scholar, ORCID, LinkedIn), and education/experience timeline.
  - Right column: Bio narrative detailing research in molecular evolution, fitness landscapes, and scientific computing.
  - Bottom: Responsive 4-photo snapshot strip.
- [x] **Phase 5: Beyond Lab Media Shelves (`beyond-lab.qmd`)**
  - Custom EJS listing template (`files/includes/shelf.ejs`).
  - Local artwork covers in `files/images/shelf/` to guarantee zero broken external links.
  - Structured YAML data files: `data/books.yml`, `data/music.yml`, and `data/movies.yml`.
  - Curated initial items across literature, science, cinema, and music.
- [x] **Phase 6: Verification & Polish**
  - Render full site with `quarto render` and verify build status.
  - Inspect responsiveness and layout integrity.
- [x] **Phase 7: Layout & Navbar Refinements (Issue #2)**
  - Rename `beyond-lab.qmd` to `personal.qmd` and update navigation and page titles.
  - Fix homepage HTML rendering by wrapping `index.qmd` markup inside a raw `{=html}` block and removing `page-layout: full`, eliminating rogue `<pre><code>` code wrappers around `.social-links`, `.experience-section`, and `.snapshot-strip`.
  - Right-align navbar links (`Research`, `Teaching`, `Blog`, `Personal`), disable search bar (`search: false`), and implement an ultra-minimal single-line centered footer with project source link.
  - Align typography and container scale to `gchure.bio`: base font size 15px (`$font-size-base: 0.9375rem;`), container width constrained to 680px, monospace uppercase navbar and headings, justified bio text, and compact experience items.
  - Verify complete site build via `quarto render`.
- [x] **Phase 8: Ultra-Compact 580px Scale, Always-Inline Navbar & Page-Jump Locks (Issue #3)**
  - Constrain `.navbar-container`, `#quarto-content`, and `.nav-footer` (including navbar and footer hairlines) to `max-width: 580px`.
  - Reduce site prose to `12px` (`0.75rem`), left `Profile Column` to `180px` (`28px` social buttons), and replace Quarto's default Research listing with a compact single-column EJS template (`files/includes/publications.ejs`).
  - Disable navbar collapsing (`collapse: false` in `_quarto.yml` + flex overrides in `custom.scss`) so `Igors Dubanevics` stays flush-left and `Research · Teaching · Blog · Personal` stay flush-right on a single line at all screen sizes with zero dropdowns.
  - Remove `Snapshot Strip` from `index.qmd`, `custom.scss`, and `CONTEXT.md`.
  - Eliminate horizontal/vertical page-switch jumps (`scrollbar-gutter: stable; overflow-y: scroll` + fixed `46px` header/body offset) and neutralize `quarto-nav.js`'s `100vh` inline `min-height` so the footer is visible without scrolling.

