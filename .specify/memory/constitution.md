<!--
Sync Impact Report
Version change: none -> 1.0.0
Modified principles: added security, maintainability, code quality, minimal scope, incremental architecture
Added sections: MVP Constraints and Runtime Standards, Development Workflow, Governance
Removed sections: none
Templates reviewed: .specify/templates/plan-template.md ✅ aligned; .specify/templates/spec-template.md ✅ aligned; .specify/templates/tasks-template.md ✅ aligned
Deferred items: none
-->

# RSS Feed Reader Constitution

## Core Principles

### I. Secure by Default
All input, feed URLs, and UI state MUST be treated as untrusted. The application MUST never render raw feed content or unescaped HTML, and all user-visible strings MUST be encoded before display. Security is mandatory for every phase, including MVP.

### II. Maintainability First
Code MUST be organized to support future extension without a full rewrite. Frontend and backend responsibilities MUST remain clearly separated, implementation details MUST be modular, and duplication or hidden dependencies MUST be avoided.

### III. Code Quality and Testability
Every deliverable MUST include a defined verification path before implementation. Acceptance criteria, regression tests, or explicit validation checks MUST be established before code is written, and implementation MUST support easy review and repeatable testing.

### IV. Minimal Scope, Clear Behavior
The MVP MUST only implement subscription management and list display. Initial delivery MUST NOT include feed fetching, parsing, persistence, or URL validation beyond safe string capture and handling. Any scope expansion MUST be deferred to Extended-MVP.

### V. Incremental Architecture for Future Extensions
The design MUST preserve clear extension points for later feed fetching, persistence, manual refresh, and background operations. Early choices MUST avoid hard-coded assumptions that would force a rewrite when moving beyond in-memory subscriptions.

## MVP Constraints and Runtime Standards

- The MVP MUST use the ASP.NET Core Web API backend and Blazor WebAssembly frontend architecture described in project context.
- Subscription storage for initial delivery MUST remain in memory only; persistence is out of scope until Extended-MVP.
- The frontend and backend MUST coordinate localhost ports and CORS settings for local development, with configuration explicit in `wwwroot/appsettings.json`, `launchSettings.json`, and backend CORS policy.
- Feed URLs entered by users MUST be handled safely; the application MUST not assume network access and MUST not render raw feed content directly in the UI.
- Runtime behavior MUST be observable through UI feedback or logs, and any non-obvious implementation decisions MUST be documented in project notes.

## Development Workflow

- Work MUST begin from a clear, testable user story or acceptance scenario before implementation.
- Foundational setup work (project structure, route cleanup, configuration, architecture) MUST complete before feature implementation begins.
- Every pull request MUST reference at least one applicable constitution principle and explain how the change preserves security, maintainability, or quality.
- Exceptions to this constitution MUST be documented explicitly and approved by the project lead before merge.
- Reviewers MUST verify constitution compliance as part of the definition of done.

## Governance

This constitution is authoritative for project architecture, security decisions, maintainability standards, and code quality expectations. If this constitution conflicts with any other project document, this constitution takes precedence.

Amendments require:
- a documented change in this file,
- a short rationale for the change,
- and a verification note explaining how affected work items will be revalidated.

Versioning policy:
- MAJOR bump for backward-incompatible principle changes or removed governance rules.
- MINOR bump for added principles, new mandatory constraints, or expanded workflow requirements.
- PATCH bump for wording clarifications and editorial improvements that do not alter meaning.

Compliance review expectations:
- Every development artifact (spec, plan, tasks, PR) SHOULD reference at least one applicable principle.
- Security, quality, and maintainability requirements MUST be evaluated during code review.
- Any deviation from this constitution MUST include a documented exception and a planned follow-up.

**Version**: 1.0.0 | **Ratified**: 2026-06-08 | **Last Amended**: 2026-06-08
