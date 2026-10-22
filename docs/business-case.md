# BingeBound — Business Case

> **When:** Week 1 · **Owner:** Lilah Leal · **Done when:** every item in the SVC Self-Check at the end is true.
>
> **Sponsor decision:** Go / No-go · **By:** James Lyst · **Date:** 22 October 2026
>
> **Filled-in Example:** `docs/examples/business-case-example.md`

The Business Case answers one question: *should we do this at all?* Keep it to about one page — detailed requirements belong in the Spec.

---

## 1. Problem

**Who is affected?** 
College students and young adults who watch shows and movies across several streaming services and countries.

**What's wrong today?** 
Titles they mean to watch next live in notes, screenshots, and half-remembered chats. The list is not searchable, status (want / watching / finished) is missing, and it disappears when the note app changes. Many apps only list popular content, leaving out lesser-known titles, especially from different countries. To keep things organized people tend to use unorganized notes or multiple apps to get what they need.

**How will we know it worked?** 
At least 70% of the team’s test users add five or more titles and mark a status within the first week of the demo.

---

## 2. Proposed Solution

A simple personal watchlist: sign in, add a title by name, set a status, make notes on each title, and search or filter your own list. During and after a series is finished, the user will be able to rate the series out of ten to further their completed status section sorting options. No social feed and no streaming catalog in the first version.

---

## 3. Options Considered

*Always compare against doing nothing — it's the baseline every other option has to beat. Mark the one you recommend.*

| Option | Description | Pros | Cons |
|--------|-------------|------|------|
| Do nothing | Keep using notes and memory | Zero effort | List stays unorganized, hard to read, and unsearchable |
| Option A   | Use Letterboxd or a streaming app’s list | Already built | Requires another account; list is not ours |
| Option B (recommended) | Build BingeBound, a small personal watchlist | Team owns the design; fits the term | Must stay small or it will not be finished in time |

---

## 4. Can We, and Is It Worth It?

*Answer honestly. If any answer is a clear "no," stop and rethink.*

| Question | Answer |
|----------|--------|
| **Will people actually use it?** | Yes, the pain of unorganized lists is real and the action (add a title) makes it easy with one step. |
| **Can we build it with what we have?** | Yes. Three students, free hosting, no paid APIs required. |
| **Can it be done in time to matter?** | Yes if scope stays on one user’s list. Social or catalog features would slip the demo. |
| **What does it cost?** One-time and per year — include ongoing costs such as hosting. | One-time: team time this term. Ongoing: $0 if we stay on GitHub Pages / free tier. |
| **What do we gain?** Say which benefits are measurable, and how much. Don't invent precise numbers. | A finishable course project and an organized list test users can actually search and manage easily. Success measure is in Section 1. |
---

## 5. Recommendation

Approve Option B (BingeBound). Waiting means the team starts implementation without a locked scope, and the demo date does not move.

---

## SVC Self-Check

- [x] **Simple** — fits on about one page; no tech stack or screen details.
- [x] **Valuable** — the problem names a specific group and a specific pain, not a solution; success is a measurable outcome, not a feature list.
- [x] **Complete** — "Do nothing" is compared; ongoing costs are included; the recommendation is one clear choice with a reason to act now; the sponsor has decided.
