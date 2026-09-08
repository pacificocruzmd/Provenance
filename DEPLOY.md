# Deploying Provenance to Netlify

This folder is a plain, dependency-free static site — 21 HTML pages, no build
step, no npm install. Any of the following works.

## Option A — drag and drop (fastest)

1. Go to [app.netlify.com/drop](https://app.netlify.com/drop).
2. Drag this whole folder onto the page.
3. Netlify gives you a live `*.netlify.app` URL immediately.

## Option B — Netlify CLI

```bash
npm install -g netlify-cli
cd netlify_export
netlify deploy --prod
```

## Option C — connect a Git repo

Push this folder to a GitHub/GitLab/Bitbucket repo, then in Netlify choose
"Import an existing project" and point it at the repo. Since there's no
build step, set:

- Build command: *(leave blank)*
- Publish directory: `.` (already set in `netlify.toml`)

## What's in here

- `index.html` — homepage (the canvas source calls this "Main"; it's
  renamed here so the bare domain resolves).
- 19 other content pages (about, services, journal, the individual
  procedure pages, consultation, locations, contact, privacy, etc.).
- `404.html` — a branded not-found page, wired up via `netlify.toml`.
- `netlify.toml` — publish directory + basic security headers + the 404 rule.
- `robots.txt` / `sitemap.xml` — basic SEO plumbing.

## Custom domain

Once deployed, add your domain under **Site settings → Domain management**
and follow Netlify's DNS instructions (either delegate the domain to Netlify
DNS, or add the CNAME/ALIAS record it gives you).

## Before you consider this launch-ready

- Every `[BRACKETED PLACEHOLDER]` on the site (inquiry email, consultation
  phone number, several photo placeholders, the Journal's opening-date
  entry, a few procedure-specific specifics) is a stand-in for a real fact
  or asset that still needs to be supplied.
- Photos are dashed placeholder boxes throughout — there are no real images
  in this export yet.
- This export has no contact-form backend. The Contact page's form fields
  (if/when added) would need a Netlify Forms attribute or another form
  handler wired in before they'll actually submit anywhere.
- If the practice wants analytics, cookie consent, or a live chat widget,
  none of that is wired in — this is intentionally a bare, no-tracking
  static export (the Privacy Notice page currently states the site "does
  not use cookies, analytics, or third-party tracking scripts," so keep
  that copy in sync with whatever gets added later).

## Keeping this in sync with the design canvas

This export was generated from the same `build_site.py` that produces the
Claude Design canvas (`export_netlify.py`, in the parent folder). If the
canvas gets edited again later, re-run `python3 export_netlify.py` to
regenerate this folder from the latest content before redeploying.
