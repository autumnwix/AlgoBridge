# MVP Feature List

*adjusted feature scope after 1st advisor meeting*  
**update time:** 11-25-26

### Feature Scope

The project focuses on helping undergraduate CS students understand natural-language algorithm problems, identify relevant information, select suitable algorithms and data structures, and formulate solutions before coding.

The system will use curated exercises and structured reasoning stages rather than evaluating arbitrary student-written programs.

#### Core Features (Must)

1. **Exercise Library:** Provide 12 selected algorithm exercises across four categories, including problem statements, examples, constraints, and difficulty levels.

2. **Guided Problem-Solving:** Guide learners through problem understanding, information extraction, problem modeling, algorithm selection, and solution construction using structured activities.

3. **Algorithm Comparison:** Allow learners to evaluate predefined candidate algorithms based on correctness, efficiency, problem constraints, and suitability.

4. **Rule-Based Validation and Misconception Detection:** Validate structured responses on the server, identify predefined common mistakes, and return appropriate feedback.

5. **Progressive Feedback and Hints:** Provide prepared explanations and hints for different reasoning stages.

6. **Interactive Algorithm Visualization:** Support state exploration, step-by-step tracing, or intermediate-result prediction for selected exercises.

7. **Variant / Transfer Problems:** Provide predefined variations for selected exercises, allowing learners to analyze how changes in constraints affect the solution.

8. **Learning Progress and Basic Analytics:** Save Student attempts, stage completion, hint usage, and identified mistakes. Display progress and basic skill-level performance in the Student dashboard.

9. **Cross-Platform Access:** Support the core learning workflow on Web and Android/iOS using the same backend.

10. **Basic Admin Management:** Allow authorized Admins to manage exercise content, reasoning stages, answer rules, feedback, hints, and exercise versions.

#### Planned Features (Should)

1. **Selective / Personalized Review:** Recommend reasoning stages for review based on previous mistakes, retries, and hint usage. Students can manually choose which stages to review.

2. **Structured Code Construction:** Extend basic pseudocode and fill-in-the-blank activities with predefined code templates, incorrect-line identification, and statement selection.

3. **External Problem Recommendations:** Recommend relevant LeetCode or other online judge problems using curated metadata, algorithm topics, and Student learning records. The system will not execute or grade submissions from external platforms.

#### Optional Features

- Advanced side-by-side algorithm visualization and execution comparison.
- More detailed learning analytics and review recommendations.
- Additional interactive problem types and exercise templates.

#### Out of Scope for MVP

- AI-Assisted Exercise Authoring / AI-generated complete exercises.
- AI Tutor / LLM Chatbot.
- Full code execution, compilation, or online judge integration.
- Machine-learning-based adaptive learning or recommendation models.
- Automatic grading of unrestricted free-text answers.
- Competitive contests, leaderboards, and social features.
- Advanced visual exercise editor.
- Multi-language code execution support.
- Microservices or distributed systems.
- Production-scale deployment.

#### Exercise Coverage

The target remains 12 complete guided exercises across four algorithm categories.

Exercises may have different reasoning stages and levels of interaction. All published exercises must have reviewed content, working validation, feedback, and appropriate hints.

At least two exercises from different algorithm categories should demonstrate a deeper learning workflow, including problem decomposition, algorithm comparison, misconception-aware feedback, interactive visualization where appropriate, and transfer challenges.

The final exercise coverage and development order may be adjusted after the first complete proof of concept and advisor review.
