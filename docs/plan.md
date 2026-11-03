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
|-----|----------|---------|-------------------------|--------------|
| ADR-00 | Use Vue without a build step for the frontend, a simulated backend for the test build, and GitHub Pages for hosting. PostgreSQL through Supabase is proposed as the database for the future system implementation. | R1–R12 | React, a backend framework, a different hosting provider, or a different database. | This follows the course's recommended technology stack and allows the team to build and test the application without requiring paid hosting or a complex backend. PostgreSQL provides a structured database option for the future implementation. |
| ADR-01 | The test build will use a simulated login or user-selection method. | R1, R9 | No user separation, device-only storage, or a fully implemented login system during the test build. | BingeBound is intended to keep each user's watchlist private. Simulated login allows the team to demonstrate separate users without building a complete authentication system during the test phase. |
| ADR-02 | The test build will use browser-based storage or simulated data. | R1, R2, R3, R11 | Storing all data only in memory, using browser storage for the entire application, or implementing the database during the test build. | Browser-based storage supports testing without requiring a live backend. A database will provide more reliable long-term storage and support multiple users in the completed application. |
| ADR-03: Manual Title Entry | Users will manually enter movie and television show titles. The application will not use streaming service APIs, catalog APIs, or web scraping to automatically retrieve titles. | R2, R12 | Searching an external movie database, connecting to streaming services, or automatically importing titles. | Manual entry keeps the first release simple and avoids depending on outside services. It also follows the project's decision to let users manage their own watchlists. |
| ADR-04: Title Origin Classification | Each title will have an origin field that identifies it as either American or international. | R2, R4 | Allowing users to enter a specific country or using a larger list of regions. | A two-option classification keeps the form and filtering process simple while allowing users to distinguish between American and international titles. |
| ADR-05: Search and Filtering | Users will be able to search titles by name and filter their watchlist by origin and watch status. | R4, R5, R7 | Requiring users to scroll through the entire list or providing only one filtering option. | Search and filtering make it easier for users to find titles in larger watchlists. These features also support the project's main goal of keeping movie and television lists organized. |
| ADR-06: Sample Data and Public Demo | The public demo will use clearly labeled sample titles rather than presenting sample information as a user's personal watchlist. The application will be hosted without requiring paid hosting or exposed secrets. | R8, R9 | Requiring users to create an account before viewing the demo, using real personal watchlists in the public demo, or using paid hosting. | Sample data allows visitors and testers to explore the application without entering personal information. Free hosting makes the project accessible for demonstrations and testing. |

*Changed your mind later? Don't delete the old row — add a new ADR and write "Replaced by ADR-0X" in the old one.*

---

## 3. Screens & Build Order

*Every screen a user sees, plus any non-screen part (such as the data layer), in the order you'll build them — anything you leave out, the agent will invent. Carry over what worked in the Week 3 prototype test. P1 first, one scenario end to end before the next: first the one that shows your data (usually browsing), then the riskiest.*

| # | Screen or part | Route | Shows / does | Req IDs | Priority |
|---|----------------|-------|--------------|---------|----------|
| 1 | | | | | P1 |
| 2 | | | | | |

**Why this order:** *(One or two sentences.)*

---

## 4. Risks & Assumptions

*Anything that might go wrong, and anything you're taking on faith — including accounts, APIs, or tools you depend on but don't control. Rate Likelihood and Impact as Low / Medium / High.*

| Risk or assumption | Likelihood | Impact | Mitigation |
|--------------------|------------|--------|------------|
| | | | |

---

## SVC Self-Check

- [ ] **Simple** — the approach reads in under a minute; each ADR states one decision.
- [ ] **Valuable** — every ADR and screen has a requirement ID; every "Why this one" names a real trade-off, not "it was easier."
- [ ] **Complete** — ADR-00 names the full stack, starter skill, and database; every P1 requirement is covered by a screen or part; P1 comes first, one scenario end to end at a time; every risk has a mitigation; the team has approved it before Tasks are written.
