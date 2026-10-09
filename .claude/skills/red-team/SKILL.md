---
name: red-team
description: A sparring partner and second pair of eyes for one specific application. Stress-tests the decision to apply and the drafted letter and CV against the posting with four red-team prompts, an ATS keyword check, a requirement-to-evidence map and a chances band. Use only when the user is applying for a named role, and offer it (never run it unasked) once that role's letter or package is drafted, or when the user is deciding whether to apply. Not for job-search sweeps, event plans, room maps or general career brainstorming.
---

# Red team: a sparring partner for one application

Friends soften critique because they like you. This skill takes the hostile seat on purpose: the hiring manager who rejects in fifteen seconds, the stronger rival applicant, the reviewer writing the rejection note. It runs on one application at a time, for a named role at a named organisation.

## 0. When to offer it

Offer it in one line, and run it only on a yes:
- after a cover letter, motivation letter or package for a specific role is drafted, logged and through the review loop in CLAUDE.md (user pass, agent pass, final draft), or after the user skipped that loop ("Want me to red-team this against the posting before you submit?");
- when the user says they want to apply for a specific role and is unsure whether to.

Do not offer it during job-search sweeps, event plans, room maps or onboarding. Without a named role and a posting there is nothing to attack.

## 1. Read first

1. The posting. Fetch the original page; if it is behind a login or blocked, ask the user to paste the text. Never reconstruct requirements from the job title alone.
2. The documents for this role: the numbered letter in `cover-letters/` and the numbered CV in `resume/` (match on the shared number prefix).
3. The master CV in `resume/`, if one exists. It is the fact bank for every suggested fix.
4. The role's row in `memory/application_log.md`, `memory/user_profile.md` (languages, location) and `memory/cover_letter_craft.md`.

## 2. Pick the mode

- **Decision mode** (no draft yet, the question is "should I apply?"): run the four prompts in section 3 on the decision, then give the chances band from Step E. Skip Steps B to D.
- **Review mode** (a draft exists): run the full review in section 4, which uses the four prompts at Step D.

If unclear, ask which one the user wants.

## 3. The four prompts

Run them one at a time as a conversation, not a monologue. After each, have the user name the result in one sentence.

1. **Key assumptions audit.** List every assumption the application depends on, including the unspoken ones (that a career-change background transfers, that the team's problem is the one the user understands, that the language level is enough). Sort them into load-bearing, weakening and minor. For each load-bearing one ask for evidence. A load-bearing assumption with no evidence is the fault line; dig there.
2. **Pre-mortem.** "It is six weeks from now and you were rejected. Walk me through exactly why." In decision mode, add a second pass: "It is twelve months from now, you took the job and you are leaving. Why?" Ask for the root cause, then: can it be prevented?
3. **Rival applicant.** The strongest other applicant meets every must-have. What do they show that this application does not? Which of the user's advantages is a real edge, and which only looks like one?
4. **The rejection note.** The hiring manager writes one sentence for the file explaining the rejection. Write it, specific and blunt. If it names something the user actually plans to do, that is the top fix.

## 4. Review module

### Step A. Requirement profile
Split the posting into three buckets, keeping its exact wording:
- **Must-have:** "required", "you bring", "Pflicht", "Voraussetzung", years-of-experience thresholds.
- **Nice-to-have:** "ideally", "plus", "von Vorteil".
- **Context signals:** seniority, team size, sector, language requirements, location, relocation, clearance, tools named.

### Step B. ATS keyword check
For each must-have, list the posting's exact phrases and check whether each appears in the letter, verbatim or as a close variant. Note where a synonym would miss a literal match. If the posting and the letter are in different languages, check the terms in both. Report the share of must-have keywords present and the important missing ones. Keyword coverage is a visibility check, not a quality check.

### Step C. Requirement-to-evidence map
One row per must-have, with where the letter addresses it, the evidence type (specific result, responsibility list, or unsupported claim) and strength (strong, weak, missing). Never suggest wording for experience the user does not have. Where the evidence exists in the master CV but not the letter, say so and suggest moving it in.

### Step D. Red-team the letter
Run the four prompts from section 3 from the reader's side, aimed at the letter: what it assumes the reader believes, which sentence caused the fifteen-second rejection, what the rival shows that this letter does not, and the one-line rejection note.

### Step E. Chances band
Give a band (low, moderate, good, strong) with three to five reasons tied to the evidence. Never a percentage: only the documents are visible, not the applicant pool, internal candidates or referrals. Base it on must-have coverage and evidence strength, seniority and scope fit, language, location and availability fit, and whether there is a specific result the letter could lead with. Also check the lane signal in `memory/application_log.md`: if this lane has only produced rejections so far, say so. State what would move the band up.

### Step F. Output
In this order, short:
1. The band and the two or three reasons for it.
2. The top three fixes, each with a before-and-after sentence drawn from the user's real experience.
3. The keyword gaps worth closing, only where the user has the experience.
4. The one thing that would most change the outcome.

Every suggested sentence follows the CLAUDE.md letter rules (no em dashes, no mid-sentence colons introducing lists, no "X is not Y, it is Z" or "not because X, but because Y"). Run the banned-pattern grep on the suggested sentences before showing them. Write the report in the language the user discusses in; keep quoted keywords and letter excerpts in their original language.

## 5. Save and hand back

- Save the report as `application-plans/{NNN}_{shortname}/red_team_review.md`, using the application's number from the log.
- Do not edit the letter or CV unless the user asks. If they do, apply the fixes to the numbered files and re-run the grep.
- Add "red-teamed YYYY-MM-DD, band: X" to the Notes column of the role's row in `memory/application_log.md`. Do not change its status.

## Sparring rules

- Be specific. "Here is the sentence that loses the reader" beats "consider strengthening the opening".
- Discomfort means you found a real seam. Do not soften the finding; soften nothing but the tone.
- Listen for what the user does not say. The assumptions too obvious to mention are often the load-bearing ones.
- Two outcomes are both a success: the application survives with a concrete fix list, or the user decides not to apply and saves the effort for a better fit. If the user drops it, set the log status to `archived`.
