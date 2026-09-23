# 0002. Compact 680px Column, 14.5px (+20%) Typography Scale, Zero-Scroll Footer, and Page-Jump Locks over Quarto Defaults

Quarto's default Bootstrap styling and runtime scripts introduce several layout behaviors that conflict with our minimalist, stable single-column design: `$font-size-base: 1.1rem` (`~17.6px`), a navbar stretched across `100vw` that collapses into a hamburger menu below `992px`, dynamic runtime script shifts where `quarto-nav.js` recalculates `body.style.paddingTop` ~250ms after page load, and an inline `min-height: calc(100vh - ...)` calculation on `#quarto-content` that pushes footers off-screen and forces unnecessary vertical scrolling on short pages. Additionally, switching between short pages and longer pages (such as `Personal`) toggles vertical scrollbars, inducing horizontal layout jumps.

We decided to enforce:
1. A centered `680px` layout column across the navbar, main content, and footer (`.navbar-container`, `#quarto-content`, `.nav-footer`).
2. An always-inline, single-line non-collapsing navbar (`collapse: false` and flex overrides) locked at an exact `50px` height.
3. A calibrated `14.5px` (`0.9rem`) (+20%) typography scale (`$font-size-base: 0.9rem`, `body { font-size: 14.5px; line-height: 1.55; }`) with a proportional `215px` left profile column on the homepage.
4. Neutralization of Quarto's `100vh + margin` scroll bug by overriding `#quarto-content` to `min-height: 0 !important; height: auto !important;` with compact footer spacing (`margin-top: 1.75rem !important; padding-top: 1.15rem !important;`), ensuring the footer is visible without scrolling on standard desktop viewports.
5. Strict CSS layout locks to prevent horizontal and vertical page-switch jumps: `html { scrollbar-gutter: stable; overflow-y: scroll; }` to preserve horizontal alignment across all pages, and fixed `50px` header height / `body { padding-top: 50px !important; }` so Quarto's delayed padding adjustment cannot shift content vertically.
