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

- “PALACETE BELA VISTA” — note the postcard uses **Palacete**, while the site currently uses **Palacio**.
- “LISBON · PORTUGAL”
- “History. Beauty. A home like no other.”
- “A historic palace offered for sale.”
- “YOUR NEXT CHAPTER, IN LISBON.”
- “Grand reception rooms. Ornate ceilings. Gardens, terraces and views of the Tagus.”
- “Discover the residence”
- “Private film & viewing enquiries”
- A QR placeholder — destination not yet defined.

## 2. Decisions needed before implementation

1. **Name:** keep **Palacio Bela Vista** or adopt the postcard’s **Palacete Bela Vista**? This affects every page, schema, OG card and translation. Do not mix the two.
2. **Sale positioning:** the postcard says “A historic palace offered for sale.” The site currently says “private residence” and does not mention sale. Confirm the public wording: “offered for sale”, “private sale”, or “available on request”.
3. **Logo:** replace the PB monogram with the window/bridge/balustrade line mark, or keep PB and use the window mark only as a cover illustration?
4. **Gallery/footer contrast:** go fully cream like the postcard, or keep the dark gallery/footer as a deliberate counterpoint? The closest match is cream gallery and cream footer.
5. **QR:** where should it point — the film, the dossier mailto, or the website itself? The postcard’s QR is currently a placeholder.
6. **Postcard download:** should the website offer a printable/downloadable postcard, or is the artwork only a design reference?

## 3. P0 — Brand and global tokens

### 3.1 Add the window mark

- Trace or redraw the postcard’s open-window illustration as a clean SVG: open shutters, bridge, river, city roofs, balustrade.
- Use it:
  - above the wordmark on the opening panel;
  - in the footer;
  - as the favicon/PWA icon at small sizes;
  - on the OG/social card;
  - optionally as a subtle watermark, never as a busy background.
- Provide an accessible name on the link/logo; decorative copies get `aria-hidden="true"`.

### 3.2 Wordmark treatment

- Two centred lines, uppercase:
  - `PALACETE` / `BELA VISTA` or `PALACIO` / `BELA VISTA`.
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
  - short line: “A historic palace offered for sale.” (pending decision);
  - a quiet “Play the film” text link/outlined control over the poster.
- Keep the 42-second click-to-load film and native dialog.

### 4.3 Gallery

- Current: dark ink background, masonry, captions over images.
- Change:
  - cream/mount background;
  - photographs inside cream mats with thin rules;
  - captions below the image in ink, not over a dark gradient;
  - filters as tracked text with a thin active rule;
  - keep 25 images, filters, lightbox and responsive carousel.
- The gallery should feel like a set of postcard plates, not a dark exhibition wall.

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
  - optional QR block only if a destination is agreed.
- Keep the localized prefilled mailto and remove any dark filled CTA.

### 4.9 Footer

- Current: dark ink footer.
- Change:
  - cream footer with black wordmark and thin rules (closest postcard match), or
  - keep dark ink as the only strong contrast block if the client prefers a clear ending.
- Keep the language selector, contact details and back-to-top.
- If cream, use the window mark and a two-line wordmark rather than the current oversized single-line treatment.

## 5. P1 — Content changes

- Add the postcard promise: **“History. Beauty. A home like no other.”**
- Add the sale statement: **“A historic palace offered for sale.”** — only after the sale-positioning decision.
- Add the back-cover headline: **“Your next chapter, in Lisbon.”**
- Add the three-line feature list: **“Grand reception rooms. Ornate ceilings. Gardens, terraces and views of the Tagus.”**
- Add the contact lead: **“Discover the residence”** and **“Private film & viewing enquiries.”**
- Do not copy `Contact details and video link to be confirmed` or the `QR PLACEHOLDER`; those are production placeholders.
- Translate every new line into all 11 locales and keep the mailto copy localized.

## 6. P2 — Assets and finishing

- Regenerate the OG card in the postcard system: cream ground, window mark, two-line wordmark, no dark overlay.
- Replace the PB monogram favicons with the window mark if the logo decision is approved.
- Crop the facade photograph for the front/cover and a ceiling or reception-room photograph for the back/contact.
- Keep natural colour grading; no heavy filters.
- Consider a “Download the postcard” PDF only if the client wants a printable leave-behind.
- Update `README.md`, `FONT-LICENSES.md` references and this document after the design pass.

## 7. Responsive and accessibility constraints

- Split panels stack on mobile: image first, cream text panel below.
- Keep the 16px minimum for every label and caption.
- Maintain 44px targets for nav, buttons, filters, language links and the dossier CTA.
- Check contrast for muted brass/taupe on cream; use the darker `--muted` for small text.
- The window mark needs a text alternative where it carries meaning; decorative copies are hidden.
- The QR block, if used, needs a visible text link as an equivalent.
- Test 320, 390, 768, 1024 and 1440px; repeat in RTL Arabic and CJK locales.
- Preserve `prefers-reduced-motion`; the postcard is static, so no new motion is needed.

## 8. Suggested implementation order

1. **Brand decision + window mark + palette tokens** (0.5–1 day).
2. **Header, wordmark and opening video panel** (1 day).
3. **Gallery, property identity and characteristics** (1–1.5 days).
4. **Craft, FAQ, contact and footer** (1 day).
5. **OG card, favicons, QR decision and translations** (0.5–1 day).
6. **Responsive/RTL/accessibility QA** (1 day).

Rough total: **4–6 working days**, excluding photography retouching and native-speaker review.

## 9. What not to change

- Do not introduce a new typeface; use Noto Serif/Noto Sans.
- Do not copy the postcard’s placeholder QR or “to be confirmed” text.
- Do not use the postcard’s exact paper texture as a website background; use the colour and matte logic.
- Do not replace the existing fact set with invented figures; the “On request” values remain until real data is supplied.
