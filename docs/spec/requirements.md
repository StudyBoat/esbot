# Functional Requirements (FR)
* **FR1: Conversational Learning Interface** - Provide a chat-based interface for users to ask questions and receive explanations.
* **FR2: Explanation and Example Generation** - Generate structured explanations and illustrative examples for course-related concepts.
* **FR3: Quiz and Practice Generation** - Enable users to request practice questions or quizzes on specific topics.
* **FR4: Answer Evaluation** - Provide feedback on user-submitted answers, including correctness and improvement tips.
* **FR5: Session Management** - Maintain user sessions and interaction history to allow continuity over time.
* **FR6: Backend API Access** - Expose functionality via a RESTful API for frontend-backend communication.
* **FR7: Guided Learning** - Offer follow-up prompts and clarification to deepen understanding.

# Non-Functional Requirements (NFR)
* **NFR1: Usability** - Intuitive and accessible UI requiring no prior training or onboarding.
* **NFR2: Performance** - Response times of 2-5 seconds (time to first toke) with up to 50 concurrent users.
* **NFR3: Scalability** - Ability to scale backend and AI inference components independently.
* **NFR4: Reliability** - Graceful handling of external AI service failures with meaningful fallback responses.
* **NFR5: Maintainability** - Modular three-tier architecture (UI, Backend, Data) for easy modification.
* **NFR6: Testability** - Design must support mocking AI components and enable unit, integration, and system testing.
* **NFR7: Security** - Protection of user data and basic input validation to prevent malicious inputs.
* **NFR8: Observability** - Logging and monitoring capabilities to trace interactions and system behavior.
* **NFR9: Web-Based Access** - No installation required; accessible via various devices through a browser.
* **NFR10: Uncertainty Management** - Structured handling of non-deterministic AI outputs to ensure clarity.
* **NFR11: Technology Stack & Development Environment** - The system shall use a predefined, team-aligned technology stack and tooling environment to ensure efficient development, maintainability, consistency, and scalability.
  * The used tech stack is described in [Techstack](<https://github.com/StudyBoat/esbot/blob/main/docs/TechStack.md>)



*Info: GitHub Copilot used to refine sentences*