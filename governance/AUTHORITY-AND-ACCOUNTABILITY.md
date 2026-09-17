# Authority and Accountability

## Roles

| Role | May propose | May approve | May execute | Accountability |
| --- | ---: | ---: | ---: | --- |
| Executive owner | Yes | Yes | By policy | Final organizational responsibility |
| Security/governance owner | Yes | Within delegation | Controlled | Policy, risk, evidence |
| Maintainer | Yes | Routine/controlled scope | Repository scope | Code and review integrity |
| Soll / AI worker | Yes | No | Only explicit authorized scope | Traceable proposal and execution record |
| External provider | Yes | No | Adapter-defined scope only | Contractual/provider responsibility |

## Separation of duties

The same AI worker must not originate a consequential change, approve it, and attest its success. Human approval is required for critical changes. Kernel authorization is required for Runtime execution when AegisAI execution contracts apply.

## Decision record

Consequential decisions record the decision ID, accountable owner, proposal, applicable policy version, evidence references, approval, execution identity, result, and timestamp.
