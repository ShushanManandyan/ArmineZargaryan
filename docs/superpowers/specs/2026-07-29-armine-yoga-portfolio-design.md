# Armine Zargaryan — Yoga Instructor Portfolio: Design Spec

**Date:** 2026-07-29
**Status:** Approved design — Option C «Ուժ» (Strength), chosen from three researched mockups
**Mockup reference:** `design-options/option-c-strength.html` (visual source of truth)

## Purpose

A single-page, Armenian-language portfolio/CV website for yoga instructor Armine
Zargaryan, to be sent as a link to sport clubs in Armenia when applying for
instructor positions. The page's single job: convince a club manager, in about
a minute and probably on a phone, that Armine is professional, skilled, and
worth calling.

## Audience and constraints

- Viewers: sport club managers in Armenia; assume mobile-first viewing.
- Language: Armenian only (`lang="hy"`).
- Hosting: GitHub Pages (static files only).
- Content: launches with clearly marked placeholder text («պայմանական»);
  Armine's real details (experience, certifications, phone, Instagram) are
  swapped in when provided. Placeholder contact values must be obviously fake
  (`+374 00 00 00 00`, `armine@example.com`) so they are never mistaken for real.

## Visual design (from approved Option C)

Design tokens:

- `--night  #221728` — page background (dark plum, from Armine's training wear)
- `--deep   #2E1F35` — alternate band background
- `--card   #3A2A42` — card surfaces
- `--cream  #F5EFE8` — primary text
- `--gold   #D9A441` — accent: headings' emphasis, numbers, primary buttons
- `--plum   #B489B0` — secondary accent (links)

Typography: Noto Sans Armenian (Google Fonts). Display: weight 800–900,
uppercase, tight leading; hero headline `clamp(2rem, 8.5vw, 6.4rem)` (the 2rem
floor is required — heavy uppercase Armenian words like «ԽԱՂԱՂՈՒԹՅՈՒՆ» overflow
390px screens at 3rem). Body: weight 300, 16.5px, line-height 1.7.

Signature elements: full-viewport muted looping video hero (`video-2.mp4`,
poster `beach-headstand.jpg`) with dark gradient overlay and oversized
two-line headline «Ուժ եւ ներքին խաղաղություն» (second line gold); a 4-cell
stat band under the hero (years / students / certifications / disciplines).

## Page structure (single `index.html`)

1. Fixed top bar — name mark + anchor nav (Իմ մասին, Դասեր, Փորձ, Կապ)
2. Video hero — eyebrow «Յոգայի հրահանգիչ», headline, one-line intro, two
   buttons: «Կապվել ինձ հետ» (gold, → #contact), «Դասերի մասին» (ghost)
3. Stat band — 8+ տարվա փորձ · 500+ ուսանողուհի · 3 հավաստագիր · 4 ուղղություն
   (placeholder numbers)
4. Իմ մասին — text + studio photo
5. Դասեր — 3 cards: խմբային / անհատական / յոգա 50+ կանանց համար
6. Փորձառություն — year + role rows (CV timeline)
7. Պատկերասրահ — photo grid (5 photos, one wide cell)
8. Կապ — centered CTA: call button, phone, email, Instagram
9. Footer — © line

## Technical decisions

- Pure HTML + CSS in one file; JS not required (anchor scrolling is CSS
  `scroll-behavior`). No frameworks, no build step.
- Repo layout: site at repo root — `index.html`, `photos/` (web-named,
  optimized copies), plus `docs/` (specs) and `design-options/` (mockups).
  `res/` (raw WhatsApp originals) is gitignored.
- Photos: optimized/resized copies (target ≲300KB each, max ~1600px long edge).
  Videos kept under 6MB each ✓.
- Meta: Armenian `<title>` + description, Open Graph tags with a beach photo
  as `og:image` so the link previews well in WhatsApp/Viber/Telegram.
- Accessibility/quality bar: alt text on all photos (Armenian), visible
  keyboard focus states, `prefers-reduced-motion` disables the hero video
  (poster shown instead), no horizontal overflow at 390px (verified via
  measurement harness during mockup phase).

## Deployment

- GitHub repository (public) with GitHub Pages serving from `main` branch root.
- Resulting URL `https://<username>.github.io/<repo>/` — delivered to the user
  as the link Armine sends to clubs. Custom domain out of scope.
- Prerequisite to verify at build time: `gh` CLI authenticated (or walk the
  user through `gh auth login`).

## Out of scope (YAGNI)

- Booking/scheduling, blog, multi-language switcher, contact forms (static
  hosting has no backend; contact is tel:/mailto:/Instagram links), analytics.

## Acceptance checklist

- [ ] Renders correctly at 390px, 768px, 1440px with no horizontal overflow
- [ ] Video hero autoplays muted on desktop + iOS Safari (`playsinline`), poster fallback otherwise
- [ ] All placeholder text marked «պայմանական»; obviously-fake contact values
- [ ] Lighthouse-reasonable weight: images optimized, fonts subset by Google Fonts
- [ ] Live at the GitHub Pages URL; link preview shows title + photo
