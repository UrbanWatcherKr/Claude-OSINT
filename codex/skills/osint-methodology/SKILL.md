---
name: osint-methodology
description: Structured OSINT methodology for authorized external reconnaissance, attack-surface assessment, bug-bounty recon planning, asset graph discipline, confidence/severity grading, evidence handling, reporting, identity-fabric mapping, breach correlation, geolocation, attribution, and investigation workflows. Use when Codex needs to plan, scope, triage, document, or report an OSINT or external recon engagement, especially when authorization, evidence quality, detectability, or deliverable structure matters.
---

# OSINT Methodology

## Operating Posture

Use this skill for methodology, planning, triage, evidence discipline, and reporting for authorized OSINT and external attack-surface work. Keep the original Claude-OSINT posture intact:

- Confirm scope before acting against a third-party target unless the user has already stated ownership, written authorization, an in-scope bug-bounty target, or a formal engagement.
- Stay in reconnaissance and investigation. Do not move into active exploitation, post-exploitation, malware, credential misuse, or lateral movement.
- Treat sensitive data carefully. Do not paste real credentials, session tokens, API keys, unique pivots, or private PII into cloud services.
- Prefer passive or low-detectability collection by default. Document any active probing assumptions, limits, and detectability.
- Label assertions with confidence: `TENTATIVE`, `FIRM`, or `CONFIRMED`.

## Reference Loading

The full upstream Claude skill is preserved in `references/claude-skill.md`. Load it when the user needs detailed methodology, templates, or domain-specific guidance.

Use targeted search before loading large sections:

```powershell
Select-String -Path references\claude-skill.md -Pattern "scope check|Confidence Levels|External Red-Team Recon Pipeline|identity fabric|bug bounty|Client Deliverable|Self-Test"
```

Read the reference for these tasks:

- Engagement setup, authorization checks, time budgeting, and scope boundaries.
- Asset graph modeling, confidence upgrades, severity rubrics, and evidence schemas.
- Identity-fabric mapping across Entra, Okta, ADFS, Google Workspace, SAML, and M365.
- Breach-to-identity correlation, attribution, cryptocurrency tracing, geolocation, and media forensics.
- Bug-bounty submissions, client deliverables, executive summaries, and reproduction packages.

## Workflow

1. Restate the engagement type and scope. If authorization is unclear, ask a single concise scope-check question before giving target-specific actions.
2. Choose the appropriate methodology section from `references/claude-skill.md` and load only the needed parts.
3. Produce structured outputs with confidence, evidence, timestamps, and assumptions.
4. When concrete probe paths, dorks, regexes, or helper scripts are needed, pair this skill with `$offensive-osint`.
5. For reports, separate operator evidence from client-facing narrative and keep remediation concrete.

## Output Defaults

For findings, prefer this compact schema unless the user requests another format:

```text
Finding:
  asset_key:
  category:
  severity:
  confidence:
  title:
  evidence:
  remediation:
```

Use UTC timestamps for evidence and state when data is unverified or inferred.
