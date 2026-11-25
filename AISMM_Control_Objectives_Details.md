# CSA AI Security Maturity Model (AISMM)
## Control Objectives — Version 0.9
### Cloud Security Alliance | 2026

---

## About this document

This document presents the per-category Control Objectives for the CSA AI Security Maturity Model (AISMM). Each category contains 1–3 Key Performance Indicator (KPI) Control Objectives per maturity level, designed to indicate where an enterprise AI security program sits on the path from L1 (Initial) to L5 (Efficient).

AISMM Control Objectives are *representative* KPIs, not comprehensive controls. An organization meeting a KPI likely has the broader maturity of that level because they could not meet the KPI otherwise. Some objectives describe security states below a desired final posture but help discriminate between maturity levels.

Cross-category dependencies are guidance, not strict gates. Organizations have uneven maturity across categories; the model describes the path, not a fixed sequence.

This document is created with the assistance of AI to keep it aligned with the main AI Security Maturity Model spreadsheet and has undergone human review and edits.

### Conventions

- **ID format:** `{PREFIX}-{LEVEL}.{NUMBER}`, e.g., `MOD-03.1`. Each prefix maps to a category (see Glossary entry "AISMM Categories").
- **Maturity levels:** L1 Initial, L2 Repeatable, L3 Defined, L4 Capable, L5 Efficient. No KPIs at L1 (the starting point).
- **Deployment Types:** All | Self-hosted | PaaS | API/SaaS | combination. Indicates which of the three deployment islands the KPI applies to.
- **Manual/Automated:** Automated = auto-assessable via tooling; Manual = requires human review; Either = both possible.
- **AICM mapping:** Cross-reference to the CSA AI Controls Matrix (AICM) where applicable.
- **External references:** OWASP LLM/ASI, NIST AI RMF, ISO/IEC 42001, and other framework cross-references.
- **Key Indicator Rationale:** One-sentence explanation of why an organization meeting this KPI likely has the broader level maturity.
- **Description:** Deeper context, examples, rationale for thresholds, and clarifying scope notes.
- **Evidence:** What an assessor looks at to verify the KPI.

---

## Table of Contents

1. [Governance (GOV)](#1-governance)
2. [Organization Management (ORG)](#2-organization-management)
3. [IAM (IAM)](#3-iam)
4. [Security Monitoring (MON)](#4-security-monitoring)
5. [Infrastructure Security and Resilience (INF)](#5-infrastructure-security-and-resilience)
6. [Model Security (MOD)](#6-model-security)
7. [Application Security (APP)](#7-application-security)
8. [Data Security (DAT)](#8-data-security)
9. [Risk and Provider Assessment & Management (RSK)](#9-risk-and-provider-assessment-and-management)
10. [AI Supported Development and Supply Chain Security (DEV)](#10-ai-supported-development-and-supply-chain-security)
11. [Privacy, Compliance and Audit (CMP)](#11-privacy-compliance-and-audit)
12. [Incident Response (IR)](#12-incident-response)
13. [Glossary](#glossary)

---

## 1. Governance (GOV) <a id="1-governance"></a>

**Category description:** Enterprise governance of artificial intelligence — the policies, decision rights, approval authorities, and safety/ethics framework that set the rules every other AISMM category executes against. Includes the authoritative registries of approved AI use cases, applications, models, providers, agents, and MCP tools; the AI Council / Center of Excellence / equivalent body that issues standards; enterprise-wide AI acceptable use and role-based training; and the ethics/safety review process for high-risk AI use cases. Technical enforcement of governance decisions (AWS SCPs, Azure Policy, GCP Org Policy, AI-SPM, AI-BOM discovery) lives in Organization Management. Assessment of external AI providers and AI projects for risk lives in Risk & Provider Assessment.


---

### Level descriptors (reference — from AISMM main grid)

- **L1 Initial:** No coordinated AI governance. Teams self-manage AI usage with self-selected tools and providers. No AI-specific policies, procedures, or safety/ethics guidance.
- **L2 Repeatable:** Initial AI usage policies established with basic guidance (e.g., "do not share sensitive enterprise or customer data with generative AI"). No AI-specific governance structures or designated management in place. Policies include high-level safety/ethics statements. Some AI-related procedures documented but not consistently followed across the organization.
- **L3 Defined:** AI team, AI Council, AI Center of Excellence, or equivalent in place to guide usage. Initial AI policies in use for AI-supported development, AI-powered applications, or both. Basic adoption of procedures, standards and benchmarks (e.g., AICM). Partial control objectives established for at least one provider. AI deployment/application registry in place. General AI safety guidelines established.
- **L4 Capable:** Central AI team has subject matter experts for current AI models/providers and responsibility and authority to set rules/baselines. Developer policies for AI usage in place with training. AI security control objectives for AI-supported development and applications in use, with initial automated tracking. AI safety policies established for different use cases. Cross-functional AI ethics/safety review process for high-risk use cases.
- **L5 Efficient:** Governance is monitored and managed using automated tooling (models/provider version compliance, guardrails coverage, agent/MCP registries). Defined process to update control objectives/specifications as AI providers and tools add/modify services and release new models. AI ethics review board in place with enforcement authority.

---

### Scope note — GOV / ORG, GOV / RSK, and GOV / CMP boundaries

Governance KPIs test the existence, authority, and output of the enterprise AI governance function: does a published AI acceptable use policy exist, does the AI Council or equivalent body actually issue standards and approval decisions that downstream teams follow, are the AI use-case / application / agent registries authoritative sources of truth, and does an ethics/safety review process produce documented dispositions on high-risk use cases? The technical enforcement of those decisions — cloud-provider organization policies restricting model endpoints, AI-SPM discovery of deployed AI, account/subscription blast-radius isolation — belongs in Organization Management (ORG). The evaluation of specific AI providers and AI projects against risk criteria — provider registry with risk ratings, PIAs, reassessment cadence on provider changes — belongs in Risk & Provider Assessment (RSK). GOV sets the rules and records the approval decisions; ORG enforces those decisions technically; RSK assesses providers and projects against the rules GOV set. Enterprise AI training and role-based awareness programs live in GOV as the natural policy home. GOV / CMP carve-out: GOV owns policy authorship (writing the AI acceptable use policy, the Council standards, the role-based training curriculum); CMP owns assessor verification of compliance evidence (audit trails proving the policy is being followed in regulated contexts, third-party attestations, regulatory mapping artifacts).

---

### Level 2 — Repeatable

#### GOV-02.1 — Enterprise AI acceptable use policy with signed personnel attestation

- **Deployment Types:** All
- **Manual/Automated:** Manual
- **AICM Mapping:** HRS-15 (AI acceptable use), GRC-09 (acceptable use of AI service), HRS-02 (acceptable use of technology)
- **External References:** NIST AI RMF Govern 1.1; ISO/IEC 42001 AI management system policy requirements
- **Key Indicator Rationale:** An organization that has published a version-controlled AI acceptable use policy and achieved at least 90% signed-attestation coverage across its workforce has moved past L1 shadow-AI adoption into L2 repeatable baseline. The signal is not that a policy exists in a document library — it is that every employee has seen it, attested to it, and therefore has no deniability about the enterprise AI ground rules.

**Control Objective:** Every employee and contractor with system access has reviewed and assigned the organization's AI policies, which include which AI tools are permitted, what data classifications can go into each, what use cases are prohibited, and how to report incidents or request exceptions.

**Description:** The L2 bar is concrete ground rules plus evidence every employee has acknowledged them. The published AI acceptable use policy enumerates approved tools (named or by class), data classifications permitted per tool class, prohibited use cases, a high-level safety and ethics statement, and the reporting path for suspected incidents or exceptions. It is signed off by a named executive, carries a version number and effective date, and at least 90% of the workforce (employees plus contractors with system access) has recorded a signed attestation within the trailing 12 months. The policy does not need an AI Council behind it, does not need automated enforcement, and does not need role-specific detail — those are L3 and L4 moves. What it does need is enumerated allowed tools rather than "approved AI tools" (which at L2 is usually a short list: the organization's Microsoft 365 Copilot or Google Workspace AI tenant, the enterprise ChatGPT or Claude for Work subscription if one exists, and explicitly nothing else for work content), data-class rules that a line employee can apply without asking ("your draft customer email can go in the enterprise AI tenant, customer SSNs never go in any AI tool"), and the boundary between approved enterprise AI and personal / consumer AI use for work. The 90% attestation threshold is the hygiene signal: an organization with a policy that 60% of the workforce has signed is still at L1 in practice. Contractor inclusion matters because contractors are a common shadow-AI vector.

**Evidence:**
- Published AI acceptable use policy with version, effective date, and named executive approver
- Attestation report from the learning management or identity platform showing 90%+ signed coverage across employees and contractors with system access over the trailing 12 months
- Policy entry in the organization's policy register showing owner, review cadence, and next review date
- Documented reporting path for AI incidents or exception requests (ticket queue, mailbox, form) with a named owner

#### GOV-02.2 — Named approval authority for enterprise AI procurement and major deployments

- **Deployment Types:** All
- **Manual/Automated:** Manual
- **AICM Mapping:** GRC-06 (governance responsibility model), GRC-09 (acceptable use of AI service)
- **External References:** NIST AI RMF Govern 2.1 (roles, responsibilities, accountability)
- **Key Indicator Rationale:** A documented approval authority with signed decision records for the last several AI procurement and deployment decisions shows the organization has moved past the L1 state where teams adopt providers unilaterally. It does not require the full L3 AI Council structure, but it does require that someone with named accountability has actually made and recorded recent decisions — a property that is measurable on an assessor visit.

**Control Objective:** A named approval authority makes and records yes/no decisions before new AI providers are contracted or AI-powered applications ship to production. Teams are not allowed to adopt new AI products or use cases without approval.

**Description:** The organization documents a named approval authority (individual role or functional body) for enterprise AI procurement and production deployment of AI-powered applications, with written scope, decision thresholds, and escalation path. Signed decision records exist for at least five procurement or deployment decisions in the trailing 12 months, each showing requester, decision date, approver, outcome (approved / approved with conditions / denied), and scope, with at least one outcome other than "approved as submitted." At L2 the organization has not yet stood up an AI Council or Center of Excellence — that is the L3 state. But it has identified that someone needs to say yes or no before a new AI provider gets a contract or a new AI-powered application ships to production, and it has recorded that someone saying yes or no. The approval authority at L2 is typically an existing function pressed into AI duty: the security architecture review board reviewing Copilot rollout, procurement approving the Anthropic enterprise contract, the CIO signing off on the Salesforce Agentforce deployment. The five-decision threshold is the minimum signal that the process is actually used rather than theoretical. Decisions that were made outside this path and then backfilled as records do not count — the record must show the approval preceded the procurement or deployment, or include a documented retroactive exception with a remediation plan.

**Evidence:**
- Written approval authority document naming the role or body, scope of decisions, thresholds, and escalation path
- Five or more signed decision records from the trailing 12 months covering procurement or production deployment of AI, each with requester, date, approver, outcome, and scope
- Sample decision record showing traceability from request through approval to the resulting contract, purchase order, or production go-live
- List of AI providers and AI-powered applications with their approval record cross-referenced

---

### Level 3 — Defined

#### GOV-03.1 — AI Council issues and maintains a catalog of approved use cases with provider and data type mappings

- **Deployment Types:** All
- **Manual/Automated:** Manual
- **AICM Mapping:** GRC-01 (governance program policy), GRC-06 (governance responsibility model), GRC-09 (acceptable use of AI service)
- **External References:** NIST AI RMF Govern 1.2, Govern 2.1; ISO/IEC 42001 Clause 5 (leadership) and Annex A.6 (AI system life cycle)
- **Key Indicator Rationale:** An AI Council that exists on an org chart is an L2 structural claim; an AI Council that publishes and maintains a catalog of approved AI use cases with dated decision records is the L3 signal that the Council is actually making and owning decisions. Downstream categories (MOD approved-model registry, APP production AI applications, RSK provider assessments) anchor to this catalog, so its presence and freshness prove the governance function is producing the artifacts those categories need.

**Control Objective:** A cross-functional AI Council (or equivalent body) publishes a catalog of approved AI use cases, mapped to approved AI providers/technologies and data types. Use cases include examples like AI coding tools, customer service agents, AI data analytics platforms. These map to specific providers and which data types are allowed per use case and provider (e.g. PII).

**Description:** The Council, Governance Board, Center of Excellence, or named equivalent has cross-functional membership (minimum: security, legal or privacy, IT / platform, and at least one business representative) and publishes an approved-AI-use-case catalog. Each entry names the use case, approved tool classes or providers, approved data classifications, owning function, risk tier (low / medium / high), and decision record (date, members present, outcome). The Council meets at least quarterly with published minutes. In the trailing 12 months, the catalog has been updated at least twice with at least one entry modified or retired (not just additions) and at least one decision outcome other than "approved as submitted" (denial, deferral, or approval with conditions). At least 80% of production AI deployments in the GOV-03.2 registry map to a catalog entry. The approved-use-case catalog is the artifact that makes the AI Council measurable. An L3 Council is not a committee that meets to hear updates — it is a body that issues decisions and the catalog is where those decisions land. Use-case entries should read like "marketing content drafting in Microsoft 365 Copilot, internal data only, low risk, owned by Marketing Ops" or "customer-facing support chatbot on approved LLMs with guardrails, confidential customer data permitted under privacy controls, high risk, owned by Customer Service, AI Council decision 2026-02-14." The 80% mapping threshold means the catalog is the authoritative source — not a wishlist of approved patterns while actual production deployments run outside it. The quarterly cadence is the minimum realistic rhythm; many organizations run monthly once the function matures. Membership composition matters because an AI Council composed only of IT or only of security produces decisions that get ignored by the business — the L3 signal is that the body has the cross-functional legitimacy to make binding decisions. The modified-or-retired-entry and non-approval-outcome requirements are the anti-rubber-stamp signals: a catalog that only grows and a Council that only approves are not exercising judgment.

**Evidence:**
- AI Council charter naming the body, membership roles, decision scope, and meeting cadence
- Approved-use-case catalog with entries showing use case, approved tools, data classifications, risk tier, owner, and decision record
- AI Council meeting minutes for the trailing 12 months showing at least four meetings and catalog updates
- Reconciliation report showing 80%+ of production AI applications in the GOV-03.2 registry map to a catalog entry
- Sample high-risk use-case entry showing full decision trail from request through Council deliberation to approval with conditions

#### GOV-03.2 — Authoritative AI deployment and application registry

- **Deployment Types:** All
- **Manual/Automated:** Either
- **AICM Mapping:** GRC-05 (information security program scope), GRC-01 (governance program policy)
- **External References:** NIST AI RMF Map 1.1 (AI system context); ISO/IEC 42001 Annex A.6.2 (AI system inventory)
- **Key Indicator Rationale:** A single authoritative registry of enterprise AI tools, AI-powered applications, agent deployments, and MCP integrations — cross-referenced from the approved-use-case catalog and referenced by downstream categories — is the L3 defined signal. An L2 organization has scattered spreadsheets; an L3 organization has one canonical source the Council maintains and other categories anchor to.

**Control Objective:** The AI Council maintains an authoritative registry of AI deployments and applications, with each entry linked to the approved use case it serves under GOV-03.1, the owning team, and the underlying models, agents, and MCP integrations in use. The registry is the canonical record of what AI runs under what approval.

**Description:** Each registry entry records deployment ID, type (tool / application / agent / MCP), owning team, data classifications handled, production status, approval cross-reference to the AI Council decision (GOV-03.1), and last-reviewed date. The registry is named authoritative in the AI Council charter, and downstream categories (MOD, RSK, DEV AI-BOM, ORG enforcement scope) trace to its identifiers. Coverage reconciles against AI-SPM or equivalent discovery with no more than 15% of observed deployments unreconciled. The L2 state was scattered decision records; the L3 state is a curated inventory that every downstream function points at. The registry does not need to be a purpose-built AI-SPM product at L3 — a maintained spreadsheet, ServiceNow CMDB extension, or Airtable base is acceptable as long as it is named authoritative and used as such. Where a dedicated AI-SPM product exists it provides the discovery feed; registry curation (owner assignment, approval cross-reference, decommissioning of retired entries) stays a human activity at L3 and gets automated into workflow at L4 and L5. The 15% reconciliation slack at L3 acknowledges that enterprise AI inventory is a moving target: new Copilot licenses, experimental apps, and SaaS vendors adding AI features all create churn. Tightening this threshold is an L4+ expectation, coordinated with ORG's discovery controls.

**Evidence:**
- Registry export showing entries for enterprise AI tools, AI-powered applications, agents, and MCP integrations with the required fields
- AI Council charter or governance policy language naming the registry as the authoritative source
- Cross-reference sample showing MOD approved-model registry entries, RSK provider registry entries, or DEV AI-BOM entries tracing back to GOV-03.2 registry identifiers
- Reconciliation report comparing registry to AI-SPM or equivalent discovery telemetry showing <=15% unreconciled observed deployments
- Registry review log showing entries added, modified, or retired with review dates in the trailing 12 months

#### GOV-03.3 — Role-based AI training with measured completion

- **Deployment Types:** All
- **Manual/Automated:** Automated
- **AICM Mapping:** HRS-14 (AI competency training), HRS-11 (security awareness training), HRS-15 (AI acceptable use)
- **External References:** NIST AI RMF Govern 3.2, Govern 6.2; ISO/IEC 42001 Clause 7.2 (competence) and Clause 7.3 (awareness)
- **Key Indicator Rationale:** Role-differentiated AI training with 85%+ completion and a 90-day onboarding SLA is measurable, enforced through the LMS, and not achievable if the governance function has not identified the at-risk roles and written actual content for them. An organization that can produce this set of numbers has moved past L2 generic acceptable-use attestation into the L3 defined state where different populations get different AI guidance.

**Control Objective:** Employees receive AI training aligned with their job role. E.g. a baseline for everyone, a developer track for those using coding assistants or building AI applications, and a high-risk-role track for functions whose AI use affects customer, employee, or regulated decisions. Completion is tracked.

**Description:** Training is differentiated into three modules: a baseline module for all workforce members; a developer module for anyone using AI coding assistants or building AI-powered applications; and a high-risk-role module for legal, HR, customer service, privacy, and other functions. Trailing-12-month completion is at least 85% per role cohort (minimum cohort size 10), and at least 90% of new hires in scope complete onboarding training within 90 days of start. Small-org alternative: cohorts under 10 may use a role-mapping exception with executive sign-off, reviewed annually. L3 training is the first time the organization says "the marketing intern, the backend engineer, and the HR business partner need different AI training" and actually produces that content. The baseline module extends the L2 acceptable-use attestation into operational behavior — what does "do not put confidential data in AI tools" actually mean when the Copilot sidebar is open in Excel, how do you recognize hallucination in a research summary, how do you report a suspected AI incident. The developer module reflects that coding assistants are typically the highest-frequency AI exposure in the enterprise and deserve their own curriculum. The high-risk-role module handles functions where AI output gets used in decisions affecting people (HR screening, customer service escalations, legal review). The 85% completion bar and 90-day onboarding SLA are the L3 signals that training is operationalized rather than optional. Annual-refresh cadence, training-effectiveness measurement, and red-team-informed curriculum updates are L4+ moves.

**Evidence:**
- Training curriculum inventory showing baseline, developer, and high-risk-role modules with version and last-update dates
- LMS completion report showing 85%+ completion per cohort over the trailing 12 months
- New-hire onboarding completion report showing 90%+ compliance with the 90-day SLA
- Role-mapping definition showing how job codes or identity attributes drive cohort assignment
- Sample module outlines demonstrating that developer and high-risk-role content is genuinely differentiated from the baseline (not just the baseline with an extra slide)

---

### Level 4 — Capable

#### GOV-04.1 — AI Council issues written standards that downstream categories enforce

- **Deployment Types:** All
- **Manual/Automated:** Manual
- **AICM Mapping:** GRC-01 (governance program policy), GRC-06 (governance responsibility model), GRC-09 (acceptable use of AI service)
- **External References:** NIST AI RMF Govern 1.3, Govern 2.3; ISO/IEC 42001 Annex A.6 (AI system life cycle) and Annex A.9 (use of AI systems)
- **Key Indicator Rationale:** The L3→L4 distinguisher is traceability and propagation: downstream control descriptions cite GOV standards by name AND propagate updates within a 90-day SLA. Standards merely existing in a binder is an L3-or-below state; standards being the named authoritative source for at least three downstream categories with measurable update propagation is the program-output proof of L4 governance authority.

**Control Objective:** The AI Council adopts an enterprise standard based on an industry framework, such as the AICM, which is communicated and integrated into downstream requirements.

**Description:** The AI Council (or equivalent from GOV-03.1) publishes written enterprise AI security and safety standards covering at minimum approved model selection criteria, AI data handling by classification, agent and MCP tool usage baselines, and human-in-the-loop requirements by risk tier. Each standard is version-controlled, carries an effective date, and is cited by name as the authoritative source in at least three downstream category implementations (e.g., MOD, DAT, APP, RSK). When the Council updates a standard, downstream categories log the change and update controls within 90 days, with at least 90% compliance across the trailing four revisions. GOV-04.1 is the "AI Council actually has authority" KPI, and the test is traceability and propagation, not standards-exist. If the organization's approved-model registry lists selection criteria, those criteria should explicitly trace back to a Council-published standard cited by name and version — not to "team judgment" or unattributed convention. Similarly for data-classification-to-AI-tool mapping, agent baselines, and HITL requirements. The 90-day downstream-update SLA is the operational signal: when the Council revises a standard, downstream controls show a corresponding change-log entry and updated implementation within 90 days. A Council whose standards update but whose downstream controls take six months to catch up does not have working authority — the standards are decorative. The 90%-across-four-revisions threshold prevents the Council from declaring success on a single demonstration update. At L3 the Council approves use cases against unwritten or informal criteria; at L4 the criteria themselves are written, versioned, cited, and enforced through propagation.

**Evidence:**
- Published standards set (model selection, AI data handling, agent/MCP baselines, HITL requirements) each with version, effective date, and approver
- Citation map showing downstream category controls that reference each standard by name and version
- Change log for the trailing four standard revisions showing issuance date and downstream-control-update dates
- Compliance report showing at least 90% of downstream updates landed within 90 days of standard revision across the four revisions
- Sample traceability artifact: a MOD or DAT or APP control implementation whose documentation cites the GOV standard as its authoritative source

#### GOV-04.2 — Cross-functional ethics and safety review for high-risk AI use cases

- **Deployment Types:** All
- **Manual/Automated:** Manual
- **AICM Mapping:** GRC-10 (AI impact assessment), GRC-11 (bias and fairness assessment), GRC-12 (ethics committee), GRC-13 (explainability requirement), GRC-14 (explainability evaluation), GRC-15 (human supervision)
- **External References:** NIST AI RMF Govern 5.1, Measure 2.5, Manage 1.3; EU AI Act Article 9 (risk management system) and Article 14 (human oversight) concepts; ISO/IEC 42001 Annex A.5 (responsible use)
- **Key Indicator Rationale:** A cross-functional review process that produces written go / go-with-conditions / no-go dispositions for high-risk AI use cases before production deployment — with 100% pre-deployment coverage over 12 months — is not achievable without a standing body, written criteria, and enforcement that blocks production deployment of unreviewed high-risk use cases. An organization that can produce these records has the L4 cross-functional review process the main grid describes.

**Control Objective:** No high-risk AI use case reaches production without a cross-functional ethics and safety review that produces a written go / go-with-conditions / no-go disposition. This can be a function of the AI council.

**Description:** Every AI use case classified high-risk in the GOV-03.1 catalog undergoes a documented cross-functional ethics and safety review before production. The review covers at minimum an AI impact assessment (GRC-10), bias and fairness assessment where applicable (GRC-11), explainability determination (GRC-13), and human-oversight specification (GRC-15). Participants include at minimum security, legal or privacy, and a business owner, plus a fourth domain expert as the use case requires. Dispositions are go / go-with-conditions / no-go with written rationale and named reviewers. Over the trailing 12 months, 100% of high-risk use cases reaching production have a pre-deployment review record, and at least 25% result in go-with-conditions where the condition traces to a named, versioned GOV-04.1 standard with evidence of in-deployment enforcement (configuration, pipeline gate, monitoring rule, or runbook). High-risk use cases are defined in the AI Council catalog under GOV-03.1 — customer-affecting decisions, regulated contexts, use cases processing PHI / PII / financial data, autonomous agents with write access to production systems, generative content published under the organization's brand. The review is not a rubber-stamp: the 100% pre-deployment coverage is the binding threshold, and the 25% go-with-conditions rate (with conditions traceable to a GOV-04.1 standard and enforced in deployment) is the output signal that the review produces real changes rather than approvals dressed up as conditions. A review process that produces only go dispositions, or whose conditions are vague best-effort recommendations rather than enforceable links to a Council standard, is approving rather than reviewing. Linking conditions to GOV-04.1 standards also closes the loop on Council authority — the standards exist (GOV-04.1), and the ethics review uses them as the source of binding modifications (GOV-04.2). The AICM GRC-10 through GRC-15 controls provide the review content scope without being imported as process theater language. Ethics review board with enforcement authority (L5) extends this into a standing body that can halt deployments post-production; L4 is the pre-deployment gate with enforceable output.

**Evidence:**
- Review process definition naming participants, scope, criteria, and enforcement hook (production deployment does not proceed without review record)
- Review records for all high-risk use cases reaching production in the trailing 12 months, showing impact assessment, bias/fairness assessment, explainability determination, HITL specification, reviewers, disposition, and rationale
- Evidence of the enforcement hook (for example: deployment pipeline gate, change-management ticket requirement, AI Council catalog status field that blocks production)
- Trailing-12-month disposition summary showing at least 25% go-with-conditions rate among high-risk reviews, with each condition citing a specific GOV-04.1 standard (named and versioned) and evidence of in-deployment enforcement
- Sample review record for a high-risk production deployment showing full lifecycle from request through review through disposition to deployment, including the condition's implementation artifact (config, pipeline gate, monitoring rule, runbook)

#### GOV-04.3 — Executive / board AI risk-committee oversight with defined escalation triggers

- **Deployment Types:** All
- **Manual/Automated:** Manual
- **AICM Mapping:** GRC-06 (governance responsibility model), GRC-07 (information security committee), GRC-12 (ethics committee)
- **External References:** NIST AI RMF Govern 2.1, Govern 4.1; ISO/IEC 42001 Clause 5.1 (leadership and commitment), Clause 9.3 (management review)
- **Key Indicator Rationale:** An L3 program has an AI Council; an L4 program has executive or board-level oversight that the Council escalates to under defined triggers. This is level-discriminating because executive AI risk-committee oversight is distinct from the cross-functional working body — it adds a higher accountability layer that an L3 program does not have. The signal is a defined trigger list, documented escalations (or a documented zero-trigger justification with explicit review), and a reporting cadence the executive body actually keeps.

**Control Objective:** Executive and/or board members are actively engaged with the AI council, which includes regular reporting, review, and disposition of anything requiring executive/board feedback. Executive and/or board members sign off on any governance policies from the AI council.

**Description:** An executive or board-level AI risk committee (with executive authority distinct from the AI Council operational body) operates against a written escalation trigger list naming at minimum a material AI-related incident, a regulatory shift affecting the organization's AI use, and repeated high-risk go-with-conditions dispositions exceeding a defined threshold. Over the trailing 12 months, the committee receives reporting at least twice per year, and either (a) at least one escalation event is documented showing trigger fired, briefing, decisions, and follow-through, or (b) a zero-trigger justification is signed by the committee chair confirming no triggers fired and the trigger list was reviewed for currency. GOV-04.3 separates the cross-functional working AI Council (L3 / GOV-03.1) from the executive accountability layer (L4). At L3 the Council is empowered to make use-case decisions; at L4 the Council operates within an oversight envelope where executive leadership has explicit AI risk visibility and a defined trigger list for when Council decisions or AI-related events rise to executive attention. The L4 distinguisher is not "executives are aware of AI" — it is that the trigger list is written, the cadence is set, and either an escalation actually happened or the absence of escalations was deliberately reviewed (preventing the failure mode where a quiet 12 months means the function went dormant rather than that nothing went wrong). The committee may be an existing body (board risk committee, audit committee, executive risk council) extended to cover AI rather than a new standing committee — what matters is named authority, trigger list, reporting cadence, and documented review activity. L5 ethics review board with enforcement authority (GOV-05.2) adds in-flight enforcement teeth; GOV-04.3 establishes the executive accountability layer that L5 enforcement reports up to.

**Evidence:**
- Charter or governance policy naming the executive / board AI risk committee, its authority, and its relationship to the AI Council
- Written escalation trigger list with thresholds and routing
- Trailing-12-month committee meeting record showing at least two reporting events with materials, attendance, and decisions
- Either: at least one documented escalation event showing trigger, briefing, decisions, and follow-through; or a documented zero-trigger justification signed by the committee chair confirming no triggers fired and the trigger list was reviewed for currency
- Reporting-cadence documentation (calendar, charter clause, or governance policy) showing the cadence is committed rather than ad-hoc

---

### Level 5 — Efficient

#### GOV-05.1 — Automated governance evidence and exception lifecycle

- **Deployment Types:** All
- **Manual/Automated:** Automated
- **AICM Mapping:** GRC-01 (governance program policy), GRC-03 (organizational policy reviews), GRC-04 (policy exception process)
- **External References:** NIST AI RMF Govern 1.5, Manage 4.1; ISO/IEC 42001 Clause 9 (performance evaluation)
- **Key Indicator Rationale:** Automated governance telemetry — registry coverage, training completion, standards-to-downstream-compliance, approved-tool usage — reported on a published dashboard, plus a tracked policy-exception lifecycle with zero unexpired exceptions older than their approved duration, is the L5 "automated tooling" signal. Organizations that can show these numbers without hand-assembling them have the L5 operational rhythm.

**Control Objective:** Governance posture is visible on a live dashboard fed by source-system telemetry rather than hand-assembled, and policy exceptions move through a tracked lifecycle that closes or renews on schedule.

**Description:** The dashboard refreshes at least weekly with automated telemetry covering at minimum: GOV-03.2 registry coverage reconciled against AI-SPM or equivalent discovery; workforce and role-based training completion against GOV-03.3 thresholds; downstream category compliance with GOV-04.1 standards via auto-generated traceability map; and approved-tool usage vs. unapproved-AI signals from CASB / egress / DLP. Policy exceptions to any GOV control or AI Council standard are tracked in a central register with named requester, named approver, rationale, issuance date, expiration date (maximum 180 days standard; 365 days with executive risk committee sign-off), and remediation plan. Exceptions on the 365-day track receive a documented quarterly review checkpoint. Over the trailing 90 days, zero exceptions remain active past expiration and at least 95% of expiring exceptions are explicitly closed or renewed with a new approval record. GOV-05.1 is the difference between a governance program that reports via quarterly slide deck (L4) and one that reports via live dashboard (L5). The automation target is not glossy visualization — it is that the numbers are pulled from source systems (AI-SPM, LMS, CASB, downstream-category control registries) rather than typed into a spreadsheet by an AI Council administrator. The exception-lifecycle piece is equally important: the weakness governance programs develop at scale is that exceptions pile up, never close, and become de facto policy. The 180-day standard-exception cap, 365-day executive-approved cap, zero-past-expiration threshold, and 95% explicit-renewal rate are the measurable signals that exceptions stay exceptional. The quarterly review checkpoint on 365-day-track exceptions specifically prevents the "expires in 11 months and never gets re-examined" failure mode — long-running exceptions are revisited four times during their lifetime, not just at issuance and expiration. Ethics review board with enforcement authority extends this model by providing a body that can force-close exceptions or halt deployments even post-production — covered in GOV-05.2.

**Evidence:**
- Governance dashboard showing registry coverage, training completion, standards-to-downstream compliance, and approved-tool usage metrics with automated data-source connections and refresh timestamps
- Data-pipeline definitions showing automated pulls from AI-SPM, LMS, downstream control metadata, and CASB/egress/DLP telemetry
- Exception register showing all active and recently-closed exceptions with the required fields
- 90-day exception audit showing zero exceptions past expiration and at least 95% of expiring exceptions explicitly closed or renewed
- Quarterly review log for 365-day-track exceptions showing each long-running exception was checkpointed within the trailing quarter with reviewer, date, and confirmation that conditions and remediation plan still apply
- Sample exception lifecycle for a real case showing request, approval, issuance, expiration, and renewal or closure

#### GOV-05.2 — Ethics review board with on-change reviews and enforcement authority

- **Deployment Types:** All
- **Manual/Automated:** Manual
- **AICM Mapping:** GRC-12 (ethics committee), GRC-10 (AI impact assessment), GRC-15 (human supervision), GRC-04 (policy exception process)
- **External References:** NIST AI RMF Govern 1.3, Govern 3.2, Manage 4.1, Manage 4.3; EU AI Act Article 14 (human oversight) and Article 72 (post-market monitoring) concepts; ISO/IEC 42001 Annex A.10 (third-party relationships)
- **Key Indicator Rationale:** A standing ethics review board with documented authority to halt or modify production AI deployments — and a process that translates provider-side model, policy, or behavior changes into governance responses within defined SLAs — is the L5 signal that governance is active rather than declarative. Organizations that can show either an exercised enforcement event or a documented end-to-end enforcement drill in the trailing 12 months, and that 95%+ of provider changes receive a governance response within SLA, have the L5 proactive posture.

**Control Objective:** A standing AI ethics review board has and demonstrably exercises enforcement authority, halting, modifying, or remediating production AI deployments as needed to meet enterprise AI ethics requirements. The governance function responds to provider and regulatory changes within defined SLAs, so governance is active and current rather than declarative.

**Description:** The board (the AI Council or a distinct function with cross-membership) has charter-codified enforcement authority backed by a documented enforcement path (change-management override, pipeline block, access revocation) acknowledged by engineering and product leadership. Over the trailing 12 months, the board has either (a) exercised enforcement at least once with a documented case record (halt, required remediation with deadline, or production modification), or (b) completed a documented end-to-end enforcement drill exercising decision, routing, operational action, and follow-through with named participants and findings. Separately, in-scope provider and ecosystem changes (model deprecations, provider policy changes, safety-behavior updates, new regional AI regulations) are detected via automated feed, routed to the board or AI Council within 24 hours of publication, and produce a documented governance response within 10 business days. Over the trailing 6 months, at least 95% of in-scope changes meet the 10-business-day SLA. GOV-05.2 closes two L5 loops. First, the ethics review board gains enforcement teeth: at L4 the review process produces go / no-go dispositions pre-deployment; at L5 the body can reach into production and force change when a previously-approved deployment turns out to be problematic, a model provider behavior change invalidates an earlier approval, or a regulatory shift mandates response. The exercised-or-drill threshold over 12 months is the anti-theater signal — a charter granting enforcement authority that has never been used and never been tested cannot be distinguished from no authority at all. One documented case with real bite (a halt, a forced remediation, or a production modification) is the strongest signal; a documented end-to-end drill with named participants is the acceptable alternative for organizations that did not have a real enforcement event in the trailing year. The drill must exercise the full path (decision → routing → operational action → follow-through), not just a tabletop discussion of "what would we do." Second, provider-change responsiveness is the governance-layer counterpart to MOD-05.2: while MOD-05.2 handles the technical model-registry response to a provider change, GOV-05.2 handles the governance response — does an AI Council standard need updating, does the approved-use-case catalog need modification, does the ethics board need to re-review an affected deployment. The 24-hour detection and 10-business-day response thresholds are the L5 operational rhythm.

**Evidence:**
- Ethics review board charter naming membership, scope, and enforcement authority with executive endorsement
- Documented enforcement path showing how board decisions translate into operational action (change-management integration, pipeline gates, access-revocation procedures)
- Either: at least one case record from the trailing 12 months showing the board exercised enforcement authority with outcome, named decision makers, and evidence of operational follow-through; or a documented end-to-end enforcement drill record showing decision, routing, operational action, follow-through, named participants, and findings
- Provider-change detection feed configuration covering major model providers, AI regulatory announcements, and major ecosystem policy changes
- 6-month detection-to-governance-response metric report showing 95%+ SLA compliance
- Sample governance response record for a real provider change (for example: an OpenAI or Anthropic policy change, a Bedrock model deprecation with governance implications, an EU AI Act milestone) showing detection, routing, and documented response within SLA

---

---

## 2. Organization Management (ORG) <a id="2-organization-management"></a>

**Category description:** Controls for enterprise-wide AI management, asset discovery and inventory, and centralized technical enforcement. Covers cloud-provider organization policies (AWS SCPs, Azure Policy, GCP Organization Policy) restricting AI services, AI-SPM-driven discovery of AI services / endpoints / agents / coding tools, blast-radius control via account or subscription isolation, enterprise administration of AI coding assistants, and shared security service deployment. Policy decisions and approval authority live in Governance; ORG is the technical enforcement and discovery layer that executes on those decisions.


---

### Level descriptors (reference — from AISMM main grid)

- **L1 Initial:** No visibility into enterprise AI usage. AI-powered applications and AI coding assistants untracked. Individual teams self-manage AI tools and services without centralized oversight. No technical controls restrict or manage AI service usage.
- **L2 Repeatable:** AI usage tracked through available means (billing analysis, endpoint telemetry, manual surveys). Approved AI platforms and developer tools identified but enforcement is policy-based or limited to provider-managed settings. Basic security requirements for AI deployments documented. No automated discovery of AI services or coding tool usage. AI feature settings managed for major SaaS platforms (e.g., Microsoft 365 Copilot) but not consistently.
- **L3 Defined:** Initial technical controls for AI services on the primary cloud platform paired with a first AI-SPM (or equivalent AI-aware discovery) pilot scoped to that primary cloud. AWS SCPs restricting Bedrock models, Azure Policy for Copilot, GCP Organization Policy for Vertex AI, or equivalents. AI coding assistants deployed via enterprise licensing with centralized administration (e.g., GitHub Copilot Business/Enterprise). Dedicated cloud deployments (account/subscription) provisioned for AI workloads. AI service inventory maintained for primary platforms with the AI-SPM pilot beginning to feed discovery findings into the inventory; reconciliation across the broader environment remains manual.
- **L4 Capable:** Consistent organizational policies enforce approved AI services and models across cloud accounts. Enterprise controls for AI developer tools enforced (approved assistants, security code review agents). AI-SPM (or equivalent) operationalized across all cloud environments and the developer endpoint fleet, with drift detection on the policy baseline. Unmanaged AI discovery covering both AI services and unauthorized coding tools. Visibility into models, endpoints, agents, and dependencies. Blast radius controlled through account/subscription isolation.
- **L5 Efficient:** Policy-as-code for AI service restrictions integrated with provisioning pipelines, with automated SLA-driven response to discovered unmanaged AI and policy violations. Shared security services leverage automation for efficiency. AI-SPM integrated into security operations with automated alerting on unmanaged AI or policy violations. Org-level AI controls updated proactively as providers release new models/services. Automated workflows to bring discovered unmanaged AI under management or block.

---

### Scope note — ORG boundaries

**ORG covers enterprise shared services and org-level enforcement frameworks. Structural-domain categories (APP, MOD, DAT, INF) cover per-project / per-deployment conformance against those frameworks. Mechanism overlap is expected** — for example, the same SCP file may carry both ORG-level service restrictions and MOD-level model-id restrictions; ORG owns the org-wide enforcement framework while MOD owns per-deployment binding to approved model identifiers. The categories distinguish by ownership scope (enterprise framework vs. per-project conformance), not by the tool used to implement them.

Specific boundaries:

- **ORG vs. GOV:** GOV owns policy content and approval authority (what is approved, who decides, which registries are authoritative — including the approved AI services list referenced by ORG-03.1). ORG translates those decisions into cloud-provider org policies, AI-SPM rules, blast-radius boundaries, and administrative tenancy.
- **ORG vs. MOD:** MOD-03.2 already binds production invocations to the approved model registry using SCPs / Azure Policy / GCP Org Policy. The same physical policy file may carry both ORG and MOD content; ORG KPIs focus on service-level and account-level enforcement (disabling unapproved AI services, restricting regions, isolating AI workloads, enforcing SaaS-embedded AI feature baselines, administering coding assistants), while MOD focuses on per-deployment model-identifier conformance.
- **ORG vs. DEV:** AI-BOM authoritative ownership lives in DEV. ORG owns service-layer endpoint and agent discovery (Bedrock endpoints, Azure AI Agent Service definitions, etc.); DEV owns per-application AI-BOM components (DEV-04.2 is authoritative for application-internal AI library and dependency inventory). ORG consumes AI-BOM and AI-SPM inventory for visibility and enforcement, but does not own its generation.
- **ORG vs. INF:** ORG owns cloud-provider *organization-level* and *account-boundary* controls (SCPs, Azure Policy at management-group scope, GCP Org Policy, tenancy structure, account-boundary egress allowlists). INF owns workload-internal infrastructure hardening of the AI workloads that run inside those boundaries (compute, network microsegmentation inside the workload, serving-host hardening). Account-boundary egress is org-policy and stays in ORG-04.3; workload-internal network hardening is INF.

---

### Level 2 — Repeatable

#### ORG-02.1 — Enterprise AI service discovery via reconciled telemetry

- **Deployment Types:** All
- **Manual/Automated:** Manual
- **AICM Mapping:** CCC-06 (change management baseline — establishing the AI service baseline), CCC-07 (detection of baseline deviation — manual at L2)
- **External References:** NIST AI RMF MAP-1; CSA AI Controls Matrix; Gartner AI TRiSM guidance
- **Key Indicator Rationale:** Producing a single authoritative inventory of AI services across the enterprise — reconciled against the three independent denominator sources (cloud and SaaS billing, endpoint and DNS telemetry, and a DNS allowlist of known AI provider endpoints) — is the L2 hygiene signal. An organization without this cannot tell the CISO which AI services are in use or which business units own them, and defaults to L1 ad-hoc adoption.

**Control Objective:** Security leadership knows which AI services are in use across the enterprise, reconciled across cloud and SaaS billing, identity provider sign-in records for AI services, and CASB or DNS/egress allowlist matches against known AI provider endpoints. AI services adopted outside formal approval channels are visible to the Council.

**Description:** This is the L2 discovery floor. Completeness is measured against the union of three independent telemetry sources used as the denominator: (1) cloud and SaaS billing for AI services and AI-enabled subscriptions, (2) EDR plus DNS/SWG logs for coding assistants and AI provider domains, and (3) DNS/egress allowlist matches against known AI provider endpoints. Each inventory entry classifies the service as cloud AI, SaaS-embedded, direct-API, or coding assistant. Automated AI-SPM-driven discovery is an L3 pilot / L4 operational expectation; at L2 the organization uses the tooling it already has — cloud billing exports, SaaS admin-portal usage reports, DNS query logs from its resolver or secure-web-gateway, and endpoint EDR telemetry for coding-assistant processes (github-copilot, cursor, tabnine, etc.). The three-source denominator is deliberately constructed to resist gameability: a curated "approved app list" denominator can be made trivially complete by removing inconvenient discoveries, while a denominator built from the union of independent telemetry feeds catches what the others miss. Billing catches paid enterprise subscriptions, endpoint and DNS telemetry catches direct-API consumption by developer laptops or workloads, and the DNS allowlist match catches outbound to known AI providers regardless of whether anyone has paid for it. Quarterly refresh is the L2 cadence; monthly or weekly refresh is the L4 automation target.

**Evidence:**
- Inventory export (spreadsheet or CMDB extract) showing each service with owner, business unit, and discovery source populated
- Reconciliation report for the most recent quarter showing the three denominator sources (billing, endpoint and DNS telemetry, AI provider DNS allowlist match) with the union calculation and how each inventory entry maps back to at least one source
- Sample of three inventory entries drawn from across discovery sources (one cloud-provider AI service, one SaaS-embedded AI, one direct-API or coding-assistant entry) demonstrating the owner and reconciliation traceability

#### ORG-02.2 — Baseline AI-feature settings for licensed SaaS platforms

- **Deployment Types:** API/SaaS
- **Manual/Automated:** Manual
- **AICM Mapping:** CCC-06 (change management baseline), CCC-02 (quality testing / approval process for baseline)
- **External References:** Microsoft Purview for Copilot, Google Workspace admin controls for Gemini, Salesforce Einstein Trust Layer configuration guides
- **Key Indicator Rationale:** Producing a documented baseline of AI-feature settings for the SaaS platforms the organization actually uses — and showing those settings are applied in the tenant admin portal — is the L2 "managed for major SaaS platforms but not consistently" signal from the main grid. It means someone has decided which AI features are on, which are off, and which require licensing gates, even if enforcement is still manual portal configuration rather than policy-as-code.

**Control Objective:** Embedded AI features in licensed SaaS platforms run under a configuration baseline that scopes which users can invoke them, blocks customer data from being used for provider model training, and binds AI to enterprise data protection or sensitivity controls where the platform supports it. The baseline is applied in every in-scope tenant with a recent admin validation on file.

**Description:** This is the SaaS-embedded-AI companion to ORG-02.1, and it is the canonical example of ORG-as-enforcer-of-GOV-policy: GOV authors the baseline (which features are on, what data-sharing posture the org accepts, what DLP integration is required), and ORG applies and evidences that baseline inside each SaaS tenant. See GOV for baseline authorship and ownership. In-scope platforms are at minimum Microsoft 365 Copilot, Google Workspace Gemini, and Salesforce Einstein/Agentforce where the organization holds licenses at the tier that unlocks AI features; platforms not licensed for AI features are out of scope. The baseline captures settings the platform actually exposes: for Microsoft 365 Copilot that typically means Purview sensitivity label enforcement, restricted SharePoint search scope, and assignment of Copilot licenses to a controlled group; for Salesforce Agentforce that typically means Einstein Trust Layer configuration and data-masking rules; for Google Workspace Gemini that typically means Workspace admin controls over the AI feature and data-region settings. Required baseline elements are: which users or license groups can invoke the feature, tenant-level data-sharing and model-training opt-outs, and DLP or sensitivity-label integration where supported. The baseline is not a policy document in isolation — it is the admin-portal configuration that reflects a GOV decision. Configuration snapshots are tenant-admin exports or screenshots stored centrally — an L2 evidence pattern, not automated policy reconciliation (that is L4+).

**Evidence:**
- Documented baseline per in-scope SaaS platform listing required AI-feature settings, license-group scoping, and data-sharing configuration, with a reference to the GOV-authored source
- Configuration snapshot per tenant from the admin portal (Purview / Entra, Google Workspace admin, Salesforce Setup) dated within the trailing 90 days
- Change log or ticket trail showing the baseline was reviewed and updated at least once in the trailing 12 months

---

### Level 3 — Defined

#### ORG-03.1 — Cloud org policy controls AI services on the primary platform

- **Deployment Types:** PaaS (primary)
- **Manual/Automated:** Automated
- **AICM Mapping:** CCC-03 (change management technology), CCC-04 (change authorization), CCC-06 (change management baseline)
- **External References:** AWS SCP reference (organizations/aws-managed-policies, bedrock IAM actions); Azure Policy built-in definitions for Azure OpenAI and Cognitive Services; GCP Organization Policy constraints for Vertex AI
- **Key Indicator Rationale:** Deploying cloud-provider organization-level policy to restrict AI services on the primary cloud — covering which AI services are permitted (against the GOV-authored approved AI services list), which regions they may run in, which accounts or subscriptions may invoke them, and (where applicable) which data-exfiltration or public-endpoint options are blocked — requires a central platform function that has agreed with business units on a single supported configuration. That coordination, paired with a first AI-SPM pilot on the same primary cloud (see ORG-04.2 for operational expansion), is the L3 defined-process signal.

**Control Objective:** On the primary cloud, organization-level policy (SCPs, Azure Policy, GCP Org Policy, or equivalent) blocks unapproved AI services, unapproved regions, and provider model-training opt-ins. A CSPM or AI-SPM pilot on the same cloud feeds discovered services into the enterprise inventory, and exceptions carry a named approver and an expiration.

**Description:** "Primary cloud platform" is the one cloud where the majority of the organization's AI workloads run — typically identified in the L2 inventory (ORG-02.1). The three required policy effects are: (a) blocking AI services outside the GOV-authored approved list, (b) restricting usage to an approved region list aligned with data residency, and (c) blocking tenant opt-ins that send customer data to the provider for model training. The AI-SPM pilot must reconcile findings into the ORG-02.1 inventory at least monthly. Coverage of 95% is measured over a 30-day window across in-scope accounts, and exceptions carry a 90-day expiration. L3 requires this posture on the primary platform plus a first AI-SPM pilot scoped to that cloud; secondary clouds and AI-SPM operationalization escalate to L4 (ORG-04.1, ORG-04.2). The capability jump that distinguishes L3 from L2 is "no AI-SPM at all" -> "AI-SPM pilot on the primary cloud feeding the inventory." This KPI is deliberately narrower than MOD-03.2: MOD-03.2 pins production invocations to approved model identifiers via SCPs / Azure Policy / Org Policy; ORG-03.1 restricts which AI *services* are available at all, which regions, and which cross-tenant data flows are permitted. The two stack — MOD-03.2 says "only these models," ORG-03.1 says "only this service, in these regions, with these provider-training settings" — and the same physical SCP or Azure Policy file commonly carries both sets of statements (see scope note). Enforcement must be policy-as-configuration (SCP / Azure Policy assignment / Org Policy binding), not a documented request process that relies on account owners to comply. The approved AI services list itself is authored and maintained by GOV; ORG enforces the list as configuration. The 95% coverage threshold accommodates legacy accounts undergoing migration; the 90-day exception expiration forces reconciliation.

**Evidence:**
- SCP, Azure Policy assignment, or GCP Org Policy definition bodies covering service restriction, region restriction, and provider-training opt-out, with a reference to the GOV-authored approved AI services list
- Policy assignment or attachment report showing at least 95% of in-scope accounts/subscriptions on the primary cloud carry the policy
- AI-SPM pilot deployment record on the primary cloud showing scope, refresh cadence (at least monthly), and a sample inventory reconciliation against ORG-02.1
- Exception register showing each unenforced account or subscription with a named approver and expiration within 90 days of issuance
- Sample denied event (CloudTrail, Azure Activity Log, or GCP Audit Log) showing the policy blocking an out-of-scope AI service invocation or provisioning request

#### ORG-03.2 — Enterprise administration of AI coding assistants

- **Deployment Types:** All
- **Manual/Automated:** Automated
- **AICM Mapping:** CCC-04 (change authorization), CCC-06 (change management baseline)
- **External References:** GitHub Copilot Business/Enterprise admin documentation; Cursor for Teams admin controls; JetBrains AI Assistant enterprise configuration; AWS Q Developer Pro admin controls
- **Key Indicator Rationale:** Consolidating AI coding assistant usage onto enterprise-tier licensing with centralized administration — SSO-bound, scoped to the IdP group allowed to use it, with content-exclusion and telemetry-opt-out settings configured centrally — requires IT and security to agree on an assistant, procure the enterprise tier, and turn off individual purchases. That is the L3 coordination signal.

**Control Objective:** Engineering reaches AI coding assistants only through enterprise-tier licensing under centralized administration, with consumer-tier subscriptions prohibited and blocked via endpoint or network controls. Access is IdP-bound and scoped to a defined engineering group, and content-exclusion and non-enterprise telemetry opt-outs are enabled in the admin console.

**Description:** Approved enterprise-tier products include GitHub Copilot Business/Enterprise, Cursor for Teams, JetBrains AI Assistant enterprise, AWS Q Developer Pro, or equivalent. Access must be IdP-bound and scoped to a defined engineering group. The 95% SSO-authentication denominator is the larger of HRIS engineering headcount or developer-tooling license count, deliberately not "active users in the enterprise tenant" — a denominator defined as "people already in the enterprise tenant" would be 100% by construction and would tell the CISO nothing about developers who quietly opted out into a personal-tier alternative. The enterprise-tier requirement matters because only the enterprise tier of most assistants exposes central admin, group scoping, content-exclusion, and telemetry controls. Consumer-tier Copilot, individual Cursor accounts, and personal JetBrains AI Assistant subscriptions lack those controls and send code to provider-default training pipelines. Enforcement at egress / CASB (blocking unauthenticated outbound to copilot-proxy endpoints, blocking Cursor API calls without enterprise-tenant SSO, etc.) is the typical technical pattern; a CASB tile plus an SSO-enforcement rule plus a provider-side SSO requirement is the common L3 configuration. Developer self-service procurement of non-enterprise tiers is a common failure mode — anchoring the denominator in HRIS or developer-tooling seats forces unmanaged-developer alternatives into view.

**Evidence:**
- Enterprise-tier license agreement and admin-console screenshot showing IdP-bound SSO, scoped group assignment, content-exclusion settings, and telemetry opt-out where available
- 30-day usage telemetry from the enterprise tenant showing active SSO-authenticated user count
- HRIS extract or developer-tooling license report establishing the engineering-headcount denominator, with the calculation showing 95%+ SSO authentication against that denominator
- CASB or egress policy configuration blocking outbound to consumer-tier authentication endpoints for the assistant tool family
- Sample EDR or CASB detection of a blocked attempt to use a non-enterprise-tier coding assistant

#### ORG-03.3 — Dedicated cloud deployment environments for AI workloads

- **Deployment Types:** Self-hosted, PaaS
- **Manual/Automated:** Automated
- **AICM Mapping:** CCC-04 (change authorization — account provisioning), CCC-06 (change management baseline)
- **External References:** AWS Well-Architected Generative AI Lens; AWS Organizations multi-account strategy; Azure landing zones for AI/ML; GCP security foundations blueprint
- **Key Indicator Rationale:** Provisioning AI workloads into dedicated accounts or subscriptions — separated from general workload accounts, with their own guardrails, network boundaries, and data-egress controls — is how organizations actually contain AI blast radius. The L3 "dedicated cloud deployments provisioned for AI workloads" bar is met when the pattern is repeatable and covers the AI workloads that exist today, not when it is aspirational.

**Control Objective:** Production AI workloads on the primary cloud are isolated into AI-designated accounts, subscriptions, or projects vended from a repeatable landing-zone pattern that aligns with enterprise standard configurations. Exceptions carry a named approver and a remediation date.

**Description:** "Dedicated" means AI-specific, not AI-only — a single AI account typically hosts multiple AI applications owned by one business unit, which is fine. The provisioning pattern enforces three things at vending time: ORG-03.1 policy scope, a VPC/VNet egress allowlist to AI provider endpoints (or equivalent transit-gateway control), and an AI-workload tag. The 180-day remediation target on exceptions ties each waiver to a plan rather than an indefinite carve-out. Enforcement evidence is the landing-zone or account-vending module (AWS Control Tower AFT customization, Azure Landing Zone subscription-vending module, GCP project-factory Terraform) showing the AI blueprint with network egress allowlist, org-policy attachment, and tagging. The provisioning pattern matters because it is what makes L4 blast-radius isolation (ORG-04.3) achievable: an L3 org that can vend an AI account with the right guardrails baked in is one step from L4 consistency across all AI workloads. The 90% threshold acknowledges a tail of legacy workloads.

**Evidence:**
- Account-vending or landing-zone module definition (Terraform, CloudFormation, Bicep) showing the AI workload blueprint with network, tagging, and policy scope
- Inventory export showing the distribution of production AI workloads by account/subscription/project and whether each is AI-designated per tag
- Exception register for legacy AI workloads not in AI-designated accounts with remediation target date within 180 days
- Sample vended account showing the expected egress allowlist, organizational-policy inheritance, and AI-workload tag applied

---

### Level 4 — Capable

#### ORG-04.1 — Consistent AI org-policy enforcement across every cloud environment

- **Deployment Types:** PaaS, Self-hosted
- **Manual/Automated:** Automated
- **AICM Mapping:** CCC-04 (change authorization), CCC-06 (change management baseline), CCC-07 (detection of baseline deviation)
- **External References:** AWS SCP baseline guidance; Azure Policy at management-group scope; GCP Organization Policy constraints; CSA Cloud Controls Matrix UEM/IAM mappings
- **Key Indicator Rationale:** Extending the L3 primary-cloud policy posture to every cloud environment the organization operates — secondary clouds, acquisition-brought tenants, research or experimental orgs — with automated drift detection and a closed remediation loop is the L4 "consistent organizational policies across cloud accounts" bar. Achieving it requires a central cloud-governance function that owns policy content, a deployment pipeline that pushes policy to every org/tenant, and drift detection that actually closes to green.

**Control Objective:** AI deployments in cloud comply with a technical configuration standard that aligns with the approved enterprise framework in GOV-04.1 (e.g. the AICM). This is continuously monitored with CSPM/CNAPP/AI-SPM or equivalent automated tooling.

**Description:** This is the cross-environment hardening of ORG-03.1. Coverage is measured over a 30-day window. Drift must be detected within 24 hours and remediated within 7 calendar days for at least 95% of events over the trailing 90 days; the rest follow the ORG-03.1 exception format with named approver and 90-day expiration. Newly-acquired tenants have a 90-day grace period from acquisition close or from earlier identity/network integration, tracked on the exception register with a named integration owner and plan. The typical L4 pattern is a single policy-as-code repository (Terraform, Pulumi, Azure Policy as code via Bicep/ARM) that pipelines policy out to AWS Organizations, multiple Azure tenants, and GCP organizations; drift detection runs via AWS Config + Access Analyzer, Azure Policy compliance scans, and GCP Policy Intelligence (or an AI-SPM product that covers all three). The 98% coverage threshold is tighter than the L3 95% because the organization has now had a full maturity cycle to bring legacy accounts online; the 24-hour drift detection and 7-day remediation loop is what distinguishes L4 operational muscle from L3 one-time deployment. The 90-day acquisition grace period acknowledges that real-world M&A integration is a multi-month project and that holding L4 organizations to "100% from day-one" of an acquisition close is operationally unreasonable; the grace period replaces "harsh" with "tracked" — the acquired tenant is on the exception register from day one with a named integration owner, but does not depress the 98% denominator until the 90 days expire.

**Evidence:**
- Policy-as-code repository showing ORG-03.1 policy content, with CI/CD pipeline definition that deploys to every cloud org/tenant
- Coverage report across all cloud environments (primary and secondary) showing 98%+ of in-scope accounts carry the policy over 30 days, with newly-acquired tenants in their grace-period window enumerated separately
- Drift detection and remediation ticket history for the trailing 90 days showing detection timestamp, remediation timestamp, and remediation outcome (restored or exception)
- Exception register showing named approver and expiration within 90 days of issuance for each active exception, plus the integration plan and target completion date for any acquired tenant in the 90-day grace period

#### ORG-04.2 — Automated AI discovery across clouds and endpoints

- **Deployment Types:** All
- **Manual/Automated:** Automated
- **AICM Mapping:** CCC-06 (change management baseline), CCC-07 (detection of baseline deviation)
- **External References:** Gartner AI TRiSM / AI-SPM category guidance; OWASP LLM03:2025 Supply Chain (visibility into AI components); Wiz / Prisma Cloud AI-SPM / Palo Alto AI Access Security / Microsoft Defender for Cloud AI workloads / Tenable AI Aware feature sets
- **Key Indicator Rationale:** The capability jump from L3 (AI-SPM pilot on the primary cloud) to L4 is operationalization across every cloud environment plus the developer endpoint fleet, with drift detection running against the policy baseline. The L4 organization can answer "what AI services and agents are running anywhere in the enterprise" from a tool, not a spreadsheet, and drift in the AI-SPM-detected posture surfaces against the ORG-04.1 baseline within hours.

**Control Objective:** Automated AI discovery extends across cloud environments and managed endpoints, covering AI services, model endpoints, agents, MCP servers, and AI-enabled SaaS features. Discovery uses CSPM/CNAPP with AI awareness, EDR endpoint visibility, CASB, and dedicated AI-discovery products where deployed, with discovered assets auto-reconciled to a named owning team.

**Description:** Coverage is operationalized across every cloud in scope for ORG-04.1 plus the managed developer endpoint fleet — not just the L3 primary-cloud pilot. Required asset classes include AI service deployments, model endpoints, agent definitions (Bedrock Agents, Azure AI Agent Service, Vertex AI Agent Builder), AI SaaS usage from managed endpoints, and service-layer dependencies; application-internal AI-BOM is owned by DEV-04.2. L4 retires the L2 billing-plus-DNS hack and the L3 primary-cloud pilot as the primary discovery sources. The list of what AI-SPM tooling must cover is deliberately broad — the organization doesn't have to use a single product, but it has to cover the cloud-AI-service axis, the agent axis, and the endpoint-direct-API axis with some combination of tools. Agents deserve explicit call-out because Bedrock Agents, Azure AI Agent Service, and Vertex AI Agent Builder are increasingly where enterprise AI autonomy lives, and CSPM that predates those services may not discover them. The owner-assignment rule prevents a common gameability pattern: assigning every newly-discovered AI service to a generic "platform team" queue and calling the reconciliation rate 100%. A specific application team (the team that owns the workload using the service) or a shared-service team with a written remit covering the service class (e.g., a "central AI platform" team whose charter explicitly says it operates Bedrock endpoints used by line-of-business teams) are the only valid owner types — a catch-all assignment to the team that runs everything else is not a real owner and does not satisfy this KPI. The 95% reconciliation-with-real-ownership threshold is what pushes the discovery tool from a dashboard into a governance input.

**Evidence:**
- AI-SPM or equivalent tool deployment map showing operationalized coverage across every cloud environment in scope for ORG-04.1 plus the developer endpoint fleet (not just the L3 primary-cloud pilot)
- Tool inventory export showing discovered AI services, endpoints, agents, and endpoint-detected coding tools with refresh timestamps
- Reconciliation report against the ORG-02.1 inventory showing 95%+ match rate with assigned owners; sample of owner assignments demonstrating each is either a specific application team or a documented shared-service team with a written remit covering the service
- Drift-finding log showing AI-SPM-detected deviations from the ORG-04.1 policy baseline surfaced within 24 hours
- Sample discovered asset that moved from "new discovery" to "reconciled and owned" within a defined SLA window

#### ORG-04.3 — Deployment isolation

- **Deployment Types:** Self-hosted, PaaS
- **Manual/Automated:** Automated
- **AICM Mapping:** CCC-04 (change authorization), CCC-06 (change management baseline)
- **External References:** AWS Well-Architected Generative AI Lens (isolation patterns); NIST SP 800-207 Zero Trust Architecture (microsegmentation); CSA Cloud Controls Matrix IVS (infrastructure and virtualization security)
- **Key Indicator Rationale:** Taking the L3 "dedicated AI account" pattern to full coverage, with enforced account-boundary egress allowlists and isolation between AI workloads and non-AI workloads, is the L4 "blast radius controlled through account/subscription isolation" bar. Achieving 100% of production AI workloads in designated accounts with enforced account-boundary egress means the account-vending pattern from L3 is now mandatory, not optional.

**Control Objective:** AI projects run in isolated cloud accounts or datacenter environments and are network isolated. There are no unmanaged network paths to general workload environments.

**Description:** This KPI is scoped to **account-boundary egress** — the org-policy layer that decides what an AI account is allowed to talk to outside its boundary. Each designated container must carry: (a) an enforced account-boundary egress allowlist to approved AI provider endpoints and internal services, (b) no shared-tenant network path to general workload accounts except via approved logged transit, and (c) a MOD-02.1-aligned criticality tag separating high-criticality workloads from medium/low. Workload-internal network hardening (microsegmentation inside the workload, host-level network policy, service-mesh authorization) is INF, not ORG; ORG-04.3 stays at the account boundary because that is the org-policy layer of network isolation. The account-boundary egress allowlist is the operational teeth of isolation: if an AI workload in the AI account can still call arbitrary outbound, the account boundary is cosmetic. The allowlist typically lives in a VPC endpoint policy, Azure Firewall or NSG rule set at the subscription egress, GCP VPC Service Controls perimeter, or an equivalent network-policy implementation depending on the cloud. Criticality-based account separation prevents a medium-criticality internal assistant from sharing an account with a customer-facing regulated-use-case assistant — a blast-radius concern that matters once the organization has multiple AI workloads per business unit. The 15-minute detection on egress-allowlist violations and the zero-production-outside-designated-accounts bar are what differentiate L4 from L3.

**Evidence:**
- Inventory cross-check showing 100% of production AI workloads in AI-designated accounts/subscriptions/projects with criticality tags aligning to MOD-02.1
- VPC endpoint policy, Azure Firewall / NSG rule, GCP VPC-SC perimeter, or equivalent network-policy definition per AI account showing the enforced account-boundary egress allowlist
- 90-day alert history for account-boundary egress-allowlist violations with detection timestamp, acknowledgement timestamp, and disposition
- Exception register showing any non-AI-designated-account production AI workload with a named approver and unexpired timeline

---

### Level 5 — Efficient

#### ORG-05.1 — Policy-as-code pipeline for AI enforcement policies

- **Deployment Types:** All
- **Manual/Automated:** Automated
- **AICM Mapping:** CCC-03 (change management technology), CCC-04 (change authorization), CCC-06 (change management baseline), CCC-07 (detection of baseline deviation), CCC-09 (change restoration)
- **External References:** OPA / Rego, Azure Policy as code via Bicep/ARM templates, GCP Organization Policy as code via Terraform, HashiCorp Sentinel; NIST AI RMF MANAGE-4; AWS Well-Architected Generative AI Lens operational excellence pillar
- **Key Indicator Rationale:** Running AI service policy content through the same CI/CD pipeline as the organization's other policy-as-code — peer-reviewed pull requests, automated tests against policy violation fixtures, staged rollout, and closed-loop drift detection with auto-remediation — is the L5 operational bar. Shipping zero policy updates bypassing the pipeline and remediating drift within one hour requires the pipeline to be the only sanctioned path for policy change. The capability jump from L4 (operationalized AI-SPM with drift detection) to L5 is policy-as-code automation that can both push and roll back, paired with auto-remediation.

**Control Objective:** Technical controls enforcing ORG-04.1 are managed as code where tooling supports it. Both org-wide controls (such as SCPs, Azure Policy, GCP Organization Policy) and project-specific policy bundles (such as OPA rules or Cedar policies for the agents and MCP servers in a given project) live in enterprise version control and deploy via CI/CD with staged rollout and exercised rollback.

**Description:** Scope covers all AI-related organizational policy — SCPs, Azure Policy, GCP Org Policy, AI-SPM custom rules. Drift detection runs within 15 minutes and auto-remediation completes within 1 hour for the 95% target; remaining drift events become exception tickets with 90-day expiration. Rollback must be exercised in production within the trailing 12 months. This is the L5 discipline: the policy-as-code pipeline is not a convenience, it is the control. Automated tests against fixtures matter because L5 organizations catch "we tightened the SCP and broke legitimate Bedrock access for the data science team" at PR time, not in production. Staged rollout to a dev organization first lets policy changes be tested against realistic resource topology before touching production. The auto-remediation of drift within one hour is what distinguishes L5 from L4: L4 remediates drift in days with tickets, L5 remediates in minutes with automation and only escalates the exceptions. The rollback-exercised requirement mirrors MOD-03.2 — a policy pipeline that can push forward but not pull back is a brittle control.

**Evidence:**
- Policy-as-code repository showing AI-policy content under version control, peer-review approvers, and automated test fixtures for policy violations
- 90-day pipeline audit showing all AI policy changes to production flowed through the pipeline (zero manual console edits)
- Drift detection and auto-remediation log for the trailing 90 days showing 95%+ remediation within 1 hour and exception promotions for the remainder
- Rollback exercise record within the trailing 12 months showing the previous policy state was restored and the outcome documented
- Sample PR showing automated-test results against violation fixtures blocking a regressive policy change

#### ORG-05.2 — Proactive response to AI provider releases

- **Deployment Types:** All
- **Manual/Automated:** Automated
- **AICM Mapping:** CCC-07 (detection of baseline deviation), CCC-08 (exception management), CCC-09 (change restoration)
- **External References:** Gartner AI TRiSM; OWASP LLM03:2025 Supply Chain; SANS Shadow IT guidance extended to shadow AI
- **Key Indicator Rationale:** Closing the loop from "AI-SPM discovers unmanaged AI or policy violation" to "the finding is auto-routed, triaged to an outcome, or blocked" within defined SLAs across high volumes of findings is the L5 proactive posture. An organization producing a 90-day SLA-compliance metric at 95%+ has the detection pipeline, the routing logic, the owner assignments, and the automated block actions all working together — which the main grid calls out as the L5 target.

**Control Objective:** New models, features, and services from major AI providers (AWS Bedrock, Azure OpenAI, OpenAI, Anthropic, Google Vertex) are detected on announcement, given a documented approve/block/conditional decision before general availability, and translated into updates to ORG-04.1 standards and ORG-04.2 discovery rules through the same CI/CD pipeline.

**Description:** Findings flow from ORG-04.2 and ORG-05.1 into case management with finding-type-specific SLAs: unmanaged AI service triages within 4 hours and resolves within 14 days; unauthorized coding assistant triages within 4 hours and is blocked or enterprise-converted within 7 days; policy violations triage within 1 hour and remediate within 72 hours. The 95% SLA threshold is measured per category over the trailing 90 days. L4 gives the organization the discovery capability; L5 turns discovery into consistent action. The SLA-by-finding-type structure matches how real triage queues work — unmanaged AI services on a cloud account take longer to resolve than an unauthorized coding assistant on a laptop, and both are much higher-urgency than a policy-drift event on a known account. The automated block actions closing the loop is what pushes this from a well-run ticket queue into L5 "automated workflows to bring discovered unmanaged AI under management or block" per the main grid. The provider-release proactive-review piece captures the main grid's "org-level AI controls updated proactively as providers release new models/services" — this overlaps with MOD-05.2 at the model-layer cadence, but ORG-05.2 focuses on service-level and policy-level updates (new Bedrock service launches, new Azure AI Foundry agent type, new Vertex AI capability) rather than model-version turnover.

**Evidence:**
- Case-management workflow configuration showing routing rules, SLA timers per finding type, and named owner queues
- 90-day SLA compliance report per finding category showing triage and resolution times with 95%+ compliance
- Sample of one finding per category showing end-to-end lifecycle (detection, auto-routing, triage, resolution action, evidence of completion)
- Automated block-action exercise record per category (an SCP update applied, a CASB rule added, an endpoint allowlist change pushed) within the trailing 90 days
- Review record for a recent provider-announced AI service showing the 5-business-day assessment outcome and any resulting policy update through ORG-05.1

---

---

## 3. IAM (IAM) <a id="3-iam"></a>

**Category description:** Identity and access management for AI applications, agents, and customer-facing AI flows across deployment types (self-hosted, PaaS, API/SaaS). Covers human authentication into AI applications, non-human identities for AI agents and services, chain of delegation and consent when agents act on behalf of users, identity chaining and transitive trust in multi-agent workflows, MCP and tool authorization with fine-grained scopes, credential scope and lifecycle, goal-based authorization for autonomous agents, and least-privilege enforcement. Application-layer authorization logic (what the app does once it has an identity, tool restrictions in code, guardrail-based action limits) lives in APP; telemetry and logging of identity activity live in MON.


---

### Level descriptors (reference — from AISMM main grid)

- **L1 Initial:** AI services and developer tools accessed using personal credentials, shared credentials or user impersonation. Agents inherit full user permissions without scoping. No distinction between human and non-human identities. API keys manually managed with broad access. No MCP or tool authorization in place.
- **L2 Repeatable:** Initial use of service accounts or managed identities for AI workloads. SSO for enterprise AI chatbots. Basic OAuth integration for AI application access. Agent permissions defined but not scoped to tasks, agents typically receive user's full authorization. MCP servers, if used, rely on static API keys. Initial documentation of which agents access which resources.
- **L3 Defined:** Dedicated service accounts or managed identities provisioned per AI workload and enterprise AI application. Enterprise AI platforms and SaaS AI features managed through provider IAM controls. OAuth or similar standards used for primary MCP tool authorization. Agent credentials managed with rotation and revocation procedures. Initial least-privilege policies for enterprise AI agents documented. Customer-facing AI applications include authentication and consent management.
- **L4 Capable:** Distinct non-human identities established for AI agents across deployment types. Delegation and consent flows implemented (users explicitly authorize agent actions). On-behalf-of authorization patterns with tokens reflecting both user and agent identity. Agent identity integrated with enterprise IdP. MCP tool authorization with fine-grained scopes. AI developer tools consistently tag their commits/actions with agent identity.
- **L5 Efficient:** Automated agent identity lifecycle management integrated with AI deployment pipelines. Just-in-time, ephemeral credentials for agent operations. Delegation chain validation for multi-agent workflows with transitive trust boundaries enforced. Full auditability from user intent through agent actions to resource access. Policy-as-code enforcement for agent authorization. Continuous validation of agent permissions against intent. Customer-facing AI identity flows secured with consent management and revocation.

---

### Scope note — IAM / APP / MON boundaries

IAM defines *who* an identity is and *what scopes* it carries: human SSO into AI applications, non-human identity provisioning for agents and workloads, delegation token structure, MCP tool authorization scopes, credential lifecycle (rotation, revocation, ephemerality), and the trust boundaries that determine what an identity is allowed to access. What the application does once it has that identity — the authorization logic in code, tool restrictions expressed as application policy, guardrail-based action limits — belongs in APP. The logs of what identities actually did (agent action logs, delegation-chain trace records, guardrail-block events with identity attribution) belong in MON; MON's usefulness depends on IAM being well-defined first. Model-level trust properties (can this model be trusted with elevated scopes based on its safety evaluation) belong in MOD.

### Three-island note

IAM is the category where the three deployment islands diverge most sharply:

- **Self-hosted / enterprise-built agents.** The organization owns identity end-to-end: service accounts in the enterprise IdP, IAM roles / managed identities in cloud, workload identity frameworks like SPIFFE/SPIRE, custom OAuth client registration. Full control, full responsibility.
- **PaaS-embedded agents** (Bedrock AgentCore, Azure AI Foundry agents, Vertex AI agents). Identity is a joint configuration: the provider supplies the identity primitives (AgentCore Workload Identity, Azure managed identity, Vertex service agent) and the organization configures scoping, OAuth integrations, and delegation patterns through provider-native controls.
- **SaaS-embedded agents** (M365 Copilot, Salesforce Agentforce, Google Workspace Duet/Gemini, Zendesk AI agents, etc.). The provider owns the agent's identity and delegation machinery; the organization consumes it through provider-exposed IAM extensions (Copilot's access controls, Agentforce permission sets, sensitivity labels, tenant-level data access policies).

Several KPIs below split into per-island variants where the measurable outcome genuinely differs. Where the outcome is the same across islands (no personal credentials for AI workloads, SSO for AI applications), the KPI reads "All."

---

### Level 2 — Repeatable

#### IAM-02.1 — SSO with MFA for enterprise AI applications

- **Deployment Types:** All
- **Manual/Automated:** Automated
- **AICM Mapping:** IAM-14 (strong authentication), IAM-13 (uniquely identifiable users), IAM-15 (passwords and secrets management)
- **External References:** OWASP ASI03 (Identity & Privilege Abuse), NIST AI RMF GOVERN-1.4
- **Key Indicator Rationale:** Every enterprise AI application (self-hosted chatbot, Bedrock/Azure OpenAI front-end, Copilot, Agentforce) authenticating through the enterprise IdP with MFA enforced, and zero local accounts, is only achievable when IAM has taken ownership of AI-application onboarding as a recognized class. An L1 organization has personal ChatGPT accounts, shared Copilot seats, and developer-owned chatbot logins; an L2 organization has centralized that.

**Control Objective:** Human access to enterprise AI applications goes through the enterprise IdP with MFA, with no local accounts, shared logins, or personal credentials in use. This holds across self-hosted apps, PaaS AI consoles, and SaaS AI seats like Copilot, Agentforce, and Gemini, so downstream delegation and audit have a real user identity to anchor on.

**Description:** SSO-mediated authentication is the L2 baseline that keeps identity context usable downstream — an agent that claims to act on behalf of a user needs a real user identity to act on, and if the upstream login is a local account or a shared seat, delegation, consent, and audit all collapse. The measurable bar is at least 95% of AI applications in the MOD-02.1 inventory authenticating via SAML or OIDC with MFA enforced; exceptions carry a named approver and expiration within 90 days. The 95% threshold accommodates legacy applications mid-migration without eroding the control. Mechanism varies by island: SaaS AI (Copilot, Agentforce, Gemini) is a provider SSO feature the organization configures; PaaS consoles use cloud-IdP federation; self-hosted is the organization's own OIDC/SAML wiring. This KPI sits at L2 rather than L1 because an L1 organization has not yet recognized "enterprise AI applications" as a category to govern; L2 is where that recognition shows up as a population of AI apps on a known IdP.

**Evidence:**
- IdP application register showing AI applications with SAML/OIDC integration and MFA policies enforced
- AI application inventory (from MOD-02.1 or a dedicated register) cross-referenced to IdP integration status, with 95%+ covered
- Sample authentication walk-through for one self-hosted AI app, one PaaS AI console, and one SaaS AI (Copilot or Agentforce) showing IdP-mediated flow with MFA
- Exception register listing AI applications without IdP integration, each with approver name and expiration date within 90 days of issuance

#### IAM-02.2 — Inventoried non-human identities for AI workloads

- **Deployment Types:** All
- **Manual/Automated:** Either
- **AICM Mapping:** IAM-03 (identity inventory), IAM-13 (uniquely identifiable users), IAM-15 (passwords and secrets management)
- **External References:** OWASP ASI03 (Identity & Privilege Abuse), ASI10 (Rogue Agents), NIST AI RMF MAP-4
- **Key Indicator Rationale:** An organization that can produce a list of non-human identities used by AI workloads — service accounts, managed identities, API keys, workload identities — with an owner per entry, and show that no human's personal credentials are being used for scheduled or automated AI workloads, has moved past L1 ad-hoc credential use into L2 initial NHI practice.

**Control Objective:** AI workloads run under inventoried non-human identities: service accounts, managed identities, workload identities, API keys They never use personal or shared human credentials, and manage secrets in a central store rather than source code or environment files. Each NHI in use across self-hosted, PaaS, and SaaS workloads traces back to a named owner.

**Description:** This is the L2 NHI foundation. At L1, agents and automated AI jobs borrow a developer's OpenAI API key, run under a shared `ai-bot` service account, or use a credential pasted into a `.env` file; at L2, the organization has stood up dedicated NHIs per workload (even if not yet per-agent, which is the L4 expectation) and moved the credentials into a secrets store like AWS Secrets Manager, Azure Key Vault, or HashiCorp Vault (or equivalent). The inventory must include identifier, workload served, owner, and credential type (static or dynamic) per entry, but does not need to be in a single system — a spreadsheet that reconciles against IdP NHI lists, cloud managed-identity lists, and the secrets store is acceptable at L2. The per-agent split, the ephemerality requirement, and the rotation automation come later. The reason this lives at L2 rather than L3 is that an L3 organization is doing *per-workload* dedicated NHIs systematically; an L2 organization has stopped the bleeding (no personal credentials, no shared logins, no keys in code) but may still have one NHI serving multiple AI workloads.

**Evidence:**
- NHI inventory listing AI-workload service accounts, managed identities, and workload identities with owner and workload attribution
- Secrets-store inventory showing API keys for AI services (OpenAI, Anthropic, model-provider APIs, third-party AI SaaS) stored centrally with access controlled by IAM
- Sampled codebase scan or git history review for committed API keys matching known AI-provider key formats (OpenAI `sk-`, Anthropic `sk-ant-`, Azure OpenAI keys) showing zero hits in active branches
- Sample of three AI workloads showing which NHI each uses, with no overlap to named human users

---

### Level 3 — Defined

#### IAM-03.1 — Per-workload NHI with managed credential lifecycle

- **Deployment Types:** All
- **Manual/Automated:** Automated
- **AICM Mapping:** IAM-05 (least privilege), IAM-06 (user access provisioning), IAM-07 (access changes and revocation), IAM-15 (secrets management)
- **External References:** OWASP ASI03 (Identity & Privilege Abuse), NIST AI RMF GOVERN-1.4, NIST SP 800-207 (Zero Trust — NHI patterns)
- **Key Indicator Rationale:** One NHI per AI workload, each with a documented rotation cadence and a tested revocation procedure, is achievable only when a central IAM function has taken ownership of AI NHI provisioning as a defined process. An L2 organization has NHIs but sharing is common and rotation is ad hoc; L3 is where the per-workload rule is enforced and the lifecycle is written down.

**Control Objective:** Each production AI workload runs under its own non-human identity, using short-lived federated credentials where possible and with static credentials rotating on a managed cadence, when used. A compromise of one workload's identity does not cascade across the AI estate.

**Description:** The "dedicated NHI per workload" threshold is what distinguishes L3 from L2. At L2 the organization has stopped using personal credentials; at L3 it has eliminated shared NHIs across AI workloads, so an incident affecting one workload's NHI does not force rotation across ten. The measurable bar: static credentials rotate automatically on a documented cadence of no more than 90 days, or are replaced by dynamic/federated credentials (AWS STS, Azure managed identity federation, GCP Workload Identity Federation, OIDC). A documented revocation procedure exists per NHI class and has been exercised within the trailing 12 months. Shared NHIs carry an exception with named approver and expiration within 90 days. Rotation automation — tied to the secrets store's native rotation for static keys, or replacement with dynamic/federated credentials for cloud-native workloads — is the L3 hygiene signal. The revocation drill is the proof that "we can turn this off" isn't hypothetical. Exercising revocation in a non-production equivalent (or on a real decommissioned workload) within the trailing 12 months is acceptable evidence. Per-agent identity (one NHI per agent instance, not per workload) is an L4 expectation covered by IAM-04.1. At L3, agent-action logs (per MON-03.1) attribute by workload identity, not per-agent-instance. Per-agent identity for telemetry attribution arrives at L4 with IAM-04.1.

**Evidence:**
- NHI register showing one-to-one (or fewer agents-to-NHI) mapping between AI workloads and NHIs, with duplicates/sharing flagged and on a remediation plan
- Rotation configuration or secrets-store policy showing static-credential rotation no longer than 90 days, or federation configuration replacing static credentials for cloud-native workloads
- Documented revocation procedure per NHI class (IdP service account, AWS IAM role, Azure managed identity, GCP service account, third-party API key) with a recent exercise record within the trailing 12 months
- Exception register for shared NHIs with approver and expiration within 90 days of issuance

#### IAM-03.2 — PaaS and SaaS provider IAM hardened to standard

- **Deployment Types:** PaaS and API/SaaS (self-hosted marked not applicable)
- **Manual/Automated:** Automated
- **AICM Mapping:** IAM-05 (least privilege), IAM-06 (access provisioning), IAM-16 (authorization mechanisms), IAM-17 (need-to-know access to knowledge)
- **External References:** OWASP ASI03 (Identity & Privilege Abuse), ASI04 (Supply Chain Vulnerabilities — provider scoping), Microsoft Purview / Copilot Control System, Salesforce Einstein Trust Layer
- **Key Indicator Rationale:** Configuring SaaS AI provider IAM extensions (Copilot sensitivity-label enforcement and restricted SharePoint search; Agentforce permission sets and sharing rules; Gemini for Workspace data access controls) and hardening PaaS agent IAM (Bedrock AgentCore identity, Azure AI Foundry identity, Vertex AI service agents) per documented standards requires a central function that understands how each provider's IAM surface maps to enterprise policy. This is an L3 defined-process signal because the configuration has to be deliberate and consistent.

**Control Objective:** Every PaaS AI platform and SaaS AI feature in the inventory has its provider IAM surface configured to a written enterprise standard, with drift detected and remediated rather than accumulating silently. Copilot, Agentforce, Gemini, Bedrock AgentCore, Azure AI Foundry, and Vertex AI operate as governed identity surfaces rather than out-of-the-box defaults.

**Description:** This KPI is the L3 "enterprise AI platforms and SaaS AI features managed through provider IAM controls" clause made measurable. The written standard covers user/group access, IAM-level data-surface scopes (Microsoft Graph, Salesforce permission set, Workspace API scopes), and sensitivity-label or permission-boundary enforcement; the measurable bar is at least 90% of in-scope features in compliance on the most recent scan, with drift detected via CSPM/SSPM or AI-SPM and remediated within 30 days. Each provider has its own IAM surface for AI: Copilot enforces sensitivity labels, restricts access to unlabeled or over-shared SharePoint content via Restricted SharePoint Search, and respects Purview DLP; Agentforce respects permission sets, field-level security, and sharing rules; Gemini for Workspace respects Drive sharing and admin-console AI access settings; Bedrock AgentCore uses IAM roles and the AgentCore Identity Service; Azure AI Foundry uses Entra-integrated managed identities and role-based access. The written standard says what the organization's default IAM configuration is (e.g., "Copilot restricted to users in `Copilot-Licensed` group, sensitivity-label enforcement on, Microsoft Graph scopes limited to the documented permission set"). The line between IAM and DAT here: IAM owns *which provider scopes are turned on* and *which user groups can invoke the AI feature*; DAT owns *which specific data sources are approved* for AI consumption (RAG source approval, sensitivity classification of the underlying content). Drift detection is what turns the standard from a one-time configuration into a control. Self-hosted has no provider IAM extension to configure, so the deployment scope is PaaS and API/SaaS.

**Evidence:**
- Written configuration standard per provider covering user/group scoping, data-surface scoping, and sensitivity/permission enforcement
- CSPM/SSPM or AI-SPM drift-detection configuration for PaaS and SaaS AI features with the standard as the baseline
- Most-recent scan report showing 90%+ compliance with at least one sampled finding tied to remediation within 30 days
- Sample of three in-scope provider AI features (one Microsoft, one Salesforce or equivalent SaaS, one PaaS agent platform) showing current configuration matching the standard

#### IAM-03.3 — OAuth-based MCP and tool authorization with named scopes

- **Deployment Types:** All
- **Manual/Automated:** Automated
- **AICM Mapping:** IAM-16 (authorization mechanisms), IAM-19 (agent access restriction), IAM-15 (secrets management)
- **External References:** MCP Authorization spec (OAuth 2.1, RFC 8707 Resource Indicators as of 2026-03-15 spec), RFC 9728 Protected Resource Metadata, OWASP ASI02 (Tool Misuse), ASI04 (Supply Chain Vulnerabilities)
- **Key Indicator Rationale:** Moving MCP servers and AI tool integrations from static API keys to OAuth 2.1 with named scopes requires the organization to have an OAuth-capable IdP for agent/workload identities, a registered scope vocabulary, and developer enablement. An L2 organization has MCP running on static keys; L3 is where OAuth integration is the default path and static-key integrations are the documented exception.

**Control Objective:** Production AI agents and applications authorize MCP and external tool calls via OAuth-issued named scopes rather than static API keys, against a scope registry treated as authoritative. Wildcard or catch-all scopes are not used, and the registry includes an MCP-server allowlist per agent class.

**Description:** The L3 signal is that OAuth-with-named-scopes is the default path — new integrations go OAuth-first, legacy key-based integrations are on a plan. The measurable bar: production AI agents and applications using MCP servers or external tools authorize via OAuth 2.1 with RFC 8707 Resource Indicators per the current MCP spec, using named tool-level scopes (e.g., `sec-edgar:*`, `salesforce:read`); new integrations reject static API keys; existing static-key integrations migrate within 180 days; at least 80% of in-scope integrations use OAuth, with the remainder under exception. The MCP Authorization specification (2026-03-15 revision) mandates OAuth 2.1 with Resource Indicators (RFC 8707) and Protected Resource Metadata discovery (RFC 9728); static-key integrations are out of line with the current spec. The 80% threshold acknowledges that migration of established integrations takes time while refusing to let the remainder linger indefinitely; the 180-day migration target for exceptions is deliberately strict because MCP is new and most integrations are recent. The scope registry documents each scope, what it permits, requesting agents, and the MCP-server allowlist per agent class — it prevents "OAuth-with-wildcard-scope" theater (a tool configured for OAuth but granted a catch-all scope has the same effective risk as a static key) and folds in MCP-server allowlisting as a scope concern, not a separate KPI. The fine-grained per-operation scoping (`sec-edgar:read-filings` rather than `sec-edgar:*`, `s3:GetObject` on a specific prefix rather than `s3:*`) is the L4 expectation covered by IAM-04.3 — at L3 the named tool-level scope exists; at L4 the scope is decomposed to operation-level granularity.

**Evidence:**
- MCP server and tool-integration inventory showing authorization mechanism (OAuth, static key) per entry
- OAuth client registrations and scope definitions in the IdP or authorization server, with a scope registry describing each scope's permissions
- Migration backlog for static-key integrations with named owners and migration target dates within 180 days
- Sample OAuth flow for one MCP server showing scoped token issuance, Resource Indicator per RFC 8707, and the enforcement point validating the scope

---

### Level 4 — Capable

#### IAM-04.1 — Per-agent NHI federated to enterprise IdP and/or attestation-based

- **Deployment Types:** Self-hosted and PaaS (SaaS-embedded agent identity covered by IAM-04.2)
- **Manual/Automated:** Automated
- **AICM Mapping:** IAM-03 (identity inventory), IAM-13 (uniquely identifiable users), IAM-05 (least privilege)
- **External References:** OWASP ASI03 (Identity & Privilege Abuse), ASI10 (Rogue Agents), SPIFFE/SPIRE workload identity, AWS Bedrock AgentCore Identity, Azure Entra workload identity federation
- **Key Indicator Rationale:** Every production agent having its own IdP-integrated NHI means the organization has moved from "one NHI per workload" (L3) to "one NHI per agent instance with IdP-level lifecycle management" (L4). This requires an agent-identity registry, a provisioning pipeline, and IdP federation for agent identities — capabilities that only mature at L4.

**Control Objective:** Each production self-hosted or PaaS-embedded AI agent has its own non-human identity, registered or federated through an enterprise IdP or established via attestation-based identity, and uniquely attributed in every auth event, so authorization, revocation, and audit work per-agent rather than per-workload. Self-hosted agents use workload identity primitives like SPIFFE/SPIRE; PaaS agents use the provider's per-agent primitive (AgentCore Workload Identity, Foundry managed identity, Vertex per-agent service account).

**Description:** The L4 split from L3 is per-*agent* rather than per-*workload*. A "research-assistant workload" at L3 might have one NHI shared across twelve agent instances; at L4 each instance has its own identity, which is what enables per-agent authorization, per-agent revocation, and per-agent audit attribution in MON. The measurable bar: at least 95% of production agents show distinct per-agent identity in logs, with shared-identity agents under exception expiring within 90 days. Self-hosted agents use workload identity (SPIFFE/SPIRE, federated managed identity, OIDC-federated Kubernetes service accounts); PaaS agents use the provider's per-agent primitive (Bedrock AgentCore Workload Identity, Azure AI Foundry managed identity, Vertex per-agent service account), federated or inventoried in the enterprise NHI register. IdP integration (or federation) is what distinguishes this from "each agent has a random service account in some tool" — the identity lifecycle is managed in the same place as every other identity, which is where joiner-mover-leaver and NHI governance already live. SaaS-embedded agents (Copilot, Agentforce) are out of scope here because the provider owns the agent identity machinery and does not generally expose per-agent identity to the consuming organization; IAM-04.2 covers the SaaS island. The 95% threshold accommodates experimentation and legacy migration without eroding the control. Cross-category dependency note: distinct per-agent identity is a precondition for MON's per-agent action attribution — without IAM-04.1, MON's chain reconstruction at the agent level cannot work. This is informational guidance; MON achievement is not gated on IAM-04.1 in the model.

**Evidence:**
- Agent-identity register showing one NHI per production agent instance for self-hosted and PaaS deployments, with IdP or federated-identity linkage per entry
- Sample authentication/authorization log extracts showing distinct agent identity in the subject claim (or equivalent) for three agents (one self-hosted, one Bedrock AgentCore or equivalent PaaS)
- Federation configuration (SPIRE trust domain, Workload Identity Federation pool, AgentCore Workload Identity integration) linking agent identities to the enterprise IdP
- Exception register for shared-identity agents with approver and expiration within 90 days of issuance

#### IAM-04.2 — Dual-identity delegation and consent for on-behalf-of flows

- **Deployment Types:** All (mechanism varies: self-hosted uses OAuth Token Exchange; PaaS uses provider OBO primitives; SaaS uses provider-exposed consent and delegation surface)
- **Manual/Automated:** Automated
- **AICM Mapping:** IAM-13 (uniquely identifiable users), IAM-16 (authorization mechanisms), IAM-11 (customer approval for privileged access)
- **External References:** RFC 8693 (OAuth 2.0 Token Exchange) `act` claim pattern, draft-oauth-ai-agents-on-behalf-of-user, OWASP ASI03, ASI09 (Human-Agent Trust Exploitation), NIST AI RMF MANAGE-2
- **Key Indicator Rationale:** Producing tokens (or SaaS-equivalent delegation records) that carry both the acting agent's identity and the delegating user's identity, with an auditable consent record and a revocation path, requires coordinated work across the IdP, agent runtime, and application layer. Organizations that can show this end-to-end for production on-behalf-of flows have the L4 delegation posture.

**Control Objective:** When an agent acts on behalf of a user in production, the authorization carries both identities, the agent's delegated scope is a strict subset of the user's, and consent is captured up front and revocable end-to-end. Mechanism varies by island — RFC 8693 token exchange for self-hosted, provider OBO primitives for PaaS, provider consent and delegation surfaces for SaaS — but every on-behalf-of action attributes back to both the agent and the delegating user.

**Description:** The measurable bar: self-hosted and PaaS agents produce tokens with `sub` (agent) and `act` (user) claims under OAuth 2.0 Token Exchange (RFC 8693) or provider OBO primitives, with scope reduced at each hop; SaaS agents emit provider audit records attributing each action to both user and agent (Copilot, Agentforce running-user, Gemini); user consent is captured before delegation; revocation takes effect within 24 hours; and at least 90% of production OBO flows produce dual-identity records. The three-island expansion is load-bearing because the mechanism differs. For self-hosted/custom agents, RFC 8693 Token Exchange with the `act` claim is the mainstream standard; the IETF draft `draft-oauth-ai-agents-on-behalf-of-user` is still an active draft and covers single-hop OBO for agents explicitly, which is fine to use where supported but not required. For PaaS (Bedrock AgentCore Runtime OAuth Inbound/Outbound, Azure AI Foundry OBO via Entra, Vertex AI service-to-service OBO), the provider's OBO primitive produces equivalent records. For SaaS, the organization cannot issue its own dual-identity token — it consumes what Copilot/Agentforce emit as audit records attributing action to both the agent surface and the calling user; the KPI here is that this provider-side attribution is enabled and flowing. The 24-hour revocation time-to-effect is strict because delegated agent access is exactly where compromise manifests. Consent can be captured session-level (user clicks "authorize this agent" once per session) or action-category-level (user approves "read calendar" scope once, "write email" requires per-action confirmation) — APP owns the HITL confirmation UX, IAM owns that the consent record exists and is revocable. The scope-reduction evidence (token-scope comparison) closes the dual-identity-but-equal-scope failure mode: a token can carry both `sub` and `act` claims and still grant the agent the user's full scope, in which case the dual-identity attribution is cosmetic; the assessor must see that the agent's delegated scope is a strict subset of the user's session scope. This is the L4 capability; the L5 extension covers multi-hop chain validation (IAM-05.2). Cross-category dependency note: the dual-identity tokens and consent records produced here are the inputs MON uses to attribute agent actions to both user and agent at L4/L5 — informational, not a gate.

**Evidence:**
- Sample OAuth Token Exchange record for a self-hosted or PaaS agent showing `sub` (agent) and `act` (user) claims with scope-reduced token, or provider equivalent
- Token-scope comparison artifact for the same flow showing the user's session/origin scope alongside the agent's delegated token scope, demonstrating that the agent receives a strict subset and never the user's full scope (this defeats the dual-identity-but-equal-scope failure mode where an agent token carries both claims yet inherits the user's full authority)
- Provider audit-log sample for a SaaS-embedded agent action showing dual attribution (agent surface + calling user)
- Consent capture artifact (UI screenshot or API record) and consent-revocation log showing effect within 24 hours for a test revocation
- On-behalf-of flow inventory showing per-flow mechanism, attribution status, and consent/revocation implementation, with 90%+ compliance
- Exception register for flows without dual-identity attribution with approver and expiration within 90 days

#### IAM-04.3 — MCP and tool authorization with fine-grained scopes and deny-by-default

- **Deployment Types:** All (self-hosted/PaaS via policy-as-code at a policy-decision point; pure SaaS-consumer orgs via provider-native restricted-scope configuration hardened to standard — see SaaS variant in description)
- **Manual/Automated:** Automated
- **AICM Mapping:** IAM-16 (authorization mechanisms), IAM-19 (agent access restriction), IAM-05 (least privilege), IAM-04 (separation of duties)
- **External References:** MCP Authorization spec (OAuth 2.1 + RFC 8707 Resource Indicators), OAuth 2.0 scope best practices, Cedar policy language (AWS Verified Permissions / AgentCore), OPA/Rego, OWASP ASI02 (Tool Misuse)
- **Key Indicator Rationale:** Fine-grained per-operation scopes enforced deny-by-default at the MCP/tool boundary require a scope vocabulary, policy-as-code infrastructure, and an enforcement point that actually rejects out-of-scope requests. Organizations that can show rejected-request logs and a policy repository have the L4 fine-grained posture.

**Control Objective:** 95% of MCP servers and AI tool integrations authorize requests against fine-grained scopes defined per operation (read vs. write, per-resource, per-action) rather than per-tool. For self-hosted and PaaS deployments, authorization policy is expressed as code (Cedar, OPA/Rego, or equivalent) stored in version control, with a deny-by-default posture, and enforcement occurs at a policy-decision point like MCP server or gateway. For SaaS, implement least privilege using the mechanisms available in the provider (e.g. Microsoft Purview Restricted SharePoint Search). Wildcard scopes (`*`, `tool:*`, `resource:*`) are prohibited in production policy.

**Description:** This is the L4 upgrade from L3's "OAuth with named scopes." At L3 the scopes exist and are distinct from static keys; at L4 the scopes are fine-grained enough to meaningfully constrain behavior (`sec-edgar:read-filings` rather than `sec-edgar:*`, `s3:GetObject` on specific prefixes rather than `s3:*`), the policy is version-controlled rather than hand-maintained in provider consoles, and the enforcement point is on the request path rather than implicit trust. Cedar is the emerging default for AWS-hosted agents (Verified Permissions, AgentCore Gateway policies); OPA/Rego is the common alternative for multi-cloud and Kubernetes. The deny-by-default rule is what makes the scope vocabulary meaningful — a permit-by-default policy with selective forbids will always drift toward over-permission. Deny-decision logging is also load-bearing: without denies in the log, the organization cannot prove the policy is actually evaluating requests rather than passing everything.

**Practical example.** Take a customer support AI agent that helps reps look up orders, update tickets, and draft email responses. The self-hosted or PaaS-embedded implementation has three pieces:

1. *Policy-as-code in version control.* The agent ships with a Cedar (or OPA/Rego) policy bundle in the same repo as the agent code. The policy declares the intent space: `Action in [read_order, ticket_update, send_draft_email]`, scoped to `Resource.customer_id == context.user.assigned_customer_id`. Pull request review on every policy change, deployed via CI/CD with automated test fixtures.
2. *Intent evaluated at the decision point.* When a rep asks "look up order 12345 for Acme Corp," the agent constructs an intent claim (`{user: rep_42, customer: Acme, action: order_lookup}`) and includes it as a token in every downstream tool call. A Cedar/OPA decision point sits in front of each tool (the order API, ticketing API, email-draft service). On every call, the PDP checks the action against the declared intent and the policy. Concrete denial: rep_42 declared intent for Acme, agent then tries `read_customer_pii(customer: BetaCorp)`, Cedar denies because the action is outside the declared intent and the customer mismatches. Denial logged to MON.
3. *Stale permissions retired automatically.* A scheduled job (Lambda, Cloud Function, or equivalent) reads CloudTrail / Cloud Audit Logs and computes "agents that haven't exercised permission X in 90 days." Findings flow into a backlog, and permissions auto-retire after a documented grace period unless extended via PR. AWS IAM Access Analyzer's unused-access findings are the closest off-the-shelf example for the AWS path; equivalent capabilities exist on Azure (Entra Permissions Management) and GCP (IAM Recommender).

A pure SaaS-consumer organization implements the same posture using provider-native controls (see the SaaS variant subsection below for Microsoft 365 and Salesforce specifics).

**SaaS variant.** Pure SaaS-consumer organizations cannot insert a policy-decision point in front of Copilot or Agentforce — the request path is owned by the provider. The L4 capability on this path is to use the provider's native restricted-scope surface, configured to a written standard with drift detection. Concretely: for M365 Copilot, Microsoft Purview Restricted SharePoint Search confines retrieval to a curated list of sites, sensitivity-label DLP policies block AI consumption of labeled content, and Copilot data access controls are configured against the standard. For Salesforce Agentforce, the running-user model is constrained by permission sets and permission set groups specifically designed for AI agents (rather than reusing user-grade permission sets), with field-level security and sharing-rule overrides hardened. For Gemini for Workspace, admin-console AI access policies and Drive sharing controls are configured to a standard. Drift detection (SSPM, provider compliance reports, scheduled admin-export comparison no less than every 30 days) is the L4 signal on the SaaS path, just as deny-decision logs are the L4 signal on the self-hosted/PaaS path. Note the cross-reference dependency: this enables MON's chain-reconstruction capability (MON depends on IAM emitting decision and attribution records) — IAM owns producing the records, MON owns shipping and analyzing them.

**Evidence:**
- Policy-as-code repository with Cedar/Rego/equivalent policies for MCP and tool authorization, deny-by-default pattern visible (self-hosted/PaaS path)
- Policy-decision-point configuration (MCP server, AgentCore Gateway, API gateway, sidecar) with enforcement enabled in production (self-hosted/PaaS path)
- For SaaS-consumer organizations: provider-native restricted-scope configuration artifacts (e.g., Microsoft Purview Restricted SharePoint Search configuration plus sensitivity-label DLP policies; Salesforce permission set + permission set group hardening for Agentforce; Gemini for Workspace admin-console AI access configuration) compared to the written standard, with SSPM or provider compliance report showing in-compliance status
- Allow/deny decision logs showing at least one real or drill-generated deny event per in-scope integration in the trailing 30 days, with agent identity and requested scope captured (self-hosted/PaaS); SaaS-equivalent: provider DLP/sensitivity-label block events with attribution
- Scope registry showing per-operation granularity (no wildcards in production policy)
- Sample of three integrations covering the deployment mix the organization actually runs (e.g., one MCP server, one outbound API tool, one SaaS provider AI surface) showing current policy or hardened configuration and the corresponding decision/block logs

---

### Level 5 — Efficient

#### IAM-05.1 — Just-in-time ephemeral credentials wired into the agent pipeline

- **Deployment Types:** All (mechanism differs: self-hosted via STS/Vault dynamic secrets; PaaS via provider short-lived tokens; SaaS via provider consent-token lifetime policy)
- **Manual/Automated:** Automated
- **AICM Mapping:** IAM-10 (management of privileged access roles — time-limited), IAM-15 (secrets management), IAM-07 (access changes and revocation)
- **External References:** OWASP ASI03 (Identity & Privilege Abuse), NIST AI RMF MANAGE-3, NIST SP 800-207 (Zero Trust — ephemeral credentials), Auth0 Token Vault, HashiCorp Vault dynamic secrets
- **Key Indicator Rationale:** Production agents whose credentials are issued just-in-time, expire within a task/session, and are provisioned automatically by the deployment pipeline require integration between the pipeline, the identity platform, the secrets store, and the agent runtime. Long-lived static credentials in any production agent is an immediate L5 disqualifier.

**Control Objective:** Production AI agent credentials are short-lived and issued just-in-time by the identity platform, with provisioning, scoping, and revocation wired into the agent deployment pipeline. Human-in-the-Loop JIT for agents is available for applications with that use case. Long-lived static credentials exist only as time-bounded exceptions with executive sign-off and a compensating control.

**Description:** This is the L5 culmination of the credential-lifecycle arc (L2 "don't use personal credentials," L3 "rotate within 90 days or federate," L4 "per-agent NHI," L5 "ephemeral and JIT"). The measurable bar: session/task tokens with a 1-hour default lifetime and 8-hour ceiling for long-running tasks, issued on demand by the identity platform (AWS STS, Azure/GCP Workload Identity Federation, HashiCorp Vault dynamic secrets, AgentCore Identity, or equivalent); static long-lived credentials only under executive-approved exception with 180-day expiration and a compensating control; zero credential incidents in the trailing 90 days from static credentials outside the exception list. The 1-hour default matches AWS STS defaults, AgentCore Workload Identity norms, and the IETF short-lived-token guidance; the 8-hour ceiling exists for genuinely long-running agent workflows (batch research, long-horizon planning) where a 1-hour token would require unreasonable refresh frequency. Pipeline integration is the capability signal: agent deployment triggers identity provisioning and scope assignment, and agent decommissioning triggers revocation — no ticket-based credential handoff, no copy-paste into configuration. The static-credential exception exists because some third-party tools do not support OAuth or session tokens; those cases require executive sign-off and are bounded in duration so they do not accumulate silently. DPoP or mTLS for token binding is encouraged but not required at L5 because ecosystem support is still uneven.

**Evidence:**
- Credential lifetime policy and issuing-system configuration (STS session duration, Vault dynamic-secret TTL, AgentCore Identity token lifetime, equivalent) showing default at 1 hour and long-running ceiling at 8 hours
- Deployment pipeline artifact (Terraform, CDK, Helm, equivalent) showing agent provisioning, identity binding, and decommissioning automation
- Exception register for long-lived static credentials with executive approver, expiration within 180 days, and documented compensating control
- 90-day incident or audit review showing zero credential incidents from long-lived static credentials outside the exception register
- Sample credential issuance and expiration trace for one production agent from provisioning through task completion

#### IAM-05.2 — Delegation-chain validation in multi-agent workflows

- **Deployment Types:** All (self-hosted and PaaS implement via token-exchange chains and policy-as-code; SaaS implements via provider-native agent-to-agent delegation surface where available, with gaps tracked)
- **Manual/Automated:** Automated
- **AICM Mapping:** IAM-16 (authorization mechanisms), IAM-04 (separation of duties), IAM-09 (segregation of privileged access), IAM-12 (log integrity)
- **External References:** RFC 8693 token chaining with nested `act`, draft-oauth-ai-agents-on-behalf-of-user (single-hop coverage noted; multi-hop handled via RFC 8693), OWASP ASI03, ASI09 (Human-Agent Trust Exploitation), ASI10 (Rogue Agents), NIST AI RMF MANAGE-2
- **Key Indicator Rationale:** Validating that each hop in a multi-agent workflow reduces (rather than expands) authority, that the chain is traceable from user intent through every agent hop to the final resource access, and that chain-violation attempts are blocked and logged, requires policy-as-code that understands chain depth and actor nesting, plus logging infrastructure that preserves the chain across service boundaries. This is the L5 signal for agentic workflows.

**Control Objective:** In production multi-agent workflows, every hop preserves the full delegation chain and reduces (rather than expands) authority, with scope-expansion attempts denied and logged. The chain from user intent through every agent hop to the final resource action is reconstructible end-to-end, and SaaS gaps where provider records cannot carry the chain are tracked rather than hidden.

**Description:** This KPI is the agentic-workflow counterpart to IAM-04.2's single-hop OBO. The measurable bar: each hop adds the invoking agent's identity (nested `act` claims per RFC 8693 or provider equivalent), expansion attempts are denied and logged, maximum chain depth is defined (recommended 5), audit records reconstruct the full chain from user intent to final action for at least 95% of multi-agent invocations over 30 days, and at least one production-observed scope-expansion deny exists in the trailing 90 days (or a documented quarterly red-team / chaos exercise injecting a real attempt into the production decision path). SaaS chain-record gaps live in a known-gap register. When Agent A calls Agent B which calls Agent C, the common failure mode is either (a) identity context dropped at a hop so downstream authorization treats Agent B as the originator, or (b) scope expansion where B exchanges A's token for one with broader scope. RFC 8693 addresses both via nested actor claims and scope-reduction requirements, but enforcement has to be wired in at each service's policy-decision point. The 95% chain-reconstruction threshold leans on MON for log capture but the IAM KPI is about the *token structure* and *policy enforcement* that make reconstruction possible — MON owns shipping the records, IAM owns that the records carry full chain identity. The "production-observed deny" requirement exists because a deny-decision policy that has never fired in production cannot be distinguished from a deny-decision policy that does not fire at all; without at least one real or red-team-injected production deny in the 90-day window, the KPI is testing whether the org can synthesize convincing test data, not whether enforcement actually works. The SaaS gap is real: M365 Copilot-to-Agentforce or Agentforce-to-external-tool crossings may not produce chain-preserving records, and L5 requires the organization to know where the gaps are rather than pretend they don't exist. The chain-depth cap prevents runaway agent composition where a 20-hop chain defeats meaningful review. Cross-category dependency note: this KPI together with IAM-04.1 and IAM-04.2 produces the records MON needs to do chain reconstruction at MON's L4/L5; the dependency is informational, not a hard prerequisite gate — an organization can be at IAM-L5 with MON lagging or vice versa.

**Evidence:**
- Policy-as-code for delegation-chain validation showing scope-reduction enforcement and chain-depth cap
- Sample multi-hop token trace (nested `act` claims or provider equivalent) for a production three-or-more-hop workflow
- 30-day audit-reconstruction report showing 95%+ of multi-agent invocations reconstructible end-to-end from user intent to resource action
- At least one production-observed scope-expansion deny log from the trailing 90 days, with full request/decision context, OR a documented quarterly chaos/red-team exercise injecting a real scope-expansion attempt into the production decision path with the resulting deny captured
- Known-gap register for SaaS cross-agent flows where provider records are incomplete, with executive acknowledgement and provider-engagement status

#### IAM-05.3 — Policy-as-code agent authorization with intent-binding

- **Deployment Types:** All (self-hosted/PaaS via version-controlled policy-as-code; pure SaaS-consumer orgs via provider-native intent/context-based access controls hardened to standard — see SaaS variant in description)
- **Manual/Automated:** Automated
- **AICM Mapping:** IAM-05 (least privilege), IAM-08 (user access review — continuous), IAM-16 (authorization mechanisms), IAM-18 (output modification and special authorization)
- **External References:** Cedar policy language, OPA/Rego, NIST AI RMF GOVERN-1.4, OWASP ASI02 (Tool Misuse), LLM06 (Excessive Agency)
- **Key Indicator Rationale:** Expressing agent authorization as version-controlled policy-as-code, validating each agent invocation's scope against the originating user intent or task definition before execution, and automatically retiring stale agent permissions against a continuous review cadence is the L5 posture for "continuous validation of agent permissions against intent." Organizations that can show a policy repository, intent-binding mechanism, and quarterly permission drift report have this.

**Control Objective:** Production agent authorization is engineered: policy-as-code in version control, the agent's declared task or user intent evaluated at the decision point so actions outside that intent are denied, and stale permissions retired automatically. SaaS-consumer organizations achieve the same posture through provider context and intent controls managed under the same engineering discipline.

**Description:** The three L5 signals are (a) policy-as-code with CI validation and peer review on every change (no hand-edited authorization in provider consoles for production agents), (b) intent-binding at the decision point (the agent's declared task/user-intent is part of the authorization input, not just the agent's identity and the target resource), and (c) automated stale-permission retirement (unused-permission detection turned on and actually removing permissions within a bounded time). The measurable bar: zero production authorization changes bypass CI/review; drift detection runs every 30 days; permissions unused for 60 days are removed or re-justified within 90 days; SaaS-consumer organizations use provider context/intent controls (Purview Adaptive Protection, Einstein Trust Layer with Agentforce action classification) managed as configuration-as-code under the same cadence. Intent-binding is the newest of the three and is where L5 distinguishes itself from L4: at L4 a policy might say "agent X can read from bucket Y"; at L5 it says "agent X can read from bucket Y *when processing a task where the user requested financial analysis*," with context.task_type or context.user_intent enforced as a policy condition. This requires the agent runtime to pass intent context to the decision point, which is a cross-category lift with APP, but the policy expression lives in IAM. The 30-day drift-detection cadence and 60-day stale threshold match mature NHI-governance norms. CI review on every change is what converts the L4 "policy exists" into the L5 "policy cannot be changed without review."

**SaaS variant.** Pure SaaS-consumer organizations cannot author Cedar/Rego policy at the request path for Copilot or Agentforce. The L5 capability on this path is to use the provider's own intent/context-aware controls and to manage them with the same engineering discipline. For Microsoft, this is Purview Adaptive Protection (which incorporates user risk context into DLP decisions) plus Copilot context-aware DLP and sensitivity-label-driven access controls. For Salesforce, it is the Einstein Trust Layer combined with Agentforce action-classification policies and field-level security tied to declared use cases. Configuration is exported and version-controlled (M365 DSC, Salesforce Metadata API export, provider Terraform providers) so changes go through CI and peer review, and drift detection runs on the same cadence. The SaaS variant is genuinely thinner — provider intent-context controls are less expressive than Cedar with custom context attributes — but the L5 *posture* (controls managed with engineering discipline, drift detected, stale permissions retired) translates.

**Customer-facing AI identity (CIAM).** The main-grid L5 calls out customer-facing AI identity flows secured with consent management and revocation. That capability is generally captured by IAM-04.2 (consent capture, dual-identity attribution, consent revocation within 24 hours) applied to the customer-facing flow rather than the employee-facing flow — the mechanism is the same, the consenting party is the customer. Organizations operating customer-facing AI agents satisfy this by demonstrating IAM-04.2 evidence on a customer-flow sample. Where the customer-facing flow has materially different requirements (e.g., regulated CIAM with stronger consent-record retention or sector-specific revocation timelines), those requirements are documented in the consent capture standard referenced by IAM-04.2 rather than as a separate KPI here.

**Evidence:**
- Version-controlled policy repository with CI pipeline, test suite, and required-review branch protection (self-hosted/PaaS path)
- Policy sample showing intent-binding (context.task_type, context.user_intent, or equivalent) as a required condition for sensitive actions
- For SaaS-consumer organizations: provider configuration-as-code artifacts (M365 DSC export, Salesforce Metadata API export, provider Terraform state) under version control with CI/review, plus evidence that provider intent/context-aware features (Purview Adaptive Protection, Einstein Trust Layer with Agentforce action classification) are configured to the standard
- Drift-detection configuration and 90-day report showing stale-permission flags, retirement decisions, and time-to-retirement
- 90-day audit showing zero production authorization changes bypassing CI/review
- End-to-end trace for one production agent action showing the intent context passed to the decision point and the policy evaluation result (or, on SaaS path, an equivalent provider trace showing intent/context attributes affecting the access decision)

---

---

## 4. Security Monitoring (MON) <a id="4-security-monitoring"></a>

**Category description:** Monitoring and logging of AI applications and activity, including prompts, input/output, service usage, agent actions, tool/MCP invocations, data access, guardrail events, and other telemetry useful for security operations and compliance. Covers enterprise telemetry collection, SIEM integration, AI-specific detection engineering, and SOC workflow integration. Excludes runtime defenses that generate the telemetry (guardrail deployment lives in APP), response workflows and playbooks (IR), identity definition that makes action logs meaningful (IAM), and per-deployment model-behavioral metrics (MOD).


---

### Level descriptors (reference — from AISMM main grid)

- **L1 Initial:** No AI-specific monitoring. Reliance on cloud and/or AI provider default logging, if enabled. No visibility into prompts, agent actions, or AI service usage. AI activity untracked and unauditable.
- **L2 Repeatable:** Basic AI service logs collected (model invocations, API calls) and initial token/cost tracking for major AI platforms. Logs retained in the provider but not regularly analyzed for security. No prompt or response capture. AI usage logs reviewed for billing or troubleshooting but not security.
- **L3 Defined:** Prompt/response logging implemented for key AI applications (with appropriate data handling/masking). Agent action logging captures tool calls and resource access. Initial AI-specific alerting (e.g., guardrail violations, information disclosure). Logs aggregated into central SIEM. MCP and tool invocations logged.
- **L4 Capable:** Comprehensive AI telemetry across applications, including prompts, responses, agent actions, delegation chains, and data access. AI-specific threat detection in place (prompt injection, jailbreak attempts, anomalous patterns). Delegation chain auditability for multi-agent workflows. Alerts integrated with SOC workflows. Sensitive data detection in key AI inputs/outputs.
- **L5 Efficient:** Real-time AI security monitoring with automated response capabilities. Full auditability from user intent through agent actions to resource access. AI behavioral baselines with anomaly detection. Proactive threat hunting for AI attack patterns. AI monitoring integrated with incident response playbooks.

---

### Scope note — MON boundaries

MON owns enterprise telemetry collection, SIEM pipelines, and AI-specific detection engineering. The guardrail product that emits a violation event is an APP capability; the pipeline that collects that event, stores it, and fires a correlated alert is MON. The detection rule is MON; the playbook that fires when the alert lands is IR. The identity scope that makes an agent action log meaningful is IAM; the log itself and the correlation across actions is MON. Per-deployment model-behavior metrics (drift, groundedness, refusal rate on a fixed eval set) are MOD; enterprise-wide threat-detection rules, cross-deployment correlation, and SOC-routed alerting are MON.

Most enterprise AI telemetry originates in provider-managed logs: CloudTrail `bedrock:InvokeModel` events, Bedrock model-invocation logs, Azure OpenAI diagnostic logs and activity logs, Vertex AI Cloud Logging / audit logs, OpenAI / Anthropic API usage logs (organization-level), and CASB or egress telemetry for direct-to-provider consumption. KPIs reference these sources as the primary telemetry surface.

---

### Level 2 — Repeatable

#### MON-02.1 — Provider-managed invocation telemetry across the AI platform footprint

- **Deployment Types:** All
- **Manual/Automated:** Automated
- **AICM Mapping:** LOG-03 (security monitoring and alerting — baseline), LOG-04 (log records retention), LOG-07 (logging scope), LOG-08 (log records)
- **External References:** NIST AI RMF MEASURE-2.7, OpenTelemetry Semantic Conventions for GenAI
- **Key Indicator Rationale:** An organization that can produce a single list of every AI platform in use — Bedrock, Azure OpenAI, Vertex AI, direct-to-provider API consumption (OpenAI, Anthropic), and any self-hosted inference services — paired with the provider-managed invocation log stream for each, has moved past L1 reliance on defaults. It has taken ownership of knowing which AI logs exist and that they are being kept long enough to matter.

**Control Objective:** Provider-managed invocation logs are enabled, collected, and retained for every AI platform in the enterprise inventory. Coverage spans the full platform footprint rather than only the well-instrumented platforms, and token and cost telemetry gets a monthly look for billing and capacity anomalies.

**Description:** This is the L2 baseline: logs exist, are enabled by default-on provider configurations, and are retained long enough to investigate something that happened last month. Retention is at least 90 days. Covered sources per deployment type include CloudTrail and Bedrock model-invocation logs, Azure OpenAI diagnostic logs, Vertex AI Cloud Logging, organization-level API usage logs or CASB/egress telemetry for direct-to-provider consumption (OpenAI, Anthropic), and serving-runtime logs for self-hosted inference. Token and cost telemetry is captured per platform and reviewed monthly. At least 90% of distinct model + endpoint tuples in production telemetry are covered by an enabled log source, and the telemetry set is cross-checked against the MOD-02.1 inventory to confirm no inventoried platform is missing. The distinction from L1 is explicit ownership — someone in security or platform ops can name every AI platform in use, point at the log stream, and show that retention is configured. The control does not require prompt/response capture (that is L3), does not require SIEM centralization (also L3), and does not require active security review (L3). It requires that the raw telemetry is not being thrown away. The 90% distinct-tuple coverage gate prevents the common failure pattern where one or two well-instrumented platforms dominate invocation volume while a long tail of direct-API consumption (corporate OpenAI keys, Copilot, Claude.ai for Work) is completely dark. The inventory cross-check closes the circularity gap — a telemetry-only count cannot find a platform that emits no telemetry at all, so the inventoried-but-not-logged case has to be checked against MOD-02.1 directly. Token/cost review at monthly cadence is the L2 version of observability — looking at usage for billing, capacity, and obvious anomalies (a 10x week-over-week spike) without yet claiming security review.

**Evidence:**
- List of AI platforms from the MOD-02.1 inventory (or equivalent inventory source), each mapped to the enabled provider-managed log source and the retention configuration
- Sample 30-day log export from each covered source showing invocation records present
- Coverage reconciliation showing at least 90% of distinct model + endpoint tuples from production invocation telemetry are covered by an enabled log source
- Inventory-vs-telemetry cross-check showing every inventoried platform from MOD-02.1 is represented in the log estate, with any gaps tracked as exceptions with a named owner
- Monthly token/cost review artifact (dashboard screenshot, ticket, or meeting note) for the trailing three months

#### MON-02.2 — Named owner for the AI logging pipeline

- **Deployment Types:** All
- **Manual/Automated:** Manual
- **AICM Mapping:** LOG-01 (logging and monitoring policy and procedures), LOG-02 (audit logs protection)
- **External References:** NIST AI RMF GOVERN-2
- **Key Indicator Rationale:** An organization that has named a single accountable owner for AI logging, with a documented record of what is logged and where, has passed the L2 ownership bar. Without a named owner, the L3 SIEM-centralization and prompt/response-logging work has no function to land in.

**Control Objective:** A single named owner is accountable for AI logging coverage and maintains a register of platforms, log sources, retention, and storage that stays current as the AI estate changes. Raw AI logs are restricted to a named operations group rather than broadly readable.

**Description:** This is the L2 governance wrapper around MON-02.1. At L1 there is no owner; at L2 there is. The register lists each AI platform, enabled log sources, retention, storage location, and access restrictions, and is reviewed annually and whenever a new AI platform is added. The named group is typically security operations, platform engineering, or equivalent. The register does not have to be elaborate — a spreadsheet or wiki page listing platform, log source, retention, storage location, and access group is enough. The important properties are that it exists, has an owner, and gets updated when a new AI platform shows up. Access restriction matters because AI invocation logs at any scale will contain sensitive content in prompt/response fields as soon as prompt/response capture is turned on in L3; treating AI logs as broadly readable at L2 is a future compliance problem. This KPI intentionally stops short of prescribing SIEM centralization, masking, or active monitoring — those are the L3 jumps.

**Evidence:**
- Named owner for AI logging (role assignment, org-chart entry, or documented responsibility)
- Logging register listing each AI platform, log source, retention period, storage location, and access group
- Access control configuration on the log storage locations showing restriction to a named group
- Register change history showing update on addition of a new AI platform within the trailing 12 months (or an attestation that no new platforms were added)

---

### Level 3 — Defined

#### MON-03.1 — Prompt, response, and agent-action telemetry centralized in the SIEM

- **Deployment Types:** All
- **Manual/Automated:** Automated
- **AICM Mapping:** LOG-03 (security monitoring and alerting), LOG-07 (logging scope), LOG-14 (input monitoring), LOG-15 (output monitoring), LOG-08 (log records)
- **External References:** OWASP LLM02:2025 Sensitive Information Disclosure, OWASP ASI02 (Tool Misuse), OpenTelemetry Semantic Conventions for GenAI, NIST AI RMF MEASURE-2.7
- **Key Indicator Rationale:** Centralizing prompt, response, and agent-action telemetry from every high-criticality AI deployment into the enterprise SIEM — with masking applied before persistence and correlation IDs linking user session to model invocation to tool call — requires a defined standard, a built logging pipeline, and product teams that have adopted it. An L2 organization has logs sitting in provider consoles; an L3 organization has telemetry in the SIEM that an analyst can query.

**Control Objective:** Prompts, responses, and agent tool and MCP invocations from high-criticality production AI deployments arrive in the enterprise SIEM under a documented schema, with sensitive data masked before persistence, or logs are encrypted and restricted. Exceptions are time-bound and carry named owners.

**Description:** This KPI operationalizes the L3 main-grid language ("prompt/response logging implemented for key AI applications," "agent action logging captures tool calls," "logs aggregated into central SIEM," "MCP and tool invocations logged") into a measurable program-level indicator. The SIEM delivery SLO is 15 minutes from event to availability. Masking covers PII, credentials, and secrets before persistence. Each record carries a documented schema — timestamp, user identity, session ID, conversation/trace ID, model identifier and version, sanitized tool name and parameters, guardrail evaluation result, and token counts (OpenTelemetry GenAI semantic conventions are the recommended baseline). "High-criticality" is the same population defined by MOD-02.1 — customer-facing, regulated, or ingests external/untrusted content — which keeps scope consistent across categories and avoids forcing an organization to instrument experimental or internal-only deployments at L3. Exceptions carry a named owner and expiration within 90 days. Masking is a prerequisite, not optional — shipping raw prompts containing customer PII into the SIEM is a compliance problem. The 15-minute delivery SLO distinguishes an actual SIEM pipeline from a nightly batch export that cannot support investigation. The exception mechanism exists because one or two deployments will inevitably be mid-migration or built on a platform that does not yet emit compatible telemetry; exceptions with owners and expirations prevent the exception list from quietly swallowing the control. At L3, identity attribution in agent-action logs is workload-level (per IAM-03.1 NHI), not per-agent-instance — chain-level attribution and delegation reconstruction arrive at L4 with MON-04.1, which depends on IAM-04.1/04.2.

**Evidence:**
- Logging standard document specifying schema (OpenTelemetry GenAI conventions or equivalent), masking requirements, and SIEM delivery SLO
- SIEM index or data-model showing prompt, response, and tool-invocation records with the documented fields
- Coverage report listing high-criticality deployments from MOD-02.1 and their logging status, showing at least 95% coverage
- Masking pipeline configuration and test results (test PII patterns submitted, verified masked in stored logs)
- Latency metric from log-emission timestamp to SIEM-availability timestamp showing 95th-percentile at or below 15 minutes
- Guardrail / content-filter violation events from APP-04.1 / APP-04.2 ingested into SIEM with deployment ID and (where available) user/agent attribution, supporting the APP-05.1 feedback loop
- Exception register with named owners and expiration dates within 90 days of issuance

#### MON-03.2 — AI-specific detection content with routed alerts

- **Deployment Types:** All
- **Manual/Automated:** Automated
- **AICM Mapping:** LOG-03 (security monitoring and alerting), LOG-05 (audit logs monitoring and response), LOG-13 (failures and anomalies reporting)
- **External References:** OWASP LLM01:2025 Prompt Injection, OWASP LLM02:2025 Sensitive Information Disclosure, MITRE ATLAS, OWASP ASI01 (Agent Goal Hijack)
- **Key Indicator Rationale:** Deploying a documented set of AI-specific detection rules in the SIEM — covering guardrail violations, repeated prompt-injection attempts, sensitive-data exfiltration patterns, and runaway cost/token consumption — with alerts routed to a named queue and a triage SLA, requires a detection-engineering function that has taken AI as an in-scope threat surface. An L2 organization watches cost dashboards; an L3 organization has detections firing.

**Control Objective:** The SIEM runs AI-specific detection content covering guardrail violations, sensitive-data patterns in outputs, abnormal token or invocation volume, and unapproved or excessive tool use. Alerts route to a named on-call queue with a triage SLA, and the program shows confirmed true-positive activity rather than just rule presence.

**Description:** Four detection categories is the L3 minimum — enough to cover the main AI-specific attack classes from the OWASP LLM and ASI top-10 without demanding the broader behavioral-baseline and delegation-chain detection that belong at L4. The required categories are: (1) guardrail violations and repeated blocked prompts from a single identity; (2) sensitive-data patterns in model outputs (PII, credentials, internal identifiers); (3) abnormal token, cost, or invocation volume per identity or deployment relative to a baseline; (4) agent tool-invocation patterns outside the approved tool set or above a defined call-rate threshold. Alerts route to a named on-call queue with a 4-hour triage SLA for severity 1 and 2 events, and the team acknowledges at least 90% of severity 1 and 2 AI alerts within SLA over the trailing 90 days. At least one analyst-confirmed true-positive alert has been triaged per quarter across the four categories, or a signed zero-event justification with named approver exists for any quiet category. Each detection needs a named rule owner, documented logic, and a triage SLA that connects into the IR workflow (IR owns the playbook content; MON owns that the alert was acknowledged). The 4-hour SLA is deliberately looser than L4 SOC integration — at L3, AI detections exist and get acknowledged, but are not yet expected to be real-time. The 90% acknowledgement-within-SLA gate is what turns rule deployment into a detection program: shelved detections that nobody acknowledges do not count. The true-positive floor closes a known gameability: a category staffed by a low-fire signature-only rule that never alerts can technically pass the deployment requirement while contributing nothing to the program. Requiring at least one confirmed true positive per quarter across the four categories — or a signed zero-event justification when a category is legitimately quiet — forces either the rule to fire on real activity or the team to acknowledge that its detection content needs revisiting. Detection rule content itself may come from vendor detection packs (CrowdStrike, Microsoft Defender XDR, Palo Alto Cortex, AI-SPM products, or equivalent) or be authored in-house.

**Evidence:**
- Detection rule inventory in the SIEM covering the four required categories, each with a named owner, documented logic, and severity classification
- Sample fired alerts from each category over the trailing 90 days with triage records
- Acknowledgement metrics showing 90%+ of severity 1 and 2 AI alerts acknowledged within the 4-hour SLA over 90 days
- True-positive log showing at least one analyst-confirmed true-positive alert across the four categories per quarter, OR a signed zero-event justification with named approver for any quiet category
- On-call runbook reference showing AI alerts are in-scope for the named queue

---

### Level 4 — Capable

#### MON-04.1 — End-to-end auditability for agent and delegation chains

- **Deployment Types:** All (primary relevance to deployments using agent frameworks, MCP servers, or multi-agent orchestration)
- **Manual/Automated:** Automated
- **AICM Mapping:** LOG-07 (logging scope), LOG-08 (log records), LOG-14 (input monitoring), LOG-15 (output monitoring)
- **External References:** OWASP ASI02 (Tool Misuse), ASI05 (Cascading Trust Failures), ASI10 (Rogue Agents), OpenTelemetry distributed tracing for GenAI
- **Key Indicator Rationale:** Reconstructing a multi-step agent workflow end-to-end — user intent through agent reasoning through tool calls through downstream resource access, with trace IDs that link every span — requires distributed tracing across the agent runtime, instrumented MCP servers, and a correlation engine in the SIEM or observability platform. Organizations that can produce a reconstruction on demand for a randomly-selected agent session have the L4 telemetry maturity.

**Control Objective:** A randomly selected agent session can be reconstructed on demand from telemetry, showing user intent, agent reasoning, tool and MCP invocations, delegation hops, and downstream resource access in a single trace. Delegation chains carry originating user identity through IAM-issued credentials rather than synthesized correlation IDs. **N/A clause** applies for organizations with no agent deployments.

**Description:** This is the L4 "comprehensive telemetry" and "delegation chain auditability" language from the main grid. The measurable indicator is reconstruction capability on demand — a pick-five-random-sessions test that an assessor can run, where the full action chain (including failed tool calls and denied authorizations) can be reconstructed from telemetry within 15 minutes for a random sample of five agent sessions from the trailing 30 days. Coverage threshold is at least 95% of production agent deployments emitting compatible traces. Trace records must link user identity, agent identity, reasoning steps (where exposed), tool/MCP invocations with parameters and results, and downstream resource or data access under a single trace ID. Identity propagation is verified via IAM-issued credentials (identity token, scoped role, or signed assertion) carried through the chain (per IAM-04.1), not SIEM-side synthesized correlation IDs. Distributed tracing via OpenTelemetry (or equivalent) is the recommended implementation, with MCP servers instrumented to open spans for each tool invocation and the agent framework (LangChain, LangGraph, Bedrock Agents, Azure AI Agent Service, Vertex AI Agent Builder, CrewAI, custom) propagating trace context. Failed and denied calls are in scope because attack reconstruction depends on seeing what was attempted, not just what succeeded. Identity propagation through delegation chains depends on IAM having established agent/NHI identity patterns (typically IAM L3+); MON consumes what IAM provides. This is a dependency expressed in evidence (the trace must show real IAM-issued credentials, not fabricated correlation IDs) rather than a hard prerequisite — an organization can self-assess MON-04.1 even with uneven IAM maturity, but the evidence will surface the gap. The 95% coverage threshold accommodates a small set of legacy or third-party-hosted agents that cannot be instrumented without vendor changes; exceptions over time drop off as vendors catch up. The N/A clause prevents a pure-SaaS organization with no agentic systems from being penalized on a zero-denominator measurement; the zero-denominator case is documented in the AI inventory rather than scored as a fail.

**Evidence:**
- Distributed tracing configuration per production agent deployment (OpenTelemetry collector config, MCP server instrumentation, agent framework callbacks)
- Five randomly-selected agent-session reconstructions from the trailing 30 days showing full action chain including at least one failed tool call or denied authorization
- Trace samples showing IAM-issued credentials (identity tokens, scoped roles, or signed assertions) propagated through tool calls and delegation hops, rather than SIEM-side correlation IDs synthesized after the fact
- Coverage report showing at least 95% of production agent deployments emit compatible traces
- Delegation-chain example showing a multi-hop invocation with originating user identity preserved across hops
- For organizations claiming N/A: an inventory attestation that no agent deployments exist in production

#### MON-04.2 — Baseline-derived AI threat detection running at SOC cadence

- **Deployment Types:** All
- **Manual/Automated:** Automated
- **AICM Mapping:** LOG-03 (security monitoring and alerting), LOG-05 (audit logs monitoring and response), LOG-13 (failures and anomalies reporting)
- **External References:** OWASP LLM01:2025 Prompt Injection, OWASP LLM02:2025 Sensitive Information Disclosure, OWASP LLM10:2025 Unbounded Consumption, MITRE ATLAS, NIST AI RMF MEASURE-2.8
- **Key Indicator Rationale:** Operating detection content that combines signature-style rules (known prompt-injection patterns, known jailbreak indicators) with baseline-derived anomaly detection (per-identity session length, per-deployment output-distribution shifts, tool-call rate anomalies) — integrated into SOC triage with MTTA under 60 minutes for severity 1 and 2 — requires detection engineering, behavioral baselines, and a SOC that has absorbed AI as an in-scope telemetry source. Organizations meeting all three have the L4 operational posture.

**Control Objective:** AI-specific detection content fires on deviation from baselines computed and refreshed from observed telemetry rather than static thresholds alone, spanning prompt injection and jailbreak, sensitive-data exfiltration, anomalous agent action sequences, abnormal delegation depth, and cost anomalies. Alerts triage through the primary SOC queue at the same cadence as non-AI alerts of equal severity.

**Description:** L4 is the jump from "detections exist" (L3) to "detections are baseline-aware and run inside the normal SOC workflow at SOC cadence." The five required categories are: prompt-injection and jailbreak indicators (signature and behavioral), sensitive-data exfiltration patterns in model outputs (DLP/NER), anomalous agent action sequences relative to a per-deployment baseline, abnormal delegation-chain depth or fan-out, and cost/token consumption anomalies per identity. Baselines are computed from observed telemetry (via scheduled aggregation, ML/UEBA, or SIEM analytics) and refreshed at least monthly. MTTA is 60 minutes or less for severity 1 and 2 events over the trailing 90 days. At least one detection per category has fired and been triaged in the trailing 90 days, or a signed quiet-period justification from the SOC lead exists (cap: two consecutive quarters per category). The SOC-integration bar is measured by MTTA matching non-AI severity-1/2 alert handling — not a separate lower-priority AI queue. Baseline-derived detection is the technical jump: a static rule "alert on more than 100 tool calls per session" is L3 detection content; "alert on tool-call rate exceeding the per-identity p95 baseline by 3 sigma over a 10-minute window" is L4 detection content. The "computed from telemetry, refreshed at least monthly" requirement is deliberate — it prevents an organization from renaming static thresholds as "baselines" by attesting that any number ending up in a detection rule was derived from observed traffic and updates as that traffic shifts. Sensitive-data exfiltration detection depends on DLP / NER capability applied to model outputs — either from the SIEM's DLP module, a specialized AI-SPM product (Palo Alto AI Access Security, Prompt Security, Lakera, Protect AI, or equivalent), or provider-side content filters whose outputs are shipped to the SIEM. The quiet-period justification per category mirrors the pattern used in MOD-04.3 — some categories legitimately go quiet for a quarter, and that is acceptable if documented and not chronic.

**Evidence:**
- Detection rule inventory covering all five required categories with documented baseline logic per detection
- Baseline configuration artifacts showing per-identity or per-deployment thresholds computed from the trailing 30 days, including the aggregation job, UEBA model, or analytics pipeline that produces them and the refresh cadence (at least monthly)
- Sample baseline-refresh history showing thresholds updating over time as telemetry shifts, distinguishing computed baselines from fixed thresholds renamed as baselines
- 90-day alert history with acknowledgement timestamps and computed MTTA at or below 60 minutes for severity 1 and 2
- At least one fired-and-triaged alert per category over the trailing 90 days, or a signed quiet-period justification from the SOC lead
- SOC workflow documentation showing AI alerts routed through the primary severity-based queue rather than a side channel

#### MON-04.3 — Sensitive-data detection events on AI flows consumed by the SIEM

- **Deployment Types:** All
- **Manual/Automated:** Automated
- **AICM Mapping:** LOG-14 (input monitoring), LOG-15 (output monitoring), LOG-03 (security monitoring and alerting)
- **External References:** OWASP LLM02:2025 Sensitive Information Disclosure, OWASP LLM06:2025 Excessive Agency (downstream), NIST AI RMF MEASURE-2.6
- **Key Indicator Rationale:** Consuming sensitive-data detection events (DLP / named-entity recognition matches on AI prompts and responses) in the SIEM for every high-criticality deployment, with classification mapped to enterprise data-classification tiers, false-positive rate held below a tuning threshold, and a quarterly synthetic-injection test that verifies false-negative performance, requires telemetry pipelines from the detection engine into the SIEM, enterprise data-classification alignment, and a tuning loop. Organizations hitting all four are operating at the L4 main-grid description.

**Control Objective:** AI prompts and responses are scanned for sensitive data. Detection events are recorded in the SIEM tagged with the user or agent identity and the enterprise data classification, with the matched content redacted or hashed.

**Description:** This is the L4 "sensitive data detection in key AI inputs/outputs" line from the main grid, translated into a measurable telemetry-consumption standard. SIEM records carry matched classification, matched-pattern hash, user identity, deployment, and direction (input vs output), mapped to enterprise data-classification tiers (PII, PHI, PCI, credentials/secrets, internal-restricted identifiers). False-positive rate is measured monthly and kept below 20% based on triaged dispositions. At least 95% of high-criticality deployments have input-and-output match-event delivery to the SIEM; exceptions carry a named owner and expiration within 90 days. The quarterly synthetic-injection test submits a defined corpus covering PII, credential, and classified-data classes through production AI flows, with detection rate at or above 80% recorded and feeding tuning. The detection engine is deployed under APP (see APP-04.1/04.2); MON owns reliable ingestion, parsing, and SOC availability of the resulting match events. The KPI is deliberately scoped to the SIEM event — the pattern-match detection arriving as a consumable, classified, identity-attributed log record — rather than to deployment of the underlying detection engine. Engine deployment (Bedrock Guardrails sensitive-information filter, Azure AI Content Safety PII detection, Google Cloud DLP applied to Vertex AI, Prompt Security, Lakera, Protect AI Rebuff, Nightfall, Netskope AI, Microsoft Purview, Symantec DLP, or equivalent) is an APP capability and is cross-referenced rather than re-specified here; MON's responsibility starts when the engine emits an event. The match-pattern-hash requirement prevents the DLP alert itself from becoming a sensitive-data leak — the SIEM record identifies that a match occurred and of what class, without re-logging the raw content. Mapping to enterprise data-classification tiers (not an AI-specific ad-hoc tier list) keeps the AI DLP integrated with the broader data-security program and avoids a parallel classification system. The 20% false-positive cap is what distinguishes a tuned program from a firehose; above 20% the alerts become noise and lose operational value. The 80% synthetic-injection detection rate closes the inverse gameability — without it, an organization could tune the DLP toward near-zero recall (catching almost nothing, therefore almost no false positives) and still pass the false-positive gate. The synthetic corpus needs at least three classes (PII, credential, classified-data) so a single-class tune does not pass the floor. This KPI has a boundary with DAT — DAT owns data classification as a concept; MON owns SIEM consumption of classified-data pattern-match events flowing through AI systems — and with APP, which owns deployment of the detection engine itself.

**Evidence:**
- SIEM ingestion pipeline configuration showing sensitive-data match events from AI flows mapped to enterprise data-classification tiers
- Sample SIEM events showing matched classification, hashed pattern identifier, identity, and direction
- Monthly false-positive rate report based on analyst-triaged dispositions, showing below 20% over the trailing 90 days
- Quarterly synthetic-injection test record covering at minimum PII, credential, and classified-data classes, showing detection rate at or above 80% against the known corpus, with results feeding into tuning
- Coverage report showing at least 95% of high-criticality deployments have input-and-output match-event delivery to the SIEM
- Exception register with named owners and expiration dates within 90 days of issuance
- Cross-reference to APP control covering deployment of the underlying guardrail or DLP engine

---

### Level 5 — Efficient

#### MON-05.1 — Atomic automated response on high-severity AI events

- **Deployment Types:** All
- **Manual/Automated:** Automated
- **AICM Mapping:** LOG-03 (security monitoring and alerting), LOG-05 (audit logs monitoring and response), LOG-13 (failures and anomalies reporting)
- **External References:** OWASP LLM01:2025 Prompt Injection, OWASP LLM10:2025 Unbounded Consumption, OWASP ASI01 (Agent Goal Hijack), NIST AI RMF MANAGE-4
- **Key Indicator Rationale:** Running SIEM-to-action automation that can block a user session, revoke an agent credential, or circuit-break a runaway deployment within a measured end-to-end time from event to action — with a 95% success rate over 90 days and a named approver on the automation policy — requires real-time telemetry pipelines, SOAR integration, and organizational comfort with automated response on AI events. That is the L5 real-time-monitoring-with-automated-response bar.

**Control Objective:** Defined high-severity AI events trigger an atomic automated response through SOAR or equivalent within minutes of detection. This can include session termination, credential revocation, deployment throttling, or circuit-break shutdown. The automation acts reliably on matching events, reverses rarely, and operates under a named approver with recurring review.

**Description:** L5 is automated response, not just real-time detection. The defined high-severity events are confirmed prompt-injection exploitation, sensitive-data exfiltration above a defined volume, runaway agent cost/token consumption, or delegation-chain pattern matching a known attack signature. The measurable gates are (1) end-to-end mean time from event ingestion to automated action of 5 minutes or less over the trailing 90 days, (2) action rate of at least 95% on matching events, and (3) reversal rate below 5%. Playbooks have a named approver, documented scope statement, and quarterly review of action counts and outcomes. The named approver and scope statement are the governance wrapper — automated credential revocation or session termination needs explicit authority, not ad-hoc detection-engineer discretion. The 5% reversal cap protects against over-aggressive automation: if the automation is wrong more than one time in twenty, it is causing operational harm and the thresholds need tuning, not more automation.

**Boundary with IR (clean handoff clause).** MON-05.1 owns *atomic automated actions* — the SOAR fires a single bounded operation (terminate session, revoke credential, throttle deployment, circuit-break shutdown) within seconds of the triggering detection. Once that atomic action has executed, the MON capability is complete and the event is handed off to IR. IR owns *playbook orchestration and incident handling* — the multi-step response that follows the atomic action: severity classification, broader investigation, communications, escalation, evidence collection, and postmortem. Said another way: MON automates the kill-switch; IR runs the response. This KPI intentionally meets IR L5 at the handoff point. The harmonization pass should verify that IR references this atomic-action capability as a prerequisite rather than re-defining it, and that the handoff is logged (atomic-action timestamp and IR ticket creation timestamp) so the boundary is auditable.

**Evidence:**
- SOAR playbook definitions for each defined high-severity event type, with named approver and scope statement
- End-to-end timing report from event ingestion to automated action showing mean at or below 5 minutes over 90 days
- 90-day automated-action log showing action count, outcome (true positive / reversed), and matched-event coverage at or above 95%
- Quarterly review record of automated action counts, outcomes, and reversal rate with sign-off from the named approver
- Reversal-rate metric below 5% over the trailing 90 days

#### MON-05.2 — AI threat hunting and cross-deployment behavioral baselines

- **Deployment Types:** All
- **Manual/Automated:** Either
- **AICM Mapping:** LOG-05 (audit logs monitoring and response), LOG-03 (security monitoring and alerting), LOG-13 (failures and anomalies reporting)
- **External References:** MITRE ATLAS, OWASP LLM / ASI top-10 (current version), NIST AI RMF MEASURE-2.7, MANAGE-4.1
- **Key Indicator Rationale:** Operating a documented AI threat-hunting program on a quarterly cadence, driven by current threat intelligence (MITRE ATLAS updates, OWASP LLM/ASI revisions, vendor AI threat reports), with cross-deployment behavioral baselines that enable anomaly detection across the entire AI estate, requires a threat-hunting function, AI-specific threat intelligence feeds, and a unified telemetry surface across deployments. An L5 organization can show hunt reports with findings; an L4 organization cannot.

**Control Objective:** An AI threat-hunting program runs intelligence-driven hunts on a documented cadence, hands findings to IR, and produces detection-engineering output over time. Cross-deployment behavioral baselines support anomaly detection across the AI estate rather than per-deployment alone.

**Description:** L5 threat hunting is proactive, scoped to current threat intelligence, and produces artifacts — detections, null results documented for later revisit, or incidents if the hunt finds active compromise. The cadence is at least one hunt per quarter with no quarter skipped, plus an annual outcome floor of at least one hunt-derived detection rule promoted to production over the trailing 12 months. Each hunt is scoped to a current threat (MITRE ATLAS technique, OWASP LLM/ASI item, vendor advisory, or internal hypothesis) and produces a written report with findings, converted detections, or documented null result. Cross-deployment behavioral baselines — computed across the AI telemetry estate rather than per-deployment — support anomaly detection on identity behavior spanning multiple deployments, coordinated-attack indicators across tenants, and provider-level abuse patterns. The cadence is expressed as a per-quarter floor plus an annual outcome floor rather than as "quarterly" plus "four-in-12," because those two phrasings can drift apart: an organization could hit four hunts in a 12-month window while skipping a quarter, which a true quarterly cadence rules out. Mature programs hunt more often and with smaller scope per hunt. The cross-deployment baseline is the technical jump from L4's per-deployment baselines: detecting that the same user identity is running unusual query patterns across Bedrock, Azure OpenAI, and the internal RAG app in parallel is only visible when the baseline spans deployments. The annual promoted-detection floor is the "hunt-to-detection pipeline" indicator — a hunting program that never produces new detections is theater. The handoff to IR is the MON/IR boundary: MON hunts find things and hands the finding to IR; IR decides whether to declare an incident and runs the response.

**Evidence:**
- Threat-hunting program documentation including cadence, scope, methodology, and outcomes template
- Hunt reports showing at least one hunt completed in each of the trailing four quarters (no quarter skipped), each citing a current threat reference (MITRE ATLAS ID, OWASP LLM/ASI item, vendor advisory, or documented internal hypothesis)
- At least one detection rule in the SIEM with a change-log entry tracing its origin to a hunt finding in the trailing 12 months
- Cross-deployment baseline configuration showing anomaly detection spanning multiple AI deployments or tenants
- Documented handoff path from hunt findings to the IR program with a sample handoff record from the trailing 12 months

---

---

## 5. Infrastructure Security and Resilience (INF) <a id="5-infrastructure-security-and-resilience"></a>

**Category description:** Security and resilience of the hosting environment for AI workloads — compute (training clusters, inference servers), network isolation, cloud/datacenter infrastructure, host-level vulnerability management, runtime security on AI-serving hosts, and infrastructure-side resilience for AI-specific stateful components. Focuses on preventing infrastructure-level compromise and outage of AI systems. Enterprise cloud-organization policy (SCPs, Azure Policy, GCP Org Policy) and shared security-service deployment live in ORG; model-artifact integrity and behavior live in MOD; AI-component supply chain and CI/CD security live in DEV.


---

### Level descriptors (reference — from AISMM main grid)

- **L1 Initial:** AI workloads run on general-purpose infrastructure with default security settings. No dedicated or isolated environments for AI training or serving. Network segmentation between AI and other workloads is absent. Hosting infrastructure for AI not differentiated in vulnerability management or monitoring.
- **L2 Repeatable:** Basic separation between AI development, training, and production environments (e.g., separate accounts/subscriptions or network segments). AI hosting infrastructure included in standard vulnerability management. Initial security configurations documented for AI compute and serving environments but inconsistently applied.
- **L3 Defined:** Standardized AI infrastructure architecture with documented security baselines. Training and inference environments isolated with defined network boundaries. AI workloads provisioned using Infrastructure-as-Code with security configurations. Hosting infrastructure integrated into CSPM/CNAPP coverage. Hardening and resilience standards applied to AI compute resources.
- **L4 Capable:** AI infrastructure initial use of zero trust architectures. Model and app serving workloads implement runtime security monitoring and enforcement. Confidential computing evaluated for high-sensitivity training and inference workloads. Deployments managed using IaC with security checks in the pipeline. Resilience includes system prompts, agent configurations, and other AI-specific components.
- **L5 Efficient:** Zero trust architecture consistently enforced across AI infrastructure. Immutable infrastructure patterns for AI hosting where feasible. Confidential computing deployed for high-sensitivity workloads. AI infrastructure security continuously validated and adapted as new attack vectors emerge. Infrastructure changes automated with security gates.

---

### Scope note — INF boundaries

INF addresses the hosting environment for AI workloads: compute, network, host-level vulnerability and patch posture, runtime security on AI-serving hosts, infrastructure-side resilience of AI components, and CSPM/CNAPP coverage of AI infrastructure. PaaS and API/SaaS deployments offload the bulk of this surface to the provider; KPIs below call out when a KPI is primarily meaningful for self-hosted workloads. ORG owns enterprise cloud-organization policy (SCPs, Azure Policy, GCP Org Policy), account/subscription isolation policy, AI-SPM/AI-BOM visibility, and shared security-service deployment — INF inherits those controls and demonstrates AI-workload conformance. MOD owns what is loaded into the serving runtime (artifact integrity, provenance, versioning, model-level behavior). DEV owns AI-component supply chain (library scanning, AI-BOM generation, CI/CD security for AI code); INF owns vulnerability management of the hosts and runtimes the AI code runs on.

**API/SaaS scope floor.** Pure-API/SaaS organizations may have minimal INF surface — most compute and network controls live with the provider. INF maturity claims for such organizations should reference the orchestrator, RAG service, agent-host, and self-operated supporting-infrastructure footprint explicitly. Where that footprint is genuinely minimal, the organization defers to ORG (for shared cloud-organization policy and AI-SPM visibility) and to APP/DAT (for app-layer and data-layer controls) when making category-level claims, rather than claiming INF L3+ on an empty scope. The KPIs below carry forward this scope expectation in their Deployment Types fields.

---

### Level 2 — Repeatable

#### INF-02.1 — Separation of AI development, training, and production environments

- **Deployment Types:** Self-hosted (primary); PaaS and API/SaaS where the organization runs supporting infrastructure (orchestrators, agent frameworks, RAG services, vector stores)
- **Manual/Automated:** Either
- **AICM Mapping:** I&S-05 (production / non-production separation), I&S-06 (segmentation and segregation), DCS-05 (asset classification)
- **External References:** NIST AI RMF GOVERN-1.5, CSA AI Assessment Criteria INFRA-01 (approved hosting environment)
- **Key Indicator Rationale:** An organization that can produce an inventory of AI development, training, and production environments — with the inventory denominator drawn from an independent discovery signal rather than a self-reported list — and can show that production AI workloads are not co-resident with development or training workloads has moved past L1 general-purpose hosting into the L2 initial-separation state. Without environment separation the rest of the INF program has nowhere to stand.

**Control Objective:** AI workloads are classified development, training, or production, and production AI compute and serving sit on a separate account, subscription, or documented network boundary from development and training. The AI environment inventory is reconciled against an independent discovery signal (such as CSPM/CNAPP capabilities or AI-SPM where deployed).

**Description:** This is the L2 infrastructure baseline: no AI workload should be running in a shared personal or sandbox account, and a workload tagged production should not sit in the same environment as the notebook used to prototype it. Separation can be enforced by account/subscription boundary (preferred, because it inherits the blast-radius properties of the cloud provider's account model) or by a network-segmentation boundary (dedicated VPC/VNet, separate subscription, or equivalent) within a larger account, provided the boundary is documented. The environment inventory records account/subscription ID, classification, workloads hosted, and owning team. The independent-signal reconciliation requirement is the anti-gaming hook — a self-reported inventory is easy to keep clean by simply not listing the awkward workloads, so the denominator must come from a signal the application teams do not control: AI-SPM discovery output (Wiz AI-SPM, Prisma AI-SPM, Microsoft Defender for Cloud AI workloads view, or equivalent), GPU-billing telemetry from the cloud provider's cost APIs, or reconciliation against the AI-BOM (DEV-04.2) where it has been stood up. The reconciliation gate is zero discovered AI workloads absent from the inventory at quarter-close. The 90% production-classification threshold has a 180-day migration window for exceptions, each carrying a named owner. Scope covers self-hosted training clusters and inference servers, and also PaaS/API-consumer workloads where the organization owns supporting infrastructure such as orchestrators, agent frameworks, RAG services, and vector stores. Organizations that are pure API/SaaS consumers with no self-operated supporting infrastructure have minimal surface here; the KPI still applies to whatever infrastructure the organization does run. ORG sets the enterprise account-segmentation policy; INF demonstrates that AI workloads honor it.

**Evidence:**
- Environment inventory listing each AI environment with cloud account/subscription identifier, classification (development/training/production), workloads hosted, owning team, and separation boundary type
- Reconciliation report from an independent discovery signal (AI-SPM discovery export, GPU-billing telemetry filtered to AI workload SKUs, or AI-BOM cross-reference per DEV-04.2) showing zero discovered AI workloads absent from the inventory at the close of the most recent quarter
- Account or network diagram showing the separation boundaries between the three environment classes
- Reconciliation sample drawn from production AI invocation telemetry showing at least 90% of production AI workloads resolving to environments classified production, with exception records for the remainder carrying a named owner and a migration target date within 180 days

#### INF-02.2 — AI hosting infrastructure included in enterprise vulnerability management

- **Deployment Types:** Self-hosted (primary); PaaS and API/SaaS where the organization runs supporting infrastructure
- **Manual/Automated:** Automated
- **AICM Mapping:** TVM-03 (vulnerability identification), TVM-05 (external library vulnerabilities), TVM-07 (vulnerability remediation schedule), I&S-04 (OS hardening and base controls)
- **External References:** CSA AI Assessment Criteria INFRA-05 (patching and endpoint security), NIST SP 800-40
- **Key Indicator Rationale:** Producing a vulnerability-scan report that actually covers the AI training clusters, inference servers, and supporting infrastructure — with the same SLAs the rest of the enterprise operates under — requires that someone has inventoried the AI hosting footprint, tagged it, and wired it into the enterprise scanning program. An organization still in L1 treats AI hosts as invisible to vuln management.

**Control Objective:** AI hosting infrastructure including training clusters, inference hosts, orchestrator and agent-framework hosts, self-operated vector-store and RAG-service hosts, and the container images backing them are enrolled in the enterprise vulnerability scanning program under the same SLAs as everything else, with Critical and High findings tracked for remediation or formal exception.

**Description:** The L2 bar here is inclusion and basic SLA conformance, not automation sophistication. Scope covers both host-level scanning (operating systems and container runtimes) and image-level scanning (container base images, model-serving runtime images such as TorchServe, Triton, vLLM, KServe, Ray). AI libraries and framework supply-chain scanning (PyTorch, TensorFlow, Transformers, LangChain, model-format scanners) live in DEV; INF owns the host and the runtime the code executes in. Coverage is measured over the trailing 30 days against the inventory; coverage exceptions carry a named owner and enrollment date. SLA exceptions on Critical/High findings carry a named risk owner and expiration. Organizations with meaningful self-operated infrastructure carry the bulk of this scope; pure API/SaaS consumers still have orchestrator hosts, agent-framework servers, and RAG infrastructure that land in scope. The 95% coverage threshold reflects that some AI hosts — especially GPU-only training nodes — may require agent-compatibility work; the threshold is tight enough to require visible progress, loose enough to tolerate a handful of real exceptions with named owners.

**Evidence:**
- AI hosting inventory cross-referenced against the enterprise vulnerability-scanning tool showing coverage (at least 95% over the trailing 30 days)
- Vulnerability-SLA report for AI hosting infrastructure showing Critical and High finding counts, SLA status, and age distribution at the close of the most recent quarter
- Exception register for AI-host vulnerabilities outside SLA, with named risk owner and expiration date per exception
- Container image scan results for model-serving runtime images showing vulnerability counts and image build dates

---

### Level 3 — Defined

#### INF-03.1 — AI infrastructure provisioned from IaC against a hardened baseline

- **Deployment Types:** Self-hosted (primary); PaaS and API/SaaS where the organization runs supporting infrastructure
- **Manual/Automated:** Automated
- **AICM Mapping:** I&S-04 (OS hardening and base controls), I&S-01 (infrastructure and virtualization security policy), DCS-05 (asset classification)
- **External References:** CIS Benchmarks (Kubernetes, Linux, cloud-provider), NIST SP 800-190 (container security), CSA AI Assessment Criteria INFRA-01
- **Key Indicator Rationale:** A versioned AI-infrastructure security baseline that is referenced from production IaC modules — and that platform teams have actually wired their templates against — requires a central platform function, a written baseline, and product teams that have adopted the pattern. Organizations still at L2 provision AI infrastructure by hand or from forked templates with inconsistent hardening; the *enforcement* breadth at production IaC is what INF-04.2 carries.

**Control Objective:** A named, version-controlled AI-infrastructure security baseline covers host hardening and network defaults, and the production Infrastructure-as-Code that provisions training clusters, inference hosts, model-serving runtimes, orchestrator hosts, and self-operated RAG and vector-store infrastructure (e.g., Terraform, Bicep, Kubernetes manifests) imports or pins a version of that baseline.

**Description:** The baseline document is the "what good looks like" for AI infrastructure — it can be an extension of the enterprise hardening standard rather than a separate document, but it has to call out AI-specific defaults (GPU driver versions and security posture, model-serving port exposure, inference-endpoint TLS termination, vector-store network placement, notebook-service hardening where Jupyter/SageMaker Studio/Vertex Workbench are in use). Required baseline coverage spans host hardening (OS benchmark reference, container runtime configuration, secrets handling, logging enablement) and network defaults (default-deny egress, mandatory VPC/VNet placement, load-balancer and ingress defaults). The IaC reference takes one of three forms per stack: module import, policy reference, or explicit baseline-version tag. IaC is what gives the organization the repeatability signal: if a production AI host drifts from baseline, the fix is to update the template and redeploy, not to hand-patch. The L3 gate here is "the baseline exists and the production IaC references it" — the *enforcement* percentage (how often production changes actually flow through a passing gate against that baseline) is the L4 capability carried by INF-04.2; pulling that threshold into L3 would collapse the level discrimination. ORG sets enterprise-level cloud-organization policy; INF expresses the AI-workload-specific hardened baseline and demonstrates IaC-driven adoption. Kubernetes manifests count as IaC for this KPI when they are version-controlled and applied via GitOps or equivalent pipeline rather than kubectl apply from a laptop.

**Evidence:**
- AI-infrastructure security baseline document with version history and last-review date
- IaC repositories for AI workloads showing reference to the baseline (module imports, policy references, or explicit baseline-version tag per stack)
- Sample of three production AI environments demonstrating traceability from live resource to IaC commit SHA to baseline version
- Index of production AI IaC stacks with baseline-version reference per stack

#### INF-03.2 — CSPM/CNAPP coverage of AI infrastructure with tracked findings

- **Deployment Types:** Self-hosted (primary); PaaS and API/SaaS where the organization runs supporting infrastructure
- **Manual/Automated:** Automated
- **AICM Mapping:** I&S-08 (network architecture documentation), I&S-04 (OS hardening and base controls), DCS-05 (asset classification), CCC-07 (cloud configuration baseline assessment)
- **External References:** CSA AI Assessment Criteria INFRA-04 (continuous security assessment), NIST AI RMF MEASURE-2
- **Key Indicator Rationale:** An organization that can open its CSPM/CNAPP console, filter to AI workloads, and produce the current findings distribution with SLA status has already completed the prerequisites: AI tagging, policy coverage, ownership assignment, and a remediation rhythm. L2 organizations have CSPM for the enterprise but AI infrastructure is invisible or untagged within it.

**Control Objective:** AI hosting infrastructure is visible in the enterprise CSPM or CNAPP platform and runs against the production rule set plus a named AI-specific rule pack covering things like exposed model-serving endpoints, internet-reachable notebook services, and unencrypted self-operated vector stores. Critical and High findings are tracked to remediation or documented exception.

**Description:** AI infrastructure is brought into CSPM/CNAPP scope via resource tag, account classification, or policy group. The AI-specific rule pack is the part that differentiates this from "ordinary CSPM coverage with AI somewhere in scope." Examples of the AI-specific checks include exposed model-serving endpoints, permissive inference-endpoint IAM, unencrypted self-operated vector stores, and internet-exposed notebook services. The pack can be a tag-scoped subset of existing platform rules (major CSPM platforms ship AI-specific content by 2026), plus custom rules the security team has written for the organization's AI footprint — unauthenticated Bedrock agent aliases, public-read training-data buckets, agent-framework hosts with admin roles attached, Jupyter or SageMaker Studio notebooks directly reachable from the internet. AI-SPM product coverage (AI-BOM discovery, model registry visibility, shadow-AI detection) is an ORG capability and lives there; INF leverages whatever AI-SPM visibility ORG provides and combines it with the infrastructure posture view. Vulnerability scanning findings are tracked under INF-02.2; this KPI covers misconfiguration posture, which CSPM/CNAPP is the authoritative source for.

**Evidence:**
- CSPM/CNAPP dashboard export or screenshot showing the AI-workload scope, coverage percentage, and the named AI-specific rule pack
- Rule-pack definition document listing the AI-infrastructure-specific checks with rationale
- Findings report for AI infrastructure showing Critical/High counts, SLA status, and exception register at the close of the most recent quarter
- Sample finding trace showing detection, assignment to a named owner, remediation action or exception record

#### INF-03.3 — Network isolation and controlled egress for AI inference and training

- **Deployment Types:** Self-hosted (primary); PaaS and API/SaaS where the organization runs supporting infrastructure (agents, RAG, orchestrators, MCP servers)
- **Manual/Automated:** Automated
- **AICM Mapping:** I&S-03 (network security), I&S-06 (segmentation and segregation), I&S-09 (network defense), I&S-08 (network architecture documentation)
- **External References:** CSA AI Assessment Criteria INFRA-02 (network isolation), INFRA-03 (encrypted communications), OWASP LLM02:2025 Sensitive Information Disclosure
- **Key Indicator Rationale:** A documented egress allowlist for AI workloads — enforced by security group, firewall, egress proxy, or equivalent, and covering the actual set of model endpoints, MCP servers, and external services the workload calls — is not achievable without network architecture documentation per AI workload, a defined set of allowed destinations, and a mechanism to detect or block arbitrary outbound traffic. It is the concrete L3 signal that AI network segmentation has moved from "in a VPC somewhere" to a designed control.

**Control Objective:** Production AI workloads run inside a documented network-isolation boundary with deny-by-default egress restricted to a named allowlist of model APIs, MCP servers, RAG and vector-store backends, and platform dependencies. Externally reachable inference endpoints terminate at a named enterprise ingress control such as an API gateway or WAF-fronted load balancer, not directly on the workload host.

**Description:** This is the infrastructure-side network control. The isolation boundary is a subnet, VPC/VNet, namespace, or equivalent. The named ingress control for externally exposed inference endpoints is an API gateway, WAF-fronted load balancer, or service-mesh gateway. Allowlist exceptions carry a named owner and 180-day expiration. ORG sets the enterprise default-deny egress policy (via SCPs, Azure Policy, or cloud organization policy); INF demonstrates that AI workloads sit inside that policy with a workload-specific allowlist that actually reflects the AI workload's call pattern — an LLM agent calling Bedrock, Anthropic, an internal MCP server, a vector store, and a PDF-extraction service has a documented and enforced allowlist of exactly those destinations. VPC endpoints for cloud model APIs (Bedrock PrivateLink, Azure OpenAI Private Endpoint, Vertex AI Private Service Connect) are the preferred pattern for cloud-model egress because they remove the public internet from the path. Encryption-in-transit (TLS 1.2+ for external, mTLS or TLS for internal where network isolation alone is insufficient) is table-stakes under the hardening baseline referenced in INF-03.1 and is not repeated as a separate KPI.

**Evidence:**
- Network architecture diagram per production AI workload showing isolation boundary, ingress control, and egress allowlist enforcement point
- Egress allowlist configuration (security group, firewall, proxy, or VPC-endpoint policy) for a sample of three production AI workloads showing the documented set of allowed destinations
- VPC Flow Logs, proxy logs, or equivalent for a sample AI workload showing that egress outside the allowlist is blocked or alerted
- Exception register for AI workloads without a documented allowlist, with named owner and expiration within 180 days

---

### Level 4 — Capable

#### INF-04.1 — Runtime security monitoring and enforcement on AI inference and training hosts

- **Deployment Types:** Self-hosted (primary); agent-framework, orchestrator, and RAG hosts for all deployment types where the organization runs them
- **Manual/Automated:** Automated
- **AICM Mapping:** TVM-02 (malware and malicious instructions protection), TVM-04 (detection updates), I&S-09 (network defense), I&S-04 (OS hardening and base controls)
- **External References:** CSA AI Assessment Criteria INFRA-05 (endpoint security), NIST SP 800-190, MITRE ATLAS (Execution, Exfiltration tactics)
- **Key Indicator Rationale:** Multi-family runtime prevention on AI hosts plus deployment-time coverage verification is the L4 "runtime security monitoring and enforcement" state. An L3 organization has vulnerability scanning (INF-02.2) and CSPM/CNAPP visibility (INF-03.2) but often lacks coverage enforcement and falls back to detect-only mode on GPU-heavy AI hosts because of agent-compatibility or platform-team pushback.

**Control Objective:** Self-hosted AI inference, training, orchestrator, and agent-framework hosts run a runtime-security agent in prevention mode covering, at a minimum, code execution, container escape, and unauthorized process launch. Coverage is verified at deployment time so non-compliant hosts cannot enter production, and runtime alerts ship into the MON telemetry pipeline.

**Description:** The L4 jump from INF-02.2 (vulnerability scanning) and INF-03.2 (CSPM/CNAPP visibility) is active runtime defense plus coverage enforcement. The runtime agent runs in prevention mode for code execution, container escape, and unauthorized process launch as the floor. These three families map to the most exploited paths on AI hosts, which sit on GPU-class hardware and reach both external model endpoints and internal data stores, making them attractive lateral-movement targets. Kubernetes-native runtime security (Falco, Tetragon) covers the KPI when the deployment model is Kubernetes-native; commercial EDR (CrowdStrike Falcon, SentinelOne, Microsoft Defender for Cloud) and CNAPP runtime modules (Wiz Runtime Sensor, Prisma Cloud Defender) all count where deployed.

Coverage verification at deployment time is the L4 enforcement piece. An AI host without a runtime agent cannot enter production. Mechanisms vary by environment: golden-image baking that requires the agent to be present, init-script verification that fails the host's deployment when the agent doesn't register, or admission-control gates in Kubernetes that reject pods on nodes without coverage. The mechanism doesn't matter; what matters is that non-compliant hosts can't slip into production silently.

Alert routing requires a named owning team and severity-to-paging mapping. The exception pathway for agent-incompatible hosts exists because GPU-driver and kernel-version combinations still create compatibility headaches at the leading edge of AI hardware. Agent-incompatible hosts carry a named compensating control (network quarantine, agentless scanning, or restricted IAM) and a 180-day revisit so the exception doesn't become a permanent blind spot.

INF owns the runtime sensor on the host, the prevention-mode configuration, the deployment-time gate, and the on-call routing definition. MON owns enterprise telemetry aggregation, SIEM-side correlation, AI-specific detections, and the MTTA metric on those alerts. This boundary keeps INF from owning a number that depends on MON's pipeline performance.

**Evidence:**
- Runtime-security coverage report scoped to AI inference, training, orchestrator, and agent-framework hosts showing 100% coverage of production hosts with prevention mode enabled (exceptions tracked separately)
- Policy configuration showing code execution, container escape, and unauthorized process launch enabled in prevention mode on AI hosts (additional families allowed)
- Deployment-time verification artifact (e.g., golden-image manifest requiring the agent, Kubernetes admission policy, or init-script verification log) demonstrating that non-compliant hosts cannot enter production
- Alert-routing definition naming the on-call queue, owning team, and severity-to-paging mapping for AI-host runtime alerts, plus a sample showing alerts arriving in the MON-operated telemetry pipeline
- Exception register for agent-incompatible hosts showing compensating control and revisit date within 180 days
#### INF-04.2 — IaC pipeline security gates for AI infrastructure deployments

- **Deployment Types:** Self-hosted (primary); PaaS and API/SaaS where the organization runs supporting infrastructure
- **Manual/Automated:** Automated
- **AICM Mapping:** I&S-01 (infrastructure and virtualization security policy), I&S-04 (OS hardening and base controls), TVM-05 (external library vulnerabilities for IaC), DCS-05 (asset classification)
- **External References:** NIST SSDF PO.3, CIS Benchmarks, OpenSSF Scorecard
- **Key Indicator Rationale:** A pipeline gate that blocks AI-infrastructure IaC changes failing policy checks — with the trailing-period bypass count near zero and exception records well-formed — requires a working IaC foundation (INF-03.1), a policy-as-code engine, and a platform team that owns the gate. L3 organizations have IaC but merge changes without automated policy evaluation.

**Control Objective:** IaC changes targeting production AI infrastructure pass a required automated pipeline stage running policy-as-code checks (such as Checkov, OPA/Rego, or Kyverno) against the INF-03.1 baseline, with violating changes blocked at merge or apply time. Bypasses and exceptions are logged with a named owner and expiration.

**Description:** The gate enforces the hardened-baseline configuration at merge/apply time rather than relying on CSPM to catch drift afterward. This is the enforcement-breadth complement to INF-03.1: INF-03.1 establishes the baseline and the IaC reference; INF-04.2 carries the percentage that says production changes actually pass through it. Exceptions require a named approver and 90-day expiration; the change set outside the gate (the remainder under the 95%) triggers after-action review logged with a named owner. Scope covers Terraform / CloudFormation / Bicep / Pulumi / Kubernetes manifests / Helm charts that land AI infrastructure — training-cluster definitions, model-serving deployments, vector-store configurations, agent-framework hosts, orchestrator deployments. DEV owns CI/CD gates on AI-application code (SAST, SCA, AI-BOM generation, library vulnerability checks, model signing for self-hosted model artifacts handed off to MOD-04.1); INF owns the gate on the infrastructure that the application runs on. When a change fails the gate, the standard path is remediate-and-resubmit; the 95% passing-gate-or-exception metric over 90 days separates organizations whose gate is enforced from organizations whose gate is advisory. Pipeline bypasses that skip the gate entirely (break-glass merges, direct console changes, emergency hotfixes) count against the 95% metric and trigger after-action review.

**Evidence:**
- Pipeline definition showing the policy-as-code gate as a required stage on AI-infrastructure IaC repositories
- Policy-as-code ruleset under version control, mapped to the INF-03.1 baseline requirements
- 90-day audit of AI-infrastructure IaC changes showing passing-gate rate, exception records, and any gate bypasses with after-action review records
- Sample exception record showing approver, rationale, issuance date, and expiration within 90 days of issuance

#### INF-04.3 — Resilience of AI-specific stateful components

- **Deployment Types:** All (scope set by which AI-specific stateful components the organization operates)
- **Manual/Automated:** Either
- **AICM Mapping:** BCR-08 (backup), BCR-06 (business continuity exercises), BCR-11 (equipment redundancy), BCR-04 (business continuity planning)
- **External References:** NIST AI RMF MANAGE-4, ISO 22301
- **Key Indicator Rationale:** Backup-and-restore drills for the AI-specific stateful components — vector stores and their embedding indices, fine-tuned model artifacts, system prompts and agent configurations, RAG source caches, and the approved-model registry — that produce a numeric pass rate against RTO show that the AI-infrastructure resilience plan covers what is actually AI-specific, not just the underlying compute. Organizations at L3 back up the servers but have not yet worked out that the embedding index rebuild is the real recovery bottleneck.

**Control Objective:** The organization maintains backup-and-restore capability for AI-specific stateful components it operates such as self-operated vector stores and embedding indices, fine-tuned and self-hosted model artifacts, system prompts and agent configurations, RAG source caches, and the approved-model registry, with recorded RPO/RTO per component class and a restore drill exercised against each class annually.

**Description:** The AI-specific twist is that the stateful components that make an AI system functional are different from the stateful components of a classic app. A chatbot's availability depends on the model API, the vector store's embedding index, the system prompt, the agent configuration, and the RAG source corpus — losing any of those can effectively down the system even when the compute is healthy. Rebuilding an embedding index from scratch on a 10M-document corpus is a real-hours-to-days operation; an RPO/RTO target and a tested drill are what force the organization to size backup storage, re-embedding compute, or replication to hit those numbers. RPO/RTO targets are aligned with the owning workload's criticality, and each drill is logged against a named owner. For fine-tuned or self-hosted model artifacts, the drill includes signature and provenance verification at reload (coordinated with MOD-04.1). The 80% pass-rate threshold is what separates "we ran the drill and logged what happened" from "the resilience plan actually works" — an organization that restores zero of five component classes within RTO has documented capability gaps to close, not a passing KPI. For PaaS and API/SaaS deployments the provider owns the bulk of backup/restore; the organization owns whatever system-prompt, agent-configuration, and self-operated vector-store state sits outside the provider. Main-grid level-descriptor language "resilience includes system prompts, agent configurations, and other AI-specific components" maps directly to this KPI. GOV owns the approved-model-registry authority; INF owns backup of the registry data store so the authoritative source is recoverable.

**Evidence:**
- Recovery objectives (RPO/RTO) per AI-specific stateful component class, with owning workloads and criticality classifications
- Backup job configuration and 30-day backup-success report for each component class
- Restore drill record per component class within the trailing 12 months, showing planned RTO, measured restore time, and pass/fail disposition; pass rate computed across the drilled component classes meets the 80% threshold
- For self-hosted model-artifact restore drills, a linkage to MOD-04.1 signature and provenance verification at reload

#### INF-04.4 — Initial zero trust enforcement on a named AI infrastructure plane

- **Deployment Types:** Self-hosted (primary); orchestrator, agent-framework, and RAG-hosting infrastructure for all deployment types where the organization operates them
- **Manual/Automated:** Automated
- **AICM Mapping:** I&S-03 (network security), I&S-06 (segmentation and segregation), DCS-08 (equipment identification)
- **External References:** NIST SP 800-207 (Zero Trust Architecture), CISA Zero Trust Maturity Model
- **Key Indicator Rationale:** Identity-aware access deployed on a named subset of AI infrastructure access paths — with measurable flow-through and legacy paths still permitted as compensating routes — is the L4 "initial use of zero trust architectures" indicator from the main grid. It distinguishes organizations that have stood up an identity-aware access pattern for at least one production AI plane from organizations that have only piloted it on test paths. L5 (INF-05.1) extends the pattern across all planes and retires the legacy routes.

**Control Objective:** A named production AI infrastructure access plane, such as model-serving management, training-cluster admin, or the orchestrator/agent-framework control plane, is gated by zero trust access. Legacy network-only paths to that plane are inventoried with named owners and a retirement plan.

**Description:** This KPI fills the L4 main-grid descriptor "initial use of zero trust architectures" that previously had no INF KPI mapped to it. The L5 KPI (INF-05.1) lifts the bar to 95% flow-through, retires the legacy paths, and extends across all AI planes — INF-04.4 is the first-plane / 50–70% rollout step. The flow-through measurement is over the trailing 90 days for the named plane. An organization at L4 typically picks the highest-leverage plane first: model-serving management (where production model deployments are configured) or training-cluster admin (where data and weights are most concentrated) are common L4 starting points. The 50% flow-through threshold is calibrated so the rollout has visible adoption — not just a service stood up that few people use — without requiring the legacy retirement that L5 demands. Legacy paths in scope here are VPN-only, IP-allowlist-only, shared admin credentials, and long-lived access keys. ORG owns the enterprise identity-aware access service deployment (BeyondCorp-style gateway, Entra Conditional Access, Okta FastPass, AWS Verified Access, Cloudflare Access, Zscaler Private Access, or service-mesh equivalents); INF demonstrates that at least one AI infrastructure plane consumes it. The legacy-path inventory at L4 sets up the L5 retirement work.

**Evidence:**
- Documentation naming the AI infrastructure plane(s) in scope for L4 zero-trust deployment (e.g., "model-serving management plane," "training-cluster admin access")
- Identity-aware access policy definition for the named plane covering identity, device posture, and session context evaluation
- Access-log export from the identity-aware access service showing at least 50% of administrative/developer access events flowing through the path over 90 days for the named plane
- Inventory of legacy access paths to the named plane with named owner per entry

---

### Level 5 — Efficient

#### INF-05.1 — Zero trust enforcement extended to all AI infrastructure planes

- **Deployment Types:** Self-hosted (primary); orchestrator, agent-framework, and RAG-hosting infrastructure for all deployment types
- **Manual/Automated:** Automated
- **AICM Mapping:** I&S-03 (network security), I&S-06 (segmentation and segregation), I&S-09 (network defense), DCS-08 (equipment identification)
- **External References:** NIST SP 800-207 (Zero Trust Architecture), CISA Zero Trust Maturity Model
- **Key Indicator Rationale:** Identity-aware access extended across AI training clusters, inference management planes, and supporting-infrastructure consoles — with the legacy network-only paths retired — is the L5 "zero trust architecture consistently enforced" outcome. Organizations at L4 have zero trust stood up on a named plane (INF-04.4); zero trust is consistently enforced only when the rollout has reached all AI infrastructure planes and legacy paths are actually off.

**Control Objective:** Administrative and developer access to all AI infrastructure planes (training clusters, inference management, model-serving runtimes, orchestrator and agent-framework control planes, and self-operated vector-store consoles) is gated by zero trust access. Legacy paths such as VPN-only access, shared admin credentials, and long-lived access keys are retired. Service-to-service access consumes the IAM-owned workload-identity pattern (SPIFFE/SPIRE or service-mesh mTLS).

**Description:** The two signals here are the interactive access path (administrative / developer reach into AI management planes and training/inference consoles) and the service-to-service path (how an agent service authenticates to a vector store, how an orchestrator authenticates to a model endpoint, how a training job authenticates to a data lake). Both of those surfaces have historically been where long-lived keys and broad network allowlists live, and an L5 claim requires both to be gone. The identity-aware policy evaluates identity, device posture, and session context, issues short-lived credentials (≤8h interactive, ≤24h automation), and logs the decision. The 95% flow-through is measured over the trailing 90 days. Legacy paths still in use are tracked as exceptions with a named owner and 180-day retirement. This KPI is the L5 extension of INF-04.4: where INF-04.4 stood up identity-aware access on at least one named plane at 50%+ flow-through with legacy still permitted, INF-05.1 takes that to all planes at 95% flow-through with legacy retired. IAM owns identity provisioning, credential lifecycle, non-human identity patterns, and the workload-identity pattern itself; INF demonstrates that AI-infrastructure access paths consume those identity controls rather than side-channels. ORG owns the enterprise identity-aware access service deployment (BeyondCorp-style gateway, Entra Conditional Access, Okta FastPass, AWS Verified Access, Cloudflare Access, Zscaler Private Access, service-mesh equivalents); INF demonstrates AI-infrastructure conformance to it. Main-grid L5 "zero trust architecture consistently enforced across AI infrastructure" maps directly to this KPI — the distinction from L4 is the all-planes scope, the 95% flow-through threshold, and the retirement of the legacy paths.

**Evidence:**
- Identity-aware access policy definitions covering AI training clusters, inference management planes, orchestrator/agent-framework control planes, and self-operated vector-store consoles
- Access-log export from the identity-aware access service showing at least 95% of administrative/developer access events flowing through the path over 90 days, scoped to AI infrastructure planes
- Register of legacy access paths (VPN-only, IP-allowlist-only, long-lived access keys) with retirement date within 180 days per entry
- Service-to-service authentication inventory showing AI infrastructure components wired into the enterprise workload-identity pattern (SPIFFE/SPIRE identity ledger entries, service-mesh mTLS membership, cloud workload-identity federation report) — with the enterprise coverage percentage owned by IAM

#### INF-05.2 — Immutable infrastructure and confidential computing for high-sensitivity AI workloads

- **Deployment Types:** Self-hosted (primary for confidential computing); all deployment types where the organization operates supporting infrastructure (for immutable infrastructure)
- **Manual/Automated:** Automated
- **AICM Mapping:** I&S-04 (OS hardening and base controls), I&S-06 (segmentation and segregation), DCS-05 (asset classification), BCR-03 (business continuity strategy)
- **External References:** Confidential Computing Consortium reference architectures, NIST SP 800-190, Google Confidential VMs / AWS Nitro Enclaves / Azure Confidential Computing documentation
- **Key Indicator Rationale:** Production AI hosts rebuilt from versioned images on a host-age-since-last-rebuild cadence, plus a confidential-computing capability available and attestation-ready for workloads classified high-sensitivity under the enterprise data-classification scheme, requires both a platform pattern for immutable AI hosts and operational readiness for attested launch. Both are L5-class capabilities per the main grid.

**Control Objective:** Production AI inference and training hosts run under an immutable-infrastructure pattern: configuration changes happen via image rebuild rather than in-place mutation, and hosts that exceed the baseline's age-since-last-rebuild limit are redeployed. Confidential computing is an available option for workloads classified high-sensitivity under the enterprise data-classification scheme (such as Nitro Enclaves or Confidential VMs) with attestation verified before workload admission.

**Description:** Immutable infrastructure and confidential computing are both in the main-grid L5 descriptor and they address different threats.

Immutable infrastructure removes configuration drift and long-running-host compromise as a concern. If a host has been running for a month it gets replaced, which bounds the dwell time of any undetected compromise and forces the hardened-baseline posture to be re-asserted on every rebuild. The default host-age limit is 30 days, set in the INF-03.1 baseline; aged-out hosts are redeployed. Host age is measured as time since the host was last brought up from a versioned image, so a redeployment from an updated image resets the clock.

Confidential computing addresses host-administrator-in-the-loop threat models for workloads in the documented high-sensitivity scope: training data the organization cannot afford to expose to the cloud provider's operators, production workloads carrying regulated data, or model weights that are commercially valuable and must be protected even from privileged cloud operators. The L5 bar is that the capability is deployed and ready to use, with attestation infrastructure in place. An organization can elect to run a high-sensitivity workload on Nitro Enclaves, Confidential VMs, or equivalent and get attested launch. Whether every high-sensitivity workload actually runs on confidential computing is a separate operational decision that depends on workload-specific tradeoffs (cost, performance, operational complexity, ecosystem maturity).

The high-sensitivity scope references the enterprise data-classification scheme (the same scheme DAT-03.1 references; not AI-specific), which closes the scope-gaming path of declaring on the spot that zero workloads are high-sensitivity. The classification scheme is an enterprise infosec decision; INF demonstrates that the confidential-computing capability is operational and that immutable-infrastructure patterns hold for production AI hosts.

**Evidence:**
- Reference to the enterprise data-classification scheme (DAT-03.1) and the named top-tier definition that scopes high-sensitivity for INF-05.2
- Host-age-since-last-rebuild report for production AI inference hosts showing at least 90% within the baseline-defined age limit; redeployment records for hosts that aged out
- Image-rebuild pipeline definition and cadence (baseline image refresh and hot-CVE triggered rebuild)
- Confidential-computing capability inventory showing the platforms available (Nitro Enclaves, Confidential VMs, or equivalent) for AI workloads in the named high-sensitivity scope
- Attestation infrastructure documentation (verifier service, expected measurement registry, admission gate) and sample attestation record from a workload that has elected to run on confidential computing

---

## 6. Model Security (MOD) <a id="6-model-security"></a>

**Category description:** Security controls for AI models across deployment types (self-hosted, PaaS, API/SaaS), including model selection, integrity and provenance verification, model-level safety evaluation, adversarial robustness at the model layer, and model-behavior monitoring. Includes model-layer safety properties (bias, harm, hallucination tendencies) as documented by the provider or observed at the model's inference API. Application-layer defenses — guardrail deployment, system-prompt hardening, I/O validation, runtime enforcement — live in Application Security.


---

### Level descriptors (reference — from AISMM main grid)

- **L1 Initial:** Models deployed without security or safety review regardless of deployment type. For PaaS/API models, default configurations used without security assessment. For self-hosted models, no integrity controls or restrictions on unsafe file formats. No evaluation of third-party or open models before use. Model provider security posture not assessed.
- **L2 Repeatable:** Basic security requirements documented for model deployments (e.g., system prompt requirements). Third-party and open models undergo risk review for major deployments, including basic safety evaluation. For PaaS/API models, initial configuration reviews performed. For self-hosted models, unsafe file formats recognized but enforcement inconsistent. Model provider security assessments conducted for primary providers.
- **L3 Defined:** Standardized security and safety (bias/harm/hallucination) requirements for models based on deployment type and risk classification. PaaS/API model configurations hardened per documented standards. Self-hosted models require integrity verification and secure file formats. Formal risk assessment process for third-party and open models. Model versioning and rollback capability established. Initial monitoring for model behavior and performance in production.
- **L4 Capable:** Automated configuration validation for PaaS/API deployments. Model signing and provenance verification enforced for self-hosted models. Adversarial robustness testing standard for production use cases. Continuous monitoring for model drift, degradation, safety, and anomalous behavior across deployment types. Model risk metrics tracked and reported through governance processes.
- **L5 Efficient:** Automated model security verification across deployment types integrated into pipelines. Real-time monitoring with automated alerting on drift, safety issues, or anomalies. Adversarial testing integrated into CI/CD with defined thresholds. Proactive updates to model security controls as providers release changes or new attack vectors emerge.

---

### Scope note — MOD / APP boundary

Model Security KPIs address the model's own properties: which models are approved, which versions are pinned in production, whether self-hosted artifacts are signed and verified, whether the model has a documented safety evaluation at the model layer, and whether its behavior at the inference API is monitored and tested. Application-layer concerns — guardrail deployment (Bedrock Guardrails, Azure AI Content Safety, OpenAI moderation), system-prompt structure and hardening, tool/MCP restriction, runtime input/output validation, HITL enforcement, app-level auth — belong in Application Security (APP). Model-level parameter bounds (temperature, max_tokens, top_p, top_k) that the organization registers as acceptable for a specific model live in MOD; how an application applies those bounds at request time lives in APP.

---

### Level 2 — Repeatable

#### MOD-02.1 — Model inventory with pre-deployment risk review

- **Deployment Types:** All
- **Manual/Automated:** Manual
- **AICM Mapping:** MDS-12 (open model risk assessment), MDS-04 (model documentation requirements)
- **External References:** OWASP LLM03:2025 Supply Chain, NIST AI RMF MAP-1, MITRE ATLAS (Model Supply Chain)
- **Key Indicator Rationale:** An organization that maintains an inventory of production models across deployment types, with dated risk reviews for the major deployments, has moved past L1 shadow-AI adoption into L2 repeatable practice. The signal is consistent attention to the deployments that matter, not yet the L3 single-authoritative-registry-with-Council-approval bar.

**Control Objective:** An inventory of production models is maintained across PaaS, API/SaaS, and self-hosted deployments, with major deployments carrying a dated pre-deployment risk review. The inventory reflects current production usage at a documented refresh cadence.

**Description:** This KPI is the L2 foundation for Model Security. "Production" means any model invoked by an application serving real users or real business workloads, including internal tools broadly available inside the organization. The inventory captures model identifier and version, deployment type, and owning application for entries the organization knows about. "Major deployments" are defined inline as customer-facing, regulated, or ingesting untrusted content. Those entries carry a dated pre-deployment risk-review record, or one within the trailing 12 months for pre-existing models.

The L2 bar is consistent attention to the deployments that matter, with the inventory refreshed at a documented cadence (quarterly is typical at L2). The organization knows some adoption may go unrecorded between refreshes; that is the L2 reality of inconsistent shadow-AI capture. The L3 promotion happens in MOD-03.2 (single authoritative registry tied to Council approvals plus cloud-provider-enforced approval), where the inventory becomes the canonical source of truth and telemetry reconciliation closes the shadow-AI gap.

The criticality and major-deployment tag drives scope for MOD-02.2 (the high-criticality safety-review precursor) and eventually for MOD-03.1 (the L3 model-approval safety evaluation), so the definition needs inline criteria in the inventory itself rather than living in a separate document.

**Evidence:**
- Inventory export (spreadsheet, registry, or CMDB) listing production models with deployment type, owner, criticality classification, and risk-review date per major-deployment entry
- Sample of two risk-review records, drawn from across deployment types where present (at least one PaaS or API/SaaS entry, and one self-hosted or third-party/open entry if the organization runs them)
- Documented inventory refresh cadence (e.g., quarterly) with the most recent refresh date and the named owner of the refresh
#### MOD-02.2 — Model safety review for high-criticality deployments

- **Deployment Types:** All
- **Manual/Automated:** Manual
- **AICM Mapping:** MDS-04 (model documentation requirements)
- **External References:** Provider model cards / system cards (Anthropic model cards, OpenAI system cards, Google AI Principles evaluations)
- **Key Indicator Rationale:** An organization that conducts documented model-safety review for its important deployments — even without doing so systematically across the whole portfolio — has moved past L1 ad-hoc adoption into L2 initial practice. The signal is that someone is reading the model card or system card for the important deployments and recording the conclusion, even without a full registry or standardized evaluation criteria.

**Control Objective:** Every high-criticality production deployment in the MOD-02.1 inventory has a documented pre-production model-safety review sourced from the model's published safety characteristics. Reviews are scoped per unique model and deployment-type combination, not per individual deployment.

**Description:** This is the L2 precursor to MOD-03.1. At L2, the organization has not yet built a central approved-model registry with standardized safety-evaluation criteria — that's the L3 defined-process state. But it is no longer in L1 territory where models are adopted without any model-level safety consideration. At L2, the organization has identified a subset of deployments that matter — typically 10–30% of the portfolio, covering customer-facing chatbots and regulated-use-case assistants — and done a basic safety review for the models powering those deployments. The review draws on the model card, system card, or provider safety documentation, and records reviewer, date, model reference, and approval decision. The review itself can be a one-pager linking to the model card with a short assessor note. The important property is that it exists, is documented, and is tied to the high-criticality inventory entries. Per-model + deployment-type scoping (rather than per-deployment) keeps this realistic: twelve customer-support bots running on the same model and the same deployment pattern share one review, not twelve.

**Evidence:**
- High-criticality tag populated on MOD-02.1 inventory entries with inline criteria for what qualifies
- Safety review records (one per unique model + deployment-type combination covering high-criticality deployments) with reviewer name, date, model-card reference, and approval decision
- Sample of two or three high-criticality deployments showing traceability from deployment → inventory entry → model safety review

---

### Level 3 — Defined

#### MOD-03.1 — Model approval includes documented safety evaluation of the model

- **Deployment Types:** All
- **Manual/Automated:** Manual
- **AICM Mapping:** MDS-03 (model documentation), MDS-04 (model documentation requirements), MDS-06 (adversarial attack analysis), MDS-12 (open model risk assessment — for open/third-party models)
- **External References:** NIST AI RMF Map function; OWASP LLM04:2025 Data and Model Poisoning; model provider safety documentation (Anthropic model cards, OpenAI system cards, Google AI Principles evaluations)
- **Key Indicator Rationale:** Requiring each registry entry to carry a documented safety evaluation of the model itself means a central function has taken ownership of evaluating model-level safety characteristics before approving a model for enterprise use. That coordination is the L3 defined-process signal. An L2 organization has ad-hoc model adoption without a structured pre-approval safety review.

**Control Objective:** Every approved-model registry entry carries a safety evaluation applied under written criteria, signed off by a named approval authority before the model enters the registry. The evaluation is re-performed when a new model version is added.

**Description:** This KPI is the L3 safety layer for Model Security. It is deliberately about the model, not the application built on it — guardrails, system-prompt design, and I/O validation live in Application Security. The evaluation covers, at minimum: published safety characteristics (model/system cards, provider documentation, or independent evaluations); model-layer adversarial robustness and prompt-injection susceptibility; and bias/fairness on provider or independent benchmarks. The named approval authority is typically an AI Council, AI Governance Lead, or equivalent. The evaluation itself is mostly a document-review exercise at L3: reading the model card and system card for Claude / GPT / Gemini, reviewing HuggingFace safety assessments for open models, reviewing the provider's safety documentation, and recording a go/no-go decision with rationale. For open or custom-trained models where provider-supplied evaluations do not exist or are insufficient, the evaluation escalates to internally-run or vendor-commissioned assessment. The L3 goal is consistency: every approved model has a documented evaluation, stored with the registry entry, that justifies why the organization approved this model for enterprise use. Actively testing the model (running adversarial test suites, measuring bias on custom scenarios) is an L4 capability covered by MOD-04.2.

**Evidence:**
- Approved model registry entries showing attached safety-evaluation artifacts (model card references, system card excerpts, independent evaluations)
- Written evaluation criteria describing what the organization looks for in a model's safety posture (refusal behavior, jailbreak susceptibility on published benchmarks, known bias findings, prompt-injection resistance at the model layer)
- Sign-off records by the approver (named individual or function — e.g., AI Council, AI Governance Lead)
- Evidence that the evaluation was re-performed (or explicitly validated as unchanged) when a new model version entered the registry

#### MOD-03.2 — Approved models and pinned versions in production

- **Deployment Types:** All
- **Manual/Automated:** Automated
- **AICM Mapping:** MDS-12 (open model risk assessment — registry entries), MDS-09 (model signing / ownership verification — cross-reference for self-hosted version identity)
- **External References:** NIST AI RMF Govern function; OWASP LLM03:2025 Supply Chain Vulnerabilities
- **Key Indicator Rationale:** Restricting production invocations to registry-approved model + version identifiers only happens when a central function has taken ownership of model selection, risk review, and change management. This requires the L3 AI Council or equivalent to exist and be making approval decisions that get translated into technical enforcement — something an L2 program hasn't done.

**Control Objective:** Production AI workloads invoke only registry-approved models pinned to a specific version. Floating aliases such as "latest" are prohibited in production, exceptions are documented and time-bounded, and rollback to the prior approved version has been exercised.

**Description:** Each registry entry records model identifier, version, approved deployment types, risk classification, approval record, and accepted parameter bounds (temperature, max_tokens, top_p, top_k). Exception records carry a named approver and expiration within 90 days of issuance. Enforcement mechanisms vary by deployment type and should match the organization's existing cloud-governance plumbing: AWS Service Control Policies restricting `bedrock:InvokeModel` to approved model ARNs; Azure Policy restricting Azure OpenAI deployed model SKUs and versions; GCP Organization Policy / IAM conditions restricting Vertex AI endpoint publisher models; for API/SaaS direct consumption (OpenAI API, Anthropic API, Copilot, Agentforce), egress network policy or CASB enforcement limiting outbound calls to approved endpoints; for self-hosted, deployment manifests / infrastructure-as-code pinning to a specific commit SHA or registry version. The 95% threshold accommodates edge cases — experimentation accounts, research workloads that briefly escape the registry — without eroding the production control. The rollback drill is the proof that version pinning isn't a one-way door; an organization that pins but can't roll back has built a brittle control.

**Evidence:**
- Approved model registry with entries showing model ARN/SKU/endpoint identifier, version string, approved deployment types, risk classification, approval record, and accepted parameter bounds (temperature, max_tokens, top_p, top_k)
- Invocation telemetry showing 30-day invocation-to-registry match rate across CloudTrail `bedrock:InvokeModel`, Azure OpenAI activity logs, GCP Cloud Logging for Vertex AI, egress or CASB telemetry for API/SaaS consumption, and self-hosted serving logs where present
- SCP / Azure Policy / GCP Org Policy definitions or CASB / egress policy definitions enforcing approved-model restrictions
- Rollback runbook with evidence of execution in staging or non-production within the trailing 12 months

#### MOD-03.3 — Baseline production monitoring of model behavior

- **Deployment Types:** All
- **Manual/Automated:** Automated
- **AICM Mapping:** MDS-10 (model continuous monitoring)
- **External References:** NIST AI RMF MEASURE-2.6, OWASP LLM09:2025 Misinformation (hallucination baseline)
- **Key Indicator Rationale:** Producing a real per-deployment behavioral metric (not request counts) means someone built the logging pipeline, defined a metric, and assigned an owner who reads it. That is the L3 "initial monitoring for model behavior" bar without slipping into the L4 "continuous monitoring with alerting" bar.

**Control Objective:** Each production model deployment in the MOD-02.1 inventory reports at least one model-behavior metric beyond request counts and latency, with a named deployment owner who reviews it on a recorded cadence.

**Description:** Acceptable metrics include hallucination/groundedness score on a fixed eval set, refusal rate, output-length distribution, or task-specific accuracy — anything that captures the model's behavior at its inference API for the deployment's workload. Guardrail-block rate counts as a behavioral signal about the model (how often the model's output is flagged downstream) provided the metric is attributed to the model deployment rather than to the guardrail configuration itself — the guardrail's own performance is an APP or MON concern. The 14-day refresh cadence keeps the metric active enough to catch regression without demanding real-time pipelines (which is an L4 expectation under MOD-04.3). The monthly review and named reviewer are what turn this from a dashboard into a control: an L3 organization can point to who looked at the number last and when. Letting the deployment owner pick the metric is deliberate at L3 — a prescriptive minimum metric set is an L4+ move.

**Evidence:**
- Dashboard or report per deployment showing the chosen behavioral metric and its refresh timestamp (CloudWatch / Azure Monitor / Vertex AI Model Monitoring, or internal telemetry)
- Review log (ticket, meeting notes, or dashboard comment) showing at least three monthly reviews in the trailing 90 days for a sample of deployments
- Definition document for the metric and how it is computed

---

### Level 4 — Capable

#### MOD-04.1 — Signing, load-time verification, and provenance attestation for self-hosted models

- **Deployment Types:** Self-hosted only (PaaS and API/SaaS model integrity is provider-owned)
- **Manual/Automated:** Automated
- **AICM Mapping:** MDS-09 (model signing / ownership verification), MDS-08 (model integrity checks), MDS-02 (artifact scanning)
- **External References:** OpenSSF Model Signing (OMS) / sigstore model-transparency, in-toto attestation, OWASP LLM03:2025 Supply Chain (lack of provenance)
- **Key Indicator Rationale:** Combining build-time signing, load-time signature verification with fail-closed serving, and a recorded provenance attestation for every production artifact requires signing coverage across the supply chain, a verifier wired into the serving stack, and a transparency-log or attestation store that ties each artifact to a named signer and build pipeline. Organizations that block 100% of unsigned or unverifiable loads in production and can show the attestation record for a production model have the automated enforcement posture L4 describes.

**Control Objective:** Every self-hosted model in production is cryptographically signed at build time and carries a provenance attestation. The serving runtime verifies signatures at load against approved signer identities and fails closed on unsigned or invalid artifacts, enforced by a policy gate rather than operator discipline.

**Description:** The provenance attestation per artifact records signer identity, build pipeline reference, artifact digest, and transparency-log inclusion proof where applicable. The enforcement pattern is a policy gate — a Sigstore Model Validation admission controller, Kyverno or OPA policy, or serving-runtime pre-check — rather than operator discipline; if the control depends on an operator remembering to verify, it is not L4. Vendor-supplied model artifacts that arrive unsigned are re-signed locally under the organization's signing identity after completing the ingest-time scan, and the provider's attestation for signature origin is noted in the artifact's registry entry so the provenance chain is complete. The scope is self-hosted because PaaS and API/SaaS model integrity is the provider's responsibility; organizations with no self-hosted footprint mark this KPI not applicable and that is the correct answer.

**Evidence:**
- Policy gate configuration showing fail-closed behavior on unsigned or unverifiable artifacts
- Registry of approved signer identities and the verification trust root, with a change log
- 30-day audit log of load-time verification events including at least one denied load (real or drill)
- Provenance attestation record for a sample production model showing signer identity, build pipeline reference, artifact digest, and transparency-log inclusion proof
- Registry entries for vendor-supplied unsigned models showing the locally-applied organization signature and the recorded provider attestation note

#### MOD-04.2 — Adversarial and bias testing at the model layer

- **Deployment Types:** All (testing is performed against the model at its inference API — base-model behavior — not against the deployed application stack; for self-hosted and fine-tuned models, testing can additionally reach model weights)
- **Manual/Automated:** Either
- **AICM Mapping:** MDS-06 (adversarial attack analysis), MDS-07 (robustness / model hardening)
- **External References:** NIST AI RMF MEASURE-2.7, OWASP LLM09:2025 Misinformation, MITRE ATLAS
- **Key Indicator Rationale:** Actively testing each approved model against adversarial inputs, prompt-extraction, jailbreaks, and bias/harm benchmarks at the model layer — with findings triaged to severities and owners, refreshed within the trailing 12 months — is not achievable without a standing AI red team function and a version-controlled test methodology. If an organization can produce a current model-layer test report for each approved model, that is the L4 expectation.

**Control Objective:** Approved models in production are tested for adversarial robustness or bias and harm at the model layer with documented thresholds. Findings are severity-rated and tracked to remediation or accepted risk under a named owner.

**Description:** Test scope covers, at minimum: prompt-injection susceptibility, system-prompt extraction resistance, jailbreak resistance against a named benchmark, and at least one provider or independent bias/harm benchmark. Each category includes at least one externally-sourced or peer-reviewed benchmark to prevent weak-test gameability. The test subject in this KPI is the model, not the application. The test harness talks directly to the inference API — Bedrock, Azure OpenAI, Vertex AI, the OpenAI or Anthropic API, or the self-hosted serving endpoint — with the parameter bounds the organization registered for that model. Guardrail bypass tests, system-prompt robustness tests, and tool/MCP misuse tests that depend on the deployed application configuration belong in Application Security (APP L4), not here. This split matters because a model that fails a model-layer jailbreak benchmark is a model the organization should reconsider approving; a system prompt that fails a bypass test is a system prompt the app team needs to rework. For self-hosted and fine-tuned models, the methodology can additionally reach model weights (token-level adversarial attacks for LLMs, FGSM/PGD for vision models) since the organization controls the weights. The version-controlled methodology document defines which techniques apply per model family.

**Evidence:**
- Test report per approved model in the registry dated within the trailing 12 months, including test suite version, model-level parameters used, pass/fail per category, and severity-rated findings
- Named benchmark or methodology document (internal red-team playbook, HarmBench, garak configuration, Azure AI Foundry evaluators, Bedrock model evaluation jobs) under version control
- Remediation tracker showing each finding linked to a ticket or a signed risk-acceptance entry
- Sample finding showing the full lifecycle: detection, triage, owner assignment, resolution or accepted risk

#### MOD-04.3 — Drift and model-behavior monitoring with routed alerts

- **Deployment Types:** All (PaaS and API/SaaS deployments implement drift detection against observable model outputs since the provider controls weights; self-hosted deployments can add weight-level or embedding-level drift signals)
- **Manual/Automated:** Automated
- **AICM Mapping:** MDS-10 (model continuous monitoring), MDS-11 (model failure)
- **External References:** NIST AI RMF MEASURE-2.8, NIST AI RMF MANAGE-4
- **Key Indicator Rationale:** An organization that can produce per-deployment per-quarter investigated-alert records with MTTA under 60 minutes has the L4 operational muscle, because the monitoring pipeline, on-call routing, and accountability must already exist to produce those records.

**Control Objective:** Production model deployments run drift or behavioral-change monitoring with documented thresholds. Alerts route to a named on-call queue, and investigated alerts produce a recorded action outcome.

**Description:** Acceptable drift signals include output-distribution shift, refusal-rate change, provider-announced behavior change, or task-accuracy drop on a fixed eval set. The two-monitor minimum keeps deployments from declaring a single "all green" dashboard the whole monitoring story: a drift signal catches behavioral change, an availability signal catches the invocation path falling over, and neither substitutes for the other. Action outcomes from an investigated alert are remediation, tuning, risk acceptance, or a confirmed false-positive disposition — any documented triage counts. The quiet-period justification exists because some deployments are low-volume enough that a zero-alert quarter is the expected state; the owner writes down why, and the justification may not extend beyond two consecutive quarters per deployment (in quarter 3, either an investigated alert or a recalibration of the monitor configuration is required). This KPI is model-behavior monitoring — guardrail-violation telemetry aggregation, SIEM pipelines, and cross-deployment detection rules live in MON.

**Evidence:**
- Monitor configurations per deployment showing metric, threshold, and alert destination (CloudWatch alarms on Bedrock invocation metrics, Azure Monitor alerts on Azure OpenAI diagnostic logs, Vertex AI Model Monitoring jobs, or self-hosted serving telemetry)
- On-call runbook entry describing triage for model-behavior alerts
- 90-day alert history from the ticketing or alerting platform with acknowledgement timestamps and computed MTTA
- Per-deployment per-quarter record showing either an investigated alert with action outcome or a signed quiet-period justification, demonstrating no deployment has used the quiet-period justification for more than two consecutive quarters without recalibration

---

### Level 5 — Efficient

#### MOD-05.1 — CI/CD gating on model registry and version updates

- **Deployment Types:** All (applies to PaaS/API model-version changes in the registry, self-hosted retrain or fine-tune releases, and any registry-level change to an approved model's accepted parameter bounds)
- **Manual/Automated:** Automated
- **AICM Mapping:** MDS-06 (adversarial attack analysis), MDS-07 (robustness / model hardening), MDS-02 (artifact scanning)
- **External References:** NIST AI RMF MEASURE-2.7, OWASP LLM04:2025 Data and Model Poisoning
- **Key Indicator Rationale:** Automated gating with fail-closed thresholds on model registry changes requires a stable model-layer test harness, version-controlled thresholds, pipeline infrastructure that honors gate decisions, and product teams that have accepted the constraint. Shipping zero model registry updates that bypassed the gate over 90 days is the outcome only an L5 program achieves.

**Control Objective:** Model registry changes pass an automated pipeline gate that runs the MOD-04.2 model-layer test suite against version-controlled thresholds, blocks regressions, and verifies MOD-04.1 signature and provenance for self-hosted promotions. Bypass requires a time-bounded exception with a named approver.

**Description:** "Registry changes" covers new PaaS/API model versions, provider-announced behavior changes requiring re-approval, self-hosted retrain/fine-tune promotions, and updates to accepted parameter bounds. The gate is model-layer: it runs the model-layer tests from MOD-04.2 against the proposed registry change and compares to registered thresholds. For self-hosted promotions, the same pipeline stage also asserts that the artifact carries a valid signature and provenance attestation per MOD-04.1, so the L5 promise of "automated model security verification across deployment types integrated into pipelines" is closed at the gate rather than relying only on the MOD-04.1 runtime verification that happens later at model load. Application-layer CI gates — system-prompt regression tests, guardrail-effectiveness tests, end-to-end prompt-injection tests on the deployed app — live in APP L5 and run on a separate pipeline triggered by app changes. Standard exceptions require a documented exception with named approver and 90-day expiration. They follow the ordinary approval chain, may be renewed once for a total duration of 180 days, and then require either remediation or a fresh exception record with new justification; auto-renewal of standard exceptions is prohibited. A "vendor-blocked" exception category is available when remediation depends on a PaaS/API provider fix: the first 180-day window requires executive approver (CISO or delegate) sign-off, and any extension beyond that initial 180-day period requires executive risk committee (or board risk committee) sign-off, with no automatic renewal. The 90-day trailing-period zero-bypass metric is the L5 signal: at L4 a gate exists, at L5 the gate is never bypassed silently.

**Evidence:**
- Pipeline definition showing the model-layer test-and-threshold stage as a required gate (not optional / advisory)
- Version-controlled threshold file with change history
- 90-day audit of registry changes showing each change maps to either a green gate run or an unexpired exception record
- Sample exception record showing approver, rationale, issuance date, and expiration date within 90 days of issuance
- Sample "vendor-blocked" exception record showing CISO-or-delegate approval and expiration within 180 days of issuance, with any extension beyond the initial 180-day period carrying executive risk committee (or board risk committee) sign-off
- Renewal record for at least one standard exception demonstrating the one-renewal cap (total duration not exceeding 180 days) and a fresh exception record (not auto-renewal) where continued coverage was required
- Pipeline artifact for a self-hosted promotion showing the gate enforced both the model-layer test threshold pass and a valid MOD-04.1 signature/provenance verification

#### MOD-05.2 — Proactive response to provider and ecosystem changes

- **Deployment Types:** All (primary weight on PaaS and API/SaaS where the provider controls change cadence; self-hosted covered through open-model source monitoring)
- **Manual/Automated:** Automated
- **AICM Mapping:** MDS-10 (model continuous monitoring — primary), MDS-11 (model failure), MDS-12 (open model risk assessment — reassessment of Hugging Face model-card changes against prior risk review)
- **External References:** OWASP LLM03:2025 Supply Chain, NIST AI RMF MANAGE-4.1
- **Key Indicator Rationale:** Closing the loop from "provider publishes a change" to "tracked impact assessment and action" within a defined SLA requires automated detection across AWS / Azure / GCP / OpenAI / Anthropic release feeds, deprecation notices, provider health dashboards, open-model source monitoring, and CVE feeds for model-adjacent components, plus an owner for each deployment and an operational rhythm. It is the L5 proactive posture the main grid describes.

**Control Objective:** Automated feeds detect provider-side model changes across every provider and open-model source in the inventory. Each detection opens a tracked item routed to the owning team, and production-affecting changes (such as deprecations or safety-behavior regressions) trigger a documented impact assessment within a defined SLA.

**Description:** In-scope changes include new foundation-model versions, deprecation notices, model-layer safety-behavior updates, and published vulnerabilities in model dependencies. Production-affecting is defined as deprecation, model-layer safety regression, or CVE with CVSS >=7.0. The detection scope is model-ecosystem change at the model layer: Bedrock model-deprecation announcements, Azure OpenAI retirement notices, OpenAI model-sunset notices, Anthropic model-lifecycle notices, Vertex AI publisher-model changes, Hugging Face model-card updates or license changes for open models in the inventory, and CVE feeds for model-serving components. For open-model source changes the impact assessment includes a reassessment of the MOD-02.1 pre-deployment risk review entry, with the result recorded as "no change," "updated risk review," or "deployment deprecated." Application-layer provider changes (guardrail product updates, content-safety policy changes, moderation-API behavior changes) overlap with APP and should be surfaced to both teams; the model-layer detection lives here. The 95% six-month compliance threshold separates organizations with a durable detection program from those running a one-time dashboard.

**Evidence:**
- Feed/detector configuration covering provider release notes and deprecation announcements (AWS What's New + Bedrock model lifecycle, Azure OpenAI retirement page, OpenAI model-sunset announcements, Anthropic model-lifecycle, Vertex AI release notes), model-card updates for Hugging Face models in the inventory, and CVE feeds for model-serving components
- Ticket query showing detections over 6 months with open-time and first-response-time columns
- Sample impact assessment for a real provider change (for example, a Bedrock or Azure OpenAI model deprecation) completed within SLA
- Metric report showing 95% or higher timeline compliance over the trailing 6 months

---

---

## 7. Application Security (APP) <a id="7-application-security"></a>

**Category description:** Security for the implementation of AI applications across deployment types (self-hosted, PaaS, API/SaaS), including system-prompt structure and hardening, guardrail deployment (Bedrock Guardrails, Azure AI Content Safety, OpenAI moderation, NeMo, and equivalents), input/output validation, tool and MCP restrictions in application code, agent boundaries, runtime monitoring of model I/O, human-in-the-loop enforcement in application flow, application-level authorization logic, and AI-specific CI/CD testing of the deployed app stack. Model-level properties (selection, approval, version, integrity, provenance, adversarial robustness at the model's inference API) live in Model Security; identity and credential lifecycle live in IAM; telemetry aggregation and SIEM integration live in Security Monitoring; data access controls and RAG source approval live in Data Security.


---

### Level descriptors (reference — from AISMM main grid)

- **L1 Initial:** AI applications rely solely on traditional application security controls. No AI-specific input or output validation. Prompt injection risks unaddressed. No guardrails for model interactions. Agentic components and MCP servers, if used, deployed without security boundaries or tool restrictions.
- **L2 Repeatable:** AI-specific application risks identified (prompt injection, insecure outputs). Initial input/output validation for AI components or some apps. Guardrails deployed for some high-risk applications. Basic API security for AI endpoints (authentication, rate limiting). Agent tool permissions defined but inconsistently enforced. MCP servers, if used, deployed without formal security review.
- **L3 Defined:** AI application security requirements documented. Input validation standards include prompt injection mitigations. Output filtering requirements defined for sensitive content. Guardrails deployed for critical AI applications but coverage incomplete. Initial agent security boundaries defined with tool access restrictions. MCP/A2A integrations undergo security review for new deployments. Initial AI-specific security testing.
- **L4 Capable:** Guardrails deployed consistently across production AI applications. Input/output validation automated in deployment pipelines. Runtime protection monitors AI application behavior. Agent orchestration hardened against drift and unauthorized actions. Human-in-the-loop enforced for high-risk agent actions; alerting otherwise. AI-specific security testing integrated into CI/CD.
- **L5 Efficient:** Guardrails continuously tuned based on emerging attack patterns. Real-time detection and response for prompt injection and output anomalies. Agentic security automated with policy engines governing tool access and multi-agent interactions. AI application red teaming conducted regularly.

---

### Scope note — APP boundaries with neighboring categories

Application Security KPIs address what the organization builds around and on top of the model: system-prompt structure and hardening, guardrail deployment and configuration, input/output validation, runtime enforcement of tool and MCP restrictions in the app, HITL implementation at the workflow-engine layer, and testing of the deployed application stack (system prompt + guardrails + tool restrictions + app-level auth logic) against prompt-injection, jailbreak, and tool-misuse scenarios.

Adjacent categories own related but distinct scope. **MOD** owns the model itself (selection, approved-model registry, version pinning, self-hosted signing, and adversarial/bias testing of the base model at its inference API with registered parameter bounds). APP L4 adversarial testing hits the deployed app stack; MOD L4 adversarial testing hits the base model. **IAM** owns identity, credential lifecycle, non-human identity patterns, MCP/tool OAuth scopes, and rate-limit policy on identities — APP gates which tool the agent can invoke and how HITL is enforced at the workflow layer, IAM defines what the resulting identity is allowed to reach and the rate-limit envelope on it. **MON** owns telemetry collection, SIEM aggregation, novel-pattern detection, and cross-deployment correlation — APP deploys the guardrails; MON ingests and correlates the logs they emit and surfaces patterns back to APP. **DAT** owns RAG source approval, vector-store tenant isolation, and permission-aware retrieval — APP owns what the app code does at runtime with retrieved content (injection filtering before prompt assembly, output handling). **DEV** owns CI/CD pipeline infrastructure, SCA/SAST tooling, supply-chain scanning of MCP server packages and AI libraries, and AI-BOM — APP defines the AI-specific test gates (prompt regression, guardrail validation, app-stack adversarial tests) that run inside that pipeline.

---

### Level 2 — Repeatable

#### APP-02.1 — AI application inventory with AI-specific risk fields

- **Deployment Types:** All
- **Manual/Automated:** Manual
- **AICM Mapping:** AIS-02 (application security baseline requirements), AIS-08 (input validation), AIS-09 (output validation)
- **External References:** OWASP LLM01:2025 Prompt Injection, OWASP LLM05:2025 Improper Output Handling, OWASP LLM02:2025 Sensitive Information Disclosure
- **Key Indicator Rationale:** An organization that maintains an inventory of production AI-enabled applications with model and flag metadata, plus dated risk assessments for major applications, has moved past L1 shadow adoption into L2 repeatable practice. The signal is consistent attention to the apps that matter, not yet the L3 single-authoritative-inventory bar.

**Control Objective:** An inventory of production AI-enabled applications is maintained with the model used and customer-facing or untrusted-content flags. Major applications carry a dated prompt-injection and output-handling risk assessment. The inventory reflects current production usage at a documented refresh cadence.

**Description:** This is the L2 foundation for Application Security. The inventory captures production AI-enabled applications with the model they use (cross-referenced to MOD-02.1) and AI-specific flags: customer-facing and untrusted-content. The untrusted-content flag is true when the app processes free-text input, ingests documents or URLs, or calls tools.

"Major applications" are inline-defined as customer-facing, regulated, agentic, or processing untrusted content. Those entries carry a dated prompt-injection and output-handling risk assessment, with a 12-month maximum age for pre-existing applications. The L2 bar is consistent attention to the apps that matter, with the inventory refreshed at a documented cadence (quarterly is typical at L2). The organization knows some apps may go unrecorded between refreshes; that is the L2 reality of inconsistent shadow capture.

The L3 promotion happens in APP-03.x, where the inventory becomes the canonical source for systematic guardrail coverage and agent control scoping decisions. The flag fields drive downstream scope: untrusted-content determines guardrail coverage at L3, agentic determines agent tool-allowlist scoping, and customer-facing determines app-stack adversarial testing scope at L4.

**Evidence:**
- Inventory export showing production AI applications with owner, model reference, customer-facing flag, untrusted-content flag, and dated risk assessment per major-application entry
- Sample of two risk-assessment records, drawn from across deployment types where present (at least one PaaS or API/SaaS entry, and one agentic or self-hosted entry if the organization runs them)
- Written definition of what counts as an "AI-enabled application" for inventory purposes, including the trigger list for the untrusted-content flag and the criteria for "major application"
- Documented inventory refresh cadence (e.g., quarterly) with the most recent refresh date and the named owner of the refresh
#### APP-02.2 — Guardrails and prompt separation on high-exposure applications

- **Deployment Types:** All
- **Manual/Automated:** Either
- **AICM Mapping:** AIS-08 (input validation), AIS-09 (output validation), AIS-15 (prompt differentiation)
- **External References:** OWASP LLM01:2025 Prompt Injection, OWASP LLM05:2025 Improper Output Handling
- **Key Indicator Rationale:** Deploying a managed guardrail layer on the major AI applications, even on a single direction, requires an owning team to have made the deployment call, tested it, and accepted the latency and cost tradeoff. That is the L2 "guardrails for some high-risk applications" signal from the main grid.

**Control Objective:** Major AI applications (customer-facing or processing untrusted content) run behind a managed guardrail layer such as Bedrock Guardrails, Azure AI Content Safety, OpenAI moderation, or a self-hosted equivalent on input or output.

**Description:** This is the L2 application-security lift. "Major AI applications" map to the customer-facing or untrusted-content entries in the APP-02.1 inventory. The untrusted-content flag has a baseline trigger list (free-text input, document or URL ingestion, tool calls), so the scope cannot be gamed downward by an owning team self-flagging conservatively.

The managed guardrail layer is one of Bedrock Guardrails, Azure AI Content Safety / Prompt Shields, OpenAI moderation, or a self-hosted equivalent. At L2 the guardrail can be invoked on input alone (filtering prompts before they reach the model) or output alone (filtering responses before they reach the user). Both directions become standard at L3 (APP-03.x), where guardrails extend to a wider critical subset with thresholds tuned per use case. The L2 signal is that the layer exists and is wired into at least one direction for the major AI applications, with deployment owners aware of the tradeoffs.

Structured prompt separation between system instructions, retrieved context, and user input is foundational hygiene that pairs naturally with guardrail deployment, but it is not the L2 measurable for this KPI; that discipline is captured at L3 alongside expanded guardrail coverage. Per-application guardrail tuning (topic restrictions, PII entities, thresholds per context) is also deferred to L3 and L4.

**Evidence:**
- List of major AI applications from APP-02.1 (customer-facing or untrusted-content) showing which guardrail service is deployed and which direction (input, output, or both) is wired in
- Guardrail configuration export (Bedrock Guardrails JSON, Azure Content Safety policy, OpenAI moderation call pattern, or equivalent) for two sample major applications
- Sample request trace or log entry from one major application showing the guardrail invocation in the request path
#### APP-03.1 — AI application security baseline with attested conformance

- **Deployment Types:** All
- **Manual/Automated:** Manual
- **AICM Mapping:** AIS-02 (application security baseline requirements), AIS-03 (application security metrics), AIS-08 (input validation), AIS-09 (output validation), AIS-15 (prompt differentiation)
- **External References:** OWASP LLM01:2025 Prompt Injection, OWASP LLM02:2025 Sensitive Information Disclosure, OWASP LLM05:2025 Improper Output Handling, NIST AI RMF GOVERN-1.4
- **Key Indicator Rationale:** Publishing a versioned AI application security baseline that covers prompt-injection mitigation, output filtering, guardrail configuration minimums, and agent/MCP handling — and measuring conformance against the inventory's critical subset — requires a central security function that has translated AICM and OWASP guidance into a named internal standard. That's the L3 defined-process signal, versus L2 where each team figures it out locally.

**Control Objective:** A versioned AI application security baseline defines what secure looks like across deployment types, covering prompt separation, indirect-injection filtering, minimum guardrail configuration, output handling by destination, and AI API-endpoint hardening. Critical AI applications (customer-facing and processing untrusted content) record dated conformance to the baseline, with exceptions carrying a named approver and a time-bound expiration.

**Description:** This is the L3 defined-baseline KPI. The document itself is not the indicator — plenty of L2 organizations publish policy that nobody reads. The indicator is the 75% conformance rate on the APP-02.1 critical subset (customer-facing AND untrusted-content both set), attested per application with a dated record, with exceptions carrying a named approver and 180-day expiration. The critical subset is a binary rule against APP-02.1 flag combinations so that scope is unambiguous and not subject to "at scale" hedging — either both flags are set or they aren't. The full-portfolio conformance rate (APP-04.1 at 95%) is deferred to L4. The baseline specifies, at minimum: structured prompt-separation; indirect-injection filtering on RAG/document/third-party content; minimum guardrail configuration (PII, topic restrictions, prompt-attack filtering, content thresholds); output-handling by destination (HTML encoding, parameterized queries, allowlist validation, schema validation); and AI API-endpoint requirements (authN, rate limiting, size limits). The baseline names approved guardrail products per deployment type because guardrail enforcement differs meaningfully across the three islands: Bedrock Guardrails and Azure AI Content Safety are managed services with platform-native configuration, OpenAI moderation is an additional API call the application has to make, and self-hosted guardrails (NeMo Guardrails, custom layers) require the application team to operate the layer themselves. The baseline names which products are approved for which islands so teams don't invent their own.

**Evidence:**
- Published baseline document under version control, with change log and named owner
- Conformance matrix mapping critical-subset AI applications from APP-02.1 to baseline attestation status, with a dated record per attestation
- Exceptions register showing per-exception approver name and expiration date within 180 days of issuance
- Sample conformance record for two applications (one PaaS/API and one self-hosted or agentic) showing which baseline requirements each application meets and how

#### APP-03.2 — Agent tool allowlist and application-facing MCP review

- **Deployment Types:** All
- **Manual/Automated:** Either
- **AICM Mapping:** AIS-11 (agent security boundaries), AIS-13 (AI sandboxing), AIS-04 (secure SDLC)
- **External References:** OWASP LLM06:2025 Excessive Agency, OWASP Agentic Security Initiative ASI02 (Tool Misuse), ASI04 (Supply Chain Vulnerabilities), MCP Security Best Practices
- **Key Indicator Rationale:** Requiring every agentic production application to document its tool allowlist with deny-by-default, and every MCP server to pass a named application-facing security review before production use, means the organization has defined agent scope and gated the bridge between agents and external systems at the app layer. A central function is gating both — that is the L3 "agent security boundaries defined" and "MCP integrations undergo security review" signal.

**Control Objective:** Agentic production applications run inside a documented tool allowlist with deny-by-default. MCP servers used by these applications pass an application-facing security review before production deployment, with re-review on major version updates.

**Description:** At L3 the tool allowlist exists, is documented, and is defended by deny-by-default — the mechanism (app code, framework configuration, gateway sidecar) is not the L3 discriminator. Every production application flagged agentic/tool-calling in APP-02.1 names its permitted tools with deny-by-default on unlisted tools. Centralized enforcement on a policy engine that sits outside the agent's prompt-controllable surface is the L4 capability that APP-04.2 requires. For MCP servers, APP-03.2 owns the application-facing review: which tools this app's agent will invoke, the data flowing through them, and whether the requested permissions match the application's minimum needs. Reviews re-run on MCP server version updates before promotion, and allowlist and review records link to the inventory entry. Supply-chain scanning of the MCP server package itself (dependency CVEs, package provenance, signature verification) is owned by DEV — APP-03.2 cross-references it but does not duplicate it. OAuth scope review on the requested permissions of the underlying identity is owned by IAM — APP-03.2 reviews scope from the application's use-case angle ("does this agent need write access?"), IAM owns the scope-grant decision and the lifecycle. Continuous MCP inventory scanning, gateway-layer policy enforcement, and runtime tool-invocation monitoring are L4+ capabilities.

**Evidence:**
- Tool-allowlist documents for two sample agentic applications, showing the specific tool list and the default-deny stance
- MCP server inventory with version, source, last-review date, and PII-access flag, cross-referenced to the DEV-owned supply-chain scan record and the IAM-owned OAuth scope record
- Two sample application-facing MCP review records showing the application's intended tool use, data flow, and permission justification against the use case
- Evidence that an MCP version update in the trailing 6 months triggered a re-review before promotion

---


#### APP-03.3 — Sandboxed runtimes for high-risk agent types

- **Deployment Types:** All
- **Manual/Automated:** Either
- **AICM Mapping:** AIS-13 (AI sandboxing), AIS-11 (agent security boundaries)
- **External References:** OWASP LLM06:2025 Excessive Agency, OWASP ASI02 (Tool Misuse)
- **Key Indicator Rationale:** Establishing sandboxed runtimes for the agent types where the blast radius of a compromised agent is highest (code execution, developer-workflow automation, browser-using agents) is the L3 defined-process signal. The sandbox is a deterministic boundary the agent's reasoning cannot override, complementary to APP-03.2's tool allowlist and MCP review.

**Control Objective:** Agents that execute code, automate developer workflows, or interact with untrusted environments run in sandboxed runtimes (containers, VMs, OS-level sandboxes, or hosted code-execution sandboxes). The sandbox boundary is documented per agent type.

**Description:** Sandboxing at L3 targets the agent types where the impact of a compromised or misbehaving agent is largest. Code-execution agents (Claude Code, Cursor, Devin, code interpreters within AI applications) execute LLM-generated code that may contain mistakes, hidden malicious instructions, or unintended side effects. Developer-workflow agents (broader IDE automation, repository agents, build agents) have access to source code and CI/CD secrets. Browser-using agents (Computer Use, Operator-style automation) interact with untrusted web content where prompt injection from a webpage can redirect the agent's behavior.

The sandbox type matches the deployment shape. Hosted code-execution sandboxes (such as e2b, Modal, Daytona, or Bedrock AgentCore code interpreter) isolate cloud-side code execution. Containers and VMs cover heavier-weight isolation for self-hosted agents. OS-level sandboxes (macOS App Sandbox, Windows AppContainer, browser sandbox) cover desktop and browser agents. Each agent type's sandbox configuration documents what the agent can read, write, or reach over the network, and that documentation is the assessor-facing artifact.

The L4 expansion (APP-04.2) extends sandboxed runtimes from these high-risk types to all production agents as one of several deterministic boundaries.

**Evidence:**
- Sandbox configuration document per agent type (code execution, developer workflow, browser-using) showing filesystem, network, and resource boundaries
- Sample of two production agents from these types showing sandbox in use, with deployment manifest, container/VM configuration, or sandbox profile
- List of in-scope agent types from the APP-02.1 inventory, showing which sandbox configuration applies to each

### Level 4 — Capable

#### APP-04.1 — Centralized AI gateway for production AI traffic

- **Deployment Types:** All
- **Manual/Automated:** Automated
- **AICM Mapping:** AIS-06 (secure application deployment), AIS-08 (input validation), AIS-09 (output validation), AIS-10 (API security), AIS-15 (prompt differentiation)
- **External References:** OWASP LLM01:2025 Prompt Injection, OWASP LLM05:2025 Improper Output Handling, NIST AI RMF MEASURE-2.6
- **Key Indicator Rationale:** Blocking deployments that fail a guardrail-configuration or I/O-validation check across 95% of production AI applications requires the baseline from APP-03.1 to have been translated into an automated deployment-time check, integrated into the CI/CD pipeline, and accepted as a hard gate by product teams. That's the L4 "deployed consistently" and "automated in deployment pipelines" signal.

**Control Objective:** Production AI applications route model calls, MCP server calls, and external tool calls through a centralized AI gateway (such as LiteLLM, Kong AI Gateway, or a self-hosted equivalent). The gateway applies guardrails, tool allowlists, and authentication policies, so applications cannot bypass these controls by calling endpoints directly.

**Description:** The distinction from APP-03.1 is coverage scope and enforcement mechanism. APP-03.1 attests conformance manually on the critical subset; APP-04.1 enforces conformance automatically on the full APP-02.1 production inventory. The deployment-time check is what makes this L4 — it runs against the artifact being deployed (Terraform/Bicep/CDK for platform-configured guardrails, code scan for in-app guardrail invocation, template scan for prompt separation) and fails the build if the policy is missing or misconfigured. Failures cannot deploy without a documented exception naming an approver with 90-day expiration; exceptions stay at or below 5% on a rolling 30-day basis. Across deployment types the check looks different: a PaaS application fails if its Bedrock Guardrails or Azure Content Safety policy isn't attached or is configured below the baseline thresholds; an API/SaaS application fails if the OpenAI moderation call or equivalent isn't in the request path or output path; a self-hosted application fails if the NeMo Guardrails (or named equivalent) configuration doesn't match the approved policy. The 95% threshold and 5% exception cap are the L4 operational bar — an L3 program hits 75% on the critical subset, an L4 program hits 95% across everything with formal exceptions for the rest.

**Evidence:**
- Pipeline configuration showing the guardrail/validation check as a required blocking stage across the deployment platforms in use
- 30-day deployment-attempt report showing pass/fail rates and the count of deployments that required exceptions
- Coverage metric report showing 95%+ of production AI applications pass the check
- Sample exception record showing approver, expiration within 90 days of issuance, and the specific baseline item waived
- Sample pipeline run showing the check executing against a PaaS and a self-hosted or API/SaaS deployment

#### APP-04.2 — Deterministic boundaries on agent execution

- **Deployment Types:** All
- **Manual/Automated:** Automated
- **AICM Mapping:** AIS-11 (agent security boundaries), AIS-13 (AI sandboxing)
- **External References:** OWASP LLM06:2025 Excessive Agency, OWASP ASI01 (Agent Goal Hijack), ASI02 (Tool Misuse), ASI09 (Human-Agent Trust Exploitation)
- **Key Indicator Rationale:** Enforcing the tool allowlist at a centralized decision point that sits outside the agent's prompt-controllable surface — and enforcing HITL through a workflow engine's task-token or interrupt primitive — means the organization has moved from "we asked the agent nicely" and "the app code calls deny-by-default" to "the architecture prevents the agent from influencing the decision, and the decisions are logged for MON to consume." That's the L4 "agent orchestration hardened" and "human-in-the-loop enforced" signal.

**Control Objective:** Agent execution operates under deterministic boundaries the agent's reasoning cannot override: sandboxed runtimes (containers, VMs, or OS-level sandboxes for desktop agents), bounded loop iterations, deny-by-default tool allowlists enforced by a centralized policy engine (such as OPA or Cedar), human-in-the-loop interrupts for high-risk actions, and limits on multi-agent interactions.

**Description:** The L4 jump from APP-03.2 is the enforcement architecture, not the brand of tool. At L3 the allowlist is documented and defended by mechanism-agnostic deny-by-default — possibly in app code. At L4 the enforcement point is moved off the prompt-controllable surface, the policy is centrally managed and versioned across applications (not in per-app code), and the decision logs flow to MON in a form MON can correlate. A policy engine like Cedar or OPA, or AWS AgentCore with Cedar, is the canonical illustration, but the L4 capability is "centralized enforcement outside the agent's reach with consumable decision logs" — not "named tool deployed." For sensitive action categories (minimum: external comms, data modifications, financial transactions, confidential-info access), HITL is enforced at a workflow-engine or framework-interrupt primitive (Step Functions `waitForTaskToken`, LangGraph `interrupt()`, or equivalent), with approval UIs that display the full action payload rather than the agent's summary. A kill-switch at the same layer is exercised in non-production within 12 months. The HITL requirement is a hard separation from prompt-based approval patterns — "the user already approved this" in the context window does not grant approval; only a callback to `SendTaskSuccess` or a LangGraph resume call with an updated state graph does. This matters because prompt-injection attacks routinely try to fabricate approval states in the model's context. Rate-limit policy on the underlying identity is owned by IAM and is referenced from this KPI's enforcement layer rather than defined here — IAM sets the envelope, APP enforces tool-list and HITL within it. Infrastructure-level enforcement of HITL is the specific design pattern APP-06 of the assessment criteria document calls out; a program claiming L4 maturity whose HITL lives only in system prompts hasn't achieved APP-04.2.

**Evidence:**
- Policy or configuration showing tool-allowlist enforcement at a centralized decision point with deny-by-default, plus the central management mechanism (shared policy repo, versioned deployment to enforcement point)
- Architecture diagram showing where policy evaluation occurs in the request path, confirming the enforcement point is outside the agent's prompt-controllable surface
- Sample policy decision log entry in the format shipped to MON, showing the inputs evaluated and the deny/allow decision
- Workflow configuration (Step Functions state machine, LangGraph graph definition, or equivalent) showing HITL enforcement at a task-token or interrupt primitive
- Screenshot or spec of the approval UI showing full action payload display rather than agent-summarized action
- 30-day log of policy decisions and HITL approvals including at least one denied tool invocation and one denied or timed-out approval
- Kill-switch exercise record from non-production within the trailing 12 months

#### APP-04.3 — App-stack adversarial testing with layer attribution

- **Deployment Types:** All
- **Manual/Automated:** Automated
- **AICM Mapping:** AIS-05 (application security testing), AIS-07 (application vulnerability remediation)
- **External References:** OWASP LLM01:2025 Prompt Injection, OWASP ASI01 (Agent Goal Hijack), ASI02 (Tool Misuse), NIST AI RMF MEASURE-2.7
- **Key Indicator Rationale:** Running app-stack adversarial tests (prompt injection, jailbreak, indirect injection via RAG/documents, system-prompt extraction, tool-misuse for agentic apps) in the CI/CD pipeline against the deployed system prompt + guardrail + tool-restriction configuration, with findings attributed to the model layer vs. the app-stack layer and guardrail state recorded per finding, requires an AI red team or AppSec function that has built the harness against the deployed application stack. That's the L4 "AI-specific security testing integrated into CI/CD" signal — and the attribution discipline is what keeps the test from collapsing into MOD-04.2's scope.

**Control Objective:** Critical AI applications (customer-facing or processing untrusted content) run app-stack adversarial tests against the deployed system prompt, guardrails, and tool restrictions on a defined cadence. Findings are labelled app-stack-layer or model-layer so remediation routes to the right owner.

**Description:** This KPI is the app-stack counterpart to MOD-04.2 and is built to stay there. MOD-04.2 tests the base model at its inference API with registered parameters — does Claude-3-Opus-at-these-params jailbreak under HarmBench? APP-04.3 tests the deployed application stack — does this customer-support agent, with its deployed system prompt, its attached Bedrock Guardrails policy, and its enforced tool allowlist, leak its system prompt or misuse the `send_email` tool when hit with a prompt-injection payload referencing `send_email`? Every APP-03.1 production application runs the test suite on each deployment and at least every 30 days. Coverage minimum: direct injection, indirect injection, system-prompt extraction, and (agentic) tool-misuse and fabricated-approval, with at least one externally-sourced artifact per category (Promptfoo, garak, Foundry, or equivalent); generic base-model benchmarks belong under MOD-04.2. The harness records guardrail state and attribution per finding; High/Critical app-stack findings block deployment and resolve within 30 days. Two design choices keep the boundary clean. First, app-specificity is required in the payloads: a generic "ignore previous instructions" payload that doesn't reference the application's own prompt, tools, or RAG content tests the model, not the app stack. Second, every finding records the guardrail state and an attribution label, so a finding that reproduces with guardrails disabled and is purely a model behavior gets attributed to the model layer and routed to MOD — it doesn't generate an app-stack remediation ticket and doesn't earn coverage credit here. Externally-sourced benchmarks with named third-party artifacts are required to prevent owner-picked weak-test-set gameability — an internal playbook alone, however thorough, can be tuned by the owning team to the controls they happen to have implemented. The 30-day cadence outside of deployments catches drift when the model, the guardrail service, or a provider-side moderation policy changes without an application redeploy. Continuous tuning of the test suite from real-world attack patterns — the red-team-to-guardrail feedback loop — is the L5 extension in APP-05.1.

**Evidence:**
- Pipeline configuration showing the app-stack adversarial test stage as a blocking gate for High and Critical findings tagged "app-stack layer"
- Version-controlled test suite per application covering the four minimum categories, with named third-party artifacts identified per category (e.g., "Promptfoo red-team plugin X, garak probe Y, Foundry evaluator Z")
- Sample app-specific payloads showing references to *this* application's system prompt, tool names, and RAG corpus
- Most recent test report per application dated within the trailing 30 days for in-scope production applications, with severity-rated findings, per-finding guardrail state (on / off / bypassed), and per-finding attribution (model layer / app-stack layer)
- Remediation tracker showing High/Critical app-stack-layer findings linked to tickets or signed risk-acceptance records within a 30-day window
- Sample finding lifecycle: detection in a CI run, attribution check, severity triage, owner assignment, resolution or accepted risk

---

### Level 5 — Efficient

#### APP-05.1 — Guardrail and test-suite tuning loop on a defined SLA

- **Deployment Types:** All
- **Manual/Automated:** Automated
- **AICM Mapping:** AIS-03 (application security metrics), AIS-07 (application vulnerability remediation), AIS-08 (input validation), AIS-09 (output validation)
- **External References:** OWASP LLM01:2025 Prompt Injection, OWASP ASI01 (Agent Goal Hijack), NIST AI RMF MANAGE-4, MITRE ATLAS
- **Key Indicator Rationale:** Closing the loop from "new attack pattern flagged as applicable to an in-scope application" to "updated guardrail configuration and updated adversarial test suite deployed" within a defined SLA requires the guardrail configuration and test suite to be under version control, an owner per in-scope application, and an established feedback intake — regardless of which upstream source produces the pattern. That's the L5 "guardrails continuously tuned based on emerging attack patterns" signal, and shipping zero missed updates over a rolling 6-month window is the outcome only an L5 program achieves.

**Control Objective:** New attack patterns from telemetry, red-team findings, and external threat intel translate into updated guardrail configurations and updated adversarial test suites on a defined SLA, with version-controlled artifacts and a named owner.

**Description:** The L5 distinction from L4 is the feedback loop. APP-04.3 runs a version-controlled test suite; APP-05.1 updates that suite and the underlying guardrail configuration when reality changes, on a measurable cadence. For every APP-03.1 production application, guardrail configuration and the APP-04.3 adversarial test suite are under version control with a defined SLA: 14 days to test-suite addition, 30 days to guardrail-configuration update (or signed risk-acceptance). Over the trailing 6 months, at least 95% of flagged applicable patterns meet both SLAs. Intake sources include MON-provided guardrail-violation telemetry (MON L4), red-team findings, provider advisories, OWASP LLM Top 10 updates, MITRE ATLAS, and industry threat feeds. The MON dependency is real but framed as guidance, not a hard prereq: MON L4 is the canonical feedback source for guardrail-violation telemetry, but APP-05.1's measurable outcome is the SLA itself, which an organization can meet with red-team findings and external threat intel even where MON is still maturing. The 14-day test-suite SLA and 30-day configuration-change SLA are tight on purpose: L5 programs translate new attacks into updated defenses fast, not fast enough. Guardrail tuning in a managed service means updating the Bedrock Guardrails policy JSON, the Azure Content Safety filter configuration, the OpenAI moderation threshold set, or the self-hosted NeMo policy file — all of which should be in version control and promoted through the same pipeline as application code. An application owner can legitimately close a pattern with a signed risk-acceptance ("this pattern doesn't apply because this app doesn't process external documents"); the acceptance counts toward SLA compliance but is tracked separately for audit.

**Evidence:**
- Version control history for guardrail configuration and app-stack adversarial test suite showing commits correlated with feedback sources (MON ticket IDs, red-team finding IDs, external threat-intel references)
- 6-month report showing patterns-flagged, patterns-closed-with-test-update, patterns-closed-with-guardrail-update, patterns-closed-with-risk-acceptance, and SLA compliance rate of 95%+
- Feed/source list covering MON-provided guardrail-violation telemetry, red-team findings, provider advisories, OWASP updates, MITRE ATLAS, and industry threat feeds
- Sample closed loop: a specific flagged pattern, ticketed, translated to a test case, translated to a guardrail-config change, deployed, with timestamps showing SLA compliance

#### APP-05.2 — Shared agent policy baseline and qualified red-team exercises

- **Deployment Types:** All
- **Manual/Automated:** Either
- **AICM Mapping:** AIS-05 (application security testing), AIS-11 (agent security boundaries)
- **External References:** OWASP LLM06:2025 Excessive Agency, OWASP ASI02 (Tool Misuse), ASI08 (Cascading Failures), NIST AI RMF MEASURE-2.7
- **Key Indicator Rationale:** Running recurring red-team exercises against the production AI application portfolio on a named cadence by a qualified party, with coverage extended to multi-agent interactions where present, and with the centralized enforcement layer from APP-04.2 governed by a shared policy baseline rather than per-app policies, requires a standing AI red-team function (or qualified external party) and a central agent-platform team. That's the L5 "agentic security automated with policy engines governing tool access and multi-agent interactions" and "AI application red teaming conducted regularly" signal.

**Control Objective:** Agent operations share common deny-lists and high-risk action categories at the APP-04.2 enforcement layer while permitting per-application customization above that baseline. A qualified independent red team exercises the AI application portfolio on a defined cadence, with findings feeding the APP-05.1 tuning loop.

**Description:** The L5 distinction on enforcement governance is centralization. At L4 each agentic application enforces tool access at a central decision point, but the policy can be per-application; at L5 the organization runs a shared policy baseline (common sensitive-action definitions, shared deny lists, common approval workflows) with per-application overlays only where justified. For multi-agent / A2A interactions, the layer mediates inter-agent tool invocation and information exchange deny-by-default — when agent A can invoke agent B's tools by delegation, the enforcement layer has to mediate that delegation rather than trusting the agents to respect each other's scopes. The red-team cadence is the second half of the L5 signal: a qualified party runs exercises every 6 months for APP-03.1 critical-subset apps and every 12 months for the rest. "Qualified" means independent, named methodology (MITRE ATLAS, OWASP ASI, or peer-reviewed internal), and public AI red-team experience. High/Critical findings resolve within 60 days. The "qualified" definition matters because an L5 claim rests on the red team being independent enough to find what the build team can't see, methodologically grounded enough to be reproducible, and experienced enough to apply current technique — an internal AppSec engineer running ad-hoc prompt-injection payloads doesn't clear the bar, and neither does a generic pen-test vendor with no AI red-team track record. The 6-month cadence for critical apps is tight enough to catch drift and new attack techniques; the 12-month floor for the portfolio catches the long tail. The feedback into APP-05.1's tuning loop is what turns the red team from a point-in-time audit into part of the operational defense.

**Evidence:**
- Shared policy baseline (Cedar, OPA, or equivalent) with documented override mechanism and a list of applications using the shared baseline versus custom policies
- Enforcement-layer configuration demonstrating multi-agent / A2A mediation where multi-agent applications are present, including a sample policy decision log for an inter-agent invocation
- Red-team exercise schedule showing 6-month cadence for the APP-03.1 critical subset and 12-month cadence for the rest of the production AI application portfolio
- Qualification dossier for the named red-team party covering independence from the application teams, the methodology in use, and public evidence of AI red-team experience
- Red-team report sample including scope, techniques used, findings with severity ratings, and remediation status for High/Critical within a 60-day window
- Linkage from a red-team finding to an APP-05.1 test-suite update and guardrail-configuration change

---

---

## 8. Data Security (DAT) <a id="8-data-security"></a>

**Category description:** Security, privacy, and ownership controls for data flowing through AI systems across deployment types (self-hosted, PaaS, API/SaaS). Covers training- and fine-tuning-data governance (provenance, classification, lineage), RAG source approval and validation, vector-store access control and tenant isolation, permission-aware retrieval, sensitive-data filtering on inputs and outputs, and detection of data-poisoning or adversarial patterns in training and retrieval sources. Data-flow logging, detection, and telemetry aggregation live in Security Monitoring (MON); runtime retrieval-call construction and guardrail behavior on retrieved content live in Application Security (APP); model-artifact behavior, approval, and safety evaluation live in Model Security (MOD).


---

### Level descriptors (reference — from AISMM main grid)

- **L1 Initial:** AI data repositories (training data, vector stores, RAG sources) rely on general-purpose data security controls. No differentiation between AI and other data assets. Data provenance for training and fine-tuning for self-trained models not tracked. Vector databases deployed with default access controls. No validation of data sources used for grounding or retrieval.
- **L2 Repeatable:** AI-specific data risks identified (poisoning, RAG leakage). Training and fine-tuning data sources documented for critical models. Basic access controls on vector databases. Basic validation (source approval, format checks) for external sources used in RAG. Sensitive data handling requirements documented for AI contexts but inconsistently applied.
- **L3 Defined:** AI data security requirements documented by data type (training, fine-tuning, RAG, embeddings). Data ingestion restricted to approved, documented sources with format validation before use. Vector databases use tenant or application isolation to prevent cross-context access. Sensitive data filtering applied to training and grounding sources (e.g. PII scanning). Initial data versioning for critical AI systems.
- **L4 Capable:** Data sources and transformations documented and auditable for production AI systems. Automated data validation integrated into AI pipelines where applicable. Permission-aware retrieval implemented for RAG tool calls (query results filtered based on user access to source data). Comprehensive data versioning with ability to trace data changes over time.
- **L5 Efficient:** Data lineage integrated with model inventory for end-to-end traceability (for training). Permission-aware retrieval standard across RAG deployments. Scanning for detection of potential data poisoning or adversarial patterns in training/RAG. AI data security controls updated proactively as new attack vectors emerge.

---

### Scope note — DAT boundaries

Data Security KPIs address the data side of AI: which sources feed training, fine-tuning, and RAG; how those sources are classified and approved; who can read what from a vector store and under whose authority; whether sensitive data is filtered before it reaches the model or the user; and whether training and retrieval content is screened for poisoning or adversarial patterns. Model-artifact behavior, approval, and safety evaluation belong to Model Security (MOD) — including fine-tuning approval and post-tune safety testing; DAT owns the training data going into that fine-tune (classification, ownership, lineage). Runtime retrieval-call construction, guardrail invocation on retrieved content, and how the app hands retrieved data to the model belong to Application Security (APP). Logging of data flows, SIEM integration, and detection rules on data-access patterns belong to Security Monitoring (MON); DAT owns whether the access is allowed, MON owns whether the access is watched.

**API/SaaS-only consumer scope.** Organizations that consume only API and SaaS AI (no self-hosted models, no customer-configured PaaS vector stores) are assessed against a reduced DAT footprint:

- **DAT-02.1** applies (the org still inventories which sources feed M365 Copilot, Agentforce, ChatGPT Enterprise connectors, etc.).
- **DAT-02.2** does not apply at the customer level for provider-owned vector layers; provider posture is inherited and evaluated through RSK provider assessment. The KPI applies if the organization runs any customer-configured vector store.
- **DAT-03.1** applies to source approval; the DLP scan scope is the customer-supplied content (knowledge files, SharePoint sites, custom connectors), not the provider's pretraining corpus.
- **DAT-03.2** is inherited from the provider for provider-owned stores; applies directly only to customer-configured stores.
- **DAT-03.3** applies — the org configures sensitive-data filtering on the API/SaaS application surface (Bedrock Guardrails on a Bedrock-mediated API, provider-native filters where exposed, or a wrapper layer).
- **DAT-04.1** applies in the API/SaaS provider-native-trim form (verify enabled, run quarterly denial test).
- **DAT-04.2** applies to customer-supplied datasets and knowledge-base contents; the org records consumption of provider versioning where exposed.
- **DAT-05.1, DAT-05.2** scope is the customer-controlled surface only (RAG, fine-tuning content, customer-supplied training data); foundation-model pretraining and provider-owned indexes are out of scope and tracked through RSK.

---

### Level 2 — Repeatable

#### DAT-02.1 — RAG source inventory with approval record

- **Deployment Types:** All
- **Manual/Automated:** Manual
- **AICM Mapping:** DSP-03 (data inventory), DSP-20 (data provenance and transparency), DSP-04 (data classification)
- **External References:** OWASP LLM04:2025 Data and Model Poisoning, OWASP LLM08:2025 Vector and Embedding Weaknesses, NIST AI RMF MAP-4
- **Key Indicator Rationale:** An organization cannot produce a single inventory that lists every RAG and grounding source feeding production AI applications — across self-hosted vector stores, PaaS knowledge bases (Bedrock Knowledge Bases, Azure OpenAI on-your-data, Vertex AI Search), and API/SaaS data-access paths (M365 Copilot content, Agentforce data cloud) — with a dated approval record per source unless it has already identified RAG leakage and poisoning as AI-specific risks and assigned someone to review sources before they are connected. The inventory artifact is the byproduct of L2 hygiene, not the cause of it.

**Control Objective:** An inventory of production AI data sources (RAG feeds, knowledge bases, grounding connectors) is maintained, with each entry carrying a dated pre-connection approval. The inventory is refreshed on a defined cadence and reconciled against ingestion telemetry (e.g. CSPM/AI-SPM) discovery where deployed).

**Description:** "Production" means any AI application serving real users or real business workloads, including internal assistants broadly available inside the organization. Each inventory entry names the source identifier, source system, owning application, classification tag from the enterprise scheme (public / internal / confidential / restricted or local equivalent — not invented for AI use), and a dated approval record completed pre-connection (or backfilled within 12 months for pre-existing sources). At least 90% of distinct sources observed in 30 days of production ingestion telemetry must reconcile to an approved entry; unreconciled sources are listed as named exceptions with owner and remediation date, or quarantined. The approval record can be a one-pager, email, or ticket reference at L2; standardized templates are an L3 move. The reconciliation threshold catches the common L1-to-L2 failure mode where an inventory exists but ingestion pipelines have grown past it as knowledge-base connectors, SharePoint sites, and bucket mounts drift in. The denominator wording is deliberate — using a curated app-team list as the denominator makes 100% reconciliation trivial and meaningless. The independent cross-check (AI-SPM output such as Wiz AI-SPM, Prisma AI-SPM, Lacework AI security, or billing-tagged spend on Pinecone, Weaviate, OpenSearch, or Bedrock Knowledge Base resources) catches the case where ingestion telemetry itself has gaps.

**Evidence:**
- Inventory export listing production RAG and grounding sources with source identifier, source system, owning application, classification tag, and approval-record reference per entry
- Sample of three approval records drawn from across deployment types, showing pre-connection completion (or in-window backfill for pre-existing sources)
- Reconciliation report comparing inventory to 30 days of ingestion telemetry (ingestion-pipeline logs, Bedrock Knowledge Base sync events, Azure OpenAI on-your-data data-source configurations, M365 Graph connector inventory) showing at least 90% of distinct telemetry-observed sources reconciled, with the unreconciled remainder listed as exceptions or quarantined
- Independent cross-check artifact: AI-SPM scan output or billing/cost-allocation report flagging AI-related storage and vector service spend, compared to the inventory

#### DAT-02.2 — Vector store authentication and default-deny network posture

- **Deployment Types:** Self-hosted, PaaS (where the customer configures the vector store); API/SaaS vector behavior inherits from the provider and is covered by provider assessment in RSK
- **Manual/Automated:** Automated
- **AICM Mapping:** DSP-17 (sensitive data protection), CEK-03 (data encryption in transit / at rest)
- **External References:** OWASP LLM08:2025 Vector and Embedding Weaknesses, CIS Benchmarks for the underlying data platform
- **Key Indicator Rationale:** An organization that can demonstrate authenticated access and no public network exposure across every vector store backing a production AI application has moved past the L1 pattern of standing up Pinecone / Weaviate / pgvector / OpenSearch / Bedrock Knowledge Base with defaults and forgetting about it. Meeting this KPI requires someone to have identified every vector store in the estate and verified its baseline posture — that is the L2 "basic access controls on vector databases" signal.

**Control Objective:** Vector stores and knowledge-base indexes backing production AI applications require authentication, encrypt data in transit and at rest, and stay off the public internet. Anonymous access and default credentials are prohibited; any public endpoint carries a time-bounded exception with a named approver.

**Description:** Scope includes self-hosted vector databases (Pinecone self-managed, Weaviate, Milvus, Qdrant, Redis, pgvector, OpenSearch) and PaaS knowledge bases where the customer configures the underlying store (Bedrock Knowledge Bases backed by OpenSearch Serverless or Aurora, Azure AI Search, Vertex AI Search). API/SaaS consumption where the provider owns the vector layer (M365 Copilot over Microsoft Graph, Agentforce over Data Cloud) is out of scope — provider posture is evaluated through RSK. Specific thresholds: 100% coverage of in-scope stores; TLS 1.2 or higher enforced; encryption at rest uses a KMS key documented in the DAT-02.1 inventory; no anonymous access or vendor default credentials; any public network endpoint requires an exception record naming the approver and expiring within 90 days of issuance. The public-endpoint clause is the most gameable part of this control; the named-approver-and-90-day-expiration pattern keeps "we had to open it up for testing" from becoming permanent posture. Documenting the KMS key in the inventory closes the loop between what exists and how it is protected.

**Evidence:**
- Vector-store inventory (may be a tab on the DAT-02.1 inventory) listing each store with authentication method, TLS minimum version, encryption-at-rest KMS key reference, and network exposure status
- CSPM or AI-SPM scan output (Wiz, Prisma Cloud, Lacework, Orca, or equivalent) showing no findings for anonymous access, default credentials, TLS < 1.2, or public endpoints on in-scope stores; or findings with linked exception records
- Security-group / firewall / VPC configuration export for a sampled store showing private network posture
- Any public-endpoint exception records with approver name and expiration within 90 days of issuance

---

### Level 3 — Defined

#### DAT-03.1 — Approval gate on AI data sources with classification and sensitive-data scan

- **Deployment Types:** All
- **Manual/Automated:** Either
- **AICM Mapping:** DSP-04 (data classification), DSP-17 (sensitive data protection), DSP-20 (data provenance and transparency), DSP-24 (training-data differentiation and relevance)
- **External References:** OWASP LLM02:2025 Sensitive Information Disclosure, OWASP LLM04:2025 Data and Model Poisoning, NIST AI RMF MAP-4, GOVERN-5
- **Key Indicator Rationale:** The L2/L3 delta is not workflow tooling — at L2 the approval record can be a ticket, email, or one-pager (DAT-02.1). The L3 capability that distinguishes this KPI is the substantive content of the approval: a DLP or sensitive-data scan result attached to the source, plus a second-function approver (data governance, security, or AI risk) signing off rather than the source's own data owner self-approving. An organization that produces both artifacts on every newly-connected source has stood up the defined-process L3 capability, not just upgraded its ticket template. The "initial data versioning for critical AI systems" property in the L3 main-grid descriptor is implicit here: each approved source carries a snapshot reference (commit SHA, dataset version, knowledge-base version, or equivalent immutable identifier) on the approval record, with cumulative versioning becoming an L4 capability under DAT-04.2. A separate L3 KPI for versioning is not added because it would not be level-discriminating against either DAT-03.1 (which captures the snapshot reference) or DAT-04.2 (which formalizes versioning end-to-end).

**Control Objective:** New data sources connected to a production AI application (RAG feeds, knowledge bases, grounding sources, training sets, fine-tuning sets) pass through an approval workflow that attaches a sensitive-data scan result and a named second-function approver distinct from the data owner. Unapproved sources are not used with AI applications.

**Description:** The two distinguishing L3 capabilities are the DLP/sensitive-data scan result and the second-function approver — both attached to the same approval record. The workflow tooling is secondary (ServiceNow, Jira, governance platforms, structured SharePoint or Confluence lists, even repeated email threads if both artifacts are attached). The required record contents are: source identifier, classification tag, data owner, intended AI use case, DLP/sensitive-data scan result against the approved classification scope, a snapshot reference (commit SHA, dataset version, knowledge-base version, or equivalent immutable identifier), and a named approver from data governance, security, or AI risk. Coverage threshold: 100% of newly connected in-scope sources over the trailing 90 days carry a complete record. The DLP scan is the substantive gate: a source approved for "internal" cannot contain unmarked "restricted" content. Tooling examples include Microsoft Purview, AWS Macie, Google DLP, or Presidio-based pipelines applied to source content before embedding. For training and fine-tuning datasets the scan covers the full dataset; for RAG and knowledge bases it covers the source at connection time, with refresh on significant source change (the L4 versioned-and-rescanned posture lives in DAT-04.2). The named-second-function clause prevents "the data owner approved their own source."

**Evidence:**
- Approval-workflow template or ticket schema showing required fields (source identifier, classification, data owner, AI use case, DLP scan result, snapshot reference, second-function approver)
- Sample of five approval records drawn from across source types (RAG, knowledge base, training set, fine-tuning set) within the trailing 90 days, each showing a DLP scan output and a second-function approver distinct from the data owner
- DLP or sensitive-data scan output attached to each sampled record
- 90-day audit comparing newly connected sources (from ingestion telemetry) to approval records, showing 100% coverage or exceptions with named approver and expiration

#### DAT-03.2 — Vector-Store tenant isolation with cross-context denial test

- **Deployment Types:** Self-hosted, PaaS (customer-configured knowledge bases); API/SaaS inherits from provider
- **Manual/Automated:** Either
- **AICM Mapping:** DSP-17 (sensitive data protection), DSP-07 (data protection by design)
- **External References:** OWASP LLM08:2025 Vector and Embedding Weaknesses, OWASP LLM02:2025 Sensitive Information Disclosure
- **Key Indicator Rationale:** An organization that has implemented a documented isolation model per vector store (namespace, collection, index, database, or row-level security) and has exercised a cross-context denial test within the trailing 12 months has done the L3 "prevent cross-context access" work substantively rather than assuming defaults protect it. An L2 organization has basic access controls but has not verified the isolation model against a targeted test.

**Control Objective:** Production vector stores document how they isolate tenants or applications, and the boundary is exercised with a cross-context denial test on a defined cadence. A test identity scoped to one context returns nothing from another; failures are remediated and retested.

**Description:** Scope follows DAT-02.2. The isolation-model record names the mechanism per store (Pinecone namespaces, Weaviate multi-tenancy, pgvector row-level security, OpenSearch index-level access, Bedrock Knowledge Base data-source scoping, or equivalent) along with the context unit and any required query-time metadata filters. The "context" unit depends on the application: for a multi-customer SaaS product, context is the customer tenant; for an internal HR assistant, context is the employee or role; for a research-department knowledge base, context is the project or business unit. Denial-test records capture date, tester, store identifier, test identity scoping, queries used, and pass/fail; the cadence is at least once in the trailing 12 months. The denial test is what separates this control from DAT-02.2: authentication and network posture establish "only authorized clients can connect," while the denial test establishes "an authorized client in context A cannot read context B's data" — the semantic boundary that vector stores break silently when isolation is misconfigured. The 12-month cadence is realistic at L3; L4 moves to permission-aware retrieval (DAT-04.1) which is a stronger guarantee.

**Evidence:**
- Isolation-model record per in-scope store naming the mechanism, the context unit, and any metadata filters required at query time
- Denial-test records for each in-scope store within the trailing 12 months, including tester, test identity scoping, target context, queries used, and pass/fail result
- Remediation tickets for any failed tests with retest evidence
- Sample query logs or test harness output showing the cross-context queries returned zero or access-denied

#### DAT-03.3 — Input and output sensitive-data filtering on production AI applications

- **Deployment Types:** All
- **Manual/Automated:** Automated
- **AICM Mapping:** DSP-17 (sensitive data protection), DSP-10 (sensitive data transfer), DSP-11 (personal data access)
- **External References:** OWASP LLM02:2025 Sensitive Information Disclosure, NIST AI RMF MEASURE-2.10, regulatory basis (GLBA, CCPA, GDPR, PCI-DSS) as applicable
- **Key Indicator Rationale:** Every production AI application running both input and output sensitive-data filtering with a defined entity set, defined action per entity, and a filter-event log requires a standardized filter configuration to exist (typically Bedrock Guardrails sensitive-information policy, Azure AI Content Safety PII, or a Presidio/Comprehend-based pipeline) and to be enforced across deployments. That is the L3 "sensitive data filtering applied" outcome rather than the L2 "documented but inconsistently applied" state.

**Control Objective:** Production AI applications scan inputs and outputs for sensitive data, covering the regulated PII entities for the organization's jurisdictions and industries. Each entity has a defined action (block, mask, or redact), and filter events flow to telemetry.

**Description:** The filter is deployed at the application boundary: on input before it reaches the model, on output before it reaches the user or downstream system. Coverage threshold: 100% of in-scope applications show filter events over the trailing 90 days, or a documented zero-event justification. Zero-event justifications must be countersigned by data-governance or security (not solo app-owner attestation), expire at 12 months or on scope change, and apply to <10% of in-scope applications in aggregate. The zero-event clause handles internal-only developer tools where no sensitive data is expected to flow; the cap stops "everyone declares zero events" from becoming the path of least resistance. Per-application configuration records list enabled entity types, action per entity, and the filter tooling, with each entity tagged DAT-scope or APP-scope (or cross-referenced to the APP KPI on the same artifact). The minimum entity set must cover regulated PII for the organization's jurisdiction and industry: national identifiers, payment-card numbers, financial account identifiers, and contact PII; financial-services adds bank routing/account numbers and customer identifiers; healthcare adds PHI. Tooling varies by deployment: Bedrock Guardrails sensitive-information policy for Bedrock, Azure AI Content Safety PII detection for Azure OpenAI, OpenAI Moderation plus Presidio for direct API consumption, or a self-hosted Presidio, Comprehend, or custom pipeline for self-hosted models. Bedrock Guardrails, Azure AI Content Safety, and OpenAI Moderation often serve both DAT and APP scopes on a single product — the scope tagging on the configuration record is the bookkeeping that lets one guardrail policy be evaluated against both KPIs without ambiguity. Log entries to telemetry are the DAT side of a hand-off to MON, which owns SIEM aggregation and detection rules on the filter-event stream.

**Evidence:**
- Per-application filter configuration record listing enabled entity types, action per entity, and filter tooling (Bedrock Guardrails policy ID, Azure AI Content Safety resource, Presidio ruleset), with each entity / rule set tagged DAT-scope or APP-scope (or cross-referenced to the APP KPI)
- 90-day filter-event log sample per sampled application showing detected entities and actions taken
- Zero-event justifications (where applicable) signed by the application owner and countersigned by data-governance or security, with date, 12-month expiration or scope-change trigger, and a count showing <10% of in-scope applications use this justification
- Mapping document showing how the enabled entity set covers the regulatory minimum for the organization's jurisdictions and industries

---

### Level 4 — Capable

#### DAT-04.1 — Permission-Aware retrieval for RAG over access-controlled sources

- **Deployment Types:** All (pattern differs by deployment type; see Description)
- **Manual/Automated:** Automated
- **AICM Mapping:** DSP-17 (sensitive data protection), DSP-10 (sensitive data transfer), DSP-11 (personal data access)
- **External References:** OWASP LLM02:2025 Sensitive Information Disclosure, OWASP LLM08:2025 Vector and Embedding Weaknesses, NIST AI RMF MEASURE-2.10
- **Key Indicator Rationale:** Permission-aware retrieval working end-to-end — source ACLs captured, user identity propagated to the retrieval query, results filtered at the vector layer rather than in post-retrieval application code, and stale-permission fallback deny-by-default — requires the identity plumbing (OBO tokens or equivalent), the metadata capture at ingestion, and the enforcement at query time to all exist. An L3 organization may have isolation between contexts (DAT-03.2) but does not yet enforce individual-user permissions on retrieval results against access-controlled sources. This KPI assumes a working identity-delegation pattern (typically IAM L3+) and a RAG retrieval pipeline that the application team controls (typically the APP retrieval-wiring capability); per the AISMM cross-category guidance these are noted as context dependencies, not hard prerequisite gates.

**Control Objective:** RAG applications retrieving from access-controlled sources filter results against the requesting user's entitlements before content reaches the model. Filtering happens at the vector layer using ACLs captured at ingestion, the retrieval layer fails closed when permission sync breaks.

**Description:** Scope is 100% of production RAG applications retrieving from sources with per-user or per-group access controls in the source system (SharePoint, Confluence, Google Drive, file shares, permissioned databases). A RAG application over a fully-public knowledge base does not need permission-aware retrieval and should not be inflated into the control.

Deployment-type patterns differ materially:

- **API/SaaS with provider-native permission trimming** (M365 Copilot retrieving over Microsoft Graph, Agentforce over Salesforce record permissions): the provider implements the trim; the organization verifies it is enabled, sharing-link and oversharing risks are managed, and the quarterly denial test passes.
- **PaaS knowledge bases with source-system auth** (Bedrock Knowledge Bases with permissioned data sources, Azure OpenAI on-your-data with SharePoint and RBAC passthrough, Vertex AI Search with IAM-scoped data stores): the organization configures the identity passthrough and verifies it.
- **Self-hosted RAG over permissioned sources** (custom LangChain or LlamaIndex pipeline over SharePoint, Confluence, or a permissioned database): the organization implements ACL capture at ingestion, metadata filtering at the vector layer (namespace, tenant, or ACL fields), OBO token flow, and permission-sync with deny-on-failure.

Specific thresholds: source ACLs or group memberships captured as metadata at ingestion; user identity propagated via the org's federation pattern; permission staleness bounded at 24 hours for data classified above "internal"; on sync failure the retrieval layer fails closed. Quarterly denial-test coverage requires ≥25% of distinct ACL groupings (or all if fewer than four) per in-scope application, using ≥5 test identities spanning ≥3 source-ACL contexts, with each denied identity receiving zero matching RAG results. The stale-permission fail-closed posture matters because the common failure mode is a background sync job erroring out silently while the application keeps answering from yesterday's permissions. The breadth requirement replaces a single-pass test that can pass against a trivially configured pair of identities while leaving most ACL groupings unexercised.

**Evidence:**
- Application-level record per in-scope RAG application listing source system, permission-capture method, retrieval-filter mechanism, identity-propagation pattern, and staleness bound
- Ingestion-pipeline configuration or PaaS knowledge-base configuration showing ACL / group capture at embed time (self-hosted and customer-configured PaaS) or provider-native trim configuration (API/SaaS)
- Retrieval-code or query-template evidence showing metadata filter applied at query time (self-hosted / PaaS); provider configuration screenshots (API/SaaS)
- Permission-sync job configuration and alerting; sample deny-on-failure behavior log
- Quarterly denial-test records per in-scope application showing the test breadth (count of identities, count of source-ACL contexts, percentage of distinct ACL groupings exercised) and that each denied identity received zero matching RAG results

#### DAT-04.2 — Approved-source allowlist enforced for all production AI

- **Deployment Types:** All
- **Manual/Automated:** Automated
- **AICM Mapping:** DSP-23 (data integrity check / dataset versioning), DSP-20 (data provenance and transparency), DSP-05 (data flow documentation), DSP-21 (data poisoning prevention — version as preventive baseline)
- **External References:** OWASP LLM04:2025 Data and Model Poisoning, NIST AI RMF MAP-4, MEASURE-2.10
- **Key Indicator Rationale:** Producing per-dataset version records that tie a training, fine-tuning, or RAG index to a specific snapshot, with a change-triggered re-run of the DAT-03.1 sensitive-data scan on material updates and a link back to the model or RAG index consuming the dataset, requires dataset-level versioning tooling (DVC, MLflow, LakeFS, Delta Lake time travel, Bedrock Knowledge Base sync history, or an equivalent) to be in place and wired into the governance workflow. L3 has "initial data versioning for critical AI systems"; L4 is comprehensive and auditable.

**Control Objective:** Production RAG indexes and training datasets feed only from approved sources, with each indexed document or training record carrying provenance metadata (source identifier, ingest time). Source additions, removals, and revocations are logged with a named approver, and revocation propagates to production indexes within a defined SLA.

**Description:** The required record fields are: dataset or index identifier, snapshot version (commit SHA, dataset version, knowledge-base sync version, or equivalent immutable reference), approval date, approver, and link to the consuming model or application. The "material change" threshold is organization-defined and written down; a common pattern is "any source addition, any source removal, or >10% content churn since last approval." The rescan reuses the DAT-03.1 workflow so governance does not fork. The tooling landscape is heterogeneous: DVC or LakeFS for self-hosted training pipelines; MLflow or SageMaker Model Registry for managed training; Bedrock Knowledge Base sync history and Azure AI Search indexer history for PaaS RAG; M365 and Salesforce index rebuilds for API/SaaS (where the organization mostly inherits provider versioning and records consumption). **MON boundary:** the capability "reconstruct, from production-output logs, which dataset or index version served a given query within one business day" is a Security Monitoring (MON) capability — it requires invocation telemetry, log retention, and a query layer over the joined log stream. DAT-04.2 owns the version records (the artifacts being looked up) and cross-references the MON KPI that owns the reconstruction SLA. The DAT-05.1 RAG lineage SLA at L5 (4-hour, 98%) is the L5 tightening of that integrated capability. For API/SaaS applications the underlying answer is often "the provider's index at time T" with supporting provider telemetry; the org documents how provider versioning is referenced.

**Evidence:**
- Dataset and index version-record inventory showing each in-scope dataset or index, its snapshot version, approval record, and link to consuming model or application
- Tooling configuration (DVC, LakeFS, MLflow, SageMaker Model Registry, Bedrock Knowledge Base sync history, Azure AI Search indexer, or equivalent) with change-history query
- Sample material-change event with attached re-scan record generated by the DAT-03.1 workflow
- Cross-reference to the MON KPI that owns the log-based reconstruction SLA, plus a sample lookup demonstrating the DAT version records are queryable by identifier and effective date
- Documented material-change threshold and re-scan trigger definition

---

### Level 5 — Efficient

#### DAT-05.1 — RAG citations and continuous source posture monitoring

- **Deployment Types:** All (training lineage is primary for self-hosted and fine-tuned models; RAG lineage applies across all three)
- **Manual/Automated:** Automated
- **AICM Mapping:** DSP-20 (data provenance and transparency), DSP-05 (data flow documentation), DSP-23 (dataset versioning)
- **External References:** NIST AI RMF MAP-4, MEASURE-2.10, GOVERN-1; W3C PROV Data Model; EU AI Act Article 10 (data governance for high-risk systems)
- **Key Indicator Rationale:** Integrated end-to-end lineage — from training or RAG source through dataset version through model registry entry through production deployment to a specific inference output — only exists when the MOD-02.1 model inventory, the DAT-04.2 dataset versioning, and production telemetry are joined in a queryable system with sub-day reconstruction SLA. That integration is an L5 marker; an L4 organization can do the lookup per system but not as one traced chain.

**Control Objective:** Production RAG responses include source citations linking to the contributing documents. Approved sources are continuously monitored for compromise indicators, with detected events triggering automated quarantine and revocation propagating to production indexes within an hour.

**Description:** Specific thresholds: training-lineage test on 20 randomly-selected (model version, query) pairs over the trailing 90 days produces a complete trace for ≥95% of pairs; RAG lineage on 50 randomly-selected production responses over the trailing 90 days reconstructs within 4 hours for 98% of queries. The 4-hour SLA is the L5 tightening of the DAT-04.2 / MON business-day SLA: at L5 the integration is real-time enough that an incident responder or regulator can trace a response within half a day. Both samples are drawn from the trailing 90 days and rotated across model versions and applications so the test exercises the joined system, not a single hot path. The 98% (RAG) and 95% (training) thresholds leave a small window for genuinely ephemeral sources (removed between the query and the reconstruction attempt); those cases are documented as unrecoverable-by-design and capped at <10% of in-scope queries — beyond that the lineage system is not delivering the integrated capability and the KPI is not met. The lineage system is typically a graph or relational model backed by the organization's existing data-governance platform (Collibra, Alation, Unity Catalog, Purview) or a custom query layer over MLflow, DVC, and the model registry. "Under the organization's control" excludes foundation-model training data — the organization does not have lineage into OpenAI, Anthropic, or Google training corpora and this KPI does not demand it; for API/SaaS foundation-model consumption, the training-data portion reduces to documented reliance on provider model-card training-data disclosures, and active lineage is the RAG and fine-tuning side the organization does control. The joined system links: (a) approved data sources from DAT-02.1 and DAT-03.1, (b) dataset and index versions from DAT-04.2, (c) the MOD-02.1 model inventory and MOD-03.2 approved registry entries, and (d) production deployments and invocation telemetry.

**Evidence:**
- Lineage-system schema or data model documentation showing the join across source inventory, dataset version, model registry, and invocation telemetry
- Training-lineage test report: 20 randomly-sampled (model version, query) pairs over the trailing 90 days, with at least 95% producing a complete source → dataset version → model version → deployment trace
- RAG lineage reconstruction report: for 50 randomly-sampled production RAG responses over the trailing 90 days, 98% reconstructed within 4 hours
- Architecture documentation showing the integration between data-governance, model registry, and telemetry systems
- Record of documented unrecoverable cases (capped at <10% of in-scope queries) with cause and governance sign-off

#### DAT-05.2 — Poisoning and Adversarial-pattern scanning on training and RAG content

- **Deployment Types:** All (scope covers training and fine-tuning data under organization control; RAG and grounding content across deployment types; foundation-model pretraining is provider-owned)
- **Manual/Automated:** Automated
- **AICM Mapping:** DSP-21 (data poisoning prevention and detection), DSP-23 (data integrity check), DSP-17 (sensitive data protection — adjacent)
- **External References:** OWASP LLM04:2025 Data and Model Poisoning, OWASP LLM05:2025 Improper Output Handling (adjacent), NIST AI RMF MEASURE-2.7, MITRE ATLAS (Poison Training Data, LLM Meta Prompt Extraction)
- **Key Indicator Rationale:** Running continuous automated scanning for poisoning and adversarial patterns — prompt-injection payloads embedded in documents, backdoor-trigger patterns in training data, anomalous distribution shifts in embedding space, and content from sources flagged by emerging threat intelligence — with findings triaged to a named owner under SLA, requires the detection tooling, the baseline models, the integration with the ingestion pipeline, and an operational team to run it. That is the L5 "scanning for detection of potential data poisoning" capability the main grid describes, paired with the L5 "controls updated proactively as new attack vectors emerge" property.

**Control Objective:** Training data, fine-tuning data, and production RAG and grounding content under the organization's control are scanned for poisoning and adversarial patterns on ingestion and on material update. Scans cover embedded prompt-injection payloads, embedding-space distribution shifts, and matches against an AI-specific threat-intelligence feed; findings route to a named owner under SLA. Foundation-model pretraining is out of scope.

**Description:** Specific thresholds: the threat-intelligence feed updates at least monthly; severity-high findings are triaged within 1 business day and remediated or risk-accepted within 10 business days; 95% of severity-high findings over the trailing 90 days meet both SLAs. The high-severity-SLA-compliance threshold is the operational proof that detection leads to action rather than to a log nobody reads. Detection tooling examples include Lakera, Robust Intelligence, HiddenLayer, or Protect AI for commercial offerings; NVIDIA NeMo Guardrails input scanners, garak adapted for content scanning, or custom embedding-drift detection on the organization's vector store for self-hosted pipelines. Threat-intelligence feeds include OWASP GenAI Security, MITRE ATLAS updates, provider security advisories (Anthropic, OpenAI, Google, AWS), and CSA AI threat intelligence where available. The embedding-space distribution shift is a weak but useful signal: if a knowledge-base sync suddenly adds 10,000 new documents whose embedding distribution is statistically distant from the existing corpus, that is worth triaging even if the individual documents look clean. The explicit out-of-scope note on foundation-model pretraining keeps the control honest: the organization cannot scan OpenAI's pretraining corpus and the KPI does not demand it.

**Evidence:**
- Scanner configuration and tool inventory showing ingestion-time and update-time scan coverage on training, fine-tuning, and RAG content
- Threat-intelligence feed integration configuration with update frequency and coverage of AI-specific adversarial patterns
- 90-day finding history from the scanner and triage system showing severity distribution, owner routing, triage timestamps, and remediation or accepted-risk disposition
- 95%-SLA-compliance report for severity-high findings over the trailing 90 days
- Sample finding lifecycle: detection → triage → remediation or risk acceptance, with timestamps
- Documented out-of-scope note for foundation-model pretraining data, referenced in provider-assessment records (RSK handoff)

---

---

## 9. Risk and Provider Assessment & Management (RSK) <a id="9-risk-and-provider-assessment-and-management"></a>

**Category description:** Managing the phases of the AI risk management process — identification, assessment, treatment, monitoring, and reporting — across AI projects, use cases, and deployments, plus AI provider selection, third-party risk, and ongoing provider reassessment. RSK owns assessment outputs (provider registry with risk ratings, project risk assessments, reassessment triggers on provider change). It does not own the org's policies or approval authority (that's GOV), the regulatory-compliance angle of provider review (that's CMP), or per-model risk review that's already tracked at model-inventory level (that's MOD-02.1).


---

### Level descriptors (reference — from AISMM main grid)

- **L1 Initial:** No AI-specific risk assessment. AI providers and models selected by business units or individuals without security involvement. Existing general vendor assessment processes (if any) applied inconsistently to AI. No differentiation between AI services and other technology procurements. No registry of approved AI providers or models.
- **L2 Repeatable:** Security performs risk assessments for major AI providers and platforms when requested. Initial provider registry documents approved AI providers (may be informal, e.g., spreadsheet). Basic evaluation criteria established. Security engaged for some AI project risk assessments but not consistently. Initial broad data-classification requirement set for all providers/models.
- **L3 Defined:** Initial AI provider/model assessment process using industry frameworks (AI-CAIQ, AICM). Major provider/model registry documents approvals by data classification/type. Initial AI-specific project risk-assessment process. Open/third-party models require documented risk evaluation before use. Providers reassessed on a scheduled basis (typically annually) or after significant changes.
- **L4 Capable:** Provider/model registry with approvals by data type and use case. Application risk registry includes AI risk rating. Risk assessments and management plans integrated into the AI project lifecycle starting at design/architecture. Provider assessments and mitigating controls updated when providers release new models or service changes. Initial automation tracks major provider/model updates requiring reassessment.
- **L5 Efficient:** Automated discovery of AI services and models via CSPM and AI-SPM tooling feeds the risk process. Monitoring for provider and model updates with alerting triggers reassessment and mitigation. Application risk registry integrated with AI discovery tooling for enterprise visibility. Defined, efficient process to rapidly assess new provider releases and model updates. Risk dashboards aggregate provider and application risk data.

---

### Scope note — RSK / GOV / CMP / MOD boundaries

- **RSK vs. GOV:** GOV sets the rules — acceptable-use policy, approval authority, safety/ethics framework, decision rights. RSK executes the assessments against those rules: assessing Anthropic, OpenAI, Azure OpenAI, AWS Bedrock, Google Vertex, and self-hosted-model providers for risk; rating them; keeping a provider registry with risk ratings; reassessing on change.
- **RSK vs. CMP:** RSK is risk-flavored — risk scoring, risk treatment plans, risk acceptance records, reassessment triggers. CMP is compliance-flavored — AI-CAIQ completion as regulatory evidence, PIAs, IP/licensing verification, regulatory-requirement tracking, audit evidence. When both files look at the same provider, RSK asks "what's our risk exposure and treatment plan" and CMP asks "which regulatory obligations apply and can we prove we met them." A single AI-CAIQ completion can serve both — RSK consumes it as the structured risk-finding source; CMP files the same artifact as compliance evidence. One source, two uses.
- **RSK vs. MOD:** MOD-02.1 already inventories production models with a per-model dated risk review. RSK covers the broader picture — the provider behind the model (Anthropic the company, not just the Claude Sonnet entry), the AI project or use case consuming one or more models, and the application risk register entry for the AI application. If the artifact is a model in production, MOD owns the risk-review record. If the artifact is a provider, a project, or an AI application portfolio entry, RSK owns it.
- **Frontier/foundation weighting:** Provider assessment primarily means assessing the major frontier/foundation providers — Anthropic, OpenAI, Microsoft/Azure OpenAI, Google/Vertex AI, AWS/Bedrock — because that's where the concentration of enterprise AI consumption sits. Self-hosted/open model providers (Meta, Mistral, HuggingFace model authors) are secondary and handled through the open-model risk-review path.
- **Cross-category dependencies (noted, not gated):** RSK-02.1's authoritative-registry status depends on GOV designating it as the authoritative approval registry. RSK-04.2's coverage depends on AI-BOM visibility owned by DEV. RSK-05.1's automated discovery depends on discovery feeds from ORG and MON. These are dependencies in prose, not hard prerequisites — organizations may legitimately have uneven maturity across categories, and the path to RSK maturity describes the destination rather than enforcing a sequence. Provider exit and de-provisioning lifecycle is covered in IR (incident-driven exit) and DAT (data return/deletion on exit), not duplicated here.

---

### Level 2 — Repeatable

#### RSK-02.1 — Approved AI provider registry with risk ratings and data classifications

- **Deployment Types:** All
- **Manual/Automated:** Manual
- **AICM Mapping:** STA-08 (supply chain inventory), STA-09 (supply chain risk management), GRC-02 (AI risk management program)
- **External References:** NIST AI RMF Map function; CSA AI-CAIQ (reference framework)
- **Key Indicator Rationale:** An organization that can produce a single registry listing every approved AI provider with a dated risk rating and the data-classification scope the provider is approved for has committed to central visibility over AI provider decisions. That commitment is the L2 signal — not that the registry is comprehensive or uses a formal framework, but that it exists as the authoritative list and distinguishes AI providers from generic vendors.

**Control Objective:** A registry of approved AI providers records a risk rating and maximum data classification for each major provider in use, and project leads consult it before using a provider with a given data type.

**Description:** The L2 bar is authoritative visibility, not methodological rigor. The registry can be a spreadsheet, a GRC-tool entry, or a row in the CMDB — what matters is that there is one place the organization points to when asked "which AI providers have we approved and at what data classification." A named function maintains the registry. Each entry records the provider, approved model families or SKUs (Anthropic/Claude, OpenAI/GPT, Azure OpenAI deployments, Bedrock model ARNs, Vertex publisher models, self-hosted or open-model providers in use), a risk rating on a scale of at least three tiers, maximum approved data classification, initial-assessment date, and reviewer. The 80%-of-spend and all-confidential-or-higher scope thresholds prevent the L2 registry from being a token list of two frontier providers while shadow adoption runs through Copilot, Gemini, Perplexity, and ChatGPT Enterprise seats purchased by business units. The risk-rating scale doesn't need to be sophisticated at L2 (low/medium/high is fine); it needs to exist and be applied consistently across entries. Data-classification scope is load-bearing — "approved for public data only" versus "approved for internal-confidential" is the control that tells a project lead whether they can push customer data to a given provider. Recording approved model families or specific SKUs (rather than a vague "major models") is the granularity that makes the registry actionable: a project lead can look up whether GPT-4o is approved at internal-confidential, not just whether "OpenAI" is. The registry is the RSK artifact; whether individual models within an approved provider are separately inventoried for production use is MOD-02.1's job. Authoritative status here assumes GOV has designated this registry as the org's approval-of-record; without that designation the registry is a list rather than a control.

**Evidence:**
- Registry export showing provider name, approved model families or SKUs, risk rating, maximum approved data classification, initial-assessment date, and reviewer per entry
- Definition document for the risk-rating scale (minimum three tiers) and data-classification scope values
- Reconciliation showing the registry covers at least 80% of AI provider spend (sourced from procurement/AP data or SaaS-management tooling) and every provider handling internal-confidential-or-higher data

#### RSK-02.2 — AI project risk assessment at initiation

- **Deployment Types:** All
- **Manual/Automated:** Manual
- **AICM Mapping:** GRC-02 (AI risk management program), GRC-10 (AI impact assessment)
- **External References:** NIST AI RMF Map function; ISO/IEC 23894 (AI risk management)
- **Key Indicator Rationale:** An organization that produces dated, signed project risk assessments for in-scope AI projects before they go live has made security engagement on AI projects the default rather than the exception. That's the L2 "security engaged for some AI project risk assessments" bar made measurable — "some" becomes "every project that meets an inline scope definition."

**Control Objective:** Major AI projects (those meeting a written in-scope definition) do not launch to production without a dated security risk assessment naming providers, models, data classification, risk rating, and reviewer.

**Description:** The L2 construct is "risk assessment at initiation for projects that clearly need one" — not comprehensive coverage (L3) and not lifecycle-integrated risk management starting at design (L4). The inline scope definition (minimum: projects processing internal-confidential-or-higher data, customer-facing, regulated use case, or exceeding a cost/user-count threshold) matters more than any specific threshold: an L2 organization has written down what "in-scope AI project" means so the assessment population is countable. The 75% coverage bar accommodates the L2 reality that some projects will still slip past security without breaking the program's claim to repeatable practice; an L3 organization should be hitting 90%+ with a more standardized process. Each assessment records the project owner, providers and major models involved, data classification, initial risk rating, and reviewer; assessments completed within 30 days of launch are acceptable for projects predating this control. The assessment artifact can be a structured questionnaire, a filled-in template, or a ticket with mandatory fields — what it can't be is a verbal sign-off or a Slack thread. Project risk assessments here complement but do not replace RSK-02.1: a project may consume an already-approved provider and still needs its own risk assessment because the use case, data, and user population are project-specific. The L2 project assessment is lightweight; L4 adds lifecycle integration and L5 adds automation feeds.

**Evidence:**
- Written scope definition describing which AI projects require a risk assessment at initiation
- List of AI projects initiated in the trailing 12 months with a flag indicating whether each was in-scope and whether an assessment was completed
- Sample of three completed project risk assessments from across business units showing project owner, providers/models involved, data classification, risk rating, and reviewer
- Coverage metric showing at least 75% of in-scope projects have a completed assessment

---

### Level 3 — Defined

#### RSK-03.1 — Standardized AI provider assessment against a named framework

- **Deployment Types:** All
- **Manual/Automated:** Manual
- **AICM Mapping:** STA-15 (supply chain data security assessment), STA-12 (supply chain compliance assessment), GRC-02 (AI risk management program)
- **External References:** CSA AI-CAIQ; CSA AICM v1.0.3; ISO/IEC 42001; NIST AI RMF Govern/Map
- **Key Indicator Rationale:** Producing a completed framework-based assessment (AI-CAIQ, AICM-derived, or equivalent structured methodology) for every provider in the registry is the L3 "standardized process using industry frameworks" signal. An L2 organization rates providers on ad-hoc criteria; an L3 organization has adopted a standard methodology, applies it to the population, and can point an auditor at the assessment artifact.

**Control Objective:** Providers in the registry are assessed against a single named methodology (via STAR registry, AI-CAIQ, an AICM-derived questionnaire, ISO/IEC 42001 provider alignment, or documented equivalent), and each provider's approved data-classification scope traces to a specific finding in the assessment.

**Description:** L3's defining property is consistency of methodology across the provider population. The assessment covers data handling and residency, provider security certifications, training-data-use terms, model-output ownership and IP, subprocessor disclosures, incident notification, and deletion/retention commitments. Swapping AI-CAIQ between frontier providers and a reduced AICM-derived subset for open-model providers is acceptable as long as the choice is written down and applied uniformly within each tier. The linkage between framework findings and the registry's approved data-classification scope is the control that turns an assessment into a decision: an organization that completed an AI-CAIQ but then sets the approved classification by gut feel has done the exercise without the decision. Assessment storage should be traceable from the registry entry (link or attachment), not a shared-drive folder someone has to hunt through. **Boundary with CMP:** RSK runs the AI-CAIQ (or equivalent) for risk findings — what's our exposure, what treatment do we need; CMP files the same completed AI-CAIQ as compliance evidence — does this provider meet our regulatory obligations. Single source, two uses; do not double-collect. At L4 the same assessment becomes a reassessment-on-change artifact; at L3 the initial-assessment completeness is the bar.

**Evidence:**
- Completed framework-based assessments stored with each RSK-02.1 registry entry
- Named methodology document describing which framework (or which sections of AICM) is used for frontier providers, PaaS providers, and open-model/self-hosted providers
- Sample of three provider assessments across tiers (frontier, PaaS, open/self-hosted if applicable) showing the framework sections completed and the finding that justifies the approved data-classification scope
- Traceability from a registry entry's approved-classification value to a specific finding in the assessment

#### RSK-03.2 — Scheduled provider reassessment with evidenced completion

- **Deployment Types:** All
- **Manual/Automated:** Manual
- **AICM Mapping:** STA-09 (supply chain risk management — periodic review), STA-11 (supply chain agreement review), STA-14 (supply chain governance review)
- **External References:** CSA AICM v1.0.3; NIST AI RMF Govern-6
- **Key Indicator Rationale:** An organization that can show on-cadence reassessment for at least 90% of registry entries over the trailing 18 months has operationalized the reassessment program — it's not just a calendar reminder in someone's Outlook. Missed reassessments concentrate at the tail of the portfolio, so the 90% bar is the signal that the tail is getting worked, not just the top three providers.

**Control Objective:** Providers in the registry are reassessed on a written cadence (at least annually, more often for higher-risk providers), and an overdue entry is either closed with evidence, carries a named risk acceptance, or is flipped to a restricted flag that blocks new use until the reassessment is done.

**Description:** The L3 reassessment bar is scheduled completion, not event-driven reassessment (that's L4). The 18-month trailing window captures whether the current cadence has held through a full annual cycle plus some overlap. Evidence stored against the registry entry takes the form of an updated questionnaire, a delta review, or a signed no-change attestation. A delta review is acceptable when the provider's documentation hasn't materially changed — the organization doesn't need to re-complete a full AI-CAIQ every year if the provider's posture hasn't shifted — but a reviewer has to make that determination and record it. Misses carry a remediation date and named owner; entries overdue by more than 90 days trigger documented risk acceptance by the risk owner or the `restricted` flag. The overdue-and-acceptance branch is what keeps the KPI from being gameable by quietly letting lapsed entries sit: an overdue reassessment either gets done, gets explicitly accepted as risk by a named owner, or the registry entry's `restricted` field flips to true. `Restricted` is a binary register field, not a hedge — when set, the provider remains in the registry but is not approved for new projects or new data classifications until the overdue reassessment is closed and the field is flipped back. Entries where the organization has decided to deprecate the provider should be marked that way in the registry and are out of scope for the coverage metric.

**Evidence:**
- Registry showing reassessment cadence per entry (annual, or shorter for higher-risk) and the binary `restricted` field
- 18-month schedule-vs-actual report showing reassessment completion dates, misses, and current overdue entries
- Completion-rate metric showing at least 90% of scheduled reassessments completed on or before date
- Sample of three reassessment records covering a full questionnaire refresh, a delta review with documented no-change finding, and a signed risk-acceptance for an overdue entry

#### RSK-03.3 — Open and Third-party model risk evaluation before adoption

- **Deployment Types:** Self-hosted, PaaS where customer-brought open models are supported (Bedrock Marketplace, Azure AI Foundry model catalog, Vertex AI Model Garden)
- **Manual/Automated:** Manual
- **AICM Mapping:** GRC-02 (AI risk management program), STA-15 (supply chain data security assessment — open-model source), MDS-12 (open model risk assessment — cross-reference to MOD inventory)
- **External References:** NIST AI RMF Map-4; OWASP LLM03:2025 Supply Chain; Hugging Face model cards and provider transparency documentation
- **Key Indicator Rationale:** Requiring a documented risk evaluation for every open or third-party model before adoption is the L3 "documented risk evaluation before use" signal from the main grid. An organization that can produce the evaluation record for each open-model entry has forced the assessment to happen at the decision point rather than after the model is already running in production.

**Control Objective:** Open-source and third-party models reach production only after a documented evaluation of provenance, license, publisher trust, and known security findings, signed by a named approver and linked to the model's entry in the approved model registry.

**Description:** Open-model risk has a different shape from PaaS/API-SaaS provider risk — there's no SOC 2, no SLA, no incident notification. The evaluation is about provenance, license, publisher trust, and known issues. Scope covers Llama, Mistral, Qwen, DeepSeek, or any Hugging Face-sourced model in production or user-facing pilot. The evaluation record captures source and hash/commit reference, license terms, training-data disclosure status, publishing organization and credibility judgement, known security or adversarial-robustness findings, and a decision with named approver. Tying the evaluation to the MOD-02.1 inventory entry is the point where RSK and MOD meet: RSK owns the decision to adopt the open model from a risk perspective, MOD owns the ongoing production inventory and model-layer safety review. Frontier models consumed through Bedrock Marketplace or Vertex Model Garden still count as open/third-party for this KPI if the organization is pulling in a non-cloud-native model (for example, a Llama variant deployed through Bedrock custom import) — the cloud provider's platform wraps the model but doesn't absorb the model-provenance risk. This KPI is bounded to the adoption decision; ongoing reassessment of open models on source changes is an L4/L5 capability covered by RSK-04.1 and RSK-05.2.

**Evidence:**
- Written evaluation template for open/third-party model risk covering source, license, training-data disclosure, publisher credibility, known security findings, and approval decision
- Completed evaluations for every open/third-party model in the MOD-02.1 inventory, dated before or at production adoption
- Traceability from an open-model MOD-02.1 entry to its RSK-03.3 evaluation record
- Sample of two evaluations showing the decision rationale and named approver

---

### Level 4 — Capable

#### RSK-04.1 — Provider change triggers reassessment within SLA

- **Deployment Types:** All
- **Manual/Automated:** Either
- **AICM Mapping:** STA-09 (supply chain risk management), STA-11 (supply chain agreement review on significant change), MDS-10 (continuous monitoring — provider-change detection cross-reference)
- **External References:** NIST AI RMF Manage-4.1; OWASP LLM03:2025 Supply Chain
- **Key Indicator Rationale:** Closing the loop from "provider announces a material change" to "reassessment is underway or complete within a defined SLA" requires someone watches provider announcements, an SLA is set and honored, and the risk team has the capacity to keep up. The trailing-12-month SLA-compliance rate makes this measurable as an outcome of the program, not just the existence of a trigger list.

**Control Objective:** A material change at an approved provider (new model release, ToS shift, security incident, deprecation, or ownership change) opens a reassessment item on a defined SLA, and the item closes with an updated assessment or recorded risk acceptance before the SLA expires.

**Description:** L4's defining property is event-driven reassessment — the L3 scheduled cadence becomes a floor, not the whole program. The trigger list is the control: without a written definition of "material change," the detection side becomes subjective and the compliance metric can't be computed. Material changes include (minimum): new foundation-model release in use or planned, provider acquisition or ownership change, ToS change covering data handling/training-data/output IP, significant provider security incident or breach, deprecation of an approved model, or CVE affecting a provider service in use. The 10-business-day open-item SLA is fast enough to keep up with frontier providers' monthly release cadence; the 45-business-day completion SLA is realistic for a reassessment that may require re-running parts of an AI-CAIQ while leaving real daylight between L4 (any material change) and L5's tighter window for frontier-release events specifically. The reassessment doesn't always produce a change in approved data-classification scope — a new Claude release may be approved at the same classification as the prior version — but the assessment itself and its documented no-change finding are the output. Detection infrastructure (monitoring release notes, ToS-change trackers, breach feeds) overlaps with MOD-05.2 for model-layer changes; RSK-04.1 covers the provider-level signal and ensures the assessment follow-through happens.

**Evidence:**
- Written definition of material provider change triggering reassessment
- Detection source list (provider release notes, ToS-change trackers, provider security-bulletin feeds, breach/incident feeds)
- 12-month log of detected material changes with open date, completion-or-acceptance date, and owner
- SLA-compliance metric showing at least 90% of material-change reassessments met both timelines
- Sample reassessment for a real provider change (for example, a new foundation-model release or a terms-of-service update) showing the full lifecycle

#### RSK-04.2 — AI risk rating lands in the enterprise application risk registry

- **Deployment Types:** All
- **Manual/Automated:** Either
- **AICM Mapping:** GRC-02 (AI risk management program), GRC-10 (AI impact assessment), STA-08 (supply chain inventory cross-reference)
- **External References:** NIST AI RMF Manage-1; ISO/IEC 42001
- **Key Indicator Rationale:** Integrating AI risk ratings into the enterprise application risk registry so that AI-using applications show up alongside non-AI applications with a comparable rating is the L4 "application risk registry includes AI risk rating" signal. It forces the AI program to stop being a parallel-universe risk system and start feeding enterprise risk reporting — measured by use, not by presentation.

**Control Objective:** AI risk shows up as a dimension of application risk in the same enterprise registry that holds non-AI applications, on the same rating scale, and the registry data drives prioritization and treatment decisions.

**Description:** The L4 move is integration rather than invention — AI risk lands in the same registry the CISO already uses to report application risk to the CEO or the board, not in a separate AI-only dashboard. The rating scale consistency is what makes this work: if application risk uses low/medium/high/critical and AI risk uses a 1-10 score that nobody else understands, the integration is cosmetic. Each AI risk rating derives from providers/models in use, data classification processed, use case category, and findings from RSK-02.2 project risk assessments, and is dated within the trailing 12 months. The 90% coverage-of-AI-using-applications threshold ties this to the AI-BOM and application inventory — coverage of this KPI depends on AI-BOM visibility maintained by DEV; if the organization doesn't have visibility into which applications consume AI, it can't report an AI risk rating for them, which tees up the L5 automated-discovery dependency. The L4 bar is use-as-proof, not presentation-as-proof: a registry that is presented to a forum twice a year but never changes a decision is a shelf artifact. The control objective requires at least two documented instances where the registry data drove a risk decision, prioritization, or treatment action over the trailing 12 months — that's the signal the registry has been wired into how the organization actually operates. Portfolio risk management as used here means treating AI risk as one dimension of application risk, not as a separate discipline.

**Evidence:**
- Application risk registry export showing AI-using applications with their AI risk rating and rating date
- Methodology document describing how AI risk rating maps onto the broader application risk rating scale
- Coverage metric showing at least 90% of AI-using applications carry a current AI risk rating
- Documentation of at least two trailing-12-month decisions, prioritizations, or treatment actions that cite AI risk registry data as input (decision memo, governance-meeting minutes, treatment-plan record, or equivalent)

#### RSK-04.3 — Treatment plan or risk acceptance recorded for high and medium findings

- **Deployment Types:** All
- **Manual/Automated:** Manual
- **AICM Mapping:** GRC-02 (AI risk management program), GRC-10 (AI impact assessment), STA-09 (supply chain risk management — treatment)
- **External References:** NIST AI RMF Manage; ISO/IEC 23894 (AI risk treatment)
- **Key Indicator Rationale:** Closing the loop from "we found a High or Medium risk" to "there is a recorded treatment plan or formal acceptance for it" is the L4 capability that turns assessment output into managed posture. An L3 organization can produce dated assessments; an L4 organization can also produce a current state for every High/Medium finding — what's being done about it, by when, by whom, or who has accepted the residual risk. Without this loop the assessment work is documentation rather than risk management.

**Control Objective:** Critical, High and Medium AI risk findings land a documented outcome (a treatment plan with a named owner and target date, or a time-bounded risk acceptance with a named approver), and a quarterly risk forum works the register so aging items, expired acceptances, and overdue actions surface for action.

**Description:** This is the L4 treatment-loop bar — the capability that lifts the program from "we assess risks" to "we manage risks." Findings in scope come from RSK-02.2, RSK-03.1, RSK-03.3, and RSK-04.1. Treatment plans capture named owner, planned actions, and target date; acceptances capture named approver, justification, and expiration date. Lower-severity findings (Low or informational) are recorded but not gated by this KPI; the 90% bar applies to High and Medium because those are the ratings that matter for executive risk reporting and that an L4 program is expected to actively manage. Treatment plans don't have to mean remediation in every case — an explicit "monitor for 90 days, reassess" plan is a plan; what's not acceptable is a finding sitting in the register with no owner and no decision. Risk acceptances must carry an expiration so the register doesn't accumulate evergreen "accepted forever" entries that obscure the real risk posture; expired acceptances either get renewed (with a new justification) or trigger remediation. The quarterly review keeps the register honest by surfacing aging items, expiring acceptances, and overdue treatment actions to a risk-owner forum. Provider exit and de-provisioning treatment paths (when a finding's resolution is "stop using this provider") are coordinated with IR for incident-driven exit and DAT for data-return / deletion verification, not duplicated in this KPI.

**Evidence:**
- Treatment/acceptance register showing every High and Medium finding with dated treatment plan or acceptance record, owner/approver, target or expiration date
- Coverage metric showing at least 90% of trailing-12-month High and Medium findings met the 30-business-day bar
- Sample of three records: one open treatment plan, one closed treatment action, one risk acceptance with named approver and expiration
- Minutes or summary from at least four quarterly review forums in the trailing 12 months showing the register was reviewed and aging items addressed

---

### Level 5 — Efficient

#### RSK-05.1 — Automated AI discovery feeds the risk process with reconciliation

- **Deployment Types:** All
- **Manual/Automated:** Automated
- **AICM Mapping:** STA-08 (supply chain inventory), GRC-02 (AI risk management program), STA-15 (supply chain data security assessment — discovery-triggered)
- **External References:** CSA Guidance on AI-SPM; NIST AI RMF Govern-1.6
- **Key Indicator Rationale:** An organization that can show AI-SPM and CSPM discovery finding unknown AI services and feeding them into the risk-assessment queue within a defined SLA — with a reconciliation rate that proves the automation is actually closing the visibility gap rather than producing a backlog — has the L5 discovery-driven posture. This is the main grid's "automated discovery of AI services and models in use via CSPM and AI-SPM tooling feeds risk process" rendered as a measurable outcome.

**Control Objective:** CSPM/CNAPP, SaaS security tooling, and AI-SPM if available reconcile weekly against the provider and application risk registries, and a newly-discovered AI service is added with a risk rating (pulled automatically from tooling or the CSA STAR registry), attributed to an existing entry, or documented as a false positive within a defined SLA.

**Description:** The L5 question isn't "do you have an AI-SPM tool" (that's a procurement outcome); it's "does the discovery output change what's in the risk registry, on a timeline that keeps up with shadow adoption." Discovery tooling (AI-SPM, CSPM with AI-service detection, SaaS-management, CASB egress, or named equivalents) covers every major cloud and SaaS environment in use; discovered AI services, models, and consuming applications reconcile against the RSK-02.1 and RSK-04.2 registries; new items resolve to one of three outcomes (added with a risk rating, attributed to an existing entry, or documented as a false positive). The 5-business-day item-open SLA and 30-business-day resolution SLA are calibrated to the real cadence of shadow-AI adoption — a Copilot license purchased by a business unit or a Hugging Face model quietly pulled into a pipeline shouldn't sit undetected for a quarter. The 90% resolution rate is the durability signal: discovery tools tend to produce a flood of alerts in the first month of deployment and then backlog, and the 90-day trailing metric penalizes that backlog. Reconciliation cadence at weekly is load-bearing — monthly discovery lets too much shadow adoption accumulate between syncs. Reconciliation-state snapshots are retained for 12 months. Discovery itself depends on feeds from ORG (cloud-environment AI-service detection) and MON (egress and SaaS-usage telemetry); RSK consumes those feeds rather than owning the discovery infrastructure, which is why the KPI is about reconciliation outcome rather than tool ownership. The reconciliation-state retention supports the L5 audit posture and harmonizes with MOD-05.2 for provider-change detection.

**Evidence:**
- AI-SPM / CSPM / CASB / SaaS-management tool configurations showing coverage of major cloud and SaaS environments
- Weekly reconciliation report comparing discovery output to RSK-02.1 and RSK-04.2 registries
- 90-day queue data showing open/resolved state on discovered items with detection-to-resolution timestamps
- Resolution-rate metric showing at least 90% of discovered items reached resolution within 30 business days
- Sample of three discovered items showing lifecycle from detection to resolution (new-entry-added, attributed-to-existing-entry, false-positive)

#### RSK-05.2 — Rapid Frontier-release assessment with dashboarded risk aggregation

- **Deployment Types:** All (primary weight on frontier PaaS and API/SaaS providers)
- **Manual/Automated:** Either
- **AICM Mapping:** STA-09 (supply chain risk management), GRC-02 (AI risk management program), MDS-10 (continuous monitoring — cross-reference for model-layer provider-change detection)
- **External References:** NIST AI RMF Manage-4.1; OWASP LLM03:2025 Supply Chain
- **Key Indicator Rationale:** Assessing a new frontier-provider release and publishing an updated risk posture within a compressed SLA — and keeping a live risk dashboard that aggregates provider and application risk — is the L5 "defined, efficient process to rapidly assess and manage new provider releases" plus "risk dashboards aggregate provider and application risk data" bar from the main grid. The trailing-12-month metric on frontier releases makes it measurable.

**Control Objective:** A frontier-provider release (a new Claude, GPT, or Gemini generation, or a major service change at Bedrock, Azure OpenAI, or Vertex) drives an initial risk-posture update within days and a full reassessment within weeks, and the outcome lands on a live enterprise AI risk dashboard that executive or board risk forums review at least quarterly.

**Description:** The L5 tightening over L4 is on two axes — speed and aggregation — and the scope distinction is what keeps the L4/L5 levels from collapsing onto each other. Frontier-release events include new Claude/GPT/Gemini generations, major Bedrock/Azure OpenAI/Vertex service changes affecting an approved frontier model, and significant frontier-provider security advisories. RSK-04.1 covers any material provider change at a 45-business-day completion SLA; RSK-05.2 narrows to *frontier-release events specifically* — new model generations or major service changes from frontier providers — at a 30-business-day SLA. Frontier releases are where the organization's risk exposure concentrates and where business teams are pushing fastest to adopt; halving the assessment window to a frontier-only scope is what an L5 program does on top of the L4 cadence, not in place of it. The 10-business-day initial-posture update is what lets application teams make go/no-go decisions on adopting a new model generation within the business cycle rather than after it. Dashboard aggregation draws from RSK-02.1 (provider risk ratings), RSK-04.2 (application AI risk ratings), RSK-04.1 (open reassessment items), RSK-04.3 (open treatment/acceptance items), and RSK-05.1 (discovery-queue backlog), refreshed weekly with access logged. This is the sign of a program where the prior levels were built as data sources, not as paper artifacts. Executive/board presentation of the dashboard at least quarterly closes the reporting loop with GOV and completes the L5 posture of risk data feeding enterprise governance.

**Evidence:**
- Written definition of frontier-provider release events triggering the 10/30-day SLA, with the scope distinction from RSK-04.1's broader material-change definition explicit
- 12-month log of frontier-provider release events with initial-posture and full-reassessment completion dates
- SLA-compliance metric showing at least 90% of events met both SLAs
- Risk dashboard export or screenshot showing aggregated provider risk, application AI risk, open reassessment items, open treatment/acceptance items, and discovery-queue backlog, with refresh timestamp
- Access/review logs for the dashboard and executive/board presentation materials from at least four quarterly risk forums in the trailing 12 months

---

---

## 10. AI Supported Development and Supply Chain Security (DEV) <a id="10-ai-supported-development-and-supply-chain-security"></a>

**Category description:** Technical and process controls for (1) the secure use of AI developer tools — enterprise coding assistants and agents such as GitHub Copilot Business/Enterprise, Cursor, Windsurf, and Claude Code — and (2) the secure software supply chain for AI components consumed by the organization: foundation/frontier models, AI libraries and frameworks (LangChain, LlamaIndex, transformers), MCP servers, and other AI-specific dependencies. Covers AI-BOM generation and maintenance, AI-specific SAST/SCA, pipeline gating, and provenance controls for AI components. The model-artifact signing/verification gate for self-hosted models lives in MOD-04.1; DEV owns the breadth of AI-component supply-chain inventory, scanning, and vulnerability tracking. Enterprise licensing and central admin of AI coding tools live in ORG; DEV covers the secure configuration and use of those tools inside the software-delivery process.


---

### Level descriptors (reference — from AISMM main grid)

- **L1 Initial:** No controls over AI coding assistant usage; developers self-select and configure tools. No visibility into which AI tools access enterprise code. AI components (models, libraries) not differentiated from other software dependencies. No awareness of AI-specific supply chain risks. Traditional SCA may flag some AI library vulnerabilities but no AI-specific assessment.
- **L2 Repeatable:** AI coding assistant risks identified. Some approved AI coding tools identified but enforcement inconsistent. Initial documentation of AI components in use (models, AI libraries, services). Basic guidance on AI tool usage. AI libraries included in standard SCA scanning but no AI-specific checks.
- **L3 Defined:** Enterprise-managed AI coding assistant deployed (e.g., GitHub Copilot Business/Enterprise) configured to prevent code exposure to model training. AI coding tool usage tracked via enterprise licensing. AI components included in SAST/SCA scanning. AI providers and major AI components documented in supply-chain inventory. Open models require integrity verification before use.
- **L4 Capable:** SAST/SCA tools include AI-specific assessment. Security testing integrated into pipelines for AI-generated and AI-assisted code. AI security agents integrated into CI/CD. AI supply chain inventory includes models, versions, MCPs, and dependencies (initial AI-BOM). Model provenance verification for self-hosted models. Automated scanning blocks known-vulnerable AI libraries and unsafe model formats.
- **L5 Efficient:** Multiple AI development tools supported with consistent enterprise security controls. On-demand agent-based security assessments available in IDE. AI security agents integrated into pipelines for automated code review. AI-BOM generated and maintained with breadth across models, libraries, MCPs, and data sources. Model signing and provenance verification standard for production deployments. Supply chain monitoring alerts on new vulnerabilities in AI dependencies.

---

### Scope note — DEV boundaries

- **DEV ↔ MOD.** MOD-04.1 owns the self-hosted model artifact signing/verification gate at load time. DEV owns the breadth of AI-component supply-chain inventory (the AI-BOM), scanning, vulnerability tracking, and provenance attestation capture for components other than the self-hosted model gate. DEV is the authoritative owner of the AI-BOM artifact; MOD references AI-BOM content for its own registry. For vendor-supplied unsigned model artifacts that the organization re-signs locally, DEV-04.1 owns the ingest-time scan and integrity record produced before re-signing; MOD-04.1 owns the signing operation and the load-time verification gate.
- **DEV ↔ APP.** DEV stops at the deployable artifact leaving the pipeline. APP owns what the application does at runtime with that artifact (guardrails, system prompts, runtime I/O validation, HITL enforcement).
- **DEV ↔ ORG.** ORG covers enterprise licensing, tenant admin, and central account plumbing for AI coding tools — the shared-services side of the AI coding tool program. DEV covers secure configuration of those tools against code exposure, their integration into CI/CD, and developer-level secure-use controls. The two are intentionally split per shared-services framing: ORG is "we have the tenant licensed and admin'd"; DEV is "the tenant is configured securely and integrated into the SDLC."
- **DEV ↔ CMP / RSK.** Provider risk assessment (model-provider due diligence, contract review) is RSK. Regulatory obligations on supply-chain documentation (EU AI Act, SBOM mandates) are CMP. DEV owns the technical supply-chain artifacts that feed both.

---

### Level 2 — Repeatable

#### DEV-02.1 — Approved AI coding assistants with usage guidance

- **Deployment Types:** All
- **Manual/Automated:** Manual
- **AICM Mapping:** CCC-01 (change management policy), TVM-02 (malware / malicious instructions protection — coding-tool exposure)
- **External References:** OWASP LLM03:2025 Supply Chain; NIST SSDF (SP 800-218A) for AI-assisted development; GitHub Copilot / Cursor / Claude Code enterprise configuration guides
- **Key Indicator Rationale:** An organization that can produce a named list of approved AI coding tools paired with written usage guidance has moved past L1 self-selection. The list and the guidance together are the L2 signal — the organization has identified the two primary dev-tool risks (code exposure to model providers, insecure suggestions) and made a defensible decision about which tools developers should use.

**Control Objective:** Developers working on major production codebases use a named set of approved AI coding assistants (e.g. GitHub Copilot Business, Cursor, Claude Code) under written guidance covering what code can be exposed to model providers and how AI-generated suggestions are reviewed before commit. Engineering managers have acknowledged the guidance.

**Description:** This KPI is deliberately lightweight and represents the first real step out of L1. At L2 the organization has not yet enforced tool selection technically and has not yet disabled consumer-tier tools; it has recognized the two foundational AI-coding-tool risks (code exposure to model providers, insecure suggestions) and named a list. The approved list typically names tools like GitHub Copilot Business/Enterprise, Cursor, or Claude Code, with tool version or edition (Business/Enterprise/Free) per entry. The usage guidance is a one- or two-page document covering: prohibition on pasting production source, secrets, or regulated data into consumer-tier AI chat tools; required use of enterprise-tier tools where available; and review of AI-generated code before commit. "Acknowledged by developer managers" is the operationalization: a shared channel or wiki with manager sign-off timestamps counts; an untouched document no one has seen does not. Consumer-tier vs. enterprise-tier matters because the usage-policy and retention differences are the core risk driver — a developer pasting code into the free ChatGPT web UI is a very different exposure than the same developer using Copilot Business with training opt-out configured.

**Evidence:**
- Named list of approved AI coding assistants with tool version or edition (Business / Enterprise / Free) per entry
- Usage guidance document addressing code-exposure and suggestion-review expectations
- Manager acknowledgement log (email confirmations, wiki sign-offs, or training completion records) covering major engineering orgs
- Dated review of list and guidance within the trailing 12 months

#### DEV-02.2 — Initial AI component inventory in SCA scope

- **Deployment Types:** All
- **Manual/Automated:** Manual
- **AICM Mapping:** STA-08 (supply chain inventory), STA-16 (service bill of material), TVM-05 (external library vulnerabilities)
- **External References:** CycloneDX ML-BOM; OWASP LLM03:2025 Supply Chain; NIST SP 800-218 SSDF
- **Key Indicator Rationale:** An organization that can produce a single inventory listing its AI-component consumption (model providers, primary AI frameworks, any self-hosted or open models, MCP servers in production use) and can demonstrate those AI libraries are inside the existing SCA scanning scope has the L2 supply-chain-awareness posture. It's not an AI-BOM yet — that's L4 — but it's the first artifact that differentiates AI components from generic dependencies.

**Control Objective:** AI components used in production (model providers, foundation models, primary AI libraries such as LangChain or transformers, and MCP servers) are tracked as a distinct class in an inventory, and those libraries fall inside the existing SCA scanning scope.

**Description:** The two threads here are supply-chain-breadth (the component inventory) and dev-tool-usage does not yet show up at L2 (that's DEV-03.1's enterprise-managed tool config). The inventory covers: model providers and foundation models (Bedrock, Azure OpenAI, Anthropic, Vertex AI, self-hosted or third-party); primary AI libraries (LangChain, LlamaIndex, transformers, or equivalents) with version ranges observed; and MCP servers integrated with any production agent. The inventory can live in the same place as the organization's existing application inventory or CMDB — the point is that AI components are now a distinct, identifiable class rather than buried in a generic `requirements.txt`. "Version ranges observed" is deliberately loose at L2: L3 tightens this to documented supply-chain inventory with structured fields, and L4 goes further to AI-BOM with pinned versions. SCA coverage verification means the team can answer "is LangChain being scanned?" with an affirmative pointing at a recent scan, not an assumption. At L2 the scanner does not yet need AI-specific vulnerability patterns — generic CVE coverage of the libraries is the bar.

**Evidence:**
- AI-component inventory (spreadsheet, wiki page, or CMDB section) listing model providers and foundation models, primary AI libraries with version ranges observed, and MCP servers in production
- Most recent SCA scan output showing the named AI libraries appearing with matched dependency records
- Quarterly coverage reconciliation note comparing inventory AI libraries against SCA coverage

---

### Level 3 — Defined

#### DEV-03.1 — Enterprise AI coding assistant configured to prevent code exposure

- **Deployment Types:** All
- **Manual/Automated:** Either
- **AICM Mapping:** CCC-01 (change management policy), CCC-03 (change management technology), TVM-02 (malware / malicious instructions protection)
- **External References:** GitHub Copilot Business/Enterprise documentation (code referencing, content exclusions, training opt-out); Cursor enterprise privacy mode; Claude Code organization settings; OWASP LLM03:2025 Supply Chain
- **Key Indicator Rationale:** Running an enterprise-tier AI coding tool with training/retention opt-out confirmed, content exclusions deployed for secrets and sensitive paths, and consumer-tier AI chat tools blocked for production-code workflows requires that a central function owns the tool configuration and that network/endpoint controls can enforce it. An organization with all three pieces present has moved past L2 "we published a list" into L3 "we configured the tool and enforced the boundary."

**Control Objective:** Production code is written only against enterprise-tier AI coding assistants with training and retention opt-out enabled and content exclusions covering secret-bearing paths. Consumer-tier AI chat tools are blocked on developer endpoints that handle production code, with a quarterly fresh-marker test confirming the block holds.

**Description:** This KPI is the dev-tool-usage L3 centerpiece. The quantified bar is at least 90% of active developer endpoints with an AI coding assistant installed run an enterprise-tier tool (GitHub Copilot Business/Enterprise, Cursor for Business, Claude Code with organization settings, or equivalent), allowing for the small residual of experimentation and new-hire onboarding latency without eroding the control. "Training/retention opt-out confirmed" means a screenshot of the tenant setting showing the opt-out, not an assertion. "Content exclusions" vary by tool — Copilot has content-exclusion rules, Cursor has privacy-mode and ignore-file configurations, Claude Code has organization-level and project-level settings. The test is that secret-bearing files (e.g., `.env`, `secrets/`, `credentials/`) do not get sent to the model provider. Blocking consumer-tier tools (ChatGPT free, claude.ai free, Gemini consumer) is the boundary piece: without it, an L3 "enterprise tool deployed" is undermined by a developer alt-tabbing to ChatGPT's free tier to paste code. Blocking here is usually done via CASB, egress proxy, or endpoint DLP; the specific mechanism is the organization's choice but the outcome — posts blocked or alerted — is the measurable. The quarterly fresh sentinel-marker re-test (new unique string each quarter) prevents the failure mode where an organization passes the L3 test once and then silently regresses when a content-exclusion rule, CASB policy, or proxy rule is later loosened or removed; each quarter's test must use a marker that did not appear in prior tests so a stale allowlist cannot mask the regression.

**Evidence:**
- Screenshots of enterprise-tenant configuration showing training/retention opt-out and content-exclusion rules
- Endpoint inventory or MDM/EDR query showing enterprise-tier AI coding assistant install count and proportion relative to developers with any AI coding tool installed
- CASB / egress proxy / endpoint DLP policy definitions blocking consumer-tier generative-AI chat endpoints for developer devices
- Quarterly test records (at least four in the trailing 12 months) each showing a distinct fresh sentinel marker posted through a consumer-tier interface and the observed block or alert

#### DEV-03.2 — Structured AI supply chain inventory with package proxy

- **Deployment Types:** All
- **Manual/Automated:** Either
- **AICM Mapping:** STA-08 (supply chain inventory), STA-16 (service bill of material), TVM-05 (external library vulnerabilities), TVM-08 (vulnerability prioritization)
- **External References:** CycloneDX ML-BOM schema; NIST SP 800-218 SSDF Task PO.1.3; OWASP LLM03:2025 Supply Chain
- **Key Indicator Rationale:** A structured inventory covering AI providers, foundation models, AI libraries (with version pinning discipline), and MCP servers — where AI libraries install through an approved internal repository proxy rather than directly from public registries — is the L3 "defined process" signal. An L2 organization has a list but not the proxy, not pinned versions, and not MCP servers inside the inventory.

**Control Objective:** The AI-component inventory uses structured fields per component class with pinned versions. AI libraries reach production builds only through an organization-managed package proxy (e.g. Artifactory, Nexus), so direct public-registry installs are prevented, and open or third-party models carry an integrity and safe-format record before first production use.

**Description:** This is the supply-chain-breadth L3 centerpiece and the defined-process formalization of DEV-02.2. Structured fields replace free-text entries: models (name/version/provider/deployment type); AI libraries (package, pinned version, source); MCP servers (name, version, source URL, capabilities granted). Pinning replaces ranges (no more `langchain>=0.1.0`). The proxy (Nexus, Artifactory, or equivalent) is where the enforcement lives: direct PyPI/npm installs are blocked at network or configuration level for any pipeline that produces a production build artifact, and at least 95% of AI-library installs in production-build pipelines over the trailing 30 days route through the proxy. The open-model integrity check requires SHA-256 verification and a SafeTensors (or equivalent) safe-format check recorded before first production use; this matches the SC-03 control-statement (SafeTensors, checksum, provenance) but at the program-level KPI this is about existence of the check record against the inventory entry, not per-deployment verification. Self-hosted model artifact signing and load-time verification is a separate stronger gate that belongs in MOD-04.1 — L3 here only requires the pre-use integrity record. MCP-server capability enumeration at L3 is light: the inventory shows what each server is configured to do; enforcement of least-privilege capability limits and runtime verification are APP and IAM concerns.

**Evidence:**
- Inventory export with structured fields per component class (models, libraries, MCP servers) covering all production AI applications
- Package-manager proxy configuration (`pip.conf`, `.npmrc`, Poetry source config) showing the proxy as the only configured source for production-build repositories
- 30-day install telemetry from the proxy showing route rate for AI-library installs >= 95% in production-build pipelines
- Sample of three open-model integrity records showing SafeTensors (or equivalent) format check and SHA-256 match against the published value, dated before the first production use of each model
- MCP-server inventory entries showing source URL, version, and declared capabilities

#### DEV-03.3 — AI security assessment in CI/CD for critical AI applications

- **Deployment Types:** All
- **Manual/Automated:** Automated
- **AICM Mapping:** CCC-02 (quality testing), CCC-04 (change authorization), TVM-05 (external library vulnerabilities)
- **External References:** OWASP LLM02:2025 Sensitive Information Disclosure; GitHub Copilot Autofix / security-review features; Snyk Code AI; CodeRabbit / Graphite AI code review; NIST SSDF
- **Key Indicator Rationale:** Routing AI-assisted and AI-generated code through a consistent CI security-review stage — ideally with an AI security agent integrated into the review — requires that the organization has identified which code paths are AI-assisted, integrated a security-review step into those pipelines, and operationalized the review against measurable outcomes. An L5 organization extends this to on-demand IDE-embedded review; L4 is consistent pipeline-stage review.

**Control Objective:** Critical AI applications (customer-facing or processing untrusted content) pass an automated AI security assessment in CI/CD covering AI-specific insecure patterns, AI-library vulnerabilities, and unsafe model formats. Tools include AI security agents and AI-aware SAST/SCA. Critical or High findings block merge unless a named approver logs an exception.

**Description:** This KPI closes the dev-tool-usage L4 loop: AI-generated code is higher-risk for insecure-pattern introduction than non-AI-generated code (well-documented across the 2024–2025 security-research literature), and AI-assisted review tools exist to catch the patterns automatically. The pattern set covers hard-coded credentials in AI-SDK calls, unsafe deserialization of model outputs, unauthenticated tool-calling, and insecure prompts-as-data handling in agent code. An AI security-review agent (GitHub Copilot Autofix, Snyk Code AI, CodeRabbit, or equivalent) is integrated as a required status check on production branches. The AI security agent integration is the L4-specific element — L3 would only require a generic SAST review stage. The trailing-90-day quantitative bar is zero Critical-finding bypasses and under 5% of merged PRs with High-finding bypass under documented exception. The bypass-logging discipline is what moves this from "we have a scanner" to "we have a control": an unlogged bypass erodes the signal. Scope is production branches only; feature-branch development doesn't need the gate. Application-layer runtime defenses (guardrails, system-prompt validation) are APP concerns; this is about the code review before the app ships. The boundary with DEV-05.1 is intentional: DEV-04.3 is the pipeline-stage gate (merge-blocking, fail-closed); DEV-05.1 is the IDE on-demand assessment (developer-invoked, shift-left). They serve different stages with different evidence and remain split through L5.

**Evidence:**
- Branch-protection configuration showing required AI security-review status check before merge to production branches
- AI security-review agent integration manifest (app installation, workflow definition, or named tool configuration)
- 90-day PR audit showing AI-review status-check results, bypass count, and bypass exception records
- Sample finding showing the review agent identified an insecure AI-SDK pattern that was remediated before merge
- Exception register showing named approver, rationale, and expiration for any High-severity bypasses

---

### Level 5 — Efficient

#### DEV-04.1 — AI security assessment expanded to all production \ applications

- **Deployment Types:** All
- **Manual/Automated:** Automated
- **AICM Mapping:** TVM-04 (vulnerability testing), TVM-05 (external library vulnerabilities), TVM-07 (vulnerability remediation schedule), TVM-08 (SDLC integration of vulnerability management), CCC-02 (quality testing), CCC-07 (detection of baseline deviation)
- **External References:** OWASP LLM03:2025 Supply Chain; OWASP LLM02:2025 Sensitive Information Disclosure (for AI-generated code patterns); Snyk AI code security; GitHub CodeQL AI-security queries; Protect AI / HiddenLayer model scanners; Picklescan for unsafe model formats
- **Key Indicator Rationale:** Running AI-specific SAST/SCA rules — insecure AI-SDK-usage detection, prompt-injection-prone code patterns, unsafe model-format scanning (pickle, .pt), AI-library-specific vulnerability patterns — with fail-closed pipeline enforcement requires a scanner suite capable of those checks, pipeline hooks wired to those scanners, and an organization that accepts the merge-blocking constraint. This is the L4 "AI-specific assessment capabilities" signal from the main grid.

**Control Objective:** All production AI applications, AI-component repositories, and repositories with AI-assisted commits pass generalized security assessments and AI-specific SAST/SCA and security-agent scanning covering insecure AI-SDK usage, prompt and tool-output handling, AI-library vulnerability patterns, and unsafe model formats (e.g. pickle, .pt). Critical and High findings block the build. Vendor-supplied unsigned models receive an ingest-time scan and integrity record before they are re-signed under MOD-04.1.

**Description:** This is the L4 dev-tool-thread-and-supply-chain-thread convergence: the scanning pattern covers both AI-assisted code produced by developers using Copilot/Cursor/Claude Code and AI-component code inside internal libraries and agent implementations. The AI-specific rule set beyond DEV-03.3 covers: AI-SDK usage (hard-coded keys, unsafe deserialization, dangerous tool-calling), insecure prompt/tool-output handling, AI-library vulnerability patterns, and model-format scanning blocking pickle and .pt/.pth (Picklescan, ModelScan, or equivalent). Including AI-assisted-commit repositories explicitly in scope (per Copilot/Cursor/Claude Code metadata, commit trailers, or equivalent repo-tagging mechanism) closes the gap where scanners run only over paths that look like "AI applications" by name while AI-assisted code authored elsewhere in the codebase escapes review — the AI-assist usage signal is the trigger, not the application label. The tooling landscape is still maturing — the KPI names categories of checks rather than specific products because the product set changes quarterly. Blocking pickle loads at CI prevents a whole class of backdoored-model supply-chain attacks. The MOD-04.1 re-signing handoff is intentionally split: DEV produces the ingest-time scan record (format, integrity, malware/scanner outputs) against the unsigned vendor artifact; MOD-04.1 owns the signing operation with that scan record as an input attestation, and the load-time verification gate. The trailing-90-day quantitative bar — zero Critical-shipping deployments, under 5% open High under named-approver exception with 90-day expiration — tracks the MOD-05.1 pattern and is the L4 gate-with-accountability, not yet the L5 never-bypassed posture.

**Evidence:**
- Scanner configuration showing AI-specific rule sets enabled (rule list or scanner-version-and-policy references)
- Repository-scope mapping showing scanner coverage extends to repositories with AI-assisted commits (commit-author or commit-trailer signals from Copilot/Cursor/Claude Code, or equivalent repo-tagging mechanism)
- Sample pipeline artifact showing an AI-specific finding blocking a build
- 90-day aggregate metric: number of production deployments, number of Critical AI-specific findings that shipped (target: zero), number of High findings under exception
- Sample exception record showing named approver, rationale, issuance date, and expiration within 90 days
- Model-format scan configuration (Picklescan, ModelScan, or equivalent) in the build pipeline, with a sample run showing a pickle-format artifact blocked or flagged
- Sample ingest-time scan and integrity record for a vendor-supplied unsigned model artifact subsequently re-signed under the MOD-04.1 path

#### DEV-04.2 — AI-BOM generated per release as authoritative inventory

- **Deployment Types:** All
- **Manual/Automated:** Automated
- **AICM Mapping:** STA-08 (supply chain inventory), STA-16 (service bill of material), TVM-05 (external library vulnerabilities)
- **External References:** CycloneDX ML-BOM specification; SPDX AI Profile; NTIA minimum elements for SBOM; EU AI Act documentation requirements; NIST SP 800-218 SSDF Task PO.1.3
- **Key Indicator Rationale:** Auto-generating a CycloneDX ML-BOM (or SPDX AI Profile) per release with authoritative coverage of models, AI libraries, MCP servers, and data sources, plus historical retention for incident-response lookback and vulnerability-feed correlation, requires CI/CD pipeline integration and a canonical storage location. An organization that can answer "which applications use LangChain 0.1.16?" from the AI-BOM in under an hour has the L4 posture.

**Control Objective:** Production AI applications produce an AI-BOM per release covering models, AI libraries, MCP servers, and RAG data sources. Recent releases are retained, the AI-BOM is reconciled against runtime to catch drift, and it serves as the authoritative AI-component inventory consumed by ORG and RSK.

**Description:** This is the supply-chain-breadth L4 centerpiece and the authoritative-ownership claim per theme13. CI/CD generates the AI-BOM per release in CycloneDX ML-BOM or SPDX AI Profile format — CycloneDX ML-BOM is the more mature format for AI components as of the model cutoff and is the recommended default; SPDX AI Profile is acceptable where an organization already has SPDX plumbing. Field coverage: models (name/version/provider/identifier/license/checksum), AI libraries (name/pinned version/source), MCP servers (name/version/source URL/capabilities), and RAG data sources. Trailing three releases retained, supporting incident-response lookback — when a LangChain CVE drops, the team can identify not only what's currently deployed but what was running at the time a suspected event occurred. The runtime-inventory reconciliation is the drift check: per-release plus monthly stratified-random sample across deployment tiers (portfolio-proportional, minimum 10/month), with quantitative bar of 100% sampled match on deployed release and 90% completeness against runtime versions. The per-release-AND-monthly-sampled cadence closes the once-per-audit gameability where an organization could pass a single coverage audit and let drift accumulate for 11 months — the per-release run forces reconciliation at every deploy event, and the monthly sample catches drift across long-lived deployments that don't release frequently. Stratified random sampling across deployment tiers prevents both the inverse failure modes: pure random sampling can miss high-risk tier-1 applications by chance in any given month, and pure tier-1-only sampling lets tier-2/3 drift go uncaught. 90% completeness on the runtime match accommodates minor dynamic dependencies while still catching shadow imports. The authoritative-ownership framing means other categories (ORG asset discovery, RSK provider assessment) reference the AI-BOM rather than maintaining parallel inventories.

**Evidence:**
- CI/CD pipeline configuration showing AI-BOM generation as a release stage
- Sample AI-BOM for a production application in CycloneDX ML-BOM or SPDX AI Profile format, validated against the schema
- Retention query showing at least the trailing three releases available for a sample of applications
- Per-release reconciliation log showing AI-BOM-vs-runtime match at deploy time for the trailing 90 days
- Monthly sampled reconciliation reports showing the stratified-random selection methodology, tier-proportional sample sizes, and match rates per month for the trailing 6 months
- Documentation or architecture diagram showing the AI-BOM as the authoritative source referenced by ORG asset discovery and RSK provider assessment

#### DEV-05.1 — Automated remediation suggestions for AI security findings

- **Deployment Types:** All
- **Manual/Automated:** Automated
- **AICM Mapping:** CCC-02 (quality testing), TVM-08 (SDLC integration of vulnerability management — pre-commit extension)
- **External References:** GitHub Copilot Autofix in-IDE; Snyk IDE plugin with AI code checks; Cursor and Claude Code agentic security capabilities; OWASP LLM03/LLM02 coverage during authoring
- **Key Indicator Rationale:** Providing developers with an on-demand AI security-assessment agent inside the IDE that can run against AI-generated or AI-assisted code before commit, with consistent behavior across multiple approved AI coding tools and with findings ingested into the same backend that holds pipeline-stage findings, is the L5 dev-tool posture described in the main grid ("Multiple AI development tools supported... On-demand agent-based security assessments available in IDE"). Organizations that deploy this consistently — and that track remediation of IDE findings through the same workflow as pipeline findings — have moved past pipeline-stage catching into shift-left authoring-time defense with a unified vulnerability-management surface.

**Control Objective:** AI security findings come with automated remediation suggestions (inline fix proposals, suggested patches) across the developer workflow at IDE, PR, and pipeline stages. Proposed fixes are tied to verifiable remediations, and developer acceptance rates are tracked to drive tooling improvement.

**Description:** This KPI is the L5 dev-tool thread. It goes beyond L4's pipeline-stage gate by moving security signal into the IDE before the code is committed. The capability is invokable before commit in every approved AI coding tool (Copilot, Cursor, Claude Code, or equivalent), running the DEV-04.1 rule set with inline findings. The 70% adoption threshold (developers on AI applications who invoked the in-IDE assessment in the trailing 90 days) allows for the residual of developers who don't touch AI-assisted code heavily. Three elements differentiate it from L4: cross-tool consistency, findings-backend ingestion, and unified remediation tracking. Cross-tool consistency (verified quarterly via a sample change set with known insecure patterns scanned through each approved tool) is the harder requirement — organizations that succeed here have either standardized on one tool (degenerate case: consistency is trivial) or invested in tool-agnostic security-assessment integrations (e.g., Snyk IDE, CodeQL IDE, or custom LSP-based integrations) that sit beneath whichever AI coding tool the developer has chosen. The unified remediation tracking is the L5-vs-L4 discriminator that an L4 organization cannot fake: an L4 setup might report IDE findings into the same backend at a display level but track remediation in a separate IDE-only workflow; L5 requires the remediation to be tracked through the same backend, with the same SLA discipline and the same ticket-closing behavior, as pipeline-found and human-found findings. Without that unified remediation, IDE-stage findings become a separate stream that can be quietly ignored; with it, leadership sees a single time-to-remediate metric across the lifecycle.

**Evidence:**
- Documentation or configuration listing the on-demand security-assessment capability for each approved AI coding tool
- IDE telemetry showing invocation counts aggregated per developer over 90 days with at least 70% developer reach
- Findings backend showing IDE-stage findings ingested alongside pipeline findings with tool-origin tagging
- Remediation-workflow record showing IDE-stage findings tracked through the same ticketing system, the same SLA, and the same closure workflow as pipeline-found and human-found findings — with a sample showing an IDE finding's full remediation lifecycle in the shared backend
- Quarterly cross-tool consistency test record: a sample change set injected with a known AI-specific insecure pattern (hard-coded AI-SDK key, unsafe deserialization) scanned through each approved tool's in-IDE assessment, with each reporting the finding

#### DEV-05.2 — Proactive AI supply chain vulnerability alerting

- **Deployment Types:** All
- **Manual/Automated:** Automated
- **AICM Mapping:** STA-08 (supply chain inventory), STA-16 (service bill of material), TVM-04 (detection updates), TVM-05 (external library vulnerabilities), TVM-09 (vulnerability management reporting), CCC-07 (detection of baseline deviation)
- **External References:** OWASP LLM03:2025 Supply Chain; GitHub Advisory Database; PyPI Advisory Database; LangChain security advisories; HuggingFace model-card change notifications; CycloneDX ML-BOM + VEX integration
- **Key Indicator Rationale:** Closing the loop from "new vulnerability published in an AI dependency" to "alert routed to the owning application team with AI-BOM-driven blast-radius list and triage SLA" within defined time thresholds requires automated feed ingestion across AI-specific advisory sources, AI-BOM-driven correlation, and an operational practice that meets the SLA. This is the L5 "supply chain monitoring alerts on new vulnerabilities in AI dependencies" posture.

**Control Objective:** New vulnerabilities in AI-BOM components auto-correlate against the AI-BOM to produce a blast-radius list routed to the named owning team, triaged against a defined SLA, so the time from public disclosure to owning-team action is bounded. Abandoned AI libraries are flagged for replacement before they become a latent supply-chain risk.

**Description:** This is the supply-chain L5 centerpiece and is the natural endpoint of the DEV-03.2 inventory → DEV-04.2 AI-BOM → DEV-05.2 live correlation chain. Feed coverage spans GitHub/PyPI/npm advisories, AI-library-maintainer advisories (LangChain, transformers, equivalents), HuggingFace model-card changes for open models, and CVE feeds for AI-serving components. Triage SLAs are Critical within 72 hours and High within 7 calendar days, measured over the trailing 6 months. The 1-hour detection-to-alert SLA is achievable because the inputs are feed-publish events, not human discoveries. The blast-radius correlation is the AI-BOM's biggest operational value: when the next PyTorch-style supply-chain compromise drops, the team pulls a list of affected applications in minutes rather than running a multi-week inventory scramble. The AI-BOM authoritative-ownership claim from DEV-04.2 is what makes this correlation tractable — the feed detection and the inventory are reading from the same source of truth. Abandoned-library detection (no 12-month upstream activity) runs quarterly with a replacement-candidate list per candidate; this is an often-missed L5 element: a library without upstream maintenance is a latent supply-chain risk even without an active CVE, and proactive replacement planning at L5 prevents that risk from maturing into an incident.

**Evidence:**
- Feed ingestion configuration covering the named AI advisory sources
- AI-BOM correlation query or service linking detected vulnerabilities to affected applications
- 6-month metric report showing detection-to-alert latency, triage SLA compliance (>= 95% Critical-72h and High-7d)
- Sample end-to-end record: an AI-library vulnerability detected, blast-radius list produced, owning team alerted, triage completed within SLA
- Quarterly abandoned-library report with replacement-candidate list and action status per candidate

---

---

## 11. Privacy, Compliance and Audit (CMP) <a id="11-privacy-compliance-and-audit"></a>

**Category description:** Verification that AI deployments meet legal, regulatory, and internal-policy obligations — data privacy regulations (GDPR, CCPA, sector-specific rules), AI-specific regulations (EU AI Act, state AI laws), internal AI safety/ethics policies authored in Governance, intellectual property and licensing obligations for models and training data, and audit evidence needed to demonstrate the above. Includes privacy impact assessments (PIAs), AI Consensus Assessment Initiative Questionnaires (AI-CAIQ) issued to customers, and compliance reporting. The category verifies that deployments conform to the policies Governance wrote; it does not write those policies. It executes compliance-flavored provider assessments where RSK executes risk-flavored ones.


---

### Level descriptors (reference — from AISMM main grid)

- **L1 Initial:** No AI-specific audit/compliance actions. AI deployments treated the same as any other application with no recognition of unique AI requirements. No tracking of AI model or training data licensing. No verification that AI deployments meet internal safety/ethics policies established in governance.
- **L2 Repeatable:** AI-specific compliance requirements identified (e.g., EU AI Act risk classifications, data privacy regulations, sector-specific AI rules). Assessment of AI deployments against internal policies performed when requested. Initial documentation of model and dataset licensing for some deployments. No systematic process to verify compliance with AI safety/ethics policies.
- **L3 Defined:** AI providers, models, and services assessed for regulatory compliance and approved for use with different data types (aligned with provider registry). Scheduled compliance assessments of AI deployments against internal AI governance policies (safety, bias, transparency requirements). Model and training data licensing tracked and verified for in-scope deployments. Manual compliance reporting includes AI-specific controls and standards (e.g., AICM, ISO 42001). Manual AI-CAIQ for some external facing apps. Privacy impact assessments conducted for AI deployments handling personal data.
- **L4 Capable:** Continuous assessment of AI deployments using automated tooling for technical compliance (guardrails coverage, data handling, access controls). Bias and fairness audits conducted for high-risk AI use cases per governance requirements. License compliance automated for models and major AI components. Compliance status integrated into AI deployment registry. Reporting partially automated with AI-specific (or enriched) compliance dashboards. AI-CAIQ automated for major external apps.
- **L5 Efficient:** Continuous compliance monitoring across AI deployments with automated evidence collection. Real-time verification of safety/ethics policy compliance integrated into deployment pipelines. Comprehensive license tracking automated. Compliance reporting fully automated with dashboards covering AI-specific regulations, internal policies, and industry frameworks. AI-CAIQ generation automated for external apps. Proactive monitoring for emerging AI regulatory requirements.

---

### Scope notes — category boundaries

**CMP / RSK.** RSK owns risk-flavored assessment of providers, models, and projects — risk ratings, treatment decisions, reassessment on change. CMP owns compliance-flavored assessment — which regulations apply, whether deployment evidence proves conformance, PIAs for personal-data use, AI-CAIQs issued to customers, and IP/licensing verification. The two assessments often run against the same provider registry entry; the question differs (is the risk acceptable, versus does this meet regulatory requirement X).

**CMP / GOV.** GOV authors internal policy — AI acceptable-use policy, safety/ethics framework, bias and transparency requirements, approval authority. CMP verifies deployments conform to those policies and produces the evidence trail. When a new deployment fails a CMP assessment against a GOV-authored policy, CMP records the finding; remediation or policy revision flows back through GOV.

**CMP / DAT.** DAT owns training-data classification, provenance, and access control as an operational control. CMP owns the licensing question that sits on top of that data — did this training set's license permit our use, is the attribution obligation being met, did we obtain the rights we claim to have. DAT tells you what the data is; CMP tells you whether you are allowed to use it for what you're doing.

**CMP / MOD.** MOD owns the model registry and the technical approval gate. CMP adds the compliance layer: whether the registered model's license permits the intended use case (e.g., commercial use, financial-services use, EU AI Act high-risk use), and whether the provider's terms have changed in ways that affect existing deployments. MOD says "this model is approved;" CMP says "this model is approved for these use cases under these regulatory obligations."

---

### Level 2 — Repeatable

#### CMP-02.1 — Regulatory applicability per AI deployment

- **Deployment Types:** All
- **Manual/Automated:** Manual
- **AICM Mapping:** GRC-07 (Information System Regulatory Mapping), A&A-04 (Requirements Compliance)
- **External References:** EU AI Act risk classification (prohibited / high-risk / limited-risk / minimal-risk); NIST AI RMF GOVERN-1.1; state AI laws (Colorado AI Act, NYC Local Law 144); sector rules (SR 11-7, HIPAA, GLBA, SEC Marketing Rule)
- **Key Indicator Rationale:** An organization cannot populate a per-deployment regulatory applicability matrix across the AI portfolio unless someone has read the regulatory landscape, talked to Legal and Compliance, and gotten product owners to tag their deployments. That is the L2 "requirements identified" bar; L1 organizations have no such matrix at all.

**Control Objective:** Major production AI deployments carry a current regulatory applicability record signed by Legal or Compliance, naming which AI rules, privacy regulations, sector rules, and internal policy scopes apply and which do not.

**Description:** This KPI makes "AI-specific compliance requirements identified" tangible. The artifact is one record per deployment, not a single org-wide matrix, because regulatory scope is deployment-specific (a customer-support bot serving EU users is in a different regulatory posture than an internal code-review assistant). Each record names the regulations evaluated — at minimum: EU AI Act risk tier for EU-user exposure, data-privacy regulations by geography, sector rules, and internal AI acceptable-use scope — carries a per-regulation applies/does-not-apply decision with reason, and is signed off by Legal or Compliance. The minimum regulatory coverage list is set rather than left to the product team because at L2 you cannot yet trust every deployment owner to know which rules matter; Legal or Compliance naming the list for the first pass is how the organization gets consistent scoping. For most enterprises, the EU AI Act item forces the high-risk / limited-risk classification decision that drives whether downstream L3 and L4 evidence obligations kick in at all. The 80% threshold (with non-expired meaning within the trailing 18 months) accepts that some freshly registered deployments will be in flight; L3 tightens this to 100% current coverage tied to scheduled reassessment.

**Evidence:**
- Per-deployment applicability records with the named regulations evaluated, applicability decision, and Legal or Compliance reviewer
- Count of production AI deployments in the inventory versus count with a non-expired applicability record (meeting the 80% threshold)
- Sample of five applicability records spanning at least one customer-facing deployment, one internal deployment, and one deployment with personal-data processing

#### CMP-02.2 — Model and dataset license inventory

- **Deployment Types:** All
- **Manual/Automated:** Manual
- **AICM Mapping:** GRC-07 (regulatory mapping — includes licensing/contractual obligations), MDS-12 (open model risk assessment — license item)
- **External References:** OWASP LLM03:2025 Supply Chain; HuggingFace license taxonomy; provider service terms (AWS Bedrock, Azure OpenAI, Anthropic, OpenAI, Google Vertex AI)
- **Key Indicator Rationale:** An organization that produces a per-production-deployment license inventory — naming the license type and permitted-use summary for each model and each fine-tune or training dataset the deployment depends on — has done the legwork of reading provider service terms and model-card licenses. L1 organizations don't have this artifact; L3 goes further by verifying intended-use fit against license terms.

**Control Objective:** Major production AI deployments name the licenses governing the model, any organization-owned fine-tuning or RAG data, and any external datasets or retrieval corpora the deployment depends on.

**Description:** At L2 the goal is to produce the inventory at all — the verification-of-fit step (does the license actually permit this use) is the L3 move. Each record names license type and permitted-use summary for three categories: the production model (foundation-model terms for PaaS/API consumption; open-model license for self-hosted or fine-tuned models), any fine-tuning or RAG training data owned by the organization, and any external datasets or retrieval corpora the deployment depends on. An explicit "not applicable" entry with reason counts toward completeness. The three-category split is deliberate: organizations routinely get the foundation-model license right (the provider service terms cover it) while missing training-data and RAG-corpus licenses where most of the real exposure lives. For frontier-model consumption via PaaS the record is short — one entry per model pointing to the provider's service terms and the organization's enterprise agreement; the difficult entries are fine-tuning inputs and RAG corpora assembled from mixed sources. The 75% threshold at L2 reflects that back-filling license records for deployments that predate the control takes months; L4 pushes this to automated tracking with full coverage.

**Evidence:**
- License inventory export showing deployments and the three license-category entries per deployment
- Sample of three license records covering different license archetypes (one foundation-model PaaS consumption, one open-model self-host or fine-tune, one RAG corpus)
- Count of production deployments with complete records (meeting the 75% threshold)

---

### Level 3 — Defined

#### CMP-03.1 — Scheduled compliance assessment against AI policies

- **Deployment Types:** All
- **Manual/Automated:** Manual
- **AICM Mapping:** A&A-02 (Independent Assessments), A&A-05 (Audit Management Process), GRC-09 (Acceptable Use of the AI Service — verification side)
- **External References:** ISO/IEC 42001 AI management system; NIST AI RMF MEASURE-1; EU AI Act Article 17 (quality management system for high-risk AI)
- **Key Indicator Rationale:** Running scheduled assessments against a named policy set — with assessment records, finding severities, and remediation tracking — requires a compliance function that has taken ownership of AI policy verification and can point to completed cycles. L2 organizations assess on request only; L3 is the scheduled, repeatable, finding-tracked state.

**Control Objective:** Production AI deployments are assessed on a scheduled cadence against the AI policies Governance has authored, with findings carrying named remediation owners and target dates or signed time-bound risk acceptance.

**Description:** This KPI is the central L3 compliance-verification move. It is the answer to the main-grid phrase "scheduled compliance assessments of AI deployments against internal AI governance policies." The cadence is annual for high-criticality deployments and every 24 months otherwise. Each assessment evaluates the GOV-authored AI policy set (acceptable-use, safety, bias and transparency, human-oversight) and produces per-policy-area findings (pass, partial, fail with severity), a named remediation owner, and target date. Scope verifies GOV policies against actual deployment behavior, not merely policy existence. The boundary with GOV is enforced by restricting scope to verification — GOV wrote the policy; CMP checks that the deployment conforms. The split between annual and biennial cadences accommodates portfolio size: a large enterprise with 200 AI deployments cannot assess every deployment every year, but the high-criticality subset (customer-facing, regulated, personal-data-handling per CMP-03.2) must be. The 90% on-cadence completion and 80% remediation/acceptance thresholds are what separate a defined compliance program from a policy binder.

**Evidence:**
- Assessment schedule showing deployments, assigned cadence, and last completed assessment date
- Sample of three assessment reports spanning high-criticality and medium-criticality deployments, showing per-policy-area findings and remediation owners
- Finding register with 12 months of findings, severity ratings, and remediation or risk-acceptance status
- Metric report showing trailing-12-month on-cadence completion (>=90%) and finding-closure/acceptance rate (>=80% for severity 1 and 2)

#### CMP-03.2 — AI privacy impact assessments for personal data

- **Deployment Types:** All
- **Manual/Automated:** Manual
- **AICM Mapping:** GRC-10 (AI Impact Assessment — PIA is the privacy slice)
- **External References:** GDPR Article 35 (Data Protection Impact Assessment); CCPA/CPRA risk assessment requirements; NIST Privacy Framework; ICO AI and data protection guidance
- **Key Indicator Rationale:** A completed and current PIA per personal-data AI deployment requires the privacy function to have taken ownership of the AI portfolio, a template tailored to AI-specific risks (training-data exposure, inference memorization, model outputs constituting personal data), and a reassessment trigger tied to deployment changes. L2 organizations may have PIAs for the broader application but not for AI-specific processing.

**Control Objective:** AI deployments that process personal data carry a current AI-specific privacy impact assessment before reaching production, with reassessment when the model, provider, geography, or processed data category changes.

**Description:** PIAs are mandatory under GDPR for high-risk processing — which most meaningful AI personal-data processing qualifies as — and are increasingly expected under US state laws. The PIA must be completed before deployment or, for pre-existing deployments, within the trailing 18 months, and applies to deployments flagged personal-data-processing per CMP-02.1. The PIA template covers AI-specific questions: training-data content and lawful basis, inference flow and retention, memorization risk, model output as personal data, data-subject rights mechanics, and GDPR Article 22 (or equivalent) disclosures. PIAs reassess on named triggers: new personal-data category, new geography, model or provider change, or new automated decision-making. The AI-specific question set is what distinguishes a real AI PIA from a generic application PIA: a general app's PIA rarely covers model memorization, training-data scrubbing, or the data-subject-rights mechanics against an LLM. The reassessment triggers are tied to events that realistically shift the privacy posture: swapping GPT-4 for Claude on the same app isn't a deployment redesign in engineering terms, but it is a change of processor and can change the privacy analysis. The 95% currency threshold accepts that a deployment in active change may lag briefly; coverage below 95% that persists across two consecutive quarters indicates the program is failing.

**Evidence:**
- List of production deployments flagged as personal-data-processing, with current-PIA status per deployment
- Sample of three AI PIAs showing the AI-specific question set is used
- PIA reassessment log showing triggers that fired and resulting PIA revisions in the trailing 12 months
- Depth-review sample: at least 5% of completed PIAs (or three, whichever is larger) reviewed for substantive content — answers reflect the specific deployment rather than universal template defaults — with reviewer sign-off and any depth-review findings tracked
- Metric report showing trailing-12-month currency (>=95%) for personal-data deployments

#### CMP-03.3 — License-fit verification and AI-CAIQ for external apps

- **Deployment Types:** All (AI-CAIQ applies where the deployment is externally facing or offered as a service)
- **Manual/Automated:** Manual
- **AICM Mapping:** GRC-07 (regulatory/contractual mapping), A&A-04 (Requirements Compliance)
- **External References:** CSA AI-CAIQ (Consensus Assessment Initiative Questionnaire for AI); CSA AICM v1.0.3; OWASP LLM03:2025; HuggingFace model-card license taxonomy; provider service terms
- **Key Indicator Rationale:** Moving from a license inventory (L2) to verified license-fit, plus producing at least one completed AI-CAIQ per externally-facing deployment on request, requires both legal-review workflow and customer-facing compliance communications. That combination is the L3 signal — license tracking is no longer shelfware and the organization is ready to answer external compliance questionnaires about its AI.

**Control Objective:** Legal verifies that licensed components fit how the organization uses them, and externally-facing AI deployments hold a current AI-CAIQ ready to share with customers on request.

**Description:** The AI-CAIQ is CSA's AI-specific customer-assurance questionnaire aligned with AICM. At L3 it is produced manually — one per externally-facing deployment — and refreshed on request or on material change. License-fit verification refreshes on license change (provider term updates or open-model changes via MOD-05.2) or at least every 18 months. 100% of deployments with GPL/AGPL or restrictive-commercial components carry Legal sign-off on the mitigation. The license-verification step builds on CMP-02.2: the L2 inventory tells you what licenses are in play; L3 verifies the fit between license terms and actual use (a model licensed for research but deployed in a customer product is the failure mode this KPI catches). The 18-month cadence allows the verification to ride along with scheduled compliance assessment cycles; the on-change trigger is important because provider terms change and the organization needs to catch regression. The 100% threshold on GPL/AGPL and restrictive-commercial components exists because any single such component can contaminate the broader deployment's license posture; a partial credit approach doesn't make sense here.

**Evidence:**
- Verified license-fit records per deployment, signed by Legal or designated compliance reviewer, with verification date
- AI-CAIQ register showing externally-facing deployments, AI-CAIQ completion date, and AI-CAIQ version
- List of deployments with GPL/AGPL or restrictive-commercial components and the Legal sign-off / mitigation record for each
- Metric report showing trailing-12-month AI-CAIQ currency (>=90%) for externally-facing deployments

---

### Level 4 — Capable

#### CMP-04.1 — Automated compliance evidence tied to deployment registry

- **Deployment Types:** All
- **Manual/Automated:** Automated
- **AICM Mapping:** A&A-05 (Audit Management Process — automated evidence collection), A&A-06 (Remediation tracking)
- **External References:** NIST AI RMF MEASURE-3; ISO/IEC 42001; AI-SPM product category (Wiz AI-SPM, Prisma AI-SPM, Orca, SentinelOne); cloud-native tooling (AWS Audit Manager, Azure Purview, GCP Assured Workloads)
- **Key Indicator Rationale:** Automated continuous evidence collection for a named set of technical compliance controls — guardrail coverage, personal-data handling, access controls — with results joined to the deployment registry and surfaced in a dashboard is not something an L3 program runs. It requires AI-SPM or a named equivalent (AWS Audit Manager, Azure Compliance Manager, or an in-house evidence pipeline) integrated with the deployment inventory and a set of machine-verifiable controls derived from the CMP-03.1 policy assessment. If you can produce the dashboard on demand, you are at L4.

**Control Objective:** Compliance evidence for AI deployments (guardrail coverage, personal-data handling, access controls, and model-registry conformance) collects automatically from source telemetry and binds to each entry in the AI deployment registry.

**Description:** This KPI operationalizes the main-grid phrase "continuous assessment of AI deployments using automated tooling for technical compliance." The pipeline collects across four control areas: guardrail-coverage presence; personal-data handling (DAT classification tags, retention, EU-user regional constraints); access controls for personal-data or regulated deployments; and MOD enforcement telemetry consumed for compliance impact (deviations from approved model+version per MOD-03.2 surfaced as findings). The dashboard surfaces failing controls each quarter, or a signed zero-failure justification from a named approver. The four control areas are chosen because each is machine-verifiable from telemetry the organization already collects: guardrail coverage from app configuration and telemetry sample, personal-data handling from DAT controls that DAT itself owns (DAT classification is the upstream input), access controls from IAM state, and model-registry conformance from MOD telemetry (the registry and enforcement live in MOD; CMP consumes the telemetry to produce compliance-flavored evidence rather than re-checking model conformance — that would duplicate MOD-03.2). CMP does not reimplement these controls; CMP pulls the evidence and binds it to the deployment registry so an auditor or compliance reviewer can see, per deployment, whether the technical controls are in place. The 7-day refresh is loose enough to accommodate nightly batch pipelines but tight enough that the evidence is not stale at quarterly review time. The 90% coverage threshold accommodates deployments in transition; falling below 90% indicates the pipeline is broken or coverage has drifted. The negative-case requirement (failures shown, or zero-failure approved with a name) exists because an always-green pipeline is the most common failure mode of automated compliance reporting — real portfolios produce findings, and a dashboard that never shows any indicates collection is broken or thresholds are toothless.

**Evidence:**
- Dashboard or registry view showing the four control areas per deployment with refresh timestamps
- Pipeline documentation showing data sources (AI-SPM, IAM telemetry, MOD invocation telemetry, app-security guardrail telemetry) and evidence bindings — DAT classification and MOD registry telemetry are upstream inputs
- 30-day refresh log showing 7-day-or-better refresh cadence
- Quarterly failing-controls report (count of failing controls surfaced per quarter) or signed zero-failure justification with named approver
- Gap report showing deployments below the control-area coverage target with remediation or exception records

#### CMP-04.2 — Bias and fairness audits for high-risk AI

- **Deployment Types:** All
- **Manual/Automated:** Either
- **AICM Mapping:** GRC-11 (Bias and Fairness Assessment)
- **External References:** NIST AI RMF MEASURE-2.11; EU AI Act Article 10 (data and data governance — bias examination for high-risk AI); NYC Local Law 144 (bias audit for automated employment decision tools); Colorado AI Act (algorithmic discrimination); NIST SP 1270 (Standards for Identifying and Managing Bias in AI); EEOC AI guidance
- **Key Indicator Rationale:** Running a documented bias and fairness audit within the trailing 12 months for every high-risk-classified deployment — with defined fairness metrics, protected-characteristic coverage, and finding-tracked outcomes — requires a bias-testing methodology, a named analytics or research function running the audits, and governance buy-in on what "high-risk" means. That combination is the L4 operational bar.

**Control Objective:** High-risk AI deployments (hiring triage, credit decisioning, and other use cases the AI Council has flagged) undergo a documented bias and fairness audit each year, with findings tracked to remediation or signed risk acceptance.

**Description:** This KPI narrows the bias-audit obligation to the portfolio subset where it matters. High-risk classification draws from EU AI Act Annex III, internal governance, or sector rules. Each audit covers disparate-impact analysis across governance-named protected characteristics, an outcome-fairness metric from the governance-defined set for the task, and a counterfactual or perturbation check on representative inputs. Findings are severity-rated and tracked to remediation or signed risk acceptance. Running formal bias audits on an internal code-review assistant is not a productive use of the compliance function; running them on a hiring-triage assistant or a credit-decision helper is. The high-risk classification ties back to EU AI Act Annex III categories (employment, credit, education, law enforcement, critical infrastructure), sector rules, and the organization's internal risk classification. The minimum metric set is deliberately plural — a single demographic-parity number can mislead — and the counterfactual/perturbation check catches cases where the aggregate metrics look fine but the behavior shifts on plausibly-varying inputs. The 95% currency and 80% finding-closure thresholds match CMP-03.1's framing. For financial-services organizations subject to SR 11-7 (Federal Reserve / OCC supervisory guidance on model risk management), the bias-audit cycle should integrate with — not run parallel to — the model-risk-management practice: audit findings, validation evidence, and ongoing monitoring feed the same governance body that signs off on model risk, and bias-audit owners coordinate with model-risk-management leads so a single finding does not produce two unreconciled records.

**Evidence:**
- List of production deployments classified high-risk with current bias-audit status
- Sample of two bias-audit reports spanning different high-risk use-case types (e.g., one hiring or HR deployment, one customer-decisioning deployment)
- Audit methodology document showing fairness metrics, protected-characteristic coverage, and counterfactual check definition
- Finding register showing severity, remediation or risk-acceptance status, and closure dates

#### CMP-04.3 — Automated license tracking and AI-CAIQ generation

- **Deployment Types:** All
- **Manual/Automated:** Automated
- **AICM Mapping:** A&A-05 (Audit Management Process), GRC-07 (regulatory mapping)
- **External References:** OWASP LLM03:2025 Supply Chain; SPDX license identifiers; AI-BOM (see DEV category); CSA AI-CAIQ
- **Key Indicator Rationale:** Automated license tracking joined to an AI-BOM, plus AI-CAIQ generation that pulls from the same evidence pipeline CMP-04.1 feeds, is the infrastructure that turns compliance communication from a manual quarterly exercise into a dashboard. An organization producing AI-CAIQs from an automated pipeline for its major externally-facing deployments has arrived at L4.

**Control Objective:** License tracking runs automatically off the AI-BOM with SPDX resolution, and AI-CAIQs for major externally-facing deployments generate from the same pipeline that feeds the compliance dashboard, with quarterly samples cross-checked against source evidence.

**Description:** Automated license tracking covers model, framework, and major library components resolved to SPDX licenses with changes flagged within 7 days; the remaining 5% of deployments fall back to CMP-03.3. The "major externally-facing" qualifier carries a quantitative floor — >10,000 external users/month, direct revenue, or customer-contractual SLA — to prevent the judgment hedge from quietly excluding deployments that should be in scope. AI-CAIQ generation pulls from pipeline evidence (CMP-04.1 technical compliance, CMP-04.2 bias audit, license state, CMP-03.2 PIA) and refreshes quarterly. Each quarter, at least 10% (or three) AI-CAIQs are sampled against the source evidence; discrepancies track as findings. Automating AI-CAIQ generation for every internal tool is not the right investment; automating it for the deployments customers actually ask about is. The license-tracking infrastructure depends on the AI-BOM that lives in DEV; CMP consumes that artifact rather than reinventing it. For the deployments that remain in manual AI-CAIQ mode (non-major externally-facing deployments, internal tools with occasional customer-assurance requests), CMP-03.3 still applies. The 7-day license-change detection threshold matches the MOD-05.2 provider-change SLA family — license changes are a kind of provider change and deserve the same response cadence. The 80% automated-AI-CAIQ threshold at L4 accepts that some major externally-facing deployments may still be in manual-AI-CAIQ mode during transition; L5 pushes this higher. The integrity-sampling requirement exists because pipeline-generated questionnaires can confidently lie at scale: a template that pulls from stale or wrong evidence sources will produce uniformly green AI-CAIQs that misrepresent the deployment's actual posture, and customers reading them have no easy way to detect the gap. Quarterly cross-checking against the source evidence is the corrective.

**Evidence:**
- Automated license-tracking dashboard showing SPDX-identified licenses per deployment with last-change-detection timestamps
- AI-BOM export (or the organization's named AI-BOM-equivalent artifact from DEV) showing license resolution coverage
- Sample pipeline-generated AI-CAIQ for one major externally-facing deployment showing the evidence pipeline it pulled from
- Quarterly AI-CAIQ integrity-sample log: list of sampled AI-CAIQs (>=10% or three, whichever is larger), reviewer name, evidence cross-check results, and any discrepancy findings with remediation status
- Metric report showing trailing-12-month automation coverage for major externally-facing deployments (>=80%)

---

### Level 5 — Efficient

#### CMP-05.1 — Pipeline-gated safety and ethics policy conformance

- **Deployment Types:** All
- **Manual/Automated:** Automated
- **AICM Mapping:** GRC-09 (Acceptable Use — verification side), GRC-11 (Bias and Fairness — pipeline integration), A&A-05 (Audit Management Process)
- **External References:** NIST AI RMF MANAGE-4; ISO/IEC 42001 Clause 8 (operation); EU AI Act Article 17 (quality management system); policy-as-code frameworks (OPA/Rego, Kyverno)
- **Key Indicator Rationale:** Blocking deployments that fail automated conformance checks against GOV-authored safety/ethics policies — and producing a 90-day audit that shows zero policy-violating deployments reached production without either a passing gate or an unexpired exception — requires policy-as-code, a pipeline that honors gate decisions, and deployment teams that have accepted the constraint. That is the L5 "real-time verification of safety/ethics policy compliance integrated into deployment pipelines" outcome.

**Control Objective:** AI deployment pipelines run an automated conformance gate against the safety and ethics policies Governance has authored, encoded as policy-as-code. A failing deployment does not ship without a time-boxed exception carrying a named approver.

**Description:** This KPI is the L5 translation of the main-grid phrase "real-time verification of safety/ethics policy compliance integrated into deployment pipelines." The conformance stage runs machine-verifiable checks derived from the GOV policy set: required guardrail for the risk tier, personal-data handling matching CMP-03.2, model identifier matching CMP-03.3, and bias/fairness gate per CMP-04.2. Exceptions require a named approver and expire within 90 days; standard exceptions cap at one renewal (180 days total); vendor-blocked exceptions extend only with executive risk committee approval and remain time-bound. The L5 metric is zero deployments reaching production without a passing gate or unexpired exception over a trailing 90-day window. It is the sibling to MOD-05.1 (model registry gate) and APP-05.x (application security gate) at the compliance layer. The conformance checks are implemented as policy-as-code (Rego under OPA, Kyverno, Cedar, or an in-house policy engine the organization names). The authorship boundary matters: GOV authors policy intent — what the organization commits to — and CMP encodes that policy intent into machine-checkable rules and owns the gate behavior. The translation step (intent to code) is CMP's; the underlying policy text and any change to it remain GOV's. APP, MOD, and DAT implement the enforcement points downstream that the gate inspects. This split also means that GOV policy depends on this KPI to gain teeth (no policy-as-code, no enforcement), and APP guardrail gates are an upstream input the gate inspects — note the cross-category dependencies on GOV's policy set and APP's guardrail gates as context rather than hard prerequisites. Exceptions are a relief valve for real operational constraints, not a shortcut around the gate; the renewal cap on standard exceptions prevents the exception register from becoming a permanent bypass list, and the vendor-blocked track exists to handle the legitimate case where a provider must ship a fix while still keeping the exception time-bound under named executive approval. Unexpired exception counts trending upward indicate the program has slipped back toward L4.

**Evidence:**
- Pipeline definition showing the compliance-conformance stage as a required gate
- Policy-as-code repository with version history showing derivation from GOV policies (commits link policy-intent change in GOV to corresponding rule change in code)
- 90-day audit of production deployments showing each maps to a passing gate run or an unexpired exception record
- Sample exception record with approver, rationale, expiration within 90 days, and renewal count (standard exceptions cap at 1 renewal / 180 days total; vendor-blocked exceptions show executive risk committee approval to extend)
- Trailing metric showing unexpired exception count over time, with breakdown by standard vs. vendor-blocked track

#### CMP-05.2 — Live compliance dashboard with automated evidence

- **Deployment Types:** All
- **Manual/Automated:** Automated
- **AICM Mapping:** A&A-05 (Audit Management Process), A&A-06 (Remediation), GRC-11 (Bias and Fairness Assessment — pipeline-produced evidence)
- **External References:** NIST AI RMF MANAGE-4; ISO/IEC 42001 Clause 9 (performance evaluation); AWS Audit Manager / Azure Compliance Manager / GCP Assured Workloads; AI-CAIQ automated generation
- **Key Indicator Rationale:** An organization that produces a continuous compliance dashboard covering AI-specific regulations, internal policies, and industry frameworks with automated evidence collection — plus automated AI-CAIQ generation for every externally-facing deployment — has taken the full L5 step into continuous compliance. The artifact is not a quarterly report; it is a live dashboard that a CISO or regulator can look at on any given day.

**Control Objective:** A live compliance dashboard, refreshed daily from source telemetry, shows AI conformance against regulation, internal policy, and an industry framework. AI-CAIQs for externally-facing deployments generate from the same pipeline, and scheduled compliance reports are produced from the dashboard.

**Description:** The three-framework minimum forces the dashboard to speak to the three audiences compliance actually reports to: regulators (one AI-specific regulation — EU AI Act, sector rule, state AI law), internal leadership (one GOV-authored internal policy set), and customers/auditors (one industry framework — AICM, ISO 42001, NIST AI RMF). Evidence collects daily and exports as a regulator-ready report. The dashboard surfaces failing controls each quarter, or a signed zero-failure justification. Automated AI-CAIQ generation refreshes monthly and is customer-retrievable via self-service or within one business day. Daily refresh is the minimum cadence — organizations with stricter obligations may refresh hourly or on change. The 100% AI-CAIQ automation threshold at L5 is the step up from L4's 80% for major deployments; at L5 the automated pipeline covers every externally-facing deployment. The 95% pipeline-produced threshold for scheduled reports is what distinguishes "we built a dashboard" from "the dashboard is the system of record for compliance reporting." An organization still assembling quarterly compliance reports by hand is not yet at L5, no matter how good the dashboard looks. The negative-case requirement (failing controls visible, or zero-failure approved with a name) sits on top of the dashboard for the same reason it appears in CMP-04.1: an always-green continuous compliance dashboard is the most common signal that the collection pipeline has broken or that thresholds have been tuned to never trip — both of which are worse than no dashboard at all because they manufacture confidence.

**Evidence:**
- Dashboard showing the three-framework coverage with daily-or-better refresh timestamps
- Regulator-ready report export for one recent compliance reporting cycle
- AI-CAIQ register showing 100% externally-facing deployment coverage with monthly refresh and customer-retrieval mechanism
- Quarterly failing-controls summary or signed zero-failure justification with named approver covering the dashboard's reporting period
- Metric report showing trailing-6-month pipeline-production rate for scheduled compliance reports (>=95%)

#### CMP-05.3 — Regulatory-change intelligence with cascading impact assessment

- **Deployment Types:** All
- **Manual/Automated:** Automated
- **AICM Mapping:** GRC-07 (regulatory mapping — change detection), GRC-08 (Special Interest Groups — industry tracking)
- **External References:** EU AI Act phased implementation (prohibited-practice dates, high-risk obligations phase-in through 2026-2027); US state AI law tracking (Colorado, California, Texas, Illinois); NIST AI RMF updates; sector-specific regulator guidance (SEC, FINRA, HHS, OCC)
- **Key Indicator Rationale:** Detecting AI regulatory change — proposed legislation, new guidance, amended existing rules — across the jurisdictions the organization operates in, and routing each detection to a tracked impact assessment within a defined SLA, requires a regulatory-intelligence pipeline, a named owner, and Legal/Compliance engagement. Shipping 95% on-SLA over 6 months is the L5 signal that emerging-requirements monitoring is a durable program.

**Control Objective:** An automated regulatory-intelligence feed catches AI rule changes across the jurisdictions the organization operates in, routes each one to a tracked impact assessment, and cascades material findings into applicability records, scheduled assessments, and pipeline gates within defined SLAs.

**Description:** This KPI operationalizes "proactive monitoring for emerging AI regulatory requirements" from the main grid. The feed covers jurisdictions named in CMP-02.1 applicability records: EU AI Act, US federal AI guidance, US state AI laws, sector regulator guidance, and relevant international rules. Each detection opens a tracked item within 5 business days routed to Legal, Compliance, and affected deployment owners. Material detections complete impact assessment within 30 business days and cascade into CMP-02.1, CMP-03.1, and CMP-05.1 updates as applicable. The feed is a mix of regulatory-intelligence vendor subscriptions (e.g., OneTrust, Navex, LexisNexis, Bloomberg Law), law-firm alerting, CSA and sector-association updates, and direct regulator-feed monitoring where available. The 5-business-day routing threshold accommodates the reality that regulatory-intelligence pipelines run on business days, not wall-clock hours. The 30-business-day impact-assessment threshold matches typical Legal-review cycles for material regulatory change. The cascade into CMP-02.1, CMP-03.1, and CMP-05.1 is what distinguishes a real regulatory-intelligence program from a newsletter subscription: when the EU AI Act enforcement date for general-purpose AI obligations hits, the organization's applicability records, compliance assessments, and pipeline gates update to reflect the new state.

**Evidence:**
- Regulatory-intelligence feed configuration and coverage list (jurisdictions, regulator sources, vendor feeds)
- 6-month detection log with routing timestamps and impact-assessment status
- Sample impact assessment showing cascade into CMP-02.1, CMP-03.1, or CMP-05.1 artifacts
- Metric report showing trailing-6-month SLA compliance (>=95%)

---

---

## 12. Incident Response (IR) <a id="12-incident-response"></a>

**Category description:** Detecting, responding to, and recovering from security incidents involving AI systems, including AI-specific attack types (prompt injection, data exfiltration, model abuse, unauthorized AI usage, compromised agent credentials, tool misuse, agent hijacking, MCP attacks, memory manipulation) and AI-system failures. Covers AI-aware response playbooks, responder training, threat intelligence integration, SOAR automation, forensics and telemetry capture, and regulator/partner notification workflows for AI incidents. Detection infrastructure and rule quality live in Security Monitoring (MON); this category owns what happens once an alert fires.


---

### Level descriptors (reference — from AISMM main grid)

- **L1 Initial:** No AI-specific incident response capabilities. AI deployments treated the same as any other application incident. No AI-specific telemetry collection (prompt logs, model activity). IR team lacks awareness of AI-specific attack types. Incidents involving AI systems are handled ad hoc without AI-specific procedures or expertise.
- **L2 Repeatable:** Incident response team designated for AI incidents with basic manual processes. Initial AI-specific telemetry collection in place for some deployments (prompt/response logs). Major AI attack categories documented (prompt injection, data leakage, model abuse) but no formal detection. Cloud and application IR processes extended to cover AI deployments. Basic AI incident documentation.
- **L3 Defined:** Initial AI-specific playbooks (prompt injection, data exfiltration, model abuse, unauthorized usage, compromised agent credentials, tool misuse, agent hijacking). IR team trained on AI-specific threats and response procedures. Input/output monitoring in place for high-risk AI deployments. Responders have read access to AI deployment configurations, logs, and telemetry. AI incidents categorized and tracked separately from general application incidents.
- **L4 Capable:** Threat intelligence for AI systems integrated into program. Input/output security telemetry tools (guardrails, prompt injection detection) deployed for production AI systems. AI security alerts integrated with SIEM for correlation and tracking. Agentic threat detection (tool abuse, prompt injection, anomalous delegation) via log analysis. Memory manipulation playbook coverage added to the AI-specific playbook set. Response automation available for common AI incidents via SOAR integration. Responders can escalate to administrative access for AI system containment.
- **L5 Efficient:** Runtime AI security monitoring with behavioral analysis detects anomalous activity (unusual tool calls, unexpected data access patterns). Automated response for agentic AI threats (agent hijacking, MCP attacks, memory manipulation) — distinguished from L3/L4 by the *automation* of detection and containment, not by first awareness of these threats. Comprehensive telemetry capture (prompts, responses, tool executions, context state). ChatOps or workflow automation engages AI/development teams for rapid incident validation. Detection rules continuously refined based on emerging AI attack patterns and threat intelligence.

---

### Scope note — IR / MON / CMP boundaries

Incident Response KPIs address what the organization does once an AI-related event is identified: playbooks, responder skill and access, threat-intel feeds that shape response, SOAR automations, containment and forensics patterns tuned to AI deployments, and regulator/partner notification workflows. Detection infrastructure — prompt/response logging pipelines, guardrail-violation logs shipping to SIEM, agent-action log correlation rules, detection-rule coverage for AI attack patterns — lives in Security Monitoring (MON). Regulatory notification *obligations* (EU AI Act Article 73 serious incident notification, SEC Item 1.05, state AI laws) are scoped in Privacy/Compliance/Audit (CMP); the workflow that runs the notification — named timelines, named approvers, evidence preserved against forensic need — lives here in IR. The frontier/foundation bias matters: for PaaS and API/SaaS deployments many "incidents" are provider-side changes (a model regression, a guardrail bypass disclosure, a provider outage), and IR playbooks need to cover that pattern alongside self-hosted compromise scenarios.

---

### Level 2 — Repeatable

#### IR-02.1 — Named AI incident response team with AI addendum

- **Deployment Types:** All
- **Manual/Automated:** Manual
- **AICM Mapping:** SEF-01 (Security Incident Management Policy), SEF-03 (Incident Response Plans), SEF-08 (Points of Contact Maintenance), SEF-09 (Incident Response — AI incident categories and severity)
- **External References:** NIST SP 800-61r3 (Incident Response Recommendations), NIST AI RMF MANAGE-4, MITRE ATLAS
- **Key Indicator Rationale:** A named AI incident response team with a written IR plan addendum that recognizes AI-specific attack categories and records severity criteria, roles, communication paths, and at least one exercise is a byproduct of an organization having moved past "any incident, same plan." It takes a security leader, an AI/ML or app-platform lead, and a legal/privacy stakeholder to agree on the addendum and run the exercise. An L1 program has none of that.

**Control Objective:** A named IR team with on-call rotation owns AI incidents under a written AI addendum to the enterprise IR plan. The addendum covers AI-specific attack categories, severity criteria, and provider escalation contacts, and has been exercised in an AI-specific tabletop within the trailing 12 months.

**Description:** This KPI is the L2 foundation for Incident Response. The AI addendum to the enterprise IR plan covers at minimum prompt injection, data leakage, model abuse/unauthorized use, and AI service outage; states severity criteria and escalation thresholds; names internal and AI-provider points of contact; and includes at least one regulator-notification workflow artifact (template plus escalation runbook) per applicable regulatory regime. The tabletop within the trailing 12 months exercises at least one named AI-specific attack category, with findings recorded. "Named team" can be the existing SOC/IR function with a documented extension of scope, not a separate headcount — what matters is that an on-call rotation exists and includes someone who can read AI telemetry and reach the AI platform owners. The addendum is short and practical at L2: one or two pages per attack category describing the recognition signal, who to call, what evidence to preserve, and which provider support or status page to consult. Points of contact include the enterprise AI provider accounts — AWS/Azure/GCP enterprise support, Anthropic/OpenAI/Google enterprise escalation, plus any contracted AI-specific incident-response retainer — because provider-side incidents (a Bedrock model regression, an OpenAI outage, a disclosed guardrail bypass) are a common L2 reality. Regulator-notification *obligation* — what counts as a serious incident, which regimes apply, what the deadline is — is owned by Privacy/Compliance/Audit (CMP); IR owns the *workflow* that runs when the obligation triggers, which is why the KPI requires at least one workflow artifact (template plus escalation runbook reference) per applicable regime, not just a list of regulator contact names. The tabletop exercise proves the plan has been walked through with the named responders rather than living only on paper, and the AI-specific scenario requirement prevents an organization from claiming credit for running a generic ransomware tabletop and calling it AI-relevant.

**Evidence:**
- Named IR team roster with on-call rotation including AI-literate primary/secondary responders
- AI addendum to the IR plan covering the stated attack categories, severity criteria, escalation thresholds, and points of contact
- Points-of-contact list with AI provider support/escalation channels, recorded last-updated date within the trailing 12 months
- Regulator-notification workflow artifact (notification template plus escalation runbook reference) for each AI-applicable regulatory regime in scope
- Tabletop exercise record (agenda, participants, AI-specific scenario tied to a named attack category, findings/action items) within the trailing 12 months

#### IR-02.2 — Baseline AI telemetry preserved for forensic review

- **Deployment Types:** All
- **Manual/Automated:** Either
- **AICM Mapping:** SEF-06 (Event Triage Processes), SEF-09 (Incident Response)
- **External References:** NIST SP 800-86 (Guide to Integrating Forensic Techniques into IR), OWASP LLM02:2025 Sensitive Information Disclosure, OWASP LLM06:2025 Excessive Agency
- **Key Indicator Rationale:** Having prompt, response, and invocation-metadata telemetry preserved with a defined retention window for the enterprise's priority AI deployments, with responders able to pull it on request, is the evidence that an AI incident can be investigated beyond "the app stopped working." An L1 organization cannot reconstruct what a model or agent did; an L2 organization can, for its priority deployments, even if coverage is not yet portfolio-wide.

**Control Objective:** Major AI deployments (customer-facing, regulated, or agentic with tool access) capture prompts, responses, identities, and tool invocations with retention long enough to investigate, and responders can pull the telemetry on demand without filing a new access request.

**Description:** Priority AI deployments include customer-facing surfaces, regulated-use-case deployments, and any agentic deployment with tool/MCP access. Telemetry is retained at least 30 days and covers prompt text (or a documented privacy-preserving substitute), model response, invoking identity, model/version identifier, session/correlation ID, and tool/MCP invocation records where applicable. Coverage reaches at least 75% of deployments flagged priority in the AI inventory, with dated reconciliation. Responders pull telemetry within 1 business day of request. This is the L2 precursor to the L3 playbook expansion. Without telemetry an AI playbook cannot do anything useful. The priority-deployment scope is deliberate: at L2 the organization does not yet have portfolio-wide AI telemetry — that emerges in MON at L3/L4 — but it has the priority subset covered and responders know how to get at it. Privacy-preserving substitutes for raw prompt text are allowed (hashing, redaction of recognized PII, or structured metadata capture) where raw capture would violate privacy counsel guidance; what matters is that a responder can reconstruct what happened. The 1-business-day pull SLA is the control that proves this is not dark data: responders have documented access and a retrieval path, not just the dashboards existing somewhere. Retention coordinates with the detection telemetry MON collects and the audit/compliance retention CMP owns; the IR lens is "long enough to investigate."

**Evidence:**
- Telemetry configuration showing captured fields (prompt, response, identity, model/version, session ID, tool calls) per covered deployment
- Retention policy naming the 30-days-or-greater window and the storage location
- Reconciliation showing priority-deployment coverage at or above 75%, with the list of covered and uncovered deployments and dated within the trailing 90 days
- Responder access runbook and a sample pull (ticket, query log) completed within 1 business day of request

---

### Level 3 — Defined

#### IR-03.1 — AI-Specific response playbooks for named attack categories

- **Deployment Types:** All
- **Manual/Automated:** Manual
- **AICM Mapping:** SEF-03 (Incident Response Plans), SEF-06 (Event Triage Processes), SEF-09 (Incident Response)
- **External References:** OWASP LLM01:2025 Prompt Injection, OWASP LLM02:2025 Sensitive Information Disclosure, OWASP LLM06:2025 Excessive Agency, OWASP LLM08:2025 Vector and Embedding Weaknesses, OWASP Agentic AI Threats (T3 Tool Misuse, T6 Agent Hijacking, T15 Memory Poisoning), MITRE ATLAS, NIST AI RMF MANAGE-4
- **Key Indicator Rationale:** Producing named, tested playbooks across the specific AI attack categories the main grid calls out — each with a detection trigger, an owner, containment and eradication steps tailored to deployment type, and evidence-preservation instructions — requires central coordination among IR, the AI platform team, and legal. A program that has this in place has moved from "we have a plan" (L2) to "we have practiced procedures for the named attack types" (L3).

**Control Objective:** Written playbooks cover the named AI attack categories (prompt injection, data exfiltration, model abuse, compromised agent credentials, tool/MCP misuse, agent hijacking) with containment steps that branch by deployment type, and a working majority have been exercised within the trailing 12 months.

**Description:** Playbook scope covers prompt injection (direct/indirect), data exfiltration, model abuse and unauthorized use (including shadow AI), compromised AI service or agent credentials, tool/MCP misuse, and agent hijacking. Each playbook names trigger, primary responder, deployment-type-specific containment (self-hosted, PaaS, API/SaaS), eradication/recovery, evidence preservation referencing IR-02.2, and provider-coordination steps. At least 50% have been exercised in the trailing 12 months, including at least three of the four most-likely-real categories (prompt injection, data exfiltration, compromised agent credentials, tool/MCP misuse). Owner and last-reviewed date are recorded per playbook, no older than 12 months. The category list is the main-grid list expanded to include agent hijacking, which is detectable through behavioral deviation at the L3 manual-response level — the L5 reservation of agent hijacking would be too strict, since an L3 organization can recognize and respond manually to agent hijacking even before it has the runtime behavioral detection that makes the response automatable. Playbooks at L3 are still mostly manual procedures — SOAR automation is L4. Deployment-type branches matter because containment of a prompt-injection incident on a Bedrock-hosted Claude deployment (rotate credentials, disable the deployment's IAM principal, pull logs from CloudTrail and Bedrock invocation logs, notify AWS enterprise support if the injection vector implicates the provider) is materially different from containment on a self-hosted Llama deployment (pull the pod, preserve model weights and serving logs, isolate the node, capture prompt history from the serving tier). Tool/MCP misuse playbooks specifically reference the agentic deployment pattern: an agent with tool access executed an action outside the expected envelope (unexpected data deletion, unexpected outbound call, unexpected credential use), and the playbook has to name both the agent-side response (revoke the agent's tool scope via IAM) and the blast-radius review on what the tool touched. The 50% exercise threshold at L3 is intentionally partial, but the floor on which categories must appear in the exercised set prevents the gameable shortcut of exercising only the easiest categories (e.g., a model-abuse paper drill plus an unauthorized-usage tabletop and calling it L3-complete). Full exercise coverage is an L4/L5 expectation.

**Evidence:**
- Playbook set with named playbooks covering each of the seven listed attack categories, each naming trigger, owner, containment/eradication/recovery steps per deployment type where applicable, evidence-preservation steps, and provider-coordination steps
- Exercise records (tabletop notes, exercise reports, or IR post-incident reviews) linked to at least half of the playbooks within the trailing 12 months, including coverage of at least three of the four most-likely-real categories (prompt injection, data exfiltration, compromised agent credentials, tool/MCP misuse)
- Playbook review metadata showing owner and last-reviewed date within the trailing 12 months per playbook

#### IR-03.2 — Responder training and Pre-provisioned read access

- **Deployment Types:** All
- **Manual/Automated:** Manual
- **AICM Mapping:** SEF-01 (Security Incident Management Policy), SEF-06 (Event Triage Processes)
- **External References:** NIST AI RMF GOVERN-3, MITRE ATLAS, OWASP Top 10 for LLM Applications (2025)
- **Key Indicator Rationale:** A primary-responder roster that has completed named AI-specific IR training within the trailing 12 months and holds pre-provisioned read access to AI deployment configurations, telemetry, and provider consoles cannot be produced by an L2 organization. At L3 the responder not only has playbooks but can read AI-specific signals and has the access needed to execute the playbook without waiting for just-in-time provisioning.

**Control Objective:** Primary AI responders have completed AI-specific IR training within the trailing 12 months (proven by knowledge check or simulated exercise) and hold pre-provisioned read access to telemetry, deployment configs, and provider consoles sufficient to run a playbook without just-in-time provisioning.

**Description:** Each primary AI responder has completed documented AI IR training within the trailing 12 months covering the IR-03.1 attack taxonomy, reading AI telemetry (prompt/response, tool invocation, agent session traces), and provider-coordination, evidenced by knowledge check or simulated exercise (not video completion). Each holds pre-provisioned read access to deployment configs and system prompts (where permitted), telemetry stores (IR-02.2), the AI inventory, and cloud provider AI service consoles. Training and entitlements are reviewed annually. Two halves: training and access, both with proof-of-use. At L3 both matter because an untrained responder with access still misreads AI telemetry, and a trained responder without access still loses the first hour of an incident to JIT provisioning. Training at L3 does not require a formal certification — it can be an internal module, a recorded walk-through, or a third-party course — but the completion record alone (a video watched, a course launched) is not enough; the responder must demonstrate working knowledge through a knowledge check or a simulated incident exercise. Read access is scoped conservatively: read-only is the L3 bar, administrative/containment access (kill the deployment, revoke the agent's IAM role, rotate provider API keys) is an L4 escalation. System prompts are sometimes protected as IP or not readily exposed by the app platform; where that is the case the responder still gets read access to the deployment's configuration and metadata, with system-prompt review available via a documented escalation path. The exercise-in-anger requirement closes a common L3 failure mode: organizations provision JIT-friendly access on paper, but if no one has ever actually pulled telemetry through that path, the path probably broke six months ago. Access entitlements themselves are an IAM concern (provisioned through the organization's identity platform); the IR KPI here is that responders are in fact provisioned and the path actually works, rather than having to request at incident time.

**Evidence:**
- Responder roster with training completion dates, training curriculum reference, and scope of access per responder
- Training materials or vendor references documenting the curriculum (attack taxonomy, telemetry reading, provider coordination)
- Knowledge-check or simulated-exercise record per responder demonstrating working knowledge (not a video-completion log)
- Entitlement report from the identity platform showing primary responders hold read access to the named AI systems (deployment config/inventory, telemetry stores, cloud AI service consoles)
- Per-responder evidence (real incident ticket or drill record) that the pre-provisioned access path was exercised at least once within the trailing 12 months
- Annual review record of training completion and access

---

### Level 4 — Capable

#### IR-04.1 — AI threat intelligence operationalized into detection and response

- **Deployment Types:** All
- **Manual/Automated:** Either
- **AICM Mapping:** SEF-03 (Incident Response Plans), SEF-06 (Event Triage Processes), SEF-09 (Incident Response)
- **External References:** MITRE ATLAS, OWASP Top 10 for LLM Applications (2025), OWASP Agentic AI Threats, NIST AI RMF MANAGE-4.1
- **Key Indicator Rationale:** Running a named AI threat intelligence program — subscribed sources, cadence, a documented path from intel item to detection rule or playbook update, and an audit trail of items actually actioned — is not a one-time dashboard. It requires an analyst owner, a feedback loop into MON and IR, and enough operational discipline that intel lands as real changes. An L3 program consumes intel passively; an L4 program operationalizes it.

**Control Objective:** A named AI threat intelligence function turns provider advisories, AI-BOM CVEs, and external research into detection-rule updates, playbook revisions, or owner tickets, with action-required items closing on a defined SLA.

**Description:** The intel function covers provider security bulletins for every provider in the inventory, at least two AI-security external sources (MITRE ATLAS, OWASP LLM/Agentic, ISAC/ISAO, vendor research), and CVE feeds filtered to AI-BOM components, reviewed weekly. Over the trailing 6 months, 80%+ of "action-required" items have a documented outcome within 10 business days (MON rule update, IR-03.1 update, owner ticket, or risk acceptance). "Action-required" is auto-flagged as: AI-BOM CVE with CVSS >=7.0 AND exploitable-in-production, provider advisory affecting a production deployment, or new technique mapping to an IR-03.1 category. The 80% / 10-business-day SLA is the "operationalized" signal. Without it, threat intelligence is a reading list. The inline auto-flag definition prevents analyst gameability: if "action-required" were analyst-judged, an organization could meet 80% by simply classifying fewer items as action-required when SLA pressure rises. By tying the flag to AI-BOM CVE+CVSS+exploitability (which depends on DEV maintaining the AI-BOM), provider advisories, and technique-to-playbook mapping, the criterion is auditable rather than negotiable. Source coverage is scoped to what actually matters for an AI program: provider security bulletins for the PaaS/API/SaaS providers the enterprise depends on, plus structured AI threat research, plus CVE feeds filtered to the AI components in the organization's AI-BOM (which DEV maintains — this KPI assumes a working AI-BOM exists in DEV). The detection-rule handoff is explicitly to MON: IR flags what to detect, MON owns the rule quality and pipeline. Playbook updates and owner tickets are IR-internal. The boundary with MON is clean: if the intel item drives a new detection rule, MON owns the rule's implementation and tuning, and IR owns the playbook for what to do when the rule fires.

**Evidence:**
- Threat-intel source list with named sources per category (provider advisories, AI research, CVE feeds), review cadence (no less frequent than weekly), and named analyst owner
- Intel ticket/log showing items triaged over 6 months with action-required flag and outcome link (rule update, playbook revision, owner ticket, risk acceptance)
- Sample of three action-required items showing documented outcome within 10 business days each
- Compliance report showing at least 80% of action-required items met the 10-business-day SLA over the trailing 6 months

#### IR-04.2 — SOAR automation for common AI containment actions

- **Deployment Types:** All (automations differ by deployment type; coverage required across the types present in the inventory)
- **Manual/Automated:** Automated
- **AICM Mapping:** SEF-06 (Event Triage Processes), SEF-09 (Incident Response — automated response where applicable)
- **External References:** NIST AI RMF MANAGE-4, OWASP LLM06:2025 Excessive Agency, OWASP Agentic AI Threats (T3 Tool Misuse, T6 Agent Hijacking)
- **Key Indicator Rationale:** Moving the most common AI containment actions from "responder opens three consoles" to "SOAR playbook executes with audit trail" requires SOAR tooling, tested runbooks wired into real provider and serving APIs, and an automation-rollback pattern. Organizations that can show named, tested SOAR playbooks for the most common AI containment actions with measurable MTTR reduction have crossed into L4 operational automation.

**Control Objective:** SOAR playbooks execute common AI containment actions (disabling deployments, revoking agent tool scope, rotating provider keys, rolling back models or memory) across each deployment type in scope, with audited invocation and a measurable MTTR improvement over the manual baseline.

**Description:** Coverage requires at least four of: disable a deployment (IAM revoke or pod stop), revoke agent tool/MCP scope, rotate API keys, block a model+identity tuple at egress/CASB, quarantine a session/user, roll back model version (MOD-03.2), or roll back agent memory — across every deployment type. IR-03.1 adds memory manipulation as an eighth category (prompt-injection-persisted-to-memory, cross-session leakage, adversarial writes). Each action emits an audit log. At least one was invoked via real incident or drill in the trailing 6 months. Four of seven is the L4 bar; five or more starts approaching L5. The memory-rollback action and the memory-manipulation playbook category are the L4 expansion of the playbook set above the L3 seven categories — at L4 the organization is wide enough in agentic deployments to need a documented memory-manipulation response, even though *automated* detection of memory manipulation remains an L5 capability (IR-05.1). The deployment-type-coverage requirement is deliberate — an organization with a big self-hosted footprint cannot claim L4 by automating only the Bedrock cases. Each action has an audit trail (the SOAR platform's native execution record is fine), because automated containment without attribution is an unacceptable IR artifact. MTTR comparison was previously hedged as "measurably lower"; the 30%-magnitude floor against the manual-only L3 baseline gives the metric teeth without locking in an unrealistic absolute number. The baseline is established at the L3 transition because that is when MTTR for AI categories first becomes computable (L2 doesn't have the categorized incident records). Rollback to a prior approved model version specifically ties to MOD-03.2; the IR KPI here is that the rollback is automatable from the incident side, not just available as a deployment action.

**Evidence:**
- SOAR playbook list showing named automations for at least four of the listed containment actions across the deployment types in scope
- Memory-manipulation playbook in the IR-03.1 playbook set with manual-response procedures for prompt-injection-persisted-to-memory, cross-session memory leakage, and adversarial memory writes
- Playbook definition/export showing the provider-API calls or serving-tier actions the automation executes
- Audit log samples showing invoker identity, target, time, and outcome for at least two distinct automated actions within the trailing 6 months
- MTTR comparison (AI-incident-category automated vs. L3 manual-only baseline) showing at least 30% reduction, with the computation method and the baseline definition documented

#### IR-04.3 — Break-Glass administrative containment access

- **Deployment Types:** All
- **Manual/Automated:** Either
- **AICM Mapping:** SEF-06 (Event Triage Processes), SEF-09 (Incident Response)
- **External References:** NIST SP 800-61r3, NIST AI RMF GOVERN-3, OWASP LLM06:2025 Excessive Agency
- **Key Indicator Rationale:** A break-glass administrative access path to AI systems, pre-provisioned, access-audited, time-bounded, and exercised in the trailing 12 months, closes the containment gap that read-only L3 access left open. An organization can only produce this artifact when IAM, the AI platform owners, and IR have jointly engineered a trusted-path for the "actually stop this" action — an L4-level integration.

**Control Objective:** Responders can stop, isolate, or revoke AI deployments through a time-bounded, audited break-glass path with secondary approval or post-use review, exercised end-to-end across the deployment types in scope within the trailing 12 months.

**Description:** The break-glass path covers at minimum: disabling invocation IAM principals for PaaS/API deployments, revoking agent tool/MCP scopes, rotating provider API keys, and stopping/isolating self-hosted serving workloads. Access auto-expires within 8 hours, is automatically audited (invoker, time, target, justification ticket), and requires secondary approval or immediate post-use review by a named approver. At L3 responders had read access; at L4 they have a tested path to the "contain now" actions. The break-glass pattern intentionally mirrors cloud-provider break-glass conventions: time-bounded session, automatic audit, secondary approval or post-use review — not standing administrative access. This is both a security and a blast-radius control, because standing admin access to agents and AI deployments is itself an incident waiting to happen. The exercise record matters because break-glass paths that aren't exercised don't work when needed; the L4 signal is that the organization has tested this in the last 12 months and knows it works. This KPI depends on IAM L4 (which owns the time-bounded identity model and the audit-and-approval workflow that make the break-glass primitive sound) — cross-category note, not a hard gate. The IR lens is that the responder can actually reach admin-equivalent control when the playbook says to.

**Evidence:**
- Break-glass access configuration showing time-bound credentials, audit logging, and the named approver/review workflow, per deployment type in scope
- Audit log sample of a break-glass activation (real or drill) showing invoker, time, target, justification ticket reference
- Exercise record within the trailing 12 months attesting end-to-end function of the break-glass path across the deployment types in scope
- Post-use review record for the exercised activation

---

### Level 5 — Efficient

#### IR-05.1 — Automated response for agentic threat patterns

- **Deployment Types:** All agentic deployments (agents with tool access, MCP connections, or persistent memory); not applicable where no agentic deployments exist
- **Manual/Automated:** Automated
- **AICM Mapping:** SEF-06 (Event Triage Processes), SEF-09 (Incident Response — automated response)
- **External References:** OWASP Agentic AI Threats (T3 Tool Misuse, T6 Agent Hijacking, T12 Identity Spoofing, T15 Memory Poisoning), CSA MAESTRO framework, NIST AI RMF MANAGE-4
- **Key Indicator Rationale:** Automated response specifically targeted at agentic threat patterns — the ones the main grid lists at L5 (agent hijacking, MCP attacks, memory manipulation) — requires behavioral detection pattern feeding into SOAR, containment actions that understand agent-and-tool identity boundaries, and validated true-positive rates high enough to make automation safe. An L4 organization automates generic containment; an L5 organization automates agentic-specific response with a documented accuracy record.

**Control Objective:** Production agentic deployments trigger automated containment for agentic-specific threats (agent hijacking, MCP compromise, memory manipulation) with a documented true-positive rate at or above 80% over the trailing 90 days and human-in-the-loop review on each invocation.

**Description:** Patterns covered are at least three of: agent hijacking, MCP compromise/unauthorized invocation, agent identity spoofing or delegation-chain anomaly, memory/context-store manipulation, cross-tenant data access via agent tools, anomalous tool-call sequences. Each has a defined containment action (tool-scope revocation, session termination, memory rollback, principal suspension). The 80% TPR floor is computed over the trailing 90 days against at least five qualifying alerts per deployment per quarter, or documented quiet-period justification. HITL review runs within the playbook SLA. This KPI is the L5 version of IR-04.2 with two moves: the threat patterns are specifically agentic (not generic AI containment), and the automation has an accuracy floor. The L5 differentiator from L3/L4 is the *automation* of detection and containment for these patterns — at L3 the playbooks for agent hijacking exist and are run manually; at L4 some containment actions are automated and a memory-manipulation playbook is added; at L5 the detection and response are automated with an accuracy floor. Agent hijacking is the behavioral-deviation case where an agent's actions no longer match its policy, and the automated containment is usually suspension of the agent's tool scope. MCP attacks span MCP-server compromise and unauthorized MCP tool invocation; the containment is disconnection of the MCP server or revocation of the MCP tool binding. Memory manipulation covers the case where the agent's persistent memory has been tampered with (prompt-injection-persisted-to-memory, cross-session memory leakage, or outright adversarial memory injection) and containment is rollback to a known-good snapshot plus quarantine of the suspected memory writes. The 80% true-positive floor over 90 days prevents "automate and forget", and the volume floor (five qualifying alerts per deployment per quarter) prevents the trivial gameable case of declaring 100% TPR on zero alerts; quiet-period justification with a named approver covers legitimate low-volume deployments without granting a free pass. HITL review is required because agentic containment touches production: the action executes automatically but a human validates the decision within a defined window. This KPI depends on L4 runtime behavioral detection in MON and L4 agentic identity modeling in IAM (cross-category note — not a hard gate); the IR ownership is of the response side.

**Evidence:**
- Automated-response playbook catalog showing at least three of the listed agentic threat patterns with containment action, detection source, and HITL review SLA per playbook
- True-positive rate report per playbook over the trailing 90 days, computed and documented (analyst-dispositioned alerts with TPR >= 80%) and showing alert volume per deployment per quarter at or above the five-alert floor, OR documented quiet-period justification per low-volume deployment with named approver
- Invocation log over 90 days showing real or drill invocation per covered pattern, with HITL review completion within the defined SLA
- Agent identity/tool-scope model reference showing the containment action targets the correct identity primitive

#### IR-05.2 — Tamper-Evident agentic telemetry for forensic reconstruction

- **Deployment Types:** All agentic and high-risk deployments; baseline AI deployments covered under IR-02.2. Organizations with a SaaS-dominant footprint document the provider-telemetry boundary (what the provider exposes vs. what is org-controlled) and demonstrate forensic completeness for the org-controlled components only.
- **Manual/Automated:** Automated
- **AICM Mapping:** SEF-06 (Event Triage Processes), SEF-09 (Incident Response)
- **External References:** NIST SP 800-86, OWASP Agentic AI Threats, NIST AI RMF MANAGE-4
- **Key Indicator Rationale:** Producing a full forensic reconstruction of an agent's session — prompts, responses, tool calls and returns, context-state snapshots, delegation chain, and memory reads/writes — on demand, with integrity controls, is impossible without a production-grade telemetry stack, defined schema, and retention. The drill requirement (one forensic reconstruction per quarter) is the operational signal that the stack works under real conditions.

**Control Objective:** Production agentic deployments preserve tamper-evident, indexed telemetry (prompts, tool I/O, context checkpoints, delegation, memory events) and responders can reconstruct any agent session on demand, validated by a quarterly forensic drill.

**Description:** Telemetry captures prompts, responses, tool I/O, context-state snapshots at checkpoints (session start, pre/post tool-call, session end), delegation-chain records, and memory read/write events for org-controlled components. It is written tamper-evident (WORM/append-only/object-lock), retained at least 180 days, and indexed by session ID, agent identity, user identity, time window, and tool. SaaS-dominant orgs document the provider-telemetry boundary per deployment and demonstrate forensic completeness for org-controlled components. The quarterly drill runs against a live session and is archived. IR-02.2 established baseline telemetry; this KPI extends to the agentic-forensic level the main grid asks for at L5. The checkpoint list is deliberate: a prompt-response log alone does not let a responder reconstruct what an agent did if the agent called three tools and mutated memory in between, so the KPI names the checkpoints where state must be captured. Tamper evidence matters because adversarial scenarios at this level (memory manipulation, session replay, agent impersonation) require the forensic record be trusted. The provider-telemetry boundary is the realistic ceiling for pure-API/SaaS-heavy organizations: they cannot produce tamper-evident forensic telemetry for components they do not own (the provider's model serving, the provider-managed agent runtime, the provider's tool gateway), so the requirement is to document the boundary explicitly and demonstrate forensic completeness for the org-controlled components — typically the orchestration layer, the tool implementations the org runs, the data the org provides as context, and the org-managed memory store — with provider-side reconstruction available only to the extent the provider's contracted telemetry exports allow. The quarterly drill prevents the telemetry from rotting — schema drift, silent logging failures, and shard-level retention bugs all show up only when someone actually runs a reconstruction. The 4-hour drill completion target is the L5 operational signal: the organization can reconstruct an agentic session on demand within half a business day. Baseline (non-agentic) deployments remain covered under IR-02.2; this KPI adds the agentic overlay.

**Evidence:**
- Telemetry schema covering prompts, responses, tool I/O, context-state checkpoints, delegation chain, and memory read/write events for org-controlled components
- Storage configuration showing tamper-evident / WORM / object-lock properties and 180-day retention for agentic telemetry
- Index definition showing session ID, agent identity, user identity, time window, and tool as queryable
- For SaaS-dominant deployments: provider-telemetry boundary document per deployment naming provider-owned vs. org-controlled components and the contracted provider telemetry/logging exports relied on for provider-side reconstruction
- Quarterly reconstruction drill records over the trailing 12 months showing timeline output, 4-hour completion, and archival location

#### IR-05.3 — ChatOps engagement and Detection-rule feedback loop

- **Deployment Types:** All
- **Manual/Automated:** Automated
- **AICM Mapping:** SEF-04 (Incident Response Testing), SEF-05 (Incident Response Metrics), SEF-06 (Event Triage Processes)
- **External References:** NIST AI RMF MANAGE-4.1, OWASP Top 10 for LLM Applications (2025), MITRE ATLAS
- **Key Indicator Rationale:** A ChatOps-or-workflow channel that automatically engages the owning AI/development team within minutes of an incident, plus a documented feedback loop where closed incidents produce detection-rule refinements tracked to implementation, together demand a cross-team workflow plumbing and measurement discipline that only an L5 program sustains. The metric combination — engagement time + feedback-loop closure rate — proves the process actually runs.

**Control Objective:** ChatOps or workflow automation pulls the owning AI or development team into qualifying incidents within 10 minutes, and closed sev-2+ incidents produce a detection-rule, playbook, or intel change with at least 80% implemented within 30 days and reported quarterly to AI governance leadership.

**Description:** Engagement runs via Slack/Teams with pinned context, ticket auto-assignment, or on-call page above a defined severity, measured over the trailing 90 days. Every closed sev-2+ incident produces a post-incident review identifying at least one detection-rule, playbook, or threat-intel change; over the trailing 6 months, 80%+ are implemented and verified with MON or IR within 30 days. Two linked mechanisms: the front end (fast engagement of the owning team) and the back end (closed incidents drive detection and playbook refinement). The front end matters because AI incidents often require domain context the SOC does not have — the deployment owner knows whether a prompt-injection alert is against a customer-facing surface or an internal eval harness, and that context collapses triage time. The back end is what makes the L5 "continuously refined based on emerging attack patterns" claim measurable: the organization can point to the rate at which post-incident findings land as real changes. The 80% / 30-day threshold is deliberate: lower and the loop isn't closing; higher and the organization is either small enough to move fast or gaming the measurement. Quarterly leadership reporting elevates this above SOC-internal metric-watching. The MON handoff is explicit — detection-rule changes execute in MON, not IR — but IR owns the hand-off record and the closure tracking.

**Evidence:**
- ChatOps/workflow automation definition routing qualifying AI incidents to the owning team within 10 minutes
- 90-day alert-to-engagement-time report showing at least 90% compliance with the 10-minute SLA
- Post-incident review template requiring at least one detection/playbook/intel change per sev-2+ incident
- 6-month report showing identified changes and implementation status, with at least 80% implemented within 30 days
- Quarterly report to AI governance leadership on feedback-loop implementation rate

---

---

## Glossary <a id="glossary"></a>

| Term | Definition | Used In |
|---|---|---|
| A2A | Agent-to-Agent protocol. An emerging standard for direct communication and authentication between AI agents, enabling multi-agent workflows. | IAM, App Security |
| AI-BOM | AI Bill of Materials. An inventory of AI-specific components in a deployment, including models (with versions), training data sources, agents, MCP servers/tools, libraries, and dependencies. Analogous to a software BOM (SBOM) but extended for AI. | AI Dev & Supply Chain, Organization Management |
| AI-CAIQ | AI Consensus Assessment Initiative Questionnaire. A CSA assessment tool for evaluating AI service providers, extending the CAIQ framework to AI-specific concerns. | Risk & Provider Assessment |
| AI-SPM | AI Security Posture Management. A category of tooling that provides automated discovery, configuration assessment, and security monitoring of AI services across cloud environments. Analogous to CSPM for cloud infrastructure. | Organization Management, Security Monitoring |
| AICM | AI Controls Matrix. A CSA framework of security control objectives for AI systems. The AISMM aligns with and is additive to the AICM. | Governance, Compliance & Audit |
| AISMM Categories | The twelve AISMM category prefixes used in KPI IDs and cross-references: GOV (Governance), ORG (Organization Management), IAM (Identity and Access Management), MON (Security Monitoring), INF (Infrastructure Security and Resilience), MOD (Model Security), APP (Application Security), DAT (Data Security), RSK (Risk and Provider Assessment), DEV (AI Supported Development and Supply Chain Security), CMP (Privacy, Compliance and Audit), IR (Incident Response). | All categories |
| AWS SCP | AWS Service Control Policy. An AWS Organizations feature that sets permission guardrails across AWS accounts. Used in the AISMM as an example of cloud provider organizational policy controls for restricting AI services. Equivalent capabilities exist in other providers (Azure Policy, GCP Organization Policy). | Organization Management |
| Azure Policy | A Microsoft Azure governance service for enforcing organizational standards across Azure resources. Referenced as an example of cloud provider policy controls equivalent to AWS SCPs. | Organization Management |
| CASB | Cloud Access Security Broker. A security tool that enforces enterprise security policies on cloud services and SaaS application usage, including AI services. Used to discover unsanctioned AI usage, enforce egress allowlists, and apply DLP to cloud-bound AI traffic. | ORG, MON |
| CNAPP | Cloud-Native Application Protection Platform. An integrated security platform combining CSPM, CWPP, and other cloud security capabilities. Referenced in the context of extending cloud security coverage to AI workloads. | Infrastructure Security |
| CoSAI | Coalition for Secure AI (under OASIS). An industry group developing secure AI frameworks and tooling guidance. The AISMM aligns with CoSAI/SAIF guidance. | Governance |
| CSPM | Cloud Security Posture Management. Tooling for continuous assessment of cloud infrastructure security configurations. Referenced alongside AI-SPM for extending coverage to AI services. | Infrastructure Security, Organization Management |
| DPoP | Demonstrating Proof of Possession. An OAuth extension that binds tokens to a client's cryptographic key, preventing stolen token replay. Relevant to securing agent-to-service authentication. | IAM |
| EDR | Endpoint Detection and Response. A category of host-level runtime security tooling (CrowdStrike Falcon, SentinelOne, Microsoft Defender for Endpoint) that detects and prevents process-level threats. Applied to AI inference, training, orchestrator, and agent-framework hosts at AISMM L4. | Infrastructure Security |
| GCP Organization Policy | Google Cloud organizational policy constraints. Used to enforce restrictions on GCP resources including Vertex AI services. Referenced as an example equivalent to AWS SCPs. | Organization Management |
| Guardrails | Runtime security controls that monitor, filter, or constrain AI model inputs and outputs. Includes prompt injection detection, content filtering, sensitive data masking, and output validation. May be implemented as middleware, proxy layers, or integrated platform features. | App Security, Model Security |
| HITL | Human-in-the-Loop. A pattern where human review or approval is required before an AI system executes certain actions, particularly for high-risk or irreversible operations. | App Security, Governance |
| IaC | Infrastructure as Code. The practice of managing infrastructure through machine-readable configuration files rather than manual processes. Referenced for provisioning AI workloads with security configurations. | Infrastructure Security |
| IdP | Identity Provider. A service that manages digital identities and authentication. Referenced in the context of extending IdP capabilities to manage AI agent identities. | IAM |
| ISO 42001 | An international standard for AI management systems, providing requirements for establishing, implementing, and improving AI governance within organizations. | Governance, Compliance & Audit |
| MCP | Model Context Protocol. A protocol that enables AI models and agents to interact with external tools, data sources, and services. MCP servers expose capabilities that agents can invoke, creating security considerations around authorization, tool access, and data exposure. | IAM, App Security, Security Monitoring, AI Dev & Supply Chain |
| MTTR | Mean Time to Remediate (or Resolve). The average time from incident or finding identification to closure. Used in AISMM as an SLA metric for incident response and detection rule action outcomes. | Incident Response, Security Monitoring |
| NHI | Non-Human Identity. Digital identities used by AI agents, services, and automated systems (as distinct from human user identities). Includes service accounts, managed identities, API keys, and agent-specific credentials. | IAM |
| OASIS | Organization for the Advancement of Structured Information Standards. An open standards body. Hosts CoSAI (Coalition for Secure AI). | Governance |
| OBO | On-Behalf-Of. An authorization pattern where an AI agent acts with delegated authority from a user, with tokens reflecting both the user's identity and the agent's identity. Limits agent actions to the scope the user has authorized. | IAM |
| OPA | Open Policy Agent. A general-purpose policy engine that evaluates declarative policies (written in Rego) against structured input. Used in AISMM as an example of a centralized policy engine for tool-allowlist enforcement and configuration policy evaluation outside the agent's prompt-controllable context. | App Security, IAM, Organization Management |
| OWASP | Open Worldwide Application Security Project. Produces AI security guidance including the LLM Top 10, Agentic Top 10, and AI Maturity Assessment (AIMA). The AISMM is designed to be additive to OWASP work. | App Security, Model Security |
| Permission-Aware Retrieval | A RAG security pattern where retrieval queries are filtered based on the requesting user's access permissions to source documents, preventing unauthorized access to data through AI-mediated queries. | Data Security |
| Prompt Injection | An attack where malicious input is crafted to override an AI model's system prompt or instructions, causing unintended behavior. Includes direct injection (user input) and indirect injection (via data sources like RAG documents). | App Security, Security Monitoring, Incident Response |
| RAG | Retrieval-Augmented Generation. An architecture pattern where AI models retrieve relevant documents or data from external sources (typically vector databases) to augment their responses. Creates security considerations around data access, poisoning, and permission enforcement. | Data Security, App Security |
| RPO | Recovery Point Objective. The maximum acceptable data loss measured in time, expressing how far back a restore can recover. Used in AISMM resilience KPIs for AI-specific stateful components (vector stores, fine-tuned model artifacts, agent configurations). | Infrastructure Security |
| RTO | Recovery Time Objective. The maximum acceptable downtime to restore a service after disruption. Used in AISMM resilience KPIs alongside RPO. | Infrastructure Security |
| SAIF | Secure AI Framework (Google). A conceptual framework for securing AI systems. Referenced alongside CoSAI as industry guidance the AISMM aligns with. | Governance |
| SAST | Static Application Security Testing. Automated analysis of source code to find security vulnerabilities. Referenced in the context of scanning AI-generated code. | AI Dev & Supply Chain |
| SCA | Software Composition Analysis. Automated identification and assessment of open-source and third-party components. Referenced for tracking AI library vulnerabilities. | AI Dev & Supply Chain |
| SIEM | Security Information and Event Management. A platform for centralized log aggregation, correlation, and security alerting. Referenced for integrating AI-specific telemetry into enterprise security operations. | Security Monitoring, Incident Response |
| SOAR | Security Orchestration, Automation and Response. A platform for automating incident response workflows. Referenced for integrating AI security alerts into automated response playbooks. | Incident Response, Security Monitoring |
| SOC | Security Operations Center. The enterprise team and tooling responsible for monitoring, detection, and incident response. AISMM AI security alerts are integrated into the SOC at L4 and feed into AI-specific incident response workflows. | Security Monitoring, Incident Response |
| SPIFFE | Secure Production Identity Framework for Everyone. An open standard for issuing cryptographic workload identities (SPIFFE Verifiable Identity Documents, or SVIDs) to non-human services. Used in AISMM for self-hosted agent and workload identity at L4-L5. | IAM, Infrastructure Security |
| SPIRE | SPIFFE Runtime Environment. The reference open-source implementation of the SPIFFE specification, providing the platform that issues and rotates SVIDs. Often paired with SPIFFE in AISMM evidence as the practical mechanism for workload identity attestation. | IAM, Infrastructure Security |
| SSO | Single Sign-On. An authentication scheme allowing users to access multiple systems with one set of credentials. Referenced as a baseline control for enterprise AI platform access. | IAM, Organization Management |
| Transitive Trust | A trust relationship where Agent A trusts Agent B, and Agent B trusts Agent C, creating an implicit trust chain from A to C. In AI systems, this creates risks of privilege escalation and confused deputy attacks across multi-agent workflows. | IAM |
| TTL | Time-to-Live. In the IAM context, the duration a credential or token remains valid before expiring. Short/low TTLs for agent credentials reduce the window of exposure if compromised. | IAM |
| Vector Database | A specialized database optimized for storing and querying high-dimensional vector embeddings. Used in RAG architectures to store document embeddings for semantic search. Security considerations include access control, tenant isolation, and data poisoning. | Data Security |
| WAF | Web Application Firewall. A perimeter security control that inspects HTTP/HTTPS traffic to web-facing applications. Used in AISMM as an example of an enterprise ingress control for externally-reachable AI inference endpoints. | Infrastructure Security |
| Zero Trust | A security architecture that requires continuous verification of every user, device, and connection regardless of network location. Referenced for AI infrastructure security at higher maturity levels. | Infrastructure Security, IAM |

---

© 2026 Cloud Security Alliance. All rights reserved.
