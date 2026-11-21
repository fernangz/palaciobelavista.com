# Palacio Bela Vista

Static website for **Palacio Bela Vista**, a Pombaline palace at **Rua do Ataíde 9, 1200-034 Lisboa**, parish of Misericórdia.

- **Live for now:** https://fernangz.github.io/palaciobelavista.com/
- **Repository:** https://github.com/fernangz/palaciobelavista.com
- **Final domain (pending):** https://palaciobelavista.com
- **Enquiries:** enquiries@palaciobelavista.com

> The public name is **Palacio Bela Vista** (two words). The domain, repository and email address keep the compact `palaciobelavista.com` form; the video and VTT filenames also keep the hyphenated form.

> **Hosting note.** The site is published on GitHub Pages at the repository URL while the final domain is arranged. GitHub Pages deploys after a push to `main`; the build and CDN usually update within 1–10 minutes, occasionally longer. A hard refresh or a fresh `curl -I` is the quickest way to confirm the new `last-modified` header. Canonical, hreflang, Open Graph and JSON-LD URLs currently use the GitHub Pages address, not the future domain.
>
> **Indexing is disabled.** `robots.txt` disallows all crawlers, every page has `noindex`, and `sitemap.xml` is absent. This is not access control: the GitHub Pages site and the repository are still public.

## 1. Project overview

A private Pombaline residence in Lisbon, presented through architecture, interiors, craft, garden, film and a 25-image gallery, with a quiet private-viewing and dossier enquiry flow.

| Field | Value |
| --- | --- |
| Name | Palacio Bela Vista |
| Street | Rua do Ataíde 9 |
| Postal code | 1200-034 |
| City / parish | Lisboa / Misericórdia |
| Country | Portugal |
| Coordinates | 38.7086386, -9.1443863 |
| Email | enquiries@palaciobelavista.com |

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

app.js                      Menu, filters, lightbox, film, form
assets/img/                 Responsive AVIF/WebP/JPEG, map, icons, OG card
assets/video/               Film, poster, English VTT
favicons, site.webmanifest, robots.txt, _headers, vercel.json, .nojekyll
README.md
FONT-LICENSES.md
```

- **URLs:** `/` (English), `/fr/`, `/pt/`, `/es/`, `/de/`, `/it/`, `/ja/`, `/zh/`, `/ar/`, `/ru/`, `/hi/`.
- The old `/fr.html`, `/pt.html`, `/es.html`, `/de.html` and `/it.html` URLs were removed, not redirected. GitHub Pages serves `folder/index.html` at the folder URL; there is no server-side redirect layer.
- CSS is inlined in each HTML page; Noto Serif, Noto Sans and the script-specific Noto WOFF2 subsets are inlined as base64. Source masters and build scripts live outside this publishing repo.
- Local preview: `python3 -m http.server 8000`, then open `http://127.0.0.1:8000/`, `http://127.0.0.1:8000/fr/`, and so on. Opening a locale folder directly from disk also works, but a local server is closer to production.

## 3. Design decisions

### Direction

- **Private residence, not a hotel or estate listing.** No price panels, badges, stock photography or glossy marketing cards; the house is the subject.
- **Editorial, quiet, confident.** Generous white space, thin rules, muted colour, a few strong typographic moments. Gold is an accent, never a wash.
- **One atmosphere, changing temperature.** Ivory reading sections, ink “rooms” for architecture/gallery/film, dark footer.
- **Craft in the interface.** Precise spacing, letter-spaced labels, fine borders and a custom PB monogram instead of generic UI chrome.

### Typography

| Role | Typeface | Treatment |
| --- | --- | --- |
| Display | **Noto Serif** | High-contrast editorial serif; tight leading; italic emphasis |
| Body/UI | **Noto Sans** | Neutral humanist sans; light prose, medium labels |
| Labels | Noto Sans | Uppercase, 1rem, wide tracking, gold |
| Navigation/buttons | Noto Sans | Uppercase, 1rem, tracked, thin rules |

- Noto Serif + Noto Sans were chosen for complete script coverage and a coherent editorial voice across all eleven languages; the serif keeps old-house authority, while the sans keeps labels quiet and legible.
- Hero H1: `clamp(4.1rem, 12.5vw, 11.6rem)`; section H2s use fluid clamps up to 7rem.
- Body: `1.0625rem` mobile, `1.09rem` desktop, 1.7 line-height.
- **Every label, caption, nav item, form hint and footer line has a 1rem/16px floor.**
- FAQ questions are `clamp(1.25rem, 2.2vw, 1.7rem)`; answers are `1.0625rem`.
- Italic display words carry emotion: “light”, “many lights”, “instrument”.
- Menu/gallery numerals use tracked Noto Sans as editorial folios, not UI counters.
- **Script coverage:** Noto Serif and Noto Sans carry Latin and Cyrillic, so Russian uses the same serif/sans pairing as the Latin pages, with Cyrillic glyphs included in the embedded subsets.
- All pages use the same two CSS families, `Noto Serif` and `Noto Sans`. Script-specific faces are registered under those same family names with `unicode-range`, so there are no per-language font stacks or duplicated font-family rules.
- Japanese, Simplified Chinese, Arabic and Hindi use embedded Noto faces, subset to the characters actually used on that page:
  - Japanese: Noto Serif JP 400 for display; variable Noto Sans JP for body and labels.
  - Chinese: Noto Serif SC 400 for display; variable Noto Sans SC for body and labels.
  - Arabic: Noto Naskh Arabic 400 for display; variable Noto Sans Arabic for body and labels.
  - Hindi: Noto Serif Devanagari 400 for display; variable Noto Sans Devanagari for body and labels.
- Every page also embeds tiny native-name subsets for `中文`, `हिन्दी`, `العربية`, `Русский`, `日本語` plus arrow and prime subsets, all registered as additional `Noto Sans` faces with exact `unicode-range` values. The language list therefore renders consistently without a separate CSS class.
- Local system fonts remain as a final fallback, but they are no longer the primary source for any script.
- No external font request is introduced: all faces are inline WOFF2 data URIs. The trade-off is page weight — Japanese, Chinese and Hindi pages are roughly 0.5–0.6 MB of HTML (Chinese just over 0.6 MB) because the embedded subsets are larger.
- Font licences and copyright notices are in `FONT-LICENSES.md`.

### Colour tokens

| Token | Value | Use |
| --- | --- | --- |
| `--ink` | `#11150f` | Gallery, film, footer, buttons |
| `--ink-2` | `#1a2018` | Image placeholders |
| `--forest` | `#1d2a21` | Deep green support |
| `--paper` | `#f2ece1` | Primary light background |
| `--paper-2` | `#e9e1d3` | Map/form/alternating sections |
| `--stone` | `#e2d8c7` | Warm neutral support |
| `--gold` | `#b08a4f` | Primary accent |
| `--gold-2` | `#d6b77e` | Accent on dark |
| `--gold-deep` | `#7a5a29` | Accessible gold text on paper |
| `--wine` | `#6a2228` | Rare editorial accent |
| `--text` | `#34362d` | Body copy |
| `--muted` | `#5c574d` | Secondary copy |

- Gold-deep for labels on ivory; gold-2 on ink for contrast. Ivory-on-ink is the primary pairing.
- No pure black/white: darkest is green-black ink, lightest is warm paper.
- Section colour changes are structural: light reading, dark rooms, dark footer.

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
| `< 22rem` | Wordmark hidden; PB monogram remains |
| `36rem` | 2-column form rows; gallery 2 columns; facts 3 columns |
| `48rem` | Editorial grids; chapter layouts; 2-column footer |
| `68rem` | Full desktop nav + header CTA; gallery 3 columns |
| `90rem` | 3-column footer; maximum hero scale |

- Navigation enters the full-screen menu below 68rem; it never wraps or crowds on tablets.
- Footer stays 2-column until 90rem so translated labels fit.
- Gallery: 3-column masonry desktop, 2-column tablet, snap carousel mobile.
- Buttons use `0.12em` tracking at 16px to avoid unnecessary wrapping.
- German compounds hyphenate; footer headings are non-breaking.
- No horizontal overflow at 320, 360, 390, 412, 768, 960, 1024, 1280 or 1440px in the Latin locales.
- Arabic is RTL: the page sets `dir="rtl"`, mirrors flex/margin direction, flips the gallery filter fade, select arrow, lightbox arrows, film label and decorative PB watermark, and disables letter-spacing for connected Arabic script. Arabic line-height is increased to 1.95.
- CJK and Devanagari body line-height is increased to 1.85–1.9 for readability.

### Header and menu

- Header transparent over hero; after 48px it becomes **dark frosted glass**: ink gradient, 18px blur, ivory text, gold monogram border.
- Fixed header is shallow; a scroll-padding offset keeps anchors clear; state restores on reload/direct anchors.
- Desktop nav is five quiet links; enquiry CTA is a thin outlined rectangle, not a filled sales button.
- Mobile uses a two-line toggle and full-screen dialog, not a cramped drawer.
- Menu is 85% ink with 22px blur, numbered 01–08, Noto Serif links, contact and language switcher at the foot. Native `showModal()`, Escape, backdrop click and focus return.

### Hero and narrative

- Full-viewport atrium image, dark shade, two-line H1: “Palacio” roman / “Bela Vista” italic.
- Address in a small translucent label; short lede; two actions; bottom rail with coordinates, building rhythm and scroll cue.
- Image focal point 38% vertical keeps the lantern visible under the headline. No autoplay video or carousel.
- Page order: Hero → Palace → Architecture → Interiors → Craft → Garden & river → Film → Gallery → Private viewings → Find us → FAQ → Request dossier → Footer.
- Commercial content is deliberately deferred until after the house has been shown; FAQ sits immediately before the enquiry.

### Photography, gallery and lightbox

- Only palace photography; no stock. Crops favour symmetry, doorways, ceiling roundels and garden depth; natural colour, no heavy filters.
- Images alternate full-bleed, framed editorial plates and tall portraits; explicit dimensions and responsive AVIF/WebP/JPEG.
- Hero `fetchpriority="high"`; below-fold images native lazy; map desaturated so the gold pin/card carry colour.
- Visible Engel & Völkers watermarks were removed by seam-cropping quiet areas and blending, not painting over architecture.
- Gallery: 3-column masonry desktop, 2-column tablet, 84%-viewport snap carousel mobile. Filters: All, Architecture, Interiors, Craft, Garden, Lisbon.
- Hover/focus: soft gold radial light + thin inset frame; captions over a bottom gradient.
- Lightbox: near-black blurred backdrop, large image, title/category, count, arrows, keyboard/swipe, no thumbnail strip; selects a viewport-appropriate variant instead of upscaling.

### Film, plan and map

- Film presented as a framed portrait poster with circular play control; never autoplays; opens a native-control dialog with captions. Runtime 42 seconds.
- Architecture plan is a custom reduced line drawing. Tiny SVG labels were removed for the 16px floor; the caption explains three storeys to the street and four to the garden.
- Map is a **static OSM image**, not an iframe: no cookies, no third-party JS, desaturated basemap, gold HTML pin, address/coordinates/metro card and visible OSM attribution. Google Maps removed.

### Form, footer and languages

- Form: two-column editorial layout on desktop, stacked mobile; underlined fields; uppercase gold labels; name/email, phone/interest, message, consent, dark rectangular submit.
- Short form by design: the dossier is the offer. Native validation, labels, consent, honeypot; mailto fallback or optional static endpoint; `aria-live` status with direct email fallback.
- The email subject uses the page’s localized hidden `_subject` value, so the mail subject follows the page language.
- Footer: dark ink, oversized Noto Serif wordmark, italic gold “Bela Vista”; Visit/Discover/Contact columns.
- Language switcher in footer and menu, not header: visible two-letter codes, native-language accessible names, active gold rule. It now lists eleven languages in speaker order.
- Back-to-top is a plain text arrow link, not a floating button.

### Motion and performance trade-offs

- Restrained motion: image scale, gold gallery light, dialog fades, arrow shifts. No scroll reveals, parallax or clip-path entrances.
- Scroll reveals were removed because they delayed LCP, blocked native lazy loading and caused ghosting.
- Anchor navigation is instant; `prefers-reduced-motion` disables transitions/animations/smooth scrolling.
- Fonts inlined as per-script subset WOFF2 data URIs; critical CSS inlined; one deferred vanilla JS file; no framework hydration.
- Map is an image; film is click-to-load; no third-party requests.
- Section `content-visibility` was removed because placeholder heights caused anchor/layout jumps at tablet widths.
- Explicit image dimensions/aspect ratios prevent CLS.
- The new locale pages reuse the same CSS, imagery and JS; they add no network requests beyond the shared page assets. The embedded CJK/Devanagari subsets make those HTML files heavier, but they are cached as part of the document.

### Accessibility-driven visual decisions

- The 16px floor changed the scale: labels, captions and nav are larger and the layout was re-spaced around them.
- Header became dark frosted glass rather than pale translucent paper so it always contrasts with content beneath.
- Language switchers moved out of the header so 16px labels would not crowd primary navigation.
- Footer reflows earlier; German compounds hyphenate; long email addresses wrap safely.
- Icon-only controls have accessible names; text controls stay text; gold is darkened to gold-deep on light paper.
- New locales translate `alt`, `aria-label`, lightbox titles/captions, gallery category labels, form messages and the film close controls.
- Arabic keeps native RTL reading order; focus order follows the DOM.

### Rejected directions

- Google Maps iframe/embed — privacy, performance, visual control.
- Third-party fonts, analytics, heatmaps, cookie banner, chat widget — omitted entirely.
- Autoplaying hero video — performance and tone.
- Scroll-reveal/parallax and section `content-visibility` — LCP, ghosting and layout jumps.
- Tiny 10–12px luxury captions — inaccessible; 16px floor.
- Header language dropdown — moved to menu/footer.
- Rounded pills, heavy cards, drop shadows — replaced by thin rules, flat planes, editorial type.
- Stock palace imagery — replaced by photography of the actual house.
- `.html` locale files at the root — replaced by folder URLs with `index.html`.

## 4. Accessibility specification

The site targets **WCAG 2.2 AA** and was audited with Lighthouse plus manual checks; Lighthouse is a baseline, not a certification.

- **No text below 1rem/16px.** FAQ questions are larger; answers are `1.0625rem`.
- Body copy has generous line-height and readable measures.
- German compounds use `hyphens: auto`; footer headings are non-breaking; overflow checked at all listed widths in the Latin locales.
- Header: transparent over hero, dark frosted glass on scroll; ivory-on-dark composite with gold accent; 18px blur.
- `:focus-visible`: 2px gold outline, 4px offset. Skip link moves focus to `main`.
- Minimum **44px** targets for nav, buttons, form controls, language and footer links.
- Native `<dialog>` menu with `showModal()`, Escape, backdrop click, focus restoration.
- Lightbox: arrow keys, Escape, focus return, labelled prev/next.
- Film dialog: native controls, labelled close.
- `prefers-reduced-motion` disables animation, transitions and smooth scroll.
- `aria-live` form status; labelled fields; required name/email/message/consent; consent not pre-checked; honeypot.
- Form never claims to send when it opens mail; status explains and gives the direct email.
- Semantic landmarks/headings; one H1 per page; correct `<html lang>`; localized alt text; descriptive map alt and OSM attribution.
- Arabic pages set `dir="rtl"` and keep logical reading order; CJK/Hindi pages declare the correct language subtag.
- Known limits: published VTT captions are English in every locale (the standalone French export has French VTT); no backend validation; noindex is not privacy; the new translations should receive a native-speaker review before launch.

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

Every locale has localized copy, navigation, form labels/options, FAQ, footer, title/description, OG/Twitter metadata, JSON-LD (`inLanguage`, descriptions, FAQ, amenity names, image captions), gallery captions/categories, form status messages and mail subject, plus hreflang alternates including `x-default`.

The gallery count and filter counts use locale-aware plural forms: Arabic (1 / 2 / 3–10 / 11+), Russian (1 / 2–4 / 5+), Hindi (1 / plural), and invariant forms for Chinese and Japanese.

## 6. SEO, canonical URLs and indexing

Pages include canonical URLs, OG/Twitter cards, JSON-LD (`Organization`, `WebSite`, `WebPage`, `Place`, `FAQPage`, `BreadcrumbList`), hreflang, descriptive metadata and image alt text.

- **Current base URL:** `https://fernangz.github.io/palaciobelavista.com`
- **Current canonical URLs:** root `/`, locale `/{code}/`.
- `hreflang` alternates use the same 11 URLs, with `x-default` pointing at the English root.
- `og:url`, `og:image`, Twitter image and all JSON-LD URLs use the same GitHub Pages base.
- When the final domain is connected, replace the base in all 11 pages and in JSON-LD (canonical, hreflang, OG, Twitter, schema). A project-wide search for `https://fernangz.github.io/palaciobelavista.com` is the complete checklist.

**Indexing is intentionally disabled:** `robots.txt` disallows all; every page has `noindex, nofollow, noarchive, nosnippet, noimageindex`; explicit googlebot/bingbot meta; `X-Robots-Tag` in `_headers`/`vercel.json`; sitemap absent. To re-enable: allow crawlers, replace noindex on all eleven pages, remove `X-Robots-Tag`, and restore a sitemap.

## 7. Last-modified metadata

Every page carries a visible-to-machines timestamp in the head:

```html
<meta name="lastmod" content="2026-11-21T12:13:00+01:00">
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

**Improvements retained:** responsive AVIF/WebP/JPEG with dimensions; hero preload/fetchpriority; inline subset fonts; static OSM (no iframe); click-to-load film; single small vanilla JS; no analytics/third-party; removed reveal/clip effects and `content-visibility`; stable aspect ratios; reduced TBT/CLS. On macOS headless, `--disable-gpu` avoids a spurious GPU-teardown long task.

## 9. Assets

- 25 gallery photographs in AVIF/WebP/JPEG at multiple widths; responsive hero and architectural sets.
- Watermarked sources cleaned by quiet-area seam-crop/blend; originals left outside this repo.
- Film `assets/video/palacio-belavista.mp4`, 42 s H.264 fast-start; poster; `palacio-belavista-en.vtt`.
- Static OSM map; gold HTML pin; OSM attribution.
- OG card `assets/img/og-image.jpg` (1200×630); PB monogram favicons.
- Fonts are embedded as subsets; `FONT-LICENSES.md` records the Noto licences.
- Original masters/build pipeline are outside this publishing repo.

## 10. Contact form

Default opens the visitor’s mail app to `enquiries@palaciobelavista.com`. Optional static endpoint via `data-endpoint` + `app.js` (Formspree/FormSubmit); no server/secrets. Honeypot `company`/`_gotcha`; provider spam controls if used. No analytics/tracking. Test an endpoint after configuring it; published copy uses mailto.

> The email domain depends on `palaciobelavista.com`, which is not yet registered or delegated. Until it is, the mailto path cannot deliver mail even though the form works as designed.

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
5. Set up MX/mail for `enquiries@palaciobelavista.com` (or change the published address), then test the form end-to-end.
6. Re-test old links, the language switcher and the canonical/hreflang set after the domain switch.

## 12. Task recap

1. Audited supplied palace photography/film; selected the gallery set.
2. Removed visible Engel & Völkers watermarks via seam-crop/blend; produced AVIF/WebP/JPEG derivatives.
3. Compressed film to H.264, generated poster and VTT.
4. Art direction: Noto Serif + Noto Sans, ivory/ink/gold, mobile-first editorial layout.
5. Built hero, palace, architecture, interiors, craft, garden, film, gallery, private viewings, map, FAQ and form.
6. Gallery: masonry/carousel, filters, hover light, lightbox, keyboard/swipe, responsive variants.
7. Film: poster/play treatment, native video dialog, captions.
8. Replaced Google Maps with a static OSM plan, gold pin and attribution.
9. Form: accessible fields, consent, honeypot, mailto fallback/static endpoint.
10. SEO: canonical, OG/Twitter, JSON-LD, image metadata, hreflang, sitemap.
11. Accessibility: 16px floor, contrast, 44px targets, skip link, focus, landmarks, keyboard dialogs, reduced motion.
12. Header: transparent hero state; dark frosted glass on scroll.
13. Added French, Portuguese, Spanish, German and Italian with localized metadata/JSON-LD/switchers.
14. Responsive fixes: tablet footer, German hyphenation, no overflow, localized counts/hints.
15. Performance: inline fonts, optimized images, deferred JS, static map, no third-party; Lighthouse 100s.
16. Renamed Boavista → Belavista → **Palacio Bela Vista**, including social card/schema/translations. The domain, repository and email retain the compact `palaciobelavista.com` form because DNS names and local-parts cannot contain spaces.
17. Produced a single-file French export with images/film/captions/fonts/map/icons embedded (kept outside this publishing repo).
18. Full-page desktop/mobile screenshots stitched to avoid Chrome’s 16k duplication.
19. Moved only the final site contents into this repo; committed and pushed.
20. Disallowed all crawlers, added noindex to every page, removed the sitemap, enabled GitHub Pages.
21. Moved every locale from root `xx.html` to `xx/index.html`; updated assets, JS, favicons, manifest, canonicals and hreflang.
22. Added Japanese, Simplified Chinese, Arabic, Russian and Hindi pages with localized metadata, body copy, gallery captions, form messages and JSON-LD.
23. Sorted the language selector by total speakers (Ethnologue 2026): EN, ZH, HI, ES, AR, FR, PT, RU, DE, JA, IT.
24. Added RTL layout support and script-specific Noto fonts for Arabic, CJK, Devanagari and Cyrillic.
25. Added `<meta name="lastmod">` to every page and documented the GitHub Pages propagation window and eventual custom-domain migration.
26. Switched the whole site to Noto Serif + Noto Sans, with script-specific Noto faces and regenerated subsets for all eleven locales and the OG card.

## 13. Credits

Photography/film from the palace archive. **Noto Serif**, **Noto Sans** and the script-specific Noto families under SIL OFL; see `FONT-LICENSES.md`. Map data © OpenStreetMap contributors, ODbL. No third-party analytics/advertising/cookies/tracking. Website copy, photography and film remain property of Palacio Bela Vista; code not licensed for reuse without permission.
