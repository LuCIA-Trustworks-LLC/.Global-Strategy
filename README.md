
# LuCIA Trustworks — Global Strategy " Supported by Omdia. "


This repository is the governance and operating baseline for LuCIA Trustworks, LLC., AegisAI Project, and SeaAI Project.

> Providers propose. The Kernel authorizes. The Runtime executes.



## Repository purpose


This repository defines how people, AI agents, software, evidence, and standards are governed. It does not contain production secrets, customer data, private keys, model weights, or large binary datasets.



## Authority order


1. Applicable law and signed company obligations
2. Human executive authority of LuCIA Trustworks, LLC.
3. Approved governance and security policies in this repository
4. Repository rules, CODEOWNERS, and protected-branch checks
5. Human or AI work instructions
6. Tool and model suggestions


No AI system, provider, model, plugin, or tool may promote itself above this order.



## Main areas


| Path | Purpose |
| --- | --- |
| `governance/` | Authority, conduct, human accountability, AI-worker rules |
| `security/` | Security policy, threat domains, incident and evidence rules |
| `compliance/` | Standards mapping and claims discipline |
| `legal/` | License scope, third-party and AI asset registers |
| `technology/apple/` | Apple PKI, Swift, Xcode, virtualization boundaries |
| `technology/firebase/` | Firebase candidacy, data and authorization boundaries |
| `.github/` | Ownership, PR controls, templates, safe automation |



## Status



Baseline v0.1 is a governance design, not a certification or legal opinion. A referenced standard informs controls only when a mapping and evidence record exist. No file may claim NIST, CSA, ISO, Apple, or other certification without independent evidence and approval.




## Contribution gate


All changes use a pull request. Security-, governance-, license-, or authorization-sensitive changes require human approval from the designated owner. AI agents may draft and test; they may not self-approve, merge, publish, rotate credentials, or change their own authority.



## Public references


- Apple PKI: https://www.apple.com/certificateauthority/
- Xcode: https://developer.apple.com/xcode/
- Swift: https://www.swift.org/
- NIST Cybersecurity Framework: https://www.nist.gov/cyberframework
- NIST SP 800-207: https://csrc.nist.gov/pubs/sp/800/207/final
- Cloud Security Alliance: https://cloudsecurityalliance.org/
- ISO/IEC JTC 1/SC 42: https://www.iso.org/committee/6794475.html



## © 2026 AegisAI Project · © 2026 SeaAI Project · LuCIA Trustworks, LLC.


- LuCIA Trustworks, LLC.logo  © 2026 by LuCIA Trustworks, LLC. is licensed under Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International. To view a copy of this license, visit https://creativecommons.org/licenses/by-nc-sa/4.0/


-  © 2026 AegisAI Project.  © 2026 by LuCIA Trustworks, LLC. is licensed under Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International. To view a copy of this license, visit https://creativecommons.org/licenses/by-nc-sa/4.0/


# I will decline contact from those who cannot provide an answer regarding 


- Please ensure you understand the three pillars as defined by MIT.



- Please strictly adhere to the principles of responsible AI.


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


## About the CSF 2.0 Community Profile Template

This template is provided as an optional supplemental resource to NIST CSWP #32, NIST Cybersecurity Framework 2.0: A Guide to Creating Community Profiles ("Community Profiles Guide").  The Community Profiles Guide provides considerations for creating and using Community Profiles to help implement CSF 2.0. The purpose of the template is to help communities develop their own Community Profiles.  

This template contains the following worksheets:
- Profile Metadata: Contains administrative information about the Community Profile
- Community Profile:  The template communities can follow to complete a Community Profile
- Column Descriptions:  Explains each column in the Community Profile

Please send questions or feedback regarding this template to framework-profiles@nist.gov.



# Integrating a Core ML Model into Your App

Add a simple model to an app, 
pass input data to the model, and process the model's predictions. 

## Overview

This sample app uses a trained model, `MarsHabitatPricer.mlmodel`, 
to predict habitat prices on Mars.

## Add a Model to Your Xcode Project

Add the model to your Xcode project by dragging the model into the project 
navigator. 

You can see information about the model—including 
the model type and its expected inputs and outputs—by 
opening the model in Xcode. 
In this sample, the inputs are the number of solar panels and greenhouses, as well 
as the lot size of the habitat (in acres). 
The output is the predicted price of the habitat.

## Create the Model in Code

Xcode also uses information about the model’s inputs and outputs to 
automatically generate a custom programmatic interface to the model, 
which you use to interact with the model in your code.
For `MarsHabitatPricer.mlmodel`, Xcode generates interfaces to 
represent the model (`MarsHabitatPricer`), the model’s inputs (`MarsHabitatPricerInput`), 
and the model’s output (`MarsHabitatPricerOutput`).

Use the generated `MarsHabitatPricer` class’s initializer to create the model:

``` swift
let marsHabitatPricer = try? MarsHabitatPricer(configuration: .init())
```

## Get Input Values to Pass to the Model

This sample app uses a `UIPickerView` to get the model’s input values from the user:

``` swift
func selectedRow(for feature: Feature) -> Int {
    return pickerView.selectedRow(inComponent: feature.rawValue)
}

let solarPanels = pickerDataSource.value(for: selectedRow(for: .solarPanels), feature: .solarPanels)
let greenhouses = pickerDataSource.value(for: selectedRow(for: .greenhouses), feature: .greenhouses)
let size = pickerDataSource.value(for: selectedRow(for: .size), feature: .size)
```

## Use the Model to Make Predictions

The `MarsHabitatPricer` class has a generated 
`prediction(solarPanels:greenhouses:size:)` method that’s used to predict a
price from the model’s input values—in this case, the number of solar panels,
the number of greenhouses, and the size of the habitat (in acres). The result of
this method is a `MarsHabitatPricerOutput` instance.

``` swift
// Use the model to make a price prediction.
let output = try marsHabitatPricer.prediction(solarPanels: solarPanels,
                                              greenhouses: greenhouses,
                                              size: size)
```

Access the `price` property of `marsHabitatPricerOutput` to get a predicted price 
and display the result in the app’s UI.

``` swift
// Format the price for display in the UI.
let price = output.price
priceLabel.text = priceFormatter.string(for: price)
```

- Note: The generated `prediction(solarPanels:greenhouses:size:)` method can throw an error. The most common type of error you’ll encounter when working with Core ML occurs when the details of the input data don't match the details the model is expecting—for example, an image in the wrong format. 

## Build and Run a Core ML App 

Xcode compiles the Core ML model 
into a resource that’s been optimized to run on a device. 
This optimized representation of the model is included in your app bundle
and is what’s used to make predictions while the app is running on a device. 




---

<div align="center">

**Trust is not a feature added after execution. It is the condition that makes execution possible.**

© 2026 AegisAI Project · © 2026 SeaAI Project · LuCIA Trustworks, LLC.

</div>



