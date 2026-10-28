---
title: Hybrid IAM Security Lab — Case Study
project: Hybrid IAM Security Lab
status: Evidence-limited portfolio case study
reviewed: 2026-10-28
tags:
  - cybersecurity
  - iam
  - portfolio
  - identity-security
---

# Hybrid IAM Security Lab — Case Study

> [!important] Evidence boundary
> The owner describes this as a completed IAM project. In the material available for this review, the linked GitHub repository is empty and the named Obsidian vault folder, screenshots, configurations, and test records were not available. This document does not present a suggested design as a deployed system. See the [Evidence Register](Evidence-Register.md) for what was checked and what evidence would close the gaps.

## 1. Executive Summary

The **Hybrid IAM Security Lab** is an owner-described identity and access management portfolio project. Its title indicates a hybrid IAM focus, but no directory, identity provider, cloud platform, configuration, or test evidence was available to confirm the implementation. The public repository exists, but the repository contents endpoint reported that it is empty at the time of review.

This case study frames the business problem, target controls, and validation approach expected of a hybrid IAM lab. It is suitable as a documentation foundation; the actual platform names, build sequence, screenshots, results, and measured outcomes must be added from the project evidence before the case study is presented as a record of implementation.

**Portfolio objective (inferred from the project name and owner brief):** demonstrate the ability to reason about identities that need controlled access across on-premises and cloud resources. This is an interpretation of the project scope, not a confirmed description of its built components.

**Expected value of the target design:** clearer identity lifecycle ownership, consistent authentication and authorization controls, reduced standing privilege, and better auditability. These are desired outcomes, not measured results from this lab.

## 2. Project Background

### Organization context

No real organization or environment details were supplied. For a portfolio narrative, use this clearly simulated context only if it matches the actual lab:

> A small organization operates a mix of local and cloud-hosted services. Staff and administrators need access based on job responsibility, while identity changes and departures must result in timely access changes across both environments.

### Security challenges the lab can address

These are common hybrid identity risks and portfolio design goals, not confirmed incidents or findings in this project:

- Separate identity stores can create inconsistent account lifecycle and access decisions.
- Broad groups or long-lived administrator access can grant more privilege than a task requires.
- Password-only or inconsistent authentication controls can make account compromise easier.
- Delayed disablement or incomplete session revocation can leave access after a person changes roles or leaves.
- Logs split across systems can make investigation and access review difficult.

### Reference requirements

| ID | Requirement for a defensible lab | Evidence to add |
|---|---|---|
| IAM-R1 | Identify the authoritative source for each user and administrator identity. | Design note or identity flow configuration. |
| IAM-R2 | Define joiner, mover, and leaver actions, including access removal. | Runbook plus before/after account and group evidence. |
| IAM-R3 | Grant access through named roles/groups with least privilege. | Role/group matrix and representative membership evidence. |
| IAM-R4 | Require strong authentication proportionate to account and resource risk. | Sanitized policy configuration and positive/negative sign-in results. |
| IAM-R5 | Keep privileged administration separate, limited, and auditable. | Admin role assignments, elevation procedure, and audit records. |
| IAM-R6 | Record identity and access events in a reviewable location. | Sanitized event samples, retention setting, and alert/review process. |
| IAM-R7 | Test allowed and denied access, including lifecycle changes and failure cases. | Dated test matrix with actual observed outcomes. |

### Governance and compliance considerations

Map controls to a named framework only when the lab objective requires it, and describe the result as a learning exercise rather than a compliance assessment. A control mapping is not proof of compliance. For authentication and federation design, use the current NIST SP 800-63 Revision 4 suite as a reference; NIST SP 800-207 is a useful resource-centric architecture reference for zero-trust principles. See [Further reading](#references-and-further-reading).

## 3. Solution Overview

### Confirmed implementation

No technologies, services, identity stores, integrations, roles, policies, or provisioning workflows could be confirmed from the available repository or workspace materials. Do not name a vendor or protocol as implemented until a configuration, screenshot, or test trace supports that claim.

### Logical solution concept

The proposed reference design in [architecture.svg](architecture.svg) separates identity lifecycle management, a local identity domain (if used), an identity bridge, cloud authentication and policy, target resources, and centralized audit evidence. It is technology-neutral and should be replaced or relabeled to match the actual lab.

| Capability | Target behavior | Current evidence status |
|---|---|---|
| Identity lifecycle | Create, update, disable, and remove access in response to approved identity changes. | Unknown / not provided |
| Authentication | Authenticate users and administrators using risk-appropriate factors and policy. | Unknown / not provided |
| Authorization | Assign access through scoped roles or groups and check it at the resource. | Unknown / not provided |
| Hybrid connectivity | Define which system is authoritative and how identity attributes or assertions cross the trust boundary. | Unknown / not provided |
| Governance | Review access, privileged assignments, exceptions, and dormant identities. | Unknown / not provided |
| Monitoring | Collect and review identity, policy, provisioning, and resource access events. | Unknown / not provided |

## 4. Architecture Design

### Diagram

![Proposed technology-neutral hybrid IAM reference architecture. It is an illustrative target design, not evidence of deployed components.](architecture.svg)

Editable source: [architecture.mmd](architecture.mmd). The diagram uses generic roles rather than vendor-specific services because no products or configurations were supplied.

### Components and trust boundaries

1. **People and lifecycle source:** a user or approved identity event initiates a change. An HR system is one possible source, but none was confirmed.
2. **Provisioning and role governance:** an operator or workflow maps job function to scoped groups/roles, applies approval where needed, and records exceptions. This is recommended design behavior.
3. **Local identity domain:** a directory may serve on-premises resources if the real lab includes one. Its product, authority, and configuration are unknown.
4. **Identity bridge:** a controlled synchronization and/or federation mechanism crosses the local/cloud boundary. Direction, attributes, protocol, service account, and failure behavior must be documented from the actual build.
5. **Cloud identity and policy:** the identity provider authenticates the subject and evaluates applicable factors and access policy. The identity provider, MFA method, and policy behavior are unknown.
6. **Resources:** cloud and local applications enforce their own role/group permissions after the identity decision. A successful sign-in alone does not prove resource authorization is correctly scoped.
7. **Audit and monitoring:** identity, bridge, policy, and resource events are collected for investigation and access review. No logging platform or retention setting was confirmed.

### Reference data flow

1. An approved joiner, mover, leaver, or privileged-access event is recorded.
2. Provisioning updates the authoritative identity and its scoped access assignments.
3. If hybrid synchronization or federation is in scope, the identity bridge exchanges only the attributes or assertions required by the design.
4. A user requests a resource; authentication and applicable policy are evaluated before a session is granted.
5. The target resource evaluates its own authorization rules and returns only the allowed operations.
6. Relevant changes, sign-ins, policy decisions, and resource activity are logged and reviewed.

These steps describe the reference model. Confirm actual directionality, protocols, and enforcement points from the implemented configuration before presenting them as project facts.

### Security boundaries

- **Identity administration boundary:** only authorized administrators should change identity sources, mappings, policy, or privileged assignments.
- **Local/cloud trust boundary:** synchronization or federation credentials, certificates, and endpoints need explicit ownership, least privilege, rotation, and failure handling.
- **Authentication/authorization boundary:** successful authentication is distinct from approval to use a specific resource.
- **Evidence boundary:** screenshots and exported logs should be sanitized; never publish passwords, tokens, recovery codes, personal data, tenant secrets, or reusable identifiers.

## 5. Implementation Walkthrough

The available materials did not include a build log, so the following is a **recommended walkthrough structure**, not a claim that these steps were completed. Replace each bracket with the observed product and action.

1. **Plan the scope.** Record lab purpose, in-scope identities and resources, success criteria, and whether the environment is simulated. Document the threat assumptions and what the lab does not cover.
2. **Prepare the environment.** Identify the local directory (if any), identity provider, test users, test resources, network/DNS prerequisites, licensing constraints, and rollback path. Keep secrets out of source control.
3. **Define identity ownership.** Record which system owns each attribute and which system can create, update, disable, or delete an identity. Decide how conflicts and sync failures are handled.
4. **Configure the identity bridge.** Document the actual sync/federation method, source/target scope, attribute mappings, service identity privileges, credential handling, and monitoring. Capture sanitized evidence.
5. **Design groups and roles.** Create role names tied to job function and resource permissions. Separate everyday accounts from privileged administration where supported. Record owners and review cadence.
6. **Provision test identities.** Use non-production test accounts. Demonstrate the intended joiner and mover flows and verify both grants and removals at the target resource.
7. **Configure authentication controls.** Record which users/resources require MFA or other factors, the exception path, recovery process, and how administrators are protected. Test an allowed and a denied case.
8. **Configure access policy.** Document the exact conditions and outcomes for each policy. Avoid broad exclusions; make emergency access narrow, monitored, and tested.
9. **Enable audit evidence.** Identify the event sources, destination, retention, access to logs, and alert or review process. Verify events arrive and contain enough context for investigation.
10. **Validate and document.** Run the test cases in [Testing and Validation](#9-testing-and-validation), record actual output and date, and include sanitized screenshots with captions.
11. **Review and clean up.** Remove temporary grants and test accounts, rotate lab credentials if needed, capture final configuration, and list known limitations and next steps.

**Evidence status for each step:** unknown / not provided. The Evidence Register lists the exact artifacts that would make this walkthrough specific to the built lab.

## 6. Screenshot Walkthrough

No screenshots were available in the supplied workspace or repository. Therefore, there are no project screenshots to describe as observed evidence. Capture the following only if these screens exist in the actual build:

| Suggested caption | Capture | Purpose and security point |
|---|---|---|
| **Figure 1 — Lab topology and identity boundaries** | Final topology view with local/cloud boundary, trust flow, and system names. | Lets a reviewer understand where identity is authoritative and where policy is enforced. Label any proposed or simulated elements. |
| **Figure 2 — Identity bridge configuration** | Sanitized connector/sync/federation settings and scope. | Shows configured direction and scope. Redact tenant IDs, domains if sensitive, certificates, secrets, and personal identifiers. |
| **Figure 3 — Role and group model** | Role/group names and permission scope, with test identities anonymized. | Shows how access is assigned and whether privileges are separated. Avoid exposing real users. |
| **Figure 4 — Authentication policy** | Policy conditions, target population, MFA requirement, and exclusions. | Makes enforcement and exceptions reviewable. Do not show recovery codes or secrets. |
| **Figure 5 — Joiner/mover/leaver validation** | Before/after membership or account state for a test identity. | Demonstrates lifecycle change and access removal. Include timestamps and expected/actual result. |
| **Figure 6 — Audit event** | Sanitized sign-in, policy, provisioning, or admin event. | Demonstrates that the control creates reviewable evidence. Redact IPs and identifiers as appropriate. |

Use consistent figure numbering and provide a one-sentence caption, the test identity label, capture date, and what the screenshot proves. A configuration screen shows intent; a separate test result is needed to show behavior.

## 7. Security Analysis

The analysis below describes recommended controls and their evidence needs. It does not assert that the lab implemented them.

| Control area | Target practice | Status from available evidence | Evidence needed |
|---|---|---|---|
| Least privilege | Scope roles to the minimum resource actions; avoid broad nested groups and standing admin rights. | Unknown | Permission matrix, group membership, and denied-access test. |
| RBAC | Use named roles/groups with an owner, purpose, scope, and review cadence. | Unknown | Role catalog and representative assignment review. |
| MFA and authentication | Select factors and recovery controls for the account/resource risk; test exceptions and recovery paths. | Unknown | Sanitized policy, factor configuration, positive/negative sign-in evidence. |
| Conditional access | If supported, evaluate relevant user, device, application, and risk signals; keep exclusions narrow and reviewed. | Unknown | Policy export, scenario tests, exception owner and expiry. |
| Identity governance | Define approval, periodic access review, leaver cleanup, and exception expiry. | Unknown | Runbook, review record, and lifecycle test. |
| Privileged access | Separate administrative identities/roles where feasible, limit duration, and log elevation/actions. | Unknown | Privileged role inventory, elevation workflow, admin event samples. |
| Audit and monitoring | Collect identity, bridge, policy, and resource events; protect and review the records. | Unknown | Event samples, retention configuration, monitoring/review procedure. |
| Recovery and resilience | Document bridge outage, identity-provider outage, emergency access, and restoration procedures. | Unknown | Failure-mode test record and approved recovery runbook. |

NIST SP 800-207 emphasizes protecting resources and evaluating access rather than relying on network location alone. NIST SP 800-63-4 provides current guidance on digital identity, authentication, and federation. Use these as design references; do not label the lab “compliant” without a scoped assessment and supporting evidence.

## 8. Challenges and Resolutions

No project notes, error logs, or troubleshooting history were supplied. Specific problems and fixes cannot be attributed to this lab without evidence.

For each real issue, document: **symptom → impact → root cause → diagnostic evidence → resolution → retest → lesson learned**. Useful hybrid IAM troubleshooting topics, if encountered, include:

- stale or conflicting identity attributes;
- synchronization scope or duplicate identity behavior;
- DNS, time, certificate, or connectivity problems across the trust boundary;
- a policy exclusion that unintentionally bypasses a control;
- a role/group mapping that grants access too broadly or blocks an expected user;
- missing audit events or insufficient context for a sign-in decision.

These are investigation prompts, not reported project challenges. Add only issues that occurred and evidence the actual resolution.

## 9. Testing and Validation

No test results were provided. The matrix below is a proposed baseline. **Actual result is “Not provided” for every scenario**; do not present an expected result as a pass.

| ID | Scenario | Expected result | Actual result / status |
|---|---|---|---|
| T-01 | Joiner receives only the role/group access approved for the test job. | Identity is provisioned and can access the intended resource; unrelated resource access is denied. | Not provided — not verified |
| T-02 | Mover changes role. | Old access is removed and only new approved access remains. | Not provided — not verified |
| T-03 | Leaver is disabled or removed. | Authentication and resource access are blocked; applicable sessions/tokens are revoked or expire according to documented behavior. | Not provided — not verified |
| T-04 | Standard user signs in under the required authentication policy. | Required factor is enforced; sign-in and policy decision are logged. | Not provided — not verified |
| T-05 | Privileged action is attempted by a standard user. | Request is denied and recorded. | Not provided — not verified |
| T-06 | Authorized administrator performs a scoped action. | Access is granted only for the intended action; actor and activity are auditable. | Not provided — not verified |
| T-07 | Sync/federation or policy dependency is unavailable. | Failure behavior matches the documented safe design and creates an operational signal. | Not provided — not verified |
| T-08 | Identity uses an unsupported device/context, if device policy is in scope. | Access follows the defined policy outcome and the reason is observable. | Not provided — not verified |

For each run, record date/time and timezone, test identity label, preconditions, exact policy/resource, expected result, actual result, log/event reference, screenshot path, and pass/fail. Use synthetic accounts and sanitize evidence. A lab test validates only the tested configuration and scenarios; it does not prove production readiness.

## 10. Project Outcomes

### Confirmed outcome of this review

- The public GitHub repository was found, but its contents endpoint reported that the repository is empty.
- The named Obsidian folder, implementation files, screenshots, and test reports were not available in the supplied workspace.
- This documentation package now provides a case-study structure, evidence register, technology-neutral reference diagram, validation plan, and recruiter/interview templates.

### Outcomes of the IAM implementation

Unknown. No measured security improvement, operational saving, user count, provisioning time, test pass rate, or deployed control could be established. Do not add numerical impact without source records.

### Scalability considerations for a future revision

- Make identity ownership and attribute mappings explicit before adding more directories or applications.
- Automate repeatable provisioning only after lifecycle rules and failure handling are understood.
- Review group nesting, privileged assignments, and policy exceptions as scope grows.
- Centralize audit events and define retention, ownership, and response actions.
- Add failure and recovery tests for the identity bridge and authentication dependencies.

### Prioritized next improvements

1. Add a minimal repository README and sanitized architecture/configuration artifacts.
2. Record the actual products, versions, protocols, identity source, and trust direction.
3. Capture joiner/mover/leaver and allowed/denied access test evidence.
4. Add a screenshot set with captions and safe redactions.
5. Record limitations and any measured outcomes supported by logs or before/after data.

## 11. Recruiter-Friendly Project Summary

**Short version:** The owner describes the Hybrid IAM Security Lab as a completed identity and access management project focused on hybrid identity. The public repository was empty during this review, so the specific tools, controls, and results are not yet evidenced in the available portfolio material.

**Skills the project can demonstrate once backed by artifacts:** identity lifecycle design, directory and identity-provider integration, role/group-based authorization, MFA and access policy, privileged access handling, audit analysis, troubleshooting, and security test planning. Only list the skills that match the actual build and can be explained with evidence.

**Why this can matter for IAM / security roles:** a well-documented lab can show how an engineer connects identity decisions to resource access, handles joiner/mover/leaver changes, limits administrative privilege, and verifies both allowed and denied outcomes. The current evidence does not establish which of these were implemented.

## 12. Resume Version

Use the editable entry in [Resume and Interview Preparation](Resume-and-Interview-Preparation.md) after filling in the bracketed values from the actual environment. Do not list products, MFA, Conditional Access, RBAC, automated provisioning, production readiness, compliance, or impact metrics unless the project artifacts support them.

**Safe drafting template:**

> **Hybrid IAM Security Lab — Portfolio Project** | [Month Year]
> - Built a lab using **[confirmed identity provider]** and **[confirmed directory/resources]** to demonstrate **[specific verified identity lifecycle or access-control capability]**.
> - Configured **[specific verified control]** and validated it with **[test scenario]**, recording **[actual outcome and evidence location]**.
> - Documented **[confirmed architecture / troubleshooting / audit work]** and identified **[specific limitation or next improvement]**.

If the evidence remains unavailable, keep this as a draft rather than placing unverified technologies or outcomes on a resume.

## 13. Interview Preparation

Use the prompts and answer frameworks in [Resume and Interview Preparation](Resume-and-Interview-Preparation.md). Be ready to show the architecture, one real configuration, one denied-access test, and one limitation. If an item was not built, say so and explain how you would implement and validate it; a clear boundary between implemented and planned work is stronger than an unsupported claim.

## References and Further Reading

- [NIST SP 800-63B-4 — Authentication and Authenticator Management](https://csrc.nist.gov/pubs/sp/800/63/b/4/final) — current authentication guidance within the NIST SP 800-63 Revision 4 suite.
- [NIST SP 800-63-4 — Digital Identity Guidelines](https://www.nist.gov/publications/nist-sp-800-63-4-digital-identity-guidelines) — identity proofing, authentication, and federation guidance.
- [NIST SP 800-207 — Zero Trust Architecture](https://csrc.nist.gov/pubs/sp/800/207/final) — resource-focused zero-trust architecture principles.

These references inform the recommendations in this document. They do not demonstrate that the lab implemented a control or meets a standard.

