# Pairlo: shared project context

Last updated: 2026-11-09 (Asia/Singapore).

This is the short starting point for product/business conversations. Read [PROJECT_STATUS.md](PROJECT_STATUS.md) for current implementation, [PRODUCT_REFINEMENT.md](PRODUCT_REFINEMENT.md) for proposals, [DECISIONS.md](DECISIONS.md) for accepted decisions and [BACKLOG.md](BACKLOG.md) for the next work. The [GitHub documentation hub](https://github.com/rexchoicn/pairlo) is the shared published copy.

## Product direction

Pairlo is a recruitment SaaS for recruiters making permanent placements. Its two core jobs are helping a recruiter find suitable candidates for a role, and helping a candidate find suitable roles. Companies, people, opportunities and recruiting history should feel connected, with clear next actions and enough hierarchy to skim quickly.

The first reviewers are based in Hong Kong. The current private POC targets desktop. The product owner decides business direction and UX; engineering owns implementation within approved behavior. The market focus is an initial testing context, not evidence of a validated segment or pricing strategy.

## What exists now

- Working CRM/ATS: companies, shared people/candidate identity, contacts, roles, candidate-role applications and recruiting history.
- Conversations, follow-ups, Tasks/Today, recorded submissions, feedback, interviews, offers and placements.
- Fee agreements with company defaults and role overrides; explicit placement basis/percentage or fixed fee; manual invoice/payment/guarantee records. These record outside actions rather than sending money or invoices.
- Excel templates, validation/review/import for companies, contacts and candidates, with explicit reuse and no overwriting of existing saved fields; search, reporting, defaults and separate private drafts.
- Supabase authentication/database/private CV storage. Individual accounts are isolated. Shared agency/team data is not implemented.
- A protected hosted POC at [pairlo-poc.vercel.app](https://pairlo-poc.vercel.app). Its UI is older than the latest local refinements. Final-domain and actual partner acceptance remain pending.
- A realistic **fictional** review portfolio: 12 companies, 60 candidates, 30 roles, 180 applications, 140 conversations and eight placements. Its six-month chronology is sample data, not six months of actual customer usage.

Current technical evidence: the latest local runtime checkpoint has 236 passing tests across 26 files, plus the recorded build/type/format and browser/database checks. Those are prior checks; a documentation publication does not rerun them. [TESTING.md](TESTING.md) distinguishes verification dates, limits and remaining acceptance.

## Current design checkpoint

The current focus is the unified person-profile pilot and stronger visual hierarchy. Candidates and company contacts can share one identity with distinct employer and business-contact relationships. The pilot leads with identity, opportunities, meeting context and the next follow-up. Charcoal actions/dark navigation stay quiet; coloured chips make company/person/role links recognizable.

The user moved candidate design review into Figma. Ten editable candidate screens and a shared UI Kit are available:

- [Candidate screens / start with Summary](https://www.figma.com/design/5ZDRXCDj97A00pgYFniMnN/Recruiter-SaaS?node-id=471-2).
- [UI Kit](https://www.figma.com/design/5ZDRXCDj97A00pgYFniMnN/Recruiter-SaaS?node-id=468-70).
- [Design handoff and scope](FIGMA_CANDIDATES.md).

The wider profile rollout is pending review. Figma changes do not automatically change the app.

## Proposed next work

Review the candidate profile first. Then clarify company/person relationships, role criteria and candidate facts before implementing matching. Potential matching must explain evidence, missing information and practical constraints rather than inventing a precise score from weak data. Smart matching, reverse recommendations and structured career/education/experience editing are **proposals**, not implemented features or accepted detailed specifications. No nationality-based ranking rule has been accepted.

Contract staffing, teams/agency administration, subscriptions, integrations, automatic email/WhatsApp sending, AI parsing and mobile/tablet remain outside the current POC. Business model, target customer segment, pricing, success metrics and the exact matching policy still need product decisions; this document does not assume answers.

## Keeping conversations aligned

Use this prompt when starting a business/design discussion:

> Read START_HERE.md, PROJECT_STATUS.md, PRODUCT_REFINEMENT.md, BACKLOG.md and the newest DECISIONS.md entries from rexchoicn/pairlo. Separate implemented behavior, accepted decisions and proposals. Discuss the product/business question using that context. At the end, list any explicit owner decisions and open questions so they can be recorded; do not describe suggestions as accepted or implemented.

The repository is the shared record, not a live transcript. Re-read the latest default-branch files when freshness matters. Decisions made in another chat or directly in Figma must be captured explicitly before they become project truth. [DOCS_SYNC.md](DOCS_SYNC.md) explains the update and publication process.
