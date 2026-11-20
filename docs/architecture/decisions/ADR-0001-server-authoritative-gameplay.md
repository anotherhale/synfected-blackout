# ADR-0001: Server-Authoritative Gameplay

- Status: Accepted for BLACKOUT
- Date: 2026-11-19

## Context
Hidden roles, combat, sabotage, recovery objectives, and rewards must resist client manipulation.

## Decision
The Roblox server is authoritative for round lifecycle, roles, elimination, sabotage, objectives, rewards, progression grants, and interaction authorization. Clients send intent and render approved state.

## Consequences
Consistent multiplayer outcomes and auditable transitions, at the cost of explicit RemoteEvent contracts, validation, and server-side tests.

## Required validation
Validate player, action, target, game phase, role, range, cooldown/rate, and prerequisites as applicable.