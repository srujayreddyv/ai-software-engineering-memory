# AI Software Engineering Memory

## Overview

AI Software Engineering Memory is a lightweight repository knowledge layer for AI coding agents. It preserves context that cannot be reliably inferred from source code alone, such as architectural boundaries, engineering decisions, repository conventions, and long-term constraints.

The project is intentionally minimal. It provides reusable memory artifacts and templates, not an agent framework, workflow engine, CLI, automation system, review bot, IDE plugin, MCP server, or RAG system.

## Problem Statement

AI coding agents can already read code, search repositories, implement changes, run tests, and review work. What they often lack is durable repository memory between tasks.

Source code shows what exists now, but it rarely explains why boundaries were chosen, which tradeoffs matter, or which patterns should remain consistent. This repository captures that knowledge in short files that can be read before each task.

Without this memory, agents often rediscover the same context repeatedly, make plausible but inconsistent architectural choices, or miss constraints that were obvious to the team but not encoded in the code. A small memory layer helps future work start from the repository's actual history and conventions.

## Core Concepts

**Memory over process:** Store stable repository knowledge, not detailed workflows.

**Small context wins:** Keep every file short enough to read before a task.

**Single responsibility:** Agent behavior, repository memory, planning templates, and review templates each live in their own files.

**Decision preservation:** Record significant architectural decisions and tradeoffs without turning the log into release notes.

## Repository Structure

```text
ai-software-engineering-memory/
  README.md
  AGENTS.md
  memory/
    CODEBASE.md
    ARCHITECTURE.md
    PATTERNS.md
    DECISIONS.md
  templates/
    TASK_PLAN_TEMPLATE.md
    REVIEW_TEMPLATE.md
```

`AGENTS.md` defines behavior for AI coding agents.

`memory/` contains durable repository knowledge.

`templates/` contains reusable planning and review artifacts.

## Quick Start

1. Copy `AGENTS.md` into a repository.
2. Create `memory/CODEBASE.md`, `memory/ARCHITECTURE.md`, `memory/PATTERNS.md`, and `memory/DECISIONS.md`.
3. Create a task plan before implementation.
4. Review work after implementation.
5. Update memory when repository knowledge changes.

## How to Use This in a Repository

Add these files to any software project where AI coding agents help with implementation, review, planning, or maintenance. The files should be committed with the code so every future task starts with the same repository knowledge.

Before asking an agent to make a change, tell it to read `AGENTS.md` and the files in `memory/`. The agent should use that context to understand the codebase, preserve architectural boundaries, follow established patterns, and create a short plan before editing.

Use `templates/TASK_PLAN_TEMPLATE.md` for tasks that require judgment, multiple files, behavior changes, migrations, or meaningful risk. For trivial edits, the template can be used lightly, but the agent should still state assumptions and verification steps.

Use `templates/REVIEW_TEMPLATE.md` after implementation to check correctness, security, performance, maintainability, backward compatibility, and test coverage. The review should focus on risks and missed requirements, not process compliance.

Update the memory files only when durable knowledge changes. Good updates include new architectural boundaries, important constraints, adopted implementation patterns, major dependency choices, or decisions that future contributors should not have to rediscover. Do not add ordinary task notes, commit summaries, or information that is obvious from reading the source code.

## Workflow

Before implementation, read the memory files and create a short task plan. During implementation, follow existing architecture and patterns, make minimal changes, and avoid unrelated refactoring. After implementation, review correctness, security, performance, maintainability, compatibility, and test coverage.

Update memory only when durable repository knowledge changes. Do not use memory files for task history, release notes, or notes that can be reconstructed from source code.

The intended loop is:

1. Read memory.
2. Plan the task.
3. Implement the smallest suitable change.
4. Verify the result.
5. Review the work.
6. Update memory only if lasting repository knowledge changed.

## Example Task Usage

Use the memory files as task context, not as a replacement for reading code.

For a feature request:

```text
Read AGENTS.md and the memory files first.

Task: Add support for exporting invoices as CSV.

Create a short task plan before editing. Pay attention to existing API,
database, testing, and logging patterns. Preserve the billing module boundary.
After implementation, review the work and update memory only if this introduces
a durable new pattern or architectural decision.
```

For a bug fix:

```text
Read AGENTS.md and the memory files first.

Task: Fix duplicate payment webhook processing.

Use CODEBASE.md to find the webhook handler, ARCHITECTURE.md to understand the
payment flow, PATTERNS.md to follow the existing idempotency and testing
conventions, and DECISIONS.md to preserve relevant tradeoffs. Add or update a
regression test, then review correctness and risk before finalizing.
```

For a code review:

```text
Read AGENTS.md and the memory files first.

Task: Review the pull request for the account settings change.

Check whether the change preserves architectural boundaries, follows existing
patterns, updates the right tests, and avoids unrelated refactoring. Lead with
bugs, regressions, security issues, missing tests, and maintainability risks.
```

For a refactor:

```text
Read AGENTS.md and the memory files first.

Task: Refactor invoice status calculation for readability without changing
behavior.

Use CODEBASE.md to locate the relevant module, ARCHITECTURE.md to preserve
boundaries, and PATTERNS.md to keep naming, testing, and error handling
consistent. Verify behavior before and after the refactor.
```

For database or migration work:

```text
Read AGENTS.md and the memory files first.

Task: Add a column that tracks when an invoice export was requested.

Use ARCHITECTURE.md to understand data ownership and lifecycle constraints.
Use PATTERNS.md for migration, transaction, fixture, and test conventions.
Document rollout or rollback risk in the task plan before editing.
```

For testing work:

```text
Read AGENTS.md and the memory files first.

Task: Add regression coverage for invoice export permissions.

Use CODEBASE.md to find the relevant test suites and commands. Use PATTERNS.md
to follow fixture, mocking, naming, and assertion conventions. Add the smallest
test that proves the behavior and run the focused test command before final
review.
```

For a dependency upgrade:

```text
Read AGENTS.md and the memory files first.

Task: Upgrade the payment provider SDK.

Use CODEBASE.md to find integration points, PATTERNS.md to follow dependency
management rules, and DECISIONS.md to preserve past technology tradeoffs.
Verify affected tests and review security, compatibility, and rollback risk.
```

## Example Memory Snapshot

**Repository Overview:** A billing service that manages subscriptions, invoices, and payment provider callbacks.

**Architecture Summary:** The service is a modular monolith. Billing, account, and notification modules share one database but expose separate application-layer boundaries.

**Pattern:** New external callbacks are handled through idempotent command handlers with provider payloads stored before processing.

**Decision:** The team chose a modular monolith over microservices to keep transaction boundaries simple while the product and team are still small.

## Future Ideas

Future versions may add security memory, testing memory, deployment memory, incident memory, domain memory, architecture diagrams, subdirectory memory support, repository automation, MCP integration, or decision validation tooling.

These are not part of v1.

## License

MIT
