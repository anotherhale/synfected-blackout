# ADR-0003: No Runtime LLM Dependency in MVP

- Status: Accepted for BLACKOUT MVP
- Date: 2026-11-19

## Context
The 30-day target is a reliable Roblox vertical slice. Runtime LLM behavior adds latency, cost, moderation, privacy, and reliability dependencies unnecessary to prove the core loop.

## Decision
MVP gameplay rules, sabotage, objectives, role assignment, and facility behavior are deterministic and server-authoritative. Development-time AI assistance through CIPHER/OH is separate from runtime game behavior.

## Consequences
Lower runtime complexity and predictable tests. Any future runtime AI requires a separate proposal, safety review, cost model, and ADR.