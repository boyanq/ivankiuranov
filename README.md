# Ivan Kiuranov — website

Static portfolio site for contemporary artist Ivan Kiuranov, published with GitHub Pages at
**[ivankiuranov.com](https://ivankiuranov.com)**. Originally built on Webflow
([ivankiuranov.webflow.io](https://ivankiuranov.webflow.io)).

Plain HTML and CSS, no build step. Everything is in this repo except the
[Satoshi](https://www.fontshare.com/fonts/satoshi) variable font, which loads from Fontshare's CDN
instead of being committed here, because its license restricts redistributing the font files.

## Structure

| Path | URL |
|------|-----|
| `index.html` | `/` — works grid and short bio |
| `about/index.html` | `/about/` — biography and press |
| `work/project-1/index.html` … `project-4/` | `/work/project-1/` … — one page per artwork |
| `404.html` | Shown by GitHub Pages for any missing URL |
| `assets/css/style.css` | All site styles (breakpoints: 991px, 767px, 479px) |
| `assets/js/` | jQuery + webflow.js (mobile menu) |
| `assets/images/` | Artwork images, avatar, icons |
| `CNAME` | Custom domain for GitHub Pages |
| `sitemap.xml`, `robots.txt` | For search engines |
| `favicon.ico`, `apple-touch-icon.png`, `assets/images/icon.svg` | Site icons |

Links use root-relative paths (`/about/`, `/assets/...`) so they work from any page, including
the 404 page at any depth. The site must therefore be served from the root of a domain.

## Preview locally

Serve the folder from its root; opening the files directly won't resolve the `/…` paths.

```sh
python3 -m http.server 8000
# open http://localhost:8000
```

## Publishing on GitHub Pages

1. Push `main` to GitHub (`boyanq/ivankiuranov`).
2. In the repo, open **Settings → Pages**:
   - **Source:** Deploy from a branch → `main`, folder `/ (root)`.
   - **Custom domain:** `ivankiuranov.com` (already set by the `CNAME` file).
3. At your domain registrar, add these DNS records:

   | Type | Name | Value |
   |------|------|-------|
   | A | `@` | `185.199.108.153` |
   | A | `@` | `185.199.109.153` |
   | A | `@` | `185.199.110.153` |
   | A | `@` | `185.199.111.153` |
   | AAAA | `@` | `2606:50c0:8000::153` |
   | AAAA | `@` | `2606:50c0:8001::153` |
   | AAAA | `@` | `2606:50c0:8002::153` |
   | AAAA | `@` | `2606:50c0:8003::153` |
   | CNAME | `www` | `boyanq.github.io` |

4. Once the DNS check passes in **Settings → Pages**, tick **Enforce HTTPS**
   (the certificate can take up to an hour to be issued).

Optionally, [verify the domain](https://docs.github.com/en/pages/configuring-a-custom-domain-for-your-github-pages-site/verifying-your-custom-domain-for-github-pages)
in your GitHub account settings so no other account can claim it.

## Adding a new artwork

1. Add the images to `assets/images/`.
2. Copy `work/project-1/` to a new folder (e.g. `work/project-5/`) and update the title,
   description, canonical/`og:` URLs and image.
3. Add a card for it to the works grid in `index.html`.
4. Add the URL to `sitemap.xml`.
