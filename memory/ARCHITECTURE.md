# Architecture Memory

Use this file for stable architectural knowledge: system structure, components, data flow, boundaries, constraints, and extension points.

Do not include coding conventions, implementation patterns, task plans, or detailed file inventories.

## System Overview

Describe the system shape in a few paragraphs: application type, runtime model, major subsystems, and how users or external systems interact with it.

Focus on what exists now.

## Major Components

List the major architectural components and each component's responsibility. Include boundaries that should be preserved during changes.

Avoid naming low-level classes, helpers, or files unless they define an architectural boundary.

## Data Flow

Explain the primary flow of data through the system, including key inputs, transformations, persistence points, and outputs.

Do not document every endpoint or function call.

## Authentication

Describe how identity, authentication, sessions, tokens, and authorization boundaries work at the system level.

Do not include implementation recipes or framework-specific coding patterns.

## Database Architecture

Describe databases, schemas, ownership boundaries, migration expectations, and data lifecycle constraints.

Do not copy schema definitions or table-by-table reference material.

## External Integrations

Describe external systems and how they fit into the architecture, such as payment providers, email services, analytics platforms, queues, storage, or identity providers.

Do not list incidental libraries or SDK installation details.

## Architectural Boundaries

Define boundaries between modules, services, layers, domains, or teams. Explain what must not cross those boundaries.

Use this section to prevent changes that collapse important separation.

## Architectural Constraints

Record constraints that materially affect design choices, such as latency goals, regulatory limits, offline support, data residency, compatibility, or deployment restrictions.

Do not include preferences that belong in `PATTERNS.md`.

## Extension Points

Describe where the system is intended to grow: plugin points, provider abstractions, module boundaries, integration adapters, or public APIs.

Do not invent extension points that do not exist.
