# AGENTS.md — australian_accounts

Entry file for any AI agent or person working in this repository. It is tool-neutral. `CLAUDE.md` imports it, so
edit this file, not that one.

## What this repository is
Frappe app: "Accounts additions and customisations for Australian market" (README). DocTypes for BAS and PAYG set-up,
Business Activity Statements, PAYG Payment Summaries and Salary Slip YTD, two workspaces (Australian Payroll,
Australian Reporting) and a payroll client script. `hooks.py` names the publisher as Oneiric Group Pty Ltd: it is a
third-party app uploaded here as files.

**Legacy.** Three commits, all on 5 Feb 2024 ("Add files via upload"); nothing since. Where it runs, if anywhere,
is not recorded in this repo (unverified).

## Read first
The estate's rules live in `AL2018/littlecocoa-docs`. Read them in this order before working here:
1. `docs/cc-briefs/METHOD-02-how-we-work.md`: how Alan, the architect and the coder work. Always first.
2. `docs/cc-briefs/PRODUCTION-INTEGRITY-RULE.md`: what may touch production, and how.
3. `docs/cc-briefs/ACCEPTANCE-CRITERIA-RULE.md` and `docs/cc-briefs/OPERATING-STANDARDS-v1.0.md`.
4. `docs/cc-briefs/CC_STANDING_RULES_v0.9.md` (v0.9 governs; earlier versions are superseded).
5. `docs/architecture/GOTCHAS.md`: the single register of known traps.
Then this file, then the repo's own docs.

## Rules that bite here
A short digest; the documents above are the source, and this list is a cache.
- Production is changed only through the application or its API, never by direct SQL. Staging first.
- The default branch is protected: feature branch, then PR. Deploys name both the branch and the commit.
- No secrets in the repo. AI never sends a message to anyone outside the team.
- Australian English in copy and comments.
- Never declare `frappe` (or `erpnext`) as a pip dependency. uv cannot resolve it, because frappe's own metadata carries `PyPika @ git+https://...` and uv rejects transitive URL dependencies (fixed in dieline and Silent-Print-ERPNext, 28–29 Jul 2026). Bench provides frappe. `requirements.txt` here still lists `frappe` and `setup.py` reads it, so this app has the uv problem until that is changed the same way.
- Legacy code: don't build on it without a brief. Australian BAS, PAYG and payroll work in the estate happens in the workstreams recorded in littlecocoa-docs, not here.

## Structure
- `australian_accounts/australian_accounts/doctype/`: the DocTypes listed above, with their stock test stubs.
- `australian_accounts/fixtures/`: Custom Field and Workspace fixtures.
- `australian_accounts/custom_scripts/payroll.js`: payroll client script.
- `australian_accounts/hooks.py`, `setup.py`, `requirements.txt`.

## Conventions
- Default branch `main`. No tests beyond the generated stubs; no CI.
- Whether this app is installed on any site is not recorded in this repo (unverified). Any deploy is Alan's, on Frappe Cloud, by branch and SHA, after staging.

## Current state
Not kept here: entry files describe the repo, not the week. See `AL2018/littlecocoa-docs`
`docs/handoffs/STATUS-LEDGER.md` and the workstream folder under `docs/` for this repo.
