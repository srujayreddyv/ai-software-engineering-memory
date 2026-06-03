# Codebase Memory

Use this file as the repository inventory and navigation guide. Capture durable facts that help a human or AI agent understand where things live and how to orient before a task.

Do not include architecture rationale, coding conventions, task history, or long tutorials.

## Repository Overview

Describe the repository at a glance: product area, primary users, runtime shape, and major capabilities. Keep this to the facts someone needs before reading source code.

Do not repeat the README or include marketing language.

## Purpose

Explain what problem this repository solves and which responsibilities belong here.

Do not describe implementation patterns or future wishlist items.

## Applications

List user-facing applications, admin tools, workers, or packaged deliverables maintained in this repository. Include the directory and a one-line responsibility for each.

Do not list every route, page, or component.

## Services

List backend services, background workers, scheduled jobs, or internal service modules. Include ownership boundaries and how each service is invoked.

Do not duplicate data flow details from `ARCHITECTURE.md`.

## Major Directories

Map important directories to their purpose. Focus on directories that affect navigation, ownership, or change planning.

Do not document generated files, build outputs, or obvious names unless they carry repository-specific meaning.

## External Dependencies

Record important third-party systems, hosted services, SDKs, or platform dependencies. Note why each dependency matters.

Do not maintain a full package manifest by hand.

## Build Commands

List the commands required to build the repository or its major deliverables. Include prerequisites only when they are not obvious from standard tooling.

Do not include lengthy setup guides.

## Test Commands

List the commands used for unit, integration, end-to-end, and specialized tests. Note any tests that require services, fixtures, or environment variables.

Do not duplicate every test file or assertion.

## Deployment Process

Summarize how this repository reaches production or other shared environments. Include deployment owners, environments, and manual gates when relevant.

Do not turn this section into a runbook.

## Known Risk Areas

Identify parts of the repository where changes commonly require extra care, such as migrations, auth flows, billing, data deletion, or external callbacks.

Do not list speculative risks or ordinary bugs.
