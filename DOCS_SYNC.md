# Shared documentation and publication

Last updated: 2026-11-09 (Asia/Singapore).

## Purpose and scope

[rexchoicn/pairlo](https://github.com/rexchoicn/pairlo) is the user-created **public documentation hub**, on `main`. It supports business/design discussions and shared project context. This publication contains the root project Markdown and a restrictive docs-only `.gitignore`. Application source, migrations, configuration/secrets, CVs, snapshots, generated data, local artifacts and screenshots are excluded.

The application workspace remains local and is not initialized as a Git working tree. Publishing documents through the connected GitHub API creates remote commits without versioning or deploying the application. A future source-code repository/baseline is separate work. This repo is not a runnable copy of Pairlo and is not a database or source-code backup.

## Source of truth and publication

- `START_HERE.md`: concise product/business orientation and reading order.
- `PROJECT_STATUS.md`: current implementation, verification, blockers and next action.
- `BACKLOG.md`: mutable work with stable IDs.
- `DECISIONS.md`: append-only accepted rationale; reversals are new entries.
- `PRODUCT_REFINEMENT.md`: proposals, dependencies and priorities, kept distinct from accepted scope.
- `FIGMA_CANDIDATES.md`: editable design links and baseline/implementation boundaries.
- Supporting README, instructions, architecture, testing, hosting, UAT and partner-review Markdown retain their purposes.

The full local Markdown remains the operational source. Public copies are generated with deterministic redaction of personal account emails, private project/account identifiers, unique deployment identifiers and personal filesystem roots. The hub is useful project context, not an unredacted operational runbook. Real applicant data and credentials must never be added to the public documents.

## Update workflow

The user's request to keep this hub current authorizes documentation-only updates after meaningful Pairlo work. Treat publishing the relevant documents as part of completing the task, unless the user requests a read-only task or explicitly says not to publish. This does not authorize source-code pushes, releases, deployments, migrations, access changes or sending messages.

1. Read the current local status/backlog/decisions and the remote `main` head. Inspect remote changes before preparing an update. A change made elsewhere must be reconciled into local documents; never overwrite newer remote edits blindly.
2. Update the relevant local Markdown for actual product/implementation truth. Append significant accepted decisions with a dated unique ID. Distinguish implemented, tested, browser-verified, proposed and pending work.
3. Run `node scripts/prepare-docs-sync.mjs` in the full local workspace. It prepares only an explicit Markdown allowlist plus a docs-only `.gitignore`, checks links, redacts account details and rejects credential-like strings. Review the manifest under ignored `.local/docs-sync/`. It makes no network calls and does not publish.
4. Use the connected GitHub tools to create a tree based on the inspected remote tree, create one documentation commit, and advance `main` with the expected head SHA and no force. Preserve unrelated remote files; never replay a rejected update without reading the new head.
5. Read back the remote branch/tree and compare each published blob SHA with the prepared manifest. If the result is uncertain, reconcile the actual head before retrying. Confirm publication in the final response only after readback succeeds.

If access, review or synchronization fails, keep the local changes and explicitly report that GitHub is behind. Do not mark documents synchronized merely because local edits or a commit object were created.

## Collaboration boundaries

This is task-driven publishing. No background watcher, scheduled automation or automatic import of other chats/Figma changes is configured. A business discussion becomes a decision record only after the owner accepts it and the result is brought into the project records. Agents working only in the docs repo must mark implementation claims as pending engineering verification until checked against the full local workspace.

The default branch contains the latest published context; GitHub commit history records earlier snapshots. A reader or connected chat may need a fresh retrieval rather than relying on previously read content. Repository visibility/access is not changed by this workflow.
