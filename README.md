# Palacio Bela Vista

Static website for **Palacio Bela Vista**, a Pombaline palace at **Rua do Ataíde 9, 1200-034 Lisboa**, parish of Misericórdia.

- **Live for now:** https://fernangz.github.io/palaciobelavista.com/
- **Repository:** https://github.com/fernangz/palaciobelavista.com
- **Final domain (pending):** https://palaciobelavista.com
- **Enquiries:** palaciobelavista@gmail.com (mailto links only)

> The public name is **Palacio Bela Vista** (two words). The domain, repository and email address keep the compact `palaciobelavista.com` form; the video and VTT filenames also keep the hyphenated form.

> **Hosting note.** The site is published on GitHub Pages at the repository URL while the final domain is arranged. GitHub Pages deploys after a push to `main`; the build and CDN usually update within 1–10 minutes, occasionally longer. A hard refresh or a fresh `curl -I` is the quickest way to confirm the new `last-modified` header. Canonical, hreflang, Open Graph and JSON-LD URLs currently use the GitHub Pages address, not the future domain.
>
> **Indexing is disabled.** `robots.txt` disallows all crawlers, every page has `noindex`, and `sitemap.xml` is absent. This is not access control: the GitHub Pages site and the repository are still public.

## 1. Project overview

A private Pombaline residence in Lisbon, presented through film, a 25-image gallery, an Overview of the property and a direct full-dossier request.

| Field | Value |
| --- | --- |
| Name | Palacio Bela Vista |
| Street | Rua do Ataíde 9 |
| Postal code | 1200-034 |
| City / parish | Lisboa / Misericórdia |
| Country | Portugal |
| Coordinates | 38.7086386, -9.1443863 |
| Email | palaciobelavista@gmail.com (mailto only) |

The Google Maps link was removed. Location links point to OpenStreetMap; the map is a static, cookie-free image with OSM attribution.

## 2. Repository contents

This repo contains the **published static site only**, at the root. Locale pages live in their own folders so the public URLs are clean.

```text
index.html                  English (site root)
zh/index.html               Chinese (Simplified)
hi/index.html               Hindi
es/index.html               Spanish
ar/index.html               Arabic (RTL)
fr/index.html               French
pt/index.html               Portuguese
ru/index.html               Russian
de/index.html               German
ja/index.html               Japanese
it/index.html               Italian

app.js                      Menu, filters, lightbox, film
assets/img/                 Responsive AVIF/WebP/JPEG, map, icons, OG card
assets/video/               Film, poster, English VTT
qr/                         Print-ready postcard QR SVG
favicons, site.webmanifest, robots.txt, _headers, vercel.json, .nojekyll
README.md
FONT-LICENSES.md
POSTCARD-DESIGN-CHANGES.md
```

- **URLs:** `/` (English), `/fr/`, `/pt/`, `/es/`, `/de/`, `/it/`, `/ja/`, `/zh/`, `/ar/`, `/ru/`, `/hi/`.
- The old `/fr.html`, `/pt.html`, `/es.html`, `/de.html` and `/it.html` URLs were removed, not redirected. GitHub Pages serves `folder/index.html` at the folder URL; there is no server-side redirect layer.
- CSS is inlined in each HTML page; Noto Serif, Noto Sans and the script-specific Noto WOFF2 subsets are inlined as base64. Source masters and build scripts live outside this publishing repo.
- Local preview: `python3 -m http.server 8000`, then open `http://127.0.0.1:8000/`, `http://127.0.0.1:8000/fr/`, and so on. Opening a locale folder directly from disk also works, but a local server is closer to production.

## 3. Design decisions

### Client corrections

The 21 November 2026 French review document and the confirmed decisions are recorded in [CORRECTIONS-TO-APPLY.md](CORRECTIONS-TO-APPLY.md). No corrections have been applied yet.

### Postcard design reference

The supplied postcard is now the site’s visual system: cream stock, split photo/text panels, the supplied engraved emblem, a two-line uppercase wordmark, thin brass rules, serif body copy and deep-ink gallery/footer contrast. The gap analysis and implementation record are in [POSTCARD-DESIGN-CHANGES.md](POSTCARD-DESIGN-CHANGES.md). Resolved: the name stays **Palacio Bela Vista**; the supplied engraved emblem is the primary logo; the gallery stays dark; the sale wording is **“Private residence available to purchase”**; the postcard QR points to `/?play`; there is no downloadable postcard. The typefaces remain Noto Serif and Noto Sans.

### Direction

- **Private residence, not a hotel or estate listing.** No price panels, badges, stock photography or glossy marketing cards; the house is the subject.
- **Editorial, quiet, confident.** Generous cream space, thin brass rules, muted colour, a few strong typographic moments. Brass is an accent, never a wash.
- **One atmosphere, changing temperature.** Cream postcard panels for reading, a dark gallery for photographic contrast, and a dark footer as the closing block.
- **Craft in the interface.** Precise spacing, letter-spaced labels, fine borders and the supplied engraved emblem instead of generic UI chrome.

### Typography

| Role | Typeface | Treatment |
| --- | --- | --- |
| Display | **Noto Serif** | Uppercase two-line wordmark and key headings; italic emotional lines |
| Body | **Noto Serif** | Regular editorial prose, 1.06–1.09rem, 1.7 line-height |
| Labels | Noto Sans | Uppercase, 1rem, wide tracking, brass-deep |
| Navigation/buttons | Noto Sans | Uppercase, 1rem, tracked, thin rules |

- Noto Serif + Noto Sans were chosen for complete script coverage and a coherent editorial voice across all eleven languages; the serif keeps old-house authority, while the sans keeps labels quiet and legible.
- Postcard H1: `clamp(2.4rem, 4.4vw, 4rem)`, forced to two lines; section H2s use fluid clamps, with property/characteristics capped at 4.4rem so long translations fit at 320px.
- Body: `1.0625rem` mobile, `1.09rem` desktop, 1.7 line-height.
- **Every label, caption, nav item and footer line has a 1rem/16px floor.**
- Overview labels and contact metadata use the 1rem floor; values use the serif body size.
- Italic lines carry the emotional register: “History. Beauty. A home like no other.” and “Discover the residence.”
- Menu/gallery numerals use tracked Noto Sans as editorial folios, not UI counters.
- **Script coverage:** Noto Serif and Noto Sans carry Latin and Cyrillic, so Russian uses the same serif/sans pairing as the Latin pages, with Cyrillic glyphs included in the embedded subsets.
- All pages use the same two CSS families, `Noto Serif` and `Noto Sans`. Script-specific faces are registered under those same family names with `unicode-range`, so there are no per-language font stacks or duplicated font-family rules.
- Japanese, Simplified Chinese, Arabic and Hindi use embedded Noto faces, subset to the characters actually used on that page:
  - Japanese: Noto Serif JP 400 for display and body; variable Noto Sans JP for labels and UI.
  - Chinese: Noto Serif SC 400 for display and body; variable Noto Sans SC for labels and UI.
  - Arabic: Noto Naskh Arabic 400 for display and body; variable Noto Sans Arabic for labels and UI.
  - Hindi: Noto Serif Devanagari 400 for display and body; variable Noto Sans Devanagari for labels and UI.
- Every page also embeds tiny native-name subsets for `中文`, `हिन्दी`, `العربية`, `Русский`, `日本語` plus arrow and prime subsets, all registered as additional `Noto Sans` faces with exact `unicode-range` values. The language list therefore renders consistently without a separate CSS class.
- Local system fonts remain as a final fallback, but they are no longer the primary source for any script.
- No external font request is introduced: all faces are inline WOFF2 data URIs. The trade-off is page weight — Japanese, Chinese and Hindi pages are roughly 0.5–0.6 MB of HTML (Chinese just over 0.6 MB) because the embedded subsets are larger.
- Font licences and copyright notices are in `FONT-LICENSES.md`.

### Colour tokens

| Token | Value | Use |
| --- | --- | --- |
| `--ink` | `#1b1a17` | Gallery, footer, dark UI |
| `--ink-2` | `#24221d` | Image placeholders |
| `--forest` | `#2a2a24` | Deep neutral support |
| `--paper` | `#fcf3e4` | Postcard stock / primary background |
| `--paper-2` | `#f6ead8` | Characteristics / alternate cream |
| `--mount` | `#dbc9bb` | Outer mount around the cover panel |
| `--stone` | `#eadcc7` | Warm neutral support |
| `--gold` | `#9a8468` | Brass rules and accents |
| `--gold-2` | `#c8b08a` | Brass on ink |
| `--gold-deep` | `#6e5b43` | Accessible brass text on cream |
| `--wine` | `#6a2228` | Rare editorial accent |
| `--text` | `#2b2924` | Body copy |
| `--muted` | `#6b6255` | Secondary copy |

- Brass-deep for labels on cream; brass-2 on ink for contrast. Cream-on-ink is the primary pairing in the gallery and footer.
- No pure black/white: darkest is warm near-black ink, lightest is postcard cream.
- Section colour changes are structural: cream postcard panels for reading, a dark gallery for photographic contrast, and a dark footer.

### Layout and spacing

- Mobile-first; desktop enlarges the same hierarchy rather than redesigning it.
- Shell `min(100% - 2 × gutter, 1480px)`; gutter `clamp(1.25rem, 4.2vw, 4.5rem)`.
- Section rhythm `clamp(5rem, 11.5vw, 10.5rem)`.
- Asymmetric editorial grids; section intros split a large serif heading with a short standfirst.
- Body measures 33–46rem; images may break the grid and run full-bleed; text stays in the shell.
- Rules are 1px, translucent ink or ivory; no heavy dividers.

### Responsive rules

| Breakpoint | Changes |
| --- | --- |
| `< 22rem` | Wordmark hidden; emblem remains |
| `36rem` | Characteristics 2 columns; gallery 2 columns; facts 3 columns |
| `48rem` | Editorial grids; chapter layouts; 2-column footer |
| `68rem` | Full desktop nav + header CTA; gallery 3 columns |
| `90rem` | 3-column footer; maximum display scale |

- Navigation enters the full-screen menu below 68rem; it never wraps or crowds on tablets.
- Footer stays 2-column until 90rem so translated labels fit.
- Gallery: 3-column masonry desktop, 2-column tablet, snap carousel mobile.
- Buttons use `0.12em` tracking at 16px to avoid unnecessary wrapping.
- German compounds hyphenate; footer headings are non-breaking.
- No horizontal overflow at 320, 360, 390, 412, 768, 960, 1024, 1280 or 1440px in the Latin locales.
- Arabic is RTL: the page sets `dir="rtl"`, mirrors flex/margin direction, flips the select arrow, lightbox arrows and film label, and disables letter-spacing for connected Arabic script. Arabic line-height is increased to 1.95.
- CJK and Devanagari body line-height is increased to 1.85–1.9 for readability.

### Header and menu

- Header is permanently cream with ink text, a hairline rule, 14px blur and the supplied emblem. It keeps a compact 4.5rem height from first paint; there is no scroll-driven resize or colour change.
- Fixed header is shallow; a scroll-padding offset keeps anchors clear; state restores on reload/direct anchors.
- Desktop nav is three quiet links — Video, Gallery, Overview — plus the outlined Contact button. Contact is also available in the full-screen menu on mobile.
- Mobile uses a two-line toggle and full-screen dialog, not a cramped drawer.
- Menu is cream with 22px blur, numbered 01–04, Noto Serif links, address and language switcher at the foot. Native `showModal()`, Escape, backdrop click and focus return.

### Page structure

The page is ordered for a real-estate reader rather than an editorial one:

**Header → Video → Gallery → Overview → Contact → Footer.**

- **Video** opens with a postcard cover panel: framed 1:1 entrance-hall film poster beside a cream text panel with the supplied emblem, two-line wordmark, location, promise, sale line and an editorial play plaque. Contact and Gallery links sit below the panel.
- **Gallery** follows immediately: 25 photographs, filters and lightbox.
- **Contact** gives the address, appointment note and the static antique area map, with no pin, coordinates or price.
- **Overview** replaces the old Property and Characteristics sections. It uses the old Property introduction and a twelve-field grid: property type, nearest metro, reported area, reported plot area, rooms, bedrooms, bathrooms, build year, construction materials, structural features, outdoor spaces and sustainability status. The reported figures are 1,036.68 m², 488.49 m², 25 rooms, 12 bedrooms and 1783, with a garden and two terraces. Bathroom schedule and floor count remain to be confirmed; the grid carries that caveat. Coordinates and asking price are no longer published.
- The former Craft section is removed; its six photographs already live in the gallery, and the craft detail remains in the captions and Overview facts.
- **Contact** has no form and no visible email address. It opens with the italic **Discover the Palacio**, sets **Private film & viewing enquiries** beneath it, then gives the address, appointment note, a small antique-style area map without a location pin, and an outlined **Request the full dossier** button whose `mailto:` goes to `palaciobelavista@gmail.com` with a prefilled localized subject and body.
- **Footer** carries the supplied emblem, an uppercase two-line wordmark, a minimal copyright line, Back to Top and the eleven-language selector.

### Photography, gallery and lightbox

- Only palace photography; no stock. Crops favour symmetry, doorways, ceiling roundels and garden depth; natural colour, no heavy filters.
- The gallery remains full-bleed on dark ink; craft images sit as framed plates on a cream mount; explicit dimensions and responsive AVIF/WebP/JPEG.
- Video poster and below-fold images use native lazy loading; the map is eager-loaded, desaturated, and carries the brass pin and cream card.
- Visible Engel & Völkers watermarks were removed by seam-cropping quiet areas and blending, not painting over architecture.
- Gallery: 3-column masonry desktop, 2-column tablet, 84%-viewport snap carousel mobile. One gallery, no filters and no photograph count; all 25 images remain.
- Hover/focus: soft brass radial light + thin inset frame; captions over a bottom gradient.
- Lightbox: near-black blurred backdrop, large image, title/category, count, arrows, keyboard/swipe, no thumbnail strip; selects a viewport-appropriate variant instead of upscaling.

### Video, Overview and map

- Video is the first content section: a 1:1 entrance-hall poster with a cream-and-brass play plaque, never autoplaying; it opens a native-control dialog with captions. Runtime 42 seconds.
- Contact carries the address, property type and nearest metro in Overview, and a small **static OSM image** styled as an antique area map, with no location pin. The map is not an iframe: no cookies, no third-party JS, and visible OSM attribution. Coordinates, asking price and the separate Property section are removed.
- The architecture plan drawing is no longer a separate section; the essential structural facts are carried in Overview and the gallery captions.

### Contact, footer and languages

- **No contact form.** The contact section gives the email address and a single **Request the full dossier** button.
- The button is a `mailto:` link with a prefilled, localized subject and body asking for more information about the property and the full dossier.
- Footer: dark ink, supplied emblem, uppercase two-line Noto Serif wordmark with brass “Bela Vista”, a minimal copyright line, Back to Top and the eleven-language selector. The old Visit/Discover/Contact columns and descriptive/contact texts are removed.
- Language switcher in footer and menu, not header: visible two-letter codes, native-language accessible names, active brass rule. It lists eleven languages in speaker order.
- Back-to-top is a plain text arrow link, not a floating button.

### Motion and performance trade-offs

- Restrained motion: image scale, brass gallery light, dialog fades, arrow shifts. No scroll reveals, parallax or clip-path entrances.
- Scroll reveals were removed because they delayed LCP, blocked native lazy loading and caused ghosting.
- Anchor navigation is instant; `prefers-reduced-motion` disables transitions/animations/smooth scrolling.
- Fonts inlined as per-script subset WOFF2 data URIs; critical CSS inlined; one deferred vanilla JS file; no framework hydration.
- Map is an image; film is click-to-load; no third-party requests.
- Section `content-visibility` was removed because placeholder heights caused anchor/layout jumps at tablet widths.
- Explicit image dimensions/aspect ratios prevent CLS.
- The new locale pages reuse the same CSS, imagery and JS; they add no network requests beyond the shared page assets. The embedded CJK/Devanagari subsets make those HTML files heavier, but they are cached as part of the document.

### Accessibility-driven visual decisions

- The 16px floor changed the scale: labels, captions and nav are larger and the layout was re-spaced around them.
- Header is permanently cream with ink text and a hairline, so it belongs to the same paper system as the page and never changes form on scroll.
- Language switchers moved out of the header so 16px labels would not crowd primary navigation.
- Footer reflows earlier; German compounds hyphenate; long email addresses wrap safely.
- Icon-only controls have accessible names; text controls stay text; brass is darkened to brass-deep on light paper.
- Body copy, headings and contact text remain selectable; media, navigation, buttons and UI labels use `user-select:none`. Links and buttons use `pointer`, gallery images use `zoom-in`, disabled controls use `not-allowed`, and body text keeps the normal text cursor.
- New locales translate `alt`, `aria-label`, lightbox titles/captions, gallery category labels, contact copy and the film close controls.
- Arabic keeps native RTL reading order; focus order follows the DOM.

### Rejected directions

- Google Maps iframe/embed — privacy, performance, visual control.
- Third-party fonts, analytics, heatmaps, cookie banner, chat widget — omitted entirely.
- Autoplaying video — performance and tone.
- Scroll-reveal/parallax and section `content-visibility` — LCP, ghosting and layout jumps.
- Tiny 10–12px luxury captions — inaccessible; 16px floor.
- Header language dropdown — moved to menu/footer.
- Rounded pills, heavy cards, drop shadows — replaced by thin rules, flat planes, editorial type.
- Stock palace imagery — replaced by photography of the actual house.
- `.html` locale files at the root — replaced by folder URLs with `index.html`.

## 4. Accessibility specification

The site targets **WCAG 2.2 AA** and was audited with Lighthouse plus manual checks; Lighthouse is a baseline, not a certification.

- **No text below 1rem/16px.** Overview values and contact details are set in Noto Serif at readable sizes.
- Body copy has generous line-height and readable measures.
- German compounds use `hyphens: auto`; footer headings are non-breaking; overflow checked at all listed widths in the Latin locales.
- Header: permanent cream, ink text and a hairline; 14px blur; fixed 4.5rem height.
- `:focus-visible`: 2px brass outline, 4px offset. Skip link moves focus to `main`.
- Minimum **44px** targets for nav, buttons, language and footer links.
- Native `<dialog>` menu with `showModal()`, Escape, backdrop click, focus restoration.
- Lightbox: arrow keys, Escape, focus return, labelled prev/next.
- Film dialog: native controls, labelled close.
- `prefers-reduced-motion` disables animation, transitions and smooth scroll.
- Semantic landmarks/headings; one H1 per page (the property name in the video section); correct `<html lang>`; localized alt text; descriptive map alt and OSM attribution.
- Arabic pages set `dir="rtl"` and keep logical reading order; CJK/Hindi pages declare the correct language subtag.
- Known limits: published VTT captions are English in every locale (the standalone French export has French VTT); the reported areas, rooms and 1783 date still require documentary verification, and the bathroom schedule and floor count are unconfirmed; noindex is not privacy; the new translations should receive a native-speaker review before launch.

## 5. Internationalisation

| Language | URL | `lang` | Speakers (total, Ethnologue 2026) |
| --- | --- | --- | ---: |
| English | `/` | `en` | ~1,493M |
| Chinese (Mandarin, Simplified) | `/zh/` | `zh-CN` | ~1,183M |
| Hindi | `/hi/` | `hi` | ~611M |
| Spanish | `/es/` | `es` | ~561M |
| Arabic (Modern Standard) | `/ar/` | `ar` | ~335M |
| French | `/fr/` | `fr` | ~334M |
| Portuguese | `/pt/` | `pt` | ~269M |
| Russian | `/ru/` | `ru` | ~210M |
| German | `/de/` | `de` | ~133M |
| Japanese | `/ja/` | `ja` | ~126M |
| Italian | `/it/` | `it` | ~66M |

The language selector is sorted by **total number of speakers worldwide**, using the Ethnologue 2026 estimates summarised in [Wikipedia’s list of languages by total number of speakers](https://en.wikipedia.org/wiki/List_of_languages_by_total_number_of_speakers). Arabic and French are effectively tied (335M vs 334M); the table follows the published order. Counts are estimates, not exact census figures. The selector codes are `EN · ZH · HI · ES · AR · FR · PT · RU · DE · JA · IT`.

Every locale has localized copy, navigation, Overview, contact copy, footer, title/description, OG/Twitter metadata, JSON-LD (`inLanguage`, descriptions, amenity names, image captions), gallery captions and the prefilled dossier mailto, plus hreflang alternates including `x-default`.

The gallery count and filter counts use locale-aware plural forms: Arabic (1 / 2 / 3–10 / 11+), Russian (1 / 2–4 / 5+), Hindi (1 / plural), and invariant forms for Chinese and Japanese.

## 6. SEO, canonical URLs and indexing

Pages include canonical URLs, OG/Twitter cards, JSON-LD (`Organization`, `WebSite`, `WebPage`, `Place`, `BreadcrumbList`), hreflang, descriptive metadata and image alt text.

- **Current base URL:** `https://fernangz.github.io/palaciobelavista.com`
- **Current canonical URLs:** root `/`, locale `/{code}/`.
- `hreflang` alternates use the same 11 URLs, with `x-default` pointing at the English root.
- `og:url`, `og:image`, Twitter image and all JSON-LD URLs use the same GitHub Pages base.
- When the final domain is connected, replace the base in all 11 pages and in JSON-LD (canonical, hreflang, OG, Twitter, schema). A project-wide search for `https://fernangz.github.io/palaciobelavista.com` is the complete checklist.

**Indexing is intentionally disabled:** `robots.txt` disallows all; every page has `noindex, nofollow, noarchive, nosnippet, noimageindex`; explicit googlebot/bingbot meta; `X-Robots-Tag` in `_headers`/`vercel.json`; sitemap absent. To re-enable: allow crawlers, replace noindex on all eleven pages, remove `X-Robots-Tag`, and restore a sitemap.

## 7. Last-modified metadata

Every page carries a visible-to-machines timestamp in the head:

```html
<meta name="lastmod" content="2026-11-21T12:54:00+01:00">
```

- It records the **publish time of the current push**, in ISO 8601 with the `Europe/Lisbon` offset.
- It is not generated automatically. Update it on every publish, ideally to the commit/push time, and keep all eleven pages in sync.
- GitHub Pages also returns its own `last-modified` response header. The meta tag is for page-level metadata; the header reflects the deployed file.
- JSON-LD `dateModified` is set to the same calendar date.

## 8. Lighthouse results

Final **pre-noindex, pre-restructure** audit (Chrome 142, Lighthouse 13.6, mobile emulation, `--disable-gpu`), on the six-locale version:

| Category | Mobile | Desktop |
| --- | ---: | ---: |
| Performance | **100** | **100** |
| Accessibility | **100** | **100** |
| Best practices | **100** | **100** |
| SEO | **100** | **100** |

| Metric | Mobile | Desktop |
| --- | ---: | ---: |
| FCP | 1.1 s | 0.3 s |
| LCP | 1.1 s | 0.3 s |
| TBT | 20 ms | 0 ms |
| CLS | 0 | 0.015 |
| Speed Index | 1.1 s | — |

The eleven-locale, folder-based version has **not** been re-audited. The new pages reuse the same CSS, images and JS, but embedded CJK/Devanagari subsets and RTL layout change text metrics and document weight. Re-run Lighthouse on at least `/`, `/fr/`, `/ar/`, `/ja/` and `/hi/` before launch. A fresh SEO run may flag `is-crawlable` because noindex is intentional.

Reproduce:

```bash
npx lighthouse https://fernangz.github.io/palaciobelavista.com/ \
  --chrome-flags="--headless=new --no-sandbox --disable-gpu" \
  --output=html --output-path=./lighthouse-mobile.html
npx lighthouse https://fernangz.github.io/palaciobelavista.com/ \
  --preset=desktop \
  --chrome-flags="--headless=new --no-sandbox --disable-gpu" \
  --output=html --output-path=./lighthouse-desktop.html
```

**Improvements retained:** responsive AVIF/WebP/JPEG with dimensions; poster/image preload where useful; inline subset fonts; static OSM (no iframe); click-to-load film; single small vanilla JS; no analytics/third-party; removed reveal/clip effects and `content-visibility`; stable aspect ratios; reduced TBT/CLS. On macOS headless, `--disable-gpu` avoids a spurious GPU-teardown long task.

## 9. Assets

- 25 gallery photographs in AVIF/WebP/JPEG at multiple widths; responsive gallery sets.
- Watermarked sources cleaned by quiet-area seam-crop/blend; originals left outside this repo.
- Film `assets/video/palacio-belavista.mp4`, 42 s H.264 fast-start; 1:1 entrance-hall poster in AVIF/WebP/JPEG; `palacio-belavista-en.vtt`.
- Static OSM-derived antique area map in JPEG at three widths; no pin; OSM attribution.
- OG card `assets/img/og-image.jpg` (1200×630) in the postcard system with the supplied emblem; simplified favicons and PWA icons.
- Postcard QR `qr/palacio-belavista-play-qr.svg` (1200×1200 SVG, cream/ink/brass) pointing to `https://palaciobelavista.com/?play`.
- Fonts are embedded as subsets; `FONT-LICENSES.md` records the Noto licences.
- Unused wide hero image variants and the duplicate `favicon-48.png` were removed after the page restructure; the remaining asset set is fully referenced. The supplied postcard artwork stays outside the published assets.
- Original masters/build pipeline are outside this publishing repo.

## 10. Contact and dossier

There is no contact form and no visible email address. The contact section gives the address, appointment note, small area map and a **Request the full dossier** button. The button is a `mailto:palaciobelavista@gmail.com` link with a prefilled subject and body, localized per page, that asks for more information about the property and the full dossier. No analytics or tracking.

> The email domain depends on `palaciobelavista.com`, which is not yet registered or delegated. Until it is, the mailto link cannot deliver mail even though it opens correctly.

## 11. Deployment

### GitHub Pages, for now

- Source: `main` / repository root; `.nojekyll` present.
- Live: https://fernangz.github.io/palaciobelavista.com/
- Folder URLs `/fr/`, `/ja/`, `/ar/`, etc. are served by GitHub Pages from each `index.html`.
- **Propagation:** after `git push origin main`, GitHub Pages builds the site and the Fastly CDN refreshes. Expect roughly 1–10 minutes. The response header `last-modified` and a hard refresh/incognito window are the reliable checks. `Cache-Control` on HTML is `max-age=600`, so an edge or browser cache can hold the previous page for up to ten minutes after the build.
- `lastmod` is a static meta value, not an automatic deployment signal. Update it when publishing.
- GitHub Pages ignores `_headers` and `vercel.json`; noindex meta + `robots.txt` are the effective controls there. `X-Robots-Tag`, `X-Frame-Options`, `X-Content-Type-Options`, `Referrer-Policy` and `Permissions-Policy` only take effect on a host that reads those files (Netlify/Vercel).
- `CNAME` is absent and no custom domain is configured in Pages yet.

### Moving to the final domain

1. Register `palaciobelavista.com` and configure DNS (GitHub Pages apex A/AAAA records or an ALIAS/ANAME; `www` as a CNAME).
2. Add a `CNAME` file containing `palaciobelavista.com`.
3. Enable the custom domain in the repository’s Pages settings and wait for the TLS certificate.
4. Replace `https://fernangz.github.io/palaciobelavista.com` with `https://palaciobelavista.com` in all eleven pages: canonical, hreflang, `og:url`, `og:image`, Twitter image, JSON-LD URLs and `@id` values.
5. Confirm the Gmail mailbox is monitored, then test the dossier mailto link end-to-end.
6. Re-test old links, the language switcher and the canonical/hreflang set after the domain switch.

## 12. Task recap

1. Audited supplied palace photography/film; selected the gallery set.
2. Removed visible Engel & Völkers watermarks via seam-crop/blend; produced AVIF/WebP/JPEG derivatives.
3. Compressed film to H.264, generated poster and VTT.
4. Art direction: Noto Serif + Noto Sans, cream/ink/brass, mobile-first editorial layout.
5. Built the original editorial sections: hero, palace, architecture, interiors, craft, garden, film, gallery, private viewings, map, FAQ and form.
6. Gallery: masonry/carousel, filters, hover light, lightbox, keyboard/swipe, responsive variants.
7. Film: poster/play treatment, native video dialog, captions.
8. Replaced Google Maps with a static OSM plan, brass pin and attribution.
9. Form: accessible fields, consent, honeypot, mailto fallback/static endpoint (later removed in favour of the dossier mailto).
10. SEO: canonical, OG/Twitter, JSON-LD, image metadata, hreflang, sitemap.
11. Accessibility: 16px floor, contrast, 44px targets, skip link, focus, landmarks, keyboard dialogs, reduced motion.
12. Header: permanent cream over the postcard cover; hairline rule; fixed compact height.
13. Added French, Portuguese, Spanish, German and Italian with localized metadata/JSON-LD/switchers.
14. Responsive fixes: tablet footer, German hyphenation, no overflow, localized counts/hints.
15. Performance: inline fonts, optimized images, deferred JS, static map, no third-party; Lighthouse 100s.
16. Renamed Boavista → Belavista → **Palacio Bela Vista**, including social card/schema/translations. The domain, repository and email retain the compact `palaciobelavista.com` form because DNS names and local-parts cannot contain spaces.
17. Produced a single-file French export with images/film/captions/fonts/map/icons embedded (kept outside this publishing repo).
18. Full-page desktop/mobile screenshots stitched to avoid Chrome’s 16k duplication.
19. Moved only the final site contents into this repo; committed and pushed.
20. Disallowed all crawlers, added noindex to every page, removed the sitemap, enabled GitHub Pages.
21. Moved every locale from root `xx.html` to `xx/index.html`; updated assets, JS, favicons, manifest, canonicals and hreflang.
22. Added Japanese, Simplified Chinese, Arabic, Russian and Hindi pages with localized metadata, body copy, gallery captions, contact copy and JSON-LD.
23. Sorted the language selector by total speakers (Ethnologue 2026): EN, ZH, HI, ES, AR, FR, PT, RU, DE, JA, IT.
24. Added RTL layout support and script-specific Noto fonts for Arabic, CJK, Devanagari and Cyrillic.
25. Added `<meta name="lastmod">` to every page and documented the GitHub Pages propagation window and eventual custom-domain migration.
26. Switched the whole site to Noto Serif + Noto Sans, with script-specific Noto faces and regenerated subsets for all eleven locales and the OG card.
27. Restructured every locale into Header → Video → Gallery → Property identity → Characteristics → Craft → FAQs → Contact → Footer; removed the form and added the localized full-dossier mailto.
28. Removed unused wide hero image variants and `favicon-48.png`, and rechecked every remaining asset against the published references.
29. Implemented the postcard design system: engraved emblem, cream split panels, serif body copy, brass rules, two-line wordmark, “Private residence available to purchase”, and a dark gallery/footer contrast.
30. Added the `/?play` postcard QR deep link and regenerated the OG card and favicons in the postcard system.
31. Updated the property facts from dossier v04: 1,036.68 m² reported area, 488.49 m² plot, 25 rooms, 12 bedrooms, 1783, garden and two terraces, price upon request; documented the unconfirmed bathroom schedule and floor count.
32. Replaced the portrait video poster with a 1:1 entrance-hall crop and redesigned the play control as a cream-and-brass editorial plaque; on mobile the poster now leads the cover.
33. Removed the scroll-driven header state so the navigation and menu control keep the same height and treatment from first paint.
34. Added a selection and cursor policy: UI chrome/media are non-selectable, body copy stays selectable, and interactive elements carry pointer, zoom-in or disabled cursors.
35. Applied the confirmed review: Video → Gallery → Overview → Contact; removed Property, Craft and FAQ; removed gallery filters/count; replaced the mark with the supplied SVG emblem; moved the map to Contact as an antique area view without a pin; removed visible email, coordinates and price; switched mailto to `palaciobelavista@gmail.com`; simplified the footer and kept all eleven languages.

## 13. Credits

Photography/film from the palace archive. **Noto Serif**, **Noto Sans** and the script-specific Noto families under SIL OFL; see `FONT-LICENSES.md`. Map data © OpenStreetMap contributors, ODbL. No third-party analytics/advertising/cookies/tracking. Website copy, photography and film remain property of Palacio Bela Vista; code not licensed for reuse without permission.
