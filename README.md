# Litmos

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

SAP Litmos is a cloud-based learning management system (LMS) with a REST API for managing courses, learning paths, user enrollment, completions, assessments, and training compliance reporting. The API enables organizations to automate user provisioning, synchronize training data with HR and CRM systems, manage teams, and retrieve completion records for compliance workflows.

## API Overview

The Litmos REST API is available at `https://api.litmos.com/v1.svc` (US), `https://api.litmoseu.com/v1.svc` (EU), and `https://api.litmos.com.au/v1.svc` (AU). All requests must be made over HTTPS and authenticated using an API key passed as a request header. Both JSON and XML data formats are supported.

## Key Resources

- **Users** - Create, update, delete, and retrieve user accounts; manage active/inactive status
- **Teams** - Organize users into teams; manage team membership and leadership
- **Courses** - Retrieve course listings and assign courses to teams and users
- **Learning Paths** - Manage learning path assignments and track user progress
- **Enrollments** - Enroll users in courses and learning paths
- **Completions** - Retrieve course and module completion records for compliance reporting
- **Assessments** - Access assessment results and scores
- **Reports** - Pull training compliance and activity reports

## Authentication

Every request must include an API key as a header parameter. Access to the API is limited to Litmos Account Owners. The API is not available on Trial accounts.

```
apikey: YOUR_API_KEY
```

## Rate Limits

- 100 requests per minute per site (all paid plans)
- Maximum 1,000 records returned per single request
- Pagination supported for large datasets

## Pricing

Litmos offers three tiers: **Foundation**, **Platinum**, and **Platinum AI**. All plans include API access. Pricing is quote-based and depends on active learner count, feature tier, and contract length. Estimated range: $4-$15 per active learner per month (annual contract).

## Webhooks

The Litmos Webhooks feature (premium add-on) delivers real-time POST notifications to your endpoint when subscribed events occur in the LMS, eliminating the need for continuous API polling.

## Links

- [API Documentation](https://www.litmos.com/docs/litmos/apis/overview-of-developer-api)
- [Pricing](https://www.litmos.com/litmos-pricing)
- [Webhooks](https://www.litmos.com/docs/litmos/webhooks)
- [Integrations](https://www.litmos.com/features/integrations)
- [Support](https://support.litmos.com)
- [Release Notes](https://www.litmos.com/release-notes/tags/api)
- [Node.js SDK (community)](https://github.com/Trifoia/litmos-sdk)
- [Python SDK (community)](https://python-litmos-api.readthedocs.io/en/latest/readme.html)
