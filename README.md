# Litmos

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
