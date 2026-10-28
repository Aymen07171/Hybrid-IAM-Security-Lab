---
title: Hybrid IAM Security Lab — Evidence Register
project: Hybrid IAM Security Lab
reviewed: 2026-10-28
tags:
  - iam
  - evidence
  - portfolio
---

# Evidence Register

## Scope and source review

Review date: **2026-10-28**.

| Source | Observation | Classification |
|---|---|---|
| User-provided project brief | Names the project as an IAM project and supplies the repository URL and Obsidian path. The brief describes the project as completed. | Owner-reported context |
| [GitHub repository](https://github.com/Aymen07171/Hybrid-IAM-Security-Lab) metadata | Repository is public; metadata names `main` as the default branch; repository size is 0. | Confirmed at review time |
| GitHub branch, commit, and contents endpoints | Branch listing returned an empty array; commit listing returned “Git Repository is empty”; root contents returned “This repository is empty.” | Confirmed at review time |
| Available local workspace | No project configuration, screenshots, notes, or test records were present. | Confirmed within the supplied workspace |
| Obsidian target path `03 - Learning Hubs/Cybersecurity/IAM Project` | No matching folder or IAM note was located in the available workspace/document search. The actual vault was not mounted here. | Not available for review |

The GitHub source can change after this date. Re-check the repository before publishing the case study. This register describes the evidence accessible during this review, not the owner's full environment.

## Claim ledger

| Claim | Status | What would substantiate it |
|---|---|---|
| A project named Hybrid IAM Security Lab exists as an owner-described portfolio project. | Owner-reported | Project README or lab notes. |
| The public GitHub repository exists. | Confirmed | Repository page/metadata. |
| The repository had no files or commits at review time. | Confirmed | Repository metadata and root contents response. |
| The lab uses a specific cloud identity provider, local directory, or synchronization tool. | Unknown | Sanitized configuration, topology, or setup notes. |
| MFA, conditional access, RBAC, lifecycle automation, or monitoring is configured. | Unknown | Policy/configuration evidence plus a behavior test. |
| The lab passed access-control or security tests. | Unknown | Dated expected/actual test records and correlated logs. |
| The lab improved security or saved time by a measurable amount. | Unknown | Credible baseline and after measurement or direct measurement records. |
| The reference architecture diagram describes the built environment. | False | The diagram is explicitly illustrative until replaced with the verified topology. |

## Confidence labels

- **Confirmed:** visible directly in a source reviewed for this package.
- **Owner-reported:** provided in the project brief but not independently confirmed.
- **Recommended / illustrative:** proposed control, process, architecture, or test; not a deployment claim.
- **Unknown / not provided:** the available evidence is insufficient to make the claim.

## Evidence request checklist

Collect sanitized artifacts in this order to turn the case study into an implementation record:

1. **Environment inventory:** product/service names and versions, local/cloud components, lab scope, and whether data/users are synthetic.
2. **Architecture:** actual identity source, sync/federation direction and protocol, trust boundaries, target resources, and logging destinations.
3. **Configuration:** role/group matrix, privileged access model, authentication/MFA policy, conditional rules/exclusions, lifecycle automation, and audit settings.
4. **Behavior evidence:** joiner, mover, leaver, ordinary user, administrator, denied access, and one failure/recovery scenario.
5. **Troubleshooting notes:** real symptom, root cause, diagnostic record, change made, and retest outcome.
6. **Screenshots:** labeled figures with a short explanation of what each proves. Redact personal data, account identifiers, tenant IDs where appropriate, secrets, tokens, recovery codes, private keys, and reusable session material.
7. **Outcomes:** only measured results with method, baseline, date range, and source. Do not infer numerical impact from the fact that a lab was completed.

## Screenshot handling standard

- Use synthetic users and non-production test data.
- Crop to the relevant configuration or event, while retaining enough context to identify the feature.
- Remove secrets before capture where possible; do not rely on blur for credentials or tokens.
- Add figure number, date, environment label, and a one-sentence statement of what is demonstrated.
- Pair configuration screenshots with an observed test result; configuration alone does not prove enforcement.

