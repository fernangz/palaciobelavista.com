# Palacio Belavista
Static website for **Palacio Belavista**, a Pombaline palace at **Rua do Ataíde 9, 1200-034 Lisboa**, parish of Misericórdia.
- **Live:** https://fernangz.github.io/palaciobelavista.com/
- **Repository:** https://github.com/fernangz/palaciobelavista.com
- **Canonical domain (DNS pending):** https://palaciobelavista.com
- **Enquiries:** enquiries@palaciobelavista.com
> **Indexing is disabled.** `robots.txt` disallows all crawlers, every page has `noindex`, and `sitemap.xml` is removed. This is not access control: the GitHub Pages site is still public.
## 1. Project overview
A private Pombaline residence in Lisbon, presented through architecture, interiors, craft, garden, film and a 25-image gallery, with a quiet private-viewing and dossier enquiry flow.

| Field | Value |
| --- | --- |
| Name | Palacio Belavista |
| Street | Rua do Ataíde 9 |
| Postal code | 1200-034 |
| City / parish | Lisboa / Misericórdia |
| Country | Portugal |
| Coordinates | 38.7086386, -9.1443863 |
| Email | enquiries@palaciobelavista.com |
The Google Maps link was removed. Location links point to OpenStreetMap; the map is a static, cookie-free image with OSM attribution.
## 2. Repository contents
This repo contains the **published static site only**, at the root.
```text
index.html                  English
fr.html / pt.html / es.html French / Portuguese / Spanish
de.html / it.html           German / Italian
app.js                      Menu, filters, lightbox, film
assets/img/                 Responsive AVIF/WebP/JPEG, map, icons, OG card
assets/video/               Film, poster, English VTT
favicons, site.webmanifest, robots.txt, _headers, vercel.json, .nojekyll
```
CSS is inlined in each HTML page; fonts are inlined as base64 WOFF2. Source masters/build scripts live outside this publishing repo.
Local preview: `python3 -m http.server 8000` then open `http://127.0.0.1:8000/`. Opening `index.html` directly also works. GitHub Pages serves `.html` links; clean `/fr` URLs were a development-server convenience, not part of this deployment.
## 3. Design decisions
### Direction
- **Private residence, not a hotel or estate listing.** No price panels, badges, stock photography or glossy marketing cards; the house is the subject.
- **Editorial, quiet, confident.** Generous white space, thin rules, muted colour, a few strong typographic moments. Gold is an accent, never a wash.
- **One atmosphere, changing temperature.** Ivory reading sections, ink “rooms” for architecture/gallery/film, dark footer.
- **Craft in the interface.** Precise spacing, letter-spaced labels, fine borders and a custom PB monogram instead of generic UI chrome.
### Typography
| Role | Typeface | Treatment |
| --- | --- | --- |
| Display | **Prata** | Uncommon high-contrast serif; tight leading; italic emphasis |
| Body/UI | **Jost** | Geometric sans; light prose, medium labels |
| Labels | Jost | Uppercase, 1rem, wide tracking, gold |
| Navigation/buttons | Jost | Uppercase, 1rem, tracked, thin rules |
- Prata was chosen over ubiquitous luxury serifs (Playfair, Didot) for distinctiveness and old-house authority.
- Hero H1: `clamp(4.1rem, 12.5vw, 11.6rem)`; section H2s use fluid clamps up to 7rem.
- Body: `1.0625rem` mobile, `1.09rem` desktop, 1.7 line-height.
- **Every label, caption, nav item, form hint and footer line has a 1rem/16px floor.**
- FAQ questions are `clamp(1.25rem, 2.2vw, 1.7rem)`; answers `1.0625rem`.
- Italic display words carry emotion: “light”, “many lights”, “instrument”.
- Menu/gallery numerals use tracked Jost as editorial folios, not UI counters.
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
- Asymmetric editorial grids; section intros split large serif heading + short standfirst.
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
- No horizontal overflow at 320, 360, 390, 412, 768, 960, 1024, 1280 or 1440px.
### Header and menu
- Header transparent over hero; after 48px it becomes **dark frosted glass**: ink gradient, 18px blur, ivory text, gold monogram border.
- Fixed header is shallow; a scroll-padding offset keeps anchors clear; state restores on reload/direct anchors.
- Desktop nav is five quiet links; enquiry CTA is a thin outlined rectangle, not a filled sales button.
- Mobile uses a two-line toggle and full-screen dialog, not a cramped drawer.
- Menu is 85% ink with 22px blur, numbered 01–08, Prata links, contact and language switcher at the foot. Native `showModal()`, Escape, backdrop click and focus return.
### Hero and narrative
- Full-viewport atrium image, dark shade, two-line H1: “Palacio” roman / “Belavista” italic.
- Address in a small translucent label; short lede; two actions; bottom rail with coordinates, building rhythm and scroll cue.
- Image focal point 38% vertical keeps the lantern visible under the headline. No autoplay video or carousel.
- Page order: Hero → Palace → Architecture → Interiors → Craft → Garden & river → Film → Gallery → Private viewings → Find us → FAQ → Request dossier → Footer.
- Commercial content is deliberately deferred until after the house has been shown; FAQ sits immediately before the enquiry.
### Photography, gallery and lightbox
- Only palace photography; no stock. Crops favour symmetry, doorways, ceiling roundels and garden depth; natural colour, no heavy filters.
- Images alternate full-bleed, framed editorial plates and tall portraits; explicit dimensions and responsive AVIF/WebP/JPEG.
- Hero `fetchpriority="high"`; below-fold images native lazy; map desaturated so gold pin/card carry colour.
- Visible Engel & Völkers watermarks were removed by seam-cropping quiet areas and blending, not painting over architecture.
- Gallery: 3-column masonry desktop, 2-column tablet, 84%-viewport snap carousel mobile. Filters: All, Architecture, Interiors, Craft, Garden, Lisbon.
- Hover/focus: soft gold radial light + thin inset frame; captions over a bottom gradient.
- Lightbox: near-black blurred backdrop, large image, title/category, count, arrows, keyboard/swipe, no thumbnail strip; selects a viewport-appropriate variant instead of upscaling.
### Film, plan and map
- Film presented as a framed portrait poster with circular play control; never autoplays; opens a native-control dialog with captions. Runtime 42 seconds.
- Architecture plan is a custom reduced line drawing. Tiny SVG labels were removed for the 16px floor; the caption explains three storeys to the street and four to the garden.
- Map is a **static OSM image**, not an iframe: no cookies, no third-party JS, desaturated basemap, gold HTML pin, address/coordinates/metro card and visible OSM attribution. Google Maps removed.
### Form, footer and languages
- Form: two-column editorial layout desktop, stacked mobile; underlined fields; uppercase gold labels; name/email, phone/interest, message, consent, dark rectangular submit.
- Short form by design: the dossier is the offer. Native validation, labels, consent, honeypot; mailto fallback or optional static endpoint; `aria-live` status with direct email fallback.
- Footer: dark ink, oversized Prata wordmark, italic gold “Belavista”; Visit/Discover/Contact columns.
- Language switcher in footer and menu, not header: visible EN/FR/PT/ES/DE/IT codes, native-language accessible names, active gold rule. Keeps the header quiet.
- Back-to-top is a plain text arrow link, not a floating button.
### Motion and performance trade-offs
- Restrained motion: image scale, gold gallery light, dialog fades, arrow shifts. No scroll reveals, parallax or clip-path entrances.
- Scroll reveals were removed because they delayed LCP, blocked native lazy loading and caused ghosting.
- Anchor navigation is instant; `prefers-reduced-motion` disables transitions/animations/smooth scrolling.
- Fonts inlined as subset WOFF2 data URIs; critical CSS inlined; one deferred vanilla JS file; no framework hydration.
- Map is an image; film is click-to-load; no third-party requests.
- Section `content-visibility` was removed because placeholder heights caused anchor/layout jumps at tablet widths.
- Explicit image dimensions/aspect ratios prevent CLS. The single-file French export uses one JPEG per image to stay practical.
### Accessibility-driven visual decisions
- The 16px floor changed the scale: labels, captions and nav are larger and the layout was re-spaced around them.
- Header became dark frosted glass rather than pale translucent paper so it always contrasts with content beneath.
- Language switchers moved out of the header so 16px labels would not crowd primary navigation.
- Footer reflows earlier; German compounds hyphenate; long email addresses wrap safely.
- Icon-only controls have accessible names; text controls stay text; gold is darkened to gold-deep on light paper.
### Rejected directions
- Google Maps iframe/embed — privacy, performance, visual control.
- Third-party fonts, analytics, heatmaps, cookie banner, chat widget — omitted entirely.
- Autoplaying hero video — performance and tone.
- Scroll-reveal/parallax and section `content-visibility` — LCP, ghosting and layout jumps.
- Tiny 10–12px luxury captions — inaccessible; 16px floor.
- Header language dropdown — moved to menu/footer.
- Rounded pills, heavy cards, drop shadows — replaced by thin rules, flat planes, editorial type.
- Stock palace imagery — replaced by photography of the actual house.
## 4. Accessibility specification
The site targets **WCAG 2.2 AA** and was audited with Lighthouse plus manual checks; Lighthouse is a baseline, not a certification.
- **No text below 1rem/16px.** FAQ questions are larger; answers are 1.0625rem.
- Body copy has generous line-height and readable measures.
- German compounds use `hyphens: auto`; footer headings are non-breaking; overflow checked at all listed widths.
- Header: transparent over hero, dark frosted glass on scroll; ivory-on-dark composite with gold accent; 18px blur.
- `:focus-visible`: 2px gold outline, 4px offset. Skip link moves focus to `main`.
- Minimum **44px** targets for nav, buttons, form controls, language and footer links.
- Native `<dialog>` menu with `showModal()`, Escape, backdrop click, focus restoration.
- Lightbox: arrow keys, Escape, focus return, labelled prev/next.
- Film dialog: native controls, labelled close.
- `prefers-reduced-motion` disables animation, transitions and smooth scroll.
- `aria-live` form status; labelled fields; required name/email/message/consent; consent not pre-checked; honeypot.
- Form never claims to send when it opens mail; status explains and gives direct email.
- Semantic landmarks/headings; one H1 per page; correct `<html lang>`; localized alt text; descriptive map alt and OSM attribution.
- Known limits: published VTT captions are English (French standalone export has French VTT); no backend validation; noindex is not privacy.
## 5. Internationalisation
| Language | URL | `lang` |
| --- | --- | --- |
| English | `/index.html` | en |
| French | `/fr.html` | fr |
| Portuguese | `/pt.html` | pt |
| Spanish | `/es.html` | es |
| German | `/de.html` | de |
| Italian | `/it.html` | it |
Every locale has localized copy, nav, form labels/options, FAQ, footer, title/description, OG/Twitter, JSON-LD (`inLanguage`, descriptions, FAQ), gallery captions/categories, form status/mailto subject, and hreflang alternates incl. x-default. Language switchers in menu/footer have native-language accessible names.
## 6. SEO and indexing
Pages include canonical URLs, OG/Twitter, JSON-LD (`Organization`, `WebSite`, `WebPage`, `Place`, `FAQPage`, `BreadcrumbList`), hreflang, descriptive metadata and image alt.
**Indexing is intentionally disabled:** `robots.txt` disallows all; every page has `noindex, nofollow, noarchive, nosnippet, noimageindex`; explicit googlebot/bingbot meta; `X-Robots-Tag` in `_headers`/`vercel.json`; sitemap removed. To re-enable: allow crawlers, replace noindex on all six pages, remove X-Robots-Tag and restore a sitemap.
## 7. Lighthouse results
Final **pre-noindex** audit (Chrome 142, Lighthouse 13.6, mobile emulation, `--disable-gpu`). Current noindex may make a fresh SEO run flag `is-crawlable`; intentional.

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
**Improvements:** responsive AVIF/WebP/JPEG with dimensions; hero preload/fetchpriority; inline subset fonts; static OSM (no iframe); click-to-load film; single small vanilla JS; no analytics/third-party; removed reveal/clip effects and `content-visibility`; stable aspect ratios; reduced TBT/CLS. On macOS headless, `--disable-gpu` avoids a spurious GPU-teardown long task.
## 8. Assets
- 25 gallery photographs in AVIF/WebP/JPEG at multiple widths; responsive hero and architectural sets.
- Watermarked sources cleaned by quiet-area seam-crop/blend; originals left outside this repo.
- Film `assets/video/palacio-belavista.mp4`, 42s H.264 fast-start; poster; `palacio-belavista-en.vtt`.
- Static OSM map; gold HTML pin; OSM attribution.
- OG card `assets/img/og-image.jpg` (1200×630); PB monogram favicons.
- Original masters/build pipeline are outside this publishing repo.
## 9. Contact form
Default opens the visitor’s mail app to `enquiries@palaciobelavista.com`. Optional static endpoint via `data-endpoint` + `app.js` (Formspree/FormSubmit); no server/secrets. Honeypot `company`/`_gotcha`; provider spam controls if used. No analytics/tracking. Test an endpoint after configuring it; published copy uses mailto.
## 10. Deployment
- GitHub Pages: `main` / repository root; `.nojekyll` present.
- Live: https://fernangz.github.io/palaciobelavista.com/
- Custom domain not configured (`cname: null`); canonical/hreflang point to https://palaciobelavista.com, so DNS + `CNAME` are still needed.
- Pages ignores `_headers`/`vercel.json`; noindex meta + robots.txt are the effective controls.
## 11. Task recap
1. Audited supplied palace photography/film; selected gallery set.
2. Removed visible Engel & Völkers watermarks via seam-crop/blend; produced AVIF/WebP/JPEG derivatives.
3. Compressed film to H.264, generated poster and VTT.
4. Art direction: Prata + Jost, ivory/ink/gold, mobile-first editorial layout.
5. Built hero, palace, architecture, interiors, craft, garden, film, gallery, private viewings, map, FAQ, form.
6. Gallery: masonry/carousel, filters, hover light, lightbox, keyboard/swipe, responsive variants.
7. Film: poster/play treatment, native video dialog, captions.
8. Replaced Google Maps with static OSM plan, gold pin and attribution.
9. Form: accessible fields, consent, honeypot, mailto fallback/static endpoint.
10. SEO: canonical, OG/Twitter, JSON-LD, image metadata, hreflang, sitemap.
11. Accessibility: 16px floor, contrast, 44px targets, skip link, focus, landmarks, keyboard dialogs, reduced motion.
12. Header: transparent hero state; dark frosted glass on scroll.
13. Added French, Portuguese, Spanish, German, Italian with localized metadata/JSON-LD/switchers.
14. Responsive fixes: tablet footer, German hyphenation, no overflow, localized counts/hints.
15. Performance: inline fonts, optimized images, deferred JS, static map, no third-party; Lighthouse 100s.
16. Renames Boavista → Belavista → **Palacio Belavista** incl. domain/email/video/social card/schema/translations.
17. Single-file French export with images/film/captions/fonts/map/icons embedded.
18. Full-page desktop/mobile screenshots stitched to avoid Chrome’s 16k duplication.
19. Moved only final `website/` contents into this repo; committed/pushed.
20. Disallowed all crawlers, noindex on all pages, removed sitemap, enabled GitHub Pages.
## 12. Credits
Photography/film from the palace archive. **Prata** (Cyreal) and **Jost** (Indestructible Type) under SIL OFL. Map data © OpenStreetMap contributors, ODbL. No third-party analytics/advertising/cookies/tracking. Website copy, photography and film remain property of Palacio Belavista; code not licensed for reuse without permission.
