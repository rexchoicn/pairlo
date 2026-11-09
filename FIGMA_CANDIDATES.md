# Candidate design workspace

Updated: 2026-11-10 (Asia/Singapore). Status: candidate baseline and selected Option B split-preview refinement available for review; implementation pending.

## Review links

- [Start with Mina's Summary](https://www.figma.com/design/5ZDRXCDj97A00pgYFniMnN/Recruiter-SaaS?node-id=471-2).
- [Screens index](https://www.figma.com/design/5ZDRXCDj97A00pgYFniMnN/Recruiter-SaaS?node-id=481-2092) on **From Codex - Design** (`459:2`).
- [UI Kit](https://www.figma.com/design/5ZDRXCDj97A00pgYFniMnN/Recruiter-SaaS?node-id=468-70) on **From Codex - UI Kit** (`459:4`). Component masters sit to the right of the specimen sheet.

The user clarified that the requested screens are **Candidates**, not Roles. These two destination pages were empty before this task. Earlier wireframes, components and source pages remain intact.

## Included screens

All ten frames are 1440 px wide. Frame heights expose the complete desktop content for editing; this is not a mobile design.

| Screen | Node | Included state |
| --- | --- | --- |
| Candidate directory | `475:1232` | Search, filters entry, result count, sortable headings, ten representative fictional rows |
| Candidate filters | `475:1551` | Open dialog; all six saved function options, five availability options and two location options; reset controls and pay text field |
| Add candidate | `476:1797` | Existing-person search, empty essentials, optional LinkedIn, private notes, collapsed preferences, Save/Save as draft |
| Edit candidate | `476:1947` | Mina's saved identity/preferences/employer, optional empty LinkedIn, expanded preferences |
| Summary | `471:2` | Identity, discovery count, active opportunities, follow-up, contact/company context |
| Opportunities | `471:405` | Two active applications and one closed/declined application |
| Relationships | `471:674` | Harbourline combined once; distinct current-employer and company-contact relationships |
| Activity | `472:738` | Three saved conversations, related opportunities and two open follow-ups |
| Meetings | `472:980` | No upcoming interview; two expanded past schedules, 4 June and 3 June 2026 |
| CV & files | `472:1184` | Existing private CV metadata, download control, empty upload state and access guidance |

The source is the **latest local implementation**, including the DEV-only person-profile pilot, rather than the older hosted UI or initial wireframes. Relevant files are `PersonProfilePilot.tsx`, `profile-pilot.css`, `Candidates.tsx`, `PersonForm.tsx`, `RecordForm.tsx`, `DirectoryFilters.tsx`, `Workspace.tsx`, `RelationshipChip.tsx`, `Icon.tsx`, `styles.css` and `entity-chips.css` under `src/`.

The directory is a representative design sample from the approved fictional UAT portfolio; its 60-result label does not mean all 60 rows have been duplicated into Figma. Mina retains 15 unlinked active roles to explore, two active opportunities, zero upcoming meetings and two past schedules. This is manual discovery, not a fit ranking. No real candidate data, authentication state or CV document contents were exported.

## UI Kit and editing

- Native, editable text and vector layers with auto-layout; no screen-sized image fills.
- 76 main components, including source icons, brand mark, buttons, relationship chips, status badges, inputs, filter chips, navigation, tabs, avatars, sidebar, identity header, opportunity cards, follow-up, contact details, CV row and candidate table row.
- Eight variant sets: Button (12), Relationship chip (15), Status badge (4), Input (5), Filter chip (2), Navigation item (3), Profile tab (2), Opportunity card (3).
- Three scoped Pairlo variable collections with 137 new variables, semantic aliases, and 11 new text styles. Compatible existing Recruiter white/layout variables and seven Inter text styles are reused. Earlier token values/components are not changed.
- The specimen sheet documents colours, hierarchy, spacing, shape and control states. Company/person/role/task/placement chips use blue/violet/mint/amber/rose. Status colours have a separate meaning.
- Text properties expose button/chip labels, field values, person identity and table/card content. Change masters to update their instances; edit instance properties for local content. Chip entity determines its icon; sidebar icons have instance-swap properties.

Colour code syntax follows the actual local CSS, including the scoped `--entity-bg`, `--entity-text`, `--entity-border` and `--entity-hover` names. Additional layout/type variables form a Figma design contract; they do not claim corresponding exported CSS variables.

## Prototype and boundaries

There are 67 navigation hotspots: 64 within the ten screens and three on the index. Profile tabs, breadcrumb returns, active-opportunity/meeting entries, Mina's directory entry and selected add/edit/filter journeys link to their design frames. Current-tab/self-navigation is intentionally skipped.

This is a design prototype. Form saves, filtering, drafts, CV uploads/downloads, matching and destinations outside these candidate screens are visual references, not backend operations. Full-height frames do not reproduce the app's sticky scrolling behavior. No automatic Code Connect/Figma-to-code synchronization or library publication is configured. Figma edits do not change local or hosted Pairlo until separately implemented.

## Verification

Programmatic Figma checks passed: ten native screen frames; 733 styled Inter text nodes; 606 component instances including nested instances; 875 auto-layout containers; 1,448 variable-bound paints; no missing text styles, unexpected fonts, screen image fills or overflowing direct children of composed auto-layout frames. The kit has 76 components/eight variant sets; all newly created variables have explicit scopes without `ALL_SCOPES`. Selected semantic aliases, code syntax and real component-property keys were read back.

Rendered Figma screenshots were visually reviewed for the kit, Summary, Opportunities, Relationships, Activity, Meetings, filters/directory and Edit candidate form. Corrected filter options/date formatting, input clipping, icons and activity label wrapping were rechecked where affected. Add candidate was structurally checked and shares the inspected form components; it was not separately screenshot-reviewed. Prototype reactions were written/read back, not manually clicked through in Figma Present mode. User review and physical-device checks remain pending.

A temporary live capture was used only as a comparison reference and removed. Its conditional bootstrap was removed from `index.html`; the temporary capture browser tab was closed. Existing user tabs and the original local server were preserved. No app feature, schema, saved data, deployment, Git initialization, commit or push changed. Runtime tests were not rerun for this Figma/documentation-only task; prior 236-test evidence remains in TESTING.md.

An ignored `.local/figma-candidates-ledger.json` retains the task session, returned node IDs and structural evidence for follow-up edits. The durable review links and baseline are recorded here.

## Candidate UX V2 — design proposal, not accepted (9 November 2026)

Two **additional editable desktop frames** were created below the ten-screen baseline on the existing **From Codex - Design** page. The ten original candidate screens, UI Kit, app code and recorded UAT data remain unchanged.

- [**V2 Candidates directory**](https://www.figma.com/design/5ZDRXCDj97A00pgYFniMnN/Recruiter-SaaS?node-id=494-1976) — selected-person list and right preview instead of an equally weighted six-column table. Gives name/title, recorded pay period/notice, existing opportunity context, next follow-up and a full-profile entry; search and filters stay visible.
- [**V2 Mina Summary**](https://www.figma.com/design/5ZDRXCDj97A00pgYFniMnN/Recruiter-SaaS?node-id=496-2054) — compact identity and existing employer connection, explicit *Explore 15 active roles* (unlinked, **not ranked or matched**), two active opportunities, overdue follow-up, known preferences and private notes separated from shared contact relationships.

The new frames use native editable layers, existing Pairlo variable-bound colours, the existing dark sidebar, reused company-link instances and auto-layout with 4px spacing. Relevant prototype navigation is attached: Mina's list row/profile button → V2 Summary; Add/Filters/Edit/Opportunities → existing baseline screens; Summary breadcrumb → V2 directory. Other visible controls remain design-only and do not implement backend actions.

**Review gate:** Confirm whether the list-plus-preview improves sourcing versus the baseline table; whether role discovery and overdue next action have the right emphasis; which candidate facts should be visible in a dense list; and whether to propagate the visual language to Filters, Add/Edit and the other profile tabs. These are proposals, **not accepted requirements or implementation**. No global fit score, automatic matching, new schema, real candidate data, application deployment or runtime test is implied.

## Candidate card V3 — three visual alternatives (9 November 2026, pending product review)

Three **new editable full-page desktop proposals** sit side by side below V2 on **From Codex - Design** (`459:2`). The original ten-screen candidate baseline, earlier V2 frames and UI Kit remain intact.

| Alternative | Figma frame | Main UX trade-off |
| --- | --- | --- |
| A — Experience Spotlight | [`510:2165`](https://www.figma.com/design/5ZDRXCDj97A00pgYFniMnN/Recruiter-SaaS?node-id=510-2165) | Spacious reference-inspired cards with prominent years-of-experience panel, company placeholder, icon facts and a persistent contextual preview. Fewer results per viewport. |
| B — Selected Roster + Preview (owner's preferred direction) | [`511:2236`](https://www.figma.com/design/5ZDRXCDj97A00pgYFniMnN/Recruiter-SaaS?node-id=511-2236) | **Updated 10 November:** compact candidate list (~724px) plus a right selected-person details panel (~387px). Keeps visible employer/title/experience and key location/pay/notice details; the preview carries follow-up, opportunities, practical context and a full-profile CTA. |
| C — Visual Candidate Grid | [`512:2307`](https://www.figma.com/design/5ZDRXCDj97A00pgYFniMnN/Recruiter-SaaS?node-id=512-2307) | Two-column cards with large company monogram placeholders, large experience badges, icon-labelled details and a dedicated recruitment-context footer. Easier visual browsing, less list density. |

All three use the current Pairlo dark sidebar, native editable text/vectors, semantic variable-bound paints, 4px-grid auto-layout spacing and neutral company-logo monogram placeholders. Screens are illustrative rather than a new matching engine or live feature. **Years of experience and employers marked with an asterisk are invented sample content for layout evaluation, not persisted verified candidate facts.** Candidate years of experience are not an approved structured field; employer-logo support is also not a proven runtime feature. Existing recorded candidate/pay/notice/role data is represented only as sample copy.

The Mina example card, Add candidate and Filters controls have sample Figma navigation reactions; these do not implement filtering, editing, matching, logo lookup or backend transactions. Final structural verification found no direct-child auto-layout overflow or off-grid spacing in newly built frames. The user subsequently selected **B as the preferred Figma direction**, with final product sign-off and code implementation still pending. Next UX review: compare skim speed at realistic result counts; assess whether experience should be dominant or simply a clear secondary signal; choose list vs grid, preview vs no preview, icon density and behaviour for missing employer/experience. Record acceptance in DECISIONS.md before implementation.

## Candidate directory V3 B refinement — list and selected preview (10 November 2026)

**User direction:** Of the three visual alternatives, Option B was preferred, with its full-width roster changed to a narrower left list and a right-hand detail panel shown when a row is selected. This is an approved *direction for Figma iteration*, not approval to ship code or new data fields.

- [Open updated Option B, same frame `511:2236`](https://www.figma.com/design/5ZDRXCDj97A00pgYFniMnN/Recruiter-SaaS?node-id=511-2236). The frame ID and 1440px desktop canvas remain unchanged. Options A/C, the original Candidates baseline, and V2 screens remain untouched.
- Left: six compact candidate rows, with monogram company placeholders, current title/employer, illustrative years of experience, and icon-labelled location/notice/pay. Selected Mina row uses a subtle background, brand outline and accent rail. Page header/search/filter/sort remain above.
- Right: a selected-candidate preview showing Mina's identity/company, illustrative experience, two recorded active opportunities, expected pay/notice/location, last recorded conversation and overdue follow-up, plus **Open full profile**. The full-profile CTA retains its prototype destination.
- Layout is native/editable Figma, using existing local Pairlo colour variables and 4px-based auto-layout; final structural check found **0 direct-child overflow and 0 off-grid custom frames**. This is still a **static selected-state design example**; choosing another row does not yet dynamically update the preview in the prototype.
- Avoid treating invented years/employers marked * as verified records; no company-logo fetching, matching engine, new data field, application/database change or deployed UX is implemented.

**Next product review:** Confirm whether this split is the desired final directory pattern; then decide whether list selection should preserve search/filters and whether the right panel should remain visible while scrolling. Extend only after review.

## Next action

Review and edit the candidate screens in Figma. Record accepted visual/product changes in DECISIONS.md and update this baseline when implementing them. Wider profile rollout, structured career data and matching remain separate proposed increments in PRODUCT_REFINEMENT.md.
