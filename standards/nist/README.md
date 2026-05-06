# NIST AI Risk Management Framework (AI RMF 1.0)
### A Comprehensive Implementation Guide

| | |
|---|---|
| **Document** | NIST AI 100-1 |
| **Version** | 1.0 (released 26 January 2023); Generative AI Profile NIST AI 600-1 (26 July 2024) |
| **Published by** | National Institute of Standards and Technology, U.S. Department of Commerce |
| **Status** | Voluntary; next formal review no later than 2028 |
| **Primary URL** | https://www.nist.gov/itl/ai-risk-management-framework |
| **Download** | https://nvlpubs.nist.gov/nistpubs/ai/NIST.AI.100-1.pdf |
| **Playbook** | https://airc.nist.gov/airmf-resources/playbook/ |
| **Resource Center** | https://airc.nist.gov |

---

## 1. What It Is

The NIST AI Risk Management Framework is a voluntary, technology-neutral, sector-agnostic framework designed to help any organization that designs, develops, deploys, or uses AI systems manage risk and promote trustworthy AI. It was mandated by the National AI Initiative Act of 2020 (P.L. 116-283) and developed over 18 months through an open, consensus-driven process involving more than 240 contributing organizations from industry, academia, civil society, and government.

The framework does not carry the force of law. It does not prescribe specific controls or mandate compliance timelines. What it does is provide a common vocabulary, a structured methodology, and an adaptable set of outcomes that organizations can apply in full or in part depending on their sector, risk tolerance, and maturity level.

Despite being voluntary, the AI RMF has become the de facto AI governance standard in the United States. It is referenced by federal agencies, cited in state AI laws, required for certain federal contracting contexts, and used internationally as a technical companion to the EU AI Act and ISO/IEC 42001. As of 2025–2026, sector regulators including the FTC, FDA, SEC, CFPB, and EEOC increasingly reference AI RMF principles in enforcement expectations.

---

## 2. Core Design Principles

The AI RMF is built on six design principles that distinguish it from traditional software risk frameworks:

**Socio-technical framing.** AI risks emerge not only from models and data, but from the people, processes, and social contexts around them. The framework treats AI systems as inherently socio-technical and requires that risk management account for human behavior, organizational dynamics, and societal context — not just technical outputs.

**Lifecycle orientation.** Risk management under the AI RMF begins at the planning and design stage and continues through development, deployment, monitoring, and decommissioning. It is not a point-in-time assessment.

**AI actor accountability.** The framework defines "AI actors" as any person or organization that plays an active role in the AI lifecycle — including developers, deployers, end users, evaluators, and affected communities. Each actor shares responsibility proportional to their role and influence.

**Use-case agnosticism.** The framework does not prescribe what controls apply to which systems. Instead, organizations build "profiles" that tailor the framework to their specific application context, sector, and risk tolerance.

**Living document model.** The AI RMF is explicitly designed to evolve. The Playbook (the companion action guide) is updated approximately twice per year. A formal community review of the core framework is expected before 2028. Sector-specific profiles (e.g., Generative AI, Critical Infrastructure) extend the framework as new use cases emerge.

**Integration with existing risk systems.** The AI RMF is explicitly designed to sit alongside — not replace — existing enterprise risk, cybersecurity (NIST CSF, SP 800-53), and privacy frameworks. Organizations integrate AI risk into their existing governance structures rather than building a parallel process.

---

## 3. How AI Risk Differs from Traditional Software Risk

The AI RMF dedicates specific attention to the ways AI risk is categorically different from traditional IT risk, because failing to understand this leads to inadequate governance. Key differences:

- **Data dependence and drift.** AI systems are trained on data that can change over time, sometimes significantly and unpredictably. This can degrade system performance or behavior in ways that are difficult to detect without continuous monitoring — something that is not a concern in static software.
- **Emergent behavior.** AI systems can produce outputs or behaviors not explicitly programmed or anticipated by their developers. Traditional software failure modes are generally known at design time; AI failure modes are often discovered post-deployment.
- **Inscrutability.** Many AI models — particularly large neural networks — are not easily explainable or interpretable. This complicates risk measurement, audit, and accountability in ways that static code review does not.
- **Third-party model risk.** Organizations increasingly build on top of externally developed models (foundation models, open-source weights, APIs). The risk metrics of the model developer may not align with the risk context of the deployer. This creates accountability gaps not present in traditional software procurement.
- **Human-AI interaction risk.** AI systems interact with people in dynamic ways. Automation bias (over-reliance on AI outputs), miscommunication of AI uncertainty, and the opacity of AI decision-making all introduce risks specific to how humans and AI systems interact.
- **Privacy amplification.** AI systems trained on personal data can memorize, reconstruct, or infer sensitive information in ways that amplify privacy risks beyond what the underlying data would suggest.
- **Environmental cost.** Resource-heavy AI training and inference carry significant energy and environmental implications that fall outside traditional software risk models.

---

## 4. The Seven Trustworthiness Characteristics

The AI RMF defines trustworthiness through seven interconnected characteristics. These are not independent checklists — they interact with and create tradeoffs against each other. The goal is to balance all characteristics in proportion to the system's context of use.

### 4.1 Valid and Reliable
The system performs as intended, produces accurate outputs, and generalizes correctly beyond its training distribution. Validity confirms that requirements for the specific intended use are fulfilled (ISO 9000:2015). Reliability means the system performs without failure over a given time interval under expected conditions. Accuracy metrics must be paired with clearly defined, representative test sets and must include disaggregated results across data segments, not just aggregate scores. Robustness (the ability to maintain performance across varied circumstances, including edge cases and adversarial inputs) is a component of validity. **Valid and Reliable is the foundational characteristic — without it, the others cannot be meaningfully assessed.**

### 4.2 Safe
The system does not, under defined conditions, endanger human life, health, property, or the environment (ISO/IEC TS 5723:2022). Safety risk management requires responsible design from the earliest stages, rigorous simulation and in-domain testing, real-time monitoring post-deployment, and the ability to shut down or modify systems that deviate from expected behavior. Safety risks with potential for serious injury or death require the most urgent prioritization. The AI RMF encourages alignment with sector-specific safety standards in domains like transportation, healthcare, and critical infrastructure.

### 4.3 Secure and Resilient
The system maintains confidentiality, integrity, and availability through protection mechanisms that prevent unauthorized access and use. Security-specific risks for AI include adversarial examples (inputs crafted to cause model errors), data poisoning (corrupting training data to alter model behavior), model exfiltration (extracting model parameters or training data through API access), and prompt injection in large language model deployments. Resilience is the ability to return to normal function after an unexpected adverse event — and to degrade safely and gracefully when full recovery is not possible. AI security controls connect directly to NIST Cybersecurity Framework (CSF) and SP 800-53 controls.

### 4.4 Accountable and Transparent
Accountability requires that the appropriate actors can be identified and held responsible for AI system outcomes. Transparency is a prerequisite for accountability: it refers to the extent to which information about an AI system — its design decisions, training data, intended use cases, operational limitations, and outputs — is available and accessible to relevant stakeholders. Transparency is not binary; appropriate levels of disclosure vary by the role of the audience (end user, deployer, regulator, auditor) and the stage of the lifecycle. Maintaining data provenance and supporting attribution of model decisions to subsets of training data are concrete transparency practices. A transparent system is not necessarily a fair, safe, or accurate one — but it is very difficult to assess whether an opaque system is any of those things.

### 4.5 Explainable and Interpretable
Explainability refers to a representation of the mechanisms underlying an AI system's operation ("how does this work?"). Interpretability refers to the meaning of AI system outputs in the context of its designed functional purpose ("why did it produce this output, and what does that mean for me?"). Together, they allow operators, deployers, and end users to develop appropriate trust in the system and to identify and correct errors. Explainable systems are easier to debug, monitor, audit, and govern. Risk from lack of explainability is often managed through documentation — describing how the system functions at a level appropriate to the audience's role and knowledge.

### 4.6 Privacy-Enhanced
AI systems that use, generate, or process personal data should protect individuals' privacy throughout the lifecycle, including during training, inference, and post-deployment monitoring. Privacy-enhancing techniques — differential privacy, federated learning, data minimization, anonymization — can be applied at various stages, though some involve tradeoffs against accuracy or fairness. The AI RMF notes that under certain conditions (data sparsity, for example), privacy-enhancing techniques can result in accuracy losses that affect fairness outcomes — illustrating the characteristic interaction effects.

### 4.7 Fair — with Harmful Bias Managed
AI systems should not perpetuate or amplify harmful biases, discriminate unfairly, or create inequitable outcomes across demographic or social groups. Bias can emerge from training data (historical biases encoded in data), model design (objective functions that optimize for aggregate performance while ignoring subgroup disparities), deployment context (systems applied outside their training distribution), and human use (deployers or end users who apply AI outputs in biased ways). The AI RMF does not prescribe a single definition of fairness — it acknowledges that definitions of fairness are contextual, contested, and should be determined in consultation with affected communities.

---

## 5. The AI RMF Core: Four Functions

The Core is the operational heart of the AI RMF. It organizes AI risk management into four functions: **GOVERN, MAP, MEASURE, and MANAGE**. Across these four functions, the framework defines 19 categories and 72 subcategories. GOVERN is a cross-cutting function that informs and is embedded in all others. MAP, MEASURE, and MANAGE are applied at specific stages of the AI lifecycle and can be performed in any order depending on organizational needs.

---

### FUNCTION 1: GOVERN

GOVERN is the foundation. It establishes the organizational structures, culture, accountability mechanisms, policies, and resources needed for all other AI risk management activity. Without effective governance, MAP, MEASURE, and MANAGE activities lack organizational authority, consistent resources, and clear accountability.

GOVERN is applied continuously across the entire organization — not just for individual AI systems. It has **6 categories:**

#### GOVERN 1 — Policies, Processes, and Practices
Organizational-level policies, processes, and practices for mapping, measuring, and managing AI risks are in place, transparent, and implemented effectively.

Key subcategories:
- **GOVERN 1.1** — Legal and regulatory requirements involving AI are understood, managed, and documented. This includes sector-specific obligations, data protection laws, procurement rules, and emerging AI-specific regulations.
- **GOVERN 1.2** — The characteristics of trustworthy AI (the seven listed above) are integrated into organizational policies, processes, procedures, and practices.
- **GOVERN 1.3** — Processes are in place to determine the needed level of risk management activity based on the assessed risk level of each AI system.
- **GOVERN 1.4** — Risk management processes and their outcomes are established through transparent policies and documented for accountability.
- **GOVERN 1.5** — Organizational risk tolerance for AI is established, communicated, and revised as context evolves.
- **GOVERN 1.6** — AI policies and procedures are regularly reviewed and updated to reflect changes in technology, deployment context, and regulatory environment.
- **GOVERN 1.7** — Processes and procedures are in place to deactivate AI systems that pose unacceptable risks.

#### GOVERN 2 — Accountability Structures
Accountability structures are in place so that the appropriate teams and individuals are empowered, responsible, and trained for mapping, measuring, and managing AI risks.

Key subcategories:
- **GOVERN 2.1** — Roles and responsibilities for mapping, measuring, and managing AI risks are defined, documented, and communicated across the organization.
- **GOVERN 2.2** — AI risk management is incorporated into the organizational risk management structure, with senior leadership accountability.
- **GOVERN 2.3** — Mechanisms are in place to ensure AI actors across the lifecycle (developers, deployers, evaluators) are identifiable and contactable.
- **GOVERN 2.4** — Teams responsible for AI systems include members with diverse skills, backgrounds, and disciplines — including domain experts, technical practitioners, ethicists, and representatives from affected communities.
- **GOVERN 2.5** — Organizational risk management processes address the risk of conflicts of interest among AI actors.
- **GOVERN 2.6** — Training and awareness programs ensure AI actors understand their risk management responsibilities.

#### GOVERN 3 — Organizational Culture
Organizational teams are committed to a culture that considers, communicates, and manages AI risk as a first-class concern.

Key subcategories:
- **GOVERN 3.1** — Organizational leadership establishes a tone that treats AI risk as a genuine organizational priority.
- **GOVERN 3.2** — Mechanisms exist for teams to raise AI risk concerns without retaliation, including through anonymous channels.

#### GOVERN 4 — Safety-First and Critical Thinking Culture
Organizational practices support a critical thinking and safety-first mindset in AI design, development, deployment, and use.

Key subcategories:
- **GOVERN 4.1** — A critical thinking and safety-first mindset is fostered across teams involved in AI activities to minimize potential negative impacts.
- **GOVERN 4.2** — Teams document and communicate the risks and potential impacts of AI technology they develop, deploy, evaluate, and use.
- **GOVERN 4.3** — Practices are in place to enable AI testing, identification of incidents, and information sharing — including both internal processes and participation in industry-level incident reporting.

#### GOVERN 5 — Stakeholder Engagement
Processes are in place for robust engagement with relevant AI actors and affected communities.

Key subcategories:
- **GOVERN 5.1** — Organizational policies provide mechanisms to engage with affected communities, end users, and other stakeholders throughout the AI lifecycle.
- **GOVERN 5.2** — Organizational teams ensure that feedback from affected individuals and communities informs AI system design and risk management decisions.

#### GOVERN 6 — Third-Party and Supply Chain Risk
Policies and procedures are in place to address AI risks arising from third-party software, data, models, and other supply chain elements.

Key subcategories:
- **GOVERN 6.1** — AI risk management practices address risks from third-party AI components, including pre-trained models, APIs, open-source libraries, and externally sourced datasets.
- **GOVERN 6.2** — Policies establish due diligence requirements for AI supply chain partners — including transparency expectations around training data, model limitations, and risk assessments conducted by external model developers.
- **GOVERN 6.3** — Contractual mechanisms with AI providers address risk allocation, incident notification, and ongoing monitoring responsibilities.

---

### FUNCTION 2: MAP

MAP establishes context. Before risks can be measured or managed, an organization must understand what kind of AI system is being built or deployed, in what context, for what purpose, with what data, and with what potential for impact. MAP provides the contextual framing that informs all downstream risk activity and enables an initial go/no-go decision on whether to proceed with an AI system. MAP has **5 categories:**

#### MAP 1 — Context Establishment
The context for the AI system is established, including intended purpose, deployment environment, key stakeholders, and potential impacts.

Key subcategories:
- **MAP 1.1** — The intended purpose and context of use of the AI system are clearly documented, including the specific tasks, inputs, outputs, and deployment environment.
- **MAP 1.2** — All categories of AI actors involved in the lifecycle — including developers, deployers, evaluators, end users, and affected individuals — are identified.
- **MAP 1.3** — The scientific, technical, and organizational assumptions and limitations of the AI system are identified and documented.
- **MAP 1.4** — The potential beneficial and harmful impacts of the AI system on individuals, groups, communities, organizations, and broader society are identified.
- **MAP 1.5** — Organizational risk tolerances are applied to the specific system context and the appropriate level of AI risk management activity is determined.
- **MAP 1.6** — Practices and policies are implemented for AI system categorization, including classification by risk level.

#### MAP 2 — Scientific Basis and State of the Art
The specific types of risks associated with the AI system are identified based on the scientific and technical state of the art.

Key subcategories:
- **MAP 2.1** — Scientific understanding of AI risks relevant to the system type and deployment context is assessed and documented.
- **MAP 2.2** — Risks associated with the AI system are identified and prioritized using a structured methodology, taking into account both the likelihood and magnitude of potential harm.
- **MAP 2.3** — AI system failure modes — both technical and socio-technical — are identified and documented.

#### MAP 3 — AI Lifecycle Understanding
The specific stages of the AI lifecycle relevant to the system are identified and risk management activities are scoped accordingly.

Key subcategories:
- **MAP 3.1** — All stages of the AI lifecycle relevant to the system are identified — including data collection, preparation, model selection, training, testing, deployment, monitoring, and decommissioning.
- **MAP 3.2** — Roles and responsibilities of AI actors at each lifecycle stage are identified and documented.
- **MAP 3.3** — Data used for training, testing, and evaluation are documented, including provenance, quality assessments, and known limitations.

#### MAP 4 — Organizational Risk Context
The AI system's risk context within the broader organizational risk environment is established.

Key subcategories:
- **MAP 4.1** — The AI system is assessed for alignment with organizational risk tolerances.
- **MAP 4.2** — The potential for the AI system to interact with or amplify other organizational risks — including cybersecurity, privacy, regulatory, and reputational risks — is assessed.

#### MAP 5 — Impacts
The likelihood and magnitude of potential impacts are documented.

Key subcategories:
- **MAP 5.1** — The likelihood and magnitude of each identified risk and impact are documented, considering both direct and indirect effects on individuals, groups, communities, and society.
- **MAP 5.2** — Practices are in place to prioritize risks based on assessed likelihood and impact, and to allocate risk management resources accordingly.

---

### FUNCTION 3: MEASURE

MEASURE deploys quantitative, qualitative, or mixed-method tools and techniques to analyze, assess, benchmark, and monitor AI risk and related impacts. Where MAP establishes the risk landscape, MEASURE produces evidence — metrics, evaluations, test results, audit findings — that demonstrate whether trustworthiness characteristics are being achieved. MEASURE has **4 categories:**

#### MEASURE 1 — Appropriate Methods Identified
The appropriate methods and metrics for measuring AI risks are identified, based on the system context established in MAP.

Key subcategories:
- **MEASURE 1.1** — Approaches and metrics for measuring the trustworthiness characteristics are selected and documented, appropriate to the system's context of use, domain, and risk level.
- **MEASURE 1.2** — Approaches for assessing the adequacy of existing risk measurement methods are defined. Where reliable measurement methods do not exist, this is documented and alternative risk management approaches are identified.
- **MEASURE 1.3** — Internal experts and external subject matter experts are engaged as needed to assess the appropriateness of selected metrics and measurement approaches.

#### MEASURE 2 — Measurement Executed
Systematic and validated approaches are used to evaluate risks and trustworthiness characteristics.

Key subcategories:
- **MEASURE 2.1** — Test, evaluation, verification, and validation (TEVV) activities are conducted throughout the AI lifecycle, not just at deployment.
- **MEASURE 2.2** — Evaluations include disaggregated analyses across relevant subgroups — ensuring that aggregate performance metrics do not obscure disparate impacts on specific groups.
- **MEASURE 2.3** — Risks associated with third-party AI components are evaluated as part of the overall risk assessment.
- **MEASURE 2.4** — The scientific basis for claims made about the AI system's performance, safety, and fairness is documented and verifiable.
- **MEASURE 2.5** — Adversarial testing (red-teaming) is conducted to identify failure modes and vulnerabilities not apparent in standard evaluation.
- **MEASURE 2.6** — Data quality, provenance, and representativeness are assessed.
- **MEASURE 2.7** — Privacy risks are evaluated, including potential for re-identification, data leakage, and unintended inference from model outputs.
- **MEASURE 2.8** — Security vulnerabilities specific to AI systems — including adversarial inputs, model inversion, and data poisoning — are identified and evaluated.
- **MEASURE 2.9** — Human-AI interaction risks are evaluated, including automation bias, misinterpretation of AI outputs, and failure of human oversight.
- **MEASURE 2.10** — Explainability and interpretability are evaluated relative to the needs of the intended audience.
- **MEASURE 2.11** — Fairness and bias are evaluated using appropriate metrics, with results disaggregated across relevant demographic and social groups.
- **MEASURE 2.12** — Environmental impacts — including energy consumption during training and inference — are evaluated.
- **MEASURE 2.13** — The results of all evaluations are documented in a form suitable for audit and review.

#### MEASURE 3 — Continuous Monitoring
Identified AI risks are monitored over time on a regular cadence and in response to known changes.

Key subcategories:
- **MEASURE 3.1** — Mechanisms for ongoing monitoring of AI system performance, behavior, and risk indicators are in place post-deployment.
- **MEASURE 3.2** — Changes in deployment context, user population, data distribution, or regulatory environment that could affect risk are tracked and trigger reassessment.
- **MEASURE 3.3** — Monitoring data is regularly reviewed and findings are fed back into MANAGE function activities.

#### MEASURE 4 — Findings Communicated
Measurement results are communicated to relevant AI actors.

Key subcategories:
- **MEASURE 4.1** — Findings from risk measurement activities are documented and communicated to relevant AI actors — including leadership, deployers, operators, and affected stakeholders — in a timely manner and in appropriate formats.
- **MEASURE 4.2** — Residual risks (risks remaining after risk treatment) are documented and disclosed to end users and deployers.

---

### FUNCTION 4: MANAGE

MANAGE deploys risk treatments, responds to identified incidents, and ensures that risk management is operationalized across the AI lifecycle. It translates the risk awareness created by MAP and MEASURE into action. MANAGE has **4 categories:**

#### MANAGE 1 — Risk Treatment
Risks are prioritized based on their likelihood and magnitude, and treatment plans are developed and implemented.

Key subcategories:
- **MANAGE 1.1** — Documented AI risk treatments — including risk avoidance, mitigation, transfer, and acceptance — are applied based on assessed risk level and organizational risk tolerance.
- **MANAGE 1.2** — Risk treatment plans are documented, assigned to responsible AI actors, and tracked through implementation.
- **MANAGE 1.3** — Residual risks that remain after treatment are documented, reviewed by appropriate organizational leadership, and disclosed as appropriate.
- **MANAGE 1.4** — Risk prioritization takes into account impacts on the most vulnerable or marginalized groups — not only aggregate likelihood and magnitude.

#### MANAGE 2 — Strategies Maintained
Strategies for addressing AI risks and potential impacts are maintained and improved over the AI lifecycle.

Key subcategories:
- **MANAGE 2.1** — Risk treatment strategies are regularly reviewed and updated to reflect changes in the AI system, deployment context, and risk landscape.
- **MANAGE 2.2** — Lessons learned from incidents, near-misses, and monitoring data are incorporated into updated risk treatment strategies.
- **MANAGE 2.3** — AI systems operating in high-risk domains are subject to enhanced ongoing scrutiny, with more frequent review cycles.

#### MANAGE 3 — AI Risks from Third Parties
AI risks arising from third-party entities in the AI supply chain are managed.

Key subcategories:
- **MANAGE 3.1** — Risks from third-party AI models, datasets, tools, and APIs are actively managed throughout the deployment lifecycle, not just at initial procurement.
- **MANAGE 3.2** — Incident response plans address failure scenarios involving third-party AI components, including model degradation, API unavailability, and supply chain integrity failures.

#### MANAGE 4 — Post-deployment Operations
AI risks are managed on an ongoing basis after deployment, including monitoring, incident response, and decommissioning.

Key subcategories:
- **MANAGE 4.1** — Post-deployment monitoring mechanisms are in place and actively used, with human oversight of monitoring processes.
- **MANAGE 4.2** — Mechanisms are in place for end users and affected individuals to appeal or seek review of AI-driven decisions.
- **MANAGE 4.3** — Incident response plans are in place for AI failures, including procedures for detecting incidents, assessing impact, notifying affected parties, and remediating harms.
- **MANAGE 4.4** — AI systems are decommissioned in a structured, documented, and safe manner when they are retired, replaced, or found to pose unacceptable risk.
- **MANAGE 4.5** — Change management processes ensure that modifications to AI systems (model updates, data changes, deployment context changes) trigger appropriate re-evaluation of risk.

---

## 6. AI RMF Profiles

A **Profile** is an implementation of the AI RMF Core functions, categories, and subcategories for a specific setting, application, or technology. Profiles tailor the framework to sector-specific regulatory requirements, risk tolerances, and use cases. Two official profiles have been published as of May 2026:

### 6.1 Generative AI Profile (NIST AI 600-1)
Released 26 July 2024, the Generative AI Profile addresses the unique risks posed by large language models, image generators, code generation systems, and other generative AI technologies. It identifies **12 unique risk categories** specific to generative AI:

1. **CBRN Information** — Risk of providing information that could enable creation of chemical, biological, radiological, or nuclear weapons.
2. **Confabulation** — The production of convincing but factually incorrect outputs (hallucinations).
3. **Data Privacy** — Memorization of private training data and potential disclosure through model outputs.
4. **Environmental** — Energy and resource consumption associated with training and inference at scale.
5. **Human-AI Configuration** — Misalignment between user expectations and actual system capabilities, including anthropomorphization.
6. **Information Integrity** — Generation of disinformation, synthetic media, and content designed to deceive.
7. **Information Security** — Vulnerabilities exploitable through AI systems, including prompt injection and jailbreaks.
8. **Intellectual Property** — Risks related to training on copyrighted data and generating potentially infringing content.
9. **Obscene, Degrading, and Abusive Content (NCII)** — Generation of non-consensual intimate imagery and other harmful content.
10. **Operational and Legal** — Legal exposure from AI outputs used in professional, medical, or legal contexts without appropriate human review.
11. **Societal** — Broader impacts on employment, democratic processes, and social trust from widespread generative AI use.
12. **Value Chain and Component** — Risks from the complex supply chains underlying generative AI systems.

For each risk, the profile maps suggested actions into the GOVERN, MAP, MEASURE, and MANAGE functions — providing over 200 specific actions for generative AI risk management.

### 6.2 Critical Infrastructure AI Profile (Concept Note, April 2026)
Released as a concept note on 7 April 2026, this profile is under development to guide critical infrastructure operators — covering information technology (IT), operational technology (OT), and industrial control systems (ICS) — in applying the AI RMF to AI deployments in high-stakes environments including energy, water, transportation, communications, and healthcare. The profile focuses on the specific trust requirements of critical infrastructure: enhanced safety, security, reliability, and availability, and addresses AI agents and autonomous systems operating in these environments. Stakeholder input is being gathered through 2026, with a draft profile expected later that year.

---

## 7. Companion Resources

### 7.1 The AI RMF Playbook
The Playbook is the operational companion to the AI RMF Core. For each subcategory in GOVERN, MAP, MEASURE, and MANAGE, it provides specific suggested actions that organizations can take to achieve the outcomes described in the framework. The Playbook is:

- **Non-prescriptive.** It is not a checklist to be completed in sequence. Organizations select suggested actions relevant to their sector, use case, and maturity.
- **Living.** It is updated approximately twice per year as AI technology, risk landscapes, and organizational practices evolve.
- **Downloadable.** Available in PDF, CSV, Excel, and JSON formats at https://airc.nist.gov/airmf-resources/playbook/

### 7.2 AI Resource Center (AIRC)
Launched 30 March 2023 at https://airc.nist.gov, the AIRC is the central hub for all AI RMF resources. It hosts the Playbook, framework documentation, use case examples, crosswalk documents, a glossary, and technical reports. It also facilitates international alignment by hosting crosswalks to international standards.

### 7.3 Crosswalk Documents
NIST publishes formal crosswalk documents mapping the AI RMF to other major frameworks, enabling organizations to demonstrate multi-framework alignment without duplicating evidence. Published crosswalks include:

| Framework | Direction |
|---|---|
| ISO/IEC 42001 | AI RMF ↔ ISO 42001 controls |
| ISO/IEC 23894 | AI RMF ↔ ISO AI risk management |
| EU AI Act | AI RMF functions ↔ EU AI Act obligations |
| OECD AI Principles | AI RMF trustworthiness characteristics ↔ OECD principles |
| CSA AICM (August 2025) | AICM ↔ NIST AI 600-1 mapping |

---

## 8. Risk Concepts and Terminology

Understanding how the AI RMF uses key terms is essential for correct implementation:

| Term | AI RMF Definition |
|---|---|
| **Risk** | Composite measure of the probability of an event occurring and the magnitude of its consequences. |
| **Risk tolerance** | An organization's or AI actor's readiness to bear risk in pursuit of its objectives. Not prescribed by the AI RMF — defined by the organization. |
| **Residual risk** | Risk remaining after risk treatment has been applied. Must be documented and disclosed. |
| **AI actor** | Any person or organization playing an active role in the AI lifecycle (developers, deployers, evaluators, end users, affected communities). |
| **TEVV** | Test, Evaluation, Verification, and Validation — a continuous process spanning the AI lifecycle. |
| **Profile** | An implementation of the AI RMF tailored to a specific sector, use case, or technology (e.g., Generative AI Profile). |
| **Current Profile** | A description of how an organization currently manages AI risk. |
| **Target Profile** | A description of the AI risk management outcomes an organization aims to achieve. |
| **Gap Analysis** | Comparison of current profile to target profile, used to prioritize risk management improvements. |

---

## 9. Implementation Approach

### Phase 1: Establish Governance Foundation (GOVERN)
Before assessing or managing any specific AI system, establish the organizational governance infrastructure:

1. Map existing organizational risk management structures and identify where AI governance needs to connect.
2. Define and document AI risk tolerance thresholds appropriate to your sector and stakeholder context.
3. Assign roles and responsibilities for AI risk management — including executive sponsorship, a designated AI risk function, and AI actor accountability structures.
4. Inventory legal and regulatory requirements applicable to your AI use cases.
5. Establish policies for AI supply chain due diligence, third-party model use, and data governance.
6. Create mechanisms for stakeholder engagement and incident reporting.

### Phase 2: Build a Current Profile (MAP)
For each AI system or class of AI systems in scope:

1. Document intended purpose, deployment environment, and key stakeholders.
2. Identify all relevant AI actors across the lifecycle.
3. Assess and document potential harms — to individuals, groups, communities, and society — across the seven trustworthiness dimensions.
4. Classify the AI system's risk level based on assessed likelihood and magnitude of harm.
5. Document data provenance, quality, and known limitations.
6. Make an initial go/no-go decision based on the risk assessment.

### Phase 3: Measure and Evaluate (MEASURE)
Design and execute a measurement program:

1. Select metrics appropriate to the system's context, risk level, and trustworthiness priorities.
2. Conduct pre-deployment TEVV across all seven trustworthiness characteristics.
3. Perform disaggregated evaluations across relevant subgroups.
4. Conduct adversarial testing (red-teaming) for high-risk or high-impact systems.
5. Document and disclose residual risks.
6. Establish baselines for continuous post-deployment monitoring.

### Phase 4: Treat and Monitor (MANAGE)
1. Develop and implement risk treatment plans proportional to assessed risk levels.
2. Deploy post-deployment monitoring systems and define threshold conditions that trigger reassessment.
3. Establish incident response procedures for AI-specific failure modes.
4. Create appeal and redress mechanisms for affected individuals.
5. Plan and document decommissioning procedures.
6. Conduct regular review cycles (at minimum annually; more frequently for high-risk systems).

### Phase 5: Build a Target Profile and Close Gaps
1. Define the Target Profile — the desired risk management state for each AI system.
2. Conduct gap analysis between current and target states.
3. Prioritize improvements based on risk level, regulatory requirements, and available resources.
4. Track progress and report to organizational leadership.

---

## 10. Regulatory Integration and Enforcement Context

The AI RMF is voluntary but it operates in an increasingly mandatory regulatory environment. Organizations implementing the AI RMF can use it as evidence of due diligence in the following contexts:

**U.S. Federal Contracting.** Federal agencies increasingly require NIST AI RMF alignment in AI procurement. Contractors deploying AI in federal contexts should treat AI RMF compliance as a de facto requirement.

**Sector Regulation.** The FTC (consumer protection), FDA (medical AI), SEC (financial AI), CFPB (credit and lending AI), EEOC (employment AI), and FAA (aviation AI) all reference AI RMF principles in their enforcement expectations or guidance documents. Demonstrating AI RMF alignment strengthens the position of organizations facing regulatory scrutiny in these sectors.

**EU AI Act.** The AI RMF functions map directly to EU AI Act conformity assessment requirements for high-risk systems. Organizations using the AI RMF already have much of the evidence base needed for EU AI Act compliance — particularly technical documentation, risk assessments, data governance records, and human oversight procedures.

**ISO/IEC 42001.** The AI RMF's GOVERN function maps closely to ISO 42001's management system requirements. Organizations seeking ISO 42001 certification can use their AI RMF implementation as a foundation, using published NIST crosswalks to identify gaps.

**State AI Laws.** Several U.S. states (including Colorado, Texas, and California) have enacted or proposed AI laws that reference NIST AI RMF alignment as a compliance pathway or safe harbor consideration. A December 2025 Executive Order asserting federal primacy over state AI laws is under legal challenge, so state-level requirements remain relevant.

---

## 11. Current State and Roadmap (as of May 2026)

| Item | Status |
|---|---|
| AI RMF 1.0 | Published January 2023; current version |
| NIST AI 600-1 (GenAI Profile) | Published July 2024; operational |
| Critical Infrastructure Profile | Concept note released April 2026; stakeholder input underway |
| SP 800-53 Control Overlays for AI (COSAIS) | Concept paper released; first public draft expected late 2026 |
| AI RMF Playbook | Living document; updated ~twice per year |
| AI RMF 1.1 or 2.0 | No confirmed timeline; formal community review required before 2028 |
| AI Standards Evaluation Report | Released January 2026 (GCR-26-069) |
| Center for AI Standards and Innovation (CAISI) | Formerly US AISI; ~290 member organizations; closed to new members as of mid-2025 |
| International alignment | Crosswalks published to ISO 42001, ISO 23894, OECD Principles, EU AI Act, CSA AICM |

---

## 12. Key Documents and Links

| Resource | URL |
|---|---|
| AI RMF 1.0 (PDF) | https://nvlpubs.nist.gov/nistpubs/ai/NIST.AI.100-1.pdf |
| NIST AI 600-1 GenAI Profile (PDF) | https://nvlpubs.nist.gov/nistpubs/ai/NIST.AI.600-1.pdf |
| AI Resource Center (AIRC) | https://airc.nist.gov |
| AI RMF Playbook | https://airc.nist.gov/airmf-resources/playbook/ |
| Crosswalk Documents | https://airc.nist.gov/airmf-resources/crosswalks/ |
| Critical Infrastructure Profile Concept Note | https://www.nist.gov/programs-projects/concept-note-ai-rmf-profile-trustworthy-ai-critical-infrastructure |
| AI RMF Roadmap | https://airc.nist.gov/airmf-resources/roadmap/ |
| AIRC Use Cases | https://airc.nist.gov/airmf-resources/usecases/ |
| NIST AI Standards page | https://www.nist.gov/artificial-intelligence/ai-standards |
| Contact | aiframework@nist.gov |