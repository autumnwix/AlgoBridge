# AlgoBridge - Use Cases v0.2

**update time:** 11-25-26

## Role Definitions

| User | Expected Usage | Access |
|---|---|---|
| Guest | Explore and complete guided exercises without an account | Published exercises, structured activities, validation, feedback, hints, and temporary practice |
| Student/Learner | Practice algorithm problem-solving and track learning progress | Guest features plus saved sessions, resume, learning history, and dashboard |
| Admin | Manage and maintain educational content | Draft and published exercises, reasoning stages, validation rules, feedback, and exercise versions |

Learners are expected to have introductory programming and basic algorithm knowledge.

The main learning workflow focuses on understanding problem statements, identifying important information, comparing solution strategies, and constructing algorithms before coding.

### Guest Use Cases

| No. | Description |
|---|---|
| UC-G01 | Browse published exercises and problem summaries |
| UC-G02 | View public problem statements, examples, and constraints |
| UC-G03 | Register a Student account |
| UC-G04 | Log in to an existing account |
| UC-G05 | Complete guided reasoning activities, including problem decomposition, information extraction, and problem modeling |
| UC-G06 | Compare candidate algorithms and select suitable solution strategies |
| UC-G07 | Submit structured answers, receive feedback, request hints, and retry |
| UC-G08 | Explore interactive algorithm visualizations for supported exercises |
| UC-G09 | Complete available variant / transfer challenges and view an exercise summary |

Guest practice does not save permanent learning history or support cross-device resume.

### Student Use Cases

| No. | Description |
|---|---|
| UC-S01 | Browse and filter published exercises |
| UC-S02 | Start a guided reasoning exercise |
| UC-S03 | Submit and validate a reasoning response |
| UC-S04 | Request progressive hints |
| UC-S05 | Review feedback and retry a stage |
| UC-S06 | Complete an exercise and view its summary |
| UC-S07 | Resume an incomplete exercise |
| UC-S08 | View learning progress and mistake history |
| UC-S09 | Log out |
| UC-S10 | Identify problem inputs, objectives, constraints, parameters, and variables through guided activities |
| UC-S11 | Compare candidate algorithms and explain their suitability based on problem constraints |
| UC-S12 | Explore algorithm states and intermediate results through supported interactive visualizations |
| UC-S13 | Complete predefined variant problems and identify how changed conditions affect algorithm selection |
| UC-S14 | View basic skill-level performance, hint usage, and common misconceptions in the learning dashboard |

**Should:**

| No. | Description |
|---|---|
| UC-S15 | Select reasoning stages for review based on previous performance or personal preference |
| UC-S16 | Complete additional structured code-construction activities |
| UC-S17 | View recommended external practice problems related to completed exercises and identified weaknesses |

### Admin Use Cases

| No. | Description |
|---|---|
| UC-A01 | Create, update, and archive topics |
| UC-A02 | Create and edit problem content |
| UC-A03 | Configure reasoning stages and predefined response validators |
| UC-A04 | Manage feedback, misconception tags, and progressive hints |
| UC-A05 | Preview, publish, and unpublish exercises |
| UC-A06 | View aggregate exercise usage statistics (Should) |
| UC-A07 | Manage predefined algorithm comparison content and variant problems |
| UC-A08 | Configure supported interactive exercise activities using existing templates |

Admin content management uses predefined templates and configuration forms. A complex visual rule editor is not required for the MVP.
