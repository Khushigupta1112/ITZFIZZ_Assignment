# Welcome Itz Fizz: Scroll-Driven Hero Section

A hero section where a car drives across the screen as you scroll. The animation follows scroll position (not a timer), and the page is built with HTML, CSS, JavaScript, GSAP and Tailwind.

**Live demo:** [https://khushigupta1112.github.io/ITZFIZZ/](https://khushigupta1112.github.io/ITZFIZZ_Assignment/)
**Repository:** https://github.com/khushigupta1112/ITZFIZZ

## Features

**Layout**
- Full-screen hero (`100vh`) with a letter-spaced headline: **W E L C O M E &nbsp; I T Z &nbsp; F I Z Z**
- Three impact stats below the headline, each with a percentage and a short description
- Responsive: the headline wraps and the stats stack on small screens

**Load animation**
- Headline letters fade in and rise with a slight blur, one after another
- Stats appear one by one with a delay, and the percentages count up from 0
- The car slides in last, then a short "Scroll to drive" hint appears

**Scroll animation (core feature)**
- The hero is pinned while the user scrolls through about 2.5 screens
- Animation progress is tied to scroll position using GSAP ScrollTrigger with `scrub: 1.2`, so motion eases and trails the scroll smoothly
- As you scroll:
  - The car drives from left to right and scales up slightly
  - Both wheels rotate in step with the distance travelled
  - Road dashes move in the opposite direction to suggest speed
  - Speed lines fade in mid-trip and fade out at the end
  - The headline letters drift outward from the centre and fade
  - The stats lift slightly and dim as the car passes
  - The sun shifts slightly for a parallax effect
  - A progress bar along the bottom fills from 0% to 100%

## Tech stack

| Tool | Use |
|---|---|
| HTML5 | Page structure and the inline SVG car |
| CSS3 | Scene styling, theming through CSS variables |
| JavaScript (ES6) | Letter splitting, timelines, counters |
| [GSAP 3](https://gsap.com/) + ScrollTrigger | Intro timeline and scroll-scrubbed animation |
| [Tailwind CSS](https://tailwindcss.com/) (CDN) | Layout utilities (flex, grid, spacing) |
| Google Fonts | Syne (headline and numbers), Manrope (body text) |

## Performance and accessibility

- Only `transform` and `opacity` are animated, so there is no layout reflow while scrolling
- `will-change` is set on animated elements
- Travel distance is calculated once per refresh (`invalidateOnRefresh`), not on every scroll event
- The car is an inline SVG, so there are no image files to load
- With `prefers-reduced-motion: reduce`, scroll animation is turned off and the final content is shown

## Run locally

No build step is needed.

```bash
git clone https://github.com/khushigupta1112/ITZFIZZ.git
cd ITZFIZZ
# open index.html in your browser, or serve it:
npx serve .
```

## Project structure

```
ITZFIZZ/
├── index.html   # markup, styles and animation script
└── README.md
```

## Customising

- **Stats:** edit the `data-count` values and descriptions in the `#stats` list in `index.html`
- **Colours:** change the CSS variables at the top of the `<style>` block (`--bg`, `--accent`, and so on)
- **Scroll length:** change `end: "+=250%"` in the ScrollTrigger config (a larger value makes the car drive more slowly)
- **Smoothness:** change `scrub: 1.2` (higher values trail the scroll more)

## Deployment

Hosted on GitHub Pages from the `main` branch (root folder). The entry file must be named `index.html`.
