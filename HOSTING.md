# Pairlo hosting

Last updated: 2026-11-09 (Asia/Singapore). This date includes the documentation-hub reference; the deployment/hosted verification below remains the earlier Batch 7 checkpoint.

## Current deployment

| Item | Verified state |
| --- | --- |
| Provider / account | Vercel / PRIVATE_VERCEL_SCOPE |
| Project | pairlo-poc · prj_GUrYXO2LtARlSgbAeJApO4q6YDAz |
| Deployment | PRIVATE_DEPLOYMENT_ID · READY · production target |
| Exact build | https://pairlo-poc.vercel.app |
| Stable provider URL | https://pairlo-poc.vercel.app |
| Source | Unversioned local application workspace; app Git is not initialized. The separate GitHub docs hub does not contain or deploy application source. |
| Build | Node 24.x, npm ci, npm run build, dist output |
| Source manifest | 82 files; SHA256 adf619921cf70ec6f9bab7650ab223461ec93c970b5494185102058a8206c966 |
| Backend | Existing SUPABASE_PROJECT_REF Supabase project, Singapore |
| Custom domain | Pending the user's exact GoDaddy-managed hostname |

The deployment API's first deployment was assigned the production target and provider aliases. The returned state is recorded above; it is not a separate staging environment. The Vercel region in the deployment metadata is static hosting/build placement, not a move of the Supabase database.

Vercel Authentication remains enabled with the existing all_except_custom_domains scope. An unauthenticated request to the exact build redirects to Vercel access. A connector-created 23-hour review link was used privately for the agent's browser check; its token is not stored in source or this document. It expires at 2026-11-06 09:16 Asia/Singapore. This grants access to the frontend, not a Supabase workspace. Pairlo still requires a separate approved account.

The source upload used an explicit frontend allowlist. .env files, .local, outputs, node_modules, database migrations and project documents were excluded. The tracked .vercelignore provides the equivalent boundary for a future CLI source upload. Only VITE_SUPABASE_URL and VITE_SUPABASE_PUBLISHABLE_KEY are browser configuration; both configured values were found in the hosted bundle. No privileged-key/private-key pattern was found in the uploaded source or hosted bundle.

## Verified hosting boundaries

- HTTPS, HSTS, CSP, frame denial, MIME protection, referrer and permissions headers are present. The CSP permits the existing Supabase origin without broadening scripts/styles.
- Root and direct company/role/placement/import paths return the SPA. The deployed JavaScript/CSS filenames match the tested local build. This HTTP check does not establish signed-in business behavior.
- All three templates return the Excel MIME type and expected byte lengths. robots.txt and X-Robots-Tag exclude indexing; access is enforced separately by Vercel/Supabase.
- Hosted public signup and anonymous Auth remain disabled. Anonymous Data API reads of company/candidate/file/placement/import data return 401. Both normal and public CV object paths reject anonymous access.
- The user privately signed into the primary-host native panel, and engineering independently verified its Companies page. The approved task [Batch 7 hosted persistence check (POC test)](https://pairlo-poc.vercel.app/tasks/f0454295-ba39-4350-b6b0-f108aadf6ae4) was created through the hosted UI and survived full reload. Its unsaved draft guard retained the entered text; it is listed exactly once.
- Hosted saved CRM/ATS/commercial/import records, canonical application links, private 701-byte PDF download, duplicate/invalid import checking, formatted-phone search, report counts and restored HK/blank-industry/HKD defaults pass. Warning/error browser logs are empty. Fresh hosted writes cover the one approved task; other write flows retain prior local/live database evidence. Final-domain Auth URLs and actual partner use remain pending.

## Connect the supplied domain

1. Confirm the exact hostname and inspect its current authoritative DNS. Prefer the user's chosen subdomain when the root already serves another site. Do not infer a domain from its availability or buy/transfer it.
2. Add that hostname to this project. Use the exact DNS/ownership records returned for it; do not assume a universal A/CNAME target or force-detach another project.
3. Inspect the existing GoDaddy zone before adding the specific records. Preserve unrelated website, MX, SPF, DKIM and verification records. The connected GoDaddy plugin exposes domain search/availability, not existing-zone management; use an authorized dashboard session or provide the exact records for the user to enter.
4. Verify authoritative resolution, Vercel ownership/configuration, issued HTTPS and the intended deployment on the hostname. A saved DNS change alone is not acceptance.
5. Set Supabase Authentication → URL Configuration → Site URL to the final HTTPS origin. Add only the exact intended return URLs if a redirect-based Auth flow is introduced, keeping required local development URLs. Do not add a wildcard covering unrelated Vercel apps. The POC uses password sign-in with detectSessionInUrl disabled; SMTP/OAuth/reset links are not configured.
6. Verify the hosted browser journey again on the final origin. Authentication is origin-specific, so the user signs in privately there once. Keep Vercel's existing protection settings; the current custom-domain exception still leaves Pairlo Auth, operator approval and owner RLS in force.

The connected Supabase tools do not expose hosted Auth user/settings management. Use an authorized dashboard session or ask the owner to make the exact configuration change; do not retrieve a privileged token/password to automate around this limit.

## Partner access and review

The user must identify the partner email before provisioning. Follow the owner-created, confirmed email/password account plus operator approval procedure in README.md. Password entry/credential delivery belongs to the owner and tester; do not send invitations or credentials through this chat. Do not grant access to an inferred person.

Each tester has isolated records. A new partner account starts empty and cannot see the owner's existing sample records. Shared agency data is outside the POC. Use PARTNER_REVIEW.md to walk through a fresh account or to review the owner's labelled fixtures with the owner present. Actual partner use and feedback are still required for final acceptance.

## Future updates and recovery

Keep source and project documentation together. Before publishing an authorized update, inspect current local changes, run npm run check and npm run format:check, inspect public configuration and use the exact project/team above. Do not upload an entire working folder or its local credentials. Reconcile an uncertain deployment by listing deployments before retrying it.

For a later release, stage and verify a production build before assigning the final domain. Record its returned deployment ID, source revision/manifest and verification. Do not promote a preview under the assumption it is the same production build: production environment variables may rebuild it.

The current release is the first deployment, so there is no earlier Vercel release to roll back to. A later rollback changes the frontend only; it does not undo Supabase records/migrations. Never reset the hosted database to recover a frontend release. No new schema migration was needed for Batch 7 hosting.

Vercel runtime logs do not monitor this static app's direct browser-to-Supabase calls. Use browser error evidence plus Supabase diagnostics for those failures. No external monitoring/drain integration has been added to the POC.
