# Product refinement proposal

Last updated: 2026-11-09 (Asia/Singapore).

Status: Mostly proposed for discussion. On 9 November the user approved the UX-001/002 unified person-profile UI pilot, including relationship chips and stronger hierarchy, for local review before rollout. That pilot is implemented at the development-only `/people/:personId/profile-preview` route; user acceptance is pending. New career/preference fields, smart matching and other pages below remain proposed. This document is not approval to implement every item, change private-data access, introduce an AI provider, publish application source or deploy. The separately authorized GitHub hub publishes project documentation only. Current implementation is in PROJECT_STATUS.md; accepted decisions belong in append-only DECISIONS.md.

## Product goal and current findings

Help a recruiter answer two questions: who could fit this role, and which roles could suit this person? Make the supporting people/company/role relationships clear without requiring the recruiter to reconstruct them across screens.

The 9 November review inspected current local source and signed-in Company People, contact/person, candidate and role screens. Findings:

- One identity can have separate contact and candidate presentations. Mina's company contact view conceals the richer recruiting context available on her candidate page.
- Company People currently lists business contacts, not all current employees or all candidates employed at that company.
- Employer and business-contact links already exist in the data, but their relationship types and clickability are weakly signalled. One company can appear twice with different meanings.
- Role Function currently uses industry options. Separate job function from employer industry before using them as matching criteria.
- Skills and pay are largely text; education, employment timelines, relevant experience and candidate work-arrangement preferences are not sufficiently structured for reliable criteria-based matching.
- Many white panels, small labels and metadata blocks receive similar emphasis. The person header omits useful job/employer context. The Connected identity panel explains implementation rather than helping a recruiter act.
- Roles initially mixes active, paused, briefing and closed records; a recently updated closed role can appear first. The current Find candidates flow is manual linking, without fit ranking.

## Priority and approval model

- High: core identity, matching foundations and the first candidate-to-role journey. Dependencies determine which gets built first.
- Next: strengthen surrounding navigation and the reverse matching journey once the shared foundations work.
- Later: supporting-page improvements that do not determine the first useful matching experience.

These are recommendations, not accepted implementation scope. Review one contained page/journey before extending its patterns. For each approved increment: settle behavior and examples, implement, verify, update status/backlog, and append any significant accepted decision.

## Page-by-page proposals

### UX-001 — Shared navigation and UI patterns — High, delivered with the first profile pilot

Purpose: make identity, relationships and primary actions recognizable everywhere.

Potential changes:

- Keep the approved dark sidebar, light gray canvas and charcoal primary buttons.
- Introduce a shared linked-record chip: a restrained brand tint, entity icon, record name and small right chevron. The full chip is a real link, with hover and keyboard focus; no underline.
- Use the same treatment for company/person/role links. Icons and explicit relationship labels distinguish their meanings. Static status badges stay quieter and do not resemble links.
- Establish one stronger page header, one dominant task action and clear section hierarchy. Keep existing sticky form Save/Save as draft behavior.
- Use initials/monograms for quick identity recognition, without requiring photos or logos.
- Keep the current sidebar sections initially. A new top-level People area is an open product choice, not a requirement for unified profiles.

Review checkpoint: a tester can distinguish a linked company from a static status and can identify the page's primary action without explanation. Apply first on one profile, not every page simultaneously.

### UX-002 — Unified person profile and candidate edit/career data — High

Pilot checkpoint (9 November): shared identity header with initials/current title/employer and contextual profile sections. The latest refinement adds plain-title opportunity cards whose surface opens the saved opportunity, independent company/person chips, shared entity colours, stronger type/spacing/surface hierarchy, sticky active-opportunity/next-meeting entries and a Meetings section using recorded interviews. The primary count means active roles without any existing pair, including closed/declined history; it opens that filtered manual list. It does not claim a role is unseen or a fit match. Existing person/candidate pages retain default destinations and the explicit protected candidate/file access path. New structured editing and automated suggestions remain future work; user pilot review is pending.

Purpose: one identity and one consistent profile reached from Companies, Candidates or a role.

Potential changes:

- Shared header: name, current title, current-employer link, location, relationship roles and verified availability/search preferences where known. Do not infer job-search status from existing applications.
- A person can be an employee/former employee, candidate, hiring contact or referrer in different relationships. Employer and applications remain optional.
- Organize into Summary, Opportunities, Relationships, Activity and Career & CV modules; choose the final tab order in the pilot. Show useful modules for contact-only people without inventing candidate data or empty applications.
- Summary surfaces skills, relevant experience, practical preferences, current opportunities and next action. Move record timestamps and technical explanations out of prime space.
- A candidate's primary discovery action is Find suitable roles. Contact-focused actions include their hiring roles and recording business interactions. Exact action selection needs review when a person has both roles.
- Retain separate protection for private salary, CVs and recruiter notes. A common layout must not broaden contact-only queries/access or expose private data through company summaries.
- Extend editing, when approved, with employment history, relevant qualifications, structured skills, work preferences and source/last-confirmed dates. Represent unknown explicitly. Do not force users to complete everything before saving a person.
- Compensation comparison needs amount/range, currency and period. Preserve existing text until an explicit migration/conversion is agreed; do not assume annual/monthly equivalence.

Review checkpoint: open the same person through both entry points, see one coherent identity, identify employer and active opportunities, and return to the original company/role context. Test contact-only, candidate-only, dual-role and between-jobs examples.

### UX-003 — Company detail, particularly People — Next; early visible improvement

Purpose: show who matters to this company and how they connect to recruitment.

Potential changes:

- Retain Roles / People / Activities / Detail as the base structure.
- People distinguishes Hiring contacts, Candidates employed here and All connected people. Past employment should be labelled separately once history exists.
- Person rows/cards show title, explicit relationship, relevant hiring roles or active candidate opportunities, and recorded last interaction/next follow-up where available. No fabricated counts or contact dates.
- Open the unified profile instead of a thin contact-only destination. Preserve company/tab return context.
- Company header summarizes useful hiring context, such as open-role count and key contact, without repeating every detail field.
- Role cards/table remain company-specific; retain existing fee terms and saved history. Activities should make its person/role sources navigable.

Dependencies: UX-001/002 for links/profile; employee/relationship history for broader People views. Do not relabel all contacts as current employees.

Review checkpoint: explain why each person appears, open someone who is both a contact and candidate, and reach a relevant hiring role without losing the company context.

### UX-004 — Role workspace, detail and criteria editor — High; matching dependency

Purpose: make the target hire clear before ranking anyone.

Potential changes:

- Consider an Active roles default with explicit views for All, On hold and Closed; this changes the current default and needs acceptance.
- Make Find close matches the discovery action while retaining manual search and the established pipeline flow.
- Add a structured criteria section distinguishing Required and Preferred. Include job function, relevant skills/proficiency, relevant experience, role scope, genuinely required qualifications and practical constraints.
- Keep industry separate from job function; relevant experience is more useful than a single total-years number.
- Capture work arrangement, location, budget currency/period/range and expected timing so practical compatibility is explainable.
- A brief or AI-extracted suggestion may propose criteria, but the recruiter confirms them before they affect ordering.
- Keep criteria, current pipeline and next follow-up visually distinct. Fee terms and administrative metadata receive less emphasis.

Review checkpoint: a recruiter can explain the brief and identify negotiable criteria before running a match. Agree examples of an eligible close fit, a known gap and missing evidence.

### UX-005 — Role matching results and comparison — High; new page/journey

Purpose: find a small useful set of candidates and explain the ordering.

Potential changes:

- Candidate list beside a match-evidence preview, with the role criteria accessible without leaving.
- Each result shows identity/current-employer link, relevant expertise, a few supported reasons, the most important gap/question and practical preference alignment.
- Sort by an explicit role-specific fit model. Prefer understandable labels initially; an eventual numerical score needs a clear definition and validation, and is not a probability of hiring success.
- Separate qualification fit, candidate preferences/practical alignment and evidence completeness. Missing data is unknown rather than a failed requirement or silent exclusion.
- Evidence links to its source, with last-confirmed dates where recorded. Do not infer facts from names, photos or nationality.
- Compare a small set (proposed maximum three) against the same criteria. Show which trade-offs the recruiter is making.
- Potential actions: inspect profile/CV, save for review, compare and explicitly Add to pipeline. Already-linked candidates show their existing opportunity/stage.
- Suggested matches and saved-for-review pairs remain separate from applications. Add to pipeline is not an application by the candidate, consent, a client submission or an external message.
- A dismiss/review reason applies to this pair, not a permanent judgement of the person.

Dependencies: approved role criteria, usable candidate facts, agreed scoring/unknown-data rules and a small recruiter-labelled evaluation set. A UI prototype can precede the live engine if clearly labelled with illustrative data.

Review checkpoint: for the top few suggestions, the recruiter can explain the reasons and concerns, compare candidates and deliberately advance a pair. Evaluate relevance and missed candidates, not just whether a score appears.

### UX-006 — Candidates directory — Next

Purpose: browse a talent pool with enough context to choose whom to inspect.

Potential changes:

- Rows show current title/employer, expertise, availability/preferences freshness and active-opportunity context when known.
- Preserve efficient search, filters and a preview. Add filters for new structured fields only as those fields become reliable.
- Keep unrelated contact-only people out of the candidate view, even though they share the same underlying person profile.
- Do not show a universal match score on the directory: fit needs a selected role.
- When entered from a role, retain a visible role context and a clear return route.

Review checkpoint: find a plausible person quickly, understand their current employer and opportunities, and return without losing search/filter context.

### UX-007 — Suggested roles for a person — Next; second matching direction

Purpose: help a recruiter identify the person's next move.

Potential changes:

- Entry from Find suitable roles on the person profile.
- Rank active roles against relevant experience and the person's stated career goals, interests and practical preferences.
- Role/company cards show fit reasons, trade-offs, hiring contact and existing relationship/opportunity state.
- Keep suggested, saved for review and already-linked roles distinguishable. Explicit recruiter action creates a pipeline relationship.
- Reuse evidence, comparison and source/freshness patterns from UX-005; candidate preference alignment can change the ordering and is not simply the reverse of employer criteria.

Dependencies: the first matching journey and candidate preference data. Do not create a candidate-facing portal as part of this proposal.

Review checkpoint: a technically suitable but unwanted role is distinguishable from one that supports the person's stated next move.

### UX-008 — Opportunity detail and role pipeline — Next

Purpose: keep the person-role pair and next action clear after discovery.

Potential changes:

- Header links person, role and company, with the responsible hiring contact available.
- Surface response, current stage, next action and important dates before the full event history.
- Where matching was used, retain the reasons assessed at review time and allow later reassessment without rewriting the original decision/history.
- Preserve independent candidate response/stage, manual submissions, structured recruitment steps and commercial safeguards.
- Use language that distinguishes recruiter-created opportunities, actual candidate interest and client submissions.

Review checkpoint: understand what happened, what needs doing next and how to navigate either side of the pair.

### UX-009 — Today, Tasks and global search — Later

Potential changes:

- Today groups a small actionable set: sourcing needed, feedback to chase, upcoming interviews and offers needing action. Prioritize explicit saved due dates before inferred urgency.
- Tasks show their person/role/company links and contextual action without automatically completing or advancing recruitment state.
- Global search presents canonical records with relationship context and consistent linked-record treatment.
- Keep warning generation explainable; do not introduce notification sending or automated outreach in this pass.

Review checkpoint: a recruiter can select the next useful action and reach the exact related record.

### UX-010 — Imports, Settings, Analytics, Placements and Drafts — Later, targeted changes

Potential changes:

- Imports: when the new data model is approved, extend templates for structured employment/skills/qualifications with preview, validation, explicit identity reuse and no overwrites. Do not silently turn unparsed CVs into verified profile facts.
- Settings: consider job-relevant matching preferences only after distinguishing personal defaults from each role's required/preferred criteria.
- Analytics: later measure reviewed suggestion relevance, time to a useful shortlist and progression. Avoid a global candidate-quality metric.
- Placements: reuse person/role/company navigation while preserving existing fee/payment/guarantee behavior.
- Drafts: ensure any approved new editor/journey retains incomplete work safely. Commercial and import rules are not being redesigned in this proposal.

## UI direction to pilot

| Element | Proposed treatment |
| --- | --- |
| Navigation | Keep dark sidebar and current grouping/order; improve identity/context in content first |
| Canvas/surfaces | Light gray background, white main surface, fewer competing panels; dividers for secondary sections |
| Identity header | Stronger name/headline, current title and employer connection, small initials/monogram |
| Primary action | One dominant charcoal action per page; secondary actions quieter, editing less prominent on read views |
| Linked records | Soft brand tint + relevant icon + name + right chevron, whole-chip link, no underline |
| Static status | Neutral compact badge; semantic colour only for meaningful fit/gap/urgency states |
| Selection | Restrained brand accent or tinted edge with visible focus; do not fill every card with brand colour |
| Typography | Proposed 28–32 px main identity, 18–22 px section headline, 14 px body and 12 px supporting metadata; verify on the desktop canvas |
| Layout | Fast-scanning list with stable right preview for discovery; clear main reading area plus compact relationship/context section on profiles |
| Detail density | Show decision-relevant facts first; progressive disclosure for long history, fee administration and record timestamps |

Exact styling and tab/action choices are proposed for one coded demo before wider rollout. A calmer palette does not require identical visual weight. Static badge, interactive link, selected result and primary action should be visibly different.

## Recommended one-at-a-time delivery order

| Increment | Deliverable | Gate before the next increment |
| --- | --- | --- |
| 0 | Source-control baseline, separately authorized | Public docs-only hub is established separately. Review source repository/visibility and exclusions before initializing or publishing application source |
| 1 | Unified person profile pilot plus shared relationship-link/visual hierarchy pattern | Review contact-only, candidate-only and dual-role examples; approve layout/privacy behavior |
| 2 | Company People and its connected-person navigation | Confirm employment versus business-contact meanings and useful card facts |
| 3 | Role criteria/detail editor | Agree required/preferred criteria for the first recruitment desk and separate function/industry |
| 4 | Candidate career/preferences editing and directory refinements | Confirm fact sources, unknown handling and practical matching fields |
| 5 | Role-to-candidate match review, comparison and explicit pipeline addition | Validate against a small recruiter-labelled set; confirm no automatic decisions/submissions |
| 6 | Person-to-role suggestions | Validate candidate goals and practical preferences in the reverse direction |
| 7 | Opportunity/pipeline context, then Today/Tasks | Verify the complete discovery-to-follow-up journey |
| 8 | Supporting-page extensions as needed | Extend imports/reporting/defaults only when the preceding workflow justifies them |

Highest-priority outcome: a recruiter can move from a role to a useful candidate profile, understand why a pair may fit, inspect the relevant connections and deliberately take a next step. The first UI increment can improve identity/connections before the matching engine is available.

## Matching boundaries and inputs still needed

- Rank on explicit job-relevant evidence and candidate preferences. Do not score nationality, race, sex, age or inferred personal traits. Any necessary work-authorisation/sponsorship information is separate recruiter-reviewed administration, not a capability score.
- A genuinely required credential can be a criterion; school prestige or unsupported assumptions should not stand in for relevant ability. Equivalent experience and negotiable criteria need an explicit product rule.
- Unknown information stays visible and recoverable. No automatic rejection, outreach, CV sending or stage changes from a match score.
- AI extraction/semantic interpretation may be a later implementation choice. Provider access to CVs/personal data requires an explicit reviewed data-processing design; existing private-CV boundaries remain.
- Choose the first recruitment desk, the recruiter's first five CV checks, which criteria are negotiable, and representative close-fit/gap/unknown examples before settling ranking.
- Decide which primary action wins for a dual-role person, whether suggested-pair saving needs a separate review queue, and whether a top-level People directory is useful. None is assumed approved.

Context sources for the matching discussion: [EOC job-related selection guidance](https://www.eoc.org.hk/Upload/files/EM%20Unit/files/The%20Racial%20Diversity%20and%20Inclusion%20Charter/Infographic_good_practices_Eng.pdf) and [PCPD AI framework](https://www.pcpd.org.hk/english/resources_centre/publications/files/ai_protection_framework.pdf). These support consistent job-related assessment, human oversight and transparency; this document is a product proposal, not a jurisdiction-specific legal assessment.

## Project records and GitHub

Existing local files already separate current status (PROJECT_STATUS.md), mutable work (BACKLOG.md), accepted rationale (DECISIONS.md), implemented architecture (ARCHITECTURE.md) and verification (TESTING.md). README.md is the entry point. Keep this proposal separate so unaccepted ideas do not become project truth by accident.

On 9 November the user created the public [rexchoicn/pairlo](https://github.com/rexchoicn/pairlo) repository and requested a current documentation hub for business/design discussions. [START_HERE.md](START_HERE.md) provides the reading order and context. [DOCS_SYNC.md](DOCS_SYNC.md) defines the docs-only publication/redaction workflow. Remote documents and commits do not imply an application-source backup or deployment; the full local app remains outside a Git working tree.

A future source repository/baseline still needs separate authorization, visibility and exclusion review. Environment secrets, CVs, snapshots and generated/local artifacts must stay excluded. Git/version history is not a replacement for database backups. Business discussions and Figma changes must become explicit accepted records before implementation; proposals in this document remain proposals.
