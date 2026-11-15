# Pfast Reliable Racquet Stringing — website

Single static page (`index.html`). No build step.

## Setup (one time)

1. **Formspree** — done. The form posts to `https://formspree.io/f/xbgdonvl`; manage notifications and view submissions at https://formspree.io. Formspree's free tier allows 50 submissions/month.
2. **Prices / strings** — edit the cards in `#pricing` and the String dropdown in the `#request` form together (see *String setups* below).
3. **GitHub Pages** — create an empty repo on GitHub (e.g. `pfast-stringing`), then:

   ```bash
   git remote add origin git@github.com:YOUR_USER/pfast-stringing.git
   git push -u origin main
   ```

   In the repo: Settings → Pages → Source: *Deploy from a branch* → `main` / `/ (root)`. The site goes live at `https://YOUR_USER.github.io/pfast-stringing/` within a minute or two.
4. **RacquetTech** — log in at racquettech.com (Get Password link) and put the Pages URL in your stringer profile's website field so it shows up in the stringer search.

## Editing

Open `index.html` in any editor. Colors and fonts live in the `:root` block at the top of the `<style>`. The look is a tennis-court theme: hard-court blue sections alternating with pale ones, white panels, ball-yellow buttons, clay-orange prices and a grass-green footer. Barlow and Barlow Semi Condensed are self-hosted in `fonts/` under the SIL Open Font License. Commit and push to redeploy.

- **Fonts** — besides Barlow there are four "Fallback" font rules at the top of the styles. They resize the system font shown before Barlow arrives so the layout does not jump; leave them alone unless the typeface changes.
- **Hero photo** — the masthead shows `img/hero.jpg` on the right under a court-blue scrim that is solid behind the text. The current file is a rendered string-bed artwork; replace it with a real photo of the bench (about 1800×1000, JPG, with the interesting part on the right) and nothing else needs to change.
- **Section backgrounds** — every block of the page is a `<section class="sec …">`. `sec light` is the pale background, `sec white` is white, `sec deep` is the dark blue and a plain `sec` is court blue. Changing the word changes the background, and the text colours follow.
- **Answers under the headline** — the three entries in `.facts` at the top of `#how` (how fast, how much, where). The second and third are links to the price list and the map.
- **Where to meet** — the `#dropoff` section holds the map and one row per school. To move a pin or add a school, edit the `<li>` rows: `data-lat` / `data-lng` place the pin, the letter in `.pin` is its label, and the row's link opens Google Maps directions. The map is Leaflet with OpenStreetMap tiles (no API key). It loads when the section comes near the screen, and if it cannot load the rows are shown without it.
- **String setups** — the cards in `#pricing` carry a `data-option` that must match the `value` of an option in the form's String dropdown exactly; "Choose this setup" pre-fills it. Each dropdown option has a full `value` (what arrives in your email) and a shorter visible label (what fits on a phone). Move the `featured` class and the "Most popular" flag to whichever setup you sell most.
- **String guide** — the "Not sure?" buttons above the cards. Each button lists the cards it suggests in `data-rec` (the cards' `data-key` names, separated by spaces) and the sentence it shows in `data-note`.
- **The stringer's standard** — four entries in `#standard`. Two blocks wait there inside comments: *Your stringer* (fill in your first name and a line or two, save a square photo as `img/stringer.jpg`) and a photo gallery (machine, string close-up, finished racquets). Remove a block's comment wrapper to switch it on.
- **Serving players** — the band at the end of `#standard` states service areas and memberships. A template for real customer quotes (with permission) is in a comment below it.
- **Request form** — three steps: racquet and string, timing and drop-off, your details. Formspree receives `racquet`, `racquets`, `string`, `tension`, `timing`, `dropoff_spot`, `dropoff_time`, `name`, `email`, `notes` and `estimated_total`. The estimate is the price written in the chosen string's `value` times the number of racquets, so it follows any price you change there. A confirmation card replaces the form after a successful send.
- **Returning customers** — while the box on step 3 stays ticked, the racquet, number of racquets, string, tension and usual spot are kept in that visitor's own browser and offered back next time ("Use it" / "Forget it"). The name and email are never stored, and the saved details never leave that browser.
- **Request button in reach** — on phones a "Request stringing" button docks to the bottom of the screen while neither the hero button nor the form is on screen. On wider screens a slim bar with the menu and the button slides in at the top once the hero buttons have scrolled away (`#topbar`).

## Analytics

- **Visits** — Cloudflare Web Analytics (cookie-free). The beacon is the last script tag in `index.html`; the dashboard is in the Cloudflare account under Analytics & Logs → Web Analytics.
- **Requests sent** — after a successful send the page changes its address to `/request-sent` (no reload), which the beacon records as a page view, so the dashboard's page list shows a `request-sent` row. `request-sent.html` only redirects a reload of that address back home. Formspree's submission count stays the source of truth; ad blockers hide some beacon hits.
- **Search** — Google Search Console is verified for the whole domain through a TXT record at the registrar, so no tag is needed in the page. `sitemap.xml` is the sitemap to submit there.
