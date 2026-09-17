# Apple, Swift, and Xcode Boundary

## Apple PKI

Apple PKI publishes root and intermediate certificates, certificate revocation information, Certificate Policies, Certification Practice Statements, and audit references. Project trust decisions must validate the intended certificate purpose, chain, validity, revocation behavior, and applicable Apple policy. An Apple certificate does not by itself authorize an AegisAI action.

## Swift

Swift is the preferred implementation language for the Apple-facing security, endpoint, traffic, and virtualization components. Swift is general-purpose and supports Apple platforms, Linux, and Windows. The upstream Swift project is distributed under Apache License 2.0 with a Runtime Library Exception; dependencies retain their own licenses.

Swift language safety reduces certain programming errors but is not proof of system security. Unsafe interfaces, C/C++ interoperability, concurrency, cryptography, network parsing, authorization, and data handling still require explicit review and tests.

## Xcode

Xcode is the Apple-platform development environment for building, testing, profiling, debugging, simulation, signing workflows, and distribution. Xcode Cloud may perform CI/CD builds and parallel tests under its service terms.

Xcode Instruments can observe CPU, GPU, disk, memory, and performance behavior. These are measurement capabilities, not authorization or compliance decisions.

## Virtualization

Apple's Virtualization framework can support isolated macOS or Linux guest environments on compatible systems. A virtual machine is an isolation boundary with its own image provenance, patching, identity, network, storage, logging, and resource limits; it is not automatically trusted.

## Storage boundary

Git is for reviewable source and small text evidence. Large datasets, VM images, model weights, build products, and raw telemetry must not enter ordinary Git history. Use an approved artifact/data store or Git LFS only after classification, retention, encryption, cost, access, provenance, and deletion requirements are defined. GitHub and Xcode are not treated as unlimited archival storage.

## HTTPS boundary

HTTPS protects transport when correctly configured; it does not establish business authorization. Certificate validation, hostname verification, modern TLS, key protection, revocation strategy, API authentication, replay defense, request binding, rate limits, and audit remain separate controls.
