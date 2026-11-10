# BingeBound — Plan

> **When:** Week 3 (Sections 1–2), Week 4 (Sections 3–4) · **Owner:** Ben Anderson · **Done when:** every item in the SVC Self-Check at the end is true.
>
> **Version:** 1.0
>
> **Approved on:** ___ **by:** Product Owner: Lilah Leal · Architecture Lead: Austin Hammond · Delivery Lead: Ben Anderson
>
> **Filled-in Example:** `docs/examples/plan-example.md`

The Spec says *what* to build. The Plan says *how*, in what order, and what might go wrong.

---

## 1. Approach

BingeBound will be a web application that allows users to create and manage a personal watchlist of movies and television shows. Users will manually enter titles and provide information such as the title type, origin, and watch status. The application will allow users to search their lists, filter titles, update statuses, and delete titles when they are no longer needed.

---

## 2. Key Decisions (ADRs)

*An ADR (Architecture Decision Record) is one row per real choice between options. ADR-00 is always your tech stack — decide it first, early in Week 3, because the database goes into `data-api-design.md` Section 0. The course defaults are filled in; change one only for a real reason, and say why in "Why this one."*

| ADR | Decision | Req IDs | Alternatives considered | Why this one |
| ----- | ---------- | --------- | ------------------------- | -------------- |
| ADR-00 | Use Vue without a build step for the frontend, a simulated backend for the test build, and GitHub Pages for hosting. PostgreSQL through Supabase is proposed as the database for the future system implementation. | R1–R15 | React, a backend framework, a different hosting provider, or a different database. | This follows the course's recommended technology stack and allows the team to build and test the application without requiring paid hosting or a complex backend. PostgreSQL provides a structured database option for the future implementation. |
| ADR-01 | Version 1 will not require real user accounts or login. The course test build may use a simulated user picker to demonstrate separate user lists. Each user's information will remain stored on their device. | R1, R8, R9 | Real user authentication, shared accounts, or requiring login before viewing the demo. | A simulated user picker can still support course testing without requiring a real authentication system. |
| ADR-02 | The test build will use browser-based storage or simulated data. | R1, R2, R3, R11, R13, R14 | Storing all data only in memory, using browser storage for the entire application, or implementing the database during the test build. | Browser-based storage supports testing without requiring a live backend. A database will provide more reliable long-term storage and support multiple users in the completed application. |
| ADR-03 | Users will manually enter movie and television show titles. The application will not use streaming service APIs, catalog APIs, or web scraping to automatically retrieve titles. | R2, R12 | Searching an external movie database, connecting to streaming services, or automatically importing titles. | Manual entry keeps the first release simple and avoids depending on outside services. It also follows the project's decision to let users manage their own watchlists. |
| ADR-04 | Each title will have an origin field that identifies it as either American or international as well as the type (Movie or Series) and status. Titles will also support optional notes and ratings from 0 to 10. Series entries will support episode progress tracking. | R2, R3, R13, R14, R15 | Allowing users to enter a specific country or using a larger list of regions. | A two-option classification keeps the form and filtering process simple while allowing users to distinguish between American and international titles. |
| ADR-05 | Users will be able to search titles by name and filter their watchlist by origin and watch status. The home screen will include All, To Watch, Watching, and Completed filters. | R4, R5, R7 | Requiring users to scroll through the entire list or providing only one filtering option. | Search and filtering make it easier for users to find titles in larger watchlists. These features also support the project's main goal of keeping movie and television lists organized. |
| ADR-06 | The public demo will use clearly labeled sample titles rather than presenting sample information as a user's personal watchlist. The application will be hosted without requiring paid hosting or exposed secrets. | R8, R9 | Requiring users to create an account before viewing the demo, using real personal watchlists in the public demo, or using paid hosting. | Sample data allows visitors and testers to explore the application without entering personal information. Free hosting makes the project accessible for demonstrations and testing. |

*Changed your mind later? Don't delete the old row — add a new ADR and write "Replaced by ADR-0X" in the old one.*

---

## 3. Screens & Build Order

*Every screen a user sees, plus any non-screen part (such as the data layer), in the order you'll build them — anything you leave out, the agent will invent. Carry over what worked in the Week 3 prototype test. P1 first, one scenario end to end before the next: first the one that shows your data (usually browsing), then the riskiest.*

| # | Screen or part | Route | Shows / does | Req IDs | Priority |
| --- | ---------------- | ------- | -------------- | --------- | ---------- |
| 1 | Simulated data layer (`data.js`) | — | Handles the watchlist using device-only browser storage. Includes functions to retrieve, add, update, and delete titles. Uses the Specification's field names and values for title, type, origin, status, notes, ratings, and episode progress. Provides sample titles for the public demo. | R1, R2, R3, R8, R11, R12, R13, R14 | P1 |
| 2 | Home / Watchlist | `/` | Displays the user's titles as cards, newest first. Includes the label "Sample titles. Not your personal list." when displaying sample data. Provides the All, To Watch, Watching, and Completed filters. Includes an Add Title button. | R1, R4, R8, R9 | P1 |
| 3 | Add Title form | `/add` | Allows users to enter a title, select Movie or Series, choose U.S. or International, and select Plan to Watch, Watching, Completed, On Hold, or Dropped. Prevents blank titles from being saved and displays "Type a title to save it." | R2, R6, R12 | P1 |
| 4 | Title Details | `/titles/:id` | Displays the selected title and its saved information. Allows users to change the title's status and return to the watchlist. Changes remain saved after reload. | R3 | P1 |
| 5 | Search and filter controls | `/` | Adds title search and filters for title type, origin, and status. Displays "No titles match. Clear filters." when no titles match and provides a way to clear the search and filters. | R4, R5, R7 | P1 |
| 6 | Phone layout and public demo | Application-wide | Keeps Add Title, filters, and Save usable at 375px width without horizontal scrolling. Loads on a free public URL without a login wall or exposed secrets. Uses clearly labeled sample data so the instructor can explore the application without an account. | R8, R9, R10 | P1 |
| 7 | Delete title functionality | Title card / details | Adds an X control to title cards so users can delete a title. The deleted title remains gone after reload. | R11 | P2 |
| 8 | Notes and ratings | `/add`, `/titles/:id` | Allows users to save an optional note and a rating from 0 to 10. Displays saved notes and ratings on the title after reload. | R13 | P2 |
| 9 | Series episode tracker | `/add`, `/titles/:id` | Shows current and total episode progress when the title type is Series. Hides episode fields when the title type is Movie. | R14 | P2 |

**Why this order:** The first build establishes the data layer, displays the watchlist, and allows users to add titles. This supports the main browsing and adding experience in S1 and the public demo in S4. The next build completes S2 by allowing users to search, filter, open titles, and update their status. These P1 features are completed and tested before adding P2 functionality such as deletion, notes, ratings, and episode tracking.

---

## 4. Risks & Assumptions

*Anything that might go wrong, and anything you're taking on faith — including accounts, APIs, or tools you depend on but don't control. Rate Likelihood and Impact as Low / Medium / High.*

| Risk or assumption | Likelihood | Impact | Mitigation |
| -------------------- | ------------ | -------- | ------------ |
| Browser storage data could be lost if a user clears browser data or switches devices. | Medium | High | Test that titles and status changes remain after reload. Clearly communicate that v1 uses device-only storage and does not support cloud syncing or cross-device access. |
| The simulated data storage could differ from the future database design, causing implementation work to need changes later. | Medium | High | Keep the data layer's field names and operations consistent with the Data & API Design document. Review the design before implementation and update it to reflect the Specification's device-only storage decision. |
| Sample data could be mistaken for a user's personal watchlist. | Low | Medium | Display "Sample titles. Not your personal list." whenever sample data is shown. Keep sample data separate from the user's device-only watchlist. |
| Inconsistent status values could cause incorrect filtering or display results. | Medium | Medium | Use the exact five status values from the Specification throughout the data layer, add form, title cards, and filters. Test each status against the acceptance tests. |
| The phone-width layout could make buttons, filters, or form fields difficult to use. | Medium | Medium | Follow the Style Guide and test the application at 375px width. Verify that Add Title, filters, and Save remain usable without horizontal scrolling. |
| Manual title entry could become inconvenient for users with larger watchlists. | Low | Medium | Keep the add-title form simple and test adding multiple U.S. and International titles. Do not add streaming or catalog APIs because they are outside the v1 scope. |

---

## SVC Self-Check

- [ ] **Simple** — the approach reads in under a minute; each ADR states one decision.
- [ ] **Valuable** — every ADR and screen has a requirement ID; every "Why this one" names a real trade-off, not "it was easier."
- [ ] **Complete** — ADR-00 names the full stack, starter skill, and database; every P1 requirement is covered by a screen or part; P1 comes first, one scenario end to end at a time; every risk has a mitigation; the team has approved it before Tasks are written.
