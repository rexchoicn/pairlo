# Candidate design workspace

Updated: 2026-11-09 (Asia/Singapore). Status: editable Figma baseline created and visually reviewed; product review is pending.

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

## Next action

Review and edit the candidate screens in Figma. Record accepted visual/product changes in DECISIONS.md and update this baseline when implementing them. Wider profile rollout, structured career data and matching remain separate proposed increments in PRODUCT_REFINEMENT.md.
