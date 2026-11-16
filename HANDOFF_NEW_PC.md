# Pairlo — new PC handoff

Prepared: 2026-11-17 (Asia/Singapore). This document is a handoff, not authorization to implement a redesign, reset data or deploy.

## Read this first

**The GitHub repository contains documentation only. Cloning it does not restore the working application.** The latest runnable source has been stored only in the original local application folder, which is not a Git working tree. Transfer the prepared **source ZIP** as well as this document before losing access to the original PC.

- Shared handoff: [HANDOFF_NEW_PC.md on GitHub](https://github.com/rexchoicn/pairlo/blob/main/HANDOFF_NEW_PC.md).
- Source package: `pairlo-source-2026-11-17.zip` — runnable project source, tests, migrations, assets/templates, setup/configuration files and current local Markdown. No environment credentials or dependency/build folders.
- Optional reference package: `pairlo-reference-2026-11-17.zip` — selected historical UAT inputs, original synthetic CV files, verification artifacts, design/source manifests and documentation-sync metadata. This is not required to run the app and is not a fresh database backup.
- `pairlo-transfer-manifest-2026-11-17.json` and matching `.sha256` files describe and verify the packages. The files are exported under `outputs/pc-handoff/2026-11-17/` in the original workspace. That is a **local path, not a cloud download location**: save/copy the ZIPs to your new PC, USB or private shared storage.

The source/reference ZIPs are private transfer artifacts and are **not uploaded to the public GitHub repository**. The source includes unredacted operational documentation; the reference package includes fictional sample records and account-linked technical identifiers. The public Markdown copy is sanitized by the documentation publication workflow.

If you have only the public repo and this handoff, you can continue business/design discussion and Figma work. You cannot run or accurately edit the latest application until the source ZIP or original source folder has been recovered. Do not recreate the application from screenshots under the assumption that the code is in the docs repo.

## Project and implementation checkpoint

Pairlo is a desktop recruitment CRM/ATS for permanent placements, initially reviewed by Hong Kong testers. Help recruiters find suitable candidates for roles and suitable roles for people. Keep identity, employer/business-contact relationships, applications and next actions connected. The owner decides product direction and UX; engineering owns implementation within accepted scope.

The local application already includes companies, people/contacts/candidates, roles, applications, conversations, tasks/Today, submission/feedback/interview/offer records, placements, manual invoice/payment/guarantee history, Excel template imports/review/results, search, analytics, preferences and private saved drafts. Supabase provides authentication, database and private file storage. Email/WhatsApp/invoice/payment actions are recorded, not sent or executed by Pairlo.

The latest runtime refinement is the **development-only person-profile pilot**, with a stronger identity header, counted manual role discovery, active-opportunity/meeting entries and coloured relationship links. It is not a smart-matching engine. The public hosted UI remains the older Batch 7 release. Newer Figma studies have not been implemented or deployed.

Verification baseline: 236 tests in 26 files, TypeScript/build/format and the recorded browser/database checks passed on 9 November. On 11 November the localhost server was restarted and its review route returned HTTP 200. These are historical checks, not proof of a successful new-PC setup. During this handoff, archive integrity and document reconciliation are checked; existing Supabase project metadata reports `ACTIVE_HEALTHY`. The application journeys, cloud row counts, backup coverage and Figma canvas have not been freshly re-tested on 17 November.

## Where everything is stored

| Item | Location | What to do on the new PC |
| --- | --- | --- |
| Latest application source, tests, migrations and local docs | Original local workspace; included in source ZIP | Copy/extract the source package. It is not recoverable by cloning the public docs repo. |
| Browser configuration | Original `.env.local`; deliberately excluded from ZIPs and public docs | Recreate it privately from the existing Supabase project's URL and publishable key, or transfer your own file privately. Never paste keys/passwords into chat or public GitHub. |
| Business records, saved Drafts, preferences, Auth users and uploaded candidate CVs | Existing hosted Supabase `pairlo-poc` project in the Pairlo organization, Singapore | Reconnect to the same project and sign in with the same approved Pairlo account. Another account has an isolated workspace. Do not create a replacement backend or reseed it for a PC move. |
| A form not explicitly saved as a Draft | Browser/application memory | It does not travel with the source or sign-in. Save it as a Draft on the original PC if still available. |
| Login sessions and connector credentials | Browser/OS/app credential stores | Sign in/reconnect privately on the new PC. Browser profiles, refresh tokens, plugin credentials and account passwords are not exported. |
| Figma designs | Existing cloud Figma file | Open the existing file with authorized access; read the latest design notes and inspect the live canvas before editing. |
| Hosted frontend | Existing Vercel `pairlo-poc` project | Continues independently of the PC. Deployment access/protection can require separate sign-in. It is not a backup of the newer local source. |
| Public project records | [rexchoicn/pairlo](https://github.com/rexchoicn/pairlo) | Read the latest `main`, not an old chat snapshot. Public operational identifiers are redacted. |
| Historical UAT generation, sample originals and verification evidence | Selected `.local/` files and generated synthetic PDFs; optional reference ZIP | Preserve privately for reference only. The consumed seed/snapshots must not be replayed on the hosted project. |
| Dependencies, build output and CLI caches | `node_modules/`, `dist/`, `*.tsbuildinfo`, `supabase/.temp/` | Not transferred; reinstall/rebuild as needed. |
| Codex/plugin installations and global working preferences | Outside the project folder | Reinstall/reconnect as needed. The project `AGENTS.md` is included, but machine-global settings/credentials are not. |

Normal app reads/writes use the hosted Supabase client, and saved drafts query `form_drafts`; there is no application-data database in the source ZIP. Its `supabase/config.toml` is a development template, not an instruction to provision a new backend.

## Current Figma direction — newer than the local UI

Newer remote edits were found at GitHub commit `6224891963e789c3bf595733af90f16d27d9cf93` and reconciled into the source documentation before export. DEC-045 and the 10 November design study are preserved. The supplied source code remains the older verified implementation.

- [Latest study index](https://www.figma.com/design/5ZDRXCDj97A00pgYFniMnN/Recruiter-SaaS?node-id=532-2527).
- [Candidates / joined roster and preview](https://www.figma.com/design/5ZDRXCDj97A00pgYFniMnN/Recruiter-SaaS?node-id=529-2520).
- [Candidate detail](https://www.figma.com/design/5ZDRXCDj97A00pgYFniMnN/Recruiter-SaaS?node-id=530-2520).
- [Role workspace](https://www.figma.com/design/5ZDRXCDj97A00pgYFniMnN/Recruiter-SaaS?node-id=531-2520).
- [Earlier preferred Option B](https://www.figma.com/design/5ZDRXCDj97A00pgYFniMnN/Recruiter-SaaS?node-id=511-2236).
- [Original profile Summary](https://www.figma.com/design/5ZDRXCDj97A00pgYFniMnN/Recruiter-SaaS?node-id=471-2) and [UI Kit](https://www.figma.com/design/5ZDRXCDj97A00pgYFniMnN/Recruiter-SaaS?node-id=468-70).

The recorded structural requests are one fixed labelled navigation column, no collapse control, the same sidebar on candidate detail, no candidate-switching menu on detail, and one shared surface for the candidate list and selected preview. Stronger focal points and more energetic colours were requested; electric cobalt/violet/emerald/coral are **proposed colours, not a finalized brand system**. Designs have static sample selection/content; some employers, experience values and pipeline counts are illustrative rather than saved facts. Figma iteration does not authorize code rollout.

## Restore and run on the new PC

1. Save the packages outside this chat to a location reachable from the new PC. Compare the source ZIP SHA256 against its `.sha256` sidecar. In PowerShell, `Get-FileHash -LiteralPath .\pairlo-source-2026-11-17.zip -Algorithm SHA256` prints the hash.
2. Extract the source ZIP into a **new, separate folder**, such as your development directory. It has a top-level `pairlo/` folder. Do not extract over a different version or into the clone of the public docs repo: that repo intentionally ignores app files and is not the source repository.
3. Open the extracted `pairlo` directory in your coding app. Inspect the included `AGENTS.md`, this handoff, `PROJECT_STATUS.md`, latest `DECISIONS.md`, `BACKLOG.md` and `FIGMA_CANDIDATES.md`. Compare newer GitHub/Figma changes before editing.
4. Install Node.js **24.x** with npm. Original-PC runtime: Node 24.18.0 / npm 11.16.0. Use the existing lockfile and dependencies; a PC move is not a reason to upgrade them.
5. From the full source directory, run:

```powershell
npm ci
Copy-Item -LiteralPath .env.example -Destination .env.local
```

If `.env.local` already exists, inspect/use your private file rather than overwriting it. In that file, privately configure the existing project's:

```dotenv
VITE_SUPABASE_URL=YOUR_EXISTING_PROJECT_URL
VITE_SUPABASE_PUBLISHABLE_KEY=YOUR_EXISTING_PROJECT_PUBLISHABLE_KEY
```

The included `.env.example` identifies the original project URL. Retrieve the publishable key from your existing Supabase project dashboard/API keys or privately copy your original configuration. Use the existing project, not a newly created empty one. The browser app does not need a database password, secret/service-role key or personal access token. [Supabase's key guidance](https://supabase.com/docs/guides/getting-started/api-keys) explains the distinction.

6. Run the standard checks, then start development:

```powershell
npm run check
npm run format:check
npm run dev
```

`check` runs TypeScript, unit/mock tests and the production build. It does not migrate/reset the hosted database. Normal hosted-backend frontend development needs no local Docker/Supabase stack or UAT seed. The server binds to `127.0.0.1:5173` with a strict port; keep its terminal/process running and use Ctrl+C to stop it.

7. Open [the local app](http://127.0.0.1:5173) in your new PC's browser/preview and sign in privately with the same approved Pairlo account. `localhost` means the computer running that browser; the old PC's localhost link is not a remote server. If necessary, reconnect the Supabase/GitHub/Figma tools with the authorized accounts. Account connections and chat context do not replace transferring the source files.
8. Review [Mina's local profile pilot](http://127.0.0.1:5173/people/ed787d8b-285b-424b-ba1e-319d3f61da92/profile-preview?from=%2Fcandidates&section=opportunities) in **development** mode. Its route is omitted from production builds. Other review entries include `/companies`, `/roles`, `/candidates`, `/today`, `/drafts` and `/placements`. A different/new account can legitimately be empty because records are isolated.
9. Manually verify the intended saved-record reads, navigation and private file access on the new PC before claiming that migration is verified. Saving/recording new test data or deploying a newer UI is separate work; do not replay the old UAT refresh.

On 11 November, a sandboxed server could start while loopback requests timed out; an authorized server restart outside the sandbox restored HTTP 200. If that recurs, check the process/port and use the environment's normal permission flow. A Vite startup message alone is not proof the embedded browser can reach it. Do not stop unrelated projects merely because a port is occupied.

## Source layout and files to inspect

| Area | Local paths included in source ZIP |
| --- | --- |
| App entry/routes and workspace | `src/main.tsx`, `src/components/Workspace.tsx` |
| Current profile pilot | `src/pages/PersonProfilePilot.tsx`, `src/profile-pilot.css`, `src/lib/profile-pilot*.ts`, `src/lib/profile-meetings.ts`, `src/lib/role-discovery.ts` |
| Entity links and hierarchy | `src/components/RelationshipChip.tsx`, `src/components/EntityBadge.tsx`, `src/entity-chips.css`, `src/styles.css` |
| Existing CRM and recruitment | `src/pages/Companies.tsx`, `CompanyRecord.tsx`, `Candidates.tsx`, `PersonDetail.tsx`, `PersonForm.tsx`, `Roles.tsx`, `Applications.tsx`, `src/lib/crm.ts`, `recruitment-api.ts`, `role-workbench.ts` |
| Drafts/forms and navigation safety | `src/components/RecordForm.tsx`, `src/pages/Drafts.tsx`, `src/lib/draft-api.ts`, related draft modules |
| Hosted-backend client/types | `src/lib/supabase.ts`, `src/lib/database.types.ts` |
| Schema/history checks | Fifteen SQL files under `supabase/migrations/`; existing rollback-only SQL suites under `supabase/tests/` |
| Assets/import templates | `public/assets/`, `public/templates/*.xlsx`, public security/SPA files |
| Local documentation export/preparation | `scripts/prepare-docs-sync.mjs`, `scripts/export-handoff.mjs` |

## Exclusions and remaining transfer obligations

The packages do not contain `.env.local`, browser/session tokens, plugin or CLI credentials, OS/global coding-agent settings, `node_modules`, `dist`, `.vercel`, `supabase/.temp` or every historical scratch file. The optional reference ZIP is an explicit selection, **not the entire `.local` directory or a current Supabase backup**. Its archive manifest is the exact inventory. If an excluded scratch file is uniquely valuable, preserve it privately before deleting the old folder.

No file has been installed on the new PC by this export, and no source ZIP has been uploaded to GitHub or another storage service. Ensure the source package is actually copied and readable on the new PC. Retain the original folder until the restored app is checked. A separate **private source-control baseline** is recommended to remove this single-PC dependency; creating/pushing it still requires an explicit request. Do not push app code to the current public docs repo.

## Next product work

Continue reviewing the latest Figma study and settle the final palette/hierarchy before implementing it. Preserve the existing shared identity, confidential candidate data, explicit drafts, independent application response/stage, recorded outside actions and commercial history. Matching, structured education/career/experience data, reverse recommendations and wider profile rollout remain separate proposals. Teams, contract staffing, integrations, mobile and subscriptions are outside the current POC. Exact domain, partner access/review and some verification follow-ups remain open in the backlog.

## Paste into the new coding chat

> Continue Pairlo using HANDOFF_NEW_PC.md and the recovered source ZIP. First confirm the full app source is present, not just the public documentation repository. Read AGENTS.md, PROJECT_STATUS.md, BACKLOG.md, newest DECISIONS.md and FIGMA_CANDIDATES.md; reconcile newer GitHub/Figma work. The public repo is docs-only. The latest code is the local profile pilot; the newer fixed-sidebar, joined roster/preview Figma study is not implemented and its palette is not finalized. Restore private frontend configuration for the existing hosted Supabase project and ask me to sign in privately. Never reset/reseed the database, copy browser tokens, publish source or deploy merely to restore this PC. Run the standard checks, then verify the local browser. Product/UX decisions remain mine; discuss the next approved change before rolling out proposals.

Useful published records: [Start here](https://github.com/rexchoicn/pairlo/blob/main/START_HERE.md), [status](https://github.com/rexchoicn/pairlo/blob/main/PROJECT_STATUS.md), [backlog](https://github.com/rexchoicn/pairlo/blob/main/BACKLOG.md), [decisions](https://github.com/rexchoicn/pairlo/blob/main/DECISIONS.md), [design handoff](https://github.com/rexchoicn/pairlo/blob/main/FIGMA_CANDIDATES.md), [architecture](https://github.com/rexchoicn/pairlo/blob/main/ARCHITECTURE.md), [testing](https://github.com/rexchoicn/pairlo/blob/main/TESTING.md), [hosting](https://github.com/rexchoicn/pairlo/blob/main/HOSTING.md), [documentation sync](https://github.com/rexchoicn/pairlo/blob/main/DOCS_SYNC.md).
