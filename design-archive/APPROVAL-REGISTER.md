# Approval register

This register deliberately distinguishes explicit user approval from the mere existence of a page in the repository. A page is not marked approved solely because it was created, committed, or included in the archive.

## Explicitly confirmed in the available project record

| Page | Evidence | Status |
|---|---|---|
| `cv-upload.html` | User explicitly approved the CV Upload screen | Approved |
| `dashboard.html` | User confirmed the dashboard CSS correction with “все ок” | Confirmed after correction |

## Included, but explicit visual approval is not confirmed in the available record

### Recruiter area
`index.html`, `registration.html`, `login.html`, `forgot-password.html`, `reset-password.html`, `email-verification.html`, `vacancies.html`, `vacancy-create.html`, `vacancy-details.html`, `candidate-profile.html`, `screening-result.html`, `candidate-comparison.html`, `screening-results.html`, `candidates.html`, `analytics.html`, `settings.html`, `notifications.html`.

### Admin area
All seven admin screens are included. The Admin Dashboard was explicitly noted as not yet visually approved in the project handoff context. The other admin screens are archived as current designs, but this register does not infer a formal visual approval.

### Payments and subscription
All seven payment/subscription screens are included as the latest frontend prototype set. They were created and committed, but explicit visual approval of each screen is not recorded here.

## Handling rule for implementation

Use the pages marked **Approved** or **Confirmed after correction** as confirmed visual references. Treat all other pages as current design references requiring a final product-owner visual check before declaring them approved for production. Do not remove or silently redesign them during integration.
