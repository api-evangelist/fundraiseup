# Fundraise Up (fundraiseup)

Fundraise Up is an online donation and fundraising platform for nonprofits that optimizes the digital giving experience to lift conversion and recurring revenue. Its REST API gives programmatic access to fundraising data - donations, recurring plans, supporters (donors), and an events audit log - so organizations can process offline and non-digital donations through their Fundraise Up account, combine them with online giving, and sync everything to CRMs, BI tools, and data warehouses.

**APIs.json:** [https://raw.githubusercontent.com/api-evangelist/fundraiseup/refs/heads/main/apis.yml](https://raw.githubusercontent.com/api-evangelist/fundraiseup/refs/heads/main/apis.yml)

## Access Model

The REST API is available to Fundraise Up account holders. There is **no separate API fee and no tiered software plans** - Fundraise Up's business model is a single transaction-based platform fee taken as a percentage of each processed donation (a standard **4%**, and **5%** for cryptocurrency), with no setup fees, no monthly fees, and no contracts. Payment processor fees (Stripe, PayPal, Gemini) are charged separately; donors can opt to cover fees at checkout, which most do, lowering the organization's effective net cost.

- **Base URL:** `https://api.fundraiseup.com/v1`
- **Authentication:** API key created in the dashboard under **Settings > API keys**, sent as an HTTP **Bearer** token.
- **Format:** Resource-oriented JSON. Request bodies are JSON with `Content-Type: application/json`.
- **Pagination:** Cursor-based on list endpoints via `limit` (1-100, default 10), `starting_after`, and `ending_before`.
- **Rate limits:** 8 requests/second and 128 requests/minute; exceeding either returns HTTP `429 Too Many Requests`.
- **Update window:** Donations and recurring plans can be updated **only within 24 hours** of creation. Supporters and events are read-only.
- **No WebSocket / no native webhooks:** The API is request/response REST. Event-based syncing is done by polling the Events resource (an audit log) or bridging through Zapier - Fundraise Up does not push events over a WebSocket or configurable webhook.

## Tags

- Fundraising
- Donations
- Nonprofit
- Payments
- Recurring Giving
- Donor Management

## Timestamps

- **Created:** 2026-07-05
- **Modified:** 2026-07-05

## APIs

### Fundraise Up Donations API

List, create, and retrieve one-time and recurring donations, including donations collected outside the website (face-to-face, direct mail, telethons, events) and ACH US Direct Debit donations. Donations can be updated only within 24 hours of creation.

- **Human URL:** [https://api.fundraiseup.com/v1/docs/](https://api.fundraiseup.com/v1/docs/)
- **Base URL:** `https://api.fundraiseup.com/v1`

Endpoints: `GET /donations`, `POST /donations`, `GET /donations/{id}`, `POST /donations/{id}` (update within 24h).

### Fundraise Up Recurring Plans API

List, create, and retrieve recurring donation plans that model a supporter's ongoing giving schedule and terms. Like donations, recurring plans can be updated only within 24 hours of creation.

- **Human URL:** [https://api.fundraiseup.com/v1/docs/](https://api.fundraiseup.com/v1/docs/)
- **Base URL:** `https://api.fundraiseup.com/v1`

Endpoints: `GET /recurring_plans`, `POST /recurring_plans`, `GET /recurring_plans/{id}`, `POST /recurring_plans/{id}` (update within 24h).

### Fundraise Up Supporters API

List and retrieve supporters - the donor records holding a giver's profile and giving history. "Supporter" is the Fundraise Up term for a donor.

- **Human URL:** [https://api.fundraiseup.com/v1/docs/](https://api.fundraiseup.com/v1/docs/)
- **Base URL:** `https://api.fundraiseup.com/v1`

Endpoints: `GET /supporters`, `GET /supporters/{id}`.

### Fundraise Up Events API

List and retrieve audit-log events describing activity across donations, transaction attempts, recurring plans, tributes, and supporters (for example `donation.success`, `recurring_plan.activated`, `supporter.updated`). Events are pulled over REST - Fundraise Up does not push native webhooks - so consumers poll this resource to drive event-based syncing.

- **Human URL:** [https://fundraiseup.com/support/api-event-types/](https://fundraiseup.com/support/api-event-types/)
- **Base URL:** `https://api.fundraiseup.com/v1`

Endpoints: `GET /events`, `GET /events/{id}`.

### Fundraise Up Donor Portal Access Links API

Generate secure, single-use links that let a supporter open their Donor Portal - or a specific recurring plan within it - without logging in, so a nonprofit can embed self-service donor management seamlessly into its own platform.

- **Human URL:** [https://fundraiseup.com/docs/seamless-donor-portal/](https://fundraiseup.com/docs/seamless-donor-portal/)
- **Base URL:** `https://api.fundraiseup.com/v1`

Endpoints: `POST /donor_portal/access_links/supporters/{id}`, `POST /donor_portal/access_links/recurring_plans/{id}`.

## Common Properties

- [LinkedIn](https://www.linkedin.com/company/fundraiseup)
- [Website](https://fundraiseup.com)
- [Documentation](https://fundraiseup.com/docs/)
- [Plans](plans/fundraiseup-plans-pricing.yml)
- [Rate Limits](rate-limits/fundraiseup-rate-limits.yml)
- [Fin Ops](finops/fundraiseup-finops.yml)
- [Blog](https://fundraiseup.com/blog/)

## Maintainers

**FN:** Kin Lane
**Email:** kin@apievangelist.com
