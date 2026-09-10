VERA — Product Requirements Document

Product: VERA — Verifiable Execution & Risk Authority
Repository: vera_finance_ai_governance
Document: Product Requirements Document
Version: 1.0
Status: MVP Definition
Product Type: Research-driven fintech AI governance prototype

1. Product Definition

VERA (Verifiable Execution & Risk Authority) is a research-driven prototype exploring an independent decision-control layer between AI-generated financial actions and potential execution.

The system evaluates whether a proposed financial action should be:

APPROVED
SENT FOR HUMAN REVIEW
BLOCKED

before execution can occur.

VERA evaluates four primary control dimensions:

Evidence
Policy
Authority
Risk

The purpose of VERA is not to make AI independently responsible for financial execution.

Instead, VERA explores how an explicit, evidence-based and auditable control boundary can be placed between AI capability and consequential financial action.

Core Principle

AI capability does not automatically constitute execution authority.

2. Product Vision

As AI systems become increasingly capable of recommending and potentially initiating consequential financial actions, financial organisations require mechanisms that can determine whether an AI-generated action is sufficiently supported, permitted, authorised and safe to execute.

VERA aims to demonstrate a practical control architecture for this problem.

The long-term vision is to create a reusable decision-control layer capable of evaluating AI-generated actions across high-risk financial workflows while maintaining:

evidence traceability,
policy compliance,
authority boundaries,
risk controls,
human oversight,
explainability,
and complete auditability.

3. Problem Statement

AI systems can generate financially consequential recommendations or actions based on information that may be incomplete, outdated, contradictory or incorrectly interpreted.

Traditional software systems generally operate according to explicitly programmed rules and permissions.

AI agents, however, can dynamically generate recommendations and actions.

This creates a control problem:

How can an organisation determine whether an AI-generated financial action is sufficiently evidenced, policy-compliant, authorised and low enough risk to execute?

A capable AI system may be technically able to perform an action without being authorised to perform that action.

Therefore, VERA separates:

AI capability

from

execution authority.

The system introduces an explicit verification and decision layer before a proposed financial action can proceed.

4. Product Hypothesis

If AI-generated financial actions are evaluated through independent evidence, policy, authority and risk controls before execution, then organisations can reduce the probability of inappropriate automated decisions while improving explainability, consistency and auditability.

The prototype will test this hypothesis using controlled synthetic financial scenarios.

5. Product Goals

VERA's MVP will aim to:

G1 — Verify Evidence

Determine whether a proposed financial action is supported by sufficient and valid evidence.

G2 — Verify Policy

Determine whether the proposed action complies with defined financial policies and thresholds.

G3 — Verify Authority

Determine whether the AI agent, user or actor associated with the action is authorised to perform the proposed action.

G4 — Assess Risk

Evaluate the potential risk associated with the proposed action.

G5 — Produce a Deterministic Decision

Generate one of three outcomes:

APPROVE
HUMAN REVIEW
BLOCK
G6 — Explain the Decision

Provide an understandable explanation of why the decision was reached.

G7 — Preserve an Audit Trail

Record the decision inputs, results, reasoning and relevant system metadata.

G8 — Demonstrate the Concept Practically

Implement the control architecture as a functioning software prototype rather than presenting only a theoretical model.

6. Product Non-Goals

The MVP will not:

move real money,
connect to production banking infrastructure,
execute real customer transactions,
access real customer financial data,
provide financial advice to real customers,
provide regulatory certification,
claim compliance with every financial regulation,
replace human compliance or risk teams,
provide a production-ready banking security architecture,
autonomously control real financial accounts.

All financial actions and customer information used in the prototype will be synthetic or simulated.

7. Target Users
Primary User — Financial Operations / Risk Analyst

Uses VERA to review proposed AI-generated financial actions and understand why actions were approved, blocked or escalated.

Secondary User — Product / Operations Manager

Uses VERA to understand operational risk, decision patterns and control effectiveness.

Secondary User — Compliance / Risk Team

Uses VERA's decision explanations and audit records to investigate potentially problematic AI-generated actions.

Technical User — AI / Engineering Team

Uses VERA as a control layer between AI agents and downstream financial systems.

8. Core User Journey

The central VERA workflow is:

AI Agent
    ↓
Proposed Financial Action
    ↓
Evidence Verification
    ↓
Policy Verification
    ↓
Authority Verification
    ↓
Risk Assessment
    ↓
Decision Engine
    ↓
APPROVE / HUMAN REVIEW / BLOCK
    ↓
Audit Record

Each proposed action must pass through the control pipeline before a final decision is produced.

9. Core Product Components

The MVP consists of the following components:

AI Action Intake
Evidence Verification Engine
Policy Verification Engine
Authority Verification Engine
Risk Assessment Engine
Decision Engine
Human Review Interface
Explainability Layer
Audit Record System
Scenario Engine
Evaluation Framework
Web Interface
API Layer
Database

10. AI Action Intake

The AI Action Intake component receives a proposed financial action.

A proposed action should contain information such as:

action ID,
action type,
amount,
currency,
account or customer reference,
requesting agent,
actor role,
supporting evidence,
requested timestamp,
contextual information,
reason for the proposed action.

Example:

{
  "action_id": "ACT-001",
  "action_type": "REFUND",
  "amount": 250.00,
  "currency": "GBP",
  "agent_id": "AGENT-01",
  "actor_role": "CUSTOMER_SUPPORT_AI",
  "reason": "Customer reported duplicate charge",
  "evidence": [
    "transaction_record",
    "customer_case"
  ]
}

The intake layer must validate the structure of the request before it enters the control pipeline.

11. Evidence Verification

The Evidence Verification Engine determines whether sufficient evidence exists to support the proposed action.

Evidence may include:

transaction records,
customer cases,
system events,
previous decisions,
policy documents,
supporting documents,
structured system information.

Evidence statuses:

PASS

Evidence sufficiently supports the proposed action.

INSUFFICIENT

Evidence exists but does not sufficiently support the action.

INVALID

Evidence is invalid or cannot be trusted.

CONTRADICTORY

Available evidence contains conflicting information.

MISSING

Required evidence is absent.

The evidence result must be recorded and made available to the Decision Engine.

12. Policy Verification

The Policy Verification Engine evaluates the proposed action against defined business policies.

Example policies may include:

refund limits,
transaction thresholds,
approval requirements,
restricted transaction categories,
escalation requirements,
geographical restrictions,
frequency limits.

Policy outcomes:

PASS

The action satisfies applicable policies.

FAIL

The action violates one or more mandatory policies.

REVIEW_REQUIRED

The action falls into a policy condition requiring human assessment.

The policy version used for evaluation must be recorded in the audit trail.

13. Authority Verification

Authority Verification determines whether the actor associated with the action is authorised to perform it.

This component must explicitly distinguish between:

Can technically perform the action

and

Is authorised to perform the action.

Authority may depend on:

actor role,
agent identity,
action type,
monetary amount,
organisational permissions,
escalation requirements.

Example:

AI Agent:
Customer Support Agent

Requested Action:
£5,000 Refund

Technical Capability:
YES

Authorised Limit:
£500

Authority Result:
FAIL

The system should therefore prevent technical capability from being treated as execution authority.

14. Risk Assessment

The Risk Assessment Engine determines the risk level associated with the proposed action.

Risk levels:

LOW
MEDIUM
HIGH
CRITICAL

Risk factors may include:

monetary amount,
transaction type,
evidence quality,
policy violations,
authority level,
unusual behaviour,
conflicting evidence,
customer impact,
potential financial loss.

The MVP will use an explainable rule-based risk model.

The risk assessment should produce both:

risk level,
risk factors contributing to the result.

15. Decision Engine

The Decision Engine combines the results of:

Evidence Verification
Policy Verification
Authority Verification
Risk Assessment

to produce the final VERA decision.

Possible decisions:

APPROVE
HUMAN REVIEW
BLOCK

The Decision Engine should be deterministic for the same inputs and policy configuration.

16. Decision Priority

Decision priority must follow a safety-first hierarchy.

Rule 1 — Critical Blocking Condition

If a critical blocking condition exists:

BLOCK
Rule 2 — Mandatory Human Review

If the action does not meet blocking conditions but requires human assessment:

HUMAN REVIEW
Rule 3 — Valid Approval

If:

evidence passes,
policy passes,
authority passes,
risk is acceptable,

then:

APPROVE
Rule 4 — Unresolved Condition

If the system cannot confidently establish that the action is safe and authorised:

HUMAN REVIEW

The system should favour controlled uncertainty over unsafe automation.

17. Human Review

Actions requiring human intervention must enter a Human Review workflow.

The reviewer should be able to see:

proposed action,
evidence results,
policy results,
authority results,
risk assessment,
VERA explanation,
recommended decision.

The reviewer should be able to select:

APPROVE
REJECT

and provide an optional review comment.

The human decision must be recorded in the audit trail.

18. Explainability

Every VERA decision must include a human-readable explanation.

Example:

Decision: HUMAN REVIEW

Reason:
The proposed refund is supported by transaction evidence,
but the requested amount exceeds the actor's authorised refund
limit. Human approval is therefore required.

The explanation should identify:

decision,
important control results,
blocking or review conditions,
relevant risk factors,
policy references where applicable.

19. Audit Record

Every evaluated action must generate an audit record.

The audit record should contain, where applicable:

action_id
timestamp
action_type
amount
currency
agent_id
actor_role
evidence_result
policy_result
authority_result
risk_result
final_decision
decision_reason
reviewer_id
reviewer_decision
policy_version
system_version

The audit record must allow a reviewer to reconstruct why VERA reached its decision.

Audit records must be immutable from the perspective of normal users within the MVP.

20. Scenario Engine

The Scenario Engine will provide controlled synthetic scenarios for testing VERA.

The MVP must include at least the following scenarios:

Scenario 1 — Normal Approval

Valid evidence, valid policy, authorised actor and acceptable risk.

Expected:

APPROVE
Scenario 2 — Missing Evidence

Required evidence is unavailable.

Expected:

HUMAN REVIEW
Scenario 3 — Policy Violation

The action violates a mandatory policy.

Expected:

BLOCK
Scenario 4 — Authority Violation

The actor is not authorised for the requested action.

Expected:

BLOCK
Scenario 5 — High-Risk Action

The action presents significant financial or operational risk.

Expected:

HUMAN REVIEW
Scenario 6 — Contradictory Evidence

Supporting information contains conflicting evidence.

Expected:

HUMAN REVIEW
Scenario 7 — Multiple Control Failures

Multiple control dimensions fail simultaneously.

Expected:

BLOCK
Scenario 8 — Adversarial Proposal

The AI proposes an action that appears reasonable but attempts to bypass or exceed defined controls.

Expected:

BLOCK

21. Functional Requirements

FR-01 — Action Submission

The system shall allow a proposed financial action to be submitted for evaluation.

FR-02 — Input Validation

The system shall validate required action fields before evaluation.

FR-03 — Evidence Evaluation

The system shall evaluate evidence associated with a proposed action.

FR-04 — Policy Evaluation

The system shall evaluate the action against defined policies.

FR-05 — Authority Evaluation

The system shall determine whether the requesting actor is authorised.

FR-06 — Risk Evaluation

The system shall calculate a risk level and relevant risk factors.

FR-07 — Decision Generation

The system shall generate APPROVE, HUMAN REVIEW or BLOCK.

FR-08 — Decision Explanation

The system shall provide a human-readable explanation.

FR-09 — Human Review

The system shall support human review of escalated actions.

FR-10 — Audit Logging

The system shall persist an audit record for every evaluated action.

FR-11 — Scenario Testing

The system shall support predefined synthetic test scenarios.

FR-12 — API Access

The system shall expose core VERA functionality through a REST API.

FR-13 — Web Interface

The system shall provide a user interface for submitting actions and reviewing results.

FR-14 — Evaluation

The system shall support systematic evaluation of decision outcomes against expected scenario results.

22. Non-Functional Requirements
NFR-01 — Determinism

The deterministic control layer should produce consistent results for identical inputs.

NFR-02 — Explainability

Decisions should be understandable to non-technical users.

NFR-03 — Auditability

Every decision should be traceable to its inputs and control results.

NFR-04 — Security

The architecture should follow least-privilege principles and avoid unnecessary access to sensitive information.

NFR-05 — Reliability

A failure in an individual control should not silently result in automatic approval.

NFR-06 — Maintainability

Control rules should be modular and independently testable.

NFR-07 — Performance

The MVP should return decisions quickly enough to support interactive demonstration.

NFR-08 — Extensibility

The architecture should allow additional action types and control modules to be introduced later.

23. User Stories

US-01 — Submit AI Action

As an AI system, I want to submit a proposed financial action to VERA so that the action can be evaluated before execution.

US-02 — Verify Evidence

As a risk analyst, I want VERA to verify supporting evidence so that unsupported actions are not automatically approved.

US-03 — Verify Policy

As an operations manager, I want VERA to evaluate policies so that financial actions comply with defined business rules.

US-04 — Verify Authority

As a compliance user, I want VERA to distinguish technical capability from authority so that actors cannot execute actions beyond their permissions.

US-05 — Assess Risk

As a risk analyst, I want to understand the risk level of an action before it is approved.

US-06 — Explain Decision

As a reviewer, I want VERA to explain why a decision was produced so that I can understand and challenge the outcome.

US-07 — Review Escalated Action

As an authorised reviewer, I want to review actions escalated by VERA so that uncertain or high-risk cases can receive human judgement.

US-08 — Audit Decision

As a compliance user, I want to inspect historical decision records so that the organisation can understand what happened and why.

24. Acceptance Criteria

AC-01

Given a valid action with sufficient evidence, valid policy, valid authority and acceptable risk:

VERA → APPROVE
AC-02

Given an action with missing mandatory evidence:

VERA → HUMAN REVIEW
AC-03

Given an action violating a mandatory policy:

VERA → BLOCK
AC-04

Given an action requested by an unauthorised actor:

VERA → BLOCK
AC-05

Given an action classified as high risk but not automatically prohibited:

VERA → HUMAN REVIEW
AC-06

Given contradictory evidence:

VERA → HUMAN REVIEW
AC-07

Given a critical blocking condition:

VERA → BLOCK
AC-08

Every decision must produce an audit record.

AC-09

Every decision must provide an explanation.

AC-10

The same input and control configuration must produce the same deterministic control result.

25. MVP Scope

The MVP will include:

Core Control Layer
Evidence Verification
Policy Verification
Authority Verification
Risk Assessment
Decision Engine
Product Layer
Action submission
Decision display
Human review
Explanation
Audit history
Technical Layer
REST API
Database persistence
Synthetic scenario dataset
Automated tests
Evaluation framework
Web interface
Technical documentation

26. Initial Action Types

The MVP will focus on two financial action categories:

1. Refund

Examples:

customer refund,
duplicate transaction refund,
service-related refund.
2. Payment / Transfer

Examples:

payment,
account transfer,
scheduled financial movement.

These action types provide sufficient variation to demonstrate evidence, policy, authority and risk controls without attempting to model the entire financial ecosystem.

27. Decision Matrix

Evidence	Policy	Authority	Risk	Decision
PASS	PASS	PASS	LOW	APPROVE
PASS	PASS	PASS	MEDIUM	APPROVE / REVIEW depending on policy
PASS	PASS	PASS	HIGH	HUMAN REVIEW
PASS	PASS	PASS	CRITICAL	BLOCK
MISSING	PASS	PASS	LOW	HUMAN REVIEW
INSUFFICIENT	PASS	PASS	LOW	HUMAN REVIEW
INVALID	PASS	PASS	Any	HUMAN REVIEW / BLOCK
CONTRADICTORY	PASS	PASS	Any	HUMAN REVIEW
PASS	FAIL	PASS	Any	BLOCK
PASS	REVIEW_REQUIRED	PASS	Any	HUMAN REVIEW
PASS	PASS	FAIL	Any	BLOCK
PASS	PASS	PASS	CRITICAL	BLOCK

The exact implementation logic must be deterministic and documented.

28. Product Metrics

The MVP evaluation framework should measure:

Decision Accuracy

Percentage of scenarios for which VERA produces the expected decision.

False Approval Rate

Percentage of unsafe or prohibited scenarios incorrectly approved.

Critical Failure Capture

Percentage of critical scenarios correctly blocked or escalated.

Human Review Appropriateness

Percentage of uncertain/high-risk scenarios correctly escalated.

Explanation Completeness

Percentage of decisions containing sufficient explanation information.

Audit Completeness

Percentage of decisions with all required audit fields.

Decision Consistency

Whether identical inputs produce identical outcomes under the same policy configuration.

29. Product Risks

Risk 1 — False Approval

VERA could incorrectly approve an unsafe action.

Mitigation: conservative decision rules and extensive scenario testing.

Risk 2 — Excessive Human Review

VERA could escalate too many actions.

Mitigation: evaluate review rates and refine risk/policy thresholds.

Risk 3 — Poor Evidence Quality

Synthetic evidence may not accurately represent production environments.

Mitigation: clearly document prototype limitations and use realistic scenario structures.

Risk 4 — Overconfidence in AI

Users may assume VERA guarantees that an action is safe.

Mitigation: clearly communicate that VERA is a research prototype and not a production safety guarantee.

Risk 5 — Model Manipulation

An AI agent could attempt to generate proposals designed to bypass controls.

Mitigation: keep critical control decisions deterministic and independent from the AI recommendation itself.

Risk 6 — Incomplete Regulatory Coverage

The MVP cannot represent every applicable financial regulation.

Mitigation: treat policies as configurable prototype rules rather than claiming regulatory certification.

30. Key Product Principles

Principle 1 — Capability ≠ Authority

The ability to technically perform an action does not establish permission to perform it.

Principle 2 — Evidence Before Execution

Consequential actions should have sufficient supporting evidence.

Principle 3 — Deterministic Controls for Critical Decisions

Critical approval and blocking logic should not depend entirely on probabilistic AI output.

Principle 4 — Controlled Uncertainty

When the system cannot establish that an action is safe and authorised, the default should favour review rather than unrestricted execution.

Principle 5 — Explain Every Decision

A decision without an understandable reason is difficult to govern.

Principle 6 — Audit Everything Important

The system must preserve enough information to reconstruct important decisions.

Principle 7 — Human Oversight

Human judgement remains part of the control system for uncertain or high-risk cases.

Principle 8 — Separation of Intelligence and Authority

The AI system can recommend an action without receiving unrestricted authority to execute it.

31. MVP Definition of Done

The VERA MVP is considered complete when:

 An AI-generated financial action can be submitted.
 Evidence can be evaluated.
 Policies can be evaluated.
 Authority can be evaluated.
 Risk can be assessed.
 A deterministic decision can be generated.
 The decision can be APPROVE, HUMAN REVIEW or BLOCK.
 The decision includes an explanation.
 Human review is supported.
 Decisions are persisted in an audit record.
 Synthetic scenarios are available.
 Automated tests cover the control logic.
 Evaluation metrics can be calculated.
 A REST API is available.
 A web interface is available.
 Technical documentation is available.
 The system can be demonstrated end-to-end.
 
32. Future Product Direction

The following capabilities are considered potential future extensions and are not required for the MVP.

V2 — Additional Financial Actions

Expand beyond refunds and transfers into additional financial workflows.

V3 — Advanced Evidence Intelligence

Introduce more sophisticated evidence retrieval, verification and provenance mechanisms.

V4 — Adaptive Risk Intelligence

Explore more advanced risk modelling using historical decision patterns.

V5 — Multi-Agent Governance

Evaluate interactions between multiple AI agents and their respective authority boundaries.

V6 — Policy Management

Introduce configurable policy management and policy versioning interfaces.

V7 — Production Integration

Explore integration with financial systems, identity systems and enterprise audit infrastructure.

These future directions are included to demonstrate product scalability and strategic thinking but will not be implemented unless the MVP is stable.

33. Prototype Boundary

VERA is a research-driven software prototype.

The prototype will use:

synthetic financial actions,
synthetic customer information,
simulated policies,
simulated authority structures,
simulated evidence,
controlled scenarios.

VERA will not:

access real bank accounts,
transfer real funds,
process real customer financial data,
make real financial decisions,
claim regulatory certification,
claim production-level security or reliability.

The purpose of the prototype is to demonstrate and evaluate the architecture and product concept.

34. Product Success

VERA will be considered successful if the prototype demonstrates that:

AI-generated financial actions can be evaluated through an independent control layer.
Evidence, policy, authority and risk can be evaluated as separate control dimensions.
Technical AI capability can be separated from execution authority.
High-risk or unsupported actions can be prevented from automatic approval.
Human review can be introduced when uncertainty exists.
Decisions can be explained.
Decisions can be audited.
The system can be evaluated systematically using controlled scenarios.
The architecture can be extended to additional financial workflows.

35. Final Product Statement

VERA — Verifiable Execution & Risk Authority is a research-driven prototype exploring how financial organisations can place an evidence-based, policy-aware, authority-aware and risk-sensitive control layer between AI-generated financial actions and execution.

VERA does not assume that increasingly capable AI systems should automatically receive increasingly broad execution authority.

Instead, it explores a different model:

AI Intelligence
      ↓
Proposed Action
      ↓
Independent Verification
      ↓
Risk & Authority Controls
      ↓
Decision
      ↓
Human Oversight Where Required
      ↓
Auditable Outcome

The central proposition is:

AI can propose. VERA verifies. Authority determines whether execution is permitted.