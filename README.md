# adavaria.github.io

Personal website and CV of Ali Davari. It's a plain static site (HTML + CSS + a little JS) with no build step, hosted on GitHub Pages at **https://adavaria.github.io**.

## Layout
```
index.html             all page content (one section per CV block)
404.html               "page not found" page
assets/css/style.css   styling, light/dark theme, mobile layout
assets/js/main.js      mobile menu, theme toggle, active nav link
assets/img/            favicon, profile photo, hobby photos
assets/cv/             downloadable CV PDF
.nojekyll              tells GitHub Pages to serve files as-is
```

## Preview locally
```bash
python3 -m http.server 8000
# open http://localhost:8000
```

## Common edits
- **Update the CV PDF:** copy the new PDF over `assets/cv/CV_Ali_Davari.pdf` (source: the `CV-general` project, `final/CV_Ali_Davari.pdf`).
- **Add a profile photo:** save a square image as `assets/img/profile.jpg`. In `index.html`, replace `<div class="avatar-placeholder" ...>AD</div>` with `<img src="assets/img/profile.jpg" alt="Ali Davari">`.
- **Add hobbies or a photo gallery:** put images in `assets/img/hobbies/`, then uncomment the `HOBBIES` section and the `Hobbies` nav link in `index.html`.
- **Add a publication:** copy one `<li class="pub">` block in the Publications section.
- **Change the accent color:** edit `--accent` in `assets/css/style.css`.

## Deploy (first time)
1. On GitHub, create a **public** repo named exactly `adavaria.github.io` (no README).
2. Push:
   ```bash
   git remote add origin https://github.com/adavaria/adavaria.github.io.git
   git push -u origin main
   ```
3. Repo → **Settings → Pages** → Source: *Deploy from a branch*, Branch: `main` / `(root)`.
4. The site is live at https://adavaria.github.io within about a minute. Each later push redeploys it automatically.

## Custom domain (later)
1. Buy a domain (e.g. Cloudflare, Namecheap, Porkbun).
2. At the registrar, add DNS records:
   - Apex (`example.com`): four `A` records → `185.199.108.153`, `185.199.109.153`, `185.199.110.153`, `185.199.111.153`
   - `www`: `CNAME` → `adavaria.github.io`
3. Repo → **Settings → Pages → Custom domain**: enter the domain, then tick **Enforce HTTPS** once the certificate is issued. GitHub then commits a `CNAME` file to the repo.
