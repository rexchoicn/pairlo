# Decision log

Append-only. Add new entries at the end using the next DEC-NNN identifier and the actual decision date. Do not edit, reorder or delete earlier entries. A change or correction must be a new entry referencing what it supersedes.

The latest applicable accepted decision governs. "Planned" implementation details are not evidence of completed work.

## DEC-001 | 2026-10-30 | Private invite-only POC

Status: Accepted by the user.

Decision: The first milestone follows the Figma handoff's private, invite-only POC with isolated per-recruiter records. Shared team databases, agency administration, paid subscriptions and public registration are deferred.

Reason: Validate the core recruiter workflow before expanding the SaaS scope.

## DEC-002 | 2026-10-30 | Permanent placements first

Status: Accepted by the user.

Decision: Support permanent placements in the POC. Contract staffing is a future extension, not current implementation scope.

Reason: The reference primarily models permanent placement fees; contract staffing adds different commercial and operational workflows.

## DEC-003 | 2026-10-30 | Maintain status and append-only decisions

Status: Accepted by the user; documentation created.

Decision: Keep PROJECT_STATUS.md as the continually updated current-state document and DECISIONS.md as an append-only historical log. README.md links the project documentation; AGENTS.md instructs future agents to maintain it.

Reason: Preserve project continuity and rationale across iterations without leaving current-state documentation stale.

## DEC-004 | 2026-10-30 | Record submissions without sending email

Status: Accepted by the user; application implementation planned.

Decision: Recruiters record that they have already sent a candidate shortlist outside the app. Do not connect an email service or send email/CVs in the POC. Refine the reference flow and labels to describe record keeping accurately.

Reason: Useful recruitment history does not require an email integration at this stage.

## DEC-005 | 2026-10-30 | Company fee defaults with role overrides

Status: Accepted by the user; application implementation planned.

Decision: A company has a default recruitment fee percentage. Each role may override it. Fees vary by agreement; there is no universal percentage.

Open details: Salary/compensation basis, guarantees, invoice timing and exceptional commercial terms need representative agreements. The Figma 20% annual-base example is illustrative.

## DEC-006 | 2026-10-30 | Confirmed Excel import

Status: Accepted by the user; application implementation planned.

Decision: Provide a downloadable Excel template, accept completed Excel uploads, validate the contents and present them for review. Create business records only after explicit confirmation.

Reason: Recruiters need to bring existing information into the workspace with a chance to catch mistakes first.

Open details: First supported entities, partial-import behaviour and duplicate merge/update policy. These must be resolved without silently overwriting existing records.

## DEC-007 | 2026-10-30 | No additional privacy-management feature for POC

Status: Accepted by the user; baseline security implementation planned.

Decision: No additional consent/retention/deletion management requirements or mandated hosting region were supplied for the POC. Do not add a compliance-management workstream at this stage. Retain the handoff's private accounts, database account isolation, confidential candidate information separation and private CV/file access.

Reason: Keep the POC focused while preserving its already-defined access boundaries. This decision is not a statement of legal compliance.

## DEC-008 | 2026-10-30 | Figma may evolve with approved behaviour

Status: Accepted by the user.

Decision: Treat Figma as a design/workflow reference. Improve flows where needed to deliver approved behaviour, including the submission-recording change. Surface material product choices to the user.

Reason: The intended recruiter experience takes precedence over copying illustrative screens literally.

## DEC-009 | 2026-10-30 | Supabase backend direction

Status: Selected by the user; account and connection pending.

Decision: Use Supabase for authentication and PostgreSQL, with private Storage planned for CVs and attachments. Retain React/Vite/TypeScript as the proposed frontend from the handoff.

Connection evidence: A Supabase plugin was found available in the coding app and suggested on this date. It is not yet installed or connected. No Supabase account, project, migrations or resources have been created by this task.

Reason: The backend supports the relational record model and the POC's private account boundaries.

## DEC-010 | 2026-10-30 | Preserve placement fee history

Status: Engineering decision; application implementation planned.

Decision: When a placement is created, preserve the agreed compensation, fee basis and effective percentage used for that placement. Later company defaults or role edits must not silently recalculate historical placement fees.

Reason: Company defaults and role overrides are mutable; historical commercial records need stable, explainable amounts. Any explicit correction workflow remains to be designed.
## DEC-011 | 2026-10-30 | Desktop-only POC

Status: Accepted by the user; implementation planned.

Decision: Implement the Figma-based recruiter workflow for desktop only. Mobile/tablet responsive layouts are not required for the POC.

Supersedes: The earlier desktop-first plus responsive desktop/tablet implementation and acceptance plan in PROJECT_STATUS.md, inherited from Figma.

Reason: Focus the first reviewable product on the desktop experience used by the initial testers.

## DEC-012 | 2026-10-30 | Hosted partner review is a POC deliverable

Status: Accepted by the user; deployment planned.

Decision: The POC includes both the functioning desktop application and hosting on the user's existing GoDaddy-managed domain, or a chosen subdomain, so the user's partner can try and review it. The user will supply the domain later.

Consequences: Hosting is authorized delivery scope. The exact hostname and host are unresolved. Deployment requires a tested build, HTTPS, correct Supabase authentication URLs and private tester access. No deployment or DNS changes have occurred.

Reason: A locally running application alone does not satisfy the intended partner review.

## DEC-013 | 2026-10-30 | Separate mutable backlog for work and inputs

Status: Accepted in response to the user's request; BACKLOG.md created.

Decision: Track implementation tasks, missing inputs and deferred follow-ups in BACKLOG.md using stable IDs and current statuses. It is editable. PROJECT_STATUS.md remains the concise current-state summary; DECISIONS.md remains append-only.

Includes: The user will provide a representative spreadsheet later. Track it without blocking initial implementation. Also track the future domain details, test-user emails and commercial agreement examples.

Reason: Tasks and inputs change frequently and need actionable next steps, while historical decisions should remain intact.

## DEC-014 | 2026-10-30 | Pairlo organization and Hong Kong testers

Status: Organization and tester location confirmed by the user; region is a planned engineering choice, not a provisioned resource.

Decision: Use the Supabase organization named Pairlo. The initial testers are based in Hong Kong. Plan Singapore (ap-southeast-1) for a new Supabase project, subject to availability and resource/cost checks.

Evidence: Supabase plugin installation is independently confirmed, but organization/project calls return Unknown tool. Organization ID, existing projects and usable authenticated access have not been verified. Do not mistake installed tools for a working connection.

Reason: Establish the intended account boundary and a regional default before creating resources.

## DEC-015 | 2026-10-30 | Provision the Supabase POC project

Status: Engineering setup completed and remotely verified.

Decision: Create pairlo-poc in the user-confirmed Pairlo organization, using Singapore (ap-southeast-1) for the Hong Kong testers. The organization is on the Free plan. The project reference is SUPABASE_PROJECT_REF; organization ID is whzvhemdxathxkvcfnks.

Verification: After the user reconnected, organization/project lookups succeeded and showed no existing projects. Project creation succeeded; a subsequent project lookup returned ACTIVE_HEALTHY. Public tables and migrations were verified empty. The application schema, RLS, invite-only authentication flow and private CV configuration have not yet been implemented.

Updates: The connection blocker recorded as evidence in DEC-014 is resolved. The provisioned project now realizes its planned region; earlier entries remain historical.

Reason: Establish the isolated POC backend environment before application implementation.

## DEC-016 | 2026-11-02 | Execute Batch 1

Status: Requested by the user; application slice implemented, final acceptance check pending.

Decision: Implement the first delivery batch: the desktop shell, private approved-user authentication, initial schema and isolation rules, a persisted Company create/list/detail flow, private file boundaries and hosting preparation. Later recruitment batches remain planned.

Verification boundary: Company create/reload/filter/draft browser checks and live database isolation tests pass. A signed-out navigation loop was fixed and covered by router regression tests; the full signed-in sign-out/sign-in browser checkpoint remains open. This entry does not mark the full POC complete.

Reason: Establish a real authenticated vertical slice before expanding the recruiter workflow.

## DEC-017 | 2026-11-02 | Static React app with database-enforced approval and ownership

Status: Engineering choice implemented and tested.

Decision: Use React/Vite/TypeScript, native CSS and React Router loaders/actions, with a typed Supabase browser client. Use an operator-managed workspace_members approval table, owner-scoped companies and a private candidate-cvs bucket with user-UUID folder policies. Do not grant browser clients approval-management rights or ship privileged keys.

Implementation: Migration 20261102151158_batch_1_private_workspace.sql is applied to pairlo-poc. Company drafts retain a stable UUID for safe retry after a lost response. Private CV policies are established; upload/download UI is deferred to Batch 2.

Reason: Keep the static frontend small in architectural scope while enforcing account boundaries independently of the UI. Retry handling prevents duplicate creation without silently overwriting a different record.

## DEC-018 | 2026-11-02 | Owner-provisioned tester accounts for the private POC

Status: Operational engineering choice implemented with user participation.

Decision: The owner creates and confirms authorized email/password Auth users and handles credentials privately. An operator grants workspace approval separately. The first tester supplied by the user is provisioned and approved. Public signup and anonymous sign-in are disabled and independently verified. Recovery currently directs the tester to the owner; no SMTP, invitation-email or self-service reset flow is configured.

Updates: Realizes DEC-001's private access requirement and resolves the initial entry approach in INPUT-007. This is account access, not recruitment email sending under DEC-004. Additional testers require explicit authorization and the same approval boundary.

Reason: Give the initial tester real access without depending on unconfigured email delivery or exposing credentials to the agent.

## DEC-019 | 2026-11-02 | Prepare Vercel hosting without deployment

Status: Engineering preparation completed and read back; no publication.

Decision: Use the existing authenticated Vercel team PRIVATE_VERCEL_SCOPE to prepare an empty pairlo-poc Vite project, ID prj_GUrYXO2LtARlSgbAeJApO4q6YDAz. Configure npm ci, npm run build, dist output and the two public Supabase environment variables. Keep default preview sign-in protection enabled. Track native SPA rewrites and security headers in vercel.json.

Updates: Advances DEC-012's hosted-review delivery scope. No deployment, Git connection, commit, push, domain attachment or DNS change was made. Hosted deep links, headers, Auth URLs and approved partner access must be checked when deployment is authorized.

Reason: Prepare the available hosting account during Batch 1 without publishing an unverified build. The existing GoDaddy domain can remain with its registrar.

## DEC-020 | 2026-11-04 | Execute Batch 2

Status: Requested by the user; implemented and verified.

Decision: Complete the approved core CRM batch: company editing, contacts, canonical shared people and candidate profiles, directory filters, private CV upload/download, related-record previews and draft protection. Roles/applications, commercial fee defaults and later recruitment workflows remain Batch 3 onward.

Verification: TypeScript, 45 unit tests, build/format and both live rollback-only SQL suites pass. Browser checks cover identity reuse, company/candidate/contact edits, contact confidentiality, filters/return context, previews and real authenticated PDF byte upload/download. Anonymous file/metadata HTTP requests are rejected. No deployment, commit or push was made.

Updates: Batch 1 acceptance referenced as pending in DEC-016 was subsequently verified on 2026-11-02, as recorded in TESTING.md. This entry does not mark the complete hosted POC delivered.

## DEC-021 | 2026-11-04 | Separate shared identities from confidential candidate context

Status: Engineering implementation of approved Person reuse and privacy requirements.

Decision: Keep name/email/phone on an owner-scoped people row. Link company-specific position/business notes through company_contacts, and keep confidential recruiting notes/pay/preferences on candidate_profiles. Contact queries and previews do not fetch candidate profiles or files. Reuse is explicit; exact normalized email/phone uniqueness prevents silent duplicate identities within an account.

Implementation: save_person_record is an atomic security-invoker RPC. Composite owner/entity foreign keys reject cross-account links; original timestamps detect stale edits; stable draft IDs and payload comparisons make creation safe to retry. The migration is 20261104081140_batch_2_people_candidates.sql.

Reason: One person can be known in different contexts without duplicating identity or placing confidential recruiting information into a business contact view.

## DEC-022 | 2026-11-04 | Track private CV uploads as immutable file versions

Status: Engineering implementation; browser-verified with a synthetic PDF.

Decision: Accept PDF/Word DOC/DOCX files up to 5 MB in the private candidate-cvs bucket. Create pending metadata first; use immutable owner/person/file-UUID paths and a per-candidate content hash. Retry the same file against its existing metadata, verify existing bytes after an uncertain upload, and mark ready after success. Expose incomplete uploads for retry, not as confirmed downloads.

Access: Storage policies require the visible candidate metadata and active owner approval. Client rename/overwrite/delete policies are removed. Downloads use authenticated requests and byte/hash validation; no public or long-lived signed URL is created. This refines DEC-017's initial user-folder boundary into a tracked candidate-file boundary. No real prior CV objects existed to migrate.

Limits: Basic type/signature/size validation is not malware scanning. Word formats are implemented; the manual byte round trip used PDF. File removal/retention management and durable offline drafts are not added to this batch.

Reason: Preserve account privacy and make interrupted uploads retryable without anonymous access, untracked binary paths or duplicate copies.

## DEC-023 | 2026-11-04 | Preserve recorded candidate compensation text

Status: Engineering choice within the Figma reference; implemented.

Decision: Retain current/expected candidate salary as text including its stated currency, range and pay period. Label the directory pay filter as a text contains search. Do not invent conversions, a universal monthly basis or numerical range comparisons from free-form values.

Reason: The reference permits entries such as a salary range and users may record different currencies/periods. Vacancy-specific compensation and final commercial rules remain in their later approved batches. A structured compensation model can supersede this choice when its product rules are agreed.

## DEC-024 | 2026-11-04 | Execute Batch 3: roles and canonical applications

Status: Requested by the user; implemented. Verification evidence is maintained in TESTING.md.

Decision: Add company-owned permanent-placement roles, same-company hiring contacts, nullable company fee defaults and role overrides, and one canonical application per candidate/role pair. Candidate and role entry points open that same application. Response, stage, vacancy-specific salary and notes are independent of other opportunities and general candidate expectations.

Implementation: Migration 20261104092534_batch_3_roles_applications.sql is applied. Nullable percentages preserve explicit zero and permit two decimal places; no universal percentage or fee amount is inferred. Role status and priority are separate. Five active Figma stages are retained; Closed/Declined/Withdrawn records remain accessible separately. Offer is a stage, not placement acceptance. Daily tasks/multi-role activity, submission records and placement agreements remain later batches.

Reason: Deliver the approved ATS foundation while preserving each opportunity's identity and commercial context. This realizes DEC-005 for mutable defaults/overrides; historical placement fee snapshots under DEC-010 remain Batch 5.

## DEC-025 | 2026-11-04 | Transactional application history and stable retries

Status: Engineering choice implemented and covered by live rollback-only database checks.

Decision: Use security-invoker bulk-link and application-update RPCs, same-owner composite references, immutable role/company and application identity, integer edit versions and trigger-generated append-only application events. Clients cannot directly forge or rewrite event rows. Retrying the same event ID requires the same payload; duplicate role/person links return the canonical record without adding history.

Dates: Each event has an entered Hong Kong date and a separate server recording timestamp. Future event dates are rejected. History sorts by event date, then recording time. Recording a backdated update still updates the current application state; it does not replay or recompute state from historical dates.

Reason: A saved response and its history must succeed together, survive uncertain-response retries and reject stale writes without losing the current draft. New applications to closed roles are rejected, while existing canonical links stay accessible.

## DEC-026 | 2026-11-04 | Execute Batch 4: conversations, tasks and Today

Status: Requested by the user; implemented. Verification evidence is tracked in TESTING.md.

Decision: Implement the Figma candidate conversation flow with selected existing applications, independent outcomes, optional per-outcome follow-up tasks, explicit confirmation of general expected-pay/notice changes, candidate Activity and canonical conversation detail. Add standalone task create/list/detail/edit, completion/reopening, related-record previews and the Today work queue. New roles are linked through the existing role/candidate flow before their outcomes are recorded.

Boundaries: General conversation notes, application outcome notes and candidate profile expectations are separate. Only the explicit profile checkbox applies general expectation changes. Saved conversations/outcomes are immutable; corrections are subsequent records. Task completion means the recruiter completed an external action; it does not send communication or progress an application. Placements/submissions/import remain later batches.

Reason: One real discussion should be recorded once while each opportunity and follow-up stays independent, as required by the accepted delivery checkpoint.

## DEC-027 | 2026-11-04 | Atomic conversations and Hong Kong task dates

Status: Engineering implementation of approved Batch 4 behaviour.

Decision: Use an invoker RPC plus insert triggers for atomic activity/outcome/history/task/profile writes. Exact stable-request retries return the saved conversation; stale versions or invalid references reject the entire save. A fresh event is required for each outcome. Standalone tasks resolve related context on the server. Conversation follow-ups retain their original source/application; versioned edits and desired-state completion/reopening prevent stale overwrites.

Dates: Tasks have an optional Hong Kong due date and optional clock time, and general tasks may remain unscheduled. Overdue is based on an earlier Hong Kong date; a same-day time orders the queue but does not make the task overdue before the next day. Today shows overdue/due-today work and a seven-day upcoming view. All counts come from loaded records; pagination remains POC-011.

Reason: Keep combined saves and retries consistent without privileged frontend credentials, and avoid using the agent's/browser's local timezone for Hong Kong testers.

## DEC-028 | 2026-11-04 | Execute Batch 5 with explicit commercial terms

Status: Requested by the user; implementation in progress. Verification is recorded separately in TESTING.md.

Decision: Add manual shortlist records, client feedback, interview arrangements, offers/decisions and placements from accepted offers. Submission records describe actions already performed outside Pairlo. They do not send messages or files. Preserve the canonical candidate-role application and its independent outreach response.

Confirmed by the user: Enter the agreed fee-basis amount and currency; inherit the role/company percentage, with explicit placement percentage or fixed-fee overrides. Enter guarantee start/end dates and terms per placement, without an assumed duration. One invoice per placement with multiple manually recorded payments is sufficient, including partial payments. Payment and guarantee follow-up remain independent.

Consequence: Store an immutable placement agreement and fee-source snapshot. Later company/role changes do not recalculate it. Do not assume 12/13 salary months, bonuses, a universal percentage, tax, refund or replacement rules. Record keeping does not issue invoices or move funds.

## DEC-029 | 2026-11-04 | Transactional recruitment steps and immutable placement ledger

Status: Engineering implementation of approved Batch 5 behaviour; automated and live rollback-only SQL verification passed. Desktop evidence remains in TESTING.md.

Decision: Reuse canonical application events for grouped shortlist items and validated Feedback/Interview/Offer records. Offer decision is independent of outreach response and discussed/general pay. The latest accepted offer on an active Offer-stage application can create one immutable placement; creation closes that application without changing its response. Preserve salary, identity labels, explicit commercial basis/currency and fee-source snapshot. Corrections to the agreement itself remain a later workflow.

Commercial history: Use one invoice with append-only revisions, multiple positive same-currency payment entries and reasoned void entries for data-entry corrections. A correction retains the original record and does not move/refund money. Payments cannot exceed the outstanding balance; refunds, overpayments, credit notes and tax rules remain outside this POC. Guarantee check-ins/status and selected tasks are separate. Recorded version, rather than entered date, determines the latest invoice/guarantee state.

Engineering: Stable IDs/exact payloads, owner/approval RLS and insert triggers keep records/history/selected tasks atomic even through direct Data API inserts. Monetary calculations use exact cents/numeric values, two decimal places and positive half-up rounding. Placement UPDATE permits only trigger-controlled version bumps; the event RPC uses an owner-scoped advisory lock for retries and its insert trigger locks the row/checks the version. All functions are invokers. Sources on generated tasks cannot be changed; completion does not update payment or guarantee state.

Verification update (2026-11-04): The Batch 5 implementation described in DEC-028/029 passed its signed-in desktop checkpoint with the user's approved labelled fixtures, in addition to 102 unit tests and five rollback-only SQL suites. TESTING.md records exact evidence and limitations; PROJECT_STATUS.md holds current completion status. No deployment or publishing occurred.

## DEC-030 | 2026-11-04 | Execute Batch 6: import and supporting features

Status: Requested by the user; implementation and verification in progress. The user confirmed companies, contacts and candidates as the first import entities, with create/reuse and no overwriting. Selected valid-row confirmation is the stated working rule while the remaining question is pending.

Decision: Provide a separate .xlsx template per entity with Data and Instructions sheets. Import companies before dependent contacts/employer links. Preview without saving records; explicitly select reuse rows and confirm eligible rows. Saved imports contain canonical result links. A fresh match check and atomic trigger protect the selected rows; stable request IDs/exact payloads protect uncertain retries. Account isolation and private candidate fields remain required.

Supporting features: Add paginated global search and server-counted period/client analytics, with literal search text and explicit cohort/counting definitions. Personal market/industry/currency preferences prefill new company/candidate/placement forms; existing records and commercial agreements stay unchanged. Keep the POC private, desktop only and without message/file sending, team administration or deployment.

Engineering: Reuse native controls, existing forms/guards/previews and local Figma assets. Parse the bounded template format using a pinned ZIP library and native XML parsing; reject formulas/macros/external links and ambiguous identities. Retain typed salary text, explicit percentages and separate currencies. No original workbook is stored in Supabase; confirmed input/results remain private in the import history.

Confirmation update (2026-11-04): The user accepted all three import choices, including selected valid rows while invalid/duplicate rows stay skipped. They also explicitly approved the retained labelled Batch 6 fixture imports and the preference test/restoration. This resolves the pending-answer status above.

Verification update (2026-11-04): Batch 6 passed 121 unit tests, TypeScript/build/format, all six rollback-only SQL suites and the signed-in desktop checkpoint. The import reuse namespace error was fixed before browser confirmation. Search preserves literal text alongside normalized phone matching. Preferences were restored and original records remained unchanged. TESTING.md holds evidence/limits; PROJECT_STATUS.md holds current completion status. Hosting and partner access remain Batch 7; no deployment or publishing occurred.

## DEC-031 | 2026-11-05 | Execute Batch 7 hosting with explicit acceptance boundaries

Status: Requested by the user; first Vercel release deployed. Final-domain, signed-in hosted and actual partner acceptance remain in progress.

Decision: Deploy the tested local frontend to the already prepared pairlo-poc project in PRIVATE_VERCEL_SCOPE. Pin package/project Node to the locally verified 24.x major. Restrict uploads to frontend build inputs, exclude local configuration/artifacts/database/project documents, and add no-index response/robots instructions alongside the existing CSP/security headers. Keep the existing Vercel Authentication policy and the independent Supabase Auth/operator approval/owner-RLS/private-file boundaries.

Release: Deployment PRIVATE_DEPLOYMENT_ID is READY, with stable provider URL https://pairlo-poc.vercel.app. The API assigned this first deployment to production despite its omitted target; actual returned state is recorded rather than calling it a preview. Source is the unversioned local workspace (82-file source-manifest hash in HOSTING.md), with no Git initialization, commit or push. No new schema migration was needed.

Access: A short-lived connector review link was used privately to render hosted sign-in without disabling Vercel protection; it does not authenticate a recruiter. The user enters their existing password privately for hosted business verification. Do not infer a GoDaddy hostname or partner recipient. A separately approved partner account starts empty under the accepted isolated-record model; do not expand this into shared team data. The existing custom-domain exception still leaves application Auth/RLS required.

Verification boundary: 121 automated tests/typecheck/build/format and dependency audit pass. Five SQL suites reran; the commercial rerun did not execute because connector confirmation expired. Its prior pass is historical, not a fresh result. Hosted HTTPS/headers/deep links/templates/public config, anonymous API/CV denial and signed-out browser rendering pass. HOSTING.md and PARTNER_REVIEW.md describe the remaining domain/Auth/account and persisted walkthrough steps; those steps are not marked complete without actual evidence.

Reason: Deliver a concrete hosted POC within the authorized scope while preserving private access, excluding local secrets and distinguishing a successful deployment from final partner acceptance.

Consent and verification update (2026-11-05): The user reports hosted sign-in and explicitly approved retaining one task named “Batch 7 hosted persistence check (POC test).” This authorizes that fixture without asking again. The controlled exact-build and primary-host sessions still return to sign-in after documented browser recovery/fresh navigation; the user's successful session has not been independently located. The primary URL opening in this chat's right panel is queued until the chat is visible. The fixture has not been created, and no hosted persistence pass is claimed. Continue through the privately signed-in panel or distinguish a user-run browser test from agent verification.

Hosted checkpoint verification update (2026-11-05): The user completed private sign-in in the primary-host native panel; engineering independently observed Companies and created/reloaded the approved task f0454295-ba39-4350-b6b0-f108aadf6ae4 through the hosted UI. This resolves the earlier session/fixture pending state. Draft guarding, saved CRM/ATS/commercial/import views, matching private PDF bytes, read-only duplicate import checking, phone search, analytics and restored defaults pass; browser warning/error logs are empty. Final readback confirms only the approved task was added, with original records/agreements/defaults unchanged. No source change or redeployment was needed. TESTING.md distinguishes this hosted task-write/read checkpoint from earlier full local/live SQL write flows. Final-domain/partner acceptance and the commercial SQL rerun remain pending.

## DEC-032 | 2026-11-06 | First annotated sidebar and directory revision

Status: Requested by the user through four delivered local Pairlo annotations. Implemented locally; automated checks and signed-in browser verification passed. No publishing or deployment is authorized by this review task.

Decision: Replace sidebar dots with related SVG icons and group navigation into Daily work, Recruitment, and Insights & data. Place Settings directly above the bottom profile. Show the saved account name rather than private-workspace/email text; its native popover contains only Sign out. The user explicitly chose Tiffany for now. Save display_name as account display metadata through the signed-in SDK after workspace approval; never use user-editable metadata for authorization. Provide an independently guarded name editor under Settings so name saves do not partially combine with versioned preferences.

Directory behavior: Companies, Candidates, Roles, Tasks, Placements and saved imports show the number of matching results and working sort dropdowns. Keep sort/search/filter state in the URL and preserve it through return links. Clear filters keeps the chosen sort. Preserve existing defaults: recently updated for CRM/roles, earliest due for Tasks, latest start for Placements and recently confirmed for imports. Missing dates stay last in either direction. Imports sort on the server before pagination; other directories retain their current loaded-row boundary (POC-011). Global search's grouped results and nested detail histories retain their existing presentation.

Companies filters: Keep text search visible, with only a filter icon/badge for the dropdown filters. Open Industry/Relationship/Location in the shared native dialog. Apply the draft together; Cancel/Escape discard it and return focus; Reset clears its fields when applied. Other directories retain their existing filter presentation because the user extended only comments 2–3 to every listing page.

Verification: 136 tests across 17 files, TypeScript/build/format, and signed-in local count/order/filter/return-context checks passed. Tiffany persists after reload; profile popover has only Sign out. No business records/preferences or schema/access policies were changed. Public hosting remains the earlier Batch 7 release; TESTING.md records the evidence and limits.

## DEC-033 | 2026-11-06 | Grayscale chip filters and sorting from column headings

Status: Explicit second local review request; implemented and verified locally. Supersedes the sort-dropdown and filter-presentation portions of DEC-032. The earlier sidebar/profile behavior remains accepted. No deployment/publishing is authorized by this local review task.

Decision: Replace filter dropdowns with visible, wrapping grayscale checkbox chips in the directory filter dialog. Multiple choices within a group match any selected choice; groups combine. Apply saves the draft to repeated URL parameters, Cancel/Escape discard it, and Reset restores defaults when applied. Extend the shared dialog to Companies, Candidates, Roles, Tasks and Placements so options are visible in the same way. Keep text search inline and expected-pay text as a text filter. Existing one-value URLs continue working; missing Task status means Open, while an explicit All choice is preserved separately.

Sorting: Remove sort dropdowns on Companies, Candidates, Roles, Tasks, Placements and saved imports. Each data-column heading is a real button; clicking another heading starts its useful default direction, and clicking the active one reverses direction. Paired arrows, pointer/hover/focus clues and a brief instruction identify sortable headings. The active heading alone has a gray background, a directional arrow and aria-sort. Keep URL sort/return context and nulls-last behavior. Give Tasks a directory table with data headings and its existing action buttons; Today and record-level task lists keep their compact presentation. Add a visible Placement start-date column so its existing default ordering has a visible active heading.

Data semantics: Candidate pay/notice sort as recorded rather than inferring periods or converting amounts. Placement fees sort by currency then numeric amount. Imports use allowlisted database columns before pagination, including records-added ordering via the existing trigger-generated JSONB array and PostgreSQL's documented array ordering. No schema change, new dependency, permission change or business-record write is needed. Large loaded-directory limits remain POC-011.

Verification: TypeScript, 145 tests across 18 files, production build and formatting passed. Signed-in browser checks cover column toggles/aria state, chip OR/AND matching and reloads, draft cancellation/reset, keyboard selection/Escape/focus, numeric role counts, task defaults/undated-last order, and live import counts in both directions. Full-page screenshots record the local result; TESTING.md holds boundaries. Public hosting remains the previous Batch 7 build.

## DEC-034 | 2026-11-06 | Empty filter groups, individual resets and simpler record headers

Status: Requested through the third local review and six annotations; implemented locally, with automated and signed-in browser checks passed. Supersedes DEC-033's Any/All chip and reset-to-default behavior. No deployment or publishing is authorized by this task.

Filters: Remove the separate Any/All choices. No selected chips means no restriction. Put a neutral Reset text button beside every group heading and text-field label; it clears only that draft key. Reset filters clears all draft groups/fields. Apply confirms the draft, while Cancel/Escape discard it. Tasks keeps its initial Open default, but explicitly clearing Task status means all statuses, represented by status=all. Existing OR within groups, AND across groups, search/sort URLs and grayscale presentation remain unchanged.

Record presentation: Remove the company-link arrow, current-page breadcrumb labels and duplicated company/candidate header descriptions. Keep existing ancestor/return destinations. New company omits its two explanatory panels while retaining the existing first-column form width and empty right grid column.

Company actions: Primary Add role and secondary Add people open the existing company-linked role/contact forms with the relevant Roles/People return context. They replace duplicate section actions. Add people records a business contact; it does not invite workspace users. Keep Edit company accessible in the Company details panel and retain the Terms editing link.

Verification: TypeScript, 145 tests across 18 files, production build and formatting pass. Browser checks cover isolated group resets, cancellation/Apply/Escape, unrestricted task status, retained company form width, role/contact prefill and return context, ancestor breadcrumbs and retained candidate profile fields. Screenshots and precise limits are in TESTING.md. No persistent records, schema/access policies, dependencies or hosted deployment were changed.

## DEC-035 | 2026-11-06 | Optional private candidate LinkedIn profile URL

Status: Explicit user request; implemented locally and in the hosted database. Automated/live database checks pass; browser field and invalid-host validation verified. No frontend deployment is authorized by this task.

Decision: Add optional linkedin_url to private candidate profiles, candidate create/edit forms and candidate detail. Accept HTTPS LinkedIn personal-profile links, normalize regional/share URLs and remove tracking query/fragment data. Enforce a 500-character limit and a database constraint. Use a safe external link with noopener/noreferrer. Do not add LinkedIn authentication, scraping, messaging or contact-view exposure; existing Excel templates are unchanged.

Compatibility: Extend the existing security-invoker save_person_record RPC. An explicit null clears the value; omission by older clients preserves it. Existing owner/approval RLS, stale checks and atomic person/profile saves remain in force. Migration 20261106085821_candidate_linkedin_url and generated types match the hosted schema.

Verification: 155 tests/18 files, TypeScript/build/format, rollback-only LinkedIn persistence/compatibility/isolation and CRM/supporting suites pass. Browser verification does not claim a newly persisted URL. TESTING.md records evidence and limits.

## DEC-036 | 2026-11-06 | Realistic fictional six-month UAT portfolio

Status: Requested by the user; generated and verified in an isolated rollback-only database run. Actual tester refresh and private CV uploads remain pending the connector/dashboard execution checkpoint; not claimed loaded.

Decision: Replace old POC-labelled sample journeys with a coherent fictional recruiter portfolio across May-November 2026. Prepare 12 companies, 60 candidates, 27 hiring/business contacts, 30 roles, 180 independent applications, 140 conversations, 8 placements, 120 tasks and 60 new PDF CVs. Fill meaningful briefs, compensation/preferences, assessments, contacts, employer links, structured recruitment/commercial history and varied follow-ups. Keep stable core IDs/import links where applicable. Preserve the old CV as a previous copy.

Execution boundary: Keep this operator-only dataset under scripts/uat, separate from migrations and product flows. Back up the original synthetic rows locally, require their exact snapshot, replace only those known test histories in a transaction, and create the new graph through normal authenticated tables/workflow functions. Do not disable triggers/RLS, change other accounts/preferences/Auth, or create a general reset feature. Historical event dates give the portfolio chronology; immutable placement creation timestamps remain their actual insertion times.

Synthetic identity: Use fictional names/businesses, reserved example email/web domains and non-routable sample phone values. Label CV footers as fictional UAT documents. Leave LinkedIn empty rather than inventing live profiles. No external messages, invoice sending or payment processing.

Checkpoint: The full isolated dataset passes and rolls back. The real replacement connector confirmation expired twice, including after the user said Ready, so engineering opened the dashboard SQL editor for direct review/private sign-in. Loading, 60 private CV uploads/byte checks and populated-browser review are still required. UAT_DATA.md is the mutable execution checkpoint; this decision does not authorize frontend deployment.

Loaded UAT checkpoint (2026-11-06): The user completed private dashboard sign-in and explicitly approved running the staged refresh. Its editor content matched the tested source, the dashboard warning was accepted under that approval, and the result returned UAT refresh committed. The loaded graph passes read-only checks for all prepared counts and canonical relationships. All 60 new CVs were uploaded/downloaded through Pairlo and independently matched to their source hashes/sizes; the retained previous CV makes 61 ready files with zero incomplete uploads. Preferences and access policies are unchanged. Browser connections, contact confidentiality, placement ledgers/guarantees, Today and six-month Analytics pass. LinkedIn browser save/reload/clear passed; the temporary synthetic link is removed. Focused CSS corrected monetary wrapping exposed by the richer data. TESTING.md records evidence and limits. This completes the requested UAT refresh; the frontend remains local and was not deployed.

## DEC-037 | 2026-11-07 | Review neutral appearance in a contained coded demo

Status: The user requested a calmer visual direction and asked about a demo before applying it everywhere. A local Company detail demo is implemented and verified for review. The exact palette and global rollout remain proposed, not accepted.

Direction: Use dark navigation and charcoal primary CTAs, a light gray page canvas, borderless white main panels and transparent contact cards with light gray outlines. The demo keeps purple on the brand mark and selected-tab underline; neutral underlined links retain an affordance without colouring every contact. Preserve the approved layout, navigation, profile, forms and record behaviour.

Engineering: Reuse the existing Company record and shared Workspace; scope the CSS behind development mode, an exact Company detail route and appearance=neutral. Company tabs retain the query; leaving the record restores the existing appearance. Do not persist a theme preference or duplicate records/UI. No data write, dependency, schema change, production activation or deployment is required for the demo.

Review checkpoint: TypeScript/build/format pass. Signed-in browser checks cover card layers, tab switching, preview/Escape/focus, profile menu, reload and isolation from the normal appearance. Colour-pair contrast calculations and before/after screenshots are recorded in TESTING.md. Collect user annotations and settle the colour roles before implementing a wider shared-style pass. This is a light-content visual direction with dark navigation, not approval for the deferred dark-mode feature.

## DEC-038 | 2026-11-07 | Adopt the reviewed neutral palette throughout Pairlo

Status: Explicitly accepted by the user after reviewing the coded demo: implement it sitewide. Implemented locally and included in the production build; no deployment is authorized by this request. Supersedes DEC-037's proposed-only palette and Company-only development gate.

Decision: Use dark navigation and charcoal primary CTAs, a light gray canvas, borderless white main panels/tables/pipeline columns, and neutral outlined cards inside them. Keep content links subtly underlined, keyboard focus visible and native selection states grayscale. Reserve purple for the logo and selected-tab/current-stage/route-progress indicators. Retain meaningful status colours rather than changing recruitment/payment/task semantics. Preserve existing layouts and workflows.

Engineering: Promote the palette into existing shared CSS tokens and component rules; scope the sidebar's dark tokens locally so its popover and navigation remain legible. Remove the prototype stylesheet and its route/query/development activation logic. Normal routes and production builds now share the approved appearance, without a theme preference, new abstraction/dependency, backend change or duplicate UI. Neutralize the disclosure chevron asset to match.

Verification: TypeScript, 155 tests across 18 files, production build and formatting pass; final CSS-only refinements passed build/format again. Seventeen signed-in page/state checks, native selection/filter/sort/preview/focus checks and seven inspected screenshots support the local rollout. TESTING.md records exact evidence and unverified signed-out/device boundaries. No records/preferences were saved and no commit, push or deployment occurred. The public frontend remains the previous Batch 7 release until a publishing request.

## DEC-039 | 2026-11-07 | Sticky form saves and separate persistent private drafts

Status: Explicitly requested through five annotations. The user confirmed a separate Drafts page, excluded from live lists/pipelines/reports, and draft edits that preserve the saved record until final Save. Implemented locally with the hosted private-draft migration applied; no frontend deployment authorized. Supersedes DEC-038's company/breadcrumb underlines and the earlier Cancel/footer/in-memory-only form behavior; the neutral palette and established business validation remain accepted.

Presentation: Make page/record/form headers sticky. Move form final Save to the header, add secondary Save as draft, and remove footer actions/Cancel buttons. Filter dialogs use labelled Close (×)/Escape to dismiss unapplied choices. Remove introductory page-title subtitles throughout, retaining field help, validation and record content. Company links and breadcrumbs have no underline. Selected grayscale filter chips show a white checkbox with a darker, heavier tick.

Draft behavior: Explicit Save as draft persists incomplete work without completing a business record. A separate searchable, sortable, 20-row Drafts page under Daily work provides resume plus recoverable Discard/Restore. Status is draft/discarded/completed and is independent of invoice/recruitment status. Existing-record snapshots preserve original versions/timestamps; final Save performs normal validation/stale checks, writes the business record, then completes its draft. Unsaved navigation offers Save draft & leave, Keep editing or Discard changes. This does not introduce automatic saving.

Engineering: Reuse shared RecordForm/Workspace/loaders and explicit registered form state, not copied business tables or a second live-record status. Add forced approved-owner RLS, no anonymous/delete grants, immutable identity/route, bounded JSONB snapshots, optimistic versions and stable retry IDs through invoker RPCs. Restore snapshots before form initialization; validate route/schema/field shapes. Company creation joins the existing shared form pattern. No dependency is added. Business save and draft completion are separate requests: a confirmed write followed by failed completion offers Finish save/Open saved record and never automatically replays the confirmed write.

Boundaries: Cover record, related recruitment/commercial and profile/default editors. Import drafts preserve checked rows/selection/uncertain request data and require another review before confirmation; original workbooks are not uploaded. Files/CVs, credentials and transient UI/errors are excluded. CV upload retains its existing guarded flow. Live records, reports, account isolation and private CV access remain unchanged.

Verification: TypeScript, 201 tests/21 files, production build and formatting pass. The rollback-only hosted draft suite verifies privacy, approval, ownership, versions/retries, bounded payloads and discard/restore/completion; fixtures roll back. Browser checks cover incomplete company/candidate saves/reloads, existing-company isolation/final Save, nested conversation outcomes/follow-ups, recoverable discard, sticky actions, ticks, links and sort direction. Two active fictional review drafts remain outside the unchanged UAT counts; one conversation draft is recoverably discarded and one company edit completed. TESTING.md records manual import/network/device limits. No commit, push or frontend deployment occurred.

## DEC-040 | 2026-11-07 | Role cards and preview focused on candidate sourcing

Status: Explicit user request with three attached references. Implemented locally and in the hosted schema; no frontend deployment authorized. Supersedes the Roles-directory table presentation and Company tab arrangement in earlier review decisions. Existing manual recruitment, draft and privacy behavior remains accepted.

Product direction: Help recruiters find the information needed to source a candidate for a role. Use role cards beside an inline preview, leading with company/title, location/arrangement, age, active pipeline counts, next-step indicator, priority and update age. Primary Find candidates opens the existing manual talent pool; brief/budget/pipeline and canonical applications remain available without duplicating every saved detail on the card. Recent candidates are not a fit ranking. No AI score, automated matching or external action is introduced by the layout reference.

Confirmed rules: Add optional On-site/Hybrid/Remote and leave existing roles blank. Meaningful progress includes candidate linking, role-related conversations/updates/submissions/feedback/interviews/offers and completed linked tasks; editing the role brief alone does not reset the seven-day clock. Implement the reference's Sourcing needed, No recent progress, Awaiting feedback, Interview upcoming and Offer in progress indicators. Normally progressing roles have no warning. Use entered Hong Kong event dates; distinguish them from actual saved-update timestamps. Card age says Added because opening/reopening history is not recorded.

Indicator detail: Count active applications independently of declined/withdrawn/closed history. Feedback waits use the latest recorded submission and clear after a later client step, with resubmission starting a fresh wait. Tomorrow means the latest saved interview schedule, including pending confirmation, without claiming attendance. Suppress active-recruiting warnings on closed/on-hold/briefing roles. Preserve all applicable signals in the preview; a card prioritizes tomorrow's interview, feedback, offer, sourcing, then stalled progress, or the matching selected indicator filter. Existing-application roles do not receive the new-role sourcing signal solely because their active count is zero. Exact rules are in ARCHITECTURE.md.

Navigation/presentation: Company tabs are Roles, People, Activities and Detail, defaulting to Roles; keep fees and saved company information in Detail, with legacy Overview/Terms URLs mapped there. Company Roles omits the redundant Company column. Recruitment sidebar is Roles/Candidates/Companies/Placements. Fixed-option table values use chips; free-text/quantities/dates remain ordinary text. Keep the neutral palette and meaningful status colours. Card selection, search, filters and compact sorting preserve URL context; no sort dropdown is restored.

Engineering: Reuse native React/CSS/controls, existing candidate linking and versioned saves. Add a nullable constrained role column, an invoker server summary for complete pipeline counts, and an invoker exact-count/20-row company feed under existing owner/approval RLS. Preview reads fetch only three recent active candidate names/titles/stages and the hiring-contact name. Company Activities combines canonical application-history/task entries while omitting candidate profile notes/pay/files and general conversation bodies. No dependency, credential or access expansion is added.

Verification: TypeScript, 216 tests/22 files, build/format and live rollback-only workbench SQL pass. SQL covers indicators, arrangement persistence, 1,001-candidate counts, deterministic paging and owner/unapproved/disabled/anonymous denial. Browser checks cover card/keyboard/reload/filter/sort, sourcing/return context, arrangement field/unsaved guard, company tabs/activities and representative table chips. TESTING.md records limits. The fictional portfolio is unchanged, all existing arrangements remain blank, and the local review remains open. No commit, push or frontend deployment occurred.

## DEC-041 | 2026-11-09 | Unified person-profile pilot before rollout

Status: Explicit user authorization to implement the first profile pilot, relationship chips and stronger hierarchy, then open it locally for review. Implemented locally; user acceptance and wider rollout remain pending. This does not approve the remaining PRODUCT_REFINEMENT.md proposals or a deployment.

Product: One contextual profile presentation for a candidate, hiring contact or both. Lead with identity, saved position/employer and one primary action; group opportunities, relationships, conversations and private CVs into useful sections. Contact-only people show company relationships and their hiring roles without empty candidate sections. Employment and business-contact relationships are distinct, optional and combined under the same company when both apply. Static statuses remain quiet; navigable company/person/role chips use a restrained brand tint, entity icon, trailing arrow, hover/focus and no underline. Keep the approved dark sidebar, gray canvas and charcoal primary buttons. Initials provide identity recognition without required photos.

Pilot boundary: Use a development-only `/people/:personId/profile-preview` route, linked from existing person/candidate pages without replacing their default destinations. Explicit full-profile reads reuse the existing authorized candidate loader only when a candidate profile exists; company/contact summary projections remain unchanged. Preserve private CV access and guarded file selection. Explore roles opens the existing manual role linker, not a fit ranking. Contextual return links retain the originating company/person/section. No new schema, structured career editor, fabricated availability, inferred fit/interest, external AI processing, UAT refresh or integration.

Verification: TypeScript, 226 tests/24 files, production build and formatting pass. Unit/API tests cover relationship identity, safe navigation, authorization/data minimization and lookup failures. Signed-in browser checks cover Mina's dual-role layout, Dennis's contact-only hiring view, Company People/candidate entry points, opportunities/activity/return context, manual role linker, keyboard chip focus and private CV download matching the original SHA256. TESTING.md records the transient implementation-time HMR reload and verification limits. No business data, drafts or preferences were saved during this walkthrough; no Git initialization, commit, push or deployment.

## DEC-042 | 2026-11-09 | Actionable profile hierarchy and entity colours

Status: Explicit user refinement of the local profile pilot. Supersedes DEC-041's single-tint relationship styling and its generic Explore roles label; the full-profile rollout remains pending user review. No deployment is authorized.

Interaction: Role-opportunity titles are plain headings. The card surface opens the saved candidate-role opportunity; independent company and person chips keep their own destinations. Use native links with a stretched hit area and keyboard focus rather than nested links or JavaScript-only row handlers.

Hierarchy: Keep active opportunities and the next recorded interview reachable from the sticky identity header. Replace a generic discovery CTA with a factual count of active roles not already linked to this person; any existing pair, including closed/declined history, is excluded. Call these roles to explore, without claiming unseen/new or fit-ranked results. Open the same filtered manual picker; a zero count leads to current opportunities. The meeting entry uses the latest interview schedule per active opportunity, with Hong Kong time and explicit confirmation state; superseded dates cannot become the next meeting. Add a contextual Meetings view for those saved schedules. No calendar integration, new meeting record type, inferred availability or matching algorithm.

Visual direction: Company blue, person/candidate/contact violet, role mint, task amber, placement/commercial rose; use saturated text on pale fills, icons and labels. Shared entity links and existing Search/Drafts/Imports type badges use the same tokens. Status/urgency colours retain separate meaning. Increase identity/section/card-title size and distinguish related spacing from section spacing. Vary white, open and warm surfaces so sections do not all have equal weight. Keep charcoal primary actions and the dark sidebar. The pilot's desktop minimum is 1100 px; this does not introduce a mobile layout.

Verification: TypeScript, 236 tests/26 files, build/format pass. New exact-count/anti-join, paging, rescheduling, timezone/invalid-date and contact-data-boundary cases pass. Read-only SQL confirms 15 eligible roles, 2 active opportunities, 0 upcoming/2 past schedules for Mina. Signed-in browser checks verify the matching 15-role picker, card-surface navigation, independent person chip, sticky entries, recorded past schedules and shared entity colours. TESTING.md records future-meeting/browser and desktop limits. Saved data/schema and hosted frontend are unchanged; no Git initialization, commit, push or deployment.

## DEC-043 | 2026-11-09 | Editable candidate baseline in Figma

Status: Explicit user request to work in Figma, use page 459:4 for the UI Kit and 459:2 for screens in file 5ZDRXCDj97A00pgYFniMnN. The user corrected the initial Roles wording to Candidates. Baseline creation is complete; design acceptance, wider profile rollout and automatic synchronization are not implied.

Scope: Mirror the latest local candidate/profile pilot from DEC-041–042 using native editable Figma layers. Include Summary, Opportunities, Relationships, Activity, Meetings and CV & files, plus the directory, filter dialog and add/edit forms. Build shared colours, typography, spacing and reusable components on the supplied UI Kit page. Preserve earlier wireframes and compatible existing foundations. Fictional UAT records illustrate the design; no real CV document or authentication state is exported.

Implementation: Ten 1440 px desktop frames, 76 main components/eight variant sets, 137 new explicitly scoped variables and 11 new Inter text styles. Reuse seven compatible prior text styles and the established layout/white tokens. Add a screen index and 67 prototype navigation hotspots. Semantic entity colours/charcoal actions and the stronger profile hierarchy remain as approved in DEC-042. Matching remains factual manual discovery, without inferred scores or new candidate criteria.

Verification and boundary: Programmatic editability/style/token/bounds checks and rendered visual reviews pass, with exact evidence/limits in FIGMA_CANDIDATES.md and TESTING.md. Add candidate is structurally checked; Present-mode manual clicks and user acceptance remain pending. Temporary capture/bootstrap assets were removed. This is a design review baseline: visual form/file/filter actions do not write records, Figma edits do not update code, and no Code Connect setup, library publication, app rollout, schema/data change, Git initialization, commit, push or deployment occurred. Accepted future refinements must be recorded and implemented separately.

## DEC-044 | 2026-11-09 | Public documentation hub for shared project context

Status: The user created https://github.com/rexchoicn/pairlo and explicitly requested publication of project Markdown so business/design chats and other readers can share current status, decisions and direction. Connected metadata confirms the repository is public and initially empty, with main as the default branch. This authorizes document publication and ongoing scoped documentation updates; it does not authorize publishing application source or deploying.

Decision: Use START_HERE.md as the concise orientation and retain separate current status, mutable backlog, append-only decisions, proposals, design handoff and supporting implementation/verification notes. Publish the explicit root Markdown allowlist with personal account identifiers redacted and a docs-only Git ignore policy. Preserve the full local operational records. App code, configurations/secrets, CVs, snapshots and generated/local artifacts are excluded. The local app remains outside a Git working tree; a source-control baseline is separate work.

Maintenance: Update relevant local documents as part of meaningful work, reconcile newer remote edits, prepare/validate the sanitized allowlist, publish on main using an expected-head check and read back blob hashes before claiming synchronization. The user's request establishes ongoing docs-only publication authorization unless a later instruction restricts it. Failures must be reported as GitHub behind, not hidden by a local-completion claim. No unattended watcher, scheduled automation or cross-chat ingestion is introduced; accepted decisions from other discussions/Figma must be brought into the records explicitly.

Verification boundary: GitHub publication is complete only after remote commit/ref/content readback. Runtime checks remain the prior 236-test checkpoint; this docs-only task does not retest or change the application, database or hosted frontend. DOCS_SYNC.md defines the repeatable process and TESTING.md records the actual publication evidence.

## DEC-045 | 2026-11-10 | Preferred candidate roster with right-side selection preview

Status: Explicit owner selection of Option B as the visual **direction for further Figma iteration**, with a requested narrowed candidate list and contextual details on the right when a row is selected. The updated prototype remains subject to owner review before implementation; this entry does not authorize code rollout, data migrations or deployment.

Direction: Prefer a dense, company-led candidate roster over oversized cards or an initial grid. Keep candidate name/current title/employer with company monogram, years of experience where actually known and key practical icon metadata scannable in the left list. A selected row receives restrained brand styling; the right preview supplies richer identity, practical facts, active opportunities, follow-up and a full-profile entry. Search/filter/sort remain accessible outside the split view.

Figma checkpoint: The [Option B frame `511:2236`](https://www.figma.com/design/5ZDRXCDj97A00pgYFniMnN/Recruiter-SaaS?node-id=511-2236) was edited in place; A/C, V2 and original candidate baseline are preserved. Native editable auto-layout and variable-bound paints pass structural overflow/4px spacing checks. Only Mina's selected state is illustrated; row-to-panel dynamic updates are not working product behaviour. Experience values and some sample employers are invented visual examples, not recorded verified candidate data. Private recruiting notes/CVs and explicit authorized full-profile access remain separate. No schema, runtime, production or matching changes were made.
