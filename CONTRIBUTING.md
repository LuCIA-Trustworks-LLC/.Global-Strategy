# Contributing

1. Open or reference an issue describing purpose, owner, risk class, and acceptance criteria.
2. Create a short-lived branch; do not work directly on the protected default branch.
3. Keep one logical change per pull request.
4. Update affected policy, license, threat, and evidence records.
5. Run relevant tests and record results without secrets or personal data.
6. Obtain CODEOWNERS review and required status checks.
7. Merge only through the approved GitHub method; retain review and provenance history.

## Change classes

| Class | Examples | Minimum gate |
| --- | --- | --- |
| Routine | Typo, non-normative link | One human review |
| Controlled | Code, workflow, dependency, data schema | Owner review plus checks |
| Critical | Authorization, identity, audit, secrets, licenses, security policy | Executive/security owner approval plus evidence |

AI agents cannot satisfy a human approval requirement.
