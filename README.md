# Pairlo

A private recruitment CRM and applicant-tracking POC for permanent placements. The full POC targets desktop and eventual partner review on the user's GoDaddy-managed domain.

Batches 1–6 implement the private CRM/ATS, conversations/tasks, submission-through-placement records, Excel imports, global search, analytics and personal defaults. Batch 7 has deployed the first protected Vercel release at [pairlo-poc.vercel.app](https://pairlo-poc.vercel.app). Its signed-in hosted checkpoint passed, including an approved task save/reload, draft guard, saved records, private CV download and supporting features. Final-domain setup and actual partner review remain pending. The full app workspace is not Git-initialized; the separate [public documentation hub](https://github.com/rexchoicn/pairlo) contains project records, not application source. Evidence and limits are in TESTING.md.

## Start with the project context

Read [START_HERE.md](START_HERE.md) for the product goal, current checkpoint and a prompt for business/design conversations. Then use [PROJECT_STATUS.md](PROJECT_STATUS.md), [PRODUCT_REFINEMENT.md](PRODUCT_REFINEMENT.md), [BACKLOG.md](BACKLOG.md) and the newest [DECISIONS.md](DECISIONS.md) entries. The current candidate review is in [Figma](FIGMA_CANDIDATES.md).

GitHub is a docs-only hub. Public copies omit personal account details; [DOCS_SYNC.md](DOCS_SYNC.md) explains ongoing publication and cross-chat handoffs. The setup instructions below apply to the full local application workspace, which is not included in this repository.

## Run locally

Requires Node.js 24.x and npm. Verified locally with Node 24.18.0; the Vercel project and package engine use the same major version.

```powershell
npm ci
Copy-Item .env.example .env.local
```

Set `VITE_SUPABASE_URL` and `VITE_SUPABASE_PUBLISHABLE_KEY` in `.env.local` using the project's API URL and publishable key. The current workspace already has this ignored file configured. Do not put a service-role key, secret API key, database password or personal access token in frontend configuration.

```powershell
npm run dev
```

Open http://127.0.0.1:5173 in a desktop browser. Sign in with an approved email/password account. The development server uses a strict port and will fail if 5173 is already in use.

For visual feedback, open that URL in ChatGPT's built-in browser, select Annotate, select an element/area, save the comment and send it in this chat. Vite development does not apply the hosted CSP that currently conflicts with annotations. Delivery from full local Pairlo is verified: four Companies/sidebar annotations arrived on 6 November. Local Pairlo uses the same hosted Supabase records as the public POC.

Keep the development server running while reviewing. Closing a browser tab does not stop the server. Stop it with Ctrl+C in its owning terminal, or ask the agent to stop the Pairlo local preview and verify port 5173 is released. Other projects can use different ports; a port is occupied only while a process listens on it. Running servers, watchers and browser tabs consume memory/CPU, so stop previews that are no longer needed. Starting the app again uses npm run dev; no records are removed by stopping this frontend server.

```powershell
npm run check
npm run format:check
```

`check` runs TypeScript, unit tests and the production build. `npm run preview` serves the built `dist` locally on port 4173. Neither command deploys the application.

The first local review revision groups navigation under Daily work, Recruitment and Insights & data. Settings sits above the profile at the bottom; clicking the profile opens its Sign out option. Set the sidebar name through Settings → Edit profile name. This saves display metadata, independently of preferences and account access.

Companies, Candidates, Tasks, Placements, saved imports and Drafts show matching-result counts and sortable data headings. Click again to reverse direction; arrows and gray active styling show the order. Fixed-option table values use chips, including status/stage, priority, industry, location/notice choices and record type. Free-text names, pay, numbers and dates retain their normal presentation. Existing semantic status colours remain. Tasks has a directory table; Today and record pages keep compact task lists.

Roles now uses selectable cards with a preview on the right. Cards show company/title, location and optional work arrangement, age since added, active Screening/Submitted/Interview counts, a relevant next-step indicator, priority and recent update age. Select a card to see its candidate brief, budget, other applicable indicators and three recent active candidate updates. Find candidates is the primary action; the full pipeline and record remain accessible. Selection, search, filters and compact Recent activity/Priority/Role name sort buttons use the URL, preserving context through reload and related journeys. Work arrangement and next-step indicator filters use the same grayscale chips. Existing roles remain visible unless filtered; the sample review can focus on Active and a company.

Companies, Candidates, Roles, Tasks and Placements keep text search visible and open their filters from an icon. Options are visible grayscale chips with multiple selections: choices within one group match any selected option, while different groups work together. An empty group includes every option; there are no separate Any/All chips. Reset beside a group heading clears only that group; Reset filters clears every group and text field. Apply confirms the filter choices; Close (×) or Escape discards unapplied changes. Selected chips have a white checkbox with a heavier dark tick. Tasks initially shows Open, but clearing Task status includes all statuses. Expected-pay text remains a text filter with its own Reset. These review revisions are local; the public deployment remains the earlier Batch 7 release.

Breadcrumbs show the ancestor/return link without repeating the current page. Company tabs are Roles, People, Activities and Detail, defaulting to Roles. The company Roles table omits the redundant Company column. Activities pages through recorded application history and company-linked tasks; Detail retains company fields, notes, fee terms and record dates. Old Overview/Terms links still open Detail. Company headers offer Add role as primary and Add people as secondary; Edit company is in Detail. Add people opens the existing company-contact form. New company retains its first-column form width and empty right column. Sidebar Recruitment is ordered Roles → Candidates → Companies → Placements.

The approved neutral appearance now applies throughout the app: dark navigation/primary buttons, a light gray canvas, borderless white panels and outlined cards. Company links and breadcrumbs have no underline; other content links retain subtle underlines. Keyboard focus and grayscale selections remain visible. Purple is reserved for the logo, selected-tab/current-stage indicators and route progress; existing status colours retain their meaning. The development-only demo and its query flag have been removed. Page headings omit introductory subtitles; field help, validation and actual record content remain. This frontend revision is local and built, not deployed.

The unified person-profile pilot is available during development at `/people/:personId/profile-preview`. Open an existing person/candidate and choose Preview new profile, or review [Mina](http://127.0.0.1:5173/people/ed787d8b-285b-424b-ba1e-319d3f61da92/profile-preview?from=%2Fcandidates&section=opportunities). Its sticky header links to active opportunities and recorded meetings; the primary count opens active roles not yet linked to that person. Any existing pair is excluded, including closed/declined history; this is manual discovery rather than fit ranking or an unseen-role count. Opportunity titles are plain headings and the card surface opens the saved opportunity, while company/person chips have independent destinations. Larger type, open recruiting details and a warm follow-up panel vary emphasis. Company chips are blue, people violet and roles mint; Search/Drafts/Imports record-type badges share the palette. Contact-only people show hiring relationships/roles. Meetings use the latest recorded interview per active opportunity, including explicit pending confirmation, with Hong Kong times and no fabricated future schedule. Pilot review supports desktop widths from 1100 px; other pages retain their existing minimum. Existing protected CV flows remain. The full profile stays DEV-only pending review; no deployment or structured-career/matching rollout. See DEC-041–042 and TESTING.md.

Page/form headers are sticky. Record editors put their final Save and secondary Save as draft at the top, with no footer actions or Cancel button. Save as draft permits incomplete fields and persists a private snapshot in Supabase. Resume it from [Drafts](http://127.0.0.1:5173/drafts) under Daily work; discarded drafts can be restored from its Discarded tab. Drafts stay outside live lists, pipelines and analytics. Saving draft edits to an existing record leaves that saved record unchanged until final Save, which still validates the complete record and checks its original version. Unsaved navigation offers Keep editing, Discard changes or Save draft & leave. Refresh/close still warns about changes not yet saved as a draft.

Draft snapshots cover record editors, related recruitment/commercial actions, checked import rows and profile/default editors. Files, CV binaries, passwords and transient errors are excluded. CV upload retains its existing upload/retry flow. For imports, check the workbook before saving a draft; the checked rows and selection can resume without the original file, and require review before confirmation. There is no automatic draft save. Review the retained fictional Northbank Advisory and Adrian Chow drafts without adding them to the live UAT portfolio.

## Supabase setup

Candidates have an optional LinkedIn profile URL on their create/edit forms and a link in Candidate profile. Use an HTTPS LinkedIn personal-profile URL; share tracking/query fragments are removed. It is private candidate data, not part of contact-only views. This records a link without connecting to LinkedIn. Existing Excel templates are unchanged.

The richer fictional UAT portfolio is loaded: 12 companies, 60 candidates with new private CVs, 27 contacts, 30 roles, 180 applications, 140 conversations, 8 placements and 120 tasks across May–November 2026. All 60 new CVs were downloaded and byte-verified after upload; Yuki's previous CV is also retained. Start with Mina's three opportunities or Harbourline's People/Roles tabs. See [UAT_DATA.md](UAT_DATA.md) for review journeys, execution evidence and the guarded seed. Local and hosted Pairlo share these records; frontend review/LinkedIn changes are still local.

The hosted [pairlo-poc project](https://supabase.com/dashboard/project/SUPABASE_PROJECT_REF) is in the Pairlo organization, Singapore (`ap-southeast-1`). Migrations `20261102151158_batch_1_private_workspace.sql`, `20261104081140_batch_2_people_candidates.sql` and `20261104092534_batch_3_roles_applications.sql` are applied. They define approved workspaces, CRM records, tracked private CVs, roles, applications and append-only application events. Generated database types are in `src/lib/database.types.ts`.

For Batch 3 review: set a default fee under Edit company, create a role under Roles, and optionally enter its fee override. Use Find candidates on a role or Link roles on a candidate. Both open the same saved application. Record update changes only that opportunity and appends a dated event; general candidate pay stays separate. Pipeline shows active stages and a separate closed/declined/withdrawn view. Offer is a pipeline stage; record the actual offer decision through the Batch 5 flow below. Contact method Email records contact already made outside Pairlo.

For Batch 4 review: open Today or a candidate and choose Log conversation. Select the linked applications discussed, set each response/stage independently and select only the follow-up tasks you want. General pay/notice changes require the explicit profile checkbox. Saving creates one conversation with linked application events/tasks in one transaction. Candidate Activity and each application's Source conversation link open the same record. Tasks supports create/edit, optional record context, due date/time, priority, completion and reopening. Today shows overdue/due-today tasks and the next seven days using Hong Kong dates. Marking a task done records completion; it does not send messages or advance an application.

For Batch 5 review: use Record submission from a role/application to record a shortlist already sent outside Pairlo. Choose only the applications sent and record the recipient/date. On an application, record Client feedback, Interview arrangements, or Offer and decision. An active application with its latest offer Accepted can create a placement; this closes that opportunity and preserves its outreach response.

Enter the placement's agreed fee-basis description, amount and currency. The role/company percentage is inherited unless a placement percentage or fixed fee is explicitly chosen. Salary months/bonuses are not inferred. Optional guarantee dates/terms are entered per placement. The saved agreement stays fixed when defaults change. Use Payments to record one invoice and multiple payments received outside Pairlo; partial payments update its balance. Correct payment-entry mistakes with a reason while retaining history. Guarantee check-ins/status and their selected tasks remain independent of payment. No invoices, messages or money are sent.

Batch 4 migrations `20261104114518_batch_4_activities_tasks.sql`, `20261104114655_batch_4_activity_event_guard.sql` and `20261104120033_batch_4_workflow_indexes.sql` are also applied. Conversations/outcomes are immutable; task sources are preserved. Later changes use new records instead of rewriting a saved conversation.

Batch 5 migrations `20261104160606_batch_5_submissions_placements.sql` and `20261104163150_batch_5_placement_event_lock.sql` are applied. Structured recruitment/commercial records are append-only; stable request IDs, version checks, owner RLS and transaction triggers protect combined saves.

For Batch 6 review: open Imports and download the Companies, Contacts or Candidates template. Fill the Data sheet from row 2, keep every header and read the Instructions sheet. Import companies first when other rows refer to them. Use .xlsx with plain values, at most 100 data rows and 1 MB per file. Phone cells must stay Text with the full number. Formulas/macros/external links, .xls/.csv files and arbitrary column layouts are not supported.

Checking a file creates no records. Explicit Save as draft can separately persist its checked rows and selection; it does not create an import result or business record. Review row errors and duplicate matches, select eligible rows and explicitly select any existing-person reuse. Confirm only the rows to add. Existing saved fields are kept; a changed match requires another review. Selected rows save together, and an uncertain confirmation retains its exact request for retry. Saved imports link to the canonical records. Original workbooks are not uploaded to storage; confirmed inputs/results remain private in import history. CVs and recruitment history use their existing record flows.

Search workspace opens grouped, paginated global results with canonical return links; phone formatting is ignored for identity matches while other text stays literal. Analytics filters activity by Hong Kong dates/client and explains first-outreach cohorts, distinct shortlist applications, recorded placements and separate currencies. Active-role/follow-up cards show current state. Settings saves market/industry/currency defaults for new forms without editing existing records or placement agreements. Auth email, private workspace mode and disabled data sharing remain fixed.

Batch 6 migrations `20261104172025_batch_6_import_search_analytics_preferences.sql`, `20261104172958_batch_6_import_lookup_guard.sql`, `20261104175337_batch_6_search_phone_matching.sql` and `20261104180149_batch_6_literal_search_queries.sql` are applied. These add private import history/preferences and security-invoker import/search/report functions. The ZIP reader is loaded only when checking a file. Templates in `public/templates` share their headers with `src/lib/import-columns.json`; update and verify both together when changing the format.

For Batch 2 review: open a company, edit its details or add a contact. Search existing people before creating another identity. Reuse a contact through “Open candidate profile,” then add preferences and a CV under “CV & files.” PDF/Word files up to 5 MB are supported; the browser walkthrough used a synthetic PDF. Salary entries retain their recorded currency/period and the pay filter searches that text. Preview buttons keep unfinished forms open. See TESTING.md for actual evidence and limitations.

The first tester is created, email-confirmed and approved. Public signup and anonymous sign-in are disabled. There is no public signup or automatic invitation/password-reset email flow.

Migration `20261106085821_candidate_linkedin_url.sql` is also applied. It adds the optional private profile link and extends `save_person_record`, preserving a saved link when older clients omit the field. Generated database types and rollback-only LinkedIn/isolation checks match the hosted schema. The current frontend review changes are local, not redeployed.

Migration `20261106170812_private_form_drafts.sql` is applied, bringing the schema to fourteen migrations. It adds private, versioned form snapshots and recoverable discard/completion transitions through security-invoker RPCs. Approved-owner RLS and a 2 MB snapshot limit apply; live business schemas and access rules are unchanged. Generated types and the rollback-only `supabase/tests/drafts_isolation.sql` checks match the hosted schema.

Migration `20261107065054_role_workbench.sql` brings the schema to fifteen migrations. Roles have an optional On-site/Hybrid/Remote field, initially blank on existing records. Private invoker functions provide complete per-role pipeline counts and a paginated company activity feed. Indicators use recorded recruiting history: no linked candidates, seven calendar days without progress, submitted candidates without a later client step, latest interviews scheduled tomorrow, and active offer-stage candidates. Role-brief edits alone do not reset progress. Dates use Hong Kong time; these are record-keeping indicators. See ARCHITECTURE.md for exact rules and TESTING.md for evidence. No UAT business records were changed during this UI review and no frontend deployment occurred.

To provision another explicitly authorized tester:

1. The workspace owner creates an email/password user in Supabase Authentication, confirms the email and handles credentials privately with the tester.
2. An operator approves that user's exact Auth UUID using privileged SQL:

   ```sql
   insert into public.workspace_members (user_id)
   values ('REPLACE_WITH_AUTH_USER_UUID')
   on conflict (user_id) do nothing;
   ```

3. The tester signs in normally. An Auth account alone does not grant access to business records.

For recovery, the tester contacts the workspace owner. The owner manages recovery in Supabase and handles the replacement credential privately. SMTP and self-service recovery are not configured or verified. Do not send passwords through chat. To revoke workspace access, set that membership's `disabled_at = now()`; RLS rejects subsequent company/CV requests even with an existing session.

`supabase/config.toml` provides local development defaults, including closed signup. It is not a downloaded copy of hosted Auth settings. A Docker-based local Supabase stack has not been started or verified. Future schema changes should use new CLI-generated migration files, applied through the approved database connection, then regenerate types and rerun isolation tests. Do not replay the existing migration against the already configured hosted project or run a remote database reset.

## Hosting

`npm run build` produces static output in `dist`. The source includes an SPA fallback (`public/_redirects`) and security/CSP headers (`public/_headers`) for hosts that support those files. Another host requires equivalent routing and headers in its native configuration. These headers are not automatically applied by Vite's development/preview server.

The `pairlo-poc` project in `PRIVATE_VERCEL_SCOPE` (ID `prj_GUrYXO2LtARlSgbAeJApO4q6YDAz`) now has a READY production deployment, `PRIVATE_DEPLOYMENT_ID`. Its exact build is [pairlo-1qgc6fmah-PRIVATE_VERCEL_SCOPE.vercel.app](https://pairlo-poc.vercel.app); the stable provider URL is linked above. Vercel Authentication retains its existing `all_except_custom_domains` setting. Pairlo separately requires the approved Supabase account; a connector review link does not grant workspace access.

`vercel.json` supplies Vercel's native SPA rewrite and security/no-index headers, following the [Vite hosting guidance](https://vercel.com/docs/frameworks/frontend/vite). `.vercelignore` restricts future CLI source uploads to frontend build inputs. The first release used that same explicit boundary and excluded local configuration, test artifacts and database/project documents. HTTPS, headers, deep-link responses, templates and the signed-in desktop checkpoint are verified on the provider host. The GoDaddy hostname/DNS, final-domain Auth URLs and partner access/review remain pending. See HOSTING.md for exact state, domain steps and update/recovery instructions. Keep existing DNS records and Vercel protection intact.

## Project documentation

- [START_HERE.md](START_HERE.md): concise business/product context, current checkpoint and discussion prompt.
- [DOCS_SYNC.md](DOCS_SYNC.md): docs-only GitHub scope, redaction, reconciliation and verified publication workflow.
- [PROJECT_STATUS.md](PROJECT_STATUS.md): current state, approved scope and delivery plan.
- [BACKLOG.md](BACKLOG.md): mutable work, inputs and follow-ups with stable IDs.
- [PRODUCT_REFINEMENT.md](PRODUCT_REFINEMENT.md): page-by-page proposals, priorities and review sequence, including the approved local profile pilot checkpoint; remaining scope is proposed.
- [FIGMA_CANDIDATES.md](FIGMA_CANDIDATES.md): editable candidate screens/UI Kit, exact review links, component inventory, verification and design-to-code boundaries.
- [DECISIONS.md](DECISIONS.md): append-only product and engineering rationale.
- [ARCHITECTURE.md](ARCHITECTURE.md): implemented frontend, database and access boundaries.
- [TESTING.md](TESTING.md): commands, actual verification evidence and remaining checks.
- [UAT_DATA.md](UAT_DATA.md): realistic fictional portfolio, guarded seed and loading checkpoint.
- [HOSTING.md](HOSTING.md): deployed build, access boundaries, domain setup and future updates/recovery.
- [PARTNER_REVIEW.md](PARTNER_REVIEW.md): desktop walkthrough and feedback checklist.
- [AGENTS.md](AGENTS.md): working instructions.
- [Figma reference](https://www.figma.com/design/5ZDRXCDj97A00pgYFniMnN/Recruiter-SaaS?node-id=375-2): all nine pages reviewed; newer explicit user decisions take precedence.
