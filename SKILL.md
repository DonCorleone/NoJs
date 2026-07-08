---
name: css-nojs-patterns
description: >
  USE THIS SKILL whenever a task involves building UI without JavaScript,
  progressive enhancement, CSP-locked or no-JS environments (email clients,
  AMP, locked-down CMSs, security-sensitive apps), or whenever the user asks
  "can this be done without JavaScript?" / "is there a pure CSS way to do
  this?". This is a curated collection of 23 standalone, dependency-free
  HTML+CSS reference implementations covering modern CSS features such as
  @property, :has(), :where()/:is(), if()/style() conditionals, popover,
  <dialog command="">, scroll-driven animations (animation-timeline: scroll()),
  container queries, corner-shape, and more. ALWAYS consult this skill before
  reaching for JavaScript to implement carousels, countdowns, modals,
  drawers/popovers, form validation, back-to-top buttons, resizable panels,
  scroll progress bars, external-link icons, gradient borders, auto-contrast
  text, or similar interactive/visual UI patterns — there is a good chance a
  pure CSS solution already exists in patterns/.
---

# CSS NoJS Patterns

A collection of 23 standalone HTML files, each demonstrating one interactive
or visual UI pattern implemented with **CSS only — zero JavaScript**.

## How to use

1. **Consult the index** — scan the "Pattern Index" table below to find a
   pattern matching what you need (by name, behavior, or technique).
2. **Read the file** — open the matching file under `patterns/` directly;
   each is fully standalone (inline `<style>`, no build step, no dependencies).
3. **Grep by technique** — every pattern file embeds machine-readable
   `<meta name="pattern:*">` tags, so you can search across all patterns by
   the CSS feature you're after, e.g.:

   ```sh
   grep -l 'scroll-timeline' patterns/*.html
   grep -l 'pattern:css-features.*at-property' patterns/*.html
   grep -rl 'popover' patterns/*.html
   ```

## Conventions

- Each file in `patterns/` is **standalone**: a single `.html` file with an
  inline `<style>` block. No external JS, no build tools, no npm packages.
- **No `<script>` tags anywhere.** If a pattern needs interactivity, it uses
  native HTML/CSS mechanisms only (`:checked`, `:focus`, `:has()`, `popover`,
  `<dialog command="">`, anchor links, `:target`, etc.).
- Every pattern file has exactly 4 meta tags right after `<title>`:

  | Meta tag | Content |
  |---|---|
  | `pattern:name` | filename without `.html`, matches the "File" column below |
  | `pattern:shows` | one sentence describing the user-visible behavior |
  | `pattern:techniques` | comma-separated core CSS techniques used |
  | `pattern:css-features` | comma-separated caniuse-style feature IDs |

- `index.html` (repo root) is a human-facing tile overview linking to all
  patterns — it is not itself a pattern.

## Pattern Index

| Pattern | File | What it shows | Key techniques |
|---|---|---|---|
| Back to Top | `back-to-top-scroll-behavior.html` | A 'back to top' link that smoothly scrolls to the top of the page using only an anchor and native smooth scrolling. | anchor link to #id, scroll-behavior: smooth |
| Autoplay Carousel | `carousel-css-animation.html` | An infinite auto-scrolling logo carousel that fades at the edges and pauses on hover or keyboard focus. | staggered animation-delay, mask-image, :has(:focus) |
| clamp() | `fluid-sizing-clamp.html` | Font size, padding, gap, and width values that fluidly scale between a minimum and maximum as the viewport resizes. | clamp(min, preferred, max), vw-based preferred value |
| Corner Shape | `corner-shape-property.html` | Card corners rendered as round, scoop, bevel, or rectangular shapes, with smooth transitions between them on hover. | corner-shape property, transition: corner-shape |
| CSS Columns | `multi-column-layout.html` | A newspaper-style multi-column article that automatically balances column heights and reflows on resize. | column-count, column-fill: balance, column-gap |
| CSS Countdown | `countdown-property-counter.html` | A large countdown number animating from 10 to 0 using CSS counters driven by an animated custom property. | @property, counter-reset with var(), content: counter() |
| CSS if() | `conditional-styling-if-function.html` | A notice box whose background color changes based on a data-status HTML attribute, using native CSS conditional logic. | if(style(): …; else: …), attr() |
| CSS Units | `typography-units-ch-lh-cap-cqi.html` | Five demos of lesser-known CSS units — ch, lh, cap, cqi, vmin/vmax — for readable line lengths, vertical rhythm, icon sizing, and container-based type scaling. | ch/lh/cap, cqi container units, vmin/vmax |
| External Link Icon | `external-link-icon-attribute-selector.html` | External links automatically get a small arrow icon appended, while internal links stay untouched. | attribute selector + :not(), ::after, inline SVG data URI |
| Form Validation | `form-validation-pseudo-classes.html` | Form inputs turn green or red in real time as the user types, using only native HTML validation and CSS pseudo-classes. | :not(:placeholder-shown):invalid, :user-valid/:user-invalid |
| Gradient Border | `gradient-border-at-property.html` | Cards and a button with animated rainbow gradient borders that rotate continuously or on hover. | padding-box/border-box layering, @property for angle |
| Auto-contrast Text | `auto-contrast-text-mix-blend-mode.html` | Text that automatically stays readable against any background — gradient, image, or checkerboard — by inverting its color. | mix-blend-mode: difference |
| Named Grid Lines | `grid-layout-named-lines.html` | A sidebar/header/content/footer layout where grid items are placed using named grid lines instead of numeric indexes. | named grid lines, grid-column/row by name |
| Popover API | `popover-api-toggle.html` | A slide-in navigation drawer opened and closed with the native Popover API and animated purely with CSS. | popover, popovertarget(action), :popover-open, ::backdrop |
| Resizable Elements | `resizable-element-resize-property.html` | Plain div boxes that users can drag-resize in both, horizontal, or vertical directions, just like a textarea. | resize: both\|horizontal\|vertical, overflow: auto |
| Safe Area Insets | `safe-area-insets-env.html` | Page content and a bottom nav bar that automatically avoid device notches, rounded corners, and gesture bars. | env(safe-area-inset-*), viewport-fit=cover, max() |
| Scroll Progress Bar | `scroll-progress-animation-timeline.html` | A fixed progress bar at the top of the page that fills up as the user scrolls, driven entirely by CSS. | animation-timeline: scroll(), scaleX() keyframes |
| Show Modal | `modal-dialog-command-api.html` | A native dialog opened and closed with the new declarative command/commandfor button attributes. | command=show-modal, commandfor, command=close |
| SVG Draw Animation | `svg-path-draw-animation.html` | SVG shapes (circle, zigzag, square) that appear to draw themselves on load and replay on hover. | pathLength normalization, stroke-dasharray/dashoffset |
| Tabular Nums | `tabular-numbers-font-variant.html` | A column of financial figures that aligns perfectly digit-by-digit using tabular figure widths. | font-variant-numeric: tabular-nums, font-feature-settings |
| Turn Unit | `rotation-turn-unit.html` | Arrows and icons rotated by fixed amounts or animated in full spins using the turn angle unit instead of degrees. | rotate: Nturn, @keyframes with turn values |
| Viewport Units | `viewport-units-dvh-svh-lvh.html` | Four full-height sections that reveal how vh, svh, lvh, and dvh differ when the mobile browser toolbar shows or hides. | 100vh vs 100svh vs 100lvh vs 100dvh |
| :where() Selector | `zero-specificity-where-selector.html` | Two identical navigation menus showing how :where() lets you group selectors without adding any specificity, unlike :is(). | :where() zero-specificity grouping vs :is() |
