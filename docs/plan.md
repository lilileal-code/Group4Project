# [BingeBound] — Plan

> **When:** Week 3 (Sections 1–2), Week 4 (Sections 3–4) · **Owner:** Ben Anderson · **Done when:** every item in the SVC Self-Check at the end is true.
>
> **Version:** 1.1
>
> **Approved on:** ___ **by:** Product Owner: Lilah Leal · Architecture Lead: Austin Hammond · Delivery Lead: Ben Anderson
>
> **Filled-in Example:** `docs/examples/plan-example.md`

The Spec says *what* to build. The Plan says *how*, in what order, and what might go wrong.

Version 1.1 removes the simulated user picker and any login. Spec R9 and constitution item 1 forbid an account in v1.

---

## 1. Approach

BingeBound is a private notepad-style list of movies and shows. The user types each title. They can mark origin, type, and status, search, filter, and reopen a title. There is no account and no catalog. The course build stores the list in the browser and hosts the demo on GitHub Pages.

---

## 2. Key Decisions (ADRs)

| ADR | Decision | Req IDs | Alternatives considered | Why this one |
| ----- | ---------- | --------- | ------------------------- | -------------- |
| ADR-00 | Vue without a build step, a simulated data layer in `data.js` (browser storage plus sample JSON), GitHub Pages. No database and no auth in the course build. | R1–R15 | React, a real backend now, paid hosting. | Matches the course stack and the free-demo rule. A database would force login or a secret, which R9 forbids. |
| ADR-01 | No user accounts, no login, and no simulated user picker. One list per browser. Replaced the earlier “simulated user picker” idea. | R1, R8, R9 | Real auth, a user picker, shared household login. | A picker is still a login. The prototype tester asked about an account and continued once told there was none. |
| ADR-02 | Persist titles in browser storage. Sample titles live in a separate JSON file and are labeled. | R1, R2, R3, R8, R11, R13, R14 | In-memory only, PostgreSQL in the test build. | Reload must keep status (R3). In-memory fails that. A database is out of scope for v1. |
| ADR-03 | The user types every title. No streaming API, catalog API, or scraper. | R2, R12 | TMDB, Netflix import. | Constitution item 2. Keeps the demo free of keys. |
| ADR-04 | Each title has origin `U.S.` or `International`, type `Movie` or `Series`, and one of five statuses: Plan to Watch, Watching, Completed, Dropped, On Hold. Optional note and rating 0–10. Series may store episode current / total. No free-text country in v1. | R2, R3, R13, R14, R15 | Free-text country, three statuses, American as the label. | Spec R2 and R3. Prototype asked for free text; Q2 deferred it. “American” was changed to “U.S.” after the test. |
| ADR-05 | Search by title. Home filters: All, To Watch, Watching, Completed. Empty result shows “No titles match. Clear filters.” | R4, R5, R7 | Scroll only, one filter. | S3. The message is required by R7 even if the data function only returns an empty list. |
| ADR-06 | Public demo uses labeled sample titles, not a personal list. Free host, no secret, no login wall. | R8, R9 | Account-gated demo, paid host. | Constitution item 3. |

*Changed your mind later? Don't delete the old row — add a new ADR and write "Replaced by ADR-0X" in the old one.*

ADR-01 replaces the Week 3 draft that allowed a simulated user picker.

---

## 3. Screens & Build Order

| # | Screen or part | Route | Shows / does | Req IDs | Priority |
| --- | ---------------- | ------- | -------------- | --------- | ---------- |
| 1 | Data layer (`data.js`) | — | Device list in browser storage. Functions match Data & API Design: list, get, add, update, delete, demo list. Field names and enums match Section 1. No user id. | R1, R2, R3, R8, R11, R12, R13, R14 | P1 |
| 2 | Home / Watchlist | `/` | Cards, newest first. Label “Sample titles. Not your personal list.” when sample data is showing. Filters All, To Watch, Watching, Completed. Add Title button. | R1, R4, R8, R9 | P1 |
| 3 | Add Title form | `/add` | Title, Movie or Series, U.S. or International, five statuses. Blank title shows “Type a title to save it.” | R2, R6, R12, R15 | P1 |
| 4 | Title Details | `/titles/:id` | Shows saved fields. Change status. Persists after reload. | R3 | P1 |
| 5 | Search and filter controls | `/` | Live title search. Empty state “No titles match. Clear filters.” | R4, R5, R7 | P1 |
| 6 | Phone layout and public demo | Application-wide | 375px, no sideways scroll, 44px targets. GitHub Pages, no login wall. | R8, R9, R10 | P1 |
| 7 | Delete title | Title card | X removes the title. Gone after reload. | R11 | P2 |
| 8 | Notes and ratings | `/add`, `/titles/:id` | Optional note and rating 0–10. Persist. | R13 | P2 |
| 9 | Series episode tracker | `/add`, `/titles/:id` | Current / total when Series. Hidden when Movie. | R14 | P2 |

**Why this order:** Data layer first, then the list, then add, then open and change status. That is S1 and S2. Search and the empty message finish S3. Phone and the public URL finish S5. P2 (delete, notes, rating, episodes) waits until every P1 task is done.

---

## 4. Risks & Assumptions

| Risk or assumption | Likelihood | Impact | Mitigation |
| -------------------- | ------------ | -------- | ------------ |
| Clearing site data or switching devices loses the list. | Medium | High | Say on the list that v1 is this device only. Test reload. Do not promise sync. |
| Data & API Design could drift back to a User table. | Medium | High | Version 1.1 of that doc has no User. Review it before the validation build. |
| Sample data could be read as a personal list. | Low | Medium | Exact label from R8 whenever sample titles show. |
| Status or origin strings could disagree across docs. | Medium | Medium | Use the five statuses and `U.S.` / `International` everywhere. |
| 375px layout could clip filters or Save. | Medium | Medium | Style Guide spacing. Test R10 before calling T13 done. |
| Users may want a catalog search. | Low | Medium | Out of scope. R12. Do not add a key. |

---

## SVC Self-Check

- [x] **Simple** — approach is one paragraph. Each ADR is one decision.
- [x] **Valuable** — every ADR and screen has requirement IDs. “Why this one” names the trade-off.
- [ ] **Complete** — ADR-00 names the stack and says no database in the course build. P1 screens cover R1–R10 and R12. Approval line is still blank until the team signs 1.1.
