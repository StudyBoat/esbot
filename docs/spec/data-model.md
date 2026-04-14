# Data Model Specification – ESBot

## 1. Overview

This document defines the persistence domain model for the ESBot system.  
The system follows a relational data model implemented using PostgreSQL and Entity Framework Core.

The goal of the data model is to support:

- conversational learning sessions,

- quiz generation and evaluation,

- persistent tracking of user interactions and performance.

## 2. Selected Entities

The following core entities are implemented:

- **User**

- **UserSession**

- **Message**

- **QuizRequest**

- **QuizItem**

- **SubmittedAnswer**

- **EvaluationResult**

These entities represent the complete lifecycle of a learning interaction within ESBot.

## 3. Entity Descriptions

### 3.1 User

Represents a registered user of the system.

**Attributes:**

- Id (UUID, PK)

- Username (string, required, max 50)

- Email (string, required, email pattern check)

- HashedPassword (string, required, min 8, max 50)

- CreatedAt (DateTime, required)

**Relationships:**

- 1:N with UserSession

### 3.2 UserSession

Represents a single learning session of a user.

**Attributes:**

- Id (UUID, PK)

- UserId (UUID, FK)

- StartedAt (DateTime, required)

- EndedAt (DateTime, optional)

**Relationships:**

- N:1 with User

- 1:N with Message

- 1:N with QuizRequest

### 3.3 Message

Represents a message within a session (user or AI).

**Attributes:**

- Id (UUID, PK)

- SessionId (UUID, FK)

- Content (string, required, max 4000)

- Role (enum: User, Bot, System)

- CreatedAt (DateTime, required)

**Relationships:**

- N:1 with UserSession

### 3.4 QuizRequest

Represents a request to generate a quiz.

**Attributes:**

- Id (UUID, PK)

- SessionId (UUID, FK)

- Topic (string, required, max 200)

- Difficulty (enum)

- CreatedAt (DateTime, required)

**Relationships:**

- N:1 with UserSession

- 1:N with QuizItem

### 3.5 QuizItem

Represents a single question within a quiz.

**Attributes:**

- Id (UUID, PK)

- QuizRequestId (UUID, FK)

- Question (string, required, max 2000)

- CorrectAnswer (string, required, max 1000)

**Relationships:**

- N:1 with QuizRequest

- 1:N with SubmittedAnswer

### 3.6 SubmittedAnswer

Represents a user’s answer to a quiz item.

**Attributes:**

- Id (UUID, PK)

- QuizItemId (UUID, FK)

- Answer (string, required, max 2000)

- SubmittedAt (DateTime, required)

**Relationships:**

- N:1 with QuizItem

- 1:1 with EvaluationResult

### 3.7 EvaluationResult

Represents the evaluation of a submitted answer.

**Attributes:**

- Id (UUID, PK)

- SubmittedAnswerId (UUID, FK, unique)

- IsCorrect (bool, required)

- Score (double, required)

- Feedback (string, optional)

**Relationships:**

- 1:1 with SubmittedAnswer

## 4. Relationship Cardinalities

| From            | To               | Cardinality |
| --------------- | ---------------- | ----------- |
| User            | UserSession      | 1:N         |
| UserSession     | Message          | 1:N         |
| UserSession     | QuizRequest      | 1:N         |
| QuizRequest     | QuizItem         | 1:N         |
| QuizItem        | SubmittedAnswer  | 1:N         |
| SubmittedAnswer | EvaluationResult | 1:1         |

## 5. Persistence Mapping Strategy

The ESBot system uses a **relational database (PostgreSQL)** with **Entity Framework Core** as ORM.

### Justification:

- Strong consistency requirements for user data and quiz results

- Clearly structured relationships between entities

- Efficient querying (joins, filtering, aggregations)

- Mature tooling and migration support via EF Core

### Implementation Details:

- Primary keys are UUIDs (GUIDs)

- Relationships are mapped via foreign keys

- Navigation properties are used for ORM tracking

- Validation constraints are defined via Data Annotations

Examples:

- `[Required]`

- `[MaxLength]`

- `[MinLength]`

- `[EmailAddress]`

## 6. Design Decisions

### Use of UUIDs

All entities use UUIDs instead of integers to:

- avoid ID collisions

- simplify distributed system scaling

- improve security (non-sequential IDs)

### Separation of Quiz Lifecycle

The quiz flow is split into:

- QuizRequest → generation

- QuizItem → structure

- SubmittedAnswer → user input

- EvaluationResult → feedback

This separation ensures:

- flexibility

- extensibility (e.g., multiple attempts, AI feedback)

- clear responsibility per entity

### Message Role Enum

The Message entity uses an enum (User, Bot, System) to:

- distinguish message origin

- support AI conversation logic

- allow future system-level instructions

### One-to-One Evaluation

Each SubmittedAnswer has exactly one EvaluationResult to:

- enforce a single evaluation per answer

- simplify querying and logic

## 8. Summary

The ESBot data model is:

- normalized and relational

- aligned with EF Core best practices

- structured for extensibility

- optimized for learning workflows and AI interaction
