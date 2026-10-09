---
name: onboard
description: Set up this workspace for a new user. Interviews for personal details, ingests documents from _inbox/, maps job search lanes, sets job-search and career-event preferences, and populates memory files. Closes by explaining and offering the parachute method (room map) and introducing the red-team application review. Run once when the workspace is new.
---

# Workspace Onboarding

Interactive setup for a new user. Run through all phases in order; do not skip phases.

## Phase 1 — Identity & preferences

Ask the user, one question at a time:

1. Name and email address
2. Field or discipline (e.g. "mechanical engineering", "public health", "marketing")
3. Current role or status (e.g. "junior researcher", "between jobs", "freelance consultant")
4. Preferred English variant (British or American) — this determines spelling conventions added to CLAUDE.md
5. Location and home base
6. Open to relocation, remote-only, or hybrid? If hybrid/on-site elsewhere is acceptable, ask about commute tolerance and second-residence willingness
7. Work arrangement preferences: permanent employment, freelance/consulting, or both

After collecting answers, write `memory/user_profile.md` with frontmatter:

```
---
name: user-profile
description: <name>, <field> in <location>, <status>
metadata:
  type: user
---
```

Then update CLAUDE.md to add the user's preferred English variant as a spelling rule under Conventions.

## Phase 2 — Document ingestion

1. Ask the user to drop their files (CV, cover letters, publications, project descriptions) into the `_inbox/` folder. Accepted formats: PDF, Word (.docx), plain text, or any other readable format. Wait for them to confirm the files are there.
2. List the contents of `_inbox/` and classify each file. Ask the user to confirm or correct the classification:
   - CV / resume -> `resume/`
   - Cover letter -> `cover-letters/` (ask about tone and content tag for the `{tone}_{content}_{shortname}.md` naming convention)
   - Publication -> `publication/`
   - Project description -> `projects/`
3. For each file, convert to .md and place in the correct folder using the naming conventions from CLAUDE.md.
4. **After all conversions, remind the user:** "You should now verify the converted .md files look correct, then delete the original files from `_inbox/` to keep the workspace clean. I won't delete them for you in case you want to check the conversions first."

## Phase 3 — Search lane mapping

1. Read the ingested CV to identify subject areas, industries, and methods the user has worked in.
2. Present the extracted experience lanes and ask the user to confirm or adjust. These are the **experience lanes** (what they have done).
3. Ask: "What does your degree qualify you for beyond your direct experience?" These are the **credential lanes** (what the degree opens).
4. Ask: "Are there any interests or side passions you'd like to explore in job searches, even if they're outside your main field?" These are the **interest/passion lanes**.

Write `memory/field_map.md`:

```
---
name: field-map
description: Credential-anchored field lanes for job searching — fields where the degree is the entry ticket
metadata:
  type: user
---
```

Include the user's credential lanes with notes on which orgs or sectors each lane reaches.

Write `memory/passion_lane_map.md`:

```
---
name: passion-lane-map
description: Interest and passion lanes for job searching — the third search axis beyond experience and credentials
metadata:
  type: user
---
```

Include the user's interest lanes with notes on realistic entry points and any portfolio/credential gaps to flag.

## Phase 4 — Job search preferences

1. Ask the user to prioritise their lanes (experience, credential, interest) from highest to lowest.
2. Ask: "What platforms do you already use for job searching?" (LinkedIn, Indeed, discipline-specific boards, etc.)
3. Ask: "What are your hard filters — things that would make a role literally impossible for you?" (e.g. language requirements, specific certifications, location constraints, visa/work-permit limitations)
4. Ask: "Any soft preferences?" (seniority level, salary range, contract type, industry preferences)

Update `memory/job_search_preferences.md` with the collected answers, filling in the template sections.

## Phase 5 — Career events consultation

Job postings are one channel; in-person events reach employers before they post and build relationships a cover letter cannot. Walk the user through this, one question at a time:

1. "Would you like career and industry events to be part of your search?" If no, write "events: not wanted" in `memory/career_event_preferences.md` and skip to Phase 6.
2. "Which cities or region should I scan, and how far will you travel for a one-day event?" (Default to the home base from Phase 1.)
3. "Which event types are worth your time?" Offer the options with their typical value:
   - Job fairs: broad, often junior or trades-heavy; low value for senior profiles
   - Industry expos and trade fairs: exhibitor lists double as employer lists
   - Conferences and summits: speakers are decision-makers; some are invite-only
   - Meetups and community events: cheapest way into a local scene
   - Investor or public fairs: low-key networking, not hiring events
4. "What is the goal at events: concrete job leads, relationships with specific employers, or exploring a new field?"
5. "What is your budget for paid tickets, and how many events per month are realistic?"
6. "Are there employers or people you'd most like to meet in person?" (These become targets to look for in speaker and exhibitor lists.)

Map events to the lanes from Phase 3: experience lanes point to industry expos and conferences in the user's field; interest lanes point to expos in fields they want to enter (an event is the cheapest way to test a passion lane).

Write `memory/career_event_preferences.md`:

```
---
name: career-event-preferences
description: Whether and how the user wants career/industry events in their search; region, event types, goals, budget, target employers
metadata:
  type: user
---
```

Then offer: "Shall I run a first event scan for the next two to three months now?" If yes, follow `.claude/skills/career-events/SKILL.md` from section 3 onward (the preferences are already collected). It writes `career-events/{city}_career_events_{YYYY}_q{N}.md` with an at-a-glance table, a priority order, one section per event (relevant exhibitors and speakers, roles that fit marked verified or seen, how to work it) and a next-steps table. Verify every event date and ticket terms on the organizer's own page, and drop events that already happened.

## Phase 6 — Seed structural files

These files should already exist with headers from the template. Verify they are in place, create an empty `career-events/` folder if it is missing, and update `memory/MEMORY.md` with the index of all created files:

```markdown
- [User Profile](user_profile.md) — <name>, <field> in <location>
- [Job Search Preferences](job_search_preferences.md) — location, field priorities, platforms, work arrangement
- [Job Search Craft](job_search_craft.md) — hard filters, report format conventions, portal workarounds
- [Cover Letter Craft](cover_letter_craft.md) — drafting lessons accumulated through use
- [Field Map](field_map.md) — credential-anchored field lanes
- [Passion Lane Map](passion_lane_map.md) — interest and passion lanes, third search axis
- [Application Log](application_log.md) — single source of truth for applications and outcomes
- [Target Org Registry](target_org_registry.md) — per-org lookup for deterministic sweeps
- [Career Event Preferences](career_event_preferences.md) — region, event types, goals, budget, target employers
- [Room Map Inputs](room_map_inputs.md) — artefacts, proven way in and lanes for the room map (only if Phase 7 ran)
```

## Phase 7 — Parachute interview (optional)

Postings are one view of a field; the people and places behind them are the other. Explain the method as set out in section 0 of `.claude/skills/parachute/SKILL.md`: Bolles's hidden job market, why there is no single "job market", his four-step approach, and how this workspace runs it as a room map.

Then ask: "Shall we do the parachute interview now? Two more questions, then I research three clusters and write a map with an act-this-month list."

- If yes, follow `.claude/skills/parachute/SKILL.md` from section 1 (the explanation is done). Most inputs are already collected in Phases 1 to 4; ask only "What can you show?" and "What was your proven way in?", then continue through the research and the report.
- If no, say they can run `/parachute` any time, and move on.

## Phase 8 — Closing

Print a summary of everything that was set up:
- Files created and where they live
- Number of documents ingested
- Lanes identified
- Event preferences, and the event-scan file if one was written
- The room map file, if one was written

Then deliver these messages:

1. **Cleanup reminder:** "If you haven't already, delete the original files from `_inbox/` now that the conversions are done."

2. **Workspace maintenance tip:** "After important drafting or job-search sessions, run `/revise-claude-md` to capture style preferences and workflow lessons. If the plugin isn't installed yet, run `/install-plugin claude-md-management` from the `claude-plugins-official` marketplace."

3. **Next step:** "To test your setup, try running `/job-search` for your first sweep. If you opted into events, run `/career-events` about once a month to refresh your event plan; before each event, tell me you're going and I'll re-check the roles and help you prepare."

4. **Red team, for when you apply:** "When you go for a specific role, I can act as a second pair of eyes. Once your letter for that role is drafted, I'll offer a red-team review. It checks the letter against the posting (keywords, requirement coverage, evidence strength), attacks it the way a hiring manager and a stronger rival applicant would, and gives a chances band with the top three fixes. You can also ask for it directly with `/red-team` when you are deciding whether to apply at all."

5. **Parachute refresh** (only if Phase 7 ran): "Re-run `/parachute` monthly for the dated items and quarterly for the whole map."
