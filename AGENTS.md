# Pairlo working instructions

The user's global coding instructions apply in addition to these project rules.

## Start here

1. Inspect the working directory, Git branch/status and relevant recent changes. If Git is not initialised, report that accurately.
2. Read [README.md](README.md), [PROJECT_STATUS.md](PROJECT_STATUS.md), [BACKLOG.md](BACKLOG.md), and [DECISIONS.md](DECISIONS.md) before meaningful work.
3. Inspect existing implementation patterns before choosing architecture or adding dependencies. Preserve user work.

## Product authority

- The user owns product direction and final UX decisions. Engineering implementation choices belong to the implementing agent within approved scope.
- New explicit user decisions take precedence over older documentation and Figma. Surface material conflicts rather than inventing product requirements.
- Figma is a reference and may be refined to support approved behaviour. See the source and precedence notes in PROJECT_STATUS.md.
- The POC targets desktop only. Mobile/tablet responsive layouts are out of scope. Delivery includes hosting for partner review on the user's existing domain when its details are supplied.
- Do not expand the private permanent-placement POC into teams, contract staffing, billing or integrations without approval.

## Documentation maintenance

- The user-created https://github.com/rexchoicn/pairlo is the public, docs-only project hub. Read [START_HERE.md](START_HERE.md) and [DOCS_SYNC.md](DOCS_SYNC.md) for its scope and publication workflow. App source remains in the full local workspace, not this docs repo.
- Update PROJECT_STATUS.md in the same working tree whenever scope, implementation status, verification, blockers or next steps change. Keep it concise and current.
- Keep BACKLOG.md as the mutable list of implementation work, deferred inputs and follow-ups. Use stable item IDs, clear next actions and dependencies; providing a sample spreadsheet is not a blocker for starting implementation.
- DECISIONS.md is append-only. Add a dated, uniquely numbered entry for a significant product or engineering decision. Do not rewrite or remove earlier entries. Reversals must reference the superseded decision in a new entry.
- Distinguish accepted requirements, proposed designs, implemented work and verified behaviour. Never present a plan as implemented.
- Keep README.md as the entry point for setup and project documentation.
- Every final response must include either **Documentation updated:** with the changed files, or **Documentation update not required.**
- Keeping the documentation hub current is part of completing meaningful Pairlo work under the user's standing docs-only publication request. Reconcile remote edits, prepare/redact the explicit document allowlist, publish with an expected-head check and verify remote contents. If blocked, report that GitHub is behind. A read-only task or explicit instruction not to publish takes precedence. Never treat discussion/proposed Figma changes as accepted implementation.

## Verification and publishing

- Run checks appropriate to the change. Distinguish automated, manual browser and device verification.
- Account isolation and private CV access remain required even though a consent/retention management feature is deferred for the POC.
- Keep credentials out of source, documentation and chat. Use the authenticated connection or local secret configuration.
- Documentation-only GitHub updates have the standing authorization above. Do not commit/push application source, merge, deploy, release, change access or submit other work unless the current task authorizes it.
