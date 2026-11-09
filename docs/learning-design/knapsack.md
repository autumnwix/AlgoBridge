# Exercise 001 — 0/1 Knapsack Guided Reasoning Specification

**Document version:** 0.1 (draft)  
**Status:** Source-grounded baseline; proposed implementation details are distinguished below  
**Exercise ID:** `EX-001` (Figma label: `EXERCISE 001 · DYNAMIC PROGRAMMING`)  
**Audience:** CS students studying DSA/Algorithm Design  
**Difficulty:** Intermediate (Figma)  
**Estimated duration:** 8–10 minutes (Figma estimate; not measured)  
**Mode:** Closed-ended reasoning checkpoints with deterministic validation  
**Related:** [`../requirements.md`](../requirements.md), [`../scope.md`](../scope.md)

## 1. Source and fidelity notes

The source design is **Figma → `01 - Workspace Flow`**, including Desktop `D0–D8`, Mobile `M0–M9`, validated/incorrect variants, and Hint Panel. The pitch describes reasoning-first exercises, rule-based checking and progressive hints. This specification **preserves the source's seven-stage 0/1 Knapsack pathway**. It does not replace it with the separately discussed Binary Search concept.

- **Existing in Figma:** exact problem data; checkpoint prompts/answers; desktop/mobile UI states; some correct/error copy; skeleton token bank; four hint levels as UI concept; example summary figures.
- **Specified here to make coding/test possible (proposed):** machine-readable IDs, API-neutral response format, correctness/routing rules, a minimum two-level hint script per stage, exact event and score semantics, error handling and test IDs.
- **Not yet evidenced:** that the prototype has runnable validation, cross-session persistence, authenticated APIs, or scientifically validated performance metrics.
- Figma's sample completion metrics (e.g. `5 / 7` independent stages, `92%` interpretation) are **illustrative UI values**, not computed scores; do not hard-code them or claim they represent learning ability.

## 2. Problem card — source data

**Title:** 0/1 Knapsack Problem  
**Category:** Dynamic Programming  
**Statement (Figma):** “Choose items for a backpack with capacity 8. Each item may be selected at most once. Maximize the total value without exceeding the capacity.”

| Item | Weight | Value | Value/weight |
|---|---:|---:|---:|
| A | 2 | 3 | 1.50 |
| B | 3 | 4 | 1.33… |
| C | 4 | 5 | 1.25 |
| D | 5 | 8 | 1.60 |

**Instance capacity:** `W = 8`.  
**Teaching constraints stated in Figma:** `1 <= n <= 100`, `1 <= W <= 1000`, positive weights, nonnegative values, each item selectable at most once.

The teaching constraints describe the general task, whereas the four-row table is a particular practice instance. This distinction matters in Stage 2.

**Reference optimal choice for the shown instance (computed, not displayed as a source answer):** select **B + D**, weight `3 + 5 = 8`, value `4 + 8 = 12`; hence optimal value is **12**. This can be used in hidden content checks, but the learner's seven-stage source flow does not ask for this numeric answer directly.

## 3. Learning objectives

By completing this exercise, the learner should be able to:

1. Differentiate **optimization objective** from a **capacity constraint**.
2. Reason about feasibility of `O(nW)` versus exponential candidate methods under the given bounds.
3. Recognize overlapping include/skip subproblems as a clue for dynamic programming.
4. Explain why a value-ratio greedy rule is **not guaranteed** to solve 0/1 Knapsack optimally.
5. Define `dp[i][w]` correctly, distinguishing **capacity available** from **capacity used exactly**.
6. Assemble the bottom-up include/skip recurrence with restricted tokens, **without executing user code**.
7. Reflect on which reasoning concepts transfer to other problems.

## 4. Seven-stage source flow and proposed answer rules

| Stage ID | Figma label | Source prompt and response | Expected answer / validation | Next |
|---|---|---|---|---|
| `S01` | Understand / Problem Decomposition | “What is the optimization objective?” Options: maximize item count; **maximize total value without exceeding capacity**; minimize unused items | Correct only on objective=total value within capacity | S02 |
| `S02` | Constraints / Constraint Analysis | “Which time complexity is practical?” Options: `O(2^n)`, **`O(n × W) dynamic programming`**, `O(n!)` | Correct on `O(nW)` option | S03 |
| `S03` | Pattern / Pattern Recognition | “Which clue suggests dynamic programming?” Options: **subproblems overlap across choices**; sorted input; equal item values | Correct on overlapping subproblems | S04 |
| `S04` | Compare / Approach Comparison | “Why can’t a value-ratio greedy rule guarantee the optimum?” Options: **local ratio ignores future combinations**; distinct values guarantee greedy; capacity must be exactly filled | Correct on lack of guaranteed global optimum | S05 |
| `S05` | Strategy / Solution Strategy | Select what `i`, `w`, and `dp[i][w]` mean | All three correct: `i` = items considered; `w` = available capacity; `dp[i][w]` = maximum obtainable value | S06 |
| `S06` | Skeleton / Skeleton Builder | Complete `max(...)` transition using constrained token bank | All required tokens in designated positions, in valid order | S07 |
| `S07` | Reflect / Reflection & Transfer | “What idea should transfer to a new problem?” | Correct: **Define state from constraints before recurrence** (source mobile stage 7) | Summary |

**Design caveat:** This seven-stage template is specific to the Knapsack reference exercise. Do not force every future searching/greedy/graph problem to have a DP state or skeleton builder.

## 5. Checkpoint specifications

### S01 — Problem decomposition

**Prompt:** What is the optimization objective?  
**Source options:**
- `S01-A`: Maximize the number of selected items — incorrect
- `S01-B`: Maximize total value without exceeding capacity — **correct**
- `S01-C`: Minimize the number of unused items — incorrect

**Source incorrect-answer example (S01-A):** “The number of items is not what the problem asks you to maximize. Look for the quantity described as value, then keep the capacity as a restriction.” The screen labels this **Objective and constraint are different**.

**Proposed error mapping:** `S01-A → OBJECTIVE_CONFUSION`; `S01-C → WRONG_OBJECTIVE`; no additional unstated psychological inference.

**Proposed progressive hints** (content drafted here, not verbatim Figma except where stated):
1. Conceptual (source hint): “Identify the quantity the statement asks you to maximize. Keep the backpack capacity as a restriction, not the objective.”
2. More specific: “Look at the *value* column. The weight total must stay at or below 8.”

**Acceptance:** wrong answer yields choice-specific feedback and stays at S01; correct answer enables S02.

### S02 — Constraint analysis

**Prompt:** Which time complexity is practical?  
**Given:** `n <= 100`, `W <= 1000`, `nW <= 100,000` states (Figma visual).  
**Source choices:** `O(2^n)`, **`O(n × W) dynamic programming`**, `O(n!)`.

**Correct explanation in Figma:** “O(n × W) uses at most about 100,000 DP states here. Exponential search grows too quickly as n increases.”

**Technical accuracy note:** `O(nW)` is **pseudo-polynomial**, because runtime depends on the numeric capacity `W`, not just the bit length of its encoding. Say “practical under the stated bounds,” **not** “polynomial in the binary input length.”

**Proposed hints:**
1. Estimate the number of `(item count, capacity)` state combinations.
2. Multiply the largest allowed `n` and `W`; compare this with `2^100`.

**Validation:** correct if option `S02-NW`; no real runtime benchmarking is inferred.

### S03 — Pattern recognition

**Prompt:** Which clue suggests dynamic programming?  
**Source choices:** **Subproblems overlap across choices**; the input is already sorted; every item has equal value.

**Source explanation:** “Include/skip decisions revisit the same remaining capacities, so the best result for a state can be stored and reused.”

**Proposed hints:**
1. Consider what happens when different include/skip paths arrive at equivalent remaining subproblems.
2. Ask whether the answer for the same `(i, w)` needs to be computed twice.

**Validation:** only overlapping subproblems is correct.

### S04 — Approach comparison

**Prompt:** Why can’t a value-ratio greedy rule guarantee the optimum?  
**Source choices:** **Local ratio ignores future combinations**; distinct values guarantee greedy; capacity must always be filled exactly.

**Source explanation:** “A high-ratio item can consume capacity needed by a better combination. The problem lacks the exchange property required for a greedy proof.”

**Concrete counterexample using the Figma dataset (computed):**
- Ratio greedy picks **D** (ratio `8/5 = 1.6`); remaining capacity = 3; next **A** (ratio `3/2 = 1.5`); total weight 7, value **11**.
- Optimal selection **D + B**, weight 8, value **12**.
- Thus this instance demonstrates the failure of that particular value-ratio greedy ordering.

**Proposed hints:**
1. A locally best ratio does not necessarily produce the best set of items when items cannot be divided.
2. Compare choosing D then A with choosing D then B.

**Validation:** only the local-vs-global consequence option is correct; don't assume every greedy heuristic has the same counterexample.

### S05 — Solution strategy / DP State Builder

Figma has **three closed-ended subquestions**:

| Field | Source options | Correct |
|---|---|---|
| `i` | Current item weight / **Items considered** / Selected item count | Items considered |
| `w` | Total value / **Available capacity** / Exact used weight | Available capacity |
| `dp[i][w]` | Number of combinations / **Maximum obtainable value** / Minimum remaining capacity | Maximum obtainable value |

**Reference interpretation:** `dp[i][w]` = maximum total value obtainable using the **first `i` items** with total weight **at most `w`**.

**Proposed validation:** stage passes only when the three field identifiers are simultaneously correct. Record feedback per incorrect field; do not discard correct fields unless explicitly desired by the team.

**Proposed hints:**
1. The state must describe both how many items are considered and the capacity limit for the best value.
2. `i` counts the available prefix of items, `w` is a capacity allowance, and the table cell stores the best **value**.

**Misconception:** `w` is **not exact used weight**. It is maximum allowed capacity; unused capacity is permitted.

### S06 — Skeleton Builder

**Source intent:** “Complete the bottom-up DP skeleton.” The system **validates structure; it does not execute code**. Figma token bank includes `i - 1`, `w - weights[i - 1]`, `max`.

**Canonical reference skeleton (for a trusted answer key, not for code execution):**

```python
# Trusted teaching reference only. Learner inserts constrained tokens.
dp = [[0] * (W + 1) for _ in range(n + 1)]

for i in range(1, n + 1):
    for w in range(W + 1):
        dp[i][w] = dp[i - 1][w]  # skip item i
        if weights[i - 1] <= w:
            dp[i][w] = max(
                dp[i][w],
                values[i - 1] + dp[i - 1][w - weights[i - 1]]
            )
```

**Proposed answer schema:**
- `function_token`: `max`
- `previous_row_token`: `i - 1`
- `remaining_capacity_token`: `w - weights[i - 1]`

**Validation:** compare **token IDs** against a trusted answer template. Any missing, duplicated or misplaced required token fails; no `exec`, `eval`, arbitrary source compilation or system subprocess execution. Show which structural concept was mistaken without silently assembling the right program for the learner.

**Proposed hints:**
1. Decide between **skip** and **take**, using the larger obtainable value.
2. The **take** branch must reference the **previous item row** and capacity after subtracting the current item's weight.

**Acceptance:** correct token combination passes; invalid tokens and unintended strings fail gracefully.

### S07 — Reflection & Transfer

**Source mobile design (`M8`):** “What idea should transfer to a new problem?”
- **Correct:** Define state from constraints before recurrence.
- Incorrect: Always prefer a two-dimensional table.
- Other source choices, if any, should be extracted from the final approved design before implementation; **do not invent them**.

**Proposed hints:**
1. Look for a principle that remains useful even if the implementation changes.
2. A recurrence only makes sense after the meaning of a state has been defined.

**Validation:** correct option permits exercise completion. If the final UI includes extra options, enumerate and test each one in the authoritative content file.

## 6. State and validation behavior (proposed implementation contract)

### 6.1 Minimal attempt states

```text
NOT_STARTED → IN_PROGRESS → COMPLETED
                    │
                    └─ wrong answer → same checkpoint (retry)
```

The learning progress within `IN_PROGRESS` is `current_stage ∈ {S01,...,S07}`. Completing a required checkpoint advances to the next. Completion requires S01–S07 passed in sequence. Disallow jumping to later stages as an authority on completion.

### 6.2 Suggested data model (not a commitment to specific persistence schema)

```json
{
  "exercise_id": "EX-001",
  "exercise_version": 1,
  "attempt_id": "<server-issued-id>",
  "status": "in_progress",
  "current_stage_id": "S01",
  "stage_results": {
    "S01": {
      "passed": false,
      "checks": 0,
      "incorrect_checks": 0,
      "revealed_hint_ids": []
    }
  }
}
```

Do not trust client-supplied `passed`, computed correctness, stage order or attempt ownership. A local-only MVP must still ensure that UI state cannot trivially claim validated completion without actual checking. The final persistence/auth implementation is **DEC-02 TBD** in `scope.md`.

### 6.3 Proposed API-neutral evaluation result

```json
{
  "stage_id": "S01",
  "is_correct": false,
  "feedback_code": "OBJECTIVE_CONFUSION",
  "can_advance": false,
  "checks_count": 1,
  "incorrect_checks_count": 1
}
```

This is a **conceptual response contract**, not a previously agreed endpoint or final OpenAPI schema. The client should obtain display copy from a versioned server response or synchronized content dataset.

### 6.4 Attempt metric definitions (proposed; advisor approval required)

| Metric | Suggested definition |
|---|---|
| Checks | Count of formally submitted responses (excluding option selection changes) |
| Incorrect checks / mistakes | Count of submissions that fail the stage validation; repeat wrong submissions count again unless deduplicated by policy |
| Hints used | Count of distinct hints revealed during the attempt, not repeated panel opens |
| Independent stage | Passed on the first check, with zero hints revealed for that stage |
| Independent stages | Count of the seven stages meeting independent-stage criterion |
| Completed | All required stages passed; success summary shown |
| Reasoning profile percentage | **Not defined** by Figma; do not calculate or display as an ability measurement in MVP until an evidence-based scoring formula is approved |

Prototype summary values (`5/7`, `2 hints`, `2 mistakes`, 92%, etc.) are examples, not seeded true records.

## 7. Hint, feedback, and retry policies

- The Figma component library has four conceptual hint levels: **Conceptual, Constraint, State, Transition**. It does **not** establish verified hint scripts for every stage. The minimum authored content in this draft is **two progressively more specific hints per stage**, pending `DEC-04`.
- Hints appear **only when requested** and never trigger a correct submission automatically.
- On a wrong submission, return the defined failure code plus contextual explanation and allow retry. Correct stage feedback should say **why**, not merely “Correct.”
- Do not leak the full expected answer through the validator result before the agreed reveal policy. Backend may know the expected answer; the learner-facing client need not display it.
- Explicitly version the question/answer rules so an attempt isn't silently evaluated against a modified exercise.

## 8. Acceptance tests for Exercise 001

| Test ID | Given / Action | Expected |
|---|---|---|
| KN-001 | Open EX-001 introduction | Title, table A–D, W=8, constraints and seven-stage preview shown |
| KN-002 | S01: choose maximum number of items | Incorrect, `OBJECTIVE_CONFUSION` (or approved equivalent); remain S01 |
| KN-003 | S01: choose maximum total value within capacity | Correct; advance permitted to S02 |
| KN-004 | S02: choose `O(nW)` | Correct; explains at most about 100,000 states for stated bounds |
| KN-005 | S02: choose `O(2^n)` | Incorrect; remain S02 |
| KN-006 | S03: choose overlapping subproblems | Correct; allow S04 |
| KN-007 | S04: choose “local ratio ignores future combinations” | Correct; allow S05 |
| KN-008 | S05: `i = items considered`, `w = available capacity`, `dp = max value` | Correct; allow S06 |
| KN-009 | S05: choose `w = exact used weight` | Incorrect; explain at-most capacity semantics |
| KN-010 | S06: tokens `max`, `i - 1`, `w - weights[i - 1]` in correct slots | Correct; allow S07; no code execution |
| KN-011 | S06: wrong/missing token, unknown token or unexpected free text | Fail safely; no execution and no advance |
| KN-012 | S07: choose state-from-constraints principle | Correct; completion permitted |
| KN-013 | Any stage: wrong first answer then correct | Exactly two checks; one incorrect check; successful retry |
| KN-014 | Any stage: reveal hint 1 then hint 2 | Two distinct hints, correct ordering, count of 2; repeat reveal does not increase count |
| KN-015 | Attempt to jump from S01 directly to S07 or mark completed | Reject / do not grant completion |
| KN-016 | Complete all stages with predetermined events | Summary counts and independent-stage count match event history |
| KN-017 | Open equivalent Web and Mobile flow | Identical stage IDs, answer validity, hint order and result semantics |
| KN-018 | Backend receives stale exercise version or unauthorized attempt ID | Predictable error; no mutation of another/stale attempt |
| KN-019 | Validate reference instance with trusted test algorithm | Best value 12 using B+D; greedy D+A gives 11 |

**Test planning note:** KN-018 depends on chosen auth/session design. Adjust its precise API error/status code once the contract is approved.

## 9. Design traceability

| Content area | Desktop reference | Mobile reference |
|---|---|---|
| Introduction | `D0 — Start` | `M0 — Execrise 001` (Figma naming typo) |
| S01 Decomposition | `D1a / D1b — Decomposition` | `M1 — Guided Workspace` |
| Incorrect response | `D2 — Incorrect Feedback` | Error option states/components |
| S02 Constraints | `D3 — Constraint Reasoning` | `M3 — Stage 2 Constraints` |
| S03 Pattern | `D4a / D4b — Pattern Recognition` | `M4 — Stage 3 Pattern` |
| S04 Compare | `D5a / D5b — Approach Comparison` | `M5 — Stage 4 Compare` |
| S05 DP state | `D6 / D6b — DP State Builder` | `M6 — Stage 5 DP State` |
| S06 Skeleton | `D7 / D7b — Skeleton Builder` | `M7 — Stage 6 Skeleton` |
| S07 Reflection | Seven-stage desktop progress path / completion | `M8 — Stage 7 Reflect` |
| Summary | `D8 — Completion Summary` | `M9 — Mobile Completion Summary` |
| Hints | Hint Panel and four-level component variants | `M2 — Hint Expanded` |

## 10. Issues to resolve before implementing the full exercise

1. **Confirm author-approved S07 options.** Figma extraction directly establishes the correct option and one distractor, not a complete exhaustive source list.
2. **Confirm hint policy.** Four conceptual levels are shown, but this draft proposes two authored levels/stage for MVP.
3. **Confirm stage aggregation.** S05 contains three subquestions; count one independent stage only if its first **complete submitted state** is correct and no hints were revealed (proposed).
4. **Confirm metrics.** Do not display fabricated percentages or a machine-generated “reasoning profile” without a defined, tested algorithm.
5. **Confirm attempt persistence/auth model** and how progress resumes, as the pitch promises resume and the Figma start screen says “progress saves automatically.”
6. **Confirm the educational rationale** for assigning the same fixed seven stages to one exercise and whether other exercises use different stage sequences.
7. **Confirm display language/wording** and whether skeleton inputs are drag-and-drop or tap-to-place on mobile; both can share token validation.
8. **Check accessibility** of selected/error/correct states; text and icon should accompany color.

## 11. Minimum deliverable for the first vertical slice

Build **S01–S03** through the actual UI → evaluation → feedback → hint → retry → state-transition pathway on Web. It should be possible to prove KN-001–006, KN-013–015, then add S04–S07 and Mobile using the same data/validation semantics. This phased engineering order **does not remove the remaining four stages from the planned SP1 flagship exercise**.
