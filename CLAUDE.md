# CLAUDE.md — Mikanah Gatherings Website

> This file provides context and instructions for Claude Code working on the mikanah.ca website.

---

## Project Overview

**mikanah.ca** is the public website for Mikanah Gatherings — a CIHR-funded, community-engaged research project run by the Urban Trails Research Program at the University of Manitoba / CHRIM. The project hosts seasonal land-based events for Indigenous communities in Winnipeg, Brandon, and Selkirk, Manitoba.

The site serves two purposes: public event information and research dissemination.

---

## Repository Structure

```
mikanah-site/          ← repo root
  mikanah-site/        ← base directory (Netlify deploys from here)
    index.html         ← Homepage
    events.html        ← 12 annual events with filters + notify modal
    team.html          ← Research team (4 sections)
    updates.html       ← Blog-style updates and event recaps
    contact.html       ← Contact form
    style.css          ← Shared styles and CSS variables
    images/
      logo.png                  ← Main logo (transparent background)
      logo-grey.png             ← Greyscale logo
      map-bg.jpg                ← Red River Settlement map (hero background)
      metis-sash.jpg            ← Métis sash textile photo (banner)
      brandon-event-1.png       ← Brandon Feb 2026 gathering collage 1
      brandon-event-2.png       ← Brandon Feb 2026 gathering collage 2
      brandon-june-opening.jpg  ← Brandon June 2026 — opening/amphitheatre
      brandon-june-tipi.jpg     ← Brandon June 2026 — tipi teaching
      brandon-june-drum.jpg     ← Brandon June 2026 — drum teaching
      carousel-winnipeg.jpg     ← PLACEHOLDER — replace with real Winnipeg photo
      carousel-assiniboine.jpg  ← PLACEHOLDER — replace with real event photo
      carousel-selkirk.jpg      ← PLACEHOLDER — replace with real Selkirk photo
```

**IMPORTANT:** Files live at `mikanah-site/mikanah-site/` — the repo has a nested folder. Netlify base directory is set to `mikanah-site`.

---

## Deployment

- **Hosting:** Netlify (auto-deploys on push to `main`)
- **Domain:** mikanah.ca via Namecheap
- **Build step:** None — plain HTML/CSS/JS
- **Repo must stay public** — free Netlify plan only allows one contributor on private repos

To deploy: commit and push to `main`. Netlify deploys automatically within ~10 seconds.

---

## Design System

### CSS Variables (defined in style.css)

```css
--brown-dark:   #3d1f0a   /* Nav, headings, buttons */
--brown-mid:    #5a3a20   /* Body text */
--brown-light:  #c9a882   /* Muted text on dark backgrounds */
--cream:        #f5efe4   /* Page background */
--cream-mid:    #ede4d4   /* Section/card backgrounds */
--gold:         #e8a830   /* Sacred colour — accent, buttons */
--red:          #b83c2a   /* Sacred colour — labels, tags */
--off-white:    #f0e8d8   /* Sacred colour — Winter Solstice */
--near-black:   #1a120a   /* Sacred colour — Fall Equinox, footer */
--border:       #ddd0bb   /* Card borders, dividers */
--text-muted:   #8a6040
--text-body:    #5a3a20
```

### Fonts
- **Headings:** Playfair Display (Google Fonts, serif)
- **Body/UI:** Lato (Google Fonts, sans-serif)

### Four Sacred Seasons — Colour Mapping
| Season | Background | Text |
|--------|-----------|------|
| Winter Solstice | `#f0e8d8` (off-white) | Dark brown |
| Spring Equinox | `#e8a830` (gold) | Dark brown |
| Summer Solstice | `#b83c2a` (red) | Cream |
| Fall Equinox | `#1a120a` (near-black) | Gold |

### Sacred Colour Strip
A 5px strip (white / gold / red / black) sits below every nav bar on every page. **Never remove this** — it is culturally significant.

---

## Writing Guidelines

- **Reading level:** Grade 4–6 for all public-facing content
- **No em dashes (—)** — they read as AI-generated. Use colons or rewrite
- **Cultural teachings:** Use "teachings were shared about..." not "they learned..."
- **Knowledge Keepers:** Do not use "elders" as a general term unless quoting
- **Tone:** Warm, community-centred — not institutional or academic
- **Event recaps:** Use the actual date, not "this past weekend"
- **"Gatherings"** preferred over "events" where possible

---

## Netlify Forms

Two forms are active — **do not remove the hidden detection divs**:

```html
<!-- Required for Netlify form detection -->
<form name="contact" data-netlify="true" hidden>...</form>
<form name="event-notify" data-netlify="true" hidden>...</form>
```

Both forms email submissions to `jslaght@chrim.ca`. Configured in Netlify dashboard → Forms → Notifications.

---

## Content Structure

### Homepage (index.html) — Section Order
1. Nav + sacred colour strip
2. Hero — map background (Red River Settlement map), logo, tagline, CTAs
3. Map markers strip — Winnipeg / Brandon / Selkirk (city names only, no subtitle text)
4. Métis sash — real textile photo at 65px height, 0.55 opacity
5. Carousel — 5 slides auto-advancing every 4.5s
6. Mission section — split grid (text left, dark panel with stats right)
7. Four seasons strip
8. About the project
9. CTA band
10. Partners bar (all 7 partners, clickable links)
11. Footer

### Carousel Slides (index.html)
- Slide 1: brandon-event-1.png — Brandon Feb 2026 (with caption)
- Slide 2: brandon-event-2.png — Brandon Feb 2026 (with caption)
- Slide 3: brandon-june-opening.jpg — Brandon June 2026 (with caption)
- Slide 4: brandon-june-tipi.jpg — Brandon June 2026 (with caption)
- Slide 5: brandon-june-drum.jpg — Brandon June 2026 (with caption)

### Events (events.html)
12 events total — 4 seasons × 3 cities. Organized chronologically:
Spring → Summer → Fall → Winter. Each with city/season filter tags and a "Get Notified" modal.

### Team Page (team.html) — Section Order
1. Principal Investigators (Jon McGavock, Jaimy Fischer)
2. Knowledge Keepers & Cultural Advisors (Helen Settee, Brian Rice)
3. Community Partners — Winnipeg subsection (Diane Roussin, Katherine Rempel, Aidan Roberts, Anders Swanson), Brandon subsection (Dean Hammond, Ingrid Gatin, Devyn McKay)
4. Research Coordinator & Co-Investigators (Jana Apperley, Erin Millions, Mélanie Morris)

### Updates (updates.html)
Blog-style. Most recent post is `class="post-card featured"`. When adding a new post, change the previous featured post to `class="post-card"`. Posts are ordered newest first within `<main>`.

---

## Known Issues — Do Not Attempt to Fix

- **Map graininess:** The hero map (map-bg.jpg) is somewhat soft. This is a source image limitation. Further processing makes it worse. Accept as-is.
- **Map markers visibility:** All 3 markers are visible on most screen widths but the crop is imperfect. Accept as-is.

---

## Outstanding To-Do

- [ ] Replace placeholder carousel images with real Winnipeg and Selkirk event photos
- [ ] Add Winnipeg Summer Solstice event recap to updates.html
- [ ] Add team member photos to team.html when available
- [ ] Confirm and update event dates on events.html as they are scheduled
- [ ] Add Selkirk community partner team members when confirmed
- [ ] Add talking circle / findings posts to updates.html as research progresses

---

## Key Contacts

| Role | Name | Contact |
|------|------|---------|
| Research Coordinator / Site Owner | Jana Apperley (Slaght) | jslaght@chrim.ca |
| Project phone | | (204) 789-3591 |
| Website | | mikanah.ca |
| Parent program | Urban Trails Research | urbantrailsresearch.ca |
