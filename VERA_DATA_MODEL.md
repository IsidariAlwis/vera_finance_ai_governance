# VERA Data Model

**Project:** VERA — Verifiable Execution & Risk Authority  
**Repository:** `vera-finance-ai-governance`  
**Document Type:** Data Model  
**Status:** Finalized  
**Version:** 1.0


## 1. Purpose

This document defines the logical data model for VERA.

VERA evaluates AI-generated financial action proposals against evidence, policy, authority and risk controls. The data model provides the structured representation required to:

- receive proposed actions
- store supporting evidence
- identify the requesting AI agent
- evaluate applicable policies
- evaluate authority boundaries
- record risk assessments
- produce final decisions
- manage human review
- maintain an auditable history
- support reproducible evaluation

The model is designed for a research-driven prototype using synthetic financial data.

No real customer financial information will be used.


# 2. Data Model Principles

## 2.1 Traceability

Every decision must be traceable back to the original proposed action.

The relationship is:

Action
  ↓
Control Evaluations
  ↓
Decision
  ↓
Audit Record

## 2.2 Separation of Control Results

Evidence, policy, authority and risk are represented as separate concepts.

This prevents one control from being incorrectly treated as another.

For example:

Evidence = sufficient
Policy = compliant
Authority = insufficient

must remain three independently observable results.

## 2.3 Version Awareness

Important control decisions must record the versions used during evaluation.

Examples:

policy_version
risk_model_version
decision_engine_version
system_version

This allows historical decisions to remain understandable even after rules change.

## 2.4 Synthetic Data

The prototype will use synthetic identifiers and fictional financial scenarios.

Example:

Customer: C-1024
Transaction: TX-80021
Agent: support-ai-01

These values must not represent real financial customers or accounts.

## 2.5 Auditability

Important state changes and decisions must be recorded so that the lifecycle of an action can be reconstructed.

# 3. High-Level Entity Model

The core VERA entities are:

Agent
   │
   │ proposes
   ▼
Action
   │
   ├──────────────► Evidence
   │
   ├──────────────► Policy Evaluation
   │
   ├──────────────► Authority Evaluation
   │
   ├──────────────► Risk Assessment
   │
   ├──────────────► Decision
   │
   ├──────────────► Review
   │
   └──────────────► Audit Events

Policies and authority rules are maintained independently and are referenced during evaluation.

# 4. Entity Overview

Entity and Purpose

Agent- Represents an AI agent or system proposing an action

Action- Represents the proposed financial action

Evidence	Represents supporting information for an action

Policy- Represents a versioned policy applicable to an action

Authority Rule- Defines what an actor is permitted to do

Risk Assessment- Stores the risk evaluation

Decision- Stores VERA's final automated decision

Review- Represents human intervention

Audit Event- Records important lifecycle events

Evaluation Scenario- Represents a controlled test scenario

# 5. Agent

The Agent entity identifies the AI system or actor that proposed the action.

Fields
agent_id
agent_name
agent_type
actor_role
status
description
created_at
updated_at
Example
agent_id: support-ai-01
agent_name: Customer Support AI
agent_type: LLM_AGENT
actor_role: SUPPORT_AGENT
status: ACTIVE

## 5.1 Agent Types

Initial supported types may include:

LLM_AGENT
RULE_BASED_AGENT
HUMAN_OPERATOR
SYSTEM_PROCESS

The prototype primarily focuses on AI-generated proposals.

# 6. Action

The Action entity is the central object in VERA.

It represents the financial action proposed for evaluation.

Fields
action_id
action_type
amount
currency
customer_ref
transaction_ref
requesting_agent_id
actor_role
reason
context
status
created_at
updated_at

## 6.1 Action Types

The initial prototype should support a small controlled set.

Examples:

REFUND
PAYMENT_REVERSAL
TRANSFER
FEE_ADJUSTMENT
ACCOUNT_CHANGE

The initial implementation may begin with REFUND as the primary scenario and expand later.

## 6.2 Action Status

Possible lifecycle states:

RECEIVED
EVALUATING
APPROVED
REVIEW_REQUIRED
BLOCKED
COMPLETED
FAILED

The prototype should distinguish between a VERA decision and actual execution status.

An APPROVED VERA decision does not mean that a real financial transaction has occurred.

# 7. Evidence

The Evidence entity represents information used to support or challenge a proposed action.

Fields
evidence_id
action_id
evidence_type
source
source_reference
content_summary
status
confidence
created_at
retrieved_at

## 7.1 Evidence Types

Examples:

TRANSACTION_RECORD
CUSTOMER_CASE
CUSTOMER_MESSAGE
FRAUD_ALERT
POLICY_REFERENCE
INTERNAL_RECORD
AGENT_JUSTIFICATION

## 7.2 Evidence Status

Possible states:

VALID
INVALID
MISSING
INSUFFICIENT
CONTRADICTORY
UNVERIFIED

## 7.3 Evidence Provenance

Where appropriate, evidence may also contain:

evidence_hash
source_type
source_timestamp
retrieval_timestamp

The purpose is to demonstrate provenance and support reproducibility.

# 8. Policy

The Policy entity represents the rules against which an action is evaluated.

Policies are versioned.

Fields
policy_id
policy_name
policy_version
action_type
description
rules
status
effective_from
effective_until
created_at
updated_at
8.1 Example Policy
policy_id:
REFUND-POLICY

policy_version:
1.2

action_type:
REFUND

Example rules:

Refund <= £500 may be automatically processed
Valid transaction evidence is required
Customer case evidence is required
Refunds above £500 require escalation

# 9. Authority Rule

The Authority Rule entity defines what an actor is permitted to do.

This entity is particularly important because VERA separates technical capability from execution authority.

Fields
authority_rule_id
actor_role
agent_id
action_type
maximum_amount
currency
approval_level
conditions
status
effective_from
effective_until

## 9.1 Example
authority_rule_id:
AUTH-SUPPORT-REFUND-01

actor_role:
SUPPORT_AGENT

action_type:
REFUND

maximum_amount:
500

currency:
GBP

approval_level:
AUTOMATED

If the proposed action is:

REFUND
£750

the Authority Engine should identify that the action exceeds the permitted limit.

# 10. Risk Assessment

The Risk Assessment entity stores the result of VERA's risk evaluation.

Fields
risk_id
action_id
risk_level
risk_score
risk_factors
assessment_version
created_at
10.1 Risk Levels
LOW
MEDIUM
HIGH
CRITICAL

## 10.2 Risk Factors

Risk factors may include:

HIGH_AMOUNT
AUTHORITY_BOUNDARY
POLICY_VIOLATION
INSUFFICIENT_EVIDENCE
CONTRADICTORY_EVIDENCE
HIGH_CUSTOMER_IMPACT
UNUSUAL_ACTION
MULTIPLE_CONTROL_FAILURES

## 10.3 Example

{
  "risk_level": "HIGH",
  "risk_score": 78,
  "risk_factors": [
    "HIGH_AMOUNT",
    "AUTHORITY_BOUNDARY"
  ],
  "assessment_version": "1.0"
}

The risk score is supporting information and does not independently determine the final decision.

# 11. Control Evaluation

For implementation, VERA should maintain a structured representation of individual control results.

A control evaluation may contain:

evaluation_id
action_id
control_type
result
reason
evaluation_version
evaluated_at
11.1 Control Types
EVIDENCE
POLICY
AUTHORITY
RISK

## 11.2 Control Results

Examples:

PASS
FAIL
REVIEW_REQUIRED
INSUFFICIENT
NOT_EVALUATED

This allows VERA to retain the individual results that led to the final decision.

# 12. Decision

The Decision entity stores the final result produced by the Decision Engine.

Fields
decision_id
action_id
decision
decision_reason
evidence_result
policy_result
authority_result
risk_level
risk_score
decision_engine_version
created_at

## 12.1 Decision Values

APPROVE
HUMAN_REVIEW
BLOCK

## 12.2 Example

{
  "decision": "BLOCK",
  "decision_reason": "The proposed refund exceeds the requesting agent's authorised limit.",
  "evidence_result": "PASS",
  "policy_result": "PASS",
  "authority_result": "FAIL",
  "risk_level": "HIGH",
  "risk_score": 78,
  "decision_engine_version": "1.0"
}

# 13. Decision Explanation

The system should retain a structured explanation associated with the decision.

Fields
explanation_id
decision_id
summary
control_summary
risk_summary
recommended_next_step
generated_by
created_at

The explanation should primarily be derived from deterministic control results.

An LLM may assist with wording in future versions, but it must not alter the underlying decision.

# 14. Human Review

The Review entity represents a case requiring human intervention.

Fields
review_id
action_id
decision_id
review_status
reviewer_id
reviewer_role
reviewer_decision
review_comment
created_at
assigned_at
completed_at

## 14.1 Review Status

PENDING
ASSIGNED
COMPLETED
CANCELLED

## 14.2 Reviewer Decision

APPROVE
REJECT

A reviewer must provide a reason when completing a review.

# 15. Audit Event

The Audit Event entity records important lifecycle events.

Fields
audit_id
action_id
event_type
actor
event_timestamp
event_data
request_id
system_version

## 15.1 Audit Event Types

Examples:

ACTION_RECEIVED
ACTION_VALIDATED
EVIDENCE_EVALUATED
POLICY_EVALUATED
AUTHORITY_EVALUATED
RISK_EVALUATED
DECISION_CREATED
REVIEW_CREATED
REVIEW_COMPLETED
DECISION_RETURNED

# 16. Evaluation Scenario

The Evaluation Scenario entity supports systematic testing of VERA.

Fields
scenario_id
scenario_name
description
input_data
expected_decision
expected_controls
category
created_at

## 16.1 Example

scenario_id:
SC-04

scenario_name:
Authority Limit Violation

expected_decision:
BLOCK

expected_controls:
Authority = FAIL

# 17. Relationships
Agent → Action

One agent may propose many actions.

Agent 1 ────────< Action

Relationship:

Agent.agent_id
        ↓
Action.requesting_agent_id
Action → Evidence

One action may contain multiple evidence items.

Action 1 ────────< Evidence
Action → Control Evaluations

One action can generate multiple control evaluations.

Action 1 ────────< Control Evaluation
Action → Risk Assessment

One action should have a risk assessment for each evaluation cycle.

The prototype may maintain the latest assessment while preserving historical versions where required.

Action 1 ────────< Risk Assessment
Action → Decision

An action produces a decision.

Action 1 ────────< Decision

Multiple decisions may exist if an action passes through human review or is re-evaluated.

Action → Review

An action may create one or more review records.

Action 1 ────────< Review
Action → Audit Event

An action can generate many audit events.

Action 1 ────────< Audit Event

# 18. Entity Relationship Diagram

The logical model is:

                         ┌───────────────┐
                         │     AGENT     │
                         └───────┬───────┘
                                 │
                                 │ 1:N
                                 ▼
                         ┌───────────────┐
                         │     ACTION    │
                         └───────┬───────┘
                                 │
              ┌──────────────────┼──────────────────┐
              │                  │                  │
             1:N                1:N                1:N
              │                  │                  │
              ▼                  ▼                  ▼
        ┌───────────┐     ┌──────────────┐    ┌──────────────┐
        │  EVIDENCE │     │   CONTROL    │    │ RISK         │
        │           │     │  EVALUATION  │    │ ASSESSMENT   │
        └───────────┘     └──────────────┘    └──────────────┘
                                 │
                                 │
                                 ▼
                         ┌───────────────┐
                         │    DECISION   │
                         └───────┬───────┘
                                 │
                        ┌────────┴────────┐
                        │                 │
                       1:N               1:N
                        │                 │
                        ▼                 ▼
                 ┌────────────┐    ┌──────────────┐
                 │   REVIEW   │    │   EXPLANATION│
                 └────────────┘    └──────────────┘

                         ACTION
                           │
                           │ 1:N
                           ▼
                    ┌──────────────┐
                    │ AUDIT EVENT  │
                    └──────────────┘


          ┌──────────────────┐
          │      POLICY      │
          └────────┬─────────┘
                   │
                   │ referenced during evaluation
                   ▼
              CONTROL RESULT


          ┌──────────────────────┐
          │   AUTHORITY RULE     │
          └──────────┬───────────┘
                     │
                     │ referenced during evaluation
                     ▼
                CONTROL RESULT

# 19. Database Design

The preferred database for the prototype is PostgreSQL.

The initial relational tables are:

agents
actions
evidence
policies
authority_rules
control_evaluations
risk_assessments
decisions
decision_explanations
reviews
audit_events
evaluation_scenarios

# 20. Primary Keys

Each entity should have a unique identifier.

Examples:

agent_id
action_id
evidence_id
policy_id
authority_rule_id
evaluation_id
risk_id
decision_id
explanation_id
review_id
audit_id
scenario_id

UUIDs are preferred for externally exposed identifiers.

# 21. Foreign Keys

Core relationships include:

actions.requesting_agent_id
    → agents.agent_id

evidence.action_id
    → actions.action_id

control_evaluations.action_id
    → actions.action_id

risk_assessments.action_id
    → actions.action_id

decisions.action_id
    → actions.action_id

decision_explanations.decision_id
    → decisions.decision_id

reviews.action_id
    → actions.action_id

reviews.decision_id
    → decisions.decision_id

audit_events.action_id
    → actions.action_id

# 22. Data Integrity Rules

The database should enforce important integrity constraints.

Examples:

Amount
amount >= 0
Currency

Currency must be represented using a controlled three-letter currency code.

Example:

GBP
EUR
USD
Required action fields

Every action must have:

action_id
action_type
requesting_agent_id
created_at
Decision

A decision must belong to an existing action.

Evidence

Evidence must reference an existing action.

Review

A review must reference the action that triggered it.

# 23. Monetary Data

Financial amounts must not be represented using binary floating-point values for authoritative monetary calculations.

The implementation should use a suitable decimal representation.

For example:

DECIMAL / NUMERIC

rather than:

FLOAT

This prevents common floating-point precision problems in financial calculations.

# 24. Timestamps

Timestamps should be stored consistently using timezone-aware timestamps.

Important timestamps include:

created_at
updated_at
retrieved_at
evaluated_at
completed_at
event_timestamp

UTC should be preferred for stored timestamps.

# 25. Sensitive Data Boundary

The prototype must minimise sensitive information.

The database should not store:

real bank account numbers
card numbers
passwords
authentication credentials
real customer identity documents
real financial account credentials
unnecessary personal information

Synthetic references should be used instead.

# 26. Data Retention for the Prototype

Because this is a research prototype, data retention should be simple and transparent.

Evaluation records should be retained for:

debugging
testing
demonstrations
reproducibility
research analysis

A future production implementation would require formal retention and deletion policies.

# 27. Versioning Strategy

The following should be versioned independently:

Policy
Risk Assessment
Decision Engine
System

Example:

policy_version = REFUND-1.2
risk_model_version = RISK-1.0
decision_engine_version = DECISION-1.0
system_version = 1.0.0

This allows VERA to answer:

Which version of the system made this decision?

# 28. Reproducibility

Given the same:

Action
Evidence
Policy Version
Authority Rules
Risk Configuration
Decision Engine Version

the VERA prototype should produce a reproducible decision.

This is a core design requirement.

# 29. Data Lifecycle

The lifecycle of an action is:

PROPOSED
   ↓
RECEIVED
   ↓
VALIDATED
   ↓
EVALUATED
   │
   ├── Evidence
   ├── Policy
   ├── Authority
   └── Risk
   ↓
DECISION
   │
   ├── APPROVE
   ├── HUMAN_REVIEW
   └── BLOCK
          │
          ▼
       AUDIT

For HUMAN_REVIEW:

HUMAN_REVIEW
      ↓
REVIEW CREATED
      ↓
REVIEWER DECISION
      ↓
APPROVE / REJECT
      ↓
AUDIT

# 30. Data Flow Example

A synthetic refund request may be represented as:

Agent
support-ai-01

        ↓

Action
REFUND
£750
GBP

        ↓

Evidence
Transaction Record
Customer Case

        ↓

Policy
REFUND-POLICY-1.2

        ↓

Authority Rule
Support Agent
Maximum = £500

        ↓

Risk Assessment
HIGH

        ↓

Decision
BLOCK

        ↓

Explanation
Authority limit exceeded

        ↓

Audit Event
Decision created

This entire chain should remain traceable through the database.

## 31. Future Data Extensions

The model is intentionally extensible.

Future versions could introduce:

Evidence Source
Policy Rule
Policy Evaluation
Agent Capability
Authority Delegation
Risk Factor
Execution Attempt
Execution Result
Model Version
Prompt Version
Human Approval
Compliance Case
Incident

These should only be introduced when justified by actual product requirements.

## 32. Data Model Definition of Done

The data model is considered complete when:

Core VERA entities are defined.
Relationships between entities are defined.
Primary identifiers are defined.
Foreign-key relationships are defined.
Evidence provenance is represented.
Policy versions are represented.
Authority rules are represented.
Risk assessments are represented.
Decisions are represented.
Human review is represented.
Audit events are represented.
Evaluation scenarios are represented.
Monetary values use appropriate decimal representation.
Timestamps are defined consistently.
Synthetic-data boundaries are documented.
Reproducibility requirements are documented.
Future extensions are separated from MVP scope.

## 33. Final Data Model Principle

The VERA data model is designed around one central idea:

A financial AI decision should not exist as an unexplained final answer. It should exist as a traceable chain of proposal, evidence, policy, authority, risk, decision and audit.

Therefore:

AI Proposal
     ↓
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
     ↓
Explanation
     ↓
Audit

This structure provides the data foundation required for VERA's API, control engines, database implementation, evaluation framework and user interface.