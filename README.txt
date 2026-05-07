QUALIPHY API DOCS + QUICK START
================================
Standalone subdomain bundle for api-docs.qualiphy.me.
Drop the entire folder at the subdomain web root.


HOSTING
-------
Static files only — works on any static host (GitHub Pages, Cloudflare
Pages, Netlify, S3+CloudFront, plain Nginx, etc.). No build step.

The /CNAME file at the root tells GitHub Pages to serve at
api-docs.qualiphy.me. On other hosts it's harmless and ignorable.

DNS (handled by whoever manages qualiphy.me):
  api-docs.qualiphy.me   CNAME   sirbrentz.github.io.
  (For non-GitHub hosts, use whatever target the host gives you.)

After DNS propagates, GitHub Pages auto-issues a Let's Encrypt
certificate; HTTPS works without further action.


FOLDER STRUCTURE
----------------
  /index.html                  Docs landing (subdomain root)
  /quick-start/index.html      Quick Start curated flow
  /dashboard/index.html        Internal observability dashboard
                               (password-gated; not crawled — see robots.txt)
  /assets/fonts/Gilroy-*       Display fonts
  /favicon.ico, .png, etc.     Favicons
  /CNAME                       GitHub Pages custom-domain marker
  /robots.txt                  Allow root + quick-start; disallow dashboard
  /sitemap.xml                 Two-URL sitemap

  /sample-plan.pdf             Example PDF — DELETE before deploy
  /dashboard/SETUP.txt         Internal setup notes — DELETE before deploy
  /README.txt                  This file — DELETE before deploy


CHECKLIST BEFORE HANDING OFF TO HOST
------------------------------------
  [ ] Delete README.txt
  [ ] Delete sample-plan.pdf
  [ ] Delete dashboard/SETUP.txt
  [ ] Confirm CNAME contains: api-docs.qualiphy.me
  [ ] Confirm canonical/og:url use api-docs.qualiphy.me in both
      index.html and quick-start/index.html (already updated in this drop)
  [ ] Confirm WEBHOOK_URL in index.html, quick-start/index.html, and
      dashboard/index.html points at the live Apps Script /exec URL
      (already wired)


CHANGING THE SUBDOMAIN LATER
----------------------------
If the deploy URL ever changes:
  1. Update /CNAME to the new hostname.
  2. Update <link rel="canonical"> and <meta property="og:url"> in
     /index.html and /quick-start/index.html.
  3. Update the DNS record at the registrar.
  4. Update /robots.txt and /sitemap.xml if you want the sitemap link
     to reflect the new host.
