# AlgoBridge - Figma Design Review (2026-11-10)

**Source:** [AlgoBridge Figma](https://www.figma.com/design/q742RXyimnSC1U86bx9Sud/AlgoBridge---Copy?node-id=2001-324)

This document records the pages and components found in the current Figma design. It is based on a review of the design files only. It does not confirm that the features have been implemented or that the designs represent the final system requirements.

## 1. Pages and Components

- `00 - component`: Stage Step (complete/current/upcoming), Reasoning Option (default/selected/error/correct), Feedback Banner (info/error/success), Hint Panel (Conceptual/Constraint/State/Transition), header and local component review.

These are the main UI components used in the design.

- `01 - Workspace Flow`: start screen and staged reasoning workspace. Visible stage names: Understand, Constraints, Pattern, Compare, Strategy, Skeleton, Reflect. Includes problem statement panel, constraints, options, hint preview, feedback and navigation.

Shows the exercise start screen and guided reasoning workspace.

- `02 - Dashboard & Admin Flows`: Student Dashboard (in-progress, completed, independent-success summary), Admin Problem Library (drafts/published/search/status/topic), Create Problem and further admin flow screens.

## 2. Implementation Notes

The Figma designs can be used as references during development. However, some parts may need to be changed or simplified to match the agreed MVP scope and the team's development time.

## 3. Items to Confirm Before Implementation

1. Guest practice is part of the current MVP requirements. It needs to be designed and tested separately because the existing Student-focused flows do not fully cover Guest usage.

2. The current Figma designs mainly show desktop screens. The mobile layout still needs to be designed and tested to make sure the main features work well on smaller screens.

3. The Knapsack example shows seven reasoning stages, but other exercises do not need to follow the same number or stage names.

4. The meaning and calculation of independent success should be clearly defined before including it in the Student Dashboard.

5. The Admin interface should follow the agreed MVP scope. Complex editing features may be simplified to predefined templates and configuration forms.

6. A feature shown in Figma does not automatically mean it is included in the final system. Each feature should be checked against the approved SRS before development.
