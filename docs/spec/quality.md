# Quality Aspects Selection (ISO 25010)

| Quality Characteristic | Sub-characteristic | Justification for ESBot |
| :--- | :--- | :--- |
| **Functional Suitability** | Functional Correctness | The core value of ESBot is providing accurate educational content. If the AI hallucinates or gives wrong quiz feedback, the learning goal fails. |
| **Reliability** | Fault Tolerance | Since ESBot relies on external LLM inference (Ollama, vLLM), it must gracefully handle API timeouts or connection drops without crashing the user session. |
| **Usability** | Learnability | Students should be able to use the "Guided Learning" features immediately. The interface must be "self-describing" so the AI's role is clear. |
| **Maintainability** | Testability | Essential for this course. Because AI responses are probabilistic, the system must be built so we can isolate the logic from the AI's "randomness" during testing. |

## Quality Model: Functional Suitability (Functional Correctness)
* **Definition:** The degree to which the ESBot provides accurate and pedagogically sound responses.
* **Metric:** Accuracy Rate of AI-generated Feedback.
* **Measurement Method:** Evaluation of a predefined "Golden Dataset" (standardized questions/answers) compared against the system's generated output using a ROUGE score or expert review.
* **Target Value:** >90% alignment with course-specific reference material in 50 consecutive test runs.

## Quality Model: Usability (Learnability)
* **Definition:** The ease with which a student can use the "Guided Learning" and "Quiz" features without prior training.
* **Metric:** Time-to-Task-Completion (TTC).
* **Measurement Method:** A user study with 10 first-time users measuring the time from opening the app to successfully starting their first quiz.
* **Target Value:** Average TTC < 45 seconds; 100% completion rate without accessing a "Help" menu.

## Quality Model: Reliability (Fault Tolerance)
* **Metric:** Failure Rate of LLM API Calls.
* **Measurement Method:** Count the number of 5xx errors from the inference service versus successful responses.
* **Target Value:** 100% of failed calls must result in a "Graceful Fallback" message to the user within 2 seconds.

## Quality Model: Maintainability (Testability)
* **Metric:** Test Coverage & Mockability.
* **Measurement Method:** Percentage of backend code lines executed during unit tests; binary check if LLM response can be simulated.
* **Target Value:** >80% code coverage; 100% mockable AI-interface.

# Measures to Guarantee Testability

To ensure that ESBot can be comprehensively tested across all layers (Unit, Integration, and System), the following specific technical measures should be implemented during development:

## 1. Decoupling & Mocking of the AI Inference Layer
* **Implementation:** Use the **Adapter or Strategy Pattern** for the LLM Inference Engine. The Backend should interact with an interface rather than a specific API (like Ollama or vLLM).
* **Benefit:** This allows testers to "mock" the AI during unit and integration tests. Instead of calling a real LLM (which is slow and unpredictable), the test suite can return a fixed, predefined string to verify that the Backend handles the response correctly.

## 2. Prompt Versioning & Determinism Control
* **Implementation:** All system prompts (the instructions sent to the AI) must be stored as version-controlled assets, not hard-coded strings. Furthermore, the API calls should set the `temperature` parameter to `0` during testing.
* **Benefit:** This minimizes the "randomness" of the AI, making it easier to reproduce bugs and ensuring that tests are as deterministic as possible.

## 3. Traceability and Semantic Logging
* **Implementation:** Implement unique **Correlation IDs** for every user request that flow from the Frontend through the Backend to the LLM logs.
* **Benefit:** In the event of a test failure, developers can trace the exact prompt sent to the LLM and the raw JSON response received, allowing for precise root-cause analysis of "hallucinations" or formatting errors.

## 4. Dependency Injection for Database & Services
* **Implementation:** Use Dependency Injection (DI) to provide the Data Layer (Tier 3) to the Backend logic.
* **Benefit:** This enables the use of an In-Memory database (like SQLite in-memory) for automated tests. Testers can "seed" the database with specific learning sessions to test if the "Session Management" (FR5) correctly retrieves historical context.

## 5. Automated API Contract Testing
* **Implementation:** Define the communication between the Frontend (Tier 1) and Backend (Tier 2) using an OpenAPI (Swagger) specification.
* **Benefit:** Allows for automated contract testing to ensure that changes in the Backend logic don't break the UI, even before the full system is integrated.

*Info: GitHub Copilot used to refine sentences*