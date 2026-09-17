# Firebase Adoption Gate

## Position in AegisAI

Firebase is a candidate external service provider and adapter, not Kernel authority. Firebase Authentication, Security Rules, App Check, Firestore, Storage, Functions, Hosting, or AI features must not independently decide whether an AegisAI Runtime action is authorized.

```text
Apple client / Swift service
        ↓ authenticated and attested request
Firebase adapter boundary
        ↓ service-local access decision
AegisAI Kernel authorization
        ↓ bound, auditable grant
Runtime execution
```

Firebase Security Rules protect supported Firebase data paths. They are necessary service-local controls, but they do not replace business authorization, Kernel policy, or Runtime grant validation. Because matching rules can grant access when any applicable condition allows it, broad overlapping rules are prohibited.

App Check helps reject requests from unauthorized clients. It is an abuse-reduction signal, not user identity, business authorization, or proof that a device is safe.

## Decision checklist

| Area | Required decision before adoption |
| --- | --- |
| Product scope | Exact Firebase products enabled; all others disabled |
| Data | Classification, purpose, region/location, retention, deletion, export, backup |
| Identity | Human/service identities, MFA, lifecycle, claims, session and revocation design |
| Authorization | Deny-by-default Rules, tests, admin-path separation, Kernel binding |
| Client integrity | App Check provider, enforcement rollout, failure and debug-token handling |
| Secrets | No service account keys in apps, Git, VM images, logs, or build artifacts |
| Network | Allowed endpoints, egress controls, TLS validation, rate limits, replay defense |
| Cost | Plan, budget owner, alerts, quotas, abuse limits, emergency shutoff |
| Operations | Logging, alerting, incident handling, evidence retention, recovery objectives |
| Legal | Terms, DPA/privacy, subprocessors, licenses, data subject and cross-border duties |
| Exit | Portable export, dependency removal, account/project deletion, evidence preservation |

## Development sequence

1. Model data and authorization without production data.
2. Develop and test locally with the Firebase Local Emulator Suite where supported.
3. Version Security Rules and their tests in the implementation repository.
4. Deploy a non-production project with synthetic data and least-privilege identities.
5. Observe App Check metrics before enforcement, then enforce by approved rollout.
6. Conduct security, privacy, license, cost, recovery, and exit reviews.
7. Approve production use explicitly; otherwise Firebase remains `candidate`.

## Prohibited defaults

- Public read/write rules, test-mode rules, or wildcard access in production
- Treating Firebase Authentication or App Check as an AegisAI AuthorizationGrant
- Client-held administrative credentials
- Production data in emulators, fixtures, screenshots, issues, or PR logs
- Unbounded Functions, storage, reads/writes, AI calls, or log retention
- Direct AI-agent deployment or rules changes without human review

## Current status

`candidate — not approved for production`

Official references:

- https://firebase.google.com/docs/rules
- https://firebase.google.com/docs/app-check
- https://firebase.google.com/docs/emulator-suite
- https://firebase.google.com/docs/projects/billing/firebase-pricing-plans
- https://firebase.google.com/support/privacy
