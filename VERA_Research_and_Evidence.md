# VERA — Research & Evidence

## 1. Purpose of This Document

This document establishes the real-world research foundation for VERA.

The purpose is to distinguish between:

- established evidence about AI and financial services;
- emerging risks associated with increasingly autonomous AI systems;
- existing approaches to AI governance and assurance;
- the specific control problem investigated by VERA; and
- the assumptions and research gaps that will be tested through the prototype.

VERA is not presented as a solution to a hypothetical problem. Its design is informed by developments and concerns documented by financial regulators, central banks, international financial organisations, and academic research.

The evidence collected here will inform VERA's product requirements, architecture, control framework, test scenarios, and evaluation methodology.

## 2. AI Adoption in Financial Services

Artificial intelligence is already used across financial services for activities including operational automation, fraud detection, compliance, customer services, risk modelling, analytics, and other decision-support activities.

The Financial Stability Board's 2024 assessment of AI in finance identified significant potential benefits from AI adoption, including operational efficiency, regulatory compliance, personalised financial products, and advanced analytics.

The same assessment identified several vulnerabilities that may become increasingly important as AI adoption expands, including cyber risk, model risk, data quality and governance, third-party dependencies, and the possibility that AI systems could amplify financial fraud and disinformation.

This establishes an important starting point for VERA:

AI adoption in finance is not a hypothetical future scenario. Financial organisations are already integrating AI into operational and decision-support workflows.

The emerging challenge is therefore not simply whether financial organisations should use AI, but how increasingly capable AI systems can be deployed while maintaining appropriate controls, accountability, and resilience.

## 4. Why Financial Actions Require Strong Controls

Financial systems differ from many ordinary software environments because automated decisions can create immediate and consequential effects.

Potential consequences may include:

- financial loss;
- customer harm;
- fraud;
- operational disruption;
- privacy or data-protection issues;
- regulatory consequences;
- reputational damage;
- cyber-security consequences; and
- broader financial-system effects.

The Financial Stability Board has identified model risk, data quality and governance, cyber risk, third-party dependencies, and AI-enabled fraud or disinformation as important vulnerabilities associated with AI adoption in finance.

The Bank of England has separately highlighted risks associated with the deployment of more advanced AI, including agentic AI, in areas such as payments and financial markets.

Consequently, the threshold for autonomous execution of a financial action should not necessarily be the same as the threshold for generating a recommendation.

This distinction provides an important foundation for VERA's control model.

## 5. Evidence from Payment-System Research

The Bank for International Settlements has experimentally investigated the use of generative-AI agents for cash and liquidity management in real-time gross settlement payment systems.

The BIS study simulated payment scenarios involving liquidity constraints, competing payment priorities, and uncertainty about future transactions.

The experiments demonstrated that a generative-AI agent could perform several cash-management tasks and adapt its recommendations across different scenarios.

However, the study also identified the need for regulatory safeguards, human oversight, and further research before AI could be safely integrated into financial market infrastructures.

This research is particularly relevant to VERA because it demonstrates both sides of the problem:

1. AI agents can perform increasingly sophisticated financial decision-support tasks.
2. Increased capability does not eliminate the need for safeguards and human oversight.

VERA extends this problem into a specific control architecture by exploring how a proposed financial action could be independently evaluated before execution.

## 6. Regulatory and Supervisory Attention

Financial regulators are increasingly examining how advanced AI systems can be deployed safely.

In July 2026, the UK Financial Conduct Authority published a major review examining how AI could reshape retail financial services.

The review identified four major AI-driven shifts:

- transformation of firm operations;
- evolution of consumer journeys;
- changes in competition and market power; and
- amplification of fraud and cyber risks.

The FCA also reported significant consumer interest in autonomous AI in personal finance.

In addition, the FCA's AI Live Testing programme is being used to help firms investigate questions around AI risk management and live monitoring, with participating firms testing a range of AI technologies including agentic AI.

These developments demonstrate that the financial sector is moving beyond purely theoretical discussions of AI governance toward practical testing and assurance.

VERA therefore positions itself within an emerging problem space rather than treating AI governance as a solved problem.

## 7. The Control Gap

Existing research and regulatory work identifies many risks associated with increasingly autonomous AI systems.

These include:

- unreliable or insufficient information;
- model risk;
- lack of interpretability;
- cyber and fraud risks;
- excessive autonomy;
- inadequate governance;
- insufficient human oversight;
- unclear accountability; and
- difficulties monitoring increasingly complex AI behaviour.

However, identifying these risks does not automatically provide a unified mechanism for evaluating an individual proposed financial action before execution.

VERA investigates the following control gap:

An AI system may be capable of generating a financially reasonable recommendation, while the organisation still needs an independent mechanism to determine whether the specific action is sufficiently evidenced, policy-compliant, authorised, and appropriately risk-bounded.

The research question therefore becomes:

**Can an independent decision-control layer provide a structured mechanism for evaluating AI-generated financial actions before they reach consequential execution?**

VERA does not claim that existing financial organisations have no controls for these issues.

Instead, the prototype investigates whether these control dimensions can be integrated into a coherent, explainable, and testable decision workflow specifically designed around AI-generated financial actions.

## 8. VERA's Proposed Response

VERA proposes a control workflow consisting of four primary verification dimensions:

1. Evidence Verification
2. Policy Verification
3. Authority Verification
4. Risk Assessment

These controls operate between the AI-generated proposal and consequential execution.

The conceptual workflow is:

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

The architecture deliberately separates AI-generated intelligence from execution authority.

The AI agent can propose an action.

VERA independently evaluates whether the action satisfies the configured control conditions.

Only after the verification process is completed does the system determine the appropriate outcome.

## 9. Research Hypothesis

VERA investigates the following hypothesis:

**An independent, evidence-based decision-control layer can improve the transparency, consistency, and boundedness of AI-generated financial actions by separating AI recommendation capabilities from execution authority and evaluating proposed actions against evidence, policy, authority, and risk conditions before execution.**

The prototype will not attempt to prove that this architecture is sufficient for production financial systems.

Instead, it will test whether the proposed architecture can:

- identify defined control failures;
- prevent defined classes of inappropriate automatic approvals;
- route ambiguous cases to human review;
- produce explainable decisions;
- maintain structured audit records; and
- apply consistent decision logic across controlled scenarios.

## 10. What the Research Does Not Claim

The research does not claim that:

- VERA is the first AI governance system;
- no financial organisation has implemented AI controls;
- no existing product performs any of VERA's individual functions;
- VERA is production-ready;
- VERA can guarantee safe autonomous financial execution;
- the prototype satisfies regulatory requirements;
- synthetic testing is equivalent to production validation; or
- VERA eliminates the need for human governance.

Instead, VERA's contribution is the design and evaluation of a prototype architecture that integrates multiple control dimensions around a specific problem: determining whether an AI-generated financial action should be permitted to progress toward execution.

## 11. Research Gap and Positioning

The research reviewed for VERA demonstrates that AI adoption in finance is accelerating and that increasingly autonomous systems introduce new governance, risk, oversight, and resilience considerations.

Existing work covers areas including:

- responsible AI governance;
- model risk management;
- AI assurance;
- fraud detection;
- compliance automation;
- human oversight;
- AI monitoring;
- payment-system safeguards; and
- financial-sector AI risk.

VERA does not attempt to replace these disciplines.

Instead, the prototype investigates a narrower integration problem:

**How can evidence, policy, authority, and risk controls be combined into an explicit decision boundary between an AI-generated financial action and its potential execution?**

This distinction will be examined through a landscape review before the final architecture is considered complete.

The project will therefore treat the existence of similar systems as a research finding rather than assuming that VERA has no precedent.

The final project will document both similarities and differences between VERA and identified existing approaches.

## 12. Source Quality Principles

Research evidence used by VERA should prioritise authoritative and primary sources.

Preferred sources include:

1. Financial regulators and supervisory authorities;
2. Central banks;
3. International financial organisations;
4. Standards and policy bodies;
5. Peer-reviewed academic research;
6. Established research institutions;
7. Industry research where primary evidence is available.

Search-engine summaries, blogs, marketing pages, social-media posts, and unsupported commentary should not be treated as primary evidence for major claims.

Where a source is used to support an important product or research decision, the project should record:

- organisation or author;
- publication title;
- publication date;
- source URL;
- relevant finding;
- relevance to VERA; and
- which VERA design decision it informs.

## 13. Initial Evidence Register

### Source 1 — Financial Stability Board

**Publication:** The Financial Stability Implications of Artificial Intelligence

**Date:** November 2024

**Key finding:** AI adoption can create or amplify financial-sector vulnerabilities including cyber risk, model risk, data-quality and governance risks, third-party dependencies, and AI-enabled fraud or disinformation.

**Relevance to VERA:** Supports the need for stronger controls around AI use in financial environments.

### Source 2 — Bank of England

**Publication:** Financial Stability Report — July 2026

**Key finding:** Agentic AI systems are increasingly capable of carrying out multi-step tasks using external tools with limited human oversight.

**Relevance to VERA:** Supports the distinction between AI capability and the controls required when AI systems become more autonomous.

### Source 3 — Bank of England

**Publication:** Financial Policy Committee Record — April 2026

**Key finding:** The Bank identified growing potential risks from advanced AI, including agentic AI, and highlighted the need for further work focused on use cases in payments and financial markets.

**Relevance to VERA:** Supports focusing the prototype on consequential financial actions and payment-related scenarios.

### Source 4 — Bank for International Settlements

**Publication:** AI agents for cash management in payment systems

**Date:** November 2025

**Key finding:** Experiments showed that generative-AI agents could perform sophisticated cash-management tasks, while the researchers highlighted the need for regulatory safeguards, human oversight, and further research.

**Relevance to VERA:** Provides direct evidence that AI agents can perform financial decision-support tasks while reinforcing the importance of controls around their deployment.

### Source 5 — Financial Conduct Authority

**Publication:** Landmark review into impact of AI on retail financial services

**Date:** July 2026

**Key finding:** The FCA identified the transformation of firm operations and the amplification of fraud and cyber risks among major AI-driven shifts in retail financial services and identified growing consumer interest in agentic AI.

**Relevance to VERA:** Demonstrates current regulatory attention toward autonomous AI and associated financial risks.

### Source 6 — Financial Conduct Authority

**Publication:** AI Live Testing — Second Cohort

**Date:** April 2026

**Key finding:** The FCA's testing programme includes questions around AI risk management and live monitoring, with firms testing technologies including agentic AI.

**Relevance to VERA:** Supports the project's emphasis on testing, monitoring, assurance, and practical AI controls.

## 14. Current Research Conclusion

The initial evidence indicates that VERA is addressing a genuine and rapidly developing problem space.

AI is already being adopted across financial services, while newer agentic systems are increasing the degree of autonomy with which AI can plan, interact with tools, and perform multi-step tasks.

Financial-sector authorities are simultaneously identifying concerns around model risk, governance, cyber risk, fraud, interpretability, resilience, and human oversight.

Research involving AI agents in payment-system environments demonstrates that these systems can perform meaningful financial decision-support tasks while also highlighting the continuing need for safeguards and human oversight.

The evidence therefore supports further investigation of an independent control layer for AI-generated financial actions.

However, the research does not yet establish that VERA's precise architecture is novel or superior to existing approaches.

That question will be investigated through a dedicated competitive and technical landscape review before the final architecture is locked.

This distinction is important to the integrity of the project:

**VERA begins with a documented real-world problem, proposes a specific control architecture, and then tests whether that architecture provides meaningful value through implementation and evaluation.**