# Job Applications Workspace (template)

A Claude Code workspace for running a job search: tailored CVs and cover letters, regular job-search sweeps, career-event planning, and an application log that keeps it all honest.

## Getting started

1. Copy this folder somewhere on your computer and rename it (e.g. `my-job-applications`).
2. Open the folder in Claude Code (terminal, desktop app or VS Code extension).
3. Put your CV, any past cover letters, publications and project descriptions into `_inbox/`.
4. Type `/onboard`. Claude interviews you (profile, search lanes, job-search preferences, career events), converts your documents, and fills in the `memory/` files.
5. Optional but recommended: run `/install-plugin claude-md-management` from the `claude-plugins-official` marketplace, so `/revise-claude-md` can save your writing preferences after drafting sessions.

## Commands

| Command | What it does |
|---|---|
| `/onboard` | One-time setup. Run first. |
| `/job-search` | A sweep for fresh postings across your lanes, written to `job-searches/job_search_YYYY_MM_DD.md`. |
| `/career-events` | Scans upcoming job fairs, expos, conferences and meetups in your region, matches exhibitors and speakers to your lanes, and writes an event plan to `career-events/`. Tell Claude when you're going to an event to get a prep briefing. |
| `/parachute` | The parachute method, after Richard Bolles: most jobs are filled before they are posted. Maps the people, venues and small organisations around your lanes, so you hear about roles early. Offered at the end of onboarding. |
| `/red-team` | A second pair of eyes for one specific application. Checks your letter against the posting and attacks it like a hiring manager would. Offered after a letter is drafted. |

For letters and CVs, just ask (e.g. "draft a cover letter for this posting: <link>"). Every package gets a number and a row in `memory/application_log.md`.

## How the process works

The workspace runs two searches side by side. The visible one hunts public postings. The hidden one maps the people and places where most jobs are filled before anyone posts them. Both feed into the same applications and the same log.

### 1. Set up once (`/onboard`)

Claude interviews you one question at a time and builds your profile.

- **Who you are:** name, field, status, location, how far you'll commute, and the work arrangements you'll accept.
- **Your documents:** the files in `_inbox/` are converted to Markdown and sorted into `resume/`, `cover-letters/`, `publication/` and `projects/`.
- **Your search lanes,** on three axes. *Experience lanes* are what you have done. *Credential lanes* are what your degree opens. *Interest lanes* are fields you'd like to explore.
- **Your preferences:** lane priority, platforms, hard filters (anything that rules a role out) and soft preferences.
- **Career events:** whether you want them, where, which types, and your budget.

At the end, Claude explains the parachute method and offers to run it straight away (step 3). It also tells you about the red-team review for later applications (step 5).

### 2. Sweep the postings (`/job-search`)

Run it whenever you want fresh openings. Claude searches your lanes, drops anything that fails your hard filters, and verifies every deadline on the original posting page. Search summaries often list closed roles as open, which is why this check matters. The result is a dated report in `job-searches/`, with the roles worth applying to this month at the top.

### 3. Map the room (`/parachute`)

This step is based on Richard Bolles, author of *What Color Is Your Parachute?*. He argued that most vacancies are filled through contacts and direct approaches before they reach a job board, and he put the share as high as 80%. That figure is his estimate, not a measured number, but the pattern holds in most fields. Jobs that go to outsiders usually go through someone who recognised the name, at an organisation small enough that the founder reads the applications.

Claude asks two questions on top of your onboarding answers. *What can you show* outside your CV (a project, a portfolio, something you published or built)? And *how did you get in* the last time you entered a new field? It then researches three clusters around your lanes and builds a map of:

- **Small organisations** where a founder or lead reads applications.
- **Reachable people**, ranked by how likely they are to reply, with a link to something you can show them.
- **Places to join**, such as communities, newsletters, meetups and local events.
- **Dated items**, such as calls, fellowships and courses with deadlines.

Every social handle and link is checked and marked verified or unverified. The map goes to `room-maps/` with an "act this month" list. Then you use it, in this order:

1. Join the venues and listen for two weeks.
2. Make first contact with a public reply that adds something useful, not with an introduction.
3. Once you've had a real exchange with someone, ask them for a short informational interview.
4. Put one thing you made in front of the room.
5. When a role opens, apply with links and name the conversation you had, instead of sending a template.

Re-run `/parachute` monthly for the dated items and quarterly for the whole map.

### 4. Meet people in person (`/career-events`)

About once a month, Claude scans job fairs, expos, conferences and meetups in your region. It matches the exhibitors and speakers to your lanes and finds open roles at those employers. Before an event, tell Claude you're going and you'll get a briefing.

### 5. Apply, then get a second opinion (`/red-team`)

When a role from any of these channels is worth applying to, ask for a letter. Claude reads your CV and your past letters first, so the draft sounds like you and only claims what your CV supports. The letter and CV get a shared number, and the application gets a row in the log.

Every new letter then goes through three passes:

1. **You make it yours.** Read the draft and change whatever doesn't sound like you. Edit the file directly, or leave notes in the form `(target text) -> (comment)` and Claude will work them in.
2. **A fresh reviewer reads it.** When you're done, Claude offers to have a second Claude agent (Opus), one that hasn't seen the drafting, review it. The reviewer checks clarity, the opening, evidence your CV supports but the letter leaves out, claims your CV can't back up, and repetition. It treats your own wording as your voice, not as a mistake.
3. **Claude shows you the final draft.** Claude applies the feedback that improves the letter and keeps your voice wherever the two conflict. You see the final draft with a short list of what changed and which suggestions were declined.

After that, Claude offers a red-team review. It is only offered for a named role with a posting, and only runs if you say yes. The review covers five things:

- Which of the posting's must-have keywords appear in your letter.
- How strong your evidence is for each requirement.
- The reasons a hiring manager would reject the letter in fifteen seconds.
- What a stronger rival applicant would show that you don't.
- A chances band (low, moderate, good or strong) with the three fixes that would help most.

You can also use it before drafting, when you're still deciding whether to apply. The review is saved next to the application in `application-plans/`.

### 6. Keep the log honest

`memory/application_log.md` records every application and its outcome. Searches never re-suggest an employer you've already applied to. A lane that only produces rejections gets less weight in later searches, however good it looks on paper. When you hear back, tell Claude and the status is updated.

## Folders

- `resume/`, `cover-letters/`, `publication/`, `projects/`: your material
- `job-searches/`, `career-events/`, `room-maps/`: dated reports
- `application-plans/`: prep for applications in progress
- `memory/`: preferences, lessons and the application log. Claude reads these every session, so edit them freely.
- `_inbox/`: drop zone for onboarding; empty it afterwards

Everything stays in this folder on your computer. Nothing is shared unless you share it.
