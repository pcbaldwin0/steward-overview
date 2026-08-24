# Steward

A personal household finance application for a single two-person household.

Not a commercial product. Not multi-tenant. Built and used by one family to replace
a spreadsheet.

---

## What it does

- **Accounts and balances** — a consolidated view of household checking, savings,
  credit and investment accounts
- **Recurring bills** — schedules generate dated occurrences; incoming transactions
  are matched against them so bills reconcile themselves instead of being ticked off
  by hand
- **Net worth** — assets minus liabilities, tracked over time
- **Goals** — saving toward defined targets with a projected arrival date
- **Projections** — forward cash-flow modelling from known income and recurring
  obligations

## Who uses it

Two people. One household. There is no sign-up, no other users, and no plan to
offer it to anyone else.

## What data it reads, and why

| Data | Why it is needed |
|---|---|
| Account balances | Net worth and available-cash calculations |
| Transactions | Matching payments to expected bills; categorising spending |
| Investment holdings and cost basis | Portfolio value and tax-aware reporting |
| Liabilities | Net worth is wrong without debt |

**Read-only.** The application never initiates payments, transfers or trades. It
has no write access to any financial institution and never asks for any.

## How the data is protected

- Bank access tokens are stored using envelope encryption, with the master key held
  in a managed key service that the application process never has access to. The
  database alone yields no usable credential.
- All traffic over TLS 1.3; database encrypted at rest; backups encrypted with
  separately-held keys.
- Two-factor authentication required on both user accounts.
- Credentials are never logged, never written to disk in plaintext, and never
  included in error reports.
- An append-only audit log records every authentication event, every token use, and
  every change to financial records.
- Data is never sold, shared, or provided to third parties. There are no analytics
  or advertising integrations.

## Stack

Python · FastAPI · PostgreSQL · React · TypeScript

## Status

In development. Source is kept in a private repository because it is configured
around one household's real financial data.

## Contact

p.ripping456@passfwd.com
