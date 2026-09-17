# Security Policy

## Reporting

Do not publish vulnerabilities, credentials, personal data, exploit details, or active incident information in a public issue. Use GitHub Private Vulnerability Reporting when enabled, or the organization-approved private channel listed in repository settings.

## Minimum repository controls

- Require multi-factor authentication for organization members.
- Protect the default branch; require pull requests, CODEOWNERS, checks, and conversation resolution.
- Disable force pushes and branch deletion for protected branches.
- Give GitHub Actions read-only permissions by default; grant write permissions per job only when justified.
- Pin third-party Actions to an immutable commit SHA and review their licenses and provenance.
- Enable secret scanning, push protection, dependency review, and Dependabot where available.
- Store secrets only in approved secret stores; never in repository content, artifacts, caches, logs, or issue text.
- Record incident evidence immutably and restrict access by need-to-know.

## AI-targeted threats

Prompt injection, poisoned context, model/tool impersonation, authorization confusion, unsafe tool calls, data exfiltration, denial of wallet/service, model extraction, adversarial inputs, and automated traffic abuse are separate threat domains. Controls are tracked in `security/AI-THREAT-DOMAINS.md`.

## Supported status

This baseline is under active development. It does not promise a response SLA until an approved contact and incident process are published.
