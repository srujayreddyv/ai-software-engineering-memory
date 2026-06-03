# AI Software Engineering Memory

## Overview

AI Software Engineering Memory is a lightweight repository knowledge layer for AI coding agents. It preserves context that cannot be reliably inferred from source code alone, such as architectural boundaries, engineering decisions, repository conventions, and long-term constraints.

The project is intentionally minimal. It provides reusable memory artifacts and templates, not an agent framework, workflow engine, CLI, automation system, review bot, IDE plugin, MCP server, or RAG system.

## Problem Statement

AI coding agents can already read code, search repositories, implement changes, run tests, and review work. What they often lack is durable repository memory between tasks.

Source code shows what exists now, but it rarely explains why boundaries were chosen, which tradeoffs matter, or which patterns should remain consistent. This repository captures that knowledge in short files that can be read before each task.

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

## Workflow

Before implementation, read the memory files and create a short task plan. During implementation, follow existing architecture and patterns, make minimal changes, and avoid unrelated refactoring. After implementation, review correctness, security, performance, maintainability, compatibility, and test coverage.

Update memory only when durable repository knowledge changes. Do not use memory files for task history, release notes, or notes that can be reconstructed from source code.

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
