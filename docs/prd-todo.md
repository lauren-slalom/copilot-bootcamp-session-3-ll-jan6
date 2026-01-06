# Product Requirements Document (PRD) - TODO App Upgrade: Due Dates, Priority, Filters

## 1. Overview

We are upgrading the basic TODO app to support due dates, simple priority levels, and filters so users can better organize tasks and focus on time-sensitive work. The MVP remains intentionally lean and client-approved for local-only storage with no backend changes.

---

## 2. MVP Scope

- Title: required field for all tasks.
- Due Date: optional ISO `YYYY-MM-DD`; invalid values are ignored (treated as absent).
- Priority: enum `P1 | P2 | P3`, default `P3`.
- Filters: All, Today, Overdue.
  - In All: completed tasks are visible.
  - In Today and Overdue: show incomplete tasks only.
- Storage: local-only; no backend or external services.

---

## 3. Post-MVP Scope

- Overdue Highlighting: visually distinguish overdue tasks (e.g., red accent/background).
- Sorting Rules: overdue first → priority (P1→P3) → due date ascending → undated last.

---

## 4. Out of Scope

- Notifications.
- Recurring tasks.
- Multi-user features.
- Keyboard navigation/accessibility enhancements beyond basics.
- External/remote storage (stay local-only).
