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