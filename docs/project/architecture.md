# AlgoBridge - Architecture Draft

**Status:** Proposed, unimplemented. Final technology choices require advisor/team confirmation.

## 1. Logical architecture

```mermaid
flowchart TB
  W[Web Client] --> API[Application API]
  M[Mobile Client] --> API
  API --> AUTH[Authentication & Authorization]
  API --> CATALOG[Problem Catalogue Service]
  API --> SESSION[Practice Session Service]
  SESSION --> ENGINE[Guided Reasoning Engine]
  ENGINE --> RULES[Rule Validators]
  ENGINE --> FEEDBACK[Hint & Feedback Policies]
  CATALOG --> DB[(Application Database)]
  SESSION --> DB
  AUTH --> DB
  API --> ADMIN[Admin Content Service]
  ADMIN --> DB
  GUEST[Guest Practice State - Transient] -.-> SESSION
```

The mobile and Web clients are UI surfaces; the backend owns validation, progress and permissions.

Guest practice is available without authentication but must never gain access to another student's records or to hidden validation keys.
