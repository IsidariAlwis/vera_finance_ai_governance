# VERA API Specification

**Project:** VERA — Verifiable Execution & Risk Authority  
**Document:** API Specification  
**Version:** 1.0  
**Status:** Finalized


## 1. Purpose

The VERA API defines how external clients, AI agents, and future application components communicate with the VERA decision-control layer.

The API accepts a proposed financial action and the information required to evaluate that action.

VERA then evaluates the proposal against evidence, policy, authority and risk controls before producing one of three outcomes:

- APPROVE
- HUMAN_REVIEW
- BLOCK

The prototype does not execute real financial transactions. Its purpose is to demonstrate how an AI-generated financial action could be evaluated before execution.


## 2. High-Level Flow

The API follows this conceptual flow:

AI Agent
→ Proposed Action
→ VERA API
→ Evidence Verification
→ Policy Verification
→ Authority Verification
→ Risk Assessment
→ Decision Engine
→ Decision
→ Audit Record

The API therefore provides a controlled boundary between AI-generated intent and financial execution.


## 3. Design Principles

### 3.1 Separation of Intelligence and Authority

An AI system may recommend an action without automatically having permission to execute it.

VERA evaluates the proposed action independently of the AI's recommendation.

### 3.2 Traceability

Every evaluation should be traceable through a unique request, action and decision identifier.

### 3.3 Explainability

The API should return sufficient information to understand the main factors behind a decision.

### 3.4 Deterministic Controls

Core policy and authority decisions should be based on explicit rules rather than relying entirely on an LLM's judgement.

### 3.5 Validation First

Requests must be validated before entering the decision process.

### 3.6 Execution Separation

The prototype evaluates actions but does not directly execute real financial transactions.



## 4. Base URL

For local development:

http://localhost:8000/api/v1

# 5. API Versioning

The API uses URL-based versioning.

Example:

/api/v1

Breaking changes in a future version may be introduced through:

/api/v2

The purpose of versioning is to prevent changes to the API contract from unexpectedly breaking existing clients.

# 6. Content Type

Requests and responses use JSON.

Content-Type: application/json

# 7. Request Identification

Every evaluation request should receive a unique request identifier.

Example:

req-8f3d2a

The identifier is used to correlate API activity, decisions and audit records.

Identifiers should not contain sensitive customer information.

# 8. Core Evaluation Endpoint
POST /actions/evaluate

This is the primary VERA API endpoint.

It accepts a proposed financial action and evaluates it through the VERA control framework.

Purpose

The endpoint receives:

proposed action
requesting AI agent
supporting evidence
relevant context

The endpoint returns:

action identifier
decision identifier
evidence result
policy result
authority result
risk result
final decision
explanation
system and control versions

## 8.1 Example Request

{
  "action": {
    "action_type": "REFUND",
    "amount": 250.00,
    "currency": "GBP",
    "customer_ref": "C-1024",
    "transaction_ref": "TX-80021",
    "reason": "Duplicate payment reported by customer"
  },

  "agent": {
    "agent_id": "support-ai-01",
    "agent_type": "LLM_AGENT",
    "actor_role": "SUPPORT_AGENT"
  },

  "evidence": [
    {
      "evidence_type": "TRANSACTION_RECORD",
      "source": "synthetic_transaction_system",
      "source_reference": "TX-80021",
      "content_summary": "Transaction record confirms duplicate payment.",
      "confidence": 0.98
    },

    {
      "evidence_type": "CUSTOMER_CASE",
      "source": "synthetic_case_system",
      "source_reference": "CASE-441",
      "content_summary": "Customer reported duplicate payment.",
      "confidence": 0.94
    }
  ]
}

# 9. Evaluation Response

A successful evaluation should return a structured decision.

Example:

{
  "success": true,
  "data": {
    "action_id": "ACT-10042",
    "decision_id": "DEC-10042",
    "decision": "APPROVE",
    "controls": {
      "evidence": {
        "result": "PASS",
        "reason": "Required supporting evidence was found and verified."
      },
      "policy": {
        "result": "PASS",
        "policy_id": "REFUND-POLICY",
        "policy_version": "1.2"
      },
      "authority": {
        "result": "PASS",
        "maximum_authorised_amount": 500.00
      },
      "risk": {
        "result": "LOW",
        "score": 18
      }
    },
    "explanation": {
      "summary": "The proposed refund is supported by sufficient evidence, complies with applicable policy and is within the requesting agent's authority.",
      "recommended_next_step": "Proceed according to the approved workflow."
    },
    "versions": {
      "decision_engine": "1.0",
      "risk_model": "1.0",
      "system": "1.0.0"
    }
  },
  "request_id": "req-8f3d2a"
}

# 10. Decision Outcomes

VERA produces one of three primary outcomes.

APPROVE

The proposed action has satisfied the required controls and is eligible to proceed through the appropriate downstream workflow.

HUMAN_REVIEW

The action cannot be automatically approved and requires human assessment.

BLOCK

The action has failed a mandatory control or exceeded an unacceptable risk or authority boundary.

These outcomes represent VERA's decision and do not represent actual execution of a financial transaction.

# 11. Evidence Evaluation

Evidence is used to determine whether the proposed action is sufficiently supported.

Evidence may include:

transaction records
customer cases
account information
policy documents
system records
other approved sources

Each evidence item should contain enough information to identify its source.

The prototype may also assign a confidence value to evidence where appropriate.

Evidence quality must not be determined solely from an LLM response.

# 12. Policy Evaluation

The policy layer determines whether the proposed action is consistent with the applicable business rule or policy.

A policy evaluation should identify:

policy identifier
policy version
evaluation result
reason for failure when applicable

Example:

{
  "result": "PASS",
  "policy_id": "REFUND-POLICY",
  "policy_version": "1.2"
}

# 13. Authority Evaluation

The authority layer determines whether the requesting agent is permitted to propose or execute the relevant type of action within the defined limits.

Authority may depend on:

agent identity
agent role
action type
monetary threshold
account or customer context
additional approval requirements

The central principle is:

Capability does not equal authority.

An AI agent may be technically capable of recommending an action while still being outside the authority boundary required to execute that action.

# 14. Risk Evaluation

The risk layer produces a risk assessment for the proposed action.

The prototype may classify risk as:

LOW
MEDIUM
HIGH

A numerical risk score may also be used.

Example:

Risk score: 18
Risk level: LOW

Risk scoring is a prototype mechanism and must not be presented as a production financial risk model.

# 15. Human Review Endpoint

POST /reviews

Creates a human review case for an action requiring additional assessment.

Example request:

{
  "action_id": "ACT-10043",
  "decision_id": "DEC-10043",
  "reviewer_role": "RISK_ANALYST"
}

Example response:

{
  "success": true,
  "data": {
    "review_id": "REV-20001",
    "action_id": "ACT-10043",
    "status": "PENDING"
  },
  "request_id": "req-cc18a2"
}

# 16. Complete Human Review

POST /reviews/{review_id}/complete

Completes an existing human review.

Example request:

{
  "reviewer_id": "human-reviewer-01",
  "reviewer_decision": "APPROVE",
  "review_comment": "Supporting documentation was manually verified."
}

Example response:

{
  "success": true,
  "data": {
    "review_id": "REV-20001",
    "status": "COMPLETED",
    "reviewer_decision": "APPROVE"
  },
  "request_id": "req-77a22f"
}

# 17. Retrieve an Action
GET /actions/{action_id}

Retrieves information about an evaluated action.

Example:

GET /api/v1/actions/ACT-10042

Example response:

{
  "success": true,
  "data": {
    "action_id": "ACT-10042",
    "action_type": "REFUND",
    "amount": 250.00,
    "currency": "GBP",
    "status": "APPROVED",
    "requesting_agent": "support-ai-01",
    "created_at": "2026-09-10T10:30:00Z"
  },
  "request_id": "req-72c91a"
}

# 18. Retrieve a Decision
GET /actions/{action_id}/decision

Retrieves the decision associated with an action.

Example:

GET /api/v1/actions/ACT-10042/decision

Example response:

{
  "success": true,
  "data": {
    "decision_id": "DEC-10042",
    "action_id": "ACT-10042",
    "decision": "APPROVE",
    "decision_reason": "All mandatory controls passed.",
    "decision_engine_version": "1.0"
  },
  "request_id": "req-9c22d1"
}

# 19. Retrieve Audit History

GET /actions/{action_id}/audit

Retrieves the audit events associated with an action.

Example:

GET /api/v1/actions/ACT-10042/audit

Example response:

{
  "success": true,
  "data": {
    "action_id": "ACT-10042",
    "events": [
      {
        "event_type": "ACTION_RECEIVED",
        "timestamp": "2026-09-10T10:30:00Z"
      },
      {
        "event_type": "EVIDENCE_EVALUATED",
        "timestamp": "2026-09-10T10:30:01Z"
      },
      {
        "event_type": "POLICY_EVALUATED",
        "timestamp": "2026-09-10T10:30:01Z"
      },
      {
        "event_type": "AUTHORITY_EVALUATED",
        "timestamp": "2026-09-10T10:30:01Z"
      },
      {
        "event_type": "RISK_EVALUATED",
        "timestamp": "2026-09-10T10:30:02Z"
      },
      {
        "event_type": "DECISION_CREATED",
        "timestamp": "2026-09-10T10:30:02Z"
      }
    ]
  },
  "request_id": "req-a82271"
}

# 20. Policy Endpoint

GET /policies

Returns the policies available to the prototype.

Example response:

{
  "success": true,
  "data": {
    "policies": [
      {
        "policy_id": "REFUND-POLICY",
        "version": "1.2",
        "action_type": "REFUND",
        "status": "ACTIVE"
      }
    ]
  },
  "request_id": "req-19a821"
}

# 21. Authority Rules Endpoint

GET /authority-rules

Returns the authority rules configured within the prototype.

The endpoint is intended for controlled development and demonstration purposes.

Production systems would require appropriate access restrictions.

# 22. Evaluation Scenarios

GET /evaluation/scenarios

Returns predefined evaluation scenarios used to test VERA.

Example:

{
  "success": true,
  "data": {
    "scenarios": [
      {
        "scenario_id": "SC-01",
        "name": "Valid Low-Value Refund"
      },
      {
        "scenario_id": "SC-02",
        "name": "Insufficient Evidence"
      },
      {
        "scenario_id": "SC-03",
        "name": "Policy Violation"
      },
      {
        "scenario_id": "SC-04",
        "name": "Authority Limit Violation"
      },
      {
        "scenario_id": "SC-05",
        "name": "High-Risk Action"
      }
    ]
  },
  "request_id": "req-92a77c"
}

# 23. Run Evaluation Scenario

POST /evaluation/scenarios/run

Runs a predefined scenario against the VERA decision engine.

Example request:

{
  "scenario_id": "SC-04"
}

Example response:

{
  "success": true,
  "data": {
    "scenario_id": "SC-04",
    "expected_decision": "BLOCK",
    "actual_decision": "BLOCK",
    "passed": true
  },
  "request_id": "req-1182aa"
}

This endpoint will later support systematic evaluation of VERA's behaviour.

# 24. Health Endpoint

GET /health

Provides a basic service health check.

Example response:

{
  "status": "healthy",
  "service": "VERA",
  "version": "1.0.0"
}

The health endpoint must not expose credentials, secrets or sensitive system information.

# 25. Validation

All incoming requests must be validated before evaluation.

Required fields for the core action request include:

action.action_type
action.amount
action.currency
agent.agent_id
agent.actor_role

Additional validation should include:

amount >= 0

The currency should use a supported three-letter currency code.

The action type must belong to the supported action set.

The requesting agent must exist within the prototype's configured agent registry.

# 26. Supported Action Types

The initial prototype may support:

REFUND
PAYMENT_REVERSAL
TRANSFER
FEE_ADJUSTMENT
ACCOUNT_CHANGE

Additional action types may be introduced in future versions.

The supported action set should remain explicitly controlled rather than accepting arbitrary actions.

# 27. Validation Error

Example:

{
  "success": false,
  "error": {
    "code": "VALIDATION_ERROR",
    "message": "Invalid action request.",
    "details": [
      {
        "field": "action.amount",
        "reason": "Amount must be greater than or equal to zero."
      }
    ]
  },
  "request_id": "req-4c812a"
}

# 28. HTTP Status Codes

The API should use conventional HTTP status codes.

200  Successful request
201  Resource created
400  Invalid request
401  Authentication required
403  Access denied
404  Resource not found
409  Conflicting request or state
422  Validation failure
429  Rate limit exceeded
500  Internal server error

# 29. Error Codes

The prototype should use machine-readable error codes.

Examples:

VALIDATION_ERROR
ACTION_NOT_FOUND
AGENT_NOT_FOUND
POLICY_NOT_FOUND
AUTHORITY_RULE_NOT_FOUND
INVALID_ACTION_TYPE
INVALID_AMOUNT
EVIDENCE_INVALID
REVIEW_NOT_FOUND
DUPLICATE_REQUEST
INTERNAL_ERROR

# 30. Idempotency

The evaluation endpoint should support an idempotency mechanism.

A client may provide:

Idempotency-Key: unique-client-key

This helps prevent accidental duplicate processing when a client retries the same request.

The prototype may store the idempotency key alongside the associated request.

## 31. Authentication

Authentication may initially be disabled during local development.

The API is nevertheless designed with production authentication in mind.

Possible future approaches include:

OAuth 2.0
JWT
API keys
Service-to-service authentication

Production credentials must never be stored directly in source code.

## 32. Authorisation

Authentication and authorisation are separate concepts.

Authentication determines:

Who is requesting access?

Authorisation determines:

What is that requester permitted to do?

VERA should therefore avoid treating authentication as automatic permission to perform every operation.

## 33. AI and LLM Boundary

The API deliberately separates AI-generated proposals from VERA's control decisions.

An AI agent may provide:

proposed action
reason
supporting context
evidence references

However, the AI must not independently determine:

final approval
policy compliance
authority

Those decisions belong to VERA's control layer.

## 34. LLM Integration

A future LLM component may assist with:

extracting structured information from unstructured evidence
summarising evidence
identifying potentially relevant information
generating natural-language explanations

The conceptual flow is:

LLM Output
    ↓
Structured Validation
    ↓
Deterministic Controls
    ↓
Decision Engine
    ↓
Decision

The LLM must not bypass the control layer.

## 35. Decision Contract

The central VERA API contract can be expressed as:

Proposed Action
       +
Evidence
       +
Policy
       +
Authority
       +
Risk
       ↓
VERA Decision
       ↓
APPROVE / HUMAN_REVIEW / BLOCK

The API should provide enough information to understand how the final decision was reached.

## 36. Audit Correlation

The following identifiers should be correlated throughout the lifecycle of an evaluation:

request_id
action_id
decision_id
review_id
audit_id

This allows the system to reconstruct the sequence of events associated with a proposed action.

## 37. Security Requirements

The prototype should implement basic secure-development practices.

These include:

input validation
strict request schemas
controlled action types
no secrets in source code
no credentials in API responses
minimal use of sensitive information
safe error messages
structured logging
request correlation
authentication-ready design
authorisation-aware design

## 38. Logging

Logs should provide useful operational information without unnecessarily exposing sensitive information.

Useful fields include:

request_id
action_id
endpoint
timestamp
processing_time
decision
system_version

Customer information and other sensitive data should not be unnecessarily written to logs.

## 39. Performance Target

For the prototype, the initial target is:

Typical evaluation response: under 2 seconds

This is an engineering target for the prototype and is not a production service-level agreement.

Performance can later be improved through:

database indexing
caching
asynchronous processing
model optimisation
queue-based processing

## 40. Observability

The completed prototype should make it possible to measure:

evaluation count
evaluation latency
decision distribution
control failures
human-review frequency
API error rate
scenario evaluation success rate

These measurements can later support the VERA monitoring and product dashboard.

## 41. API and Data Model Relationship

The API maps directly to VERA's data model.

The main evaluation flow is:

POST /actions/evaluate
        ↓
Action
        ↓
Evidence
        ↓
Control Evaluations
        ↓
Risk Assessment
        ↓
Decision
        ↓
Decision Explanation
        ↓
Audit Event

Human review follows:

POST /reviews
        ↓
Review
        ↓
Decision Update
        ↓
Audit Event

Scenario evaluation follows:

Evaluation Scenario
        ↓
API Evaluation
        ↓
Expected Decision
        ↓
Actual Decision
        ↓
Evaluation Result

## 42. Prototype Endpoint Set

The initial API surface consists of:

POST /actions/evaluate
GET  /actions/{action_id}
GET  /actions/{action_id}/decision
GET  /actions/{action_id}/audit

POST /reviews
POST /reviews/{review_id}/complete

GET  /policies
GET  /authority-rules

GET  /evaluation/scenarios
POST /evaluation/scenarios/run

GET  /health

Additional endpoints should only be introduced when they support a defined product requirement.

## 43. API Definition of Done

The API specification is considered complete when:

the core evaluation endpoint is defined
request structure is defined
response structure is defined
decision outcomes are defined
evidence handling is defined
policy evaluation is represented
authority evaluation is represented
risk evaluation is represented
human review is represented
audit retrieval is represented
evaluation scenarios are represented
validation rules are defined
error handling is defined
versioning is defined
authentication assumptions are documented
authorisation principles are documented
idempotency is addressed
AI and LLM boundaries are defined
security requirements are documented
observability requirements are documented
API and data-model relationships are defined

## 44. Final Principle

The VERA API exists to enforce a fundamental separation:

AI intelligence
      ≠
Execution authority

An AI system may propose an action.

VERA independently determines whether that action is sufficiently:

Evidence-supported
Policy-compliant
Authorised
Risk-appropriate

The resulting decision is:

APPROVE
HUMAN_REVIEW
BLOCK

The API therefore represents the controlled boundary between AI-generated intent and governed financial action.

Document Status

Status: Finalized for prototype implementation.

This specification defines the intended API contract. Implementation details may evolve during development where testing reveals technical constraints or better design decisions. Any significant change should be documented rather than silently altering the product requirements.