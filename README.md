# Fundraise Up (fundraiseup)

<!-- API-EVANGELIST-PROVENANCE:BEGIN -->
> ### About this repository
>
> **This is not our API.** This repository is an independent, third-party profile of a company's
> **publicly available** API surface, maintained by [API Evangelist](https://apievangelist.com).
> API Evangelist does not operate, host, resell, or support this company's APIs, and is not
> affiliated with or endorsed by the company unless stated on the profile.
>
> **Where the information came from.** Everything here is assembled from material a member of the
> public can reach with a browser and no credentials — the company's own website, developer portal
> and documentation, the specifications it publishes for public use (OpenAPI, AsyncAPI, JSON Schema,
> `apis.json`, `llms.txt` and similar), its public repositories, and its public status, pricing and
> changelog pages. **Nothing here is obtained by breaching a system, defeating an access control, or
> using credentials of any kind.**
>
> **The rating is an independent assessment.** The Kin Score and Agent Readiness rating are
> independently calculated scores of a company's *public* API artifacts, produced by API Evangelist
> against a published rubric. They are not certifications, endorsements, security assessments, or
> audits, and they score published artifacts — not the quality, safety, or security of the software.
>
> **Corrections, re-scores, and removal are free.** No partnership, contract, or purchase is
> required, and you do not need to justify the request.
>
> - **Something wrong?** Open an issue on this repository, or email
>   [info@apievangelist.com](mailto:info@apievangelist.com).
> - **Published something new?** Ask for a re-score and we will re-run the rating.
> - **Want the listing taken down?** Say so and we will honor it. The profile is reduced to your
>   company name, a factual description, and a link to your own site, and the company is recorded as
>   **unrated** — never scored zero for having asked.
>
> **Response times.** Acknowledgement within **one business day**; removal or restriction within
> **two business days**; corrections and re-scores within **five business days**.
>
> **Not from the company, and here with a question?** You are welcome here — we would rather be the
> front line and point you the right way than have a good report go nowhere. What this repository
> can answer is narrow, though, so it is worth knowing who you are actually looking for:
>
> - **A question about how the API works, an account, billing, or a bug in the service** — that is
>   the company's own support, not us. We profile this API; we do not operate it and cannot see
>   your account.
> - **A bug in an open-source project we only catalog** — file it on that project's own repository.
>   This has happened with a real and correct bug report that reached us instead of the people who
>   could fix it, which helped nobody.
> - **Anything about this listing itself** — the description, the tags, the rating, a missing or
>   wrong artifact — is ours. Open an issue here.
> - **Not sure, or something general about API Evangelist or APIs.io** — open an issue on the
>   [APIs.io Inbox](https://github.com/api-search/inbox) and we will route it.
>
> **This repository contains no software, and we will never ask you to download anything.** There is
> no build, release, installer, or binary here — only text and machine-readable API descriptions, so
> there is nothing here that can be "corrupt" or need "repairing". Any issue, comment, or email
> claiming otherwise and offering a download link is not from us and is hostile. Do not follow the
> link; it is a lure. Report it to GitHub and, if you like, tell us at
> [info@apievangelist.com](mailto:info@apievangelist.com) so we can take it down.
>
> **On a security or compliance team?** Email
> [info@apievangelist.com](mailto:info@apievangelist.com) with *security* in the subject line and
> you will get a person, not a form. We will tell you exactly which public URLs this profile was
> built from so your team can see the same surface we did, and we will take the listing down on
> request while you work through it.
>
> Full detail: **[Where this data comes from](https://apievangelist.com/about/where-our-data-comes-from)**
<!-- API-EVANGELIST-PROVENANCE:END -->

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
