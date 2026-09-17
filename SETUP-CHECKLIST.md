# GitHub Setup Checklist

## Before first merge

- [ ] Confirm repository visibility and remove any unintended public data
- [ ] Confirm `@Takuya-Miyazaki` is the correct initial CODEOWNER
- [ ] Create least-privilege GitHub teams before adding employees or AI integrations
- [ ] Set default Actions permissions to read repository contents only
- [ ] Protect `main`: PR required, one or more human approvals, CODEOWNERS, conversation resolution, status checks, no force push
- [ ] Enable signed commits/tags or vigilant mode according to the organization policy
- [ ] Enable private vulnerability reporting
- [ ] Enable secret scanning and push protection
- [ ] Enable Dependabot alerts, security updates, and dependency review where supported
- [ ] Define artifact/log retention and remove unnecessary workflow write tokens
- [ ] Add approved security contact privately in repository settings

## Before activating an AI worker

- [ ] Create a dedicated identity; do not share a human credential
- [ ] Grant repository and branch access only to the necessary scope
- [ ] Prohibit bypass of branch protection and approval gates
- [ ] Define allowed tools, data classes, network destinations, budget, and expiry
- [ ] Require AI disclosure and provenance in every PR
- [ ] Test prompt-injection and untrusted-content handling
- [ ] Define emergency revocation and audit procedure

## Large data

- [ ] Keep VM images, datasets, model weights, and build artifacts outside ordinary Git
- [ ] Approve Git LFS or an artifact/data store explicitly
- [ ] Define encryption, region, access, retention, backup, cost, and deletion rules
