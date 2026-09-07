# Stuff for Sailors — Website

A 5-page static site: Home, Catalog, About, Custom Order (all 4 forms), Contact.
Matches your sister's finished brand — logo, teal accent, black headline type.

## Recent updates (this batch)
- Facebook/Instagram links now point to your real pages, everywhere they appear
- Product images added to each order form (Washboard, Binocular, VHF; the
  General form shows the logo, since it's a catch-all with no single product)
- Liability disclaimer added in three places: a visible callout on the Custom
  Order page (before the forms), a shorter line on the Catalog page, and in
  the footer of every page. Wording: not for mission-critical or life-safety
  use, not a substitute for certified rigging or safety equipment. Consider
  having this reviewed by your attorney before relying on it.
- Homepage logo made more prominent: bigger in the nav, plus a large circular
  logo badge overlapping the hero product image
- Formspree endpoints wired in for all 5 forms (4 order forms + contact)

## Files
```
index.html      → Home
catalog.html    → Catalog
about.html      → About / founder story
order.html      → All 4 custom order forms (Washboard, Binocular, VHF, General)
contact.html    → Contact page
styles.css      → Shared design system — edit colors/fonts here, once, for the whole site
images/         → logo, product renders, social icons
downloads/      → Word-doc versions of the 4 order forms (backup download links)
```

## STEP 1 — Get the order forms actually working (do this first)

The forms on order.html and contact.html are wired to send submissions to your
email, but they need a real endpoint — right now they point to a placeholder
(`https://formspree.io/f/YOUR_FORM_ID`) that won't work until you fix it.

1. Go to **formspree.io** and make a free account (50 submissions/month free —
   plenty to start; upgrade later if you outgrow it).
2. Create a new form, set the destination to **sailoratlarge@stuffforsailors.com**.
3. Formspree gives you a URL like `https://formspree.io/f/abcd1234`.
4. Open each of the 5 `<form ... action="...">` tags (4 in order.html, 1 in
   contact.html) and replace `https://formspree.io/f/YOUR_FORM_ID` with your
   real URL. You can use the same form ID for all 5, or make a separate
   Formspree form per product if you want submissions pre-sorted.
5. Find-and-replace is the fastest way: search for `YOUR_FORM_ID` across both
   files and swap in your real ID.

(Web3Forms.com is a similar free alternative if you'd rather use that instead.)

## STEP 2 — Put it on GitHub Pages (free hosting)

1. Create a free account at **github.com** if you don't have one.
2. Create a **new repository** — name it anything, e.g. `stuff-for-sailors-site`.
   Make it Public (required for free GitHub Pages).
3. Upload all the files in this folder to that repository (drag-and-drop
   works on github.com — click "Add file" → "Upload files").
   **Keep the folder structure** — `images/` and `downloads/` need to stay as
   subfolders, not get flattened.
4. In the repository, go to **Settings → Pages**.
5. Under "Source," choose the `main` branch and `/ (root)` folder → Save.
6. GitHub gives you a live URL like `https://yourusername.github.io/stuff-for-sailors-site/`
   — check it loads correctly before moving to Step 3.

## STEP 3 — Point your domain (stuffforsailors.com) at GitHub Pages

Your domain is registered through Squarespace, but it can point anywhere.

1. In your GitHub repo → **Settings → Pages**, add your custom domain
   (`stuffforsailors.com`) in the "Custom domain" box → Save. This creates a
   `CNAME` file in your repo automatically.
2. Log into **Squarespace Domains** (where you manage the domain, separate
   from their website builder) → find `stuffforsailors.com` → DNS settings.
3. Add these DNS records (GitHub's current official values — double-check
   at **docs.github.com** search "Managing a custom domain" in case they've
   changed):
   - Four **A records** for the root domain (`@`) pointing to:
     `185.199.108.153`, `185.199.109.153`, `185.199.110.153`, `185.199.111.153`
   - One **CNAME record** for `www` pointing to `yourusername.github.io`
4. DNS changes take anywhere from a few minutes to 24 hours to propagate.
5. Back in GitHub repo Settings → Pages, once it detects the DNS is correct,
   check "Enforce HTTPS" for a secure padlock on the site.

If any of this trips you up, GitHub's own docs (search "GitHub Pages custom
domain") walk through it with screenshots, or bring the error back here and
I'll help troubleshoot.

## Editing the site later

- **Text changes**: open the relevant `.html` file in any text editor, find
  the sentence, edit it, save, re-upload to GitHub (or use GitHub's own
  in-browser editor — click the pencil icon on any file in the repo).
- **Colors/fonts**: everything is controlled from `styles.css` — the teal,
  black, fonts, spacing are all defined once at the top (`:root` section) and
  used everywhere, so a single edit updates the whole site.
- **New product photos**: replace files in `images/`, keeping the same
  filenames, and they'll update everywhere automatically. Once you have real
  installation photos, swap them in for the CAD renders.
- **Updated order forms**: if you edit the Word docs, re-export and replace
  the files in `downloads/` with the same filenames.

## What this site does NOT include yet

- Real installation photos (using CAD renders for now, per your call)
- The gift line (soap, keychains) — teased on the catalog page as "coming soon"
- Any e-commerce/checkout — orders come in as requests, you quote and invoice
  manually, matching your current process
- Analytics — consider adding a free tool like Plausible or GoatCounter later
  if you want to see visitor traffic
