# Job Applications Workspace

> **New here?** Run `/onboard` to set up this workspace with your CV, cover letters, job search preferences and career-event preferences.

## What this project is
Personal workspace for preparing job application packages — cover letters, motivation letters, proposals, CVs, opportunity research and career-event planning.

## Conventions
- **Always read `resume/` and existing letters in `cover-letters/` before starting any new task.** This gives context on background, writing style, and prior applications.
- If a detailed master CV exists in `resume/` (a complete fact bank of every role and evidenced achievement), build tailored CVs and letters from it, and add newly confirmed facts to it first.
- Letters in `cover-letters/` follow `{tone}_{content}_{shortname}.md` (tones: `narrative`, `professional`, `academic`; content tags discoverable via `ls`). Read across both axes when calibrating voice.
- File naming: snake_case with descriptive names.
- **Numbering**: every CV and cover letter filename carries a zero-padded, application-shared number prefix, e.g. `014_firstname_lastname_cv_acme_country_manager.md` and `014_professional_country_manager_acme.md`. The same number links a CV to its matching letter across the two folders and makes both sort together. Look up the next available number in the "File numbering" note near the top of `memory/application_log.md` (increment it there after use). A translation variant (`_en`) shares its base number. A CV reused across several applications carries all the numbers it serves, joined by underscores (e.g. `017_018_019_...`). Master/base CVs are reference sources, not per-application deliverables, and stay unnumbered.
- Keep each application's materials self-contained in appropriately named files.
- Do not use em dashes when preparing cover letters, motivation letters, or other application materials.
- Do not use mid-sentence colons to introduce lists; restructure into separate sentences instead.
- Never use "X is not Y, it is Z" or "not because X, but because Y" constructions.
- After drafting or editing any letter, verify with a quick grep for the mechanically detectable banned patterns (em dash, "not because", colon followed by lowercase) before showing it; this is a smoke test, not a substitute for careful drafting. This grep is for letters only, never job-search reports (see `memory/job_search_craft.md` under "The banned-pattern smoke test is letter-only").
- I edit drafts inline with `(target text) -> (comment)` annotations; always Read the file again after I say I added comments, and remove the annotations as part of the edit.
- Claim only what the active CV evidences; do not assert tool familiarity or access that is not on the CV.
- Match the document to what the posting actually asks for — "summary of research interests", "dissertation proposal outline", "motivation letter", "cover letter", and "statement of intent" are different genres with different lengths and registers; do not write a fuller, more formal document than the brief requests.
- Application packages are read together — do not reuse opening hooks, key phrases, or section structures across the letter, research statement, and other materials in the same submission.
- For application form sections (not cover letters): track which metric anchors have been used across earlier answers and avoid repeating them. Each answer is read independently but repetition across the form reads poorly.
- When a form field states a character limit (usually incl. spaces and punctuation), verify each answer's length with a quick script (e.g. `python3` `len()`) before showing it, and land ~10% under the cap, shorter where natural.
- Motivation letters should open with a concept or personal story, not a credentials recap. Form fields already carry the experience; the letter should add voice and motivation.
- After generating any cover letter or application package, assign it the next available number (per the naming convention above), name the files accordingly, and append a row to `memory/application_log.md` in the same turn (date, org, role, lane, numbered letter/package filenames, status), updating the "next available number" note. Use status `open` if it is being prepared and not yet submitted, `applied` once the user confirms submission. Do not wait for a separate request to log it.
- After drafting any new cover letter or motivation letter, run this review loop in order:
  1. **User pass.** Ask the user to read the draft and make it sound like them, either by editing the file directly or with `(target text) -> (comment)` annotations. Wait until they say they are done, then Read the file again and apply any annotations.
  2. **Agent pass.** Offer to have a fresh Opus agent review it. On a yes, spawn one (Agent tool, `model: opus`) with the letter, the posting, the active CV, `memory/cover_letter_craft.md` and the letter rules from this file. It returns ranked feedback only and does not edit the file. Its brief is clarity, the strength of the opening, evidence the CV supports but the letter misses, claims the CV does not support, repetition, and breaches of the letter rules. It must treat the user's own wording as intended voice, never as an error.
  3. **Apply and show.** Apply the feedback where it makes the letter better and keep the user's voice where the two conflict. Run the banned-pattern grep, then show the final draft with a short list of what changed and which suggestions were declined and why.
- Once the review loop is done (or skipped), offer a red-team review in one line (`/red-team`). Run it only on a yes, and only for a named role with a posting; never in sweeps, event plans or room maps.

## Workflow
- Existing letters in `cover-letters/` often surface experience details missing from the CV. Read all of them before drafting, not just 2-3; each letter was written for a different role and may contain evidence or framing that the current application needs.
- Before drafting any cover letter, also read `memory/MEMORY.md` for accumulated craft feedback.
- When searching for opportunities: use web search tools to find relevant openings.
- Tone varies by application type — match the conventions of the target (academic vs industry vs grants).

## Job search
- Run `/job-search` for a sweep. It reads `memory/job_search_preferences.md` (constraints, priorities, platforms) and `memory/job_search_craft.md` (hard-filter procedure, report format, portal workarounds) first.
- Also read the most recent `job-searches/job_search_*.md` before drafting a new run, for continuity on what was already surfaced. Output goes to `job-searches/job_search_YYYY_MM_DD.md` using today's date.
- Read `memory/application_log.md` before every run. It is the single source of truth for what has actually been applied to and how it turned out. Do not re-surface an org that has a live or rejected application there as a new Apply item. Append a row whenever the user applies (date, org, role, lane, letter/package, status), and update the status when an outcome comes in.
- Treat the log's outcomes as the strongest lane signal. A lane that only produces rejections should be reweighted down or dropped regardless of how well it fits on paper.
- Search runs on three axes: experience lanes (CV subjects), credential lanes (degree-anchored fields in `memory/field_map.md`), and passion/interest lanes (`memory/passion_lane_map.md`). Rotate at least one passion-lane pass into every run.
- Location and work-arrangement constraints live in `memory/job_search_preferences.md`; follow them as written.
- WebSearch summaries often report already-closed deadlines as active. Always verify a posting's deadline by fetching the original page before listing it under "Apply this month".

### Job search report structure
The canonical report skeleton and the report format conventions live in `memory/job_search_craft.md` under "Report format" — follow that section exactly.

## Parachute (room map)
- Run `/parachute` (Bolles's parachute method) to map the people, venues and small organisations around two or three lanes. Onboarding offers it at the end. Output goes to `room-maps/room_map_{YYYY_MM_DD}.md`; refresh the dated items monthly and the full map quarterly.

## Career events
- Run `/career-events` about once a month, or before a specific event. It reads `memory/career_event_preferences.md` and writes `career-events/{city}_career_events_{YYYY}_q{N}.md`.
- Employers with a live application in the log are a reason to attend an event, never a new lead.

## Project structure
- `resume/` — CV and resume variants
- `cover-letters/` — cover letters, motivation letters, proposals
- `publication/` — academic publications and papers
- `job-searches/` — dated reports; the most recent dated file is the working list
- `career-events/` — dated event plans (what to attend, who to meet, roles at those employers)
- `room-maps/` — dated room maps (people to engage, venues to join, small organisations, dated items)
- `application-plans/` — prep folders for planned or in-progress applications only
- `projects/` — personal project descriptions usable as letter material
- `memory/` — durable notes; start with `memory/MEMORY.md` for the index. Includes `memory/application_log.md`, the single source of truth for applications and outcomes.
- `_inbox/` — drop zone for files to convert during onboarding. Should be empty after setup.

## Maintaining this workspace
- **After important drafting or job-search sessions**, run `/revise-claude-md` to capture style preferences and workflow lessons into this file. This requires the `claude-md-management` plugin. Install it with `/install-plugin claude-md-management` from the `claude-plugins-official` marketplace.
- Writing-style rules beyond the banned patterns above are intentionally absent at first. They should accumulate organically through `/revise-claude-md` after a few drafting sessions, so the workspace adapts to your voice rather than inheriting someone else's.
