# SAP Litmos GraphQL Schema

## Overview

This document describes a conceptual GraphQL schema for the SAP Litmos Learning Management System (LMS) REST API. The schema models the core Litmos domain — courses, modules, learning paths, assessments, users, teams, enrollments, completions, and reporting — as GraphQL types, queries, and mutations.

The source REST API is documented at:
- https://support.litmos.com/hc/en-us/articles/227734407-API-documentation
- https://www.litmos.com/docs/litmos/apis/overview-of-developer-api

Authentication is via API key passed as a request header (`apikey`). All endpoints return JSON or XML and are versioned under `/v1.svc`.

## Schema Source

**Source type:** Conceptual — derived from the Litmos REST API reference documentation.

The GraphQL schema in `litmos-schema.graphql` was authored by mapping Litmos REST resources and their JSON response shapes to GraphQL types. No official GraphQL endpoint is published by SAP Litmos.

## Domain Model

### Courses and Learning Content

The core content objects in Litmos:

- **Course** — A training course containing one or more modules. Has status, availability, and metadata.
- **CourseDetails** — Extended course metadata including custom fields, certificate settings, and compliance options.
- **Module** — An individual learning unit within a course (video, SCORM, quiz, etc.).
- **ModuleDetails** — Extended module metadata including completion criteria and ordering.
- **ModuleType** — Enum describing the kind of module (Video, SCORM, PDF, Assessment, etc.).
- **LearningPath** — An ordered collection of courses forming a structured curriculum.
- **LearningPathDetails** — Extended learning path metadata with enrollment and completion rules.
- **ContentType** — Enum for content delivery format.
- **File** — Binary or media asset attached to a module or course.

### Assessments

- **Assessment** — A quiz or test attached to a course or module.
- **AssessmentDetails** — Extended assessment config: pass score, retake policy, shuffle settings.
- **Question** — An individual question within an assessment.
- **QuestionType** — Enum: MultipleChoice, TrueFalse, FillInTheBlank, Matching, etc.
- **Answer** — A possible answer choice for a question.
- **Attempt** — A single learner attempt at an assessment.
- **AttemptDetails** — Extended attempt data including per-question responses and timing.

### Users and Teams

- **User** — A learner or administrator account in Litmos.
- **UserDetails** — Extended user profile including custom fields, locale, and SSO identifiers.
- **UserStatus** — Enum: Active, Inactive, Pending.
- **Team** — An organizational grouping of users.
- **TeamDetails** — Extended team metadata including parent/child hierarchy.
- **TeamMember** — Junction type linking a User to a Team with role information.
- **Manager** — A user with administrative or supervisory rights over a team.
- **DirectReport** — A user who reports to a Manager.
- **Group** — A dynamic grouping of users based on criteria.
- **GroupDetails** — Extended group metadata with membership rules.

### Enrollment and Progress

- **Enrollment** — A user's assignment to a course or learning path.
- **EnrollmentDetails** — Extended enrollment data including due dates and re-enrollment policy.
- **Assignment** — An explicit assignment of a course or path to a user or team.
- **Progress** — A learner's current progress percentage within a course.
- **ProgressDetails** — Module-level progress breakdown.
- **Milestone** — A significant point in a learning path (e.g., completion of a phase).

### Completions and Results

- **Completion** — A record that a user has completed a course.
- **CompletionDetails** — Extended completion data: score, date, pass/fail, time spent.
- **Result** — Aggregate result for a user across a course or assessment.
- **ResultDetails** — Per-module or per-question result breakdown.
- **Certificate** — A completion certificate issued to a learner.
- **CertificateDetails** — Extended certificate metadata including expiration and reissue dates.

### Reporting

- **Reporting** — Top-level reporting resource for fetching training records.
- **ReportDetails** — A structured report result set with pagination and filter metadata.
- **CustomField** — User-defined metadata fields attached to users, courses, or teams.

### Authentication and Integration

- **APIKey** — An API key credential for authenticating REST API calls.
- **Token** — A session or access token for OAuth flows.
- **Webhook** — A registered callback URL for receiving Litmos events.
- **WebhookEvent** — An event payload delivered to a registered webhook.
- **SSO** — Single sign-on configuration for a Litmos account.
- **SAML** — SAML 2.0 SSO configuration details.
- **OAuth** — OAuth 2.0 authorization configuration.
- **OAuthDetails** — Extended OAuth configuration including scopes and token endpoints.

## GraphQL Operations

### Queries

| Query | Description |
|---|---|
| `courses` | List all courses with pagination |
| `course(id: ID!)` | Fetch a single course by ID |
| `learningPaths` | List all learning paths |
| `learningPath(id: ID!)` | Fetch a single learning path |
| `users` | List all users |
| `user(id: ID!)` | Fetch a single user |
| `teams` | List all teams |
| `team(id: ID!)` | Fetch a single team |
| `enrollments` | List enrollments with filters |
| `completions` | List completion records |
| `assessments` | List assessments |
| `reports` | Fetch training reports |

### Mutations

| Mutation | Description |
|---|---|
| `createUser` | Provision a new user |
| `updateUser` | Update user profile fields |
| `deactivateUser` | Set user status to Inactive |
| `enrollUser` | Enroll a user in a course or learning path |
| `unenrollUser` | Remove a user enrollment |
| `assignCourseToTeam` | Assign a course to all members of a team |
| `createTeam` | Create a new team |
| `addTeamMember` | Add a user to a team |
| `removeTeamMember` | Remove a user from a team |
| `registerWebhook` | Register a new webhook endpoint |
| `deleteWebhook` | Remove a webhook registration |

## Notes

- The Litmos REST API uses API key authentication; OAuth flows are available for SSO integrations.
- All list operations in the REST API are paginated using `limit` and `start` query parameters, modeled here as `PaginationInput`.
- Custom fields are first-class citizens in Litmos and appear on User, Course, and Team resources.
- Rate limits apply per account tier; see `rate-limits/litmos-rate-limits.yml` for details.
