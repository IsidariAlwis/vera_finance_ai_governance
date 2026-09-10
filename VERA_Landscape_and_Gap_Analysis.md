# VERA — Landscape & Gap Analysis

## 1. Purpose

This document evaluates the existing technology, research, governance frameworks, and industry initiatives related to AI governance, agentic AI, authorization, runtime controls, financial AI risk, and AI-enabled financial actions.

The purpose is not to claim that VERA is the first system to address AI governance or agent authorization.

Instead, the analysis identifies:

* what existing approaches already provide;
* which aspects of VERA overlap with existing solutions;
* where existing approaches are broader or narrower than VERA;
* which elements of the VERA concept remain worth investigating; and
* how VERA should be differentiated as a research-driven prototype.

The landscape review is therefore a critical input to the final VERA architecture.

---

## 2. Existing Landscape

### 2.1 Enterprise AI Governance Platforms

Enterprise AI governance platforms provide capabilities for managing AI systems throughout their lifecycle.

For example, IBM watsonx.governance provides AI governance, risk management, compliance workflows, policy controls, monitoring, and audit capabilities. IBM has also introduced governance capabilities specifically for AI agents, including agent inventories, agent onboarding workflows, guardrails, runtime monitoring, and traceability.

These capabilities demonstrate that enterprise AI governance is an established product category.

However, enterprise AI governance is generally broader than VERA's proposed decision-control workflow.

VERA focuses specifically on evaluating an individual proposed financial action before it progresses toward execution.

---

## 3. Agentic AI Control and Authorization

The emergence of agentic AI has created a separate need to control what individual agents are permitted to do.

The World Economic Forum's 2026 work on trusted adoption of AI agents identifies authorization as a major challenge and proposes an Agent Capability and Authorization Profile for defining delegated authority, system design, operational oversight, auditability, and accountability.

AWS similarly recommends fine-grained authentication and authorization, least-privilege access, explicit action boundaries, and monitoring when deploying agents in financial-services environments.

These approaches strongly overlap with one of VERA's principles:

**AI capability should not automatically imply execution authority.**

This confirms that authority separation is a real industry problem rather than an invented concept.

---

## 4. Runtime Governance

More recent agentic-AI research and industry work has shifted attention from static model governance toward runtime governance.

CRISIL Integral IQ's 2026 research describes runtime governance for financial workflows in which institutions evaluate whether an agent remains within its mandate, limits, and approval requirements during execution.

The work also introduces concepts relating to runtime validation, governance telemetry, containment, and autonomy risk.

This is highly relevant to VERA because it demonstrates that the industry is increasingly concerned with controlling agent behaviour during execution rather than only evaluating an AI model before deployment.

VERA therefore should not position runtime governance itself as a novel concept.

Instead, the project should investigate a narrower decision-control workflow focused on the evaluation of an individual proposed financial action.

---

## 5. Financial-Sector Agent Governance

The financial sector is beginning to develop specific frameworks for AI-agent use.

The Bank of England has identified agentic AI as an emerging area of financial-stability interest and has highlighted concerns related to autonomy, resilience, payments, and financial-system risks.

The FCA has also increased practical testing of AI systems, including work involving agentic AI and questions around risk management and monitoring.

In August 2026, CRISIL Integral IQ published research specifically addressing runtime governance for AI-driven financial workflows.

These developments demonstrate that financial-sector AI governance is rapidly evolving.

VERA therefore enters an active research and product landscape rather than an empty market.

---

## 6. Agentic Payments

Agentic payments are becoming an especially important area of development.

Recent industry initiatives demonstrate that financial organisations are beginning to address the identity, authorization, authentication, and trust requirements of AI agents acting in payment environments.

Visa, Mastercard, and Ant International announced a joint initiative in September 2026 focused on creating a trust framework for AI agents capable of making purchases on behalf of users.

Separately, India's payments ecosystem is developing an AI-agent registry intended to verify and monitor AI agents conducting transactions.

These developments reinforce the importance of agent identity, authorization, monitoring, and transaction boundaries.

They also mean that VERA must avoid claiming that it is the first system to address trusted agentic financial transactions.

---

## 7. Comparison of Existing Approaches

| Approach                          | AI Governance | Policy Controls | Agent Authorization | Runtime Controls | Risk Assessment | Human Review | Auditability |                     Financial Action Focus |
| --------------------------------- | ------------: | --------------: | ------------------: | ---------------: | --------------: | -----------: | -----------: | -----------------------------------------: |
| IBM watsonx.governance            |           Yes |             Yes |                 Yes |              Yes |             Yes |          Yes |          Yes |                                      Broad |
| AWS agentic-AI security guidance  |           Yes |             Yes |                 Yes |              Yes |         Partial |      Partial |          Yes |                Financial-services guidance |
| World Economic Forum ACAP         |           Yes |             Yes |                 Yes |              Yes |             Yes |          Yes |          Yes |                             Cross-industry |
| CRISIL runtime governance         |           Yes |             Yes |                 Yes |              Yes |             Yes |          Yes |          Yes |                        Financial workflows |
| Agentic payment trust initiatives |       Partial |         Partial |                 Yes |              Yes |         Partial |       Varies |          Yes |                                   Payments |
| VERA prototype                    |           Yes |             Yes |                 Yes |              Yes |             Yes |          Yes |          Yes | Proposed financial-action decision control |

The comparison demonstrates that VERA's individual components are not individually unprecedented.

The differentiation must therefore come from the way those components are integrated, implemented, tested, and evaluated around a clearly defined financial-action decision workflow.

---

## 8. What VERA Should NOT Claim as Novel

Based on the current landscape review, VERA should not claim novelty for:

* AI governance generally;
* AI monitoring;
* AI audit trails;
* policy enforcement;
* agent authorization;
* least-privilege access;
* human-in-the-loop controls;
* runtime monitoring;
* AI risk assessment;
* financial AI governance;
* agentic payment trust;
* or the general concept of separating AI capability from authority.

These are already represented in research, standards, industry frameworks, and commercial products.

Making unsupported novelty claims would weaken the credibility of the project.

---

## 9. The VERA Opportunity

Although individual components already exist, VERA can investigate a more focused product question:

**Can an AI-generated financial action be evaluated through a unified, explicit decision-control workflow that combines evidence sufficiency, policy compliance, execution authority, and risk conditions before determining whether the action should be approved, escalated, or blocked?**

The key emphasis is therefore not simply on governing an AI model.

The emphasis is on governing the transition:

**AI recommendation → consequential financial action**

This creates a narrower product boundary than a general AI governance platform.

---

## 10. Evidence as a First-Class Control

One potential area of differentiation is the explicit treatment of evidence as a decision-control input.

Traditional AI governance may evaluate model performance, risk, compliance, monitoring, or lifecycle controls.

VERA additionally asks:

**What evidence supports this specific action?**

The prototype can therefore investigate whether action-level evidence verification can be represented as a structured control alongside policy, authority, and risk.

This does not imply that evidence verification is a completely new concept.

Rather, VERA treats evidence sufficiency as a first-class component of the proposed action decision.

---

## 11. Action-Level Rather Than Model-Level Governance

Many AI governance systems operate at the level of:

* models;
* AI applications;
* use cases;
* AI agents;
* governance processes; or
* enterprise risk.

VERA focuses on the level of the **individual proposed action**.

For example:

An AI system may be generally approved for use.

However, that does not necessarily mean every action it proposes should automatically be executed.

VERA therefore introduces an additional decision boundary:

**Approved AI system ≠ Automatically approved financial action**

The proposed control layer evaluates the action itself.

---

## 12. Authority and Intelligence Separation

A central VERA design principle is:

**Capability does not equal authority.**

An AI agent may be capable of generating a £500 refund recommendation.

That does not necessarily mean the agent should possess authority to execute a £500 refund.

The authority decision can instead depend on:

* action type;
* transaction value;
* agent role;
* delegated permissions;
* applicable policies;
* risk level;
* customer or account context; and
* required approval level.

This principle is consistent with current industry discussions around agent authorization and delegated authority.

VERA's contribution is to make this distinction an explicit component of the prototype's action-level decision engine.

---

## 13. VERA's Proposed Differentiation

Based on the current research, VERA should be positioned as:

**A research-driven prototype exploring an action-level decision-control layer for AI-generated financial actions.**

The proposed workflow integrates:

**Evidence**
+
**Policy**
+
**Authority**
+
**Risk**
↓
**Decision**
↓
**Approve / Human Review / Block**
↓
**Audit Record**

The project's differentiation therefore lies in the integration and practical demonstration of these controls around a single financial-action lifecycle rather than in claiming ownership of any individual control concept.

---

## 14. Research Questions Emerging from the Landscape

The landscape review creates several questions that VERA can investigate experimentally.

### Question 1

Can evidence quality be represented as an explicit decision-control input?

### Question 2

Can authority boundaries be evaluated independently from the AI's recommendation?

### Question 3

Can multiple control failures be combined into a deterministic and explainable decision?

### Question 4

Can ambiguous actions be reliably separated from clearly approvable and clearly blockable actions?

### Question 5

Can a structured audit record make the decision process sufficiently transparent for operational and risk stakeholders?

### Question 6

Can the architecture remain modular enough to support different financial action types without redesigning the entire control layer?

### Question 7

Can the prototype demonstrate meaningful improvement over a baseline in which an AI recommendation is accepted without the additional VERA control layer?

---

## 15. Competitive Positioning

VERA is not intended to compete directly with enterprise platforms such as IBM watsonx.governance.

Those platforms operate at significantly broader enterprise scales and include extensive lifecycle, compliance, model-management, monitoring, and governance capabilities.

VERA instead functions as a focused research prototype.

Its value lies in demonstrating:

1. a clearly defined problem;
2. an explicit action-level control architecture;
3. practical implementation;
4. measurable evaluation;
5. transparent limitations; and
6. a documented product rationale.

The project therefore demonstrates product discovery and systems thinking rather than attempting to reproduce an enterprise governance platform within a short prototype development cycle.

---

## 16. Preliminary Gap Statement

The current landscape does not support the claim that no solutions exist for controlling autonomous AI systems.

Instead, the research suggests that multiple technologies and frameworks already address individual or overlapping aspects of the problem.

The preliminary gap investigated by VERA is therefore:

**The practical integration of evidence sufficiency, policy compliance, delegated authority, and risk assessment into a single action-level decision boundary for AI-generated financial actions, accompanied by explainable outcomes and an auditable decision record.**

This is a hypothesis to be tested through implementation and evaluation rather than a claim of proven market uniqueness.

---

## 17. Implications for VERA's Architecture

The landscape review directly affects the architecture.

VERA should therefore include:

* an explicit action proposal object;
* evidence representation and verification;
* policy evaluation;
* authority evaluation;
* risk assessment;
* deterministic decision logic;
* human-review routing;
* structured audit records;
* configurable control thresholds;
* clear separation between AI recommendation and execution authority; and
* an evaluation framework capable of testing control failures independently.

The architecture should also remain modular so that future versions could integrate with external identity, policy, risk, monitoring, or AI-governance systems.

---

## 18. Implications for Product Strategy

The research suggests that VERA should not be marketed as:

> "A completely new AI governance platform."

A more credible positioning is:

> **"An experimental action-level control layer for AI-generated financial decisions."**

This positioning allows VERA to demonstrate product differentiation without making unsupported claims about the entire AI governance market.

It also creates a clearer potential product evolution:

**Prototype**
→ action-level verification

**V2**
→ richer financial workflows

**V3**
→ agent integrations

**V4**
→ enterprise policy and identity integrations

**V5**
→ continuous runtime governance and portfolio-level controls

The prototype therefore serves as a focused demonstration of a potentially larger product architecture.

---

## 19. Current Conclusion

The landscape review confirms that the problem VERA addresses is real, current, and increasingly important.

It also confirms that VERA is entering a competitive and rapidly developing technology landscape.

The project should therefore be judged not by whether every individual component is unprecedented, but by whether VERA can demonstrate a useful, coherent, explainable, and testable integration of those components around a specific financial-action control problem.

The next stage of the project will convert these research findings into formal product requirements and measurable acceptance criteria.

The resulting prototype will then provide evidence for whether the proposed architecture works as intended.

VERA's credibility will therefore come from:

**research → design → implementation → testing → evidence**

rather than from unsupported claims of novelty.
