# Application Log

Single source of truth for what has actually been applied to and how it turned out. Append a row on every new application; update the status when an outcome comes in.

**Status vocabulary**
- `applied` — submitted, awaiting reply
- `rejected` — declined
- `no-response` — submitted, never heard back
- `interview` — reached interview / further stage
- `offer` — offered
- `open` — in preparation, posting still live
- `unconfirmed` — no evidence that it was submitted
- `archived` — not pursued

Rows sitting at `applied` for 60+ days with no reply get flagged at the next check to flip to `no-response`.

**External tracker** (optional): if you also track applications in Notion, a spreadsheet or similar, note it here. This log holds the imported copy, and job-search runs read only this log.

**File numbering**: every CV and cover letter carries a zero-padded, application-shared number prefix (e.g. `001_firstname_lastname_cv_acme_marketing_manager.md` and `001_professional_marketing_manager_acme.md`) so a CV and its matching letter sort together. A CV reused across several applications carries all the numbers it serves. Master/base CVs are unnumbered reference sources. Next available number: **001**.

## Applications

| Date | Org | Role | Lane | Files | Status | Notes |
|---|---|---|---|---|---|---|

## Lane signal

*(Summarize which lanes produce interviews and which only produce rejections, once there are outcomes.)*
