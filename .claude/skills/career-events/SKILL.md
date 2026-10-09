---
name: career-events
description: Scan upcoming career and industry events (job fairs, expos, conferences, summits, meetups) in the user's region, match exhibitors and speakers to the user's search lanes, find open roles at those employers, and write a dated event plan with priorities and next steps. Also prepares the user for a specific event. Run monthly or before an event.
---

# Career events scan

Job postings are one channel. Events reach employers before they post and build relationships a cover letter cannot. This skill finds the events worth attending, says why, and turns each into concrete targets.

This file is the stable procedure. Evolving preferences live in `memory/career_event_preferences.md`; when the two disagree, the memory file wins.

## 1. Read, in this order

1. `memory/career_event_preferences.md`. If it is missing or says events are not wanted, ask the consultation questions in section 2 first (or stop if the user declines).
2. `memory/user_profile.md` and `memory/job_search_preferences.md` for home base, travel tolerance, seniority and hard filters.
3. `memory/field_map.md` and `memory/passion_lane_map.md` for the lanes events are matched against.
4. `memory/application_log.md`. Employers with a live application are a reason to attend (reinforce the application in person), never a new lead.
5. The most recent `career-events/*.md` file for continuity. Do not re-list events it already covers unless their dates or terms changed; update that file's outcomes instead if the user reports back.

## 2. Consultation questions (only when preferences are missing)

Ask one at a time, then write `memory/career_event_preferences.md`:

1. Should events be part of the search at all?
2. Which cities or region, and how far will you travel for a one-day event?
3. Which event types are worth your time?
   - Job fairs: broad, often junior or trades-heavy; low value for senior profiles
   - Industry expos and trade fairs: exhibitor lists double as employer lists
   - Conferences and summits: speakers are decision-makers; some are invite-only
   - Meetups and community events: cheapest way into a local scene
   - Investor or public fairs: low-key networking, not hiring events
4. Goal at events: concrete job leads, relationships with specific employers, or exploring a new field?
5. Budget for paid tickets, and how many events per month are realistic?
6. Employers or people you most want to meet in person?

Frontmatter for the memory file:

```
---
name: career-event-preferences
description: Whether and how the user wants career/industry events in their search; region, event types, goals, budget, target employers
metadata:
  type: user
---
```

## 3. Discover

Default window: the next two to three months. Search per lane, in the user's region:

- City and regional event calendars (city marketing sites, chambers of commerce, trade-fair venue calendars)
- Industry associations and clusters for each lane (they run or list the sector's conferences and expos)
- Conference and expo sites in the user's experience and interest lanes
- Event platforms: Eventbrite, Meetup, Luma, LinkedIn Events
- Career-fair organizers for the region

Map events to lanes: experience lanes point to industry expos and conferences in the user's field; interest lanes point to expos in fields they want to enter, since an event is the cheapest way to test a passion lane.

## 4. Verify and enrich

For every event that makes the list:

- Verify the date, venue, times and ticket terms on the organizer's own page. Search snippets carry last year's dates. Drop events that have already happened.
- Pull the exhibitor list, speaker list or partner list, and keep only the organizations relevant to the user's lanes.
- For those organizations, look for open roles that fit the user's profile and hard filters. Label each role:
  - **verified**: the employer's own posting page was fetched and read this run (with date and any deadline)
  - **seen**: the role appeared on LinkedIn or a job board, with its age; the user should open it before applying
- Rate fit per event as Low, Medium or High, naming the lane.

## 5. Write the plan

Write `career-events/{city}_career_events_{YYYY}_q{N}.md` (or `{region}_...` for multi-city scans):

```
# {City} Career & Industry Events, {Month} to {Month} {YYYY}
One paragraph: research date, scope, profile the events were matched against.
Status labels for roles: "verified" / "seen" as defined above.

## At a glance
| Date | Event | Venue | Cost | Fit | Why go |

**Priority order:** ranked list, one line of reasoning per event.

## 1. {Event name}, {date}
Link and ticket terms.
Relevant exhibitors / speakers (lane-relevant only).
**Roles that fit:** | Organization | Role | Status | Note |
**How to work it:** who to look for, plus a one-line pitch built from the CV.

(one section per event, in priority order)

## Next steps
| When | Action |   (keyed to event dates, registration cut-offs and application deadlines)
```

Rules: claim only what the CV evidences in pitches; flag invite-only events with how to apply for a spot; put low-value events (e.g. trades-heavy job fairs for a senior profile) last with a one-line verdict instead of a full section.

## 6. Before a specific event (prep mode)

When the user says they are going to an event:

1. Re-check every listed role at that event's organizations; update verified/seen status and note any that closed.
2. Re-check the speaker and exhibitor list for changes.
3. Give the user: three to five named targets, a 30-second introduction tailored to the event, and two questions to ask each target.
4. Offer a one-page CV variant tuned to the event's sector.

## 7. After an event

When the user reports back, add an "Outcome" line under that event in the plan file (contacts made, follow-ups promised, roles to apply to). New applications go to `memory/application_log.md` as usual. Update `memory/career_event_preferences.md` if the user's view of an event type changed.
