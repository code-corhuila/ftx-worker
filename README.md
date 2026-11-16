# ftx-worker

> Asynchronous jobs and background processing

Part of **Futbolix**, the distributed system for reserving the four football courts of a
single sports facility (team `futbolix`, Group 1). Governance and documentation live in
[`ftx-docs`](https://github.com/code-corhuila/ftx-docs).

## Status in MVP 3 (`v3.0.0`)

**This repository contains no application code yet.** It is reserved for work that must run
outside the request path of the APIs (background jobs, scheduled tasks).

In MVP 3 the asynchronous work is done inside the services themselves, not here:

- `ftx-reservations-api` stores each domain event in a transactional outbox and publishes it to
  RabbitMQ, so an event is not lost while the broker is down (ADR-006, ADR-010).
- The platform that runs those services and the broker is composed in
  [`ftx-workflow`](https://github.com/code-corhuila/ftx-workflow).

Nothing in the running system depends on this repository.

## Next steps

- Decide with the team which job, if any, justifies a separate worker (for example, delivery of
  notifications or reconciliation of payments once the payment service exists).
- Record that decision in an ADR in `ftx-docs` before adding code.

## Branching

Three permanent branches. **None of them accepts a direct commit**: you enter through a child
branch and leave through a Pull Request.



Promotion happens **by re-application** (`git cherry-pick -x`), never by merging one permanent
branch into another.

`main` requires **1 approval from `ariel5253`**. Full policy:
`00-governance/branching-policy.md` in [`ftx-docs`](https://github.com/code-corhuila/ftx-docs).
