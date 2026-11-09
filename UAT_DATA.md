# UAT workspace

Last updated: 2026-11-07 (Asia/Singapore).

## Current checkpoint

The richer dataset is **loaded and verified in Tiffany's workspace**, following the user's action-time approval on 6 November. The exact tested refresh ran in dashboard query `PRIVATE_UAT_QUERY_ID` and returned “UAT refresh committed.” All 60 new CVs were uploaded through Pairlo, downloaded, and matched to their original sizes/SHA256 hashes. The retained previous CV makes 61 ready file records in total; none are incomplete. Browser checks passed for connected records, directory counts, Today, placements and the six-month report.

The optional LinkedIn field is implemented in the local candidate forms/detail page and the hosted database. Its migration and database isolation/compatibility checks passed. Browser save/reload/normalization/clear also passed; the temporary verification link was removed. The frontend has not been redeployed. The hosted POC shares the refreshed data; its UI remains the earlier release.

The 7 November draft walkthrough retains two private incomplete records under Drafts: Northbank Advisory (company) and Adrian Chow (candidate). They are separate snapshots, excluded from every live portfolio count below. Availability follow-up is a recoverably discarded conversation draft; Harbourline has a completed edit draft whose temporary note was removed before final Save, leaving its business fields unchanged and updating only its normal saved timestamp. No new live company, candidate, conversation or task was created. These drafts are review examples, not another portfolio refresh; do not rerun the seed.

## Loaded portfolio

| Records | Count | Coverage |
| --- | ---: | --- |
| Companies | 12 | Clients, prospects, discussions and dormant relationships; industry, location, website, notes and fee defaults |
| Candidates | 60 | Six functions; salary, notice, preferences, skills, employer links and private recruiter assessments |
| Business contacts | 27 | Hiring directors/talent contacts; two candidates also have business relationships |
| Roles | 30 | Briefing, active, on hold and closed; hiring contacts, detailed briefs, budgets and fee overrides |
| Applications | 180 | Three per candidate; independent responses/stages, discussed pay and dated history |
| Conversations | 140 | Two multi-role conversations per candidate and 20 later availability check-ins |
| Placements | 8 | Accepted offers, explicit fee bases, guarantees, paid/partial/unpaid/draft/not-invoiced examples |
| Tasks | 120 | 80 completed and 40 open, with candidate/application/conversation/placement context and general desk tasks |
| CVs | 60 new PDFs | One fictional document per candidate, privately uploaded and byte-verified; previous Yuki CV also retained |

The portfolio spans May–November 2026 using entered event dates. Placement agreement creation times remain their true insertion times; this is a historical portfolio backfill, not evidence of six months of actual platform use. Existing import IDs/result links and core company/person/role/application IDs are retained where applicable. The old candidate CV is retained as a previous copy; the new CVs are additional private files.

All identities, employers, career histories, agreements and money are fictional. Email/websites use reserved example domains; phone numbers are deliberately non-routable sample values. No real LinkedIn profile is invented for a fictional person, so seeded LinkedIn fields are empty. Real links can be entered on candidate forms later. No messages, invoices or payments are sent.

The optional structured role work arrangement was added on 7 November. All 30 existing values remain blank under the user's confirmed rule; prose in old briefs was not automatically converted. The role-card/company-tab review did not change the portfolio counts or save recruiting actions. Older entered event dates can correctly produce stale-progress indicators even where the backfill/saved-update timestamp is recent.

## Inputs and execution

- `scripts/uat/build_dataset.py` builds the manifest and expanded SQL from `scripts/uat/refresh.sql`. It never connects to Supabase.
- `.local/uat-before-2026-11-06.json` is the ignored pre-refresh snapshot. It contains the existing synthetic business rows, not Auth credentials. Preserve it before applying the refresh.
- `.local/uat/dataset.json`, `refresh.sql`, `dry-run.sql` and `cv-manifest.json` are generated/ignored inputs. PDFs are under ignored `output/pdf/uat-cvs`.
- The real refresh checks every backed-up row and rejects additions/edits since the snapshot. It then replaces only the known old test journeys in one transaction, updates their core records and inserts the portfolio through normal RLS-protected tables/workflow functions. It never disables triggers/RLS or changes other accounts, preferences, membership or Auth settings.
- Do not run this as a schema migration, app startup hook or general-purpose reset. Do not rerun it after people start editing the richer dataset. A failed/stale snapshot requires reviewing the differences and preparing a new explicit plan.
- The refresh and all 60 uploads/download checks are complete. `scripts/uat/verify.sql` verifies the loaded graph without writes. `.local/uat/cv-upload-audit.json` records the verified downloads; final database readback matched all 60 manifest hashes/sizes, ready metadata and stored object sizes. Local and hosted Pairlo share this database.

## Suggested review journey

1. Open Harbourline Technologies: review its hiring contacts, fee terms and roles.
2. Open an active role and follow its candidates into their canonical applications.
3. Open Mina Chan: review three opportunities, conversation history, employer/business relationships and private CV.
4. Open Yuki Law's Cloud Lead placement: review the accepted offer, agreed fee, invoice/payment and guarantee history; compare other placements for partial/unpaid/issue states.
5. Review Today/Tasks and Analytics across the six-month period. Try filters, sorting and related-record return links.
