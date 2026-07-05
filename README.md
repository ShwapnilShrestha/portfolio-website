# shwapnilshrestha.com.np

Personal portfolio of **Shwapnil Shrestha** — Software Engineer (C#/.NET, distributed systems), Kathmandu.

Hand-built with vanilla HTML/CSS/JS. **No framework, no build step, no dependencies** — clone it, open it, deploy it.

## Design notes

The site's two accent colors are borrowed from CQRS, the pattern behind most of the work shown:

- **Amber** = commands · writes · actions (CTAs, timeline markers for engineering roles)
- **Cyan** = queries · reads · metadata (labels, tags, academic markers)

The animated hero diagram introduces the system; the rest of the page reuses it. Typography is Archivo (variable width for display) + Martian Mono (labels/data), loaded from Google Fonts with system fallbacks. Dark theme by default, light theme via the toggle, `prefers-color-scheme` respected, `prefers-reduced-motion` respected.

## Structure

```
├── index.html          # everything: markup, styles, scripts (single file, ~45 KB)
├── 404.html            # custom not-found page
├── assets/
│   ├── Shwapnil_Shrestha_CV.pdf   # linked from "Download CV"
│   └── og-image.png               # social preview card (1200×630)
├── CNAME               # custom domain for GitHub Pages
├── robots.txt
├── sitemap.xml
├── LICENSE             # MIT (code); content rights reserved
└── .gitignore
```

## Preview locally

Just open `index.html` in a browser, or serve it:

```bash
python3 -m http.server 8000
# → http://localhost:8000
```

## Deploy

### Option A — GitHub Pages (recommended, free)

1. Create a repo (e.g. `portfolio`) and push this folder:
   ```bash
   git init && git add -A && git commit -m "Initial portfolio"
   git branch -M main
   git remote add origin git@github.com:ShwapnilShrestha/portfolio.git
   git push -u origin main
   ```
2. Repo → **Settings → Pages** → Source: `Deploy from a branch` → Branch: `main` / `/ (root)`.
3. The included `CNAME` file tells Pages to serve `shwapnilshrestha.com.np`.
4. Point DNS (below), then in **Settings → Pages** tick **Enforce HTTPS** once the certificate is issued (can take up to ~24 h after DNS propagates).

#### DNS for a `.com.np` domain

`.np` registration (via Mercantile / register.com.np) requires you to supply **nameservers** rather than raw records, so the usual setup is:

1. Create a free **Cloudflare** account, add `shwapnilshrestha.com.np`, and copy the two nameservers Cloudflare gives you.
2. Enter those nameservers in your register.com.np domain panel (or in the update request), then wait for propagation.
3. In Cloudflare DNS, add:

   | Type  | Name | Value                     |
   |-------|------|---------------------------|
   | A     | `@`  | `185.199.108.153`         |
   | A     | `@`  | `185.199.109.153`         |
   | A     | `@`  | `185.199.110.153`         |
   | A     | `@`  | `185.199.111.153`         |
   | CNAME | `www`| `shwapnilshrestha.github.io` |

   (Set the records to **DNS only** — grey cloud — at least until the GitHub certificate is issued.)
4. Verify GitHub's current IPs in their Pages docs if this ever breaks — they change rarely, but they do change.

### Option B — Netlify / Vercel / Cloudflare Pages

All three deploy a static folder in minutes: import the Git repo (or drag-and-drop the folder on Netlify), **no build command**, publish directory = root. Then add `shwapnilshrestha.com.np` as a custom domain in the dashboard and follow its DNS prompt — the Cloudflare-nameserver step above still applies for `.com.np`.

## Customizing

Everything lives in `index.html`, organized by commented sections.

- **Content**: each case study is an `<article class="case">`; timeline entries are `<article class="job">`. Edit in place.
- **Colors/typography**: all tokens are CSS custom properties at the top of the `<style>` block (`--cmd`, `--qry`, fonts, radius).
- **Add real metrics**: the strongest upgrade you can make. Where the copy says "pushed runtime performance hard" or "cut storage costs," replace with numbers when you can share them (e.g. "p95 latency −40%", "storage −30%"). Recruiters weight quantified impact heavily.
- **Photo**: optional — drop `assets/portrait.jpg` and add an `<img>` in the hero's right column above the diagram.
- **New CV**: replace `assets/Shwapnil_Shrestha_CV.pdf` (keep the filename, or update the two links).
- **Analytics**: paste a privacy-friendly snippet (Plausible, GoatCounter, Cloudflare Analytics) before `</body>`.
- **Sitemap**: bump `<lastmod>` when you make meaningful changes.

## Deliberately left out

- **Phone number** — the CV has it; the public web shouldn't (spam/scraping). Email + LinkedIn are the contact channels.
- **References' names and numbers** — never publish other people's contact details. The site says "available on request," which is the professional norm.

## License

Code: MIT. Written content, CV, and personal information: © Shwapnil Shrestha, all rights reserved.
