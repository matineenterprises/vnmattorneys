# VNM Attorneys Inc — Website

A single-page site for VNM Attorneys Inc, ready to deploy on GitHub Pages with the
custom domain `vnmattorneys.co.za`.

## Files
- `index.html` — the page
- `styles.css` — all styling
- `script.js` — mobile nav + small scroll effects
- `assets/` — logo, favicon, and a placeholder for the director's photo
- `CNAME` — tells GitHub Pages to serve this site on `vnmattorneys.co.za`

## Before you publish
- **Director's photo**: `director` section currently shows a placeholder monogram
  (`assets/director-placeholder.svg`). Save a professional photo as e.g.
  `assets/director.jpg` and update the `src` in `index.html` (search for
  `directorPhoto`).
- **Practice areas**: the list in the "Areas of Practice" section is a reasonable
  general-practice starting point, not confirmed content — check it with Vangeli
  and edit the `<div class="practice-card">` blocks in `index.html` as needed.

## 1. Push to GitHub
```bash
cd vnm-site
git init
git add .
git commit -m "Initial site"
git branch -M main
git remote add origin https://github.com/<your-username>/<repo-name>.git
git push -u origin main
```

## 2. Turn on GitHub Pages
1. On GitHub, open the repo → **Settings → Pages**.
2. Under **Build and deployment → Source**, choose **Deploy from a branch**.
3. Branch: `main`, folder: `/ (root)` → **Save**.
4. Under **Custom domain**, enter `vnmattorneys.co.za` and save (this reads the
   `CNAME` file already in the repo, so it should pre-fill automatically).

GitHub will show a message that DNS isn't configured yet — that's expected until
step 3 below is done. It can take a few minutes to a few hours to verify.

## 3. Point the domain at GitHub Pages
Do this wherever `vnmattorneys.co.za` is registered/managed (its DNS zone) —
based on the earlier screenshot that's the HostAfrica client area.

For the **apex domain** (`vnmattorneys.co.za`, no `www`), add four **A records**
all pointing to GitHub Pages:

| Type | Host | Value            |
|------|------|------------------|
| A    | @    | 185.199.108.153  |
| A    | @    | 185.199.109.153  |
| A    | @    | 185.199.110.153  |
| A    | @    | 185.199.111.153  |

For `www.vnmattorneys.co.za` (recommended so both work), add:

| Type  | Host | Value                        |
|-------|------|------------------------------|
| CNAME | www  | `<your-username>.github.io.` |

Then back in **Settings → Pages**, once DNS has propagated, tick **Enforce HTTPS**.

DNS changes usually take effect within an hour, but can take up to 24–48 hours
depending on the registrar's TTL settings.

## Notes
- This is a static site — no backend, no build step. Editing is just editing
  the HTML/CSS/JS files directly and pushing again.
- The "Book a Consultation" and phone/WhatsApp links go straight to `tel:`,
  `mailto:`, and `wa.me` links — there's no contact form to wire up or host.
