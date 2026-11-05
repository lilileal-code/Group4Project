# BingeBound — Specification

> **When:** Week 1 (Section 0), Week 2 (the rest), refined in Week 3 · **Owner:** Lilah Leal · **Done when:** every item in the SVC Self-Check at the end is true.
>
> **Version:** 1.0
>
> **Approved on:** 29 October 2026 **by:** Product Owner: Lilah leal · Architecture Lead: Austin Hammond · Delivery Lead: Ben Anderson
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
| E5 | Viewed the sample entries and the add title screen. She tried adding a title, paused on the word "American," then said "U.S. would be clearer." Used the choices after that and successfully created a new title. | Cousin, in person, 11/05/2026 |
| E6 | On the series screen, they pointed out that the international option should be free text because they wanted to specify where the series was internationally (e.g. seperating Korean series from other countries). | Friend, over the phone via screenshare, 11/05/2026 |
| E7 | Used the Plan to Watch, Watching, and Completed home screen filters. Asked what the Dropped and On Hold filters would be used for. After explaining, they used it to mark one of the shows. Liked the notes option and gave it a 10/10. | Sister, in person, 11/05/2026 |
| E8 | Asked before opening prototype if they'd need to make an account once it's fully finished. Continued when told that their info will be stored on their device. Tapped the X on one of the cards expecting it to delete. Overall, thought it was a solid start. | Uncle, in person, 11/05/2026 |
**Riskiest assumption:** People will type titles by hand instead of searching a catalog. If they refuse to type, the no-API rule sinks the product. We find out by watching a friend add three mixed titles (one American, one international) in the Week 3 prototype.
**Prototype Result:** They did as we hoped. They added a U.S. title and an international title by typing it in. The assumption holds for V1.
---

## 2. Scope

**In scope:** *(What this version will do.)*
- A private list of titles the user typed
- Fields: title, type (movie or series), language or origin (U.S. / international), status (Plan to watch / Watching / Completed / On Hold / Dropped), optional note, episode tracker and rating bar (only when series and watching, or completed, are selected together).
- Add a title, open it, change status, delete it
- Filter or search the list by title, type, origin, or status
- Sample data so the instructor can use the demo without signing in, clearly labeled as demo data
- Phone-width layout on a free static host
  
**Out of scope:** *(What it will NOT do. This list stops the AI build from adding extras.)*
- Streaming catalog search, IMDB, Netflix, or auto-import
- Public profiles, follows, ratings feeds, or comments
- Real accounts; device-only flags are acceptable in v1 if login cannot ship on Pages
- Release-date alerts and “what’s new this week”
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
| R1 | The system shall show a private list of titles, newest first. | P1 | Load home → sample cards visible; add “Parasite” → it is the first card. | E1, E7 |
| R2 | When the user adds a title, the system shall save title, country (U.S. or International), status, and type (Movie or Series). | P1 | Add Parasite, International, Watching, Movie → card shows those values. | E2, E5 |
| R3 | When the user sets status, the system shall use the words Plan to Watch, Watching, Completed, Dropped, or On Hold, and keep it after reload. | P1 | Set The Handmaiden's Tale to Completed, reload → status is still Completed. | E3, E7 |
| R4 | When the user taps All, To Watch, Watching, or Completed, the system shall show only titles in that status. All shows every title. | P1 | Tap To Watch → only Plan to Watch cards remain. | E7 |
| R5 | When the user types in Search titles here, the system shall filter cards by title as they type. | P1 | Type “para” → only Parasite stays. | E1 |
| R6 | If Save is tapped with a blank title, then the system shall not save a row and shall say “Type a title to save it.” | P1 | Save with an empty title → no new card; that message shows. | S1 failure |
| R7 | If a filter or search matches nothing, then the system shall say “No titles match. Clear filters.” | P1 | Search “zzzz” → that message and a way to clear. | S3 failure |
| R8 | The system shall label sample data as “Sample titles. Not your personal list.” | P1 | Read home → that sentence is visible. | E4, constitution 1 |
| R9 | The system shall load on a free public URL with no paid account, no secret, and no login wall. | P1 | Open the Pages URL in a fresh browser → list appears. | E8, constitution 3 |
| R10 | Where the screen is phone width, the system shall keep Add Title, filters, and Save usable with no sideways scroll. | P1 | View at 375px → no horizontal scroll; buttons at least 44px. | ASSUMPTION |
| R11 | When the user taps the X on a card, the system shall delete that title and keep it gone after reload. | P2 | Tap X on Squid Game, reload → it is gone. | E8 |
| R12 | The system shall not call a streaming or catalog API to fill titles. | P1 | Inspect the app → titles come from typed or sample data only. | Constitution 2, E5 |
| R13 | When the user saves a note or a rating from 0 to 10, the system shall show them on that title after reload. | P2 | Set rating 8 and a note, reload → both remain. | E7 |
| R14 | While type is Series, the system shall show episode progress as current / total. While type is Movie, the system shall hide episode fields. | P2 | Pick Series → 0 / 0 fields show. Pick Movie → they hide. | Prototype series screen |
| R15 | If the user asks to type a country instead of International, then the system shall still offer only U.S. and International in v1. | P2 | Add form → two country choices, no free-text country field. | E6 |

---

## 5. Open Questions

*The team's one list of unresolved questions — from any document or task. Don't let a builder or an AI guess. If the answer changes a document, update that document before marking the question Resolved.*

| ID | Question | Raised by | Owner | Status |
| --- | --- | --- | --- | --- |
| Q1 | Does v1 use real login, or device-only storage so the free host can demo it? | Spec | Team | Resolved: device-only in v1. No login. |
| Q2 | Is “origin” a two-value flag (American / international) or a free-text country? | Spec | Team | Resolved: not in v1. Two options, labeled U.S. and International. Revisit later. |
| Q3 | Prototype findings? | Team | Product owner | Resolved: E5-E8. Changes are U.S. label, five statuses, notes, rating 0-10, series episode tracker, no login. |

---

## Prototype Screenshots:

<img width="360" height="480" alt="View Parasite" src="https://github.com/user-attachments/assets/a2a0f1a7-0d8a-47d0-a191-42861736392b" />
<img width="360" height="480" alt="Home Page" src="https://github.com/user-attachments/assets/e69aa61c-8039-41f3-94a9-5ca7137b0a03" />
<img width="360" height="480" alt="Add Title" src="https://github.com/user-attachments/assets/c3e10717-cdb3-4b4a-a9ee-90bebe4f2565" />
<img width="360" height="480" alt="Add Title - Watching Series" src="https://github.com/user-attachments/assets/07109773-8b70-45d8-bd70-1c052cc899f0" />
<img width="360" height="480" alt="Add Title – 1" src="https://github.com/user-attachments/assets/e9523cf5-f76e-401e-af3e-54f2b8f40bf8" />


---

## SVC Self-Check

- [X] **Simple** — each requirement is one sentence in one EARS pattern; no jargon a new teammate wouldn't know.
- [X] **Valuable** — the Constitution has 2–3 principles that would actually stop a feature; the Evidence table has 3+ rows from real people outside the team, plus the prototype test; each P1 requirement cites evidence or a standard, or says ASSUMPTION; the riskiest assumption is named.
- [X] **Complete** — 3–5 scenarios, each with actor, trigger, steps, and both outcomes; P1 is 1–2 scenarios that make a complete journey; every requirement has a unique ID, a priority, and an acceptance test; no open question blocks a P1 requirement; the team has approved it.
