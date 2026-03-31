<!--
Sync Impact Report:
- Version change: null -> 1.0.0
- Added sections: Core Principles, Quality Constraints, Development Workflow, Governance
- Modified principles: (Initial Ratification)
  - I. Learning-Centered Interaction
  - II. Modular Architecture & Testability
  - III. Determinism in Testing
  - IV. Graceful AI Failure Handling
  - V. Observability and Context Continuity
- Templates requiring updates (updated / pending): 
  - .specify/templates/plan-template.md (updated)
  - .specify/templates/spec-template.md (updated)
  - .specify/templates/tasks-template.md (updated)
-->
# ESBot Constitution
## Core Principles
### I. Learning-Centered Interaction
User interactions MUST be structured to facilitate learning rather than passive consumption. The system SHALL guide users through explanations, quizzes, and constructive feedback to build comprehension based on educational course content.
### II. Modular Architecture & Testability
The system MUST follow a clear three-tier architecture (UI, Backend, Database) and an optional LLM component. Tight coupling SHALL NOT occur. Dependency injection and the Adapter pattern MUST be used for the AI inference layer to ensure tests can fully mock external components.
### III. Determinism in Testing
Since AI-generated responses are inherently probabilistic, testing MUST be tightly controlled. Prompts MUST be version-controlled assets. Test executions MUST set AI generation parameters (e.g. temperature=0) to minimize non-determinism, or utilize predefined mocked responses.
### IV. Graceful AI Failure Handling
The reliance on external LLM inference MUST NOT compromise core application stability. Whenever an AI request fails (e.g., API timeouts or 5xx errors), the system MUST present a clear, graceful fallback message to the student within 2-5 seconds, ensuring the session remains functional.
### V. Observability and Context Continuity
The system MUST implement robust semantic logging, including correlation IDs to trace the flow from UI to LLM. Stored sessions MUST ensure context continuity across sessions and enable precise root-cause analysis for hallucinations or formatting errors.
## Quality & Performance Constraints
- UI interactions SHOULD respond within 2-5 seconds.
- The system MUST achieve an Accuracy Rate of AI-generated feedback >90% against a golden dataset.
- The average time-to-task-completion (first-time workflow to quiz) MUST remain under 45 seconds.
## Development Workflow
- All submissions for course exercises MUST be organized in the \docs/\ folder.
- Unit and integration tests MUST mock the AI-interface 100%, targeting >80% backend code coverage.
- OpenAPI specifications MUST be used for automated UI-to-Backend contract testing.
## Governance
The constitution serves as the foundational rulebook for all architectural and development decisions for the ESBot project. 
- All Pull Requests and peer reviews MUST verify compliance with these core principles (especially test automation and AI mockability guidelines).
- Amendments to the constitution MUST increment the version following semantic versioning. 
- Ensure that the primary repository reference materials (README and docs/) are consulted as the runtime guidance.
**Version**: 1.0.0 | **Ratified**: 2026-03-31 | **Last Amended**: 2026-03-31
