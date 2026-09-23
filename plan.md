# Website Redesign Plan (`gchure.bio` × `brianhie.com`)

*Reference: [GitHub Issue #1](https://github.com/igorsdub/igorsdub.github.io/issues/1)*

## Vision & Architecture

Transform the personal academic website of **Igors Dubanevics** into a clean, minimalist, human-centered portfolio inspired by:
- **[Griffin Chure (`gchure.bio`)](https://gchure.bio/)**: Centered narrow column (`max-width: 740px`), crisp monochrome typography (`Geist` / `Geist Mono`), left profile column with photo, circular social links, and experience list, paired with an evocative 4-photo snapshot strip.
- **[Brian Hie (`brianhie.com/bookshelf`)](https://brianhie.com/bookshelf)**: Stripped-down aesthetic shelves displaying personal culture (books, music, movies) using a clean 4-column hairline grid.
- **[Dr. Gang He's Quarto Academic Template](https://github.com/drganghe/quarto-academic-website-template)**: Solid academic foundation with structured listings, publications, and teaching entries.

---

## Roadmap & Milestones

- [x] **Phase 1: Implementation Planning & Issue #1 Specification**
  - Establish design requirements: 740px container, Geist typography, clean navigation, profile column, and multi-media shelf.
- [ ] **Phase 2: Configuration & Workflow Updates**
  - Update `_quarto.yml`: remove duplicate brand title, streamline navbar right to GitHub source repository, add `Beyond Lab` nav item, update footer attribution and HTML theme (`cosmo` + `custom.scss`).
  - Update `.github/workflows/publish.yml`: set `tinytex: false` for ultra-fast GitHub Pages deployments.
- [ ] **Phase 3: Minimalist Styling System (`custom.scss` & `styles.css`)**
  - Define SCSS defaults: Geist + Geist Mono font imports, typography variables, monochrome color palette.
  - Constrain `.navbar-container`, `#quarto-content`, and `.nav-footer` to `max-width: 740px`.
  - Implement `.about-grid`, `.profile-section`, `.social-button`, and `.experience-section` styles.
  - Implement `.snapshot-strip` 4-image grid below the homepage bio.
  - Implement `.shelf-grid`, `.shelf-cell`, and `.shelf-cover-wrap` with aspect ratios (`2:3` for books/movies, `1:1` for music).
  - Scope title block suppression so only `index.qmd` hides the header block while subpages display clean page titles.
- [ ] **Phase 4: Homepage Profile & Snapshot Redesign (`index.qmd`)**
  - Replace Trestles about layout with custom two-column `.about-grid`.
  - Left column: Portrait image, circular social icons (GitHub, Google Scholar, ORCID, LinkedIn), and education/experience timeline.
  - Right column: Bio narrative detailing research in molecular evolution, fitness landscapes, and scientific computing.
  - Bottom: Responsive 4-photo snapshot strip.
- [ ] **Phase 5: Beyond Lab Media Shelves (`beyond-lab.qmd`)**
  - Custom EJS listing template (`files/includes/shelf.ejs`).
  - Local artwork covers in `files/images/shelf/` to guarantee zero broken external links.
  - Structured YAML data files: `data/books.yml`, `data/music.yml`, and `data/movies.yml`.
  - Curated initial items across literature, science, cinema, and music.
- [ ] **Phase 6: Verification & Polish**
  - Render full site with `quarto render` and verify build status.
  - Inspect responsiveness and layout integrity.
