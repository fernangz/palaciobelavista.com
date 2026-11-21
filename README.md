# Palacio Belavista

The published static website for **Palacio Belavista**, a Pombaline palace at **Rua do Ataíde 9, 1200-034 Lisboa**, in the parish of Misericórdia.

- **Live site (GitHub Pages):** https://fernangz.github.io/palaciobelavista.com/
- **Repository:** https://github.com/fernangz/palaciobelavista.com
- **Canonical domain (pending DNS):** https://palaciobelavista.com
- **Enquiries:** enquiries@palaciobelavista.com

> **Search indexing is disabled.** `robots.txt` disallows all crawlers, every page carries `noindex` metadata, and `sitemap.xml` has been removed. This is not access control: the GitHub Pages site is still publicly reachable.

---

## 1. Project overview

Palacio Belavista is a private Pombaline residence in Lisbon. The website presents the architecture, interiors, craftsmanship, garden, film and gallery of the house in a restrained editorial style, with a private-viewing enquiry flow.

The design pairs **Prata**, a high-contrast display serif, with **Jost** for text, against ivory, ink and muted gold. The gallery is a dark room of its own: a masonry grid on desktop, a snap carousel on mobile, and a full-screen lightbox with keyboard and swipe navigation. All public paths are relative so the site works from GitHub Pages or directly from disk.

The site is intentionally **static**: no framework, no analytics, no third-party embeds, no cookies and no runtime dependencies.

### Address and NAP

| Field | Value |
| --- | --- |
| Name | Palacio Belavista |
| Street | Rua do Ataíde 9 |
| Postal code | 1200-034 |
| City | Lisboa |
| Parish | Misericórdia |
| Country | Portugal |
| Coordinates | 38.7086386, -9.1443863 |
| Email | enquiries@palaciobelavista.com |

The obsolete Google Maps link has been removed. Location links point to **OpenStreetMap**, and the map is a static, cookie-free image with visible OSM attribution.

---

## 2. Repository contents

This repository contains the **published static site only**, at the repository root.

```text
index.html                  English page
fr.html                     French page
pt.html                     Portuguese page
es.html                     Spanish page
de.html                     German page
it.html                     Italian page
app.js                      Menu, gallery filters, lightbox and film player
assets/img/                 Responsive AVIF / WebP / JPEG images, map, icons, OG card
assets/video/               Film, poster and English VTT captions
favicon.ico, favicon-32.png, favicon-48.png, apple-touch-icon.png
site.webmanifest
robots.txt                  Disallow all crawlers
_headers                    Netlify/Cloudflare headers, including X-Robots-Tag
vercel.json                 Vercel headers, including X-Robots-Tag
.nojekyll                   Disable Jekyll on GitHub Pages
```

The original masters, build scripts and image-generation pipeline are kept outside this publishing repository. CSS is inlined in each HTML page; fonts are inlined as base64 WOFF2 subsets.

### Local preview

No build step is required:

```bash
cd /Users/ny/projects/palaciobelavista.com
python3 -m http.server 8000
# http://127.0.0.1:8000/
```

Opening `index.html` directly with `file://` also works because fonts, images, video and scripts are all self-contained or referenced relatively.

> GitHub Pages serves the `.html` filenames directly, so language links use `fr.html`, `pt.html`, etc. Clean `/fr` URLs were a local-server convenience in the development project and are not part of this static GitHub Pages deployment.

---

## 3. Accessibility specification

The site targets **WCAG 2.2 AA** and was audited with Lighthouse and manual checks. Lighthouse is a useful automated baseline, not a certification.

### Typography and legibility

- **No text below `1rem` / 16px.** Navigation, eyebrows, captions, form labels, map credits, footer copy and lightbox controls all use a 16px floor.
- FAQ questions use `clamp(1.25rem, 2.2vw, 1.7rem)`; FAQ answers use `1.0625rem`.
- Body copy uses a generous line height and a maximum readable measure.
- German long compounds are protected with `hyphens: auto` and controlled `overflow-wrap`; footer headings are explicitly kept on one line.
- The layout was checked for horizontal overflow at 320, 360, 390, 412, 768, 960, 1024, 1280 and 1440px.

### Header, contrast and focus

- The header is transparent over the hero and switches on scroll to a **dark frosted-glass** bar:
  - `rgba(17, 21, 15, 0.85)` to `0.92` gradient
  - `backdrop-filter: blur(18px) saturate(1.25)`
  - ivory text on a dark composite background
  - gold brand-mark border
- Because the header is fixed, a scroll-padding offset keeps anchor targets clear.
- `:focus-visible` uses a 2px gold outline with a 4px offset.
- Skip link: **“Skip to content”** moves focus to `main`.

### Interaction and targets

- Minimum **44px** target height for navigation, buttons, form controls, language links and footer links.
- The menu is a native `<dialog>` with `showModal()`, Escape handling, backdrop click and focus restoration.
- The lightbox is keyboard-operable: arrow keys, Escape, focus return, previous/next buttons with accessible names.
- The film opens in a dialog with a visible close control and native video controls.
- The mobile menu/footer language switch is a set of ordinary links with `hreflang` and native-language `aria-label`s.
- `prefers-reduced-motion` disables animations, transitions and smooth scrolling.
- Aria-live status messages announce form submission state.

### Forms

- Every field has a visible `<label>` and an explicit `for`/`id` pair.
- Name, email, message and consent are required; HTML validation is used.
- Email uses `type="email"` and `autocomplete="email"`; phone uses `autocomplete="tel"`.
- Consent is a labelled checkbox, not a pre-checked box.
- A quiet honeypot (`company`, `_gotcha`) protects the static endpoint.
- The form never claims to have sent anything when it opens the visitor’s mail app; the status text explains what happened and gives the direct email fallback.

### Semantic structure

- One `<h1>` per page; sections use labelled `<h2>`/`<h3>` headings.
- Landmarks: `<header>`, `<nav>`, `<main>`, `<footer>`, plus labelled `<dialog>` elements.
- All six pages declare the correct `<html lang>`.
- Decorative images use empty alt text; content images have descriptive, localized alt text.
- The static map has a descriptive alt and visible OSM attribution.

### Known limits

- The VTT captions included in this published copy are **English**; the standalone French export has French VTT captions.
- The site has no backend validation; the form is a mail-app handoff unless a static form endpoint is configured.
- `noindex` prevents search indexing but does **not** make the site private.

---

## 4. Internationalisation

Six complete language versions ship in this repository:

| Language | URL | `<html lang>` |
| --- | --- | --- |
| English | `/index.html` | `en` |
| French | `/fr.html` | `fr` |
| Portuguese | `/pt.html` | `pt` |
| Spanish | `/es.html` | `es` |
| German | `/de.html` | `de` |
| Italian | `/it.html` | `it` |

Each localized page has:

- localized visible copy, navigation, form labels/options, FAQ and footer
- localized `<title>` and meta description
- localized Open Graph/Twitter metadata
- localized JSON-LD (`inLanguage`, descriptions, FAQ questions and answers)
- `hreflang` alternate links, including `x-default`
- a language switcher in the menu and footer
- localized gallery captions/categories and accessible labels
- localized form status messages and mailto subject

---

## 5. SEO and indexing

The pages include:

- canonical URLs
- Open Graph and Twitter cards
- JSON-LD (`Organization`, `WebSite`, `WebPage`, `Place`, `FAQPage`, `BreadcrumbList`)
- `hreflang` alternates
- descriptive titles and meta descriptions
- image alt text and structured image metadata

**Current indexing state:** intentionally disabled.

- `robots.txt`: `User-agent: * / Disallow: /`
- Every page: `noindex, nofollow, noarchive, nosnippet, noimageindex`
- Explicit `googlebot` and `bingbot` meta
- `X-Robots-Tag` in `_headers` and `vercel.json`
- `sitemap.xml` removed from the repository

To make the site indexable later, all four controls must be reversed: allow crawlers in `robots.txt`, replace the noindex meta on all six pages, remove the X-Robots-Tag headers, and restore a sitemap.

---

## 6. Lighthouse results

The following is the final **pre-noindex** audit (Chrome 142, Lighthouse 13.6, mobile emulation, `--disable-gpu`). The site is now deliberately blocked from indexing, so a fresh Lighthouse SEO run may flag the `is-crawlable` audit; that is intentional, not a regression.

| Category | Mobile | Desktop |
| --- | ---: | ---: |
| Performance | **100** | **100** |
| Accessibility | **100** | **100** |
| Best practices | **100** | **100** |
| SEO | **100** | **100** |

| Metric | Mobile | Desktop |
| --- | ---: | ---: |
| First Contentful Paint | 1.1 s | 0.3 s |
| Largest Contentful Paint | 1.1 s | 0.3 s |
| Total Blocking Time | 20 ms | 0 ms |
| Cumulative Layout Shift | 0 | 0.015 |
| Speed Index | 1.1 s | — |

Reproduce with:

```bash
npx lighthouse https://fernangz.github.io/palaciobelavista.com/ \
  --chrome-flags="--headless=new --no-sandbox --disable-gpu" \
  --output=html --output-path=./lighthouse-mobile.html

npx lighthouse https://fernangz.github.io/palaciobelavista.com/ \
  --preset=desktop \
  --chrome-flags="--headless=new --no-sandbox --disable-gpu" \
  --output=html --output-path=./lighthouse-desktop.html
```

On macOS headless Chrome, GPU teardown can create a spurious multi-second long task. `--disable-gpu` avoids that measurement artefact.

### Lighthouse improvements made

- **LCP:** responsive AVIF/WebP/JPEG images with explicit dimensions; hero image preloaded with `fetchpriority="high"`; inline font subsets so there is no font round-trip.
- **TBT:** no framework, no third-party scripts, no analytics, no iframe; a single small vanilla JS file handles only menu, filters, lightbox and film.
- **CLS:** stable image aspect ratios, fixed header offsets, no layout-shifting reveal animations, and removal of section-level `content-visibility` placeholders that caused anchor jumps.
- **Network:** all critical fonts inlined; static OSM map instead of an iframe; no cookie banners or external embeds.
- **Rendering:** scroll reveals and clip-path entrance effects were removed because they delayed LCP and prevented native lazy loading.
- **Images:** native `loading="lazy"` below the fold, `decoding="async"`, and `srcset`/`sizes` for the gallery, hero and map.
- **Caching:** immutable `/assets/*` caching in `_headers`/`vercel.json`; GitHub Pages uses its own cache policy.
- **Accessibility:** 16px floor, contrast fixes, 44px targets, focus states, localized labels, unique landmark names and keyboard dialogs.

---

## 7. Image, film and map assets

- 25 gallery photographs, each in AVIF, WebP and JPEG at multiple widths.
- Separate responsive hero and architectural-detail sets.
- Selected source images originally carried Engel & Völkers watermarks. The build removed a thin horizontal band through quiet areas and blended the seam; originals were left untouched outside this repo.
- Film: `assets/video/palacio-belavista.mp4`, 42 seconds, H.264 with fast-start.
- Captions: `assets/video/palacio-belavista-en.vtt` (English).
- Map: static OpenStreetMap image generated from OSM tiles, muted to the site palette, with a gold HTML pin overlay.
- Social card: `assets/img/og-image.jpg` (1200×630), regenerated with the current Palacio Belavista name.
- Icons and favicons: PB monogram.

---

## 8. Contact form

The form is backend-free by design and works on GitHub Pages.

- **Default behaviour:** opens the visitor’s mail app with a pre-composed message to `enquiries@palaciobelavista.com`.
- **Optional static endpoint:** the static page can POST to Formspree/FormSubmit via the `data-endpoint` attribute and `app.js`; no server is required.
- **No secrets:** endpoints are public and contain no credentials.
- **Spam:** `company` + `_gotcha` honeypot; provider-side spam controls should be enabled if an endpoint is used.
- **Privacy:** details are used only to reply to the enquiry. There is no analytics or tracking.

If an endpoint is configured, test it after editing because the current published copy uses the mailto fallback.

---

## 9. Deployment

- GitHub Pages source: **`main` branch / repository root**
- `.nojekyll` is present so files are served as-is.
- Custom domain: **not configured** (`cname` is null). The site currently lives at the `fernangz.github.io` project URL.
- Canonical and hreflang URLs point at `https://palaciobelavista.com`; DNS and a `CNAME` file are still required before that domain can serve the site.
- GitHub Pages ignores `_headers` and `vercel.json`; the noindex meta tags and `robots.txt` are the controls that matter on Pages.

---

## 10. Task recap

1. **Source audit** — reviewed the supplied palace photography and film; identified the selected gallery set.
2. **Image preparation** — removed visible Engel & Völkers watermarks with seam-crop/blend work; produced responsive AVIF, WebP and JPEG derivatives.
3. **Film preparation** — compressed the 42-second film to H.264, generated a poster and an English VTT track.
4. **Art direction** — Prata + Jost typography, ivory/ink/gold palette, editorial layout, mobile-first section rhythm.
5. **Core pages** — hero, palace introduction, architecture, interiors, craft, garden, film, gallery, private viewings, map, FAQ and enquiry form.
6. **Gallery** — masonry desktop grid, mobile snap carousel, filters, hover light, full-screen lightbox, keyboard/swipe navigation and responsive image selection.
7. **Film** — custom poster/play treatment, native video dialog and caption track.
8. **Map** — replaced Google Maps with a static OpenStreetMap plan, custom gold pin and OSM attribution.
9. **Enquiry form** — accessible fields, consent, honeypot, mailto fallback and optional static form endpoint.
10. **SEO** — canonical, Open Graph, Twitter, JSON-LD, image metadata, hreflang and sitemap.
11. **Accessibility** — 16px minimum text, contrast, 44px targets, skip link, focus states, semantic landmarks, keyboard dialogs and reduced motion.
12. **Header** — transparent over the hero; dark frosted glass on scroll with high-contrast ivory text.
13. **Languages** — added French, Portuguese, Spanish, German and Italian pages with localized copy, metadata, structured data and language switchers.
14. **Responsive fixes** — tablet footer reflow, German hyphenation, no horizontal overflow, localized gallery counts and swipe hints.
15. **Performance** — inline fonts, optimized images, deferred vanilla JS, removed costly reveal/layout effects, static map, no third-party requests.
16. **Lighthouse** — achieved 100 in Performance, Accessibility, Best Practices and SEO on mobile and desktop.
17. **Renames** — Boavista → Belavista → **Palacio Belavista**, including domain, email, video filenames, social card, schema and translations.
18. **Single-file export** — produced a self-contained French HTML export with all images, film, captions, fonts, map and icons embedded.
19. **Full-page captures** — stitched accurate desktop and mobile screenshots without Chrome’s 16k-pixel duplication artefact.
20. **Publishing** — moved only the final `website/` contents into this repository, committed and pushed to GitHub.
21. **Indexing lock-down** — disallowed all crawlers, added noindex metadata to all pages, removed the sitemap and enabled GitHub Pages.

---

## 11. Credits

- Photography and film from the palace archive.
- **Prata** by Cyreal and **Jost** by Indestructible Type, both under the SIL Open Font License.
- Static map data © OpenStreetMap contributors, available under the Open Database Licence.
- No third-party analytics, advertising, cookie or tracking scripts.

All website copy, photography and film remain the property of Palacio Belavista. The code is not licensed for reuse without permission.
