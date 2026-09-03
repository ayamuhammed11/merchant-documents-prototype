# Merchant Documents — prototype

The **Documents** tab of a merchant account in the Kashier back office.

Open it: https://ayamuhammed11.github.io/merchant-documents-prototype/

## What it shows

- **All documents** — one listing for every document on the account, replacing the
  earlier Required / Additional split. The account type sits above it, and
  *Download all* / *Upload document* sit to the right of the section title,
  directly over the listing. The listing is paginated, with a rows-per-page
  control. Uploaded By reflects who actually filed a document — Bank Statement
  and Proof of Address, the two types a merchant typically self-uploads, show
  the account owner's name rather than the agent's email.
- **Document details drawer** — clicking any row opens it, with three tabs:
  - *Details* — preview, document details, and **Previous Versions**: a
    dropdown listing every superseded upload for that type (kept rather than
    deleted), with the selected version's file(s), uploader and date shown
    below it, and a Download that acts on whichever version is currently
    picked. Commercial Registration is seeded with a real V1 → V2 history to
    show this; other types show "No previous versions" until re-uploaded.
  - *Document info fields* — the editable form, validated live against that
    type's definition.
  - *Audit Logs* — this document's own history.
- **Row menu (⋮)** — *Preview* opens the same document details drawer a
  row-click does. *Download* is a single action normally, or a small picker
  — current version plus each previous one, dated — when a type has more
  than one version on file.
- **Upload document drawer** — pick a document type, and the drawer reshapes
  itself to that type's **file upload rule** as authored in Document Types:
  - *Single file* — one dropzone; a second file replaces the first.
  - *Multiple — fixed labels* — one required slot per named label
    (National ID asks for Front side and Back side separately).
  - *Multiple — no labels* — any number of files.

  Upload stays disabled until the rule is satisfied, and the footer names what is
  still missing. Accepted formats and the per-file size cap come from the same
  definition and are enforced, saying what was refused and why. Re-uploading a
  type supersedes its current version rather than replacing it outright — the
  old one moves into Previous Versions.
- **Events** — everything done on the tab and inside its documents: uploads,
  downloads, and the info fields captured or changed on each document (opening
  a preview isn't logged, since nothing changes or moves). Each entry is
  chipped with the document it belongs to, or *This tab* for account-level
  actions. Paginated, newest first.

## Notes

It is a single self-contained HTML file — no build step, no dependencies beyond
Google Fonts. Open `index.html` directly, or serve the folder.

Values captured in the info fields persist to `localStorage`, so a reload keeps
them, as does the event and version history. The *Simulate: no documents
uploaded* control flips the tab to an account with nothing uploaded, and back.

Document types, their info fields and their file rules are read from the
Document Types module when it has been used in the same browser; otherwise the
page falls back to the same definitions that module ships with.

Sidebar navigation is decorative — this prototype is the Documents tab only.
