# Implementation Patterns

Use this file for repository conventions and implementation patterns. It should help an AI agent make changes that fit the existing codebase.

Do not duplicate architecture documentation or record one-off task decisions.

## API Pattern

Describe how APIs are structured, validated, authenticated, versioned, and tested. Include naming conventions, response shapes, and error response expectations when they are repository-specific.

Do not list every endpoint.

## Database Pattern

Describe how database access is organized, including query ownership, transactions, migrations, seed data, and test fixtures.

Do not repeat schema documentation from architecture memory.

## Authentication Pattern

Describe the implementation conventions for identity checks, permission checks, session handling, and protected routes or actions.

Do not restate system-level authentication architecture.

## Error Handling Pattern

Describe how expected errors, unexpected failures, validation issues, retries, and user-visible messages should be handled.

Include conventions for logging or alerting only when they are tied to error handling.

## Testing Pattern

Describe preferred test types, naming conventions, fixture usage, mocking boundaries, and when to add regression tests.

Do not include a full test strategy for every feature.

## Logging Pattern

Describe logging levels, structured fields, correlation IDs, sensitive data rules, and where logs are expected to appear.

Do not document observability architecture beyond implementation conventions.

## Dependency Management Pattern

Describe how new dependencies are evaluated, added, upgraded, pinned, or avoided. Include repository-specific constraints such as bundle size, license, runtime support, or security review.

Do not mirror lockfile contents.
