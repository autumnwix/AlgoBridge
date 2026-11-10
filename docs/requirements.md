# AlgoBridge — Functional Requirements Baseline v02
> This file is the draft for SRS

**Status:** current requirements for review, not frozen SRS (it'll adjust) 

**Date:** 2026-11-10

**Functional Requirements (FR)**
    - Every FR is a system behavior 
    - Numbers here are for readability
    - Every FR starts with "The system shall "

Priority: 
    **Must** = must do in MVP; 
    **Should** = important, but after core flow; 
    **Could** = future 

## Roles and account management
| No. | Priority | Requirement | Evidence / acceptance idea |
|---|---|---|---|
| FR001 | Must | allow guests to start a published guided exercise without registration | New anonymous user starts stage 1 |
| FR002 | Must | allow guests to submit structured reasoning responses, receive feedback and request available hints | Guest completes a sample exercise |
| FR003 | Must | not create an account-bound, durable learning record for guest practice | Guest session absent from registered progress; no cross-device resume |
| FR004 | Must | allow students to register, sign in and sign out securely | Login/logout works; private endpoint requires auth |
| FR005 | Must | enforce Student/Admin roles and account ownership on protected endpoints | Student A cannot read B's records; guest/student denied admin API |

## Exercise discovery
| No. | Priority | Requirement | Evidence / acceptance idea |
|---|---|---|---|
| FR006 | Must | list published exercises and show their topic, difficulty and description | Published listed, draft hidden |
| FR007 | Must | display statements, examples, input constraints and learning objectives | Detailed exercise page renders content |
| FR008 | Must | support topic/category filtering | Category selection filters |
| FR009 | Should | support title/keyword search | Search returns matching titles |

## Guided reasoning
| No. | Priority | Requirement | Evidence / acceptance idea |
|---|---|---|---|
| FR010 | Must | deliver ordered, configurable reasoning stages per exercise | Knapsack and another category have different stage configurations |
| FR011 | Must | render configured closed-ended response controls | Single-select, multi-select and ordering/structured choices render |
| FR012 | Must | validate submitted responses using predetermined server-side rules | Correct/incorrect/malformed test cases |
| FR013 | Must | return stage-specific feedback and configured misconception explanations | Distinct wrong choices trigger appropriate feedback |
| FR014 | Must | permit retries and unlock subsequent stages only when configured completion conditions are satisfied | Incorrect keeps locked, correct unlocks |
| FR015 | Must | reveal configured hints in progressive order on explicit request | Hint 1 revealed before Hint 2; hidden hints not returned early |
| FR016 | Must | provide a completion summary after the final stage | Final stage produces completion state/summary |
| FR017 | Should | support numeric/expression templates beyond basic structured answer controls | Optional validator suite |

## Learning state and progress
| No. | Priority | Requirement | Evidence / acceptance idea |
|---|---|---|---|
| FR018 | Must | create persistent exercise attempts for authenticated students | Start session creates record with owner |
| FR019 | Must | persist valid student submissions, stage completion and hint usage | Refresh and fetch retain state |
| FR020 | Must | allow an authenticated student to resume incomplete attempts from another device | Sign in on second client and continue |
| FR021 | Must | display a student's in-progress and completed exercises | Dashboard reflects learning records |
| FR022 | Should | display basic statistics and misconception/mistake trends | Aggregates agree with submissions |

## Content administration
| No. | Priority | Requirement | Evidence / acceptance idea |
|---|---|---|---|
| FR023 | Must | permit an authorized admin to create/edit draft exercise metadata and curated stage content through a defined management workflow | Admin can update draft, unauthorized user blocked |
| FR024 | Must | validate essential exercise configuration before publishing and permit publish/unpublish | Invalid rule blocks publish |
| FR025 | Must | preserve the exercise version referenced by saved historical student attempts | Existing attempts still resolve old version |
| FR026 | Should | support a rich visual editor for arbitrary response rules, misconception tags and reusable stage templates | Admin builds a new exercise without engineering intervention |
| FR027 | Should | display aggregate usage statistics for admins | Aggregate counts only, no unrestricted private attempts |

## Platform and safety
| No. | Priority | Requirement | Evidence / acceptance idea |
|---|---|---|---|
| FR028 | Must | expose one consistent API for Web and mobile clients | Same exercise definition and validation outcomes in both clients |
| FR029 | Must | withhold unpublished content, validator keys and unrevealed hints from learner-facing responses | API response tests detect no secrets |
| FR030 | Must | prevent a duplicate student submission from creating duplicate graded records when the same retry token is used | Repeat request creates one record |

## Core use-case traceability
| Use case | FRs | Candidate test |
|---|---|---|
| UC-G01 Guest practices | 001,002,003,010–016 | AT-GUEST |
| UC-S01 Register/login | 004,005 | AT-AUTH |
| UC-L01 Find problem | 006–009 | AT-LIBRARY |
| UC-L02 Complete reasoning stage | 010–015,029 | AT-STAGE |
| UC-S02 Resume across devices | 018–021,030 | AT-RESUME |
| UC-A01 Publish curated exercise | 023–026 | AT-ADMIN |
| UC-L03 Complete exercise | 016,021 | AT-COMPLETION |

## Candidate nonfunctional acceptance targets (subject to benchmarking)
- NFR01 Security: adaptive password hashing, HTTPS in deployment, server-side authorization checks
- NFR02 Reliability: transactional persistence for accepted student submissions and stage state; retry-safe submissions
- NFR03 Privacy: guests have no persistent learning profile; no cross-student reads
- NFR04 Maintainability: exercises with existing stage/answer types can be introduced through versioned configuration with minimal or no engine code changes
- NFR05 Testing: automated validation tests for correct, incorrect, malformed and boundary responses per supported rule strategy
- NFR06 Performance target (provisional): p95 validation < 1s at 20 concurrent users in a controlled environment; revise after measurement
- NFR07 Usability target (provisional): at least 80% of a small test group can complete a guided session without intervention; sample size and tasks to be defined
- NFR08 Compatibility: Web responsive browser and Expo mobile targets Android/iOS; real-device validation plan pending

## Differences from the earlier SRS
1. Prior SRS prohibited unauthenticated attempts; **FR001–003 now explicitly enable guest practice**
2. Prior SRS proposed 8–12 exercises
3. Rich arbitrary admin stage/rule authoring is moved to **Should**, while essential content publishing remains Must
4. essential closed-ended types and ordered hints, final exact repertoire pending Exercise 001 and advisor review
5. Previously quoted benchmark targets remain provisional, not claimed test outcomes

