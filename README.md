# miftah.cloud - public site

Public landing site for **mymind** by Miftah Ahmad Choiri, published with GitHub Pages at
<https://miftah.cloud>. Anyone can read it, no login.

The documentation is **not** in this repository. It is a separate private app at
<https://docs.miftah.cloud> that requires sign-in (Cloudflare Access). The menu item
"MyDocs" and the home page buttons link there.

| Part | Where |
|---|---|
| Public site (this repo) | GitHub Pages, <https://miftah.cloud> |
| Private docs | Homelab (Podman) behind Cloudflare Access, <https://docs.miftah.cloud> |

## How deployment works

Push to the `main` branch. The workflow in `.github/workflows/pages.yml` builds the site with
Jekyll and publishes it to GitHub Pages. Nothing else to do.

One-time setup in GitHub: *Settings -> Pages -> Source: GitHub Actions*, and set the custom
domain to `miftah.cloud` (the `CNAME` file in this repo already contains it).

## Preview locally

Requires Ruby 3.x and Bundler.

```bash
bundle install
bundle exec jekyll serve
```

Then open <http://127.0.0.1:4000>.

To only check that the site builds:

```bash
JEKYLL_ENV=production bundle exec jekyll build -d /tmp/mymind-site
```

## What lives here

| Path | Purpose |
|---|---|
| `index.md` | Home page (splash layout) |
| `_pages/` | About, Terms, Blog (portfolio), Sitemap, archives, 404 |
| `_posts/` | Blog posts |
| `_data/navigation.yml` | Top menu |
| `_layouts/default.html` | Layout override (loads `assets/js/scroll-top.js`) |
| `_includes/` | AdSense snippets used by the layout |
| `assets/` | Only the images used by the pages above |
| `_config.yml` | Site settings (`url` is `https://miftah.cloud`, `baseurl` is empty) |

## Rules for this repo

- Public content only. No customer names, no internal documents, no PDFs (except the resume).
- Do not add private documentation here; add it to the private docs app instead.
- Theme: `minimal-mistakes-jekyll` pinned to 4.26.2 in the `Gemfile`.

## Things to do once

- Analytics: the old Universal Analytics id was removed (that product no longer collects data).
  Create a GA4 property and set `analytics` in `_config.yml` if you want statistics.
- Google Search Console: verify `https://miftah.cloud` and put the new token in
  `google_site_verification` in `_config.yml`.
- Google AdSense: add `miftah.cloud` as a site in your AdSense account, otherwise ads will not show.
