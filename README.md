# Zetwerk Bond Desk – static deploy (GitHub + Render)

## Files
- `index.html` – the whole app (HTML, CSS and JavaScript in one file)
- `seed.json` – starting data: Surety Bond Tracker (domestic + international), insurers, entities, stamp duty
- `SECI_70MW_tender_extract.pdf` – sample tender for the "Read the tender" demo

## Deploy on Render
1. Push these three files to the root of a GitHub repo.
2. In Render: **New → Static Site**, connect the repo.
3. Build command: leave empty. Publish directory: `.`
4. Deploy. The app opens at the Render URL.

## How it behaves on Render (outside claude.ai)
| Feature | On claude.ai (artifact) | On Render (this static build) |
|---|---|---|
| Data | Shared database, everyone sees the same requests | Saved in each person's browser only (localStorage) |
| Sign-in | claude.ai account linked to a Bond Desk user | No sign-in; use "Signed in as" to switch demo users |
| Uploaded files | Kept in the uploader's browser; download from there | Same: kept in the uploader's browser (IndexedDB) |
| Downloads (Excel, payment advice PDF, files) | Through the claude.ai download prompt | Normal browser download |
| Read tender with Claude (OCR) | Live | Demo values only (no Claude access) |

## What the production build needs (not in this static file)
- A backend and database (shared data, audit log, approvals across users)
- File storage (S3 / Azure Blob / GCS) so every document opens for everyone
- SSO (Google Workspace / Azure AD) for sign-in and roles
- OCR service for tender, PI and final bond
- Phase 2 integrations: OMS (PI → invoice → UTR back) and the CSO mailbox
