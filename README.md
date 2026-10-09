# Pfast Reliable Racquet Stringing — website

Single static page (`index.html`). No build step.

## Setup (one time)

1. **Formspree** — sign up at https://formspree.io (free tier is plenty), create a form pointed at `zpropertytexas@gmail.com`, and copy the form ID. In `index.html`, replace `YOUR_FORM_ID` in the form's `action` with it. Until then, submitting the form opens the visitor's email app instead.
2. **Prices / strings** — edit the `#pricing` rows and the radio buttons in the `#request` form.
3. **GitHub Pages** — create an empty repo on GitHub (e.g. `pfast-stringing`), then:

   ```bash
   git remote add origin git@github.com:YOUR_USER/pfast-stringing.git
   git push -u origin main
   ```

   In the repo: Settings → Pages → Source: *Deploy from a branch* → `main` / `/ (root)`. The site goes live at `https://YOUR_USER.github.io/pfast-stringing/` within a minute or two.
4. **RacquetTech** — log in at racquettech.com (Get Password link) and put the Pages URL in your stringer profile's website field so it shows up in the stringer search.

## Editing

Open `index.html` in any editor. Colors live in the `:root` block at the top of the `<style>`. Commit and push to redeploy.
