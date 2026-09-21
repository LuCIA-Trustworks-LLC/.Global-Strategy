# LuCIA Trustworks Project Manifest

**Document ID:** LTW-PM-001  
**Version:** 0.1-draft  
**Status:** Proposed baseline; not yet approved  
**Owner:** LuCIA Trustworks, LLC.  
**Executive authority:** Takuya Miyazaki  
**Projects:** AegisAI Project; SeaAI Project  
**Review cycle:** On material scope, authority, provider, regulatory, or architecture change

## 1. Purpose

This manifest is the single high-level record of project identity, authority, scope, operating boundaries, external relationships, and current delivery status. It reduces reliance on chat history, individual memory, vendor dashboards, and undocumented configuration.

This document governs descriptions of the project. Detailed policies, contracts, controls, and evidence remain in their approved records.

## 2. Governing principle

> Providers propose. The Kernel authorizes. The Runtime executes.

The AegisAI Kernel is the authoritative decision boundary for policy, identity, authorization, execution decisions, audit, and evidence. A provider, model, platform, protocol, application, cloud service, or execution environment does not become an authority merely by being connected or paid for.

Authority order:

1. Applicable law and signed company obligations
2. Human executive authority of LuCIA Trustworks, LLC.
3. Approved governance and security policies
4. Repository rules, CODEOWNERS, and protected-branch checks
5. Authorized human or AI work instructions
6. Provider, tool, and model suggestions

## 3. Project identity and objectives

### AegisAI Project

A vendor-independent authorization and execution governance architecture for AI-assisted work. Its intended components are:

- **Kernel:** policy, authorization, identity, audit, and evidence
- **Runtime (Soll):** execution only after valid authorization
- **Adapters:** bounded provider integrations
- **MCP or other protocols:** transport and capability interfaces, never authority
- **Canonical configuration:** approved, versioned project configuration

The current design baseline includes an Authorization Grant lifecycle:

`ISSUED -> CLAIMED -> CONSUMED`

with the terminal alternatives:

`ISSUED -> REVOKED` and `ISSUED -> EXPIRED`.

The grant is single-use, bound to its authorized subject and action, expiration-aware, revocation-aware, replay-resistant, auditable, evidenced, and fail-closed.

### SeaAI Project

SeaAI is a related project under the same human and organizational authority. Its independent technical scope, data classification, infrastructure, and release criteria require separate approval before production use.

## 4. Human and organizational accountability

- LuCIA Trustworks, LLC. retains final organizational responsibility.
- Takuya Miyazaki is the named executive authority for the current baseline.
- Material security, authorization, legal, privacy, production, credential, publication, and incident decisions require explicit human approval.
- Employees, contractors, collaborators, and AI workers receive only the minimum access required for their role.
- No AI system may approve its own work, expand its own authority, or bypass a human gate.

## 5. Soll / Codex operating relationship

Soll is the project-facing runtime role used for planning, analysis, drafting, validation, and authorized execution. Where Soll is provided through an OpenAI Codex or ChatGPT service:

- OpenAI is a provider, not the project authority.
- A subscription grants the account holder access to provider capabilities; it does not transfer ownership of an independent worker or create an employment relationship.
- Access to GitHub, Apple, Microsoft, local devices, or other systems exists only through explicitly connected and authorized capabilities.
- No background access, persistent device control, independent purchasing authority, or authority outside the active approved scope is assumed.
- Durable project knowledge must be recorded in approved files, evidence records, or repositories rather than relying only on conversation history.
- Soll must state intended changes, affected resources, risk, validation, and rollback before material execution.

The project owner does not need to research provider internals to assign ordinary work. The required input is the objective, authority boundary, sensitive-data boundary, and any approval condition. Soll is responsible for identifying missing technical details and stopping when authority or evidence is insufficient.

## 6. Approved and candidate environments

| Environment | Intended role | Current status | Authority boundary |
| --- | --- | --- | --- |
| GitHub organization and repositories | Governance, source, review, evidence pointers | Active; controls incomplete | Repository permissions and approved human review |
| macOS and Xcode | Apple-platform development and local validation | Inventory required | Local device owner and approved project configuration |
| Xcode Cloud / App Store Connect | Apple CI/CD and distribution | Candidate; workflow activation not established by login alone | Apple roles, explicit workflow configuration, human release approval |
| Microsoft 365 / Office Business | Organizational documents and participant productivity | Licensed for designated participants | Named accounts, tenant policy, least privilege, no credential sharing |
| Local Ollama models | Optional local inference | Historical presence reported; inventory pending | Local authorization, model license, data classification, resource budget |
| External AI providers | Proposal and assistance capabilities | Provider-specific | No provider becomes Kernel authority |

No environment is production-approved merely because software, SDKs, frameworks, models, credentials, or subscriptions are present.

## 7. Framework and government-relationship statement

The project references NIST CSF 2.0, NIST SP 800-207, and NIST AI RMF as risk-management and architecture sources. It may also map relevant CSA and ISO materials.

Use of a public NIST framework does **not** by itself establish:

- government affiliation, sponsorship, partnership, endorsement, certification, accreditation, or procurement status;
- that NIST or another government body has reviewed or approved the project; or
- that a control is implemented merely because it is cited.

The project owner reports that a draft security / Zero Trust governance project has been submitted to a government body. Until authoritative submission evidence and any response are reviewed, the controlled status is:

> **Submission reported; verification and disposition pending.**

Submission evidence should be retained privately with the receiving body, submission date, subject, receipt or case identifier, submitted version digest, sender identity, response status, and disclosure classification. Public records must not expose sensitive identifiers or imply acceptance where only submission occurred.

## 8. Security and Zero Trust baseline

- No implicit trust based on network location, device ownership, provider identity, or prior access.
- Authenticate and authorize the subject, device, action, resource, context, and time boundary.
- Use least privilege, short-lived grants, explicit binding, single use where required, and fail-closed decisions.
- Separate proposal, authorization, execution, audit, and evidence functions.
- Treat repository content, prompts, retrieved pages, issue text, documents, and model output as untrusted input.
- Never store secrets, private keys, credentials, personal data, model weights, or confidential government correspondence in a public repository.
- Record provenance, decisions, execution results, exceptions, and revocation events.

## 9. Repository governance

The `.Global-Strategy` repository is the current public governance baseline. Required controls include:

- protected `main` branch or equivalent ruleset;
- pull request and human approval requirements;
- CODEOWNERS review;
- required status checks and resolved conversations;
- no force push or protected-branch deletion;
- read-only GitHub Actions permissions by default;
- immutable pinning and review of third-party Actions;
- private vulnerability reporting, secret scanning, push protection, and dependency monitoring where available.

Discussions are for deliberation, Issues are for tracked proposals and work, and Pull Requests are for reviewable changes. A discussion or issue does not itself authorize execution.

## 10. Data, evidence, and licensing

- Data is classified before ingestion, external transfer, training, fine-tuning, or publication.
- Large datasets, VM images, model weights, build artifacts, and signed evidence are not stored in ordinary Git without an approved storage decision.
- Every material asset records owner, origin, license or governing terms, version, provenance, restrictions, and approved destination.
- Documentation may use CC BY-NC-SA 4.0 only where explicitly marked.
- Code, models, datasets, media, brands, Apple SDKs, Microsoft assets, and third-party materials retain their applicable and distinct terms.
- Framework references are separated from implementation evidence and compliance claims.

## 11. Change and execution gates

Before a material change, the proposer records:

1. objective and authority;
2. affected files, systems, identities, and data;
3. security, privacy, legal, license, operational, and cost impact;
4. validation and acceptance criteria;
5. rollback or revocation procedure;
6. evidence to retain; and
7. required human approval.

AI-generated work remains a proposal until the required human gate is complete.

## 12. Current phase and priorities

Current phase: **baseline recovery, inventory, and governance stabilization**.

Priority order:

1. Preserve and classify the second terminal inventory as the current AegisAI evidence baseline.
2. Separate project implementation, Apple/Xcode SDK content, agent templates, Ollama models, caches, and metadata.
3. Complete GitHub identity, team, ruleset, branch protection, security reporting, and evidence controls.
4. Add the missing governance, security, and compliance records referenced by the repository baseline.
5. Finalize the four authorization data contracts: AuthorizationRequest, AuthorizationDecision, AuthorizationGrant, and RuntimeExecutionRequest.
6. Confirm the government-submission evidence and record its exact non-public status.
7. Decide whether a SwiftUI application should be created only after reusable Swift/Xcode assets and their licenses are verified.

## 13. Explicit non-goals for the current phase

- No claim of government approval, NIST certification, ISO certification, or CSA certification.
- No production deployment or public release based solely on this draft.
- No automatic activation of Xcode Cloud, App Store distribution, GitHub Enterprise, external AI, or cloud infrastructure.
- No deletion of local files, model data, evidence, or repositories without a reviewed inventory and recoverable plan.
- No shared human credentials or unbounded AI access.

## 14. Approval record

| Role | Name | Decision | Date | Evidence |
| --- | --- | --- | --- | --- |
| Executive authority | Takuya Miyazaki | Pending | — | — |
| Security/governance reviewer | Pending designation | Pending | — | — |

Approval of this manifest confirms the project description and authority boundaries only. It does not certify implementation, compliance, security, legal fitness, or government acceptance.

## 15. Primary references

- NIST Cybersecurity Framework 2.0: https://www.nist.gov/cyberframework
- NIST SP 800-207, Zero Trust Architecture: https://csrc.nist.gov/pubs/sp/800/207/final
- NIST AI Risk Management Framework: https://www.nist.gov/itl/ai-risk-management-framework
- Repository framework map: `FRAMEWORK-MAP.md`
- Repository security policy: `SECURITY.md`
- AI and automation rules: `AGENTS.md`
- GitHub setup controls: `SETUP-CHECKLIST.md`

