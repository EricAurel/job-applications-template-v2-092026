---
name: parachute
description: The parachute method (after Richard Bolles). Explains the hidden job market to the user, then maps the rooms around the user's field instead of hunting postings: reachable people, the places they gather, the small organisations where a founder reads applications, and the money that funds them. Interviews for the two inputs onboarding does not cover, runs three research clusters in parallel with strict verification, and writes a dated room map with an act-this-month list. Run at the end of onboarding, then monthly for dated items and quarterly in full.
---

# Parachute: map the room before you hunt the job

## 0. Explain the method first

Before any questions, explain the idea to the user in your own words, briefly, covering these points:

- **Where it comes from.** Richard Bolles, author of *What Color Is Your Parachute?*, popularised the idea that most vacancies are filled through contacts, referrals and direct approaches before they reach a public job board. He put the share as high as 80%. Present that as his claim; figures in the 70 to 80% range circulate widely but are estimates, not measured data.
- **There is no single "job market".** Bolles called it a metaphor. Employers and candidates who would fit each other pass on the street without knowing, because there is no one place where they meet.
- **The parachute approach** replaces mass-sending CVs to postings with four steps:
  1. A self-inventory of skills, values and preferred working conditions (his "Flower Exercise").
  2. Research into specific organisations that match that profile.
  3. Informational interviews to build relationships inside them.
  4. Approaching the people who hire before a formal opening is announced.
- **How this workspace runs it.** Step 1 is mostly done already (the CV, lanes and preferences from onboarding, plus two questions below). Steps 2 and 3 are the room map: the organisations, the reachable people and the places they gather. Step 4 is the playbook at the end, where an application names a real exchange and links something you made.

Then ask whether they want to continue. If not, stop here and mention they can run `/parachute` any time.

## Why the map works

Postings are the last thing a field produces, and by the time one is public, hundreds of people have seen it. The jobs that go to outsiders go through a person who recognised the name, at an organisation small enough that the founder reads the applications. This skill maps those people, the places they gather and the money behind small organisations. Roles fall out of the map as a by-product, and the ones that do are the ones the user can actually get.

## 1. Collect the inputs

Most inputs already exist after onboarding. Read them, then ask only for what is missing, one question at a time.

| Input | Source |
|---|---|
| Lanes (two or three, named as a practitioner would) | `memory/field_map.md`, `memory/passion_lane_map.md`, `memory/job_search_preferences.md` (lane priority) |
| Base and reach | `memory/user_profile.md`, `memory/job_search_preferences.md` |
| Record in three lines | the CV in `resume/` (draft it, ask the user to confirm) |
| Languages and constraints | `memory/job_search_preferences.md` (hard filters) |
| What I can show | **ask**: "What exists outside your CV? A project, portfolio, published piece, a community you ran, a tool you built." Check `projects/` and `publication/` first and propose candidates. |
| My proven way in | **ask**: "Think of the one time you got into a new field. Who recognised your name, and where had they seen it?" |

Ask the user to pick two or three lanes for this map if they have more. Save the answers to `memory/room_map_inputs.md` (frontmatter `name: room-map-inputs`, `type: user`) so later runs skip the interview, and add it to `memory/MEMORY.md`.

## 2. Propose the three clusters

Propose three clusters from the lanes and let the user confirm or adjust. A typical split:
1. The core organisations of the lane and their people.
2. The adjacent or supplier organisations where the same skills are hired under other titles.
3. The money and gatekeeper layer: funders, associations, programmes, local institutions.

## 3. Research, one task per cluster, in parallel

Launch one research agent per cluster in parallel (Agent tool). If agents are unavailable, run the clusters one after another. Give each agent the inputs and this brief:

1. **Organisations (20 to 30):** name, city or remote, approximate team size, what it does in one line, how it is funded, careers URL, social handle, whether it has roles of the user's kind, remote-friendliness. Prefer organisations under about 40 people where a founder or lead reads applications.
2. **People (30 to 50):** name, role and organisation, the handle on the platform the field uses, what they post about, a reachability signal (posts often, replies to small accounts, runs a newsletter or podcast with an open inbox, follower tier), and a hook linking their work to something the user can show. Rank founders and leads of small organisations above famous names. Include the newsletter and podcast people who route the field.
3. **Where to join (20 to 30):** venue, type (Discord, Slack, forum, course, meetup, conference, newsletter, job board, advising service), URL, how to get in, cost, next date if findable, what a newcomer gets. Check Meetup, Luma and Eventbrite calendars by name for the user's city, plus the city's industry associations and co-working spaces; local events are real but often invisible to plain search.
4. **How this room works (under 250 words):** what gets engagement, whether founders read direct messages, the standard junior entry path, and the fastest way to skip steps.
5. **Live leads:** any open role, call, fellowship, programme or deadline found on the way, with the date as shown on the original page.

**Verification rules** (pass these to every agent verbatim):
- Verify every handle on the person's or organisation's own site, a conference speaker page, or a search result showing the exact profile URL. Mark each VERIFIED or UNVERIFIED. Never guess a handle.
- Verify every URL by fetching it or by a search result showing the exact URL.
- Never present a role or deadline from a search snippet. Read the original posting page. A blocked page is a fetch problem, not a closed role.
- Follower counts and reply habits are estimates when platforms block anonymous reads; label them as such.
- Say where you hit limits (search caps, blocked sites) rather than filling gaps from memory.

If one cluster comes back thin, offer a second pass on the cluster that matters most.

## 4. Cross-check against the workspace

- Read `memory/application_log.md`. An org with a live or rejected application is context (a person to know there), never a new lead.
- Respect the hard filters in `memory/job_search_preferences.md`; drop live leads that fail them at first sight.
- Add newly found organisations with a careers page to `memory/target_org_registry.md` (status WATCH unless they have a fitting open role).
- Venues with a date go to the user's attention in the report; if the user uses `/career-events`, note that the next event scan should include them.

## 5. Filter and write

Write `room-maps/room_map_{YYYY_MM_DD}.md` with:
1. **Act this month:** every dated item, soonest first, deadlines verified on the original page.
2. **Twelve people to engage first,** chosen for reachability and fit, one line each on why.
3. **Second tier** of about twenty to follow and reply to when natural.
4. **Where to join,** in the order to join, local venues named.
5. **Live roles seen on the way,** marked "not yet assessed" (assess them with `/job-search` rules before applying).
6. **How the rooms work,** a paragraph per cluster.
7. **Verification limits.**

Put the full tables in `room-maps/room_map_{YYYY_MM_DD}_tables.md`. Create `room-maps/` if missing.

## 6. Hand over the playbook

End the report, and the chat reply, with this order of use:
1. **Join the venues and listen** for two weeks before posting. Learn what gets engagement in each room.
2. **Reply with information, never with an introduction.** First contact is a public reply that adds a fact, correction or data point. A short, specific direct message comes a week later. Once there is an exchange, ask for a twenty-minute informational interview with one concrete question about their work. A cold "Can we have a quick chat" goes unanswered.
3. **Put one artefact in front of the room:** a write-up, demo, dataset or number the room has a use for.
4. **Take the unpaid seat** if one exists (ambassador, volunteer, organiser, moderator).
5. **Apply with links, not templates.** When a mapped role opens, the letter names the exchange the user had with someone there and links the artefact. Offer `/red-team` on that application.
6. **Do the dated items first.** Courses, fellowships, conference applications and funder calls have deadlines; jobs are rolling.

Remind the user: open every profile and check the bio matches the person before messaging (one verified handle was still wrong when this was first run), and confirm reachability by looking at the person's last twenty posts.

## 7. Refresh cadence

A map goes stale in weeks. Re-run section 5's "Act this month" monthly, and the whole map quarterly or whenever sweeps keep returning the same names. On a re-run, read the latest `room-maps/` file first and mark who has moved, which items expired, and which people the user has already engaged.
