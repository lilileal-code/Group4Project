# [BingeBound] — Tasks

> **When:** Week 5, then updated through Weeks 6–8 · **Owner:** Delivery Lead · **Done when:** every item in the SVC Self-Check at the end is true.
>
> **Approved on:** ___ **by:** Delivery Lead ___ · Architecture Lead ___ · Product Owner ___
>
> **Filled-in Example:** `docs/examples/tasks-example.md`

Tasks break the Plan into small steps you can build and check one at a time.

---

## 1. Task List

*One row per task, P1 first, in the Plan's build order. A good task starts with a verb, can be finished in under a day, and has a one-sentence "Done when" check that says where to look (a file, the browser console, or a screen). When a task completes a requirement, its Done when is that requirement's acceptance test; groundwork tasks get their own concrete check. T0 is filled in, because every build starts by scaffolding the app.*

| ID | Task | Priority | Traces to (R# / ADR) | Depends on | Done when | Status |
|----|------|----------|----------------------|------------|-----------|--------|
| T0 | Scaffold the Vue application without a build step for the GitHub Pages test build. | P1 | ADR-00 | — | The application starts locally and the starter template's sample page opens in the browser without build errors. | Not started |
| T1 | Create the device-only data layer (`data.js`) for retrieving and saving watchlist titles through browser storage. | P1 | R1, R2, R3, ADR-01, ADR-02 | T0 | The data layer can save a title and retrieve the same title after the browser page is reloaded, using the approved device-only approach. | Not started |
| T2 | Prepare synthetic sample titles for the public demo and keep them separate from personal watchlist data. | P1 | R8, R9, ADR-06 | T1 | The demo data contains sample titles, including an International title, and the home screen displays the exact label "Sample titles. Not your personal list." | Not started |
| T3 | Build the Home / Watchlist screen to display saved titles as cards, newest first. | P1 | R1, R8, ADR-05, ADR-06 | T1, T2 | The home screen displays saved titles as cards, places the newest title first, and displays the sample-data label when sample titles are shown. | Not started |
| T4 | Build the Add Title form with title, type, origin, and status inputs. | P1 | R2, R12, ADR-03, ADR-04 | T3 | The form allows a user to enter a title, select Movie or Series, select U.S. or International, and choose Plan to Watch, Watching, Completed, Dropped, or On Hold. | Not started |
| T5 | Validate title submissions and display the required blank-title message. | P1 | R6 | T4 | Submitting the Add Title form with a blank title does not save a title and displays "Type a title to save it." | Not started |
| T6 | Connect the Add Title form to the device-only data layer so new titles are saved. | P1 | R1, R2, ADR-02, ADR-03 | T1, T4, T5 | Adding a title displays it in the watchlist, and the title and its selected type, origin, and status remain present after reloading the page. | Not started |
| T7 | Build the Title Details view so users can open a saved title and view its information. | P1 | R1, R3 | T3, T6 | Selecting a title from the watchlist opens its details view and displays the saved title, type, origin, and status. | Not started |
| T8 | Add status editing to the Title Details view and save status changes. | P1 | R3 | T1, T7 | Changing a title's status to any of the five approved values updates the displayed status and preserves the change after reloading the page. | Not started |
| T9 | Add the All, To Watch, Watching, and Completed filters to the Home / Watchlist screen. | P1 | R4, ADR-05 | T3, T8 | Selecting All displays every title, while To Watch, Watching, and Completed display only titles with the corresponding status. | Not started |
| T10 | Add live title search to the Home / Watchlist screen. | P1 | R5, ADR-05 | T3, T6 | Typing part of a title into the search field immediately filters the displayed cards to titles containing the entered text. | Not started |
| T11 | Add the no-results message and clear-filters action for unsuccessful searches and filters. | P1 | R7 | T9, T10 | Searching for a title with no matches displays "No titles match. Clear filters." and provides a working action to clear the search and filters. | Not started |
| T12 | Verify that the application does not use streaming or catalog APIs to populate titles. | P1 | R12, ADR-03 | T4, T6 | Reviewing the application code confirms that titles come only from manual user entry or the synthetic sample data, with no streaming or catalog API calls. | Not started |
| T13 | Apply the phone-width layout and accessibility rules from the Style Guide across the application. | P1 | R10 | T3, T4, T7, T9, T10 | At a 375px viewport, Add Title, filters, and Save remain usable without horizontal scrolling, and buttons meet the 44px minimum height. | Not started |
| T14 | Publish the public demo using the approved free hosting approach. | P1 | R8, R9, ADR-00, ADR-06 | T2, T3, T4, T13 | The public GitHub Pages URL opens in a fresh browser without a login wall, paid account, or exposed secret, and displays the labeled sample titles. | Not started |
| T15 | Test the P1 user scenarios and requirement acceptance tests in the browser. | P1 | R1–R10, R12, ADR-00–ADR-06 | T5–T14 | The browser tests confirm the P1 acceptance tests for adding a mixed title, finding and updating a title, opening the public demo, storage persistence, search, filters, validation, and the 375px layout. | Not started |
| T16 | Add title deletion using the X control on a title card. | P2 | R11 | T1, T3, T6 | Selecting the X removes the chosen title from the watchlist, and the title remains deleted after reloading the page. | Not started |
| T17 | Add optional notes and ratings from 0 to 10 to title records. | P2 | R13, ADR-04 | T1, T4, T7 | A user can save an optional note and a rating from 0 to 10, and both values appear on the title after reloading the page. | Not started |
| T18 | Add episode progress fields for Series titles and hide them for Movie titles. | P2 | R14, ADR-04 | T1, T4, T7 | Selecting Series displays current and total episode progress fields, while selecting Movie hides those fields. | Not started |
| T19 | Verify that the origin field does not allow free-text country entry in v1. | P2 | R15, ADR-04 | T4 | The Add Title form offers only U.S. and International as origin choices and does not display a free-text country field. | Not started |
| T20 | Test the P2 title management features and their persistence. | P2 | R11, R13, R14, R15 | T16–T19 | Browser tests confirm that deletion, notes, ratings, episode progress, and the two-option origin restriction behave as specified and persist where required. | Not started |

*Status: Not started · In progress · Done · Blocked (Q#) — when a task is blocked, add the question to the Spec's Open Questions and put its ID here.*

---

## 2. Cross-Check (Week 5)

*Before the Week 6 build, follow every P1 requirement through the documents. An empty cell is a gap — fix the document, not this table.*

| Req ID | Data & API (entity / endpoint) | Plan (ADR / screen #) | Task(s) |
|--------|--------------------------------|-----------------------|---------|
| R1 | `User.id`; `Title.id`; `Title.owner_id`; `GET /v1/titles`; `GET /v1/titles/{id}`. **Gap:** No creation-date field is defined to support newest-first ordering. The user ownership and login model also conflicts with the device-only v1 decision. | ADR-01, ADR-02; Screen #1 (data layer), Screen #2 (Home / Watchlist), Screen #4 (Title Details) | T1, T3, T6, T7, T15 |
| R2 | `Title.title`; `Title.type`; `Title.origin`; `Title.status`; `POST /v1/titles`. **Gap:** The endpoint request does not explicitly include status, and the origin enum uses `American` instead of the Specification's `U.S.`. | ADR-03, ADR-04; Screen #1 (data layer), Screen #3 (Add Title form) | T1, T4, T6, T15 |
| R3 | `Title.status`; `PATCH /v1/titles/{id}`. **Gap:** Data & API Design defines only `To watch`, `Watching`, and `Finished`, not the five required Specification values. | ADR-02; Screen #1 (data layer), Screen #4 (Title Details) | T1, T8, T15 |
| R4 | `Title.status`; `Title.type`; `Title.origin`; `GET /v1/titles` with search and filter parameters. **Gap:** The endpoint supports filtering, but its documented status and origin values do not fully match the Specification. | ADR-05; Screen #2 (Home / Watchlist), Screen #5 (Search and filter controls) | T9, T15 |
| R5 | `Title.title`; `GET /v1/titles` with search text. | ADR-05; Screen #5 (Search and filter controls) | T10, T15 |
| R6 | `Title.title` (required and non-blank); `POST /v1/titles`. | Screen #3 (Add Title form) | T4, T5, T6, T15 |
| R7 | `GET /v1/titles` returns an empty array when no titles match. **Gap:** The endpoint does not define the required user-facing message or clear-filters action. | ADR-05; Screen #5 (Search and filter controls) | T11, T15 |
| R8 | `User.is_demo`; `GET /v1/demo/titles`; `GET /v1/demo/titles/{id}`. | ADR-06; Screen #1 (data layer), Screen #2 (Home / Watchlist), Screen #6 (Phone layout and public demo) | T2, T3, T14, T15 |
| R9 | No entity or endpoint required; this is a hosting and public-access requirement. | ADR-00, ADR-06; Screen #2 (Home / Watchlist), Screen #6 (Phone layout and public demo) | T2, T14, T15 |
| R10 | No entity or endpoint required; this is a responsive layout requirement. | Screen #6 (Phone layout and public demo) | T13, T15 |
| R11 | `Title.id`; `DELETE /v1/titles/{id}`. | Screen #7 (Delete title functionality) | T16, T20 |
| R12 | No entity or endpoint required; the requirement prohibits streaming and catalog API calls. | ADR-03; Screen #3 (Add Title form) | T4, T12, T15 |

**Result:** All P1 requirements (R1–R10 and R12) have corresponding tasks and are mapped to the relevant Plan decisions or screens. Every task traces to at least one requirement or architecture decision. However, the cross-check identifies unresolved gaps in Data & API Design: the ownership/authentication approach, newest-first ordering field, origin values, and five-status definition do not fully match the Specification and Plan. The Data & API Design document also does not define the user-facing behavior for R7. These conflicts must be reviewed before implementation; they are not silently resolved by this task list.

---

## 3. Gap Log (Weeks 6–7)

*During the Week 6 AI build, log every place the agent guessed, got stuck, or misread a document. In Week 7, each document's owner fixes their gaps; then mark whether the re-run confirmed the fix.*

| What the agent got wrong or guessed | Which document & section caused it | Fix applied | Fixed in re-run? |
|-------------------------------------|------------------------------------|-------------|------------------|
| | | | |

---

## 4. Build Notes (Week 8)

*What the final test build simulated or left out. Together with the documents, this is the handoff to System Implementation.*

- **Live URL:** *(The app's GitHub Pages address.)*
- **Simulated:** *(Each simulated requirement ID and how it's simulated, e.g. "R1: a 'log in as…' picker instead of real login.")*
- **Not built:** *(Each task you didn't build, with its priority — P2 or P3 only — or "None.")*

---

## SVC Self-Check

- [ ] **Simple** — each task is one action starting with a verb, small enough to finish in under a day, with a one-sentence Done when check.
- [ ] **Valuable** — every task traces to a requirement or ADR; nothing is built "just because."
- [ ] **Complete** — every P1 requirement has at least one task; P1 tasks come first in the Plan's build order; the cross-check has no empty cells; the team approved it before the Week 6 build; every gap has a fix or a reason it wasn't fixed; the Build Notes are filled in by the end of Week 8.
