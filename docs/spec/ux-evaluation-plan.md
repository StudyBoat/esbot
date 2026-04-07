## Exercise 3.3 (15 Points): UX Evaluation Plan and Acceptance Criteria

Create a compact UX evaluation plan for ESBot that can be executed in your team.

Your plan must include:

1. **Evaluation scope** (which UX factors and user journeys you will test)
2. **Method set** (e.g., heuristic evaluation, cognitive walkthrough, think-aloud sessions, scenario-based tests)
3. **Participants and setup** (target users, session duration, materials)
4. **Metrics and acceptance criteria** (measurable thresholds)
5. **Findings template** (issue description, severity, evidence, recommendation)
6. **Quality gate proposal** explaining when UX findings must block release

Align your acceptance criteria with:

- ISO/IEC 25010-based quality requirements
- Constitution principles (testability, architecture-aware contracts, and reviewable quality expectations)

Document your plan in `docs/spec/ux-evaluation-plan.md`.

# UX Evaluation Plan (ESBot)

## 1. Evaluation Scope

### UX Factors:

- Actuality
- Efficiency
- Immersion
- Intuitive Operation
- Credibility

### User Journeys:
The following journeys were selected because they represent the main intended usage of ESBot as an AI supported learning assistant:

  1. **First time onboarding and first interaction**
    - User opens ESBot for the first time and asks an initial question without prior instructions.

  2. **Concept explanation**
    - User asks a course related conceptual question and receives an explanation.

  3. **Iterative learning flow**
    - User asks a question, requests an example, starts a quiz, and continues with a follow up question.

  4. **Document supported learning**
    - User uploads learning material and asks ESBot to generate questions or explanations based on it.

  5. **Session continuation**
    - User returns to a previous session and continues learning with existing context.



## 2. Method Set

### Heuristic Evaluation
Two team members review ESBot based on usability principles (e.g., consistency, feedback, error prevention)

### Cognitive Walkthrough
The team performs a step by step walkthrough of first time usage scenarios to evaluate whether a new user can understand what to do at each step.

## 3. Participants and Setup

- **Target Users:**
  - 5–8 Computer Science students (primary ESBot audience)
  - Preferably students with mixed experience levels
- **Session Duration:**
  - ~15–30 minutes per participant
- **Setup:**
  - Laptop or smartphone with ESBot access
  - Stable internet connection
  - Test moderator for observing and noting

- **Materials:**
  - Prepared task scenarios
  - Example learning questions
  - Example lecture notes or documents for upload

## 4. Metrics and Acceptance Criteria

### 4.1 Intuitive Operation
**Sub characteristics:** Appropriateness Recognizability, Operability

**Metrics:**
- Whether users can complete the main tasks on their own
- How often users need help
- How many failed attempts or wrong clicks happen

**Acceptance Criteria:**
- At least **80% of first time users** can complete these tasks without help:
  - start a chat
  - ask a question
  - upload a file
  - request a quiz

---

### 4.2 Efficiency
**Sub characteristic:** Time Behaviour

**Metrics:**
- How long it takes until the first meaningful response appears
- How long users need to complete a task
- Whether the answer is useful for the user’s goal

**Acceptance Criteria:**
- At least **80% of users** receive a first meaningful answer to their main question within **30 seconds**
- At least **80% of the tested tasks** are completed within the time defined in the test scenario

---

### 4.3 Actuality
**Sub characteristics:** Functional Correctness, Functional Appropriateness

**Metrics:**
- Comparison of answers with current course material or approved sources
- Number of answers that are outdated, misleading, or incomplete

**Acceptance Criteria:**
- At least **90% of reviewed answers** match the current course material or approved reference sources
- No serious factual error is allowed in important predefined test questions

---

### 4.4 Trust
**Sub characteristics:** Confidentiality, Functional Correctness

**Metrics:**
- Number of critical or major security problems
- Number of misleading AI answers without warning
- User rating of trust after the session

**Acceptance Criteria:**
- **0 critical security vulnerabilities**
- **0 cases of unauthorized access** to another user’s files or sessions
- At least **80% of participants** rate ESBot as trustworthy with **4 or more out of 5**

---

### 4.5 Immersion
**Metrics:**
- Average session duration
- Number of follow up questions per session
- Whether users continue learning after the first answer

**Acceptance Criteria:**
- Average session duration is at least **5 minutes**
- At least **70% of users** ask at least **one follow up question** after the first answer


## 5. Findings Template

Each identified issue must be documented as follows:

## 5. Findings Template

Each issue should be documented in a simple and clear way:

- **Issue ID:** Unique identifier
- **Description:** What the problem is
- **Severity:**
  - **Critical:** blocks task completion or creates a serious risk
  - **Major:** strongly affects usability or learning flow
  - **Minor:** smaller issue with low impact
- **Evidence:** for example user quotes, observations, screenshots, logs, or measured data
- **Affected UX Factor:** for example Intuitive Operation, Efficiency, Trust
- **Recommendation:** suggested improvement

## 6. Quality Gate Proposal

UX findings should block the release if one of the following happens:

- there is any critical usability issue in an important user journey
- the task success rate is below 80%
- answer correctness is below 90%
- there are critical security vulnerabilities
- the system does not meet the defined response time

**Release is allowed only if:**

- all critical issues are fixed
- major issues are fixed or clearly documented and accepted
- acceptance criteria are met

## Alignment with Constitution Principles

- **Testability:**  
  The UX factors are connected to measurable criteria and can be checked through testing, observation, or review.

- **Architecture Aware Contracts:**  
  The criteria take different parts of the system into account, such as frontend usability, answer generation, and secure handling of session data.

- **Reviewable Quality Expectations:**  
  The acceptance criteria are written clearly, so the team can review them and decide objectively whether ESBot is ready for release.
