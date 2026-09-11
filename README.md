<div align="center">

# AegisAI

### Built for the space between trust and autonomy.

**A vendor-neutral authorization architecture for responsible AI execution.**

![Status](https://img.shields.io/badge/status-research%20%26%20development-111827?style=for-the-badge)
![Architecture](https://img.shields.io/badge/architecture-zero%20trust-0ea5e9?style=for-the-badge)
![License](https://img.shields.io/badge/license-CC%20BY--NC--SA%204.0-22c55e?style=for-the-badge)

</div>

---

## The principle

> **Providers propose. The Kernel authorizes. The Runtime executes.**

AegisAI separates intelligence from authority.

Models, vendors, tools, and execution environments may propose actions—but none of them become the final authority. Every consequential action must pass through explicit policy, authorization, identity, and audit controls before execution.

## Architecture

```text
AegisAI
├── Kernel
│   ├── Policy
│   ├── Authorization
│   ├── Identity
│   └── Audit
├── Runtime
│   └── Soll
├── Adapters
├── MCP
└── Config
```

| Layer | Responsibility |
| --- | --- |
| **Kernel** | The sole authority for policy, authorization, identity, and audit decisions |
| **Runtime / Soll** | Executes only what the Kernel has explicitly authorized |
| **Adapters** | Connect providers and platforms without transferring authority to them |
| **MCP** | Provides a controlled interoperability boundary |
| **Config** | Holds canonical, reviewable system configuration |

## Authorization model

Execution is bound to explicit contracts:

1. `AuthorizationRequest`
2. `AuthorizationDecision`
3. `AuthorizationGrant`
4. `RuntimeExecutionRequest`

Authorization grants are single-use and fail closed.

```text
ISSUED ──▶ CLAIMED ──▶ CONSUMED
   ├────▶ REVOKED
   └────▶ EXPIRED
```

Requests, grants, policies, provenance, and evidence are cryptographically bindable so that an approved action cannot be silently replaced at execution time.

## Design commitments

- **Vendor neutrality** — no model, cloud, protocol, or platform becomes Kernel authority.
- **Least privilege** — every execution receives only the authority it requires.
- **Explicit authorization** — proposed intent and executable action remain distinct.
- **Fail-closed behavior** — missing, invalid, expired, replayed, or revoked authority stops execution.
- **Evidence by design** — authorization and execution produce traceable audit records.
- **Human accountability** — autonomy does not remove responsibility.

## Governance direction

AegisAI is being developed with reference to established security and governance work, including:

- NIST SP 800-53
- NIST SP 800-207 Zero Trust Architecture
- NIST Cybersecurity Framework
- Cloud Security Alliance guidance

These references inform the project; they do not imply certification, endorsement, or completed compliance.

## Project status

> [!IMPORTANT]
> AegisAI is under active research and development. It is not currently represented as a production-ready security product.

Current work focuses on the authorization contract, grant lifecycle, policy binding, provenance, evidence, replay resistance, and auditable runtime execution.

## Organization

AegisAI is a project of **LuCIA Trustworks, LLC.**  
Related research and creative direction: **SeaAI Project.**

## License

Documentation and project materials are licensed under the [Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International License](https://creativecommons.org/licenses/by-nc-sa/4.0/), unless a file states otherwise.

---

<div align="center">

**Trust is not a feature added after execution. It is the condition that makes execution possible.**

© 2026 AegisAI Project · © 2026 SeaAI Project · LuCIA Trustworks, LLC.

</div>
