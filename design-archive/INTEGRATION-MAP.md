# Integration map and implementation notes

## Global product and UI constraints

- Main product user: recruiter. The admin panel is an internal owner/platform-admin area, not a customer/company admin portal.
- Do not add an Upload CV item to the main recruiter navigation. CV upload starts from a vacancy context or Telegram bot flow.
- Accepted CV formats: PDF, DOC and DOCX. JPG/PNG are not supported.
- Failed CV uploads belong at the bottom of the list, in red, with a reason and an individual Retry action. Successful uploads proceed to Screening.
- Do not expose the internal Admin Panel in the recruiter navigation.
- Do not represent demo UI states as live services or persisted data.
- Keep the existing `assets/refinder-logo.svg` unchanged.
- Preserve responsive desktop and mobile behavior.

## Recruiter page mapping

| Archive file | Intended application area | Integration notes |
|---|---|---|
| `index.html` | Public landing page | Uses shared `css/style.css` and `js/main.js`; connect legal/support routes in app |
| `registration.html` | Account registration | Replace form demo with real registration/auth API |
| `login.html` | Sign-in | Connect production authentication |
| `forgot-password.html` | Password recovery request | Connect recovery email flow |
| `reset-password.html` | Password reset | Validate secure reset token server-side |
| `email-verification.html` | Email verification | Connect verification token/status |
| `dashboard.html` | Recruiter dashboard | Replace illustrative metrics/activity with API data |
| `vacancies.html` | Vacancy list | Connect search, filters, sorting and pagination |
| `vacancy-create.html` | Vacancy creation | Connect validation and create endpoint |
| `vacancy-details.html` | Vacancy workspace | Connect vacancy data, candidate pipeline and actions |
| `candidate-profile.html` | Candidate details | Connect candidate record and recruiter decisions |
| `screening-result.html` | Individual screening result | Connect screening result and source evidence |
| `candidate-comparison.html` | Candidate comparison | Preserve comparison of 2–5 candidates; connect real candidate data |
| `cv-upload.html` | CV upload from vacancy | Enforce PDF/DOC/DOCX; handle failed/retry and successful-to-screening transitions |
| `screening-results.html` | Screening queue/results | Connect jobs, filters, statuses and retry/export actions |
| `candidates.html` | Global candidate database | Connect global search/filter and access rules |
| `analytics.html` | Recruiter analytics | Replace demo metrics/charts with aggregated backend data |
| `settings.html` | Recruiter account settings | Keep separate from internal Admin Settings |
| `notifications.html` | Recruiter notifications | Replace local demo state with persisted notifications |

## Admin page mapping

| Archive file | Intended application area | Integration notes |
|---|---|---|
| `admin-dashboard.html` | Internal platform overview | Replace illustrative KPIs/service health/activity with telemetry and billing data |
| `admin-users.html` | Internal user management | Connect user search, account status and audited admin actions |
| `admin-billing.html` | Internal subscription/payment operations | Connect Stripe/PayPal events and subscription ledger; do not treat sample MRR as accounting |
| `admin-screening.html` | Internal AI screening operations | Connect queue/jobs/failures/telemetry; no fake retry or queue control |
| `admin-events.html` | Internal system events | Connect structured logs/alerts; never expose CV contents or unnecessary candidate data |
| `admin-audit.html` | Internal audit log | Connect immutable audit records; never store credentials, tokens or CV contents |
| `admin-settings.html` | Internal platform settings | Security settings require server enforcement and audit; service states must be live; retention policy is read-only |

## Payment page mapping

| Archive file | Intended application area | Integration notes |
|---|---|---|
| `subscription.html` | Pricing/plan selection | Single plan: €4.99/month |
| `checkout.html` | Checkout initiation | Start a provider-hosted or securely tokenized Stripe/PayPal checkout; never collect raw card data in this prototype |
| `payment-processing.html` | Pending provider result | Wait for server-side verified provider result/webhook |
| `payment-success.html` | Confirmed payment | Show success only after server-side provider verification; activate subscription server-side |
| `payment-failed.html` | Failed payment | Use provider error status; allow retry without duplicating charges |
| `subscription-manage.html` | Subscription management | Cancellation keeps paid access until end of paid period; afterward paid features become read-only and recruitment data remains accessible |
| `payment-history.html` | Payment history/invoices | Read from server-side payment ledger and expose legally required documents |

## Billing and retention product rules

- One plan: **€4.99/month**, recurring.
- Cancellation: subscription remains active until the end of the paid period.
- After paid access expires: paid features become read-only; recruitment data remains accessible.
- Recruitment data is retained until account deletion.
- Account deletion removes vacancies, candidate profiles, CVs, screening results, recruiter decisions, notes, activity history and user analytics.
- Payment documents and records subject to mandatory legal retention are retained for 3 years as the current product requirement. Legal basis and exact scope/period must be validated for applicable jurisdictions.
- Audience: both individual and business users.
- Do not introduce additional plans or change the agreed subscription price without product-owner approval.

## Technical boundaries

- HTML prototype interactions are not backend contracts.
- Do not port sample users, candidate profiles, CVs, screening scores, metrics, event logs or payment records as production data.
- Do not infer API endpoints from element IDs or demo JavaScript.
- Authentication, authorization, subscription state, payment confirmation, data retention, deletion and audit must be enforced server-side.
- Replace placeholder links with actual app routes and preserve the intended user flow.
- Confirm all routes, keyboard behavior, validation, empty/error/loading states, mobile breakpoints and accessibility after integration.
