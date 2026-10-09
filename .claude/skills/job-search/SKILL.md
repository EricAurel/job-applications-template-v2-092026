---
name: job-search
description: Run a job-search sweep. Reads preferences, craft, registry, and the application log; applies hard filters at first sight; sweeps experience, credential, and interest lanes with verified fetch methods; channel-switches when empty; gates every Apply entry before writing the dated report; updates the registry afterwards.
---

# Job search run

This file is the stable procedure skeleton only. Every evolving rule (filters, report format, org statuses, channel lists) lives in `memory/` and is read fresh each run. When this file and a memory file disagree, the memory file wins and this file should be updated to match.

## 1. Read, in this order

Memory is read as a **filter and cache**, not as the search space. These files tell you what to skip, how to fetch a known board, and what not to repeat. They do NOT define where to look — discovery happens in the open web (Step 2).

1. `memory/job_search_preferences.md` for constraints, lane definitions, and the hard filters.
2. `memory/job_search_craft.md` for procedure rules, the canonical report skeleton, and portal workarounds.
3. `memory/target_org_registry.md` as a cache/skip-list: skip DEAD orgs, and look up the verified fetch method when a known org surfaces in discovery. Not the list to sweep.
4. `memory/application_log.md` (if the user keeps an external tracker such as Notion or a spreadsheet, the log holds the imported copy; do not read the external tracker during a search run). Never re-surface an org with a live or rejected application as a new Apply item. Use the lane-signal block for weighting.
5. The most recent `job-searches/job_search_*.md` for continuity. Work through its "Next run" notes, but never re-list or re-verify its roles: reports contain new finds only, and the prior report stays the working list for its own roles.

## 2. Sweep — discovery first, registry as cache

The search space is the open web, NOT the registry. Spend the first and largest part of every run finding employers not already tracked. The registry is a cache you consult while triaging hits, never the list you sweep.

- **Start in open-world channels, per lane** (experience / credential / interest): fresh-posting searches that return arbitrary employers — LinkedIn date-sorted (`site:linkedin.com/jobs`), remote aggregators, discipline-specific boards, and any field-relevant platforms from `job_search_preferences.md`. Fetch the canonical live board; never trust WebSearch snippets (they return years-stale postings).
- **Use the registry as a cache during triage:** when a hit is a known org, use its verified fetch method and its DEAD/skip status; when it is new, run it against the hard filters and add it to the registry afterwards.
- **Exploration quota:** every run must evaluate employers not previously in the registry. If a lane's discovery channels are dry or blocked, name the blocked channel — "re-confirmed the known orgs, nothing new" never stands as a search result.
- Geographic scope follows `job_search_preferences.md`: sweep the home base first, then the wider areas the user accepts (commute, second residence, remote), in the sort order written there.
- Rotate at least one passion/interest-lane pass into every run. Hard-filter at first sight of a disqualifier; do not research a role past its disqualifier.

## 3. If the sweep comes back empty

Zero Apply candidates is a channel signal, never a finding. Run the channel-switch protocol in `job_search_craft.md` before writing anything.

## 4. Gate, then write

Before a role enters "Apply this month", check all five. Any failure moves it to "Worth a browser check" or a one-line dead-end instead.

1. The canonical posting page was fetched with a 200 this run. A real posting page; an application-form shell or a careers landing page does not count.
2. The role detail and a future deadline were both read from that fetch, and the entry carries a "verified live on <domain> as of <date>" stamp.
3. The org has no live or rejected application in `application_log.md`.
4. The org is not DEAD/OUT in the registry, and the role is not one the user has declined by name.
5. The deadline is in the future. Rolling deadlines require a positive currency signal dated within 30 days instead.

Then write `job-searches/job_search_YYYY_MM_DD.md` (today's date) exactly per the canonical skeleton in `job_search_craft.md` under "Report format".

## 5. After writing

- Update `memory/target_org_registry.md` rows touched this run (status, hits, dates, newly verified fetch methods).
- Record genuinely new procedure lessons in `memory/job_search_craft.md` with **Why:** and **How to apply:** lines; reflect any skeleton-level change back into this file.
- Do not edit `application_log.md` unless the user applied or reported an outcome.
