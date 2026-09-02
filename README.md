# Merchant Documents — prototype

The **Documents** tab of a merchant account in the Kashier back office.

Open it: https://ayamuhammed11.github.io/merchant-documents-prototype/

## What it shows

- **All documents** — one listing for every document on the account, replacing the
  earlier Required / Additional split. The account type sits above it, and
  *Download all* / *Upload document* sit to the right of the section title,
  directly over the listing.
- **Document details drawer** — clicking any row opens it, with three tabs:
  *Details* (preview and document details), *Document info fields* (the editable
  form, validated live against that type's definition), and *Audit Logs*.
- **Upload document drawer** — pick a document type from the predefined set, attach
  files by browsing or drag & drop. A type not yet on the account appears as a new
  row at V1; a type already on file is superseded at the next version.

## Notes

It is a single self-contained HTML file — no build step, no dependencies beyond
Google Fonts. Open `index.html` directly, or serve the folder.

Values captured in the info fields persist to `localStorage`, so a reload keeps
them. The *Simulate: no documents uploaded* control flips the tab to an account
with nothing uploaded, and back.

Sidebar navigation is decorative — this prototype is the Documents tab only.
