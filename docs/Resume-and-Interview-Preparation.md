---
title: Hybrid IAM Security Lab — Resume and Interview Preparation
project: Hybrid IAM Security Lab
tags:
  - microsoft-entra
  - conditional-access
  - career
---

# Resume and Interview Preparation

> [!warning] Keep the status precise
> The screenshots substantiate a created MFA policy in Report-only, not enforced MFA. The legacy-authentication policy is a draft without a Block access grant or creation evidence. Do not describe these as enforced controls.

## Resume entry

**Microsoft Entra Conditional Access Lab — Hybrid IAM Security Lab** | 2026

- Created a Microsoft Entra emergency-access Security group with Assigned membership and configured an all-resources MFA Conditional Access policy in Report-only for impact analysis.
- Documented an emergency Global Administrator account and identified validation requirements for account redundancy, phishing-resistant authentication, monitoring, and recovery testing.
- Assessed policy evidence and identified deployment gaps: Security Defaults disabled, MFA policy not enforced, legacy-authentication block unfinished, and hybrid directory integration not evidenced.

Keep the scope caveat if using these bullets. Do not claim on-premises integration, MFA enforcement, successful sign-in testing, compliance, or quantified impact until supported by evidence.

## 30-second recruiter explanation

> “I built a Microsoft Entra Conditional Access lab focused on emergency access, group-based exclusions, and MFA policy design. I created an all-resources MFA policy in Report-only so its impact could be reviewed before enforcement. I also identified that the legacy-authentication policy was still a draft and that Security Defaults were disabled, so my next step is to complete and validate the replacement baseline. The available notes show Entra policy work; I have not yet documented an on-premises synchronization path.”

## Recruiter questions

### What did you configure?

Describe the `CA-Exclude-EmergencyAccess` Security group with Assigned membership, the emergency Global Administrator assignment visible in the screenshot, and the CA-01 MFA policy created in Report-only. Note that only one emergency account role assignment is shown and the group’s final roster needs verification.

### What is the project’s current limitation?

Explain that the screenshots show Security Defaults disabled, CA-01 in Report-only, and CA-02 still in a draft form without Block access selected. The current evidence does not establish an enforced baseline.

### Why use Report-only?

Report-only evaluates and logs policy results without enforcing grant/session controls. It allows impact review before rollout. Explain that users are not prompted for MFA by a report-only MFA policy.

### Is this a hybrid IAM implementation?

Be exact: “The project is named Hybrid IAM Security Lab, but the notes I reviewed show Entra Conditional Access. They do not document AD DS, Entra Connect/Cloud Sync, or federation. I would add that architecture and test evidence before claiming a verified hybrid integration.”

### What would you do next?

1. Verify licensing and inspect every active Conditional Access policy.
2. Reconcile CA-01’s name with its actual user assignment and review all exclusions.
3. Complete CA-02 with Block access, use Report-only to inspect interactive and non-interactive legacy sign-ins, then enable after review.
4. Verify two cloud-only emergency accounts, distinct phishing-resistant methods, secure credential handling, alerts, and regular sign-in validation.
5. Add evidence of the actual hybrid connector if the lab includes one.

## Technical questions to prepare for

- How do Security Defaults differ from Conditional Access?
- What does Report-only do, and where are its results reviewed?
- Why can legacy clients bypass MFA?
- Which legacy client categories are selected in the draft and what grant control is missing?
- Why keep emergency access accounts separate, and what authentication methods should protect them?
- When should emergency accounts be excluded from a policy, and why does a Report-only policy not need an exclusion?
- What does a group-based exclusion make easier, and how do you control membership changes?
- Which evidence would prove that an MFA or legacy-authentication policy is enforcing at runtime?
- What evidence is needed to support the “hybrid” part of the project title?

## Answer anchors

- **Authentication vs authorization:** authentication establishes the sign-in context; authorization determines what the identity may do at a resource.
- **Security Defaults transition:** either keep the built-in baseline or replace it with complete, enforced Conditional Access controls. The screenshot shows defaults disabled while the visible MFA policy is Report-only.
- **Legacy authentication:** older clients/protocols may not support modern MFA or device controls. A Conditional Access block policy needs a Block access grant, a defined scope, and runtime validation.
- **Evidence quality:** policy configuration screens show intended settings; sign-in log results and positive/negative tests show behavior.
- **Emergency access:** maintain redundant cloud-only accounts, use strong distinct methods, exclude only where needed to prevent lockout, monitor use, and test regularly.

## Evidence checklist before an interview

- [ ] Inspect the saved CA-01 policy and resolve the name/scope mismatch.
- [ ] Confirm the final group roster contains only the intended emergency accounts.
- [ ] Verify both emergency accounts, their authentication methods, and a successful controlled sign-in test.
- [ ] Confirm what protects the tenant while Security Defaults are disabled.
- [ ] Finish or clearly label the legacy-authentication policy as incomplete.
- [ ] Capture sanitized Report-only sign-in results and any enforced outcomes.
- [ ] Add evidence for AD DS / Entra Connect / Cloud Sync / federation before claiming hybrid integration.

