## Exercise 3.2 (10 Points): ISO 25010 Mapping for UX

Map your selected UX factors to relevant ISO/IEC 25010 quality characteristics (for example: Usability, Functional Suitability, Reliability, Security, Maintainability, Compatibility).

For each mapping, define:

1. UX factor -> ISO 25010 characteristic(s)
2. A measurable quality criterion
3. A verification method (how you would evaluate or test it)

Important:

- Avoid vague wording such as "easy", "good", or "fast" without measurable criteria
- Ensure each criterion can be verified by a test, review, or measurable observation

Document your findings in `docs/spec/ux-quality-model.md`.

### Factors from 3.1
---
- **Actuality**
  
  - Functional Suitability
    - Functional Correctness
    - Functional Appropriateness
  
  - At least 90% of responses to current or rapidly changing topics match the approved reference sources or the latest course material.
  - Review / expert evaluation of the responses by comparing them with current reference sources or course materials

- **Efficiency**
  
  - Performance Efficiency
    - Time Behaviour

  - At least 80% of users receive a first meaningful answer to their main question within 30 seconds.
  - Measurement of response times using system logs or performance tests

- **Immersion**
  
  - Usability
  - At least 70% of users continue the learning session with two or more follow up interactions after the first answer.
  - Analysis of session logs, especially the number of follow up interactions per session

- **Intuitive Operation**
  
  - Usability
    - Appropriateness Recognizability
    - Operability
  
  - At least 80% of first time users can start a chat, upload a file, and request a quiz without using the help function.
  - Usability testing with new users and analysis of help function usage

- **Trust**
  
  - Security
    - Confidentiality
  
  - 0 critical security vulnerabilities and no unauthorized access to other users’ files or session data.
  - Security testing, for example penetration testing and access control testing