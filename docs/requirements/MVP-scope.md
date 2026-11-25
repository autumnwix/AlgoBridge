# MVP Feature List

*adjusted feature scope after 1st advisor meeting*  
**update time:** 11-25-26

## Section 1 - Feature Scope 
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

---

## Section 2 - MVP Feature List

**1. Exercise Library**

Provide 12 selected algorithm exercises across four categories, with problem descriptions, examples, difficulty levels, and category filters.  
Exercises may have different reasoning stages and levels of interaction.

**2. Guided Problem-Solving**

Guide learners through structured reasoning stages, including:

- Understanding the problem statement.
- Identifying inputs, outputs, objectives, and constraints.
- Extracting important information and defining parameters and variables.
- Building a structured problem representation.
- Recognizing algorithmic patterns.
- Selecting suitable algorithms and data structures.
- Constructing solution logic and basic pseudocode.

Use predefined structured questions and answer controls.

**3. Candidate Algorithm Comparison**

Allow learners to compare possible algorithms based on problem constraints, correctness, efficiency, and suitability.  
Provide explanations for why an algorithm is suitable, inefficient, or not generally correct for a given problem.

**4. Rule-Based Answer Checking and Misconception Detection**

Check structured answers using predefined server-side rules.  
Identify selected common mistakes in problem understanding, modeling, algorithm selection, and solution construction.  
Show appropriate feedback and allow learners to retry.

**5. Structured Feedback and Hints**

Provide prepared feedback for correct and incorrect answers, along with progressive hints to help learners understand each reasoning stage.

**6. Interactive Algorithm Visualization**

Provide interactive visualizations for selected exercises.  
Allow learners to observe algorithm states, predict intermediate results, and understand important state transitions.  
Visualization types depend on the supported algorithms and available development time.

**7. Variant / Transfer Problems**

Provide predefined variations of selected exercises where important constraints or conditions are changed.  
Ask learners to identify how these changes affect the problem model, algorithm choice, or solution logic.

**8. Learning Progress and Basic Analytics**

Allow registered Students to save exercise attempts, completed stages, hint usage, and identified mistakes.  
Provide a dashboard showing completed and unfinished exercises, learning history, and basic skill-level performance.  
Allow Students to resume their progress across devices.

**9. Cross-Platform Access**

Allow Guests and Students to browse exercises and complete guided practice through Web and Android/iOS mobile applications using the same backend.  
Students can access their saved progress from either platform.

**10. Basic Admin Management**

Allow authorized Admins to create and edit draft exercises, manage reasoning stages, validation rules, feedback, hints, and predefined variants.  
Allow Admins to preview, publish, and unpublish exercises using supported templates and configuration forms.

### Planned Features (Should)

**11. Selective / Personalized Review**

Allow Students to review selected reasoning stages based on previous mistakes, hint usage, and learning performance.  
Students can manually choose which stages to review.  
Use rule-based review recommendations without training a machine-learning model.

**12. Structured Code Construction**

Expand basic pseudocode and fill-in-the-blank activities with predefined code templates, incorrect-line identification, and statement selection.  
Support Python only in the initial version.

**13. External Practice Recommendations**

Recommend relevant LeetCode or other online judge problems based on exercise topics and identified learning weaknesses. 
Use curated problem metadata and rule-based matching.  
The system will not execute or grade external code submissions.

### Optional Features

- Advanced side-by-side algorithm visualization and comparison.
- More detailed learning analytics.
- Additional exercise interaction types.

### Scope Exclusions

- AI Tutor / LLM Chatbot.
- AI-Assisted Exercise Authoring and AI-generated complete exercises.
- Arbitrary code execution or compilation.
- Online judge integration and automatic submission grading.
- Machine-learning-based adaptive learning.
- Automatic grading of unrestricted free-text responses.
- Leaderboards, competitive contests, and social features.
- Advanced visual exercise editor.
- Multi-language code execution.
- Microservices / Distributed Systems.
- Production-scale Deployment.

### Exercise Coverage

The MVP targets 12 curated exercises across four algorithm categories:

- Divide and Conquer
- Dynamic Programming
- Greedy Algorithms
- Backtracking / Search

All published exercises should provide complete guided reasoning workflows, working answer validation, appropriate feedback, and hints.  
At least two exercises from different categories should demonstrate a deeper learning workflow with interactive visualization and transfer challenges.  
The final content coverage will be reviewed based on development progress and advisor feedback.
