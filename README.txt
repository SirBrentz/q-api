QUALIPHY API DOCS + QUICK START
================================
Standalone subdomain bundle (e.g. docs.qualiphy.me).
Drop the entire folder at the subdomain web root.

WHAT'S NEW IN THIS DROP
-----------------------

NAV / TOP-OF-PAGE

1. Removed "Reference" link from the top nav on both pages.
   This site fully replaces api-docs.qualiphy.me, so the
   outbound link no longer makes sense.

2. Removed all 11 outbound "Full reference" links to
   api-docs.qualiphy.me from endpoint sections, plus the
   "Canonical reference" footer link, plus the now-unused
   .canonical-link CSS.

3. Removed redundant "Canonical API: api-docs.qualiphy.me/"
   references from the wizard's email-body template and PDF.
   Kept the Postman collection link since that's a legitimate
   static asset.

EMAIL VALIDATION TIMING

4. The email-format error message on Quick start step 0 ONLY
   surfaces when the user tries to Continue with a malformed
   email -- not on blur, not on initial load. Verified end-to-end:
     - On load: error hidden
     - After bad email + click elsewhere (blur): error stays hidden
     - After click Continue with bad email: error appears
   The Continue button stays disabled until all three fields
   have any value, then the format check fires on click.

FOOTER

5. New "Prefer no code? / Use Quidget for WordPress." promo
   block added above the column grid. Linear-gradient background,
   lavender CTA button "Explore Quidget" that opens
   https://quidget.qualiphy.me in a new tab.

6. Footer columns cleaned up: duplicate Quick start link removed,
   buried Quidget link consolidated into the promo block.

DOCS HERO

7. Single CTA: "Get a tailored API plan for your team" with
   explanatory subtext below. No secondary button.

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
  - Delete README.txt and sample-plan.pdf -- they're for review only.
