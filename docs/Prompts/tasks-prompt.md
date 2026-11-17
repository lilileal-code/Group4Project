# Tasks Prompt

**Now we will complete the `tasks.md` file based on the `plan.md`, `specification.md`, `data-api-design.md`, `style-guide.md`, and `business-case.md` files. Creating a complete, organized, and actionable task list for the **BingeBound** application. The goal is to break the approved project plan into small, independently implementable tasks that will guide the development of the front-end prototype.**

**Change the existing `tasks.md` by completing only Sections 1 (Task List) and 2 (Cross-Check). Leave Sections 3 (Gap Log) and 4 (Build Notes) untouched.**

## Task List

- **Structure the application** using the technology and starter approach established in ADR-00 of `plan.md`.
- **Create the simulated data layer** using the approved device-only browser storage approach. Ensure the data structure follows the entities and field definitions in `data-api-design.md` and supports the required title operations.
- **Implement the home/watchlist screen** to display the user's titles as cards, newest first, including the appropriate sample-data label for the public demo.
- **Implement the Add Title form** to support manually entering movie and series titles, selecting U.S. or International origin, and choosing from the five approved watch statuses.
- **Implement title details and status updates** so users can open a title, view its saved information, and change its status with changes preserved after reload.
- **Implement title search and filtering** using the requirements in `specification.md`, including searching by title and filtering by type, origin, and status.
- **Implement empty states and validation** for blank title submissions and searches or filters that return no matching titles.
- **Implement the public demo experience** using clearly labeled fake sample data, ensuring the application can be accessed through a free public URL without a login requirement or exposed secrets.
- **Implement the responsive phone-width layout** in accordance with the requirements in `specification.md` and the visual and accessibility rules in `style-guide.md`.
- **Implement title deletion** so users can remove titles and the deletion persists after reload.
- **Implement optional notes and ratings** so users can save notes and ratings from 0–10 and view them on the corresponding title after reload.
- **Implement the series episode tracker** to display current and total episode progress for series while hiding episode-tracking fields for movies.
- **Include appropriate tasks for testing** the P1 user scenarios, requirement acceptance tests, browser storage persistence, search and filtering behavior, and responsive layout.
- **Ensure every task traces to one or more relevant requirements (`R#`) or architecture decisions (`ADR-#`), with clear dependencies and measurable Definition of Done criteria.**

## Cross-Check

- **Complete the Cross-Check table** by tracing every P1 requirement from `specification.md` to its corresponding entity, field, or endpoint in `data-api-design.md`, its related ADR or screen number in `plan.md`, and the task IDs that implement it.
- **Verify that every P1 requirement has at least one corresponding task.**
- **Verify that every task traces to at least one requirement or ADR.**
- **Ensure there are no empty cells or unsupported references in the Cross-Check table.**
- **Add a brief Result statement** confirming whether all P1 requirements are traced and whether every task has a valid reference.

Follow the build order established in Section 3 of `plan.md`, prioritizing P1 tasks before P2 tasks and P2 tasks before P3 tasks. Break larger features into small, atomic tasks that can be implemented and tested independently, ideally within one day. Every task must start with an action verb and include a specific, measurable Definition of Done that identifies how or where the task will be verified.

Use only the status values `Not started`, `In progress`, `Done`, and `Blocked (Q#)`. Do not mark a task as `Done` unless its implementation has actually been completed and successfully tested or reviewed.

Use the exact requirement IDs, architecture decision IDs, entity names, field names, and endpoint definitions from the project documents. Do not invent missing requirements, endpoints, architecture decisions, or implementation details. If you discover conflicts or gaps between the documents, identify them rather than silently resolving them.

Avoid creating redundant tasks, duplicating existing functionality, introducing conflicting technologies, expanding beyond the approved project scope, or requiring an unnecessary rewrite of the application.

**Do not modify any other project documents. Do not write application code or begin implementation. Only update Sections 1 and 2 of `tasks.md`, preserving all other existing content and formatting.**