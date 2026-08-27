---
name: update-events
description: Rotate mikanah-site/events.html - remove gathering seasons that have fully passed, reorder the remaining sections chronologically, and roll the next year's season(s) onto the bottom so exactly 4 season sections (12 cards) stay live. Use when a season has ended or when checking events.html for staleness.
---

# Update Events

`events.html` always shows exactly 4 season sections (Winter, Spring, Summer, Fall - whichever 4 are next in the rolling calendar), 3 city cards each (Winnipeg, Brandon, Selkirk) = 12 cards total. This skill keeps that window current.

## 1. Read the current state

Open `mikanah-site/events.html`. Each season section looks like:

```html
<h2>{Season} — {Month} {Year}</h2>
<div class="events-grid">
  <div class="event-card" data-city="..." data-season="...">...<span class="event-date">{Month} {Year} · {date text}</span>...</div>
  ... (3 cards: winnipeg, brandon, selkirk)
</div>
```

Season order cycles: Spring (March) → Summer (June) → Fall (September) → Winter (December), then the next year's Spring, etc.

## 2. Decide which sections have passed

For each section, check its `event-date` text:

- **If it still reads "Date TBD"** (no real date confirmed): treat the whole month as not-yet-over. The section counts as passed once today's date is on or after the 1st of the month *after* the listed month/year. (e.g. "March 2026 · Date TBD" is passed starting April 1, 2026.)
- **If a real date has been filled in** (e.g. "March 15, 2026"): compare directly against today's date instead of the month heuristic.
- Dates can differ per city card within the same section if some cities have confirmed dates and others are still TBD. If cards within one section disagree on whether they've passed, ask the user how to handle it rather than guessing - don't split a section silently.

## 3. Remove, reorder, and roll forward

- Delete every section that has fully passed.
- Keep the remaining sections in chronological order, earliest first.
- Add new season section(s) at the bottom, continuing the Spring→Summer→Fall→Winter cycle into the next year(s), until exactly 4 season sections (12 cards) remain.
- For each new section, reuse the same h3 title and body copy per city/season as the last time that city+season combination appeared (find it in git history if it's no longer in the file - `git log -p -- mikanah-site/events.html`). Only the year in the `<h2>` and in each `event-date` span changes. Keep "Date TBD" unless the user gives you a real date.
- If the info-box or hero copy hardcodes a specific year (e.g. "All 2026 gatherings..."), consider whether it should stay generic instead now that the page spans multiple years.

## 4. Flag, don't fabricate, recaps

Any city/season card you remove because it already happened (not just because its window elapsed with nothing scheduled) represents a gathering that took place. Don't write recap copy for it - that needs real narrative and photos from the event. Instead, tell the user which gatherings were removed and remind them to add a recap post to `updates.html` if one hasn't been added yet (see the Outstanding To-Do list in `CLAUDE.md`).

## 5. Show the diff, then ask before publishing

Show the user a summary of what changed (sections removed, sections added, any copy carried over). This site auto-deploys on push to `main` and is publicly live at mikanah.ca, so **always ask for explicit confirmation before committing and pushing** - don't push automatically as part of this skill.
