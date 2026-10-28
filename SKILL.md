---
name: event-program-os
description: "An operating system for a B2B event program: event IDs, the ten-gate model, where artifacts live, file naming, intake rules, and how to keep the tracker from bloating. Use whenever the conversation touches running an event program: adding a new event, filing a contract, target list or lead export, filling in gates, asking what's blocking an event, setting up an events tracker, or answering \"how much pipeline does this need\". Layers on top of `event-vetting` (scoring method and payback maths) and `event-debrief` (closing the loop). Fill in config.md with your own numbers and systems first."
---

# Event program OS

A program of 30+ events a year runs on three things that each do one job. Getting those jobs straight is most of what this skill is for.

Read `event-vetting` for the six scoring dimensions, weights, tiers and payback chain. This skill is how that method gets *run* across a whole calendar.

## The systems

| System | Holds | Rule |
|---|---|---|
| **Tracker** (e.g. a Notion database) | Live events, scores, gates, artifact links | New events enter **here**. It is the operating board. |
| **File storage** (e.g. Google Drive) | Every artifact a human edits or signs | One folder per event, named `EVT-0XX Event Name — YYYY-MM-DD` |
| **CRM** (e.g. HubSpot / Salesforce) | Campaigns and lead membership | One campaign per event, created before the event |

The split that decides where a thing goes: **file storage for anything a human edits or signs, the tracker for anything a formula reads back.** Sales works in Docs and Sheets, so don't ask them to move.

## Commercial assumptions

Every derived number depends on these. Keep them in `config.md`, get them from finance, and **don't substitute remembered figures.** When the planning and trailing win rates differ, say which one a bar assumes. Someone will ask, and the gap between the two multiples is entirely the assumption.

## Event IDs

Format `EVT-0XX`. The next ID is the highest existing ID plus one.

**Never reuse or renumber an ID**, including for cancelled events. A recycled ID silently points old files and old CRM campaigns at a different event, and nothing surfaces the error until someone opens the wrong contract.

## The ten gates

An event's status is calculated from its gates. Nobody marks an event "ready": people complete gates and the status updates itself.

| Gate | Artifact | Lives in |
|---|---|---|
| G01 Approved | Proposal + approval | Files |
| G02 Contract | Signed contract PDF | Files |
| G03 Content | Speaker, session or booth content | Files |
| G04 Target List | Target account / attendee sheet | Files |
| G05 Enablement | Doc **and** a live 30-min session with sellers | Files |
| G06 Outreach | Copy + plan | Files |
| G07 Logistics | Checklist | *(checkbox only, no link field)* |
| G08 Leads In | CRM campaign **and** leads CSV | CRM + files |
| G09 Follow-Up | Follow-up copy: email, sequence, LinkedIn script or calls | Files |
| G10 Debrief | Outcome fields on the tracker; a narrative doc is optional | Tracker + files |

Why the gates are designed this way:

- **G09 comes before G10 on purpose.** Follow-up loses value fast, and the debrief closes the loop. If the order is reversed, a tidy write-up starts standing in for actually contacting anyone.
- **G09 is about reaching people, not about one channel.** Naming a gate after a single channel ("Emails Sent") makes it wrong the first time a rep follows up by phone or LinkedIn. Any reach counts. Coverage questions belong in the debrief, not in the schema.
- **G07 has no artifact field by design.** A field people paste junk into just to clear a gate is worse than no field.
- **G08 needs both a campaign and a CSV.** The campaign proves the leads reached the CRM. The CSV is the permanent record, because campaign membership changes as leads merge, convert and get reassigned. **Create the campaign at G06, not after the event.** An event without a campaign object has to be reconciled by hand at T+90.
- **G10 is structured data first.** `Meetings Held`, `Qualified Leads`, `Opps Created`, `Pipeline T+90` and `Verdict` go on the tracker, because they feed next cycle's `Prior Performance`. Numbers written only in a document can't be read by anything.

**Moving from checkboxes to link-driven gates.** Checkboxes rely on people being honest. Add an `Evidence Gaps` formula that flags any gate ticked with no artifact behind it. Convert gates to link-driven formulas **one at a time**, starting with ones whose links are already filled. Converting them all at once with empty links flips the whole board to OVERDUE.

## Keeping the system from growing

A tracker people maintain by hand has a practical limit on how many fields it can hold. Past it, people clear fields instead of filling them in properly, and the board becomes less trustworthy. One program turned its playbook into task rows and created over a thousand unowned rows. Removing that step is what fixed it.

**Nothing new goes into the tracker unless something comes out.** The test for any proposed field: does a human have to type it, and does anything read it back? If it's typed and read, it earns its place. If it's typed and never read, it's pure cost.

Before proposing a new field, check whether the information belongs somewhere that already exists:

- An outside party expects a file by a date → a **deliverables** row with an owner and the organizer's deadline
- One person does one thing once → a **task** with a named owner and due date
- Every event does it the same way → the **playbook**, as a reference, never as rows to tick off
- A number someone wants once, on some events → a question in the debrief outline, not a field

## File naming

Folder: `EVT-0XX Event Name — YYYY-MM-DD`
File: `{EventID}_{TYPE}_{ShortName}`, with underscores between parts and hyphens inside them.

Each type is one word, and always the same word:
`PROPOSAL` · `CONTRACT` · `CONTENT` · `TARGETS` · `ENABLEMENT` · `OUTREACH` · `LOGISTICS` · `LEADS` · `FOLLOWUP` · `DEBRIEF`

Prior-year files for a repeating event go in the *current* event's folder with the period marked, for example `EVT-033_LEADS_PRIOR-2025-11_ShortName.csv`.

Four rules that keep it working:

1. **The ID comes first.** It's the only unique part of the name, so searching `EVT-024` returns exactly that event's files.
2. **No dates, "final" or "v2" in names.** Version history handles that. Use dates only for files that genuinely come in a series, like `EVT-024_OUTREACH_Wave2_2026-09-14`.
3. **Never improvise the type.** "Contract" vs "Agreement" vs "SOW" makes it impossible to filter by type across the calendar.
4. **Put the event ID inside the document too**, on the top line, so full-text search still finds it after someone renames the file.

## Scoring at intake

Score all six dimensions **at intake, before money is committed.** An event scored after the fact is an event already decided.

- **Read the contract, not the prospectus,** for Data / List Rights and Meeting Mechanism. Together they're 35% of the score, and both are facts written in the contract. A Meeting Mechanism of 2 means every meeting has to be self-generated, so expect to miss the meeting target unless outreach is resourced to carry it alone.
- **Prior Performance of 3 is the honest default** for a new event. Don't inflate it to move a tier.

## Two things that are easy to get wrong

**`ICP Prospects` and `Match Rate` are pre-event fields.** They count qualified people on a *target or attendee* list obtained before the event (G04). A leads CSV is a post-event record and feeds `Prior Performance`, not these fields.

**Match rate and cost per ICP prospect answer different questions.** Match rate (`ICP Prospects ÷ Expected Attendance`) measures concentration and ignores cost. Cost per ICP prospect (`All-In Cost ÷ ICP Prospects`) is a price. A curated dinner wins on concentration and loses on price; a large expo does the reverse. Both are true. Two events can produce the same number of wins from wildly different lead volumes.

**`Expected Attendance` means attendees, not registrations,** and getting it wrong isn't cosmetic. Swag, print runs, booth staffing and lead-capture setup are all sized from it. An event planned for 50 that actually draws 600 is under-provisioned on every one of those decisions before anything else goes wrong. Get the number from the organizer in writing before ordering against it.

## Adding a new event

1. **Take the next event ID.**
2. **Create the tracker row and score it immediately,** including the fee.
3. **Create the folder at intake, not at contract.** The proposal is already an artifact and needs a home.
4. **Work the gates in order.** A `Blocked On` field names the single next thing.

**Approval thresholds** come from `config.md` (example: under $2.5k → event lead · $2.5–10k → marketing lead · $10–30k → VP · over $30k → VP + CFO). `Tier` and `Required Pipeline` are the case you bring into that conversation.

**No intake inside 8 weeks of the event date** without a written exception. G04–G06 need lead time. An event approved 30 days out clears its gates on paper and produces no pipeline. Budget is rarely the binding constraint; lead time and executive availability are.

## Verdicts

Before the event, end with one of four verdicts plus the number that drove it: **GO · NEGOTIATE · DOWNGRADE · DECLINE.** See `event-vetting` for what each one means and which terms to ask for when negotiating.

After the event, the verdict is a separate field: **Renew as-is · Renew with changes · Downgrade tier · Kill.** It stays open until T+90.

## Program patterns worth watching

- **Format mix.** Sponsored conferences tend to take most of the budget, while partner co-hosted events and field dinners often win on cost per qualified conversation and get under-used.
- **Deal size vs lead volume.** If cost per opportunity beats the model but pipe-to-spend still misses, the gap is deal size, not lead volume. Check event-sourced ACV against the blended ACV before approving new spend.
- **Market entry is not a channel.** Report new-region spend honestly as entry spend until it produces opportunities, and report regions separately when they tell opposite stories.
- **Paid-for, never-claimed entitlements** are a recurring leak: unclaimed lead-scanning licenses, unused customer passes, speaking slots with no attendee list. Check them at intake and name an owner, not at the debrief.
- **Seeded vs observed inputs.** Say which scoring inputs were measured and which were estimated whenever you present a score.
