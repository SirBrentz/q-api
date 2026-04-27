QUALIPHY API DOCS + QUICK START
================================
Standalone subdomain bundle (e.g. docs.qualiphy.me).
Drop the entire folder at the subdomain web root.

WHAT'S NEW IN THIS DROP
-----------------------

ENV TOGGLE

1. Production is now the default environment. Code samples
   show api.qualiphy.me on first page load.
2. Order swapped: Production sits on the left (active by
   default), Sandbox on the right.
3. Choice persists in localStorage; switches every code block
   on the page live.

TOP NAV (DARK MODE)

4. Top nav is now styled like the left sidebar -- solid dark
   surface (#15121C) with strong-contrast nav links and
   buttons:
     - "Documentation" active pill: white text on indigo bg
     - "Quick start" link: legible mid-grey, lifts to bright
       text on hover
     - "Run quick start" outline button: visible borders,
       text contrast
     - "Get API access" primary button: lifted lavender bg
       with dark text for high contrast against the page
5. Theme toggle button: matching dark-mode borders and hover
   states so it doesn't float ghostly on the surface.

DARK-MODE CALLOUT BLOCKS (.cb-info / .cb-warn / .cb-tip / .cb-success)

6. The pastel callouts had light backgrounds with light text
   in dark mode -- washed out. Each callout now uses a subtle
   tinted-dark surface plus a 3px left-accent border in the
   accent color, plus a properly-contrasting icon:
     - Info -> lavender accent
     - Warn -> amber accent (e.g. staging deprecation, "Never
       expose your API key", "Multi-exam constraint")
     - Success -> emerald accent ("That's it.", "Ready to ship?")
     - Tip -> mid-grey accent ("For unit tests in CI",
       "Subscription pattern")

DARK-MODE INLINE CODE CHIPS

7. The small <code> chips inline in prose (like
   sandbox-api.qualiphy.me, /exam_invite, approve, etc.) now
   render as lavender-on-dark with subtle borders. Was
   washed-out and hard to read against the dark page.

DARK-MODE RECIPE / EXAM-WORKS BLOCKS

8. The "How an Exam Works" steps and recipe section blocks
   (e.g. "GFE for Aesthetic Treatment") had hardcoded white
   backgrounds. Now use subtle dark surface with proper border
   contrast. Numbered circles use the deeper indigo for
   contrast on dark.

QUIDGET CTA

9. The "Explore Quidget" footer button stays in its light-mode
   appearance (light lavender bg, dark indigo text) regardless
   of theme, since that's the look that works best for the
   call-to-action.

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
