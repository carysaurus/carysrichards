# Portfolio Site — Skills & Techniques Reference
*Created by Carys Richards · © 2026*

---

## Languages & Technologies

- **HTML5** — semantic page structure, accessible markup, single-page anchor navigation
- **CSS3** — modular stylesheet architecture, animations, responsive layout, modern CSS APIs
- **Git & GitHub** — version control throughout the project lifecycle

---

## HTML Skills

### Document Structure & Semantics
- **Semantic HTML5 elements** — used `<header>`, `<nav>`, `<main>`, `<section>`, and `<footer>` to convey document structure meaningfully to browsers and screen readers
- **SEO & metadata** — included `<meta name="Description">`, `charset`, and `viewport` tags in `<head>` for search discoverability and correct mobile rendering
- **Custom favicon** — linked a custom `.png` icon via `<link rel="icon">` for branding in browser tabs

### Navigation & Interactivity (No JavaScript)
- **Anchor-based single-page navigation** — all nav links use `href="#section-id"` hash anchors to scroll between sections without any page reloads or JavaScript
- **`<details>/<summary>` mobile nav accordion** — implemented a collapsible mobile navigation menu entirely in HTML using the native `<details>` element, requiring zero JavaScript for open/close toggling
- **Dual nav pattern** — built two separate nav structures (`.nav-desktop` and `.nav-mobile`) and toggled between them with CSS media queries, keeping the HTML clean and accessible

### Content & Accessibility
- **Descriptive `alt` text on all images** — every `<img>` includes a meaningful `alt` attribute for screen reader users and image load failures
- **`target="_blank"` on external links** — all project and live demo links open in a new tab, keeping the portfolio itself in context
- **`mailto:` contact link** — contact CTA uses a `mailto:` href to open the user's email client directly, avoiding the need for a backend form

---

## CSS Skills

### Architecture & Organization
- **Modular CSS file structure** — split stylesheets across 11 purpose-built files (`reset.css`, `variables.css`, `base.css`, `typography.css`, `animations.css`, `buttons.css`, and five section-specific files) all assembled via `@import` in a single `main.css` entry point
- **CSS custom properties (variables)** — defined a full design token system in `variables.css` using `:root` CSS variables for the colour palette (`--pink-l`, `--pink-d`, `--blue-d`, etc.), making global theming changes a single-file edit
- **Meyer Web CSS reset** — applied Eric Meyer's CSS reset as a baseline to normalize default browser styles before applying custom rules

### Layout
- **CSS Grid with `repeat()` and `span`** — built the skills section as a `repeat(3, 1fr)` grid, with the "Credited Projects" card spanning two columns using `grid-column: span 2` for visual emphasis
- **Flexbox throughout** — used flexbox for all major layout components: nav header, about section side-by-side layout, project cards (image + info columns), project button rows, and the footer copyright bar
- **`clamp()` for fluid sizing** — applied `clamp()` on widths, font sizes, padding, and gaps throughout to create fluid values that scale smoothly between minimum and maximum sizes without breakpoints

### Responsiveness
- **Four responsive breakpoints** — implemented dedicated `@media` queries at `600px`, `768px`, `800px`, and `900px` to progressively adapt the layout from three-column grids down to single-column stacks
- **Mobile-first nav switch** — used `display: none` / `display: flex` toggling at the `768px` breakpoint to swap the desktop horizontal nav for the `<details>`-based mobile accordion
- **Responsive image containers** — project image galleries use `clamp()` widths with `flex-shrink: 0` to prevent images from collapsing on narrow screens

### Animation & Motion
- **Eight custom `@keyframes` animations** — defined named animations (`fadeUp`, `fadeRight`, `fadeLeft`, `skillFadeUp`, `projectFadeRight`, `projectFadeLeft`, `lineFadeLeft`, `rotateBorder`, `textcol`) in a dedicated `animations.css` file
- **CSS Scroll-Driven Animations (`animation-timeline: view()`)** — used the modern Scroll-Driven Animations API to trigger entrance animations on the projects and skills sections as they enter the viewport, with `animation-range` to fine-tune the entry start and end points — no JavaScript IntersectionObserver required
- **Staggered `animation-delay` for entrance sequencing** — applied incremental `animation-delay` values (`0.2s`, `0.4s`, `0.6s`, `0.8s`) on the About section paragraphs so they fade in one after another, creating a polished reveal effect
- **Animated gradient text** — applied `background-clip: text` with `-webkit-background-clip: text` and `color: transparent` to the intro subtitle, then animated `background-position` via the `textcol` keyframe to create a continuously cycling gradient colour effect
- **`opacity: 0` + `forwards` fill mode** — elements start invisible and use `animation-fill-mode: forwards` so they remain in their final visible state after the animation completes, enabling clean scroll-triggered entrance effects

### Visual Effects & Decoration
- **Rotating conic-gradient border** — used a `::before` pseudo-element with `conic-gradient(var(--blue-l), var(--pink-d), var(--blue-l))`, `position: absolute; inset: -200%`, and the `rotateBorder` animation to create a continuously spinning gradient border on each skill card
- **Background image with opacity overlay** — applied a background image to the `#page::before` pseudo-element at `opacity: 0.2` to create a subtle, non-distracting texture without affecting child element opacity
- **`::after` pseudo-element link underlines** — all `<a>` elements grow a `width: 0% → 100%` underline on hover using a `::after` pseudo-element with a `transition`, producing a smooth animated underline effect
- **Linear gradient buttons** — `.faux-button` uses `box-shadow` with two coloured glows (blue left, pink right) at rest, switching to a `linear-gradient` background fill on hover
- **`linear-gradient` decorative lines** — the project section divider lines use `linear-gradient(to right, ...)` fading to `transparent` for a soft, branded separator
- **Custom scrollbar styling** — applied `scrollbar-width: thin` and `scrollbar-color` using a CSS variable for a branded scrollbar appearance in supported browsers

### Scroll & Overflow
- **CSS Scroll Snap on image carousels** — project image galleries use `scroll-snap-type: x mandatory` on the container and `scroll-snap-align: start` on each image, creating a precise swipeable image carousel with no JavaScript
- **`scroll-behavior: smooth`** — applied to the `#content` scroll container so anchor navigation transitions are smooth rather than instant
- **`position: sticky` header** — the nav header uses `position: sticky; top: 0` so it remains visible at the top of the scroll container at all times

### Typography
- **Google Fonts via `@import`** — loaded the Roboto typeface (full weight range, 100–900, including italics) via a CSS `@import` from Google Fonts CDN
- **`clamp()` fluid font sizes** — all headings (`h1` through `h3`) use `clamp()` to scale font size smoothly with viewport width, staying readable on mobile and impactful on desktop
- **Coloured semantic elements** — used `b` (bold, blue) and `i` (italic, pink) as branded colour tokens in body copy, tying semantic meaning to the colour system

---

## Features Implemented (End-to-End)

- Single-page portfolio with smooth anchor navigation — no routing library, no JavaScript
- Responsive layout adapting from desktop (3-column grid) to mobile (single-column stack) across four breakpoints
- JavaScript-free collapsible mobile navigation using the native `<details>/<summary>` HTML elements
- Scroll-driven entrance animations on projects and skills sections using the CSS Scroll-Driven Animations API
- Rotating animated gradient border on all skill cards via CSS `conic-gradient` and `@keyframes`
- Swipeable image carousels for each project card using CSS Scroll Snap (no JavaScript)
- Animated cycling gradient text on the intro tagline using `background-clip: text` and `@keyframes`
- Staggered fade-in entrance animation on About section content
- Branded design system (pink/blue/purple palette) implemented as CSS custom properties
- External project links to live demos (Itch.io, Steam, Render) and source code (GitHub)
- `mailto:` contact CTA opening the user's native email client

---

## Project Organization & Development

- **Modular CSS architecture** — stylesheets are split into 11 files by responsibility (reset, variables, base, typography, animations, buttons, and five section files), all assembled through a single `main.css` entry point via `@import`
- **Git version control** — project developed with regular, descriptive commits tracked in GitHub, covering feature additions, styling updates, content changes, and bug fixes
- **VS Code** — developed using VS Code with a project-specific `.vscode/settings.json` configuration
- **Asset organization** — images are separated into `assets/` with a dedicated `assets/projects/` subfolder for project screenshots, keeping media files distinct from code
- **No build step or dependencies** — the portfolio is entirely plain HTML and CSS with no npm packages, bundlers, or preprocessors, making it trivially deployable to any static host

---

*This document is intended as a resume-building reference — each item above represents a concrete, demonstrable skill from the Portfolio Site codebase.*
