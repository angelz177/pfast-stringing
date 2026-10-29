# Pfast Reliable Racquet Stringing — website

Single static page (`index.html`). No build step.

## Setup (one time)

1. **Formspree** — done. The form posts to `https://formspree.io/f/xbgdonvl`; manage notifications and view submissions at https://formspree.io. Formspree's free tier allows 50 submissions/month.
2. **Prices / strings** — edit the `#pricing` rows and the radio buttons in the `#request` form.
3. **GitHub Pages** — create an empty repo on GitHub (e.g. `pfast-stringing`), then:

   ```bash
   git remote add origin git@github.com:YOUR_USER/pfast-stringing.git
   git push -u origin main
   ```

   In the repo: Settings → Pages → Source: *Deploy from a branch* → `main` / `/ (root)`. The site goes live at `https://YOUR_USER.github.io/pfast-stringing/` within a minute or two.
4. **RacquetTech** — log in at racquettech.com (Get Password link) and put the Pages URL in your stringer profile's website field so it shows up in the stringer search.

## Editing

Open `index.html` in any editor. Colors and fonts live in the `:root` block at the top of the `<style>`. The look is a tennis-court theme: hard-court blue with white court lines, white panels, ball-yellow buttons, clay-orange prices and a grass-green footer. Barlow and Barlow Semi Condensed are self-hosted in `fonts/` under the SIL Open Font License. Commit and push to redeploy.

- **Hero photo** — the masthead shows `img/hero.jpg` under a court-blue overlay. The current file is a rendered string-bed artwork; replace it with a real photo of the bench (about 1800×1000, JPG) and nothing else needs to change. The faint court lines on top are an inline SVG (`.court`) that draws itself in on load.
- **String setups** — the cards in `#pricing` carry a `data-option` that must match an option in the form's String dropdown exactly; "Choose this setup" pre-fills it. Move the `featured` class and the "Most popular" flag to whichever setup you sell most.
- **The stringer's standard** — four cards in `#standard`. A photo gallery (machine, string close-up, finished racquets) is ready in a comment there: save the three files named in the comment into `img/` and remove the comment wrapper.
- **Trusted by** — the band in `#areas` states service areas and memberships. A template for real customer quotes (with permission) is in a comment below it.
- **Request form** — three steps (racquet, string & tension, contact); the fields and names are unchanged, so Formspree receives the same submission. The turnaround line under "When do you need it?" is set in the `ETA` array in the script. A confirmation card replaces the form after a successful send.
- **Phones** — a "Request stringing" button docks to the bottom of the screen while neither the hero button nor the form is on screen.

The drop-off map in the FAQ uses Leaflet with OpenStreetMap tiles (no API key; it loads only when that FAQ item is opened). To move a pin or add a school, edit the `<li>` rows inside `#dropoff`: `data-lat` / `data-lng` place the pin, the letter in `.pin` is its label, and the *Directions* link points to Google Maps.
