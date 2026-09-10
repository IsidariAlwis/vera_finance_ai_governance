# VERA — Implementation Plan

## Verifiable Execution & Risk Authority

**Project:** VERA — Verifiable Execution & Risk Authority  
**Repository:** `vera-finance-ai-governance`  
**Status:** Implementation Planning Complete  
**Implementation Model:** Research-driven working prototype  
**Primary Objective:** Build a functional prototype that evaluates AI-generated financial actions before execution using evidence, policy, authority and risk controls.



# 1. Implementation Objective

The purpose of the implementation phase is to transform the VERA product and technical specifications into a working software prototype.

VERA will demonstrate the following control flow:

AI-generated proposal
→ Action intake
→ Evidence verification
→ Policy verification
→ Authority verification
→ Risk assessment
→ Deterministic decision
→ Human review when required
→ Audit record
→ Investigation / replay

The prototype must demonstrate that an AI-generated recommendation does not automatically receive authority to execute a financial action.

The system therefore separates:

- AI-generated recommendations
- verification
- authority
- risk assessment
- final decision
- human oversight
- auditability

The implementation must remain consistent with the existing Product Vision, Research & Evidence, Literature & Gap Analysis, Product Requirements Document, System Architecture, Data Model and API Specification.



# 2. Implementation Principles

The implementation will follow these principles.

## 2.1 Preserve the VERA Concept

The implementation must not turn VERA into a generic AI governance dashboard.

VERA is specifically focused on evaluating AI-generated financial actions before execution.



## 2.2 Deterministic Control Over Final Authority

The AI/LLM layer may assist with:

- evidence extraction
- evidence summarisation
- classification
- natural-language explanations
- identifying potentially relevant information

The AI/LLM layer must not independently determine the final VERA decision.

Final decisions must be produced by deterministic control logic.

Possible final outcomes:

- `APPROVE`
- `HUMAN_REVIEW`
- `BLOCK`



## 2.3 No Real Financial Execution

The prototype will simulate financial actions.

It will not:

- move real money
- connect to real bank accounts
- modify real customer accounts
- process real customer transactions
- use real customer data

Synthetic data will be used throughout the prototype.



## 2.4 Research-Driven Implementation

The implementation should demonstrate how the research and identified gaps influenced the system design.

Relevant design themes include:

- verifiability
- evidence traceability
- bounded authority
- human oversight
- explainability
- reproducibility
- auditability
- separation of intelligence from execution authority



## 2.5 Prototype Rather Than Production System

The project must be presented honestly as a research-driven prototype.

It must not claim to be:

- production-ready
- bank-grade
- regulatory-approved
- enterprise-certified
- production-secure
- a replacement for banking controls

The purpose is to demonstrate a technically credible approach to controlling AI-generated financial actions.



# 3. Technology Stack

The implementation will use the following stack.

## Frontend

- React
- Vite
- TypeScript
- React Router
- Tailwind CSS or equivalent lightweight UI system
- Recharts or equivalent charting library where appropriate

The frontend will communicate with the backend through the documented API.



## Backend

- Python
- FastAPI
- Pydantic
- SQLAlchemy
- Uvicorn

The backend will contain the core VERA control logic.



## Database

Primary target:

- PostgreSQL

Lightweight local fallback:

- SQLite

PostgreSQL should be treated as the primary architecture.

SQLite may be used for simplified local development when required.



## Database Migration

Use:

- Alembic

Database schema changes should be represented through migrations rather than manually modifying the database.



## Testing

Use:

- Pytest
- FastAPI testing utilities
- HTTPX where appropriate

Testing should cover both individual control engines and complete evaluation scenarios.



## Development Environment

Where practical, provide:

- `.env.example`
- Docker configuration
- PostgreSQL development environment
- clear local setup instructions

No secrets should be committed to the repository.



# 4. Target Repository Structure

The implementation should follow a modular structure similar to:

    vera-finance-ai-governance/
    │
    ├── README.md
    │
    ├── docs/
    │   ├── 01_PRODUCT_VISION.md
    │   ├── 02_RESEARCH_AND_EVIDENCE.md
    │   ├── 03_LITERATURE_AND_GAP_ANALYSIS.md
    │   ├── 04_PRODUCT_REQUIREMENTS_DOCUMENT.md
    │   ├── 05_SYSTEM_ARCHITECTURE.md
    │   ├── 06_DATA_MODEL.md
    │   ├── 07_API_SPECIFICATION.md
    │   └── 08_IMPLEMENTATION_PLAN.md
    │
    ├── backend/
    │   ├── app/
    │   │   ├── api/
    │   │   ├── core/
    │   │   ├── models/
    │   │   ├── schemas/
    │   │   ├── services/
    │   │   ├── engines/
    │   │   ├── repositories/
    │   │   ├── db/
    │   │   └── main.py
    │   │
    │   ├── tests/
    │   ├── alembic/
    │   ├── pyproject.toml
    │   └── .env.example
    │
    ├── frontend/
    │   ├── src/
    │   │   ├── components/
    │   │   ├── features/
    │   │   ├── pages/
    │   │   ├── layouts/
    │   │   ├── services/
    │   │   ├── hooks/
    │   │   ├── types/
    │   │   └── lib/
    │   │
    │   ├── package.json
    │   └── vite.config.ts
    │
    ├── data/
    │   ├── scenarios/
    │   └── seed/
    │
    └── ...
    
The exact structure may be adapted by the implementation tool when necessary, but the architectural separation must remain.


# 5. Implementation Phases

The implementation will be completed in the following sequence.



## Phase 1 — Repository Inspection and Environment Setup

Before creating major code, the implementation agent must inspect the existing repository.

It must identify:

- existing documentation
- existing configuration
- existing files
- existing dependencies
- existing Git configuration
- existing frontend/backend code, if any

Existing documentation must not be unnecessarily rewritten.

The implementation should then establish the required project structure and dependencies.

### Deliverables

- working backend environment
- working frontend environment
- database configuration
- environment variable configuration
- development instructions
- initial project structure



# 6. Phase 2 — Database Implementation

Implement the VERA data model using SQLAlchemy.

Core entities:

- Agent
- Action
- Evidence
- Policy
- Authority Rule
- Risk Assessment
- Decision
- Review
- Audit Event

Evaluation/scenario entities may also be added where required for the Scenario Lab.

Each entity should have:

- appropriate identifiers
- timestamps
- relationships
- foreign keys
- useful indexes
- appropriate status fields
- version information where relevant

The implementation must follow the previously defined Data Model.

Database migrations should be created with Alembic.



# 7. Phase 3 — Synthetic Data and Seed System

Create realistic but entirely synthetic financial data.

The seed system should include examples such as:

- synthetic AI agents
- synthetic actions
- synthetic evidence
- synthetic policies
- synthetic authority rules
- synthetic risk assessments
- synthetic reviews
- synthetic audit events

The data should be realistic enough to demonstrate the product but must not represent real customers.



# 8. Phase 4 — Core VERA Control Engines

The most important part of the implementation is the control engine.

The system should implement separate modules for:

1. Evidence Verification
2. Policy Verification
3. Authority Verification
4. Risk Assessment
5. Decision Determination

These should remain logically separated.



## 8.1 Evidence Verification Engine

The evidence engine evaluates whether sufficient supporting evidence exists for an action.

It should be capable of determining:

- whether evidence exists
- whether evidence is relevant
- whether evidence is valid for the scenario
- whether required evidence is missing
- evidence confidence/status
- evidence references

The result must be recorded so that the decision can later be investigated.



## 8.2 Policy Verification Engine

The policy engine evaluates the action against configured policies.

Examples may include:

- action type restrictions
- transaction thresholds
- refund conditions
- prohibited circumstances
- required evidence
- escalation requirements

Policies must be represented as data/configuration rather than scattered throughout frontend code.



## 8.3 Authority Verification Engine

The authority engine determines whether the AI agent has sufficient authority to propose the action.

Authority can depend on:

- agent
- role
- action type
- monetary limit
- currency
- policy
- escalation requirements

An AI agent may be capable of recommending an action while still lacking authority to execute it.

This distinction is central to VERA.



## 8.4 Risk Assessment Engine

The risk engine evaluates the action using the defined prototype risk factors.

Possible factors include:

- monetary value
- action type
- evidence quality
- policy result
- authority result
- agent characteristics
- scenario-specific risk indicators

The system should produce:

- numerical prototype risk score where appropriate
- risk level
- risk factors
- explanation

Risk levels:

- LOW
- MEDIUM
- HIGH

The implementation must keep the risk model transparent and understandable.



# 9. Phase 5 — Deterministic Decision Engine

The Decision Engine combines the control results.

It must determine one of:

- `APPROVE`
- `HUMAN_REVIEW`
- `BLOCK`

The decision logic must be deterministic and independently testable.

A simplified decision structure may follow:

1. Invalid action → validation failure
2. Mandatory evidence failure → BLOCK or HUMAN_REVIEW according to configured rule
3. Policy violation → BLOCK
4. Authority violation → BLOCK or escalation according to configured rule
5. High-risk action → HUMAN_REVIEW or BLOCK according to configured threshold
6. All mandatory controls pass and risk is acceptable → APPROVE

The final implementation must encode the actual rules consistently with the PRD and configured policies.

The decision engine must not rely on an LLM to choose the final outcome.



# 10. Phase 6 — Audit and Traceability

Every evaluation must create an auditable sequence.

The audit system should capture events such as:

- action received
- evidence evaluated
- policy evaluated
- authority evaluated
- risk evaluated
- decision produced
- review created
- review completed
- action status changed

Each event should have:

- event ID
- action ID
- timestamp
- event type
- relevant metadata
- actor/source where applicable

The audit trail should allow the user to understand how the final decision was reached.



# 11. Phase 7 — Human Review Workflow

Implement the human review system for actions requiring manual intervention.

A reviewer should be able to see:

- action details
- agent
- amount
- currency
- reason
- evidence
- evidence status
- policy result
- authority result
- risk result
- VERA explanation
- audit history

The reviewer should be able to complete the review with an appropriate outcome and comment.

Possible review outcomes can include:

- approve
- reject
- escalate

Review completion must generate an audit event.



# 12. Phase 8 — Backend API Implementation

Implement the endpoints already defined in the API Specification.

Core endpoints include:

    POST /actions/evaluate

    GET /actions/{action_id}

    GET /actions/{action_id}/decision

    GET /actions/{action_id}/audit

    POST /reviews

    POST /reviews/{review_id}/complete

    GET /policies

    GET /authority-rules

    GET /evaluation/scenarios

    POST /evaluation/scenarios/run

    GET /health

The API layer should primarily handle:

- request validation
- authentication-ready request context
- routing
- response formatting
- error handling
- service invocation

Core decision logic must remain outside the API route functions.

FastAPI should expose automatically generated OpenAPI documentation.



# 13. Phase 9 — AI / LLM Integration Layer

An optional AI layer may be implemented.

The architecture should isolate the AI/LLM provider behind an interface.

The AI layer may support:

- evidence extraction
- evidence summarisation
- action explanation
- classification assistance
- natural-language reasoning support

However:

    LLM output
        ↓
    VERA verification
        ↓
    deterministic controls
        ↓
    final decision

The LLM must never bypass:

- evidence verification
- policy verification
- authority verification
- risk assessment
- audit logging

The application should work without an external LLM API key.

A deterministic/mock provider should therefore be available for development and demonstration.



# 14. Phase 10 — Frontend Implementation

Build the VERA Operations Console using React + Vite.

The interface should feel like a sophisticated fintech risk and operations product.

It should be:

- professional
- modern
- information-dense
- clear
- evidence-oriented
- operational rather than decorative

It must not look like a generic AI chatbot.



# 15. Required Frontend Screens

## 15.1 Control Center Dashboard

Display:

- total evaluations
- approval count
- human review count
- blocked count
- risk distribution
- recent actions
- control failures
- evaluation activity
- system health

Users should be able to drill into individual actions.



## 15.2 Action Investigation

Display the complete evaluation of an individual action.

Suggested structure:

Action
↓
Evidence
↓
Policy
↓
Authority
↓
Risk
↓
Decision

The interface should make the decision path visually understandable.

The user should be able to inspect evidence and control results.


## 15.3 Human Review Queue

Provide:

- pending reviews
- filtering
- sorting
- risk level
- action type
- age
- review status

Selecting an item should open the detailed review workflow.


## 15.4 Review Detail

Show the complete evidence and control context.

Provide actions for:

- approve
- reject
- escalate

Require an appropriate reviewer comment where applicable.


## 15.5 Audit / Replay

Provide a chronological audit timeline.

The user should be able to inspect:

- event sequence
- timestamps
- evaluation stages
- control results
- decision
- review activity

Where technically feasible, provide a replay capability using the stored evaluation information.


## 15.6 Agent & Authority Management

Display:

- AI agents
- agent roles
- permitted action types
- monetary limits
- authority status
- relevant authority rules

This screen should visually reinforce the concept of bounded AI authority.


## 15.7 Policy Library

Display:

- policies
- descriptions
- versions
- status
- rules
- applicable action types

Policies should be presented as controlled configuration rather than arbitrary UI text.


## 15.8 Evidence Explorer

Allow users to inspect:

- evidence records
- evidence type
- source
- confidence
- verification status
- linked action


## 15.9 Scenario Lab

Provide predefined evaluation scenarios.

Users should be able to:

- select a scenario
- run the scenario
- inspect expected result
- inspect actual result
- determine pass/fail
- inspect the control path


## 15.10 AI Proposal Simulator

Provide a controlled interface where a user can simulate an AI-generated financial action.

The user may select:

- agent
- action type
- amount
- currency
- reason
- supporting evidence

The proposal is then submitted to VERA.

The resulting decision should be displayed with the complete verification path.



# 16. Frontend Data Principle

The frontend must not independently calculate the final VERA decision.

The frontend should:

1. collect input
2. send request to API
3. receive evaluation
4. display results
5. allow authorised review actions
6. retrieve audit information

The backend remains the source of truth for evaluation and decisions.


# 17. Phase 11 — Scenario Evaluation

Create a set of deterministic scenarios.

At minimum, implement scenarios representing:

### Scenario A — Valid Low-Risk Action

Expected:

`APPROVE`


### Scenario B — Insufficient Evidence

Expected:

`HUMAN_REVIEW` or `BLOCK` according to the configured control policy.


### Scenario C — Policy Violation

Expected:

`BLOCK`


### Scenario D — Authority Limit Violation

Expected:

`BLOCK` or escalation according to the configured authority rule.


### Scenario E — High-Risk Action

Expected:

`HUMAN_REVIEW` or `BLOCK` according to the configured risk threshold.


### Scenario F — Valid Action With Strong Evidence

Expected:

`APPROVE`

These scenarios should be executable through the Scenario Lab and automated tests.


# 18. Phase 12 — Testing Strategy

Testing is a major part of the VERA implementation.

## Unit Tests

Test:

- evidence engine
- policy engine
- authority engine
- risk engine
- decision engine
- audit service
- review service


## API Tests

Test:

- action evaluation
- action retrieval
- decision retrieval
- audit retrieval
- review creation
- review completion
- policies
- authority rules
- scenarios
- health endpoint


## Integration Tests

Where practical, test:

    API
    ↓
    service layer
    ↓
    control engines
    ↓
    database
    ↓
    audit trail


## Negative Tests

Include cases such as:

- invalid action type
- missing amount
- invalid currency
- missing agent
- missing evidence
- policy violation
- authority violation
- high-risk action
- malformed request
- duplicate request using Idempotency-Key


## Decision Precedence Tests

Explicitly test cases where multiple controls fail.

The purpose is to ensure that the final decision follows deterministic and documented precedence.


# 19. Phase 13 — Security and Reliability Basics

The prototype must include sensible engineering practices.

Implement:

- input validation
- safe error responses
- environment variables
- `.env.example`
- no secrets in source
- controlled action types
- CORS configuration
- request IDs
- correlation IDs where appropriate
- database constraints
- basic authorisation-ready structure
- idempotency support where defined by the API specification


# 20. Phase 14 — Observability

Provide basic operational metrics.

Examples:

- evaluation count
- evaluation latency
- approval rate
- human-review rate
- block rate
- control failure frequency
- API error rate
- scenario evaluation success rate

The dashboard should make the prototype's operational behaviour visible.


# 21. Phase 15 — UI/UX Refinement

After the functional frontend is working, refine the interface using the approved VERA design direction.

The UI should include:

- consistent design system
- typography hierarchy
- status indicators
- risk indicators
- decision badges
- evidence cards
- control-result cards
- timelines
- filtering
- drill-down interactions
- loading states
- empty states
- error states
- responsive behaviour

The interface should prioritise clarity over visual decoration.


# 22. Phase 16 — End-to-End Validation

The completed prototype must support the following complete flow:

1. User creates/simulates an AI-generated action.
2. Frontend submits the proposal.
3. Backend validates the request.
4. Action is stored.
5. Evidence is evaluated.
6. Policy is evaluated.
7. Authority is evaluated.
8. Risk is assessed.
9. Deterministic decision is produced.
10. Decision is stored.
11. Audit events are recorded.
12. Result is returned to the frontend.
13. User can investigate the action.
14. If required, a human review is created.
15. Reviewer completes the review.
16. Review result is stored.
17. Additional audit events are generated.
18. User can inspect the complete audit history.



# 23. Performance Target

The prototype should aim for typical evaluation completion under approximately two seconds under normal local development conditions.

This is a prototype performance target, not a production SLA.

Performance optimisation should not compromise:

- traceability
- deterministic controls
- auditability
- code clarity



# 24. Error Handling

The system should handle failures explicitly.

Examples:

- invalid input
- database failure
- missing evidence
- missing policy
- unavailable AI provider
- evaluation failure
- review failure

The frontend should provide useful user-facing error states without exposing sensitive internal information.



# 25. Documentation During Implementation

Existing documentation should remain the source of architectural intent.

Implementation should not rewrite previous documents simply to make them match generated code.

If implementation decisions materially change the design, document those changes separately.

The README should remain concise.

Detailed technical information should remain in `docs/`.



# 26. Git Workflow

Implementation should be developed incrementally.

Recommended logical milestones:

1. Project setup
2. Database foundation
3. Core control engines
4. Decision engine
5. API
6. Synthetic data
7. Testing
8. Frontend foundation
9. Dashboard
10. Investigation
11. Review workflow
12. Audit/replay
13. Scenario Lab
14. Refinement
15. Final validation

Each meaningful milestone should be committed separately where practical.

Commit messages should describe the actual change.

Examples:

    feat: add VERA evaluation engine

    feat: implement authority controls

    feat: add action evaluation API

    feat: add human review workflow

    feat: add audit timeline

    test: add decision engine scenarios


# 27. Replit Implementation Rules

Replit may be used as the primary implementation accelerator.

However, the implementation agent must follow these rules.

### Rule 1 — Inspect Before Modifying

Read the existing repository and documentation before creating or replacing architecture.

### Rule 2 — Preserve Existing Decisions

Do not replace the VERA concept with a generic AI platform.

### Rule 3 — Do Not Rewrite Documentation Unnecessarily

Existing research and product documentation should be preserved.

### Rule 4 — Build Real Functionality

Do not create a static mockup pretending to be a working system.

The prototype must contain:

- real backend routes
- real database persistence
- real control engines
- real decision logic
- real tests
- real frontend/API communication

### Rule 5 — Synthetic Data Only

Do not introduce real customer or financial data.

### Rule 6 — No Real Financial Execution

All financial actions are simulations.

### Rule 7 — LLM Cannot Decide Authority

An LLM may assist but cannot determine the final decision.

### Rule 8 — Keep Code Understandable

The implementation should be modular and readable rather than unnecessarily complex.

### Rule 9 — No Secrets

Do not hard-code API keys, passwords or credentials.

### Rule 10 — Test Before Declaring Completion

A feature is not considered complete simply because the UI renders.

The underlying API, database interaction and control logic must also work.



# 28. Definition of Done

VERA implementation will be considered complete when:

- [ ] Frontend runs successfully
- [ ] Backend runs successfully
- [ ] PostgreSQL integration works
- [ ] Database migrations work
- [ ] Synthetic seed data loads
- [ ] AI action proposals can be submitted
- [ ] Evidence verification works
- [ ] Policy verification works
- [ ] Authority verification works
- [ ] Risk assessment works
- [ ] Deterministic decision engine works
- [ ] APPROVE works
- [ ] HUMAN_REVIEW works
- [ ] BLOCK works
- [ ] Audit events are persisted
- [ ] Action investigation works
- [ ] Human review workflow works
- [ ] Scenario Lab works
- [ ] API documentation is available
- [ ] Automated tests pass
- [ ] Error states are handled
- [ ] No secrets are committed
- [ ] No real financial execution exists
- [ ] Prototype limitations are clearly stated
- [ ] README provides clear setup instructions


# 29. Final End-to-End Architecture

The implemented system should ultimately demonstrate:

                    AI / Agent
                        |
                        v
                AI Action Proposal
                        |
                        v
                 VERA API Intake
                        |
                        v
              +---------------------+
              |  Evidence Engine    |
              +---------------------+
                        |
                        v
              +---------------------+
              |   Policy Engine     |
              +---------------------+
                        |
                        v
              +---------------------+
              | Authority Engine    |
              +---------------------+
                        |
                        v
              +---------------------+
              |    Risk Engine      |
              +---------------------+
                        |
                        v
              +---------------------+
              |  Decision Engine    |
              +---------------------+
                        |
              +---------+---------+
              |         |         |
              v         v         v
           APPROVE   REVIEW     BLOCK
                        |
                        v
                 Human Reviewer
                        |
                        v
                 Final Review
                        |
                        v
                  Audit Trail
                        |
                        v
                Investigation /
                     Replay

The central architectural principle remains:

> AI intelligence does not equal execution authority.

VERA exists to verify the action before authority is granted to proceed.



# 30. Implementation Outcome

The final prototype should demonstrate a complete, research-driven control system for AI-generated financial actions.

It should show that VERA can:

- receive an AI-generated proposal
- verify supporting evidence
- evaluate policies
- verify authority
- assess risk
- produce a deterministic decision
- route uncertain or high-risk cases to humans
- record an auditable decision trail
- allow investigators to reconstruct what happened

The result should be a technically credible portfolio prototype demonstrating product thinking, backend engineering, data modelling, API design, risk/control design, AI governance concepts, UX design and operational thinking.

The prototype is intentionally limited to a simulated environment and does not execute real financial transactions.


# 31. Next Implementation Stage

Following approval of this implementation plan, the project moves from documentation into implementation.

The next stage is:

**CODE BUILDING**

The implementation should begin with repository inspection and technical setup, followed by the backend/database/control engine foundation.

The UI/UX design can be developed in parallel so that the functional frontend and visual design converge during implementation.

The implementation should not introduce a new product concept or architectural direction unless an explicit technical conflict is discovered.