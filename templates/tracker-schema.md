# Events tracker: starter schema

A minimal set of fields for a Notion/Airtable events database. Every field is either **typed and read back** or **calculated**. If a field is neither, leave it out.

## Identity
| Field | Type | Notes |
|---|---|---|
| Event ID | Text | `EVT-0XX`, never reused |
| Event | Title | |
| Date | Date | Attendees, not registrations, start counting here |
| Format | Select | Conference · Field dinner · Partner co-host · Webinar · Trade show |
| Region | Select | |
| Folder | URL | |

## Economics (typed)
| Field | Type |
|---|---|
| Sponsorship Fee | Number |
| Other Costs | Number |
| Expected Attendance | Number (from organizer, in writing) |
| ICP Prospects | Number (from G04 list) |
| ICP Prospect Source | Text (which list, rows, date read) |

## Economics (calculated)
| Field | Formula |
|---|---|
| All-In Cost | Fee + Other Costs |
| Fit Score | SUMPRODUCT(scores, weights) ÷ 5 × 100 |
| Tier | ≥75 T1 · ≥58 T2 · ≥40 T3 · else T4 |
| Required Pipeline | All-In Cost × pipe-to-spend |
| Required Opps | ceil(Required Pipeline ÷ ACV) |
| Meeting Target | ceil(Required Opps ÷ meetings-to-opp) |
| Match Rate | ICP Prospects ÷ Expected Attendance |
| Cost per ICP Prospect | All-In Cost ÷ ICP Prospects |

## Scores (1–5)
ICP Density · Meeting Mechanism · Seniority Fit · Competitive & Partner Presence · Data / List Rights · Prior Performance

## Gates
G01–G10 checkbox + link per gate (G07 checkbox only; G08 has CRM Campaign **and** Leads CSV).

| Field | Formula |
|---|---|
| Gates Complete | count of ticked gates |
| Evidence Gaps | gates ticked with no link |
| Blocked On | first unticked gate |

## Outcomes (humans fill these in at T+90)
Meetings Held · Qualified Leads · Opps Created · Pipeline T+90 · Verdict (Renew as-is / Renew with changes / Downgrade tier / Kill)
