# Hybrid IAM Security Lab — Microsoft Entra Conditional Access

This package is based on the project note in the Obsidian vault, its linked `IAM groups` and `Block legacy authentication` notes, and the screenshots embedded in the note. It replaces the earlier technology-neutral draft with evidence from the actual lab.

> [!warning] Current-state finding
> The screenshots show Microsoft Entra Security Defaults **Disabled** and the `CA-01-Require-MFA-Admins` policy in **Report-only**. The legacy-authentication policy screenshot is still a new-policy draft with no grant control selected. The available evidence therefore does not show an enforced MFA or legacy-authentication block baseline. Verify the tenant’s complete policy state before treating it as protected.

## Start here

- [Case study](docs/IAM-Security-Lab-Case-Study.md) — 13 requested sections grounded in the Obsidian notes and screenshots.
- [Evidence-based Entra access model](docs/architecture.svg) — current findings and evidence gaps; [editable Mermaid source](docs/architecture.mmd).
- [Evidence register](docs/Evidence-Register.md) — captures reviewed, what each supports, and unresolved claims.
- [Resume and interview guide](docs/Resume-and-Interview-Preparation.md) — truthful project summary and interview answers.

## Privacy note

The original vault screenshots contain tenant identifiers, account/contact details, and an object ID. They remain in the private vault and are not copied into this public repository. The walkthrough describes what they show without reproducing those values.

## Source notes

- Vault note: `03 - Learning Hubs/Cybersecurity/IAM Project.md`
- Linked notes: `IAM groups.md` and `Block legacy authentication.md`
- Project repository: [Aymen07171/Hybrid-IAM-Security-Lab](https://github.com/Aymen07171/Hybrid-IAM-Security-Lab)

The notes/screenshots substantiate an Entra Conditional Access lab. They do not show an on-premises directory, Entra Connect/Cloud Sync, or federation. The “hybrid” integration remains to be evidenced before describing this as a verified hybrid deployment.

