# Postcard Design Alignment — Change List

Reference: the supplied postcard artwork in `postcard/` (front and back). The artwork is a design reference, not a page asset. No website visuals have been changed yet.

The current typefaces stay: **Noto Serif** and **Noto Sans**. The postcard’s serif is more high-contrast than Noto Serif, so the match will be achieved through case, size, tracking, rules and layout rather than a new typeface.

## 1. What the postcard establishes

### Visual system

- **Split postcard panel:** photograph on one half, cream text panel on the other, roughly 50/50.
- **Cream stock:** warm ivory, approximately `#FCF3E4`.
- **Mount/background:** warm greige, approximately `#DBC9BB`.
- **Ink:** near-black, approximately `#1B1A17`.
- **Rules:** thin, warm grey/taupe, approximately `#9A8B78`; no heavy borders.
- **No rounded corners, drop shadows, glossy cards or filled sales panels.**
- **Generous margins:** the photograph sits inside a cream matte rather than running edge-to-edge.
- **Centred cover block:** line-art mark, two-line uppercase wordmark, tracked location line, rule, italic promise, short sale statement.
- **Back-panel block:** large uppercase serif headline, three short feature lines, rule, italic call to action, small tracked support line, QR block.

### Typography behaviour

- **Wordmark:** uppercase serif, two lines, centred, wide tracking.
- **Headlines:** uppercase Noto Serif with tight leading and generous side margins.
- **Emotional lines:** Noto Serif italic, sentence case.
- **Supporting copy:** Noto Serif regular, not the current sans body.
- **Labels/location/UI:** Noto Sans, uppercase, small, widely tracked.
- **No all-sans body passages** in the postcard; sans is reserved for labels and interface text.

### Content cues

- “PALACIO BELA VISTA” — the website name is fixed. The postcard’s current “Palacete” wording will be revised by the designer to “Palacio”.
- “LISBON · PORTUGAL”
- “History. Beauty. A home like no other.”
- “Private residence available to purchase.”
- “YOUR NEXT CHAPTER, IN LISBON.”
- “Grand reception rooms. Ornate ceilings. Gardens, terraces and views of the Tagus.”
- “Discover the residence”
- “Private film & viewing enquiries”
- A QR code pointing to `https://palaciobelavista.com/?play`, with the URL printed alongside it.

## 2. Decisions

### Resolved

- **Name:** **Palacio Bela Vista**. The website name is fixed; the postcard’s “Palacete” will be updated by the designer to “Palacio”. All website wordmarks, metadata and translations stay on “Palacio”.
- **Sale positioning:** **“Private residence available to purchase.”** Use this exact public wording in the sale statement, metadata and translations. The postcard copy will be updated to match.
- **Logo:** use the postcard’s **window mark** as the primary brand mark. Replace the PB monogram in the header, footer, favicon and OG card.
- **Gallery:** retain the **dark ink background**. The gallery remains the deliberate dark contrast to the cream postcard panels; only its typography, rules and captions should be refined.
- **Footer:** keep the current dark footer as the closing contrast block unless a later design review decides otherwise.
- **QR:** point to **`https://palaciobelavista.com/?play`**. Opening the URL should open the film and start playback. The printed postcard must also show the URL as a fallback.
- **Postcard distribution:** the postcard is a physical print piece sent to potential buyers. It links to the website through the QR code and printed URL. **No downloadable postcard is needed on the website.**

## 3. P0 — Brand and global tokens

### 3.1 Add the window mark

- Trace or redraw the postcard’s open-window illustration as a clean SVG: open shutters, bridge, river, city roofs, balustrade.
- Replace the PB monogram with the window mark. Use it:
  - above the wordmark on the opening panel;
  - in the footer;
  - as the favicon/PWA icon at small sizes;
  - on the OG/social card;
  - optionally as a subtle watermark, never as a busy background.
- Provide an accessible name on the link/logo; decorative copies get `aria-hidden="true"`.

### 3.2 Wordmark treatment

- Two centred lines, uppercase:
  - `PALACIO` / `BELA VISTA`.
- Noto Serif 400, tight line-height, tracking around `0.08–0.12em`.
- Location line below: `LISBON · PORTUGAL`, Noto Sans, 1rem floor, wide tracking.
- Thin rule below, roughly 70% of the text-panel width.
- Do not use the current small left-aligned header wordmark as the main cover expression.

### 3.3 Palette tokens

Replace or add tokens:

| Token | Proposed value | Use |
| --- | --- | --- |
| `--paper` | `#FCF3E4` | Postcard stock / primary background |
| `--paper-2` | `#F6EAD8` | Alternate cream panel |
| `--mount` | `#DBC9BB` | Outer mount / page surround |
| `--ink` | `#1B1A17` | Text, rules, wordmark |
| `--text` | `#2B2924` | Body copy |
| `--muted` | `#6B6255` | Secondary copy |
| `--line` | `rgba(27,26,23,.15)` | Thin rules |
| `--brass` | `#9A8468` | Replaces saturated gold for rules/labels |

Keep the existing `--gold` tokens only if a warmer accent is still needed; the postcard is closer to muted brass/taupe than yellow gold.

### 3.4 Typography roles

- **Display:** Noto Serif; uppercase for cover statements and key section headlines.
- **Body:** switch editorial body copy to Noto Serif; keep Noto Sans for:
  - navigation;
  - eyebrow labels;
  - buttons;
  - metadata, coordinates and small print.
- **Emotional lines:** Noto Serif italic.
- **No new font families.**

### 3.5 Buttons and links

- Replace the current solid dark rectangular button with:
  - a thin outlined rectangle, or
  - an uppercase text link with a rule and arrow.
- The postcard has no filled CTA; the closest match is outlined/underlined text.
- Keep 44px targets and visible focus.

## 4. P1 — Section-by-section changes

### 4.1 Header

- Current: PB box, small left wordmark, four links, transparent over dark video.
- Change:
  - light cream header over the cream page, or transparent over a cream opening panel;
  - window mark + compact wordmark at left;
  - four quiet text links;
  - `CONTACT` as an outlined rectangle, not a filled button;
  - thin bottom rule only when scrolled.
- If the opening panel is cream, the header no longer needs the dark frosted-glass state; use a cream/ivory scrolled state with ink text.

### 4.2 Opening video section

- Current: dark full-bleed section, huge Noto Serif H1, portrait poster.
- Change to a **postcard cover panel**:
  - cream page/mount;
  - large framed film poster or facade photograph on one side;
  - cream text panel on the other;
  - window mark, two-line wordmark, `LISBON · PORTUGAL`, rule;
  - italic promise: “History. Beauty. A home like no other.”;
  - short line: “Private residence available to purchase.”;
  - a quiet “Play the film” text link/outlined control over the poster.
- Keep the 42-second click-to-load film and native dialog.

### 4.3 Gallery

- Current: dark ink background, masonry, captions over images.
- **Retain the dark ink background** as the deliberate counterpoint to the cream postcard panels.
- Refine instead of lightening:
  - warm brass rules and tracked Noto Sans captions;
  - a slightly warmer dark ink and softer caption gradient;
  - filters as tracked text with a thin brass active rule;
  - keep 25 images, filters, lightbox and responsive carousel.
- Do not convert the gallery to a cream/mount background.

### 4.4 Property identity

- Current: light section with a dark map card.
- Change:
  - map inside a cream frame with a thin rule;
  - remove the dark card;
  - address, coordinates, property type and map link in a cream panel separated by hairlines;
  - labels in Noto Sans uppercase; values in Noto Serif;
  - keep OSM attribution and static map.

### 4.5 Characteristics

- Current: four-column boxed grid.
- Change:
  - two-column editorial rows on desktop, one column on mobile;
  - each row separated by a thin rule, no boxes;
  - labels small caps/Noto Sans; values Noto Serif;
  - keep the eight fields and “On request” values until real figures are supplied.
- Consider using the postcard’s three-line feature list above the grid:
  - “Grand reception rooms.”
  - “Ornate ceilings.”
  - “Gardens, terraces and views of the Tagus.”

### 4.6 Craft

- Current: stone-coloured section with a dark image grid and uppercase captions.
- Change:
  - cream section;
  - images framed as postcard plates;
  - captions in italic/serif or small caps below the image;
  - keep the existing craft copy and images.
- Use the postcard’s warm, natural photography grade; avoid heavy contrast or dark overlays.

### 4.7 FAQs

- Keep the existing questions and native `<details>`.
- Change only the surface:
  - cream background;
  - thin rules between items;
  - Noto Serif questions;
  - Noto Serif answers, with Noto Sans only for icons/labels.

### 4.8 Contact

- Current: large dark button and right-hand details.
- Change to a postcard back panel:
  - cream panel with thin rule;
  - italic serif “Discover the residence”;
  - small line “Private film & viewing enquiries”;
  - email address in Noto Serif;
  - outlined `REQUEST THE FULL DOSSIER` link;
  - no QR block on the website; the QR belongs to the printed postcard.
- Keep the localized prefilled mailto and remove any dark filled CTA.

### 4.9 Footer

- Keep the current dark ink footer as the default closing contrast.
- The resolved gallery decision does not automatically make the footer cream; revisit only in a later visual review.
- Replace the PB monogram with the window mark and set the wordmark on two lines.
- Keep the language selector, contact details and back-to-top.

## 5. P1 — Content changes

- Add the postcard promise: **“History. Beauty. A home like no other.”**
- Add the sale statement: **“Private residence available to purchase.”**
- Add the back-cover headline: **“Your next chapter, in Lisbon.”**
- Add the three-line feature list: **“Grand reception rooms. Ornate ceilings. Gardens, terraces and views of the Tagus.”**
- Add the contact lead: **“Discover the residence”** and **“Private film & viewing enquiries.”**
- Do not copy `Contact details and video link to be confirmed`; it is a production placeholder. The QR destination is now `https://palaciobelavista.com/?play`.
- Translate every new line into all 11 locales and keep the mailto copy localized.

## 6. P1 — `/?play` video deep link

The postcard QR points to `https://palaciobelavista.com/?play`. The website needs a dedicated deep-link behaviour:

- On load, if `play` is present in the query string, open the existing film dialog.
- Attempt to start the film automatically.
- Browsers block audible autoplay without a gesture; if `play()` is rejected, leave the native player visible with the play control focused. Do not silently fail.
- Do not autoplay on a normal visit. `/?play` is the only trigger.
- Keep the same behaviour on the provisional GitHub Pages URL for testing: `https://fernangz.github.io/palaciobelavista.com/?play`.
- The final QR code must be generated only after the domain is live, so it encodes the final URL.
- The postcard must print `palaciobelavista.com/?play` next to the QR.
- If the visitor changes language after landing, the film dialog and controls should stay in the selected locale.

## 7. P2 — Assets and finishing

- Regenerate the OG card in the postcard system: cream ground, window mark, two-line wordmark, no dark overlay.
- Replace the PB monogram favicons with the window mark.
- Crop the facade photograph for the front/cover and a ceiling or reception-room photograph for the back/contact.
- Keep natural colour grading; no heavy filters.
- Do not add a downloadable postcard; the postcard is a physical sales piece.
- Update `README.md`, `FONT-LICENSES.md` references and this document after the design pass.

## 8. Responsive and accessibility constraints

- Split panels stack on mobile: image first, cream text panel below.
- Keep the 16px minimum for every label and caption.
- Maintain 44px targets for nav, buttons, filters, language links and the dossier CTA.
- Check contrast for muted brass/taupe on cream; use the darker `--muted` for small text.
- The window mark needs a text alternative where it carries meaning; decorative copies are hidden.
- The printed postcard must show the URL next to the QR code so the link still works if scanning fails.
- Test 320, 390, 768, 1024 and 1440px; repeat in RTL Arabic and CJK locales.
- Preserve `prefers-reduced-motion`; the postcard is static, so no new motion is needed.

## 9. Suggested implementation order

1. **Window-mark tracing + palette tokens** (0.5–1 day).
2. **Header, wordmark and opening video panel** (1 day).
3. **Gallery, property identity and characteristics** (1–1.5 days).
4. **Craft, FAQ, contact and footer** (1 day).
5. **OG card, favicons, QR/`?play` link and translations** (0.5–1 day).
6. **Responsive/RTL/accessibility QA** (1 day).

Rough total: **4–6 working days**, excluding photography retouching and native-speaker review.

## 10. What not to change

- Do not introduce a new typeface; use Noto Serif/Noto Sans.
- Do not add a downloadable postcard; the postcard is a physical sales piece. Do not copy “to be confirmed” text.
- Do not use the postcard’s exact paper texture as a website background; use the colour and matte logic.
- Do not replace the existing fact set with invented figures; the “On request” values remain until real data is supplied.
