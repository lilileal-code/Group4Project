# BingeBound — Style Guide

> **When:** Week 2, alongside the Spec · **Owner:** Delivery Lead (whole team approves) · **Done when:** every item in the SVC Self-Check at the end is true.
>
> **Version:** 1.0
>
> **Approved on:** 29 October 2026 **by:** Delivery Lead: Ben Anderson · Product Owner: Lilah Leal · Architecture Lead: Austin Hammond
>
> **Filled-in Example:** `docs/examples/style-guide-example.md`

The Style Guide tells every screen — and every AI agent — exactly how the product looks and sounds, so nobody has to guess. It targets **WCAG 2.2 AA** accessibility.

---

## 1. Brand & Voice

- **Brand principles:** This is a personal list, not a streaming app. No posters, no play button, no “what’s trending.” American and international titles look the same except for a small origin label. 
- **Tone:** Brief, plain, a little warm. Like a notebook, not a service announcement.
- **Button example:** “Add title,” not “Submit entry.”
- **Error example:** “Please type a title to save it,” not “Error 400.”
- **Logo:** Bookmark mark plus the word Bingebound, dark green on the sage page. `docs/reference/BingeBoundLogo.jpg` Don’t stretch it, recolor it, or add any other icons to it.

---

## 2. Colors

Background is `#e2ebd6`. Ratios are against that background unless noted.

| Name | Hex | Use | Contrast vs. background |
| --- | --- | --- | --- |
| Primary | `#1d441D` | Titles, selected filter, primary button, borders | 9.01:1 |
| Text | `#1d441D` | Body text | 9.01:1 |
| Background | `#e2ebd6` | Page background | — |
| Error | `#481a14` | Error messages and delete | 11.92:1 |
| Border | `#1d441D` | Borders of form fields and buttons | 9.01:1 (passes 3:1) |
| Accent | `#a4eac6` | Chip and bookmark fill only. Never text on the page. | 1.13:1 — fails as text |
| Surface | `#FFFFFF` | Cards and the add form | Dark green on white is higher than on the page |

White text on a primary button is 11.07:1. Dark green on an accent chip is 7.99:1. Do not put `#a4eac6` text on `#e2ebd6`.

---

## 3. Type & Spacing

One font family.

| Role | Font | Size | Weight |
| --- | --- | --- | --- |
| Heading 1 | system-ui, Helvetica, Arial | 24px | 700 |
| Heading 2 | system-ui, Helvetica, Arial | 18px | 700 |
| Body | system-ui, Helvetica, Arial | 16px | 400 |

* Spacing scale: 8 / 16 / 24 / 32 / 48px, from an 8px base. Card gap is 16px. Page padding is 16px. Do not use 12px or 20px.
* Max content width: 420px, centered. This is a phone column, not a 1200px dashboard.
---

## 4. Components

Every button, link, and field is reachable with the keyboard and shows a 2px primary outline on focus.

| Component | Rules |
| --- | --- |
| Button (primary) | Label “Add title” or “Save.” Fill `#1d441D`, white text, 8px radius, min height 44px. Hover: darken fill slightly. Focus: 2px outline `#1d441D` offset 2px. Disabled: 50% opacity, no click. |
| Button (secondary) | Label “Cancel” or “Clear filters.” White fill, `#1d441D` border, text `#1d441D`. Hover: background `#a4eac6`. Focus: same 2px outline. Disabled: 50% opacity. |
| Card | White surface, 1px `#1d441D` border, 8px radius, 16px padding. Title is Heading 2 in `#1d441D`. Origin and status are words, not color alone. Hover: border stays primary, background tints toward `#e2ebd6`. Focus: 2px outline if the card is a link. |
| Form field | Label above the field. White fill, 1px `#1d441D` border, 16px text. Focus: 2px primary outline. Error: border and message in `#481a14`, message under the field (“Type a title to save it”). Disabled: muted fill, no edit. |
| Navigation | One row: Bingebound wordmark in `#1d441D`, then filters (All, To watch, Watching, Finished). Selected filter uses `#1d441D` fill and white text. Unselected uses white and a `#1d441D` border. Focus: 2px outline on the chip. No hamburger in v1. |

Demo label sits under the title: “Sample titles. Not your personal list.”
---

## SVC Self-Check

- [x] **Simple** — 3–7 colors, no more than 2 font families, one spacing scale.
- [x] **Valuable** — every rule would change how a screen gets built; the brand principles actually rule things out.
- [x] **Complete** — every section is filled or marked "N/A because…"; every color meets its contrast target; components include hover, focus, disabled, and error states; the whole team has approved it.
