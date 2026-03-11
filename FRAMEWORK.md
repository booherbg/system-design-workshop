# Genesys System Design Engine

## Project Overview

The Genesys System Design Engine (GSDE) is a **Socratic, agent-assisted framework** for creating, evolving, and maintaining system design artifacts.  
It is intended to support two types of users:

1. **Domain Expert** – Provides knowledge about the real-world problem space.  
2. **Engineer** – Explores architecture, capabilities, and technical trade-offs.

Agents act as **protectors of the process**, grading completeness, consistency, and clarity, surfacing ambiguities, generating tests, and producing summaries for human approval.

---

## Core Principles

- **Persistent Knowledge Base** – Artifacts evolve over time as users revisit the system.  
- **Socratic Discovery** – The system asks questions about edge cases, assumptions, and constraints.  
- **Agent Enforcement** – Agents continuously evaluate and grade the state of the project.  
- **Red/Green Test-Driven Development** – Tests are derived from domain events and user stories; human and agent collaboration enforces correctness.  
- **Human-in-the-Loop** – Humans resolve ambiguities, provide missing context, and approve agent summaries.  

---

## Artifact Structure

All artifacts are Markdown files in a `/genesys` folder.  

### 1. vision.md
- Purpose and goals of the system
- Intended users
- Success criteria

### 2. domain-model.md
- Entities
- Relationships
- Ubiquitous language
- Automation boundaries

### 3. domain-events.md
- Event definitions
- Event triggers
- Event consequences
- Event-based TDD scenarios

### 4. capabilities.md
- Core system capabilities
- Business outcomes supported

### 5. constraints.md
- Scalability, security, and operational constraints
- Regulatory or external system dependencies

### 6. system-context.md
- Internal components
- External systems and integrations
- Scope boundaries

### 7. user-stories.md
- Jobs-to-be-done style user stories
- Corner case variations
- Priority and dependencies

### 8. test-scenarios.md
- Red/Green test cases for domain events and user stories
- Links to evolving artifacts
- Status (RED/GREEN/REFRACTOR)

### 9. architecture-decisions.md
- ADRs for key design choices
- Trade-offs and rationale
- Links to impacted artifacts

### 10. failure-scenarios.md
- Edge cases
- System failure modes
- Human/agent mitigation plan

### 11. assumptions.md
- Explicitly stated unknowns
- Assumptions about scale, environment, and users

### 12. agent-feedback.md
- Output from evaluation agents
- Completeness, consistency, feasibility scores
- Suggested actions and human homework

### 13. summaries.md
- Human-readable summaries from agents
- Artifacts reviewed, approved, or pending clarification

---

## Process Flow

1. **Initial Discovery**  
   - User answers Socratic questions about reality, goals, and actors.  
   - Artifacts are generated and populated with initial content.

2. **Edge Case Exploration**  
   - Agents identify corner cases and ask questions.  
   - Humans provide answers, update artifacts, or supply missing context.

3. **Evaluation Loop**  
   - Agents grade artifacts for completeness, consistency, and clarity.  
   - Scores and issues are logged in `agent-feedback.md`.

4. **Test-Driven Alignment**  
   - Agents generate red/green test scenarios from domain events and user stories.  
   - Human and agent collaboratively implement and verify.

5. **Summary & Approval**  
   - Agents summarize their understanding.  
   - Humans approve, reject, or modify agent interpretations.

6. **Iteration**  
   - Repeat steps 2–5 until evaluation criteria reach target thresholds.  
   - Artifacts evolve and remain current over time.

---

## Notes

- Agents act as **protectors of the process** and will refuse to approve incomplete or ambiguous artifacts.  
- Humans resolve ambiguities and provide missing domain knowledge.  
- The goal is **durable, evolving, and testable system specifications**, not instant coding.  
- This framework supports **long-term maintainability**, corner case reasoning, and agent-assisted TDD.

---

## Next Steps

1. Populate `/genesys` folder with empty artifact Markdown files.  
2. Configure agents (e.g., Claude) to:  
   - Ask Socratic questions  
   - Grade artifact completeness and consistency  
   - Generate and track red/green tests  
   - Identify ambiguities for human resolution  
   - Produce summaries for approval
3. Begin iterative exploration of a target system using this framework.  

---

*Meta Note:*  
This document itself can evolve. Over time, agents and humans may propose refinements to the process flow, artifact definitions, and evaluation criteria. It is **a living artifact**—the first Genesys artifact of the system.
