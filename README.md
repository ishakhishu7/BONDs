# Zetwerk Bond Desk – static deploy (GitHub + Render)

## Files
- `index.html` – the whole app (HTML, CSS and JavaScript in one file)
- `seed.json` – starting data: Surety Bond Tracker (domestic + international), insurers, entities, stamp duty
- `SECI_70MW_tender_extract.pdf` – sample tender for the "Read the tender" demo

## Deploy on Render (free, static, no API key)
1. Push these files to the root of the GitHub repo: `index.html`, `seed.json`, `SECI_70MW_tender_extract.pdf`, `README.md`.
2. Render: keep your existing **Static Site** (build command empty, publish directory `.`). It redeploys on commit.

Documents are read on the device: text PDFs directly, scans with the free browser OCR, plus your templates and learned rules. No Claude API, no cost.

## How it behaves on Render
| Feature | On claude.ai (artifact) | On Render |
|---|---|---|
| Data | Shared database, everyone sees the same requests | Saved in each person's browser only |
| Read LOA / tender | Claude (your claude.ai account) | On the device (free) |
| Review on document, templates, learned rules | Yes | Yes (saved in that browser) |

## Teaching the reader
- **Learned reading rules** (Masters): when someone corrects a field that was read from a document and submits the request, a rule is saved for that document format (e.g. BPCL LOA). Claude gets the rules with every document; on-device reading uses the label. Edit or switch off any rule in Masters.
- **Document templates** (Masters): boxes drawn on "Review on document", applied to every document with the same match text.
- **Reading accuracy** (Setup): how often each field was right, corrected or missed.

## What the production build needs (not in this static file)
- A backend and database (shared data, audit log, approvals across users)
- File storage (S3 / Azure Blob / GCS) so every document opens for everyone
- SSO (Google Workspace / Azure AD) for sign-in and roles
- OCR service for tender, PI and final bond
- Phase 2 integrations: OMS (PI → invoice → UTR back) and the CSO mailbox
