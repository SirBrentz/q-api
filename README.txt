QUALIPHY API DOCS + QUICK START
================================
Standalone subdomain bundle (e.g. docs.qualiphy.me).
Drop the entire folder at the subdomain web root.

WHAT'S NEW IN THIS DROP
-----------------------

This drop adds three of the requested feature improvements
end-to-end, plus the foundation for the rest. The remaining
four are listed at the bottom under "Coming next" -- they
require a follow-up round to ship cleanly.

SHIPPED THIS ROUND

1. Dark mode.
   Full dark-theme support. Toggle button (sun / moon icon)
   sits in the top-right nav, next to "Run quick start."
   - Theme stored in localStorage and persisted across visits
   - Auto-respects the user's OS preference on first visit
   - Early-init script runs before first paint to prevent flash
   - Smooth color transitions only AFTER first paint
   - All surfaces, borders, code blocks, and accent colors
     flip cleanly. Lifted indigo / emerald / amber values for
     legibility on dark.

2. Sandbox / Production environment toggle.
   New settings strip at the top of the docs page (above the
   hero) with a Sandbox / Production segmented control. Toggle
   live-rewrites every code block on the page:
     - Sandbox -> sandbox-api.qualiphy.me
     - Production -> api.qualiphy.me
   - Choice persisted in localStorage
   - Operates on a snapshot of the original code, so toggling
     is reversible

3. Live API key field.
   Right next to the env toggle: a password-style text input
   labeled "Your API key." Pasting a key live-substitutes
   YOUR_API_KEY in every code block on the page (whether the
   placeholder appears with quotes or without).
   - Stored only in localStorage (NEVER transmitted)
   - Shows / hides the key with the eye icon
   - Hint text under the field: "Saved only in your browser.
     Never sent to Qualiphy."
   - Debounced 250ms so the page doesn't re-render on every
     keystroke

4. Code line numbers.
   Every code block now has a left gutter with line numbers,
   styled with the same monospace font and a faint border
   between the gutter and the code.
   - Numbers auto-increment via CSS counter
   - Numbers are unselectable (won't show up in copied text)
   - Copy button still copies clean code without the numbers

INFRASTRUCTURE LAID FOR (BUT NOT YET WIRED)

The CSS variable system was refactored so the 4 remaining
features can be added as small additive changes:
  - --code-bg, --code-border, --code-text, --code-head, etc.
    are now tokens that flip cleanly with theme
  - --shadow-sm, --shadow-md tokens
  - All hardcoded surface colors inside the codeblock,
    sidebar search, fcard, and param-table swapped to
    var() lookups

COMING NEXT

5. Response status-code tabs (200 / 400 / 401 / 500) on every
   endpoint section. Currently the response example only shows
   the 200 case.
6. "Copy as Postman" alongside the existing Copy button on
   every code sample. Drops a ready-to-import collection JSON.
7. Right-rail "On this page" mini-TOC for long endpoint pages
   (Required -> Common Optional -> Pharmacy Routing -> Response
   -> 401 errors).
8. Inline "Test this endpoint" runner (deferred -- this requires
   either a CORS-friendly sandbox response from the Qualiphy
   API or a small backend proxy. Worth a security review before
   shipping a public endpoint runner against the real API).

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
  - Delete README.txt and sample-plan.pdf -- they're for
    review only.
