QUALIPHY API DOCS + SETUP WIZARD
=================================
Standalone subdomain bundle (e.g. docs.qualiphy.me).
Drop the entire folder at the subdomain web root.

WHAT'S NEW IN THIS DROP
-----------------------

1. Email plan button removed.
   The mailto: approach was unreliable across email clients and many
   users don't have a default mail handler configured. Removed
   entirely along with the now-pointless "Your developer's email"
   field on Step 0 of the wizard.

2. One-click PDF download.
   The "Download as PDF" button is now the primary CTA on the result
   page. Clicking it generates and downloads a real PDF directly --
   no print dialog, no "Save as PDF" choice, just a file. Output is
   real searchable PDF text, not a screenshot.

   Implementation:
     - Loads jsPDF (~50KB gzipped) from cdnjs at page load
     - downloadPdf() builds a multi-page PDF programmatically using
       the same data that powers the on-screen plan
     - Filename auto-set to:
       Qualiphy-API-integration-plan-{Company}.pdf
     - PDF includes: header strip, summary card with all wizard
       answers, 5 numbered sections (Portal setup with checkboxes,
       Endpoints, Sample API call with code block + warning callout,
       Testing with checkboxes, Receiving results with bulleted
       three-event lifecycle), links footer, page numbers
     - Theme-matched: indigo numbered headers, monospace cURL block
       with header strip, real checkboxes that print as boxes
     - Letter page size, 50pt margins, helvetica + courier fonts
       (no external font files, works offline once loaded)

   See sample-plan.pdf in this folder for what the output looks like.
   Two pages for a typical plan, ~21KB.

3. Glyph rendering fixed.
   Earlier draft had right-arrow and em-dash characters that don't
   render in jsPDF's default Helvetica encoding (showed as garbage).
   Now uses ASCII-safe equivalents inside PDF strings ("->" instead
   of "→", "-" instead of "—"). The on-screen UI keeps the proper
   typographic glyphs since browsers handle them fine.

4. Obsolete print stylesheet removed.
   The previous attempt used window.print() with an @media print
   block (~58 lines of CSS). All gone now since the PDF is built
   directly in JS.

DEPLOYMENT
----------
Folder structure:

  /index.html                      Docs landing (subdomain root)
  /integrations/index.html         Setup wizard
  /assets/fonts/Gilroy-*           Display fonts
  /favicon.ico, .png, etc.         Favicons
  /sample-plan.pdf                 Example PDF output (delete on deploy)
  /README.txt                      This file (delete on deploy)

After deploying:
  - Update <link rel="canonical"> and <meta property="og:url"> in
    both files if your subdomain isn't docs.qualiphy.me.
  - Delete README.txt and sample-plan.pdf -- they're for review only.
