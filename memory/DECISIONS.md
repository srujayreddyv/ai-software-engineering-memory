# Engineering Decisions

Use this file as a lightweight Architecture Decision Record log. Record only decisions that affect architecture, system boundaries, technology choices, infrastructure direction, or long-term maintainability.

Do not use this file as a change log, release notes, task history, or commit history.

When a decision is replaced, mark the old decision as `Superseded` and reference the replacement decision. Preserve decision history.

## 2026-06-03

### Title

Choose a Modular Monolith Instead of Microservices

### Status

Accepted

### Context

The product needs clear domain boundaries, but the team is small and the domain model is still evolving. Separate services would add deployment, observability, data consistency, and coordination overhead before the boundaries are proven.

### Decision

Use a modular monolith. Keep domain modules separated through application-layer boundaries while sharing one deployable application and one primary database.

### Alternatives Considered

Microservices were considered for independent scaling and deployment. A single unstructured application was considered for speed.

### Tradeoffs

The modular monolith keeps operational complexity low and makes cross-domain transactions simpler. It requires discipline to preserve module boundaries and may need future extraction if a module develops distinct scale, ownership, or reliability needs.

### Impact

New features should be added inside explicit domain modules. Cross-module access should use established interfaces rather than reaching into another module's internals. Service extraction remains possible if a boundary becomes stable and operationally justified.
