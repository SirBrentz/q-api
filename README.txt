QUALIPHY API DOCS + QUICK START
================================
Standalone subdomain bundle (e.g. docs.qualiphy.me).
Drop the entire folder at the subdomain web root.

WHAT'S NEW IN THIS DROP
-----------------------

API KEY FIELD REMOVED

The "Your API key" input on the main docs page has been
removed for security. A previously-stored value in
localStorage is auto-cleared on next page load.

ENV TOGGLE MOVED TO SIDEBAR

The Sandbox / Production segmented control now sits at the
top of the left sidebar (above the search box), where it's
easier to find and doesn't take up content-area real estate.
Live-rewrites every code block on the page when toggled.
Choice persists in localStorage.

EM/EN DASHES STRIPPED

Replaced em dashes (--) and en dashes (-) with plain hyphens
across both pages. Also re-indented every code block since
the dash-replacement regex squashed JSON indentation.

DARK-MODE LEGIBILITY FIXES

1. Default theme is now light. Removed the prefers-color-scheme
   auto-detection and the matchMedia listener. Dark only
   applies if the user has explicitly clicked the toggle.

2. Top nav buttons in dark mode now have proper contrast:
   - "Documentation" active pill uses a lavender-on-lavender-tint
     combo that's actually legible
   - "Quick start" link readable
   - "Run quick start" outline button: visible borders, readable text
   - "Get API access" primary button: deeper indigo (5D4B87) for
     better contrast against the dark page bg
   - Hero "Get a tailored API plan" button matches

3. Footer surface stays permanently dark in both themes.
   Root cause was that --ink token was used for both content
   text and surface backgrounds. Split into two tokens:
   --ink (text, flips with theme) and --ink-surface (footer,
   stays dark always). Footer columns + Quidget promo block
   render correctly in dark.

4. "Want a tailored plan for your team?" CTA panel + sidebar
   "Need a custom plan?" CTA both lock their indigo gradients
   to permanent dark hex literals so they don't flip.

5. Status-code chips (200, 400, 401, 500) inside the
   Errors & Status Codes section no longer stretch to fill
   their column. Was rendering as 200px-wide bars with 3-char
   text in the middle. Root cause: <code> elements inside a
   flex-column .param-name container were inheriting display:
   block from align-self:stretch. Fixed with display:inline-block
   + align-self:flex-start.

6. Removed redundant duplicate Quidget block in the footer.
   Only the .docs-foot-promo block remains as the single
   no-code callout.

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
