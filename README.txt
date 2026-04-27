QUALIPHY API DOCS + QUICK START
================================
Standalone subdomain bundle (e.g. docs.qualiphy.me).
Drop the entire folder at the subdomain web root.

WHAT'S NEW IN THIS DROP
-----------------------

CALLOUT-INTERNAL CODE CHIPS NOW MATCH THE REST OF THE SITE

The inline <code> chips inside notice/callout blocks (info,
warn, tip, success) had a special override that forced their
background to a semi-transparent white. This worked OK in
light mode but looked out of place in dark mode -- the
white-ish chips clashed against the dark callout surface.

Removed the override. Code chips inside callouts now inherit
the same styling as every other inline <code> on the page:
  - Light: lavender-mist bg, indigo text
  - Dark:  lavender at 10% opacity bg, light lavender text

Affected examples (now consistent):
  - "That's it. Switch the base URL from sandbox-api to api"
  - "January 1, 2026... should use sandbox-api.qualiphy.me/"
  - "watch the custom_pharmacy mapping"
  - Any cb-info / cb-warn / cb-tip / cb-success block with
    inline code references inside

DEPLOYMENT
----------
Folder structure:

  /index.html                      Docs landing (subdomain root)
  /quick-start/index.html          Quick start curated flow
  /assets/fonts/Gilroy-*           Display fonts
  /favicon.ico, .png, etc.         Favicons
  /sample-plan.pdf                 Example PDF (delete on deploy)
  /README.txt                      This file (delete on deploy)

After deploying:
  - Update <link rel="canonical"> and <meta property="og:url">
    in both files if your subdomain isn't docs.qualiphy.me.
  - Delete README.txt and sample-plan.pdf.
