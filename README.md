# Choreia Flow IN

India edition of Choreia Flow — the CRM for **M2labo Bharat Pvt. Ltd.** (fresh produce / strawberries, GST-exempt goods). A single-file SPA (`index.html`) that uses Google Sheets as its backend and Google Identity Services for sign-in.

## Sales pipeline

`Lead → Quotation → PI Issued → Paid → Shipped → Closed` (plus `Lost`).

India runs on advance payment: revenue counts from **Paid** onward (`Paid`, `Shipped`, `Closed`).

## Documents

Generated from a Google Sheets template (set in Flow Settings) into the customer's Drive folder:

- **Quotation / Proforma Invoice (PI)**
- **Delivery Challan**
- **Bill of Supply** — exempt goods, **no tax lines are ever written** (document number gets a `B` suffix)

Amounts are plain INR with Indian digit grouping (`en-IN`, e.g. ₹1,00,000).

## Quote numbering

Indian fiscal-year series (FY starts in April): `VB/FY{yy}-{yy2}/{seq4}`, e.g. July 2026 → `VB/FY26-27/0001`. Issued numbers are recorded in the `QuoteRegistry` sheet of the Flow spreadsheet; the next number is the max sequence for the current FY prefix + 1.

## Backend sheets

Created automatically in the configured shared-drive folder: `Customers`, `Deals`, `Activities`, `Cards`, `ActivityTargets`, `PhaseHistory`, `QuoteRegistry` (all English headers).

## Config & login

- Per-domain config file on Drive: **`choreia-flow-in-config.json`** — deliberately different from the Japanese edition's filename, so JP and IN never share config or data.
- Shares the Choreia login/domain model: users sign in with their organisation Google account (`@m2-labo.in`); consumer domains are blocked. The `choreia_token` localStorage key is intentionally shared across Choreia apps (single sign-on behaviour).

## Deployment

Pushing to the repository deploys via GitHub Pages — a push to the default branch is a production release.
