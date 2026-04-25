QUALIPHY API DOCS + QUICK START
================================
Standalone subdomain bundle (e.g. docs.qualiphy.me).
Drop the entire folder at the subdomain web root.

WHAT'S NEW IN THIS DROP
-----------------------

LAYOUT FIXES

1. Code-block overflow.
   The docs-shell grid was using "grid-template-columns: 280px
   1fr" which doesn't permit the main column to shrink below
   the intrinsic min-width of its content. When a long line
   appeared in a code block (e.g. the signed CloudFront URL in
   the webhook event 2 example, ~540 chars), the entire main
   column expanded to fit it, forcing horizontal page-scroll on
   smaller viewports.

   Fix: changed to "grid-template-columns: 280px minmax(0, 1fr)"
   so the main column can shrink. Combined with max-width:100%
   on .codeblock, long lines now scroll WITHIN the code block
   instead of expanding the layout.

   Verified at 1000px viewport: page-level horizontal scroll is
   gone. Only the one block with the genuinely long URL has
   internal x-scroll, which is the intended UX for code samples.

2. Sidebar covers footer.
   The <footer> was a child of <div class="docs-shell"> with
   "grid-column: 1 / -1" — meant to span the full grid width
   below the columns. But the sticky sidebar with
   "height: calc(100vh - 64px)" extended over the footer's left
   column on tall pages.

   Fix: moved the <footer> outside the docs-shell grid entirely.
   It's now a normal block sibling. Removed the now-unnecessary
   "grid-column: 1 / -1" from the footer CSS.

   Verified: at the bottom of the page, sidebar's last visible
   item ends above the footer with clean separation. No overlap.

DEPLOYMENT
----------
Folder structure:

  /index.html                      Docs landing (subdomain root)
  /quick-start/index.html          Quick start curated flow
  /assets/fonts/Gilroy-*           Display fonts
  /favicon.ico, .png, etc.         Favicons
  /sample-plan.pdf                 Example PDF output (delete on deploy)
  /README.txt                      This file (delete on deploy)

After deploying:
  - Update <link rel="canonical"> and <meta property="og:url">
    in both files if your subdomain isn't docs.qualiphy.me.
  - Delete README.txt and sample-plan.pdf -- they're for review.
