# CLAUDE.md — Katherine Zhang Portfolio Site

## Project Overview

Personal design portfolio and GitHub Pages static site for **Katherine Zhang**, a Data + AI + Product problem solver who combines data analysis, product thinking, and design (Figma prototyping, UX research) to turn insights into practical digital solutions.

- **URL**: `KatherineZ323.github.io`
- **Stack**: Pure HTML + CSS + vanilla JS — no frameworks, no build tools, no dependencies
- **Deployment**: GitHub Pages (push to `main` branch → live)
- **Owner**: Katherine Zhang (`git user: katherinez994`)

---

## Design System

### Color Palette (CSS custom properties in `style.css`)

| Variable | Hex | Usage |
|---|---|---|
| `--cream` | `#F7F4EF` | Page background, section backgrounds |
| `--charcoal` | `#2C2C2C` | Primary text, dark sections |
| `--sage` | `#A8B9A0` | Borders, decorative |
| `--sage-light` | `#C8D8C0` | Blobs, chips, skill cards |
| `--sage-dark` | `#6E8C65` | Accent text, labels |
| `--dusty-rose` | `#C9A49A` | Hero blob |
| `--dusty-blue` | `#8AABBC` | Hero blob, WanderPal gradient |
| `--warm-sand` | `#D4C4A8` | Contact icon bg |
| `--accent` | `#7BA05B` | CTA buttons, hover states, form submit |
| `--mid-gray` | `#6B6B6B` | Body text, descriptions |
| `--light-gray` | `#E8E4DE` | Borders, dividers |

### Typography
- **Headings**: `DM Serif Display` (Google Fonts) — serif, italic for emphasis
- **Body**: `DM Sans` (Google Fonts) — weights 300/400/500/600

### Reusable Classes
- `.btn-primary` — dark pill button
- `.btn-outline` — bordered pill button
- `.btn-accent` — green pill button
- `.section-label` — small uppercase label with leading bar
- `.section-title` — large serif heading
- `.reveal` / `.reveal.visible` — scroll-triggered fade-up animation (IntersectionObserver in JS)

---

## Site Structure

```
index.html          ← Main page (all sections)
style.css           ← Global styles (nav, buttons, footer, reveals)
assets/
  images/           ← 60+ images: portrait (pic.jpg), dog (dog.jpg), herophoto.png,
                       plus per-project images prefixed altamed_ / rural_ / pawpals_ /
                       wanderpal_ / climate_ / olympians_
  videos/
    olympinas_video.mp4  ← Olympians demo video (filename typo "olympinas")
projects/
  altamed.html
  rural-health.html
  pawpals.html
  wanderpal.html
  climate.html
  olympians.html
```

### Main Page Sections (index.html)

1. **Nav** — Fixed, frosted-glass, logo + links + dropdown "Work" menu with sub-links
2. **Hero** — Full-viewport, 2-col grid. Name, Data/AI/Product headline + supporting text. Animated floating blobs (blur), morphing photo shape, floating info cards. Tag "Open to opportunities."
3. **About** — Bio text, photo collage (pic.jpg + dog.jpg), grouped skills (Data & Analytics / Product & Research / Design & Prototyping), education timeline
4. **Work** — Featured Projects (2-col grid): AltaMed, Rural Health, PawPals, WanderPal. Academic Projects: Climate Scrollytelling, Olympians
5. **Contact** — 2-col: contact links (email/LinkedIn/phone) + message form (front-end only, no backend)
6. **Footer** — Dark, copyright + LinkedIn link

> Note: the Experience section markup was removed from `index.html` (commit `57d6ea6`); its CSS (`#experience`, `.exp-item`) is still in the file. Project pages still link to `../index.html#experience`, which now goes nowhere.

---

## Projects

### Featured Projects

| Project | File | Tags | Description |
|---|---|---|---|
| AltaMed D&A Portal | `projects/altamed.html` | UX Research, Dashboard, Healthcare | Cornell × AltaMed collaboration; SharePoint-based dashboard discovery portal for internal healthcare teams |
| Virtual Rural Health Clinic | `projects/rural-health.html` | Product Design, Accessibility | 12-week capstone; virtual healthcare portal for elderly rural residents; AI-supported clinic interface; dual GTM strategy |
| PawPals | `projects/pawpals.html` | App Design, Service Design | Pet fostering platform connecting owners, venues, and carers |
| WanderPal | `projects/wanderpal.html` | Wearable, Assistive Tech, AI | Wearable navigation device for visually impaired; tactile feedback + AI; Katherine led mapping module + dataset collection |

### Academic Projects

| Project | File | Tags | Description |
|---|---|---|---|
| Climate Scrollytelling | `projects/climate.html` | Data Viz, Scrollytelling, INFO 3312 | Interactive CO₂ emissions data story; 4 lenses (total/per capita/cumulative/consumption); Cornell Data Communication course |
| Olympians | `projects/olympians.html` | Game Design, iOS, TestFlight | iOS game inspired by Greek mythology; available on TestFlight |

### Per-Project Page Template Structure
Each project page reuses the same layout pattern:
- `.project-hero` — gradient bg, back link, emoji, tags, title, subtitle
- `.project-meta-bar` — metadata grid (role / timeline / team / tools)
- `.project-body` — max-width 820px content area with `.project-section` blocks
- `.project-nav-footer` — prev/next project navigation
- Inline `<style>` block inside each page (not shared with style.css, except base styles)

---

## Known Bugs (all fixed; re-verified 2026-09-29)

| # | File | Line | Bug | Fix |
|---|---|---|---|---|
| 1 | `index.html` | 296 | Hero photo src is `assets/images/.jpg` — filename missing | Change to `assets/images/herophoto.png` (or correct filename) |
| 2 | `index.html` | 384 | `<href="projects/altamed.html"` — missing `<a` tag, card is not clickable | Change to `<a href="projects/altamed.html"` |
| 3 | `index.html` | 269 | Nav dropdown Olympians link: `projects/projects/olympians.html` — duplicate `projects/` | Change to `projects/olympians.html` |
| 4 | `projects/altamed.html` | 57 | Nav logo links to `index.html` (relative) — should be `../index.html` from inside projects/ | Fix all project page nav links |
| 5 | `projects/altamed.html` | 54 | `<href=...>AltaMed...` missing `<a` — same pattern as bug #2 | Fix across all project pages |
| 6 | `projects/wanderpal.html` | 50 | Same `<href=...>` broken link pattern in dropdown | Fix across all project pages |
| 7 | Directory | — | The `projects/` directory has a leading space in its disk name (` projects/`) but git tracks it as `projects/`. May cause path issues. | Rename directory to remove leading space |

---

## Person: Katherine Zhang

- **Positioning**: Data × AI × Product — data analysis (SQL / Python / R), product analytics, UX research, AI product, and Figma prototyping; cross-functional work with engineers and stakeholders
- **Education**: M.P.S. Information Science, Cornell University (2025–2026); B.S. Informatics, University of Washington (2021–2025)
- **Skills** (grouped on the site): Data & Analytics (SQL, Python, R, Excel, Tableau, Power BI, Data Analysis, Data Visualization); Product & Research (Product Analytics, UX Research, Requirements Gathering, Experimentation, Roadmapping, Stakeholder Communication); Design & Prototyping (Figma, Prototyping, Interaction Design, Design Systems, Usability Testing)
- **Contact**: katherinezhang323@outlook.com | LinkedIn: kat-zhang-2189692b3 | +1 (206) 228-7198
- **Status**: Open to Product Analyst, Data Analyst, and AI/Product roles

---

## Development Plan / TODOs

### Immediate Bug Fixes
- [x] Fix hero photo image path (`index.html:295`)
- [x] Fix broken `<a` tag on AltaMed card (`index.html:383`)
- [x] Fix Olympians nav link duplicate path
- [x] Fix all project page nav links (now use `../index.html`)
- [x] Fix broken `<href=...>` pattern in all project page dropdowns
- [x] Rename ` projects/` directory to `projects/` (remove leading space)

### Content / Design
- [x] Case study images added to project pages and homepage cards
- [x] herophoto.png linked in hero section
- [ ] Consider adding a Resume/CV download button in the hero or nav
- [ ] Add real project links (Figma prototypes, live demos, TestFlight link for Olympians)

### Functionality
- [ ] Contact form currently does nothing (front-end fake submit only) — wire up to Formspree, EmailJS, or similar no-backend service
- [ ] Add mobile hamburger menu (nav collapses on mobile but no toggle button exists)
- [ ] Consider adding active nav state that highlights the current section on scroll

### Future Features
- [ ] Dark mode toggle
- [ ] Project filter/tag system on the Work section
- [ ] Add a "process" timeline or case study depth to project pages
- [ ] Analytics (simple, privacy-friendly — e.g., Plausible or Fathom)

---

## Architecture Notes

- **No build step** — edit HTML/CSS directly and push to deploy
- **All styles are either** in `style.css` (shared) or inline `<style>` blocks inside each page
- **JS is minimal** — scroll reveal observer + nav shadow + fake form submit, all in `<script>` at bottom of `index.html`
- **Fonts loaded via Google Fonts CDN** — no local font files
- **Images**: all in `assets/images/`, referenced with relative paths (`../assets/...` from project pages); one video in `assets/videos/`
- **Each project page** is self-contained with its own `<style>` block and repeated nav/footer markup
