# AI Software Engineering Memory

## Overview

AI Software Engineering Memory is a lightweight repository knowledge layer for AI coding agents. It preserves context that cannot be reliably inferred from source code alone, such as architectural boundaries, engineering decisions, repository conventions, and long-term constraints.

The project is intentionally minimal. It provides reusable memory artifacts and templates that can be copied into software repositories.

## Repository Memory Standard

AI Software Engineering Memory is a lightweight repository memory standard for AI coding agents. The goal is to create a small, consistent set of memory artifacts that preserve repository knowledge across tasks.

It is designed to be repository-centric rather than agent-centric. The memory lives with the code so different agents and contributors can use the same durable context.

## Problem Statement

AI coding agents can already read code, search repositories, implement changes, run tests, and review work. What they often lack is durable repository memory between tasks.

Source code shows what exists now, but it rarely explains why boundaries were chosen, which tradeoffs matter, or which patterns should remain consistent. This repository captures that knowledge in short files that can be read before each task.

Without this memory, agents often rediscover the same context repeatedly, make plausible but inconsistent architectural choices, or miss constraints that were obvious to the team but not encoded in the code. A small memory layer helps future work start from the repository's actual history and conventions.

## Core Concepts

**Memory over process:** Store stable repository knowledge, not detailed workflows. If an AI agent can easily infer information from source code, it should not be stored in memory.

**Small context wins:** Keep every file short enough to read before a task.

**Single responsibility:** Agent behavior, repository memory, planning templates, and review templates each live in their own files.

**Decision preservation:** Record significant architectural decisions and tradeoffs without turning the log into release notes.

## What This Is Not

This project is not:

* An agent framework
* A workflow engine
* A RAG system
* An MCP server
* A coding assistant

This project is a repository memory layer.

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

1. Copy `AGENTS.md`, `memory/`, and `templates/` into a repository.
2. Fill the memory files with durable repository knowledge.
3. Create a task plan before implementation when the task requires judgment.
4. Review work after implementation.
5. Update memory only when repository knowledge changes.

## How to Use This in a Repository

Add these files to any software project where AI coding agents help with implementation, review, planning, or maintenance. The files should be committed with the code so every future task starts with the same repository knowledge.

Before asking an agent to make a change, tell it to read `AGENTS.md` and the files in `memory/`. The agent should use that context to understand the codebase, preserve architectural boundaries, follow established patterns, and create a short plan before editing.

Use `templates/TASK_PLAN_TEMPLATE.md` for tasks that require judgment, multiple files, behavior changes, migrations, or meaningful risk. For trivial edits, the template can be used lightly, but the agent should still state assumptions and verification steps.

Use `templates/REVIEW_TEMPLATE.md` after implementation to check correctness, security, performance, maintainability, backward compatibility, and test coverage. The review should focus on risks and missed requirements, not process compliance.

Update the memory files only when durable knowledge changes. Good updates include new architectural boundaries, important constraints, adopted implementation patterns, major dependency choices, or decisions that future contributors should not have to rediscover. Do not add ordinary task notes, commit summaries, or information that is obvious from reading the source code.

## Workflow

Before implementation, read the memory files and create a short task plan. During implementation, follow existing architecture and patterns, make minimal changes, and avoid unrelated refactoring. After implementation, review correctness, security, performance, maintainability, compatibility, and test coverage.

Update memory only when durable repository knowledge changes. Do not use memory files for task history, release notes, or notes that are clear from source code.

The intended loop is:

1. Read memory.
2. Plan the task.
3. Implement the smallest suitable change.
4. Verify the result.
5. Review the work.
6. Update memory only if lasting repository knowledge changed.

## Success Criteria

The repository is helping when users see:

* Less repeated repository discovery
* More consistent implementations
* Fewer architectural violations
* Better implementation plans
* Faster onboarding for AI coding agents

## Example Task Usage

Use prompts like these when working with an AI coding agent:

```text
Read AGENTS.md and the memory files first.

Task: Add support for exporting invoices as CSV.

Create a short task plan before editing. Preserve the billing module boundary,
follow existing API and testing patterns, and update memory only if durable
repository knowledge changes.
```

```text
Read AGENTS.md and the memory files first.

Task: Fix duplicate payment webhook processing.

Use the memory files to understand the payment flow, idempotency conventions,
and testing pattern. Add a regression test, make the smallest fix, and review
correctness and risk before finalizing.
```

```text
Read AGENTS.md and the memory files first.

Task: Review this pull request.

Lead with bugs, regressions, security issues, missing tests, architectural
violations, and maintainability risks. Keep the summary brief.
```

```text
Read AGENTS.md and the memory files first.

Task: Refactor invoice status calculation without changing behavior.

Preserve architectural boundaries, follow existing naming and testing patterns,
and verify behavior before and after the refactor.
```

```text
Read AGENTS.md and the memory files first.

Task: Add an invoice export requested timestamp to the database.

Check data ownership, lifecycle constraints, migration conventions, fixture
impact, rollout risk, and rollback risk before editing.
```

```text
Read AGENTS.md and the memory files first.

Task: Add regression coverage for invoice export permissions.

Find the relevant test suites and commands. Follow fixture, mocking, naming,
and assertion conventions. Add the smallest test that proves the behavior.
```

```text
Read AGENTS.md and the memory files first.

Task: Upgrade the payment provider SDK.

Find integration points, follow dependency management rules, preserve relevant
technology tradeoffs, and verify security, compatibility, and rollback risk.
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
