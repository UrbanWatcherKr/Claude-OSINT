---
name: offensive-osint
description: Operational OSINT arsenal for authorized external reconnaissance and bug-bounty work. Use when Codex needs concrete probe paths, public dorks, secret regexes, wordlists, read-only validator guidance, endpoint scoring, identity-fabric endpoints, cloud bucket candidates, vendor fingerprints, email security checks, GraphQL/OpenAPI discovery references, package registry leak hunting, or the bundled secret_scan.py helper. Pair with osint-methodology for scope, evidence, confidence, and reporting discipline.
---

# Offensive OSINT

## Operating Posture

Use this skill for concrete references that support authorized reconnaissance. Preserve the upstream Claude-OSINT content and boundaries:

- Confirm authorization before target-specific activity when scope is unclear.
- Keep activity reconnaissance-focused. Do not provide exploitation chains, post-exploitation steps, malware, persistence, or credential misuse.
- Use read-only validators only for liveness/scope confirmation, and only when the engagement permits validation.
- Treat discovered credentials and PII as sensitive evidence. Redact in outputs and never use secrets for modification, creation, deletion, sending, or access beyond read-only proof.
- Prefer passive or low-volume checks unless the user explicitly authorizes deeper active probing.

## Reference Loading

The full upstream Claude arsenal is preserved in `references/claude-skill.md`. It is large, so search before loading.

Useful searches:

```powershell
Select-String -Path references\claude-skill.md -Pattern "Swagger|GraphQL|secret-regex|read-only validators|HudsonRock|DMARC|origin discovery|Kubernetes|GitHub code-search|Self-Test"
```

Read the reference for:

- Swagger/OpenAPI, GraphQL, SAML, M365, Okta, Entra, ADFS, and OIDC discovery paths.
- Secret regex catalogs, dorks, endpoint scoring, attack-path hints, and severity examples.
- Cloud bucket permutations, vendor fingerprints, CI/CD and container/Kubernetes exposure references.
- Email security checks, breach lookup workflows, public SaaS dorks, package registry leak hunting, and sector notes.
- Copy-paste probe examples, while adapting them to the user's authorized scope and local environment.

## Bundled Helper

Use `scripts/secret_scan.py` for deterministic local scanning of captured text or files. It is stdlib-only and emits JSONL.

Examples:

```powershell
Get-Content .\sample.txt | python .\scripts\secret_scan.py
python .\scripts\secret_scan.py .\captured-file.txt
```

Run the helper only on local files or user-provided/captured material that the user is authorized to assess. Redact matches in conversational summaries unless the user explicitly needs local-only raw output.

## Workflow

1. Verify the target and authorization context from the conversation, or ask a concise scope-check question.
2. Search `references/claude-skill.md` for the relevant arsenal section and load only that section.
3. Return concrete references as scoped, copyable guidance. Include detectability and read-only caveats when applicable.
4. Pair with `$osint-methodology` when the user needs prioritization, confidence grading, evidence packaging, or report writing.
5. Stop at reconnaissance guidance if the request moves into exploitation, unauthorized access, or harmful credential use.
