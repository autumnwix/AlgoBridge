# AlgoBridge

**Interactive algorithm problem-solving through structured reasoning checkpoints.**

AlgoBridge helps computer science students move from recognizing algorithms in lectures to independently choosing and constructing strategies for unfamiliar problems. The platform uses curated, closed-ended reasoning stages, deterministic validation, progressive hints, misconception-specific feedback, and optional persistent learning progress.

> Status: SP1 requirements and architecture planning, November 2026. No implementation is claimed in this starter repository.

## Project baseline
- Approved video pitch: November 2026; first advisor meeting: 2026-11-17
- Internal integration target: 2027-02-12 (team target)
- Web + Android/iOS mobile clients; single backend and validation engine
- MVP: 3–5 worked problems for four algorithm categories each
- Rules:
  - Guest: can practice without an account, but cannot persist/resume sessions across devices
  - Student: persistent sessions and cross-device resume after sign-in
  - Admin: manages and publishes curated content (scope to be confirmed)

## Documentation
- [Project scope](docs/project/scope.md)
- [Requirements](docs/requirements/requirements.md)
- [Use cases](docs/requirements/use_cases.md)
- [Architecture draft](docs/design/architecture.md)
- [MVP problem candidates](docs/requirements/mvp_exercises.md)
- [Figma design](docs/design/figma_design.md)

## Design references
[Figma — AlgoBridge prototype](https://www.figma.com/design/q742RXyimnSC1U86bx9Sud/AlgoBridge---Copy?node-id=2001-324)

## Next steps
Review open decisions at the first advisor meeting. Do not interpret conceptual architecture as completed code.

## Tentative repo layout
| Path | Purpose | Current state |
|---|---|---|
| `apps/web/` | Next.js client and Web admin screens | Placeholder |
| `apps/mobile/` | Expo learner client | Placeholder |
| `backend/app/` | FastAPI modular monolith | Placeholder |
| `backend/tests/` | Backend unit/API tests | Deferred until Python scaffolding |
| `content/exercises/` | Version-controlled exercise definitions | Placeholder |
| `docs/project/` | Scope, decisions | Draft documents |
| `docs/requirements/` | Requirements, use cases, MVP problems | Draft documents |
| `docs/design/` | Architecture and audited Figma design | Draft documents |
| `docs/meetings/` | Advisor meeting agendas and notes | Draft document |
| `scripts/` | Setup and seed helpers | Placeholder |

