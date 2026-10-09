---
name: job-search-craft
description: Lessons learned across job search runs — hard filters during search, report format conventions, and portal workarounds
metadata:
  type: feedback
---

*(Starter lessons from an earlier workspace. New lessons get appended with **Why:** and **How to apply:** lines as runs teach them.)*

## Hard filters during search

During search (not at report-writing time), discard roles that fail a hard filter from `job_search_preferences.md`. Filter at first sight of the disqualifier; do not research the deadline or draft a write-up first.

**Why:** Filtering on "is this an interesting role?" rather than running candidates against hard constraints first wastes sweep budget on roles that should have been dropped immediately.

**How to apply:** When reading a posting, ask: would the answer be "I literally cannot do this role" (hard filter, drop now) or "I'd need to think about it" (soft constraint, keep researching, surface with a note).

## Zero Apply roles is a tactic signal, not a finding

When a sweep produces no Apply-this-month role, that is the trigger to switch search channels *before writing anything*, not a result to report. Absence of results is almost always a channel problem, not a market fact. Do not conclude "thin-supply week" or characterize the market as scarce.

**How to apply:** If a lane's sweep comes back empty, do not write the report yet. Try different channels (aggregators, direct org boards, consultancy platforms, tender boards, VC portfolio boards) first. Only after they are exhausted does an empty Apply section get written, and then as a single terse line.

## Report format

Job search reports should surface job detail and suppress process narration. The skeleton below is canonical; it is the whole report, nothing else. Output goes to `job-searches/job_search_YYYY_MM_DD.md` using today's date.

```
# Job Search YYYY-MM-DD
One sentence on focus this run.

## Apply this month
[Full entry per role: Link, Location, Deadline (with "verified live on <domain> as of <date>"),
Terms, Topic/profile, Requirements, Note if non-obvious. New roles only, enough depth
to decide without re-opening the posting.]

## Worth a browser check
- One-liners for promising roles whose canonical page could not be verified this run, with the link.

## Track / watch
- One-liners only, with next-cycle date. Include only if a real future date exists. Skip the section otherwise.

## Next run (agent notes)
- Try: short list of platforms/orgs to add next time.
- Dead-end this run: short list. One line total.
```

Banned sections (resist re-adding): "Sources scanned" / "Filters applied" preamble, "Expired since last run", "Sources tried, nothing actionable" with per-source paragraphs, "Platform rotation note", "Conclusion" that re-ranks Apply entries in prose, per-job "Profile fit" field.

**Why:** The reader uses these reports only to decide what to apply for. Process narration adds length without signal.

## Carry-overs are never re-listed

Reports contain newly surfaced roles only. A role that appeared in any earlier report does not re-enter a later one. The prior dated report remains the working list for its own roles.

## Listing currency — Apply-this-month requires direct verification

A role enters Apply-this-month only when the canonical posting page was fetched successfully (200 OK) and the role description and application route were extracted from it during this run. If the canonical page returns 403/404 or an empty JavaScript shell, the role goes into "Worth a browser check", never Apply. Apply and browser-check are mutually exclusive states.

**Why:** Aggregator and search-index snippets persist weeks after a role closes. Promoting a role to Apply based on stale index data produces false positives.

## The banned-pattern smoke test is letter-only

Do not run the em-dash / "not because" / colon-lowercase grep on a job-search report. It is a letter-craft gate. Reports are decision lists written in normal prose.

## Every run is discovery-first; the registry is a cache, not the search space

Spend the first and largest part of every run finding employers not already tracked. The registry (`target_org_registry.md`) is a cache consulted during triage (skip dead orgs, look up verified fetch methods), never the org list to sweep. Every run must evaluate employers not previously in the registry.

## LinkedIn guest search-result pages are the best date-sorted discovery channel

`linkedin.com/jobs/search/?keywords=<terms>&location=<City>%2C%20<Country>&f_TPR=r604800&sortBy=DD` returns job cards with title, company, city, and "posted N days ago" without a login. Use `f_TPR=r2592000` for 30 days. Individual `linkedin.com/jobs/view/` pages, by contrast, render unreliably and sometimes return an unrelated page; check that the returned content matches the title you fetched.

**How to apply:** For a city-scoped run, start with 6-12 function-word queries (one per interest area, plus "head of", "chief of staff", "product owner" style queries), then verify each promising hit on the employer's own board. The age shown is a currency signal but reposts reset it, so it never replaces the canonical fetch.

## Blocked portal workaround

When a job-board portal returns 403/404 or an empty shell, do not log the role as dead on that basis. Many are JavaScript apps whose content the fetcher cannot see.

**Default workaround order:**
1. The ATS's public JSON API (see below).
2. The company's own careers site, which often mirrors the same postings in a server-rendered template (search `"<company>" careers`).
3. A `site:domain.tld <keyword>` search, since the search index has the rendered content.
4. Aggregator triangulation, cross-checked, since aggregators can be months stale.
5. "Worth a browser check" in the report, with the link.

**Blocked is not the same as dead.** A portal that explicitly confirms closure ("expired", "no longer available") means closed. A portal that merely fails to fetch stays a lead to retry.

## ATS platforms: what renders and what has an API

- **Render fully to a direct fetch:** Greenhouse (`job-boards.greenhouse.io`, `job-boards.eu.greenhouse.io`), Deel, Teamtailor, Personio, join.com, and often Lever (try one direct fetch before writing a Lever board off).
- **Usually render only a title shell:** Ashby, Workable, Workday.
- **Public JSON APIs** (use these first for blocked boards and large boards):
  - Ashby: `api.ashbyhq.com/posting-api/job-board/<org>` (full descriptions plus publish dates)
  - Greenhouse: `boards-api.greenhouse.io/v1/boards/<org>/jobs` (full list with `updated_at`; filter by location instead of paging the HTML)
  - Lever: `api.lever.co/v0/postings/<org>?mode=json` (createdAt exposes evergreen postings; the API can miss live roles, so fall back to `jobs.lever.co/<org>`)
  - Recruitee: `<org>.recruitee.com/api/offers/`
- Greenhouse's `.eu.` versus bare subdomain is not predictable per org; if one 404s, try the other.
- A Greenhouse job ID that redirects to the board root means that posting is closed. Re-fetch the live board and ask for the specific title's current link instead of retrying the ID.

## False negatives and false positives to watch for

- **"Position filled" can be a fallback page.** Some Workday-style sites serve a static "filled" page to non-browser fetchers while the role is live. If the user sees a live apply page at the same URL, the user's observation wins. A real HTTP 410 Gone is still trustworthy.
- **"0 open positions" on a recruiting sub-portal** (hire.*, jobs.*) can be a JavaScript list that didn't load. Fetch the organization's main careers page before writing the role off.
- **A careers page can render no listings while its search endpoint does.** Try the job portal's search URL with a location query.
- **Search-hit URLs on the employer's own domain can be stale.** Being on the canonical domain does not skip the "fetch and check for a closure notice" step. If several in a row are closed, re-sweep the live listing page instead.
- **Regional aggregator hub pages mix in closed roles.** Confirm on the org's own board or company page before a role appears in any report.
- **Short-ID job URLs can be reassigned** to a different posting weeks later. Re-fetch a re-shared link and verify the title it returns.
- **Mirror metadata can be wrong** (location, remote eligibility) even when the requirements text is accurate. When the user has the live posting open, defer to what they see.
- **WebSearch/WebFetch summaries can invent statistics** (counts, breakdowns). Trust only concrete, checkable facts from them, and never repeat an aggregate count in a report.

## Re-sweep fast-hiring orgs on reliable boards

An org on a reliably fetchable board can produce new fits run after run. Do not let ACTIVE status become a reason to skip its re-sweep; such boards are cheap to re-check.

## Registry claims need cross-checking against the application log

A registry note saying an application is "open in log" can be wrong. Before it gates a new find, grep `application_log.md` for the org. If the org is not there, correct the registry row in place.

## VC portfolio job boards: Getro and Consider APIs

Most VC "portfolio jobs" boards render with JavaScript, but two platforms behind them have JSON APIs.
- **Getro** (find the network id as `"network":{"id":` in the page HTML): `POST https://api.getro.com/api/v2/collections/<id>/search/jobs` with headers `Content-Type: application/json` and `Accept: application/json` (without Accept it returns 406), body `{"hitsPerPage":100,"page":0,"filters":{"searchable_locations":["<Country>"]},"query":""}`.
- **Consider** (e.g. a16z, Sequoia, Kleiner Perkins, Battery, NEA, Lightspeed, Bessemer boards): fetch `https://<host>/jobs` with a cookie jar, read `csrfToken` from the HTML, then `POST https://<host>/api-boards/search-jobs` with header `x-csrf-token` and body `{"meta":{"size":100},"board":{"id":"<slug>","isParent":true},"query":{"locations":["<Country>"]}}`; paginate with `meta.sequence`.

**How to apply:** Filter the API results by function, then verify each shortlisted role on its own ATS before it enters Apply. Board data can lag behind the employer's ATS.
