# CLAUDE.md — shoonya-festivals

Read at the start of every session. This repo powers **festivals.shoonyadance.com** — a GitHub Pages site hosting standalone festival landing pages separate from the main Shoonya web estate.

---

## Repo structure

```
shoonya-festivals/
  leylet-raqs/
    index.html          ← EN page (live)
    nl/index.html       ← NL page (live)
    assets/             ← web-compressed images + favicons
    og-image.jpg        ← 1200×630 social share image
    _build/             ← render scripts (gitignored — never commit)
      render.mjs        ← Playwright: og-image + favicons
      og-image.html
      favicon.html
  CNAME                 ← managed by GitHub Pages — NEVER commit changes to this
```

---

## Deploy rule — NEVER commit CNAME (D-026)

```bash
git add -A
git restore --staged CNAME 2>/dev/null || true
git commit -m "..."
git push
```

GitHub manages CNAME via repo Settings → Pages → Custom domain. Committing it resets SSL cert provisioning.

---

## Leylet Raqs

**"Leylet Raqs"** = Arabic for *Night of Dance*. Annual Raqs Sharqi (Egyptian bellydance) festival, Ghent, Belgium. **First edition: 2023** (the "2022 Final Budget" doc in Drive is a planning file — the event itself launched February 2023).

### Brand
- **Accent:** pomegranate `#C13B5A`
- **Fonts (page):** Playfair Display (headings) · PT Serif (body) · Inter (UI chrome)
- **Wordmark:** the **kashida "Leylet Raqs" lockup** — **EB Garamond italic 500** with a pomegranate *kashida* ligature stroke (SVG path `M4,40 C40,33 80,30 108,32 C122,33 130,29 134,22 C131,31 121,36 108,37 C80,38 40,40 4,42 Z` on viewBox `0 0 138 60`) between the two words. Used in the nav (HTML span+SVG, not the old Playfair text-SVG). Full system + monogram + circle-avatar variants: Design System `projects/shoonya/leylet-raqs/wordmark-lockups.html`; exported PNGs in `_Assets/logos/leylet-raqs/` + that project's `exports/`. Source: Claude Design "Leylet Raqs Wordmark" (Direction 02 · Ritual). EB Garamond is the **wordmark-only** face — page headings stay Playfair.
- **Mood:** intimate, ritualistic, luminous — night of dance
- **Instagram:** `@leylet_raqs_festival`
- **Page:** `festivals.shoonyadance.com/leylet-raqs/` (EN) · `.../leylet-raqs/nl/` (NL)

### SEO / AEO — "bellydance" + "international" (2026-06-20)
People search **"bellydance"**, not "Raqs Sharqi" — so the page pairs both everywhere (title, meta, OG/Twitter, JSON-LD, hero eyebrow "Ghent's International Bellydance Festival", first body line). A dedicated FAQ **"Is Leylet Raqs a bellydance festival?"** (visible accordion + FAQPage JSON-LD, both langs) captures that exact query. Festival is framed as **international** (guest teachers from across the world). Keep both keywords on any future edit; NL uses **"buikdans"** + **"internationaal"**.

### About-section photo
Uses `assets/lenka-red.jpg` — Lenka Badriyah, red-costume studio portrait (compressed from `_Assets/.../teacher-photos/lenka-badriyah/3.jpg`, 1000×1400/q80). Distinct from the pink/green curator-section shot. **No confirmed photographer** on this frame — same studio shoot as the © Isabelle Hanneuse curator photo but not verified, so no visible credit. (The old watermarked festival-dancer `festival.jpg` was removed.)

### "Past editions / guest artists" section — investigated & SKIPPED (2026-06-20)
Swapnil considered a per-edition guest-artist section; **decided to skip** to keep the page evergreen. **Image-availability finding (so it isn't re-investigated):** Drive has per-edition folders (2023 showcase ~190 photos · 2024 galashow videos · 2025 ~11 high-res by Stijn Dejonckheere) but they are **unlabeled** (stage/showcase shots, photographer-timestamp filenames) — there is **no confirmed guest-teacher roster per edition and no named artist portraits**. The "Leylet Raqs 2024-N.png" files are **blank design templates**, not artist cards. Only Lenka is reliably identified. Building a *named* artist grid would need Swapnil to supply the lineup + photos first. Drive: 2025 folder `1QqjSKNu0ByTPWk1TtCi_iENCbbTT50jX` · 2024 `1qcKbgAcEuTyJiDE6rIlBv2mX6fE-RKrj` · 2023 showcase `1gIkQlYPluhmyLAZ9IS6xBv82gWk764Ir`; performer-name spreadsheets exist for 2025 (galashow / opening-party — performers ≠ workshop teachers).

### Evergreen design principle
The page carries **no specific edition dates** — it describes the festival format so it stays live and useful year-round. Edition-specific info (dates, teachers, ticket links) is announced via Instagram only.

### Weekend format (confirmed from 2025 programme)
| Day | Programme |
|---|---|
| **Friday** | Workshops · Lecture · Feedback Show (18:00–19:00) · Opening Party with performances (19:30) |
| **Saturday** | Full day workshops · Galashow × 2 (18:30 + 21:00) — live music both shows |
| **Sunday** | Workshops · Panel discussion with artists · Closing circle |

### Live musicians (confirmed recurring)
- **Osama Abdulrasol** — qanun (Iraqi, based Ghent, Belgian Gent Cultural Prize 2013)
- **Jamal Moussaid** — tabla / percussion

### Assets
All images in `leylet-raqs/assets/` are web-compressed (≤1400px / q80 — D-030). **Never link to `_Assets/` library originals.**

| File | Use |
|---|---|
| `hero.jpg` | Page hero (current: June 2024 group shot) |
| `festival.jpg` | About / atmosphere section |
| `veil.jpg` | Veil / second atmosphere |
| `lenka.jpg` | Teacher / Lenka Badriyah portrait |
| `shoonya-oo-mark-white.png` | Footer oo-mark |
| `favicon.ico` / `favicon.png` / `apple-touch-icon.png` | Site favicons |

**Potential hero upgrade:** 2025 Stijn Dejonckheere photos in Google Drive folder `1WFwSvbrbDQ6aqx8sz3zx4kcuHohvwRbI`. Download, compress to 1400px/q80, replace `hero.jpg`, re-render og-image.

### Re-rendering og-image + favicons
```bash
cd leylet-raqs/_build
node render.mjs
# outputs: ../og-image.jpg · ../assets/favicon.ico · ../assets/favicon.png · ../assets/apple-touch-icon.png
```
Requires `node_modules` symlink: `shoonya-festivals/node_modules → ../Design System/node_modules`.

### D-029: EN ↔ NL sync
Every edit to `index.html` must be mirrored in `nl/index.html` in the same session.

### Known trap: first edition year
The Google Drive contains a file named "Leylet Raqs 2022 Final Budget" — this is a **planning document from Sept 2022**, not a 2022 event. The first actual festival was **February 17–19, 2023**. Always say "since 2023."

---

## Adding a new festival

1. Create `{festival-slug}/index.html` (+ `nl/index.html` if bilingual)
2. Add `{festival-slug}/assets/` with web-compressed images
3. Add `{festival-slug}/_build/render.mjs` for og-image + favicons
4. Add the page to `sitemap.xml` and the hub `index.html` (when one exists)
5. Deploy: `git add -A && git restore --staged CNAME 2>/dev/null || true && git commit && git push`
