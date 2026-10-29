# BingeBound — Specification

> **When:** Week 1 (Section 0), Week 2 (the rest), refined in Week 3 · **Owner:** Lilah Leal · **Done when:** every item in the SVC Self-Check at the end is true.
>
> **Version:** 1.0
>
> **Approved on:** 22 October 2026 **by:** Product Owner: Lilah leal · Architecture Lead: Austin Hammond · Delivery Lead: Ben Anderson
>
> **Filled-in Example:** `docs/examples/specification-example.md`

The Spec is the source of truth for *what* you're building. Write it so a teammate — or an AI agent — could build from it without asking you a question.

---

## 0. Constitution

*2–3 rules this product must never break, no matter what feature is added. If a rule wouldn't stop any feature, it isn't doing its job.*

| # | Principle | Why it exists |
|---|-----------|---------------|
| 1 | Every title, status, and note stays private to the signed-in user. No public profiles, follower graphs, or activity feeds. | A social layer would turn a one-term personal list into a product we cannot finish or moderate. |
| 2 | The user types the title. No streaming-catalog APIs, scrapers, or auto-import from Netflix/IMDB in the first release. | An external catalog adds keys, rate limits, and scope we do not control and do not need for the demo. |
| 3 | The public demo must load for the instructor on a free GitHub Pages (or equivalent free) URL with no paid account and no secret the team cannot commit. | If the demo only runs on one laptop or a paid host, the sponsor cannot review it and the project fails the course bar. |
---

## 1. Problem & Evidence

**Problem and success:** Movie and TV fans in one household keep a plan-to-watch list, but no simple app holds American and international titles in one place. They jump between apps and paper. Success is one private list they can add to, mark as watching or done, and find again without a second app.

**Evidence:** *(3–5 short conversations or observations with people like your user, outside your team, plus the Week 3 prototype test. Real quotes or what you saw, not opinions.)*

| ID | What we heard or saw | From whom |
|----|----------------------|-----------|
| E1 | “I keep a list on my phone and another on paper. I still forget what I meant to watch.” They opened Notes, then a handwritten list, to find one title. | Close family, in person |
| E2 | “American stuff is in one app. The Korean and Spanish shows are in a different list. I never open both.” | Close friend, text |
| E3 | Updating status (want to watch / watching / finished) is the annoying part. With so many unorganized titles, the list goes stale. | Family who share the same list, in person |
| E4 | "I don’t want followers or a feed. I just want my list.” They had tried a social movie app and stopped. | Same group, when asked about Letterboxd-style/IMDB apps |
| E5 | Week 3 Test - fill in later | Outside Team |
**Riskiest assumption:** People will type titles by hand instead of searching a catalog. If they refuse to type, the no-API rule sinks the product. We find out by watching a friend add three mixed titles (one American, one international) in the Week 3 prototype.

---

## 2. Scope

**In scope:** *(What this version will do.)*
- A private list of titles the user typed
- Fields: title, type (movie or show), language or origin (American / international), status (To watch / Watching / Finished), optional note
- Add a title, open it, change status, delete it
- Filter or search the list by title, type, origin, or status
- Sample data so the instructor can use the demo without signing in, clearly labeled as demo data
- Phone-width layout on a free static host
  
**Out of scope:** *(What it will NOT do. This list stops the AI build from adding extras.)*
- Streaming catalog search, TMDB, Netflix, or auto-import
- Public profiles, follows, ratings feeds, or comments
- Real accounts if the free host cannot support them; device-only flags are acceptable in v1 if login cannot ship on Pages
- Episode-level tracking, release-date alerts, and “what’s new this week”
- Recommendations or AI-generated lists
---

## 3. User Scenarios

*3–5 short stories of someone using the product. Tag each with a priority:*
- ***P1** — must have. Without it, the product doesn't solve the problem. Keep P1 to 1–2 scenarios that make a complete journey.*
- ***P2** — should have. The product still works without it.*
- ***P3** — nice to have. Cut first if time runs short.*

**S1: Add a mixed title to one list** — Priority: P1
- Actor: Adult who watches both U.S. shows and international shows
- Trigger: They finish a conversation and want to remember a title before they forget it
- Steps: Open the list, tap Add, type the title, pick movie or show, pick American or international, save
- Success outcome: The new title is on the list with the right type and origin
- Failure outcome: They cannot tell American from international, or the add form does not save

**S2: Find what to watch tonight** — Priority: P1
- Actor: Same person, or a family member sharing the idea of the list
- Trigger: They have time to watch and do not want to open three apps
- Steps: Open the list, filter to To watch, optionally filter international, open one title, mark it Watching or Finished
- Success outcome: They leave with one title and an updated status
- Failure outcome: Status does not stick, or the filter hides the title they just added

**S3: Clean up a finished title** — Priority: P2
- Actor: Same user
- Trigger: They finished the show and the list is cluttered
- Steps: Find the title, set status to Finished, or delete it
- Success outcome: It no longer appears in To watch
- Failure outcome: Delete or status change is unclear and the title stays in the way

  **S4: Open the demo without an account** — Priority: P1
- Actor: Instructor reviewing the project
- Trigger: They open the free URL
- Steps: Load the page, see sample titles including at least one international title, open one
- Success outcome: The demo works with no paid host
- Failure outcome: Blank page, login wall, or only American titles

---

## 4. Requirements & Acceptance Tests

*Write each requirement as one sentence using one of these [EARS](https://alistairmavin.com/ears/) patterns:*

| Pattern | Use it for | Template |
|---|---|---|
| Always | Rules that are always true | The system shall … |
| When | A user action or event | When [trigger], the system shall … |
| While | Behavior during a state | While [state], the system shall … |
| If … then | Errors and unwanted situations | If [condition], then the system shall … |


| ID | Requirement | Priority | Acceptance test (do → expect) | Evidence |
| --- | --- | --- | --- | --- |
| R1 | The system shall show a private list of titles the user added. | P1 | Load the list → at least the sample titles are visible, labeled as demo data. | E1, E4 |
| R2 | When the user adds a title, the system shall save the title, type (movie or show), and origin (American or international) that they typed. | P1 | Add “Parasite” as movie, international → it appears on the list with those values. | E2 |
| R3 | When the user changes a title’s status, the system shall show To watch, Watching, or Finished and keep that status after reload. | P1 | Set “The Bear” to Finished, reload → status is still Finished. | E3 |
| R4 | When the user filters by origin or status, the system shall show only matching titles. | P1 | Filter International + To watch → only matching sample titles remain. | E2 |
| R5 | When the user searches by title, the system shall filter the list as they type. | P1 | Type “para” → only titles containing that text stay visible. | E1 |
| R6 | If the add form is submitted with a blank title, then the system shall not save a row and shall say the title is required. | P1 | Submit Add with an empty title → no new row; “Title is required.” | S1 failure |
| R7 | If a filter matches nothing, then the system shall say no titles match and offer a way to clear the filter. | P1 | Filter to a status with no rows → empty message and a clear control. | S2 failure |
| R8 | The system shall label sample data as demonstration data, not the user’s personal list. | P1 | Read the list → demo wording is visible without opening a title. | Constitution 1, E4 |
| R9 | The system shall load on a free public URL with no paid account and no secret in the repo. | P1 | Open the GitHub Pages URL in a fresh browser → list appears. | Constitution 3 |
| R10 | Where the screen is phone width, the system shall keep add, filter, and status controls usable with no sideways scroll. | P1 | View at 375px → no horizontal scroll; primary buttons tappable. | ASSUMPTION (phone use) |
| R11 | When the user deletes a title, the system shall remove it from the list. | P2 | Delete a sample title → it is gone after reload. | E3 |
| R12 | The system shall not call a streaming or catalog API to fill titles. | P1 | Inspect the app → titles come from typed or sample data only. | Constitution 2 |


---

## 5. Open Questions

*The team's one list of unresolved questions — from any document or task. Don't let a builder or an AI guess. If the answer changes a document, update that document before marking the question Resolved.*

| ID | Question | Raised by | Owner | Status |
| --- | --- | --- | --- | --- |
| Q1 | Does v1 use real login, or device-only storage so the free host can demo it? | Spec | Team | Open |
| Q2 | Is “origin” a two-value flag (American / international) or a free-text country? | Spec | Team | Open — draft uses two values |
| Q3 | Week 3 prototype findings | Team | Product owner | Open — fill after the test |

---

## SVC Self-Check

- [X] **Simple** — each requirement is one sentence in one EARS pattern; no jargon a new teammate wouldn't know.
- [X] **Valuable** — the Constitution has 2–3 principles that would actually stop a feature; the Evidence table has 3+ rows from real people outside the team, plus the prototype test; each P1 requirement cites evidence or a standard, or says ASSUMPTION; the riskiest assumption is named.
- [X] **Complete** — 3–5 scenarios, each with actor, trigger, steps, and both outcomes; P1 is 1–2 scenarios that make a complete journey; every requirement has a unique ID, a priority, and an acceptance test; no open question blocks a P1 requirement; the team has approved it.
