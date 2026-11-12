# Refinder — Service Design Archive

**Archive branch:** `design-archive-2026-11-12`  
**Source branch snapshot:** `main` at archive creation on 2026-11-12  
**Purpose:** preserve the current HTML/CSS design screens as a handoff package for integrating the approved visual layer into the application implementation.

## Contents

- `pages/recruiter/` — recruiter-facing product screens
- `pages/admin/` — internal platform administration screens
- `pages/payments/` — subscription and checkout screens
- `assets/` — shared logo source
- `css/` and `js/` — shared public landing/auth dependencies
- `APPROVAL-REGISTER.md` — evidence-based approval state
- `INTEGRATION-MAP.md` — integration notes and boundaries
- `manifest.json` — machine-readable page inventory

## Page counts

- Recruiter-facing: 19
- Admin: 7
- Payments/subscription: 7
- Total HTML screens: 33

## Important

This is a **design/source archive**, not a production application build. It preserves the HTML pages and the local dependencies needed by the archived page groups. Demo data, local-only interactions, placeholder service states and prototype payment outcomes remain prototypes. Do not interpret them as connected backend features.

The archive intentionally does not merge anything into the application branch and does not alter the existing application implementation. Integrate page-by-page, mapping the existing markup to the production routes, components, data contracts and authentication/payment services.

## How to use

1. Download this branch as a ZIP from GitHub.
2. Keep the archive unchanged as the design reference.
3. Use `INTEGRATION-MAP.md` to map each design to its production route.
4. Port the visual structure and responsive behavior into the target application branch.
5. Replace demo data and local handlers with the actual application services.
6. Preserve the product constraints in the integration notes.
7. Verify desktop and mobile layouts and test every real navigation/action after integration.

## Source of truth

The archived files are copies of the corresponding files from `main` at archive time. If a design is updated later, update the archive intentionally and record the source commit in the manifest/change log.
