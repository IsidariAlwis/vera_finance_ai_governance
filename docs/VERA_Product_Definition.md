# VERA - Product Definition
## 1. Product Vision

VERA (Verifiable Execution & Risk Authority) is a research-driven prototype exploring how financial organisations could introduce an independent decision-control layer between AI-generated recommendations and consequential financial actions.

As AI systems evolve from providing information and recommendations toward taking actions on behalf of users and organisations, the ability of an AI system to propose an action should not automatically imply the authority to execute it. VERA explores a model in which AI-generated financial actions are independently evaluated against supporting evidence, applicable policies, authorised boundaries, and risk conditions before an execution decision is made.

The vision for VERA is to create a transparent, evidence-based control layer that can determine whether a proposed financial action should be:

- APPROVED — the action satisfies the defined control conditions;
- SENT FOR HUMAN REVIEW — the action requires additional judgement or approval; or
- BLOCKED — the action violates defined control conditions or presents unacceptable risk.

Every decision should produce an auditable record explaining what was proposed, what evidence and policies were evaluated, what authority and risk conditions were considered, and why the resulting decision was reached.

VERA is not intended to replace financial institutions' existing risk, compliance, security, or governance systems. Instead, it is a prototype for investigating how an independent verification and decision-control layer could complement AI-driven financial operations.

The long-term vision is to explore a trustworthy control architecture for increasingly autonomous financial AI systems in which intelligence and execution authority are deliberately separated, consequential actions remain bounded by explicit controls, and decisions can be reviewed, explained, and audited.

## 2. Problem Statement

Financial organisations are increasingly exploring AI systems that can move beyond generating information and recommendations toward performing multi-step tasks and supporting consequential financial decisions. As these systems become more autonomous, the distinction between an AI system's ability to propose an action and its authority to execute that action becomes increasingly important.

Recent financial-sector research and regulatory work has identified concerns around the use of agentic AI in financial environments, including authorisation, traceability, fraud and cyber risk, resilience, accountability, interpretability, and the ability to maintain effective human oversight as decision-making becomes faster and more autonomous.

However, identifying these risks does not by itself provide a practical decision-control mechanism for evaluating an individual AI-generated financial action before it is executed.

The problem VERA explores is therefore:

How can a financial organisation independently evaluate an AI-generated financial action against supporting evidence, applicable policies, authorised boundaries, and risk conditions before determining whether that action should be approved, escalated for human review, or blocked?

VERA addresses this problem by proposing an independent control layer between AI-generated action proposals and consequential execution. Rather than treating an AI system's recommendation as sufficient authority to act, VERA evaluates the proposed action through four control dimensions:

Evidence — Is the proposed action supported by sufficient and relevant evidence?
Policy — Does the action comply with the applicable rules, policies, and constraints?
Authority — Is the action permitted within the defined authority and approval boundaries?
Risk — Does the action remain within acceptable risk conditions?

The output of these evaluations is a transparent decision of APPROVE, HUMAN REVIEW, or BLOCK, accompanied by an auditable record of the factors that contributed to the decision.

VERA therefore explores a specific product and governance problem: how an independent, evidence-based control layer could help financial organisations introduce greater accountability and bounded autonomy into AI-driven financial workflows without treating AI-generated recommendations as inherently authorised for execution.

## 3. Target Users


VERA is designed as a conceptual control layer for financial organisations that use, or are considering using, AI systems within workflows involving consequential financial actions.

The primary target users are:

### 3.1 Financial Operations Teams

Operations teams may use VERA to introduce structured verification before AI-generated actions progress toward execution. VERA can provide a consistent mechanism for evaluating whether an action is supported by evidence, permitted by policy, within authorised boundaries, and appropriately risk-bounded.

### 3.2 Risk, Compliance, and Governance Teams

Risk, compliance, and governance stakeholders may use VERA to define control conditions, review exceptions, and inspect the reasoning and evidence associated with AI-generated decisions. The audit record can provide a structured view of how a proposed action was evaluated.

### 3.3 Product and Technology Teams

Product and technology teams may use VERA to design and evaluate AI-enabled financial workflows in which autonomy must remain bounded by explicit controls. The system provides a framework for separating AI capabilities from execution authority.

### 3.4 AI and Engineering Teams

AI and engineering teams may use VERA as an integration point between AI-generated action proposals and downstream financial systems. Instead of allowing an AI component to directly determine whether an action can proceed, the proposed action can be independently evaluated by the control layer.

### 3.5 Control and Audit Stakeholders

Internal control and audit stakeholders may use VERA's decision records to examine what action was proposed, what evidence and policies were considered, what authority and risk conditions applied, and why a particular outcome was produced.

### Primary User and Decision Stakeholder

For the prototype, the primary user is assumed to be a **financial operations or risk-control stakeholder responsible for overseeing AI-enabled workflows**, while the broader stakeholder group includes product, technology, compliance, governance, and audit functions.

VERA is therefore positioned as a **business-to-business control capability**, rather than a consumer-facing financial application.


## 4. Core Use Cases

### 4.1 AI-Generated Refund Decisions

An AI agent may analyse a customer case and propose a refund based on transaction information, customer history, applicable policies, and supporting evidence.

VERA evaluates whether the proposed refund is sufficiently evidenced, permitted by policy, within the agent's authorised limits, and acceptable under the defined risk conditions before determining whether it should proceed, require human review, or be blocked.

### 4.2 AI-Generated Payment and Transfer Actions

An AI agent may propose a payment or transfer on behalf of a customer or financial operation.

VERA evaluates the proposed action before execution by examining the available evidence, applicable transaction policies, authority boundaries, and risk indicators. Higher-value or higher-risk actions can be escalated for human approval rather than being automatically executed.

### 4.3 Evidence-Deficient Decisions

An AI agent may produce a seemingly reasonable financial recommendation while relying on incomplete, outdated, contradictory, or insufficient evidence.

VERA identifies deficiencies in the supporting evidence and prevents the quality of an AI-generated recommendation from being treated as sufficient justification for execution.

Depending on the severity of the deficiency, the action may be escalated for human review or blocked.

### 4.4 Policy-Violating Actions

An AI-generated action may conflict with an applicable financial policy, operational rule, transaction limit, or other defined constraint.

VERA independently evaluates the proposed action against the applicable policy conditions and prevents actions that fall outside permitted rules from being automatically executed.

### 4.5 Authority-Boundary Violations

An AI agent may be technically capable of proposing an action that exceeds the authority assigned to it.

VERA separates capability from execution authority by evaluating whether the proposed action falls within the agent's defined permissions, transaction limits, approval requirements, and operational boundaries.

An action that exceeds the agent's authority can be routed to human review or blocked.

### 4.6 High-Risk Financial Actions

Some actions may satisfy basic evidence and policy requirements while still presenting elevated financial, operational, fraud, security, or customer risk.

VERA evaluates defined risk indicators and thresholds so that actions with elevated risk can receive additional scrutiny rather than being automatically approved solely because other checks have passed.

### 4.7 Human-in-the-Loop Escalation

VERA supports situations in which automated execution is inappropriate but the proposed action may still be legitimate.

Instead of treating every non-approved action as a failure, VERA can route qualifying cases to a human decision-maker with the relevant evidence, policy findings, authority assessment, risk indicators, and decision context available for review.

### 4.8 Auditable Decision Records

Every VERA evaluation should generate a structured record containing the proposed action, relevant evidence, policy checks, authority assessment, risk assessment, resulting decision, and supporting decision metadata.

This allows authorised stakeholders to understand how a decision was reached and provides a basis for subsequent review, analysis, testing, and audit.

### 4.9 Decision Outcomes

Across these use cases, VERA produces one of three primary outcomes:

- **APPROVE** — the proposed action satisfies the defined verification and risk conditions.
- **HUMAN REVIEW** — the action requires additional human judgement, approval, or investigation.
- **BLOCK** — the action fails a critical control condition or exceeds an unacceptable risk or authority boundary.

## 5. How VERA Works

VERA operates as an independent decision-control layer between an AI system that proposes a financial action and the downstream system that could execute that action.

The core workflow is:

AI Agent
→ Proposed Financial Action
→ Evidence Verification
→ Policy Verification
→ Authority Verification
→ Risk Assessment
→ Decision Engine
→ APPROVE / HUMAN REVIEW / BLOCK
→ Audit Record

### 5.1 AI Agent

The AI agent represents an upstream intelligent system capable of analysing information and generating a proposed financial action.

The agent does not directly determine whether its proposed action is authorised for execution.

### 5.2 Proposed Financial Action

The AI agent produces a structured action proposal containing the intended action, relevant entities, transaction details, reasoning or justification, and supporting information.

The proposal becomes the input to VERA's independent verification process.

### 5.3 Evidence Verification

VERA evaluates the evidence supporting the proposed action.

The evidence layer examines factors such as relevance, completeness, consistency, recency, and whether the evidence adequately supports the proposed action.

Insufficient, contradictory, or unreliable evidence can prevent automatic approval.

### 5.4 Policy Verification

VERA evaluates the proposed action against the applicable policies and predefined business rules.

This layer determines whether the action satisfies requirements such as transaction limits, eligibility conditions, approval requirements, and other operational constraints.

### 5.5 Authority Verification

VERA independently determines whether the AI agent is authorised to propose or execute the specific type of action within the defined boundaries.

Authority may depend on factors such as action type, transaction value, account or workflow context, role, permission level, and approval thresholds.

This layer deliberately separates the AI system's capability from its authority to execute.

### 5.6 Risk Assessment

VERA evaluates risk indicators associated with the proposed action.

The risk assessment may consider factors such as transaction value, unusual behaviour, evidence quality, policy exceptions, authority violations, fraud indicators, and other defined risk signals.

The resulting risk assessment contributes to the final decision.

### 5.7 Decision Engine

The Decision Engine combines the outputs of the verification layers and applies predefined decision logic.

The resulting decision is one of three primary outcomes:

- **APPROVE**
- **HUMAN REVIEW**
- **BLOCK**

The decision should be deterministic and explainable based on the defined control conditions rather than relying solely on an AI-generated conclusion.

### 5.8 Audit Record

After each evaluation, VERA generates a structured audit record.

The record captures the proposed action, relevant evidence, verification results, authority assessment, risk assessment, decision outcome, and supporting metadata.

This creates a traceable representation of how the decision was reached and allows authorised stakeholders to review the decision later.

### 5.9 Execution Boundary

VERA is positioned before consequential execution.

An APPROVE decision indicates that the proposed action has satisfied the defined prototype control conditions. A HUMAN REVIEW decision requires an authorised human decision-maker to determine whether the action should proceed. A BLOCK decision prevents the action from progressing through the prototype execution workflow.

The prototype therefore treats VERA as a control boundary rather than as the financial execution system itself.

## 6. VERA Decision Framework

VERA evaluates every proposed financial action through four primary control dimensions:

1. Evidence
2. Policy
3. Authority
4. Risk

These dimensions are evaluated independently before being combined by the Decision Engine.

### 6.1 Evidence Control

The Evidence Control determines whether the proposed action is sufficiently supported by relevant information.

Key questions include:

- Is supporting evidence available?
- Is the evidence relevant to the proposed action?
- Is the evidence sufficiently complete?
- Are there contradictions between evidence sources?
- Is the evidence sufficiently recent for the decision context?
- Does the evidence actually support the proposed action?

### 6.2 Policy Control

The Policy Control determines whether the action complies with applicable rules and constraints.

Key questions include:

- Is the action permitted?
- Are transaction or operational limits satisfied?
- Are eligibility requirements satisfied?
- Are additional approvals required?
- Does the action conflict with any defined policy?

### 6.3 Authority Control

The Authority Control determines whether the AI agent and the workflow have sufficient authority for the proposed action.

Key questions include:

- Is the agent authorised for this action type?
- Is the transaction value within the agent's permitted limit?
- Does the action require elevated approval?
- Does the proposed action exceed the assigned authority?
- Is the required human authority available?

### 6.4 Risk Control

The Risk Control evaluates whether the proposed action falls within acceptable risk conditions.

Key questions include:

- What risk indicators are present?
- Does the action exceed a defined risk threshold?
- Are there unusual or potentially suspicious characteristics?
- Are multiple control failures occurring simultaneously?
- Does the action require additional human scrutiny?

### 6.5 Decision Logic

The four control dimensions contribute to the final decision.

A simplified conceptual model is:

Evidence
+
Policy
+
Authority
+
Risk
↓
Decision Engine
↓
APPROVE / HUMAN REVIEW / BLOCK

The Decision Engine should apply explicit and testable rules so that equivalent inputs produce consistent outcomes.

The prototype may use weighted or threshold-based scoring for selected risk dimensions where appropriate, but critical control failures should be capable of overriding a favourable aggregate score.

### 6.6 Decision Explainability

Each decision should have an explicit explanation based on the control results.

For example:

**APPROVE**

All required evidence was present, applicable policies were satisfied, the action remained within authorised boundaries, and the assessed risk remained below the configured threshold.

**HUMAN REVIEW**

The action did not contain a critical violation but one or more conditions required additional human judgement, approval, or investigation.

**BLOCK**

A critical control condition failed, such as insufficient evidence, a policy violation, an authority violation, or unacceptable risk.

The explanation is intended to make the decision understandable to authorised operational, risk, product, and audit stakeholders.

## 7. What VERA Does NOT Do

VERA is a research-driven prototype and does not claim to replace production financial infrastructure, regulatory controls, security systems, or institutional governance processes.

VERA does not:

- act as a real bank or financial institution;
- independently move real customer funds;
- provide financial advice to customers;
- replace human accountability for consequential decisions;
- claim regulatory approval or certification;
- guarantee that an AI-generated action is safe;
- provide production-grade fraud detection;
- provide a complete enterprise compliance platform;
- assume that an AI-generated explanation is inherently trustworthy;
- treat a high confidence score from an AI model as sufficient authority to execute an action.

The prototype uses controlled and, where appropriate, synthetic data and simulated financial workflows for evaluation.

Its purpose is to demonstrate and evaluate the proposed control architecture rather than to represent a production-ready financial system.

Any future production implementation would require significantly greater engineering, security, regulatory, operational, model-risk, data-governance, and institutional controls.

## 8. MVP Scope

The VERA MVP will focus on demonstrating the complete decision-control lifecycle for a controlled set of consequential financial actions.

### In Scope

The MVP will include:

- structured AI-generated financial action proposals;
- an evidence verification layer;
- a policy verification layer;
- an authority verification layer;
- a risk assessment layer;
- a deterministic decision engine;
- APPROVE, HUMAN REVIEW, and BLOCK outcomes;
- human-in-the-loop escalation;
- structured audit records;
- synthetic evaluation scenarios;
- test cases covering successful and failed control conditions;
- an interface for submitting and reviewing proposed actions;
- API-based communication between major system components;
- persistent storage for relevant decisions and audit records.

### Initial Action Types

The prototype will initially focus on a limited set of financial action categories selected for their ability to demonstrate different control requirements.

The initial implementation will prioritise refund and payment or transfer scenarios, while maintaining an architecture that can support additional consequential financial actions.

### Out of Scope for the MVP

The MVP will not include:

- live banking integrations;
- real customer financial data;
- actual movement of funds;
- production authentication infrastructure;
- production regulatory certification;
- unrestricted autonomous execution;
- institution-specific compliance certification;
- fully autonomous financial decision-making.

These capabilities may be considered as future extensions rather than requirements for the initial prototype.

## 9. Success Criteria

VERA will be considered successful as a prototype if it demonstrates that a proposed financial action can be evaluated consistently through multiple independent control dimensions before reaching an execution decision.

The MVP should demonstrate the following:

### 9.1 Functional Success

The system can accept a structured AI-generated action proposal and process it through evidence, policy, authority, and risk controls.

### 9.2 Decision Success

The system can correctly produce the intended APPROVE, HUMAN REVIEW, or BLOCK outcome for defined evaluation scenarios.

### 9.3 Control Success

Critical control failures, including policy violations, authority violations, and unacceptable risk conditions, can prevent inappropriate automatic approval.

### 9.4 Explainability Success

Every decision contains sufficient structured information to explain which controls were evaluated and why the resulting outcome was produced.

### 9.5 Auditability Success

A decision can be retrieved after evaluation together with its relevant evidence, control results, decision outcome, and associated metadata.

### 9.6 Consistency Success

Equivalent inputs processed under the same configured control conditions should produce consistent decisions.

### 9.7 Human Oversight Success

Cases requiring additional judgement can be routed to a human review workflow rather than being forced into automatic approval or rejection.

### 9.8 Evaluation Success

The prototype will be evaluated using a deliberately constructed set of positive, negative, borderline, contradictory, and adversarial scenarios.

Evaluation results will be documented rather than relying solely on qualitative claims about system performance.

## 10. Product Boundary and Design Principles

VERA is built around the principle that increasing AI capability should not automatically result in increasing execution authority.

The prototype follows the following design principles:

### 10.1 Intelligence and Authority Separation

An AI system may recommend an action without automatically possessing the authority to execute that action.

### 10.2 Independent Verification

The control layer should independently evaluate the conditions surrounding a proposed action rather than simply accepting the AI agent's conclusion.

### 10.3 Evidence Before Execution

Consequential actions should be supported by sufficient and relevant evidence before they can qualify for automatic approval.

### 10.4 Explicit Policy Controls

Policies and operational constraints should be represented as explicit, testable controls wherever practical.

### 10.5 Bounded Authority

AI actions should remain within explicitly defined authority boundaries.

### 10.6 Risk-Aware Decisioning

The system should account for risk rather than treating every technically valid action as equally suitable for automatic execution.

### 10.7 Human Oversight

Human intervention should remain available for ambiguous, exceptional, high-risk, or otherwise consequential cases.

### 10.8 Auditability

Decisions should produce structured records that allow authorised stakeholders to reconstruct and review the decision process.

### 10.9 Fail Safely

When critical information is missing or a critical control cannot be satisfactorily verified, the system should favour escalation or blocking rather than silently assuming that the action is safe.

### 10.10 Prototype Transparency

The project will clearly distinguish between implemented functionality, simulated behaviour, research assumptions, and future production capabilities.

