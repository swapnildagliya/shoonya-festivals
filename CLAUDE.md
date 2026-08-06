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

### "Past editions" section — built 2026-07-29 (supersedes the 2026-06-20 skip decision)
A Past Editions section now exists on both language pages (`#editions`), covering all four editions to date — 2023 Edition One, 2024 Edition Two, 2025 Edition Three, 2026 Heritage Edition Four — each with its historical date range, guest-teacher list and a representative photo in `assets/editions/`. **Image-availability finding (kept for history):** Drive has per-edition folders (2023 showcase ~190 photos · 2024 galashow videos · 2025 ~11 high-res by Stijn Dejonckheere) but they are **unlabeled** (stage/showcase shots, photographer-timestamp filenames) — at the time of the 2026-06-20 investigation there was **no confirmed guest-teacher roster per edition and no named artist portraits**; the 2026-07-29 build resolved this with Swapnil-supplied lineups plus one representative photo per edition. The "Leylet Raqs 2024-N.png" files are **blank design templates**, not artist cards. Drive: 2025 folder `1QqjSKNu0ByTPWk1TtCi_iENCbbTT50jX` · 2024 `1qcKbgAcEuTyJiDE6rIlBv2mX6fE-RKrj` · 2023 showcase `1gIkQlYPluhmyLAZ9IS6xBv82gWk764Ir`; performer-name spreadsheets exist for 2025 (galashow / opening-party — performers ≠ workshop teachers).

### Evergreen design principle (revised 2026-07-29)
The page describes the festival format so it stays live and useful year-round. **Historical edition dates are allowed** — the Past Editions section lists all four past date ranges. The rule is **no FUTURE edition dates or promises**: upcoming-edition info (dates, teachers, ticket links) is still announced via Instagram only.

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
| `hero.jpg` | Page hero (current: June 2024 group shot) — visible `© Stijn Dejonckheere` credit overlay added 2026-08-01 |
| `festival.jpg` | About / atmosphere section |
| `veil.jpg` | Veil / second atmosphere |
| `lenka.jpg` | Teacher / Lenka Badriyah portrait |
| `shoonya-oo-mark-white.png` | Footer oo-mark |
| `favicon.ico` / `favicon.png` / `apple-touch-icon.png` | Site favicons |
| `editions/2023-lou-pradas.jpg` · `2024-julia-farid.jpg` · `2025-hendrik.jpg` · `2026-nisaa.jpg` | Past Editions timeline photos (added 2026-07-29; compressed to 400px long-edge / q80 on 2026-08-01) |

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

## Ghent Tap Festival (2026-08-01)

- **Name is never translated:** "Ghent Tap Festival" in both languages (a past NL draft renamed it "Gent Tap Festival" — wrong, canonical per `Event Submission/docs/teacher-data.md`).
- **Hero = rehearsal video** (`assets/hero-rehearsal.mp4`, 8s cut from Swapnil's 4K rehearsal footage). The *A Pies y Manos* promo reel was rejected as hero (third-party typography, 2.3s loop) and deleted from assets. About figure = `hero-tap.jpg` with visible "Photography · Stijn Dejonckheere" credit.
- **Photo credits:** Jep Meléndez © Aarón S. Ramos (baked credit cropped by card); Joëlle Ribant © Philippe Tollet (left watermark band cropped off the file 2026-08-01; credit shown in card).
- `tapdans.be` has no valid TLS (cert is `*.axc.eu`) — links stay `http://` until that's fixed.
- Teacher bios + edition histories (2023–2026) **confirmed correct by Swapnil 2026-08-01**.

## GIDF (2026-08-01)

- Name: **Gent India Dans Festival** everywhere; JSON-LD organizer = ABC (abcbollywoodbelgium.com) + Shoonya.
- **Opening Party card is a 6.5s muted video loop** (`assets/opening-party-loop.mp4`, cut from `GIDF/2026/gidf-hub/_archive/images-2026/Opening Party.MOV` — real 2026 party). Guest-artist performance photos ≠ the party; Swapnil rejected those for this card.
- Edition-row photos are real frames (2023 stage © **Michael Backaert** — credit required, shown in row; 2024 Kalbeliya circle; 2025 community group — sources: Drive synced folder `~/Library/CloudStorage/GoogleDrive-info@shoonyadance.com/My Drive/Gent India dans festival/`). The old text-heavy promo banners were deleted.
- FAQ (5 Q&As) approved by Swapnil 2026-08-01; visible + FAQPage JSON-LD, both languages.
- Faculty rosters, Kathakali/Julien 2024, the Shampa visa mentions and the Swapnil Dec-2025 quote are all **confirmed by Swapnil 2026-08-01** — do not strip them as "unverifiable".
- ⚠️ The archive photo `GF23 Stijn ABC/20230721-*` set and `ALT-opening-party-garba-group.jpg` are **Gentse Feesten, NOT GIDF** — never caption them as GIDF.

## Groupe Furaya (2026-08-05)

- Page: `groupe-furaya/` (EN) · `groupe-furaya/nl/` (NL). Public title: **African Dance and Percussion with Groupe Furaya**.
- Event date/time: Saturday 19 September 2026, 19:00-21:30 at Shoonya Dance Centre, Gent.
- Format: 19:00 ticketed performance (€20, 90 places), 20:30 free initiations open to everyone, including people without performance tickets.
- Confirmed running order for initiations: Bawayi 20:30 traditional Congolese dance; Joseph 20:45 modern Ndombolo; Awa 21:00 dance from Burkina Faso.
- Only one source video exists. Live asset `assets/performance-teaser.mp4` is a compressed/cropped 12-second derivative; keep a reduced-motion fallback and do not add autoplay video without the `prefers-reduced-motion` hide rule.
- Do **not** use `IMG-20250726-WA0033.png` or `stage-group.jpg`; one face appears blurred/deleted and Swapnil explicitly rejected it for public use.
- Interim CTA is the Shoonya contact page until Zoho/ticket setup exists. Do not restore inert “tickets soon” spans as the primary CTA. The tickets section has **one** CTA — do not add a second button pointing at the same URL.
### Redesign 2026-08-06 — Furaya has its own visual identity

The page was rebuilt after Swapnil judged the shared brass/paper system to read as AI slop here. It now **deliberately deviates from the rest of the estate** (his call: "Furaya only for now"). Do not "restore consistency" with Leylet Raqs / Ghent Tap / GIDF unless he asks.

- **Palette comes out of the photographs, not from the estate:** `--green:#063024` and `--green-deep:#04211A` (the grass), `--gold:#E4B34A` (raffia and headdresses), `--cream:#F7F2E6` / `--cream-2:#EFE7D5` paper. Body ink `#44564E` is a green-biased neutral, deliberately not a plain grey.
- **Type is Furaya-only:** Instrument Serif (display) · DM Sans (body) · Roboto Mono (times on the spine). The house Playfair/PT Serif/Inter stack does **not** apply on this page.
- **The evening is a timeline spine, not a card grid** — `#schedule` holds one `.row` per slot with a mono time column, and the three free initiations are `.row-free` (gold wash + `Free` tag). This is the page's structural idea: it encodes that the night turns into an open floor at a specific minute. `#initiations` anchors the first free row. Don't refactor these back into three cards.
- **Every photo is used exactly once** — hero video (poster `performance-poster.jpg`), intro figure `green-portrait.jpg`, full-bleed band `energy.jpg`, gallery `hero.jpg` + `group-portrait.jpg`. There are only four stills, so any new section needs new photography, not a repeat.
- **og-image is rendered from `_build/render.mjs`** (gitignored dir, recreate if missing) and matches the green/gold identity. Re-render it if the title or the hero photo changes.

Copy rules that survived the earlier de-slop pass: no heading that is two clipped sentences ending in full stops; the "free / no ticket" fact appears about three times, not thirteen; each initiation line says what the participant actually does (no invented biography — none exists for Bawayi, Joseph or Awa).

- **Hero video loads via `data-src`**, not a `<source>` tag: the script assigns `src` only when `prefers-reduced-motion` is *not* set, so reduced-motion visitors never download the 1.5 MB mp4 (the poster carries the frame). Do not revert to inline `src`/`autoplay`.
- **`height="…"` attributes beat `aspect-ratio`.** Both cropping bugs on this page came from that: an `<img>` with a `height` attribute and `width:100%` uses the attribute height and ignores `aspect-ratio`. Any image styled with `aspect-ratio` needs an explicit `height:auto` (or `height:100%` when it should fill a grid row).

## Hub (2026-08-01)

- Root `index.html` + `assets/` (3 hero mp4s, 3 loop mp4s, 6 posters) are live; hub is in `sitemap.xml`.
- CSS ordering trap: any `@media(prefers-reduced-motion)` `video{display:none}` rule must come **after** the base `img,video{display:block}` rule or it silently loses on source order.

---

## Adding a new festival

1. Create `{festival-slug}/index.html` (+ `nl/index.html` if bilingual)
2. Add `{festival-slug}/assets/` with web-compressed images
3. Add `{festival-slug}/_build/render.mjs` for og-image + favicons
4. Add the page to `sitemap.xml` and the hub `index.html` (when one exists)
5. Deploy: `git add -A && git restore --staged CNAME 2>/dev/null || true && git commit && git push`
