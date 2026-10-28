---
title: Hybrid IAM Security Lab — Evidence Register
project: Hybrid IAM Security Lab
reviewed: 2026-10-28
tags:
  - iam
  - microsoft-entra
  - evidence
---

# Evidence Register

## Source material reviewed

| Source | Observed evidence | Classification |
|---|---|---|
| Obsidian note `03 - Learning Hubs/Cybersecurity/IAM Project.md` | Steps for two emergency accounts; Security Defaults note; emergency group setup; CA-01 MFA instructions; a statement that legacy authentication is implemented. | Owner-maintained project notes; statements checked against screenshots. |
| Linked `IAM groups.md` | Group type and membership notes; intended emergency exclusion-group use. | Owner-maintained reference note. |
| Linked `Block legacy authentication.md` | Definition of legacy authentication. | Owner-maintained reference note. |
| `Pasted image 20261026222003.png` | One emergency account shown with direct, active, permanent Global Administrator assignment. | Screenshot evidence; identifiers omitted from this public register. |
| `Pasted image 20261026222531.png` | Security Defaults setting shown as Disabled. | Screenshot evidence. |
| `Pasted image 20261026223419.png` | New Security group `CA-Exclude-EmergencyAccess`; Assigned membership; two members selected; no owners selected. | Screenshot evidence at creation. |
| `Pasted image 20261026223437.png` | Group appears in list as Security / Assigned. | Screenshot evidence of group existence; member roster not expanded. |
| `Pasted image 20261026224533.png`, `...224710.png`, `...224742.png` | CA-01 setup uses All resources and MFA grant; created policy list shows Report-only. Assignment summary appears to include all users despite the “Admins” name and written admin-role instruction. | Screenshot evidence; final saved scope should be verified. |
| `Pasted image 20261026230829.png` | New CA-02 form; Exchange ActiveSync and Other clients selected; Report-only; zero grant controls; Create button visible. | Screenshot evidence of a draft only, not creation or enforcement. |
| Sign-in logs, policy impact, successful account tests, directory sync configuration | Not supplied. | Unknown / not evidenced. |

Original screenshots remain in the private Obsidian vault. They contain tenant identifiers, account/contact details, or a directory object identifier; they were not copied into this public repository.

## Claim ledger

| Claim | Status | Evidence limit / follow-up |
|---|---|---|
| Microsoft Entra ID is in scope. | Confirmed | Admin-center screenshots and policy forms. |
| One emergency account has a direct, active, permanent Global Administrator assignment. | Confirmed | One screenshot only; no authentication method or sign-in proof. |
| Two emergency accounts are fully configured. | Partially supported | Note describes two; group form shows two members selected. Only one GA role assignment is visible. Verify both identities, methods, and sign-ins. |
| `CA-Exclude-EmergencyAccess` exists as a Security / Assigned group. | Confirmed | Group list; creation form showed two members selected. Final roster not shown. |
| CA-01 requires MFA for administrators. | Inconsistent / needs verification | Name says Admins; setup screenshot says all users included. All resources and Require MFA are shown; created state is Report-only. Inspect saved assignments. |
| CA-01 enforces MFA. | Not supported | Created policy is Report-only. Microsoft documents that Report-only evaluates/logs but does not enforce or prompt. |
| Security Defaults are disabled. | Confirmed | Screenshot. No fully enforced replacement baseline is evidenced in the reviewed material. |
| CA-02 blocks legacy authentication. | Not supported | Screenshot shows a new-policy form, Report-only, client types selected, zero grant controls, and Create still available. |
| The lab includes on-premises directory integration or synchronization. | Not evidenced | No AD DS, Entra Connect/Cloud Sync, or federation setup shown. |
| Sign-in tests passed or attack exposure decreased. | Not supported | No sign-in logs, test results, or measurements supplied. |

## Key security findings

1. **Baseline gap to verify:** Security Defaults are disabled, CA-01 is Report-only, and CA-02 is incomplete in the captured state. Check for other enforced policies; if none provide equivalent protection, restore Security Defaults or complete a licensed Conditional Access replacement immediately.
2. **Scope mismatch:** CA-01’s display name and written steps say admins, while the captured assignment says all users. Confirm the saved policy and update either its scope or name before enforcement.
3. **Legacy-auth policy incomplete:** selected client categories do not block access without the Block access grant control and policy creation.
4. **Emergency access evidence partial:** confirm two cloud-only accounts, strong distinct phishing-resistant methods, access exclusions as needed, monitoring, and regular testing.
5. **Hybrid connection absent from evidence:** obtain the actual directory and connector configuration before describing the deployment as hybrid.

## Evidence and privacy handling

- Keep the original Obsidian screenshots private; redact tenant IDs, UPNs/emails, object IDs, and other account details before publishing any image.
- Pair a configuration screenshot with sign-in log evidence; a setup screen alone does not prove runtime behavior.
- Record test date, identity label, client type, target resource, expected and actual policy result, and log reference.

## Microsoft references

- [Emergency access accounts](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/security-emergency-access)
- [Security defaults](https://learn.microsoft.com/en-us/entra/fundamentals/security-defaults)
- [Conditional Access Report-only impact](https://learn.microsoft.com/en-us/entra/identity/conditional-access/concept-conditional-access-report-only)
- [Block legacy authentication](https://learn.microsoft.com/en-us/entra/identity/conditional-access/policy-block-legacy-authentication)

