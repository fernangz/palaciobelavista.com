# Client Corrections — Confirmed Brief

**Source:** `input/corrections/Corrections_site_Fernan_avec_logo.docx` (French, 21 November 2026)  
**Status: implemented on 22 November 2026.** The page structure, gallery, Overview, contact map, email handling, logo, footer and video copy have been updated across all eleven locales. The QR/video behaviour is unchanged.

The document is based on eight screenshots of the current site plus a reference logo. It explicitly says that interactions, the film, forms and translations were not tested. The decisions below resolve the open questions in the review.

## 1. Confirmed page structure

**Video / Home → Gallery → Overview → Contact with small map → simplified Footer**

This removes the standalone **Property**, **Craft** and **FAQ** sections.

## 2. Confirmed decisions

1. **Languages:** keep all current languages. Do not reduce to ENG / FR / PT.
2. **Email:** use `palaciobelavista@gmail.com`. Remove every visible email address from the page copy. Use the address only inside `mailto:` links/buttons and machine-readable metadata.
3. **Single Contact:** keep the outlined **CONTACT** button. Remove the duplicate text link from the desktop navigation. Keep a Contact entry in the mobile menu because the header button is not visible there.
4. **Logo:** use `input/logo/Logo_Palacio_Bela_Vista_sans_texte.svg` for the header, footer and brand moments. Preserve its proportions.
5. **Gallery:** title **“A palace of many wonders.”** Remove the filters and the photograph count. Put all gallery images in one gallery. Do not keep the standalone Craft section.
6. **Overview:** use **“Overview”** as the temporary section title. Keep the current property data and use the paragraph from the old **“The property”** section as the introduction. Move **property type** and **nearest metro** into Overview.
7. **Map:** move the map into Contact in a smaller format. Style it as an 18th-century-inspired area view. Do **not** place an exact-location pin. Keep the exact address as text. Remove coordinates and all price references.
8. **QR/video:** keep the current `/?play` behavior unchanged. The video-section copy removals from the review still apply; do not add a new fade/transition or change the film duration.

## 3. Brand and navigation

### Apply

- Keep the validated name **PALACIO BELA VISTA** everywhere.
- Replace the current simplified window mark with the supplied SVG emblem.
- The supplied SVG is the emblem only, without text. Pair it with the existing typeset **Palacio Bela Vista** wordmark; do not stretch the emblem.
- Header navigation becomes **Video, Gallery, Overview** plus the outlined **Contact** button.
- Mobile menu becomes **Video, Gallery, Overview, Contact**, renumbered 01–04.
- Remove links to Property, Craft and Questions.
- Remove the duplicate text Contact link from the desktop nav.

### Implementation note

The supplied emblem is a detailed black engraving. It needs a brass treatment in the dark footer; use a CSS mask or colour filter so the vector stays crisp. Check that the emblem is still readable at header size and derive a simpler favicon only if necessary.

## 4. Home and video

### Apply

- Remove the **VIDEO** eyebrow.
- Keep:
  - the title;
  - the location;
  - “A walk through the house.”;
  - “History. Beauty. A home like no other.”;
  - “Private residence available to purchase.”
- Delete the paragraph beginning **“Forty-two seconds…”**.
- Delete **“Filmed at Palacio Bela Vista. Best watched with headphones.”**
- Remove **“42 seconds · Sound · Lisbon 2026”**.
- Add a Contact link below the video.
- Add an explicit scroll cue below the video.

### Do not change

- `/?play` behavior.
- Film duration.
- Playback/dialog mechanics.
- No new fade-to-site transition.

## 5. Gallery

### Apply

- Change the title to **“A palace of many wonders.”**
- Remove the intro paragraph.
- Remove the **“25 PHOTOGRAPHS”** count.
- Remove the entire filter bar: All, Architecture, Interiors, Craft, Garden, Lisbon.
- Show all gallery images in one gallery, without filter states.
- Remove the standalone Craft section; its six photographs are already present in the gallery.
- Keep the lightbox and captions.
- Remove the gallery count/filter JavaScript and the filter-related copy.

### Result

A single 25-image gallery with no filters, no count and no separate Craft section.

## 6. Overview section

### Apply

- Rename the current **Characteristics** section to **Overview** (temporary title).
- Move it directly after the gallery.
- Use the paragraph from the old **“The property”** section as the section introduction.
- Keep the current property data:
  - reported area;
  - reported plot area;
  - rooms;
  - bedrooms;
  - bathrooms;
  - build year;
  - construction materials;
  - structural features;
  - outdoor spaces;
  - sustainability status.
- Add **property type** and **nearest metro** to the Overview data.
- Remove **coordinates**.
- Remove the **asking price**.
- Keep the existing verification note about reported figures, bathroom schedule and floor count.

### Do not

- Do not introduce new property claims.
- Do not rekey the reported figures without verification.

## 7. Contact and map

### Apply

- Change **“Discover the residence.”** to **“Discover the Palacio.”**
- Remove the visible email row.
- Keep the address and appointment details.
- Make the dossier button a `mailto:palaciobelavista@gmail.com` link.
- Move the map into Contact in a smaller format.
- Remove the exact-location pin.
- Style the map as an 18th-century-inspired area view: sepia/paper treatment, brass/cream frame, no pin.
- Keep an area caption such as **“Misericórdia / Chiado · Lisbon”**, not the exact street address on the map.
- Keep OSM attribution.
- Remove all price references.
- Remove the visible email from the footer and any other visible copy.

### Open technical note

The current map asset is an OpenStreetMap street plan, not a satellite/aerial photograph. It can be styled as an antique area map with no pin. If a true aerial/satellite image is required, a new source image is needed.

## 8. Footer

### Apply

- Keep the logo and the **PALACIO BELA VISTA** title.
- Remove the descriptive statement.
- Remove the **VISIT / DISCOVER / CONTACT** columns.
- Remove the footer contact block and visible email.
- Remove the photography text and old columns; keep a minimal copyright line and a privacy-request link.
- Keep the full language list.
- Keep **BACK TO TOP** and verify it returns to the top.

### Pending

- Legal/privacy links or copyright text may need to remain accessible; check separately without recreating the removed columns.

## 9. Removed sections

- **Property:** remove section, intro, map card and navigation link. Reuse its paragraph in Overview; move property type and nearest metro to Overview; move the map to Contact.
- **Craft:** remove section, copy and navigation link. The six photographs already exist in the gallery.
- **FAQ:** remove all five questions, the section, the menu/footer links and the `FAQPage` structured data.

## 10. Technical implications

- Update all eleven locales, including new translations for **Overview**, **A palace of many wonders**, **Discover the Palacio**, and the map caption/alt.
- Remove Property, Craft and FAQ markup, CSS and anchors.
- Update desktop nav and mobile menu numbering.
- Move the map markup and OSM attribution into Contact; remove the pin.
- Remove gallery filters, count element and filter/count JavaScript.
- Remove FAQ JSON-LD and breadcrumb/FAQ references.
- Simplify footer markup and CSS.
- Replace all visible `enquiries@palaciobelavista.com` text; update `mailto:` links and schema email to `palaciobelavista@gmail.com`.
- Copy the supplied SVG into the published assets, replace the inline marks and preserve aspect ratio.
- Add antique map styling and check contrast/legibility.
- Recheck font coverage, mobile layouts, RTL, lightbox indices and `/?play`.
- Update `lastmod` and documentation after implementation.

## 11. Implementation notes

1. The contact map uses a pre-styled antique version of the existing OSM plan, with no pin. It is an area view, not satellite photography.
2. The footer keeps a minimal copyright line with a privacy-request mailto and all eleven languages. No separate privacy policy page exists yet.
3. “Video: no changes” was applied to `/?play` behaviour; the review’s video copy removals were applied.
