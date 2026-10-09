---
name: target-org-registry
description: Per-org lookup with canonical URL, fetch method, status, and hit-rate for deterministic sweeps
metadata:
  type: reference
---

Operational lookup for job-search sweeps. When a new org is evaluated during a sweep, add it here. When this file and `job_search_craft.md` disagree on procedure, craft is the reasoning and this file is the present status.

**Status**
- **ACTIVE** — sweep every run; live fit and a reachable application path.
- **WATCH** — check only on its cycle/date or via an alert; do not sweep every run.
- **ROSTER** — enrol once, then opportunity flow is push.
- **DEAD** — produced nothing across many runs; skip routine sweeps. Re-enter only on a user link or an aggregator hit dated in the last 14 days.
- **OUT** — excluded by a hard constraint; recorded so it is not re-surfaced.

**Method** — verified way to read the board.

**Hits** — rough count of applications or strong fits across runs.

| Org | Board | Method | Status | Note (hits) |
|---|---|---|---|---|
