# BLACKOUT Initial Implementation Backlog

**Status:** Proposed planning baseline; not yet GitHub issues.  
**Sizing:** S 1–3h, M 3–6h, L 6–8h; decompose larger work.

## Epics
| Epic | Name | Outcome |
|---|---|---|
| BLK-01 | Project foundation | Reproducible Roblox workflow |
| BLK-02 | Round management | Full round lifecycle |
| BLK-03 | Roles | Secret role assignment |
| BLK-04 | Combat | Server-authoritative elimination |
| BLK-05 | Facility sabotage | Infected disruption |
| BLK-06 | Recovery objectives | Operative counterplay |
| BLK-07 | Facility map | Readable playable environment |
| BLK-08 | UI and experience | Role reveal, HUD, results, onboarding |
| BLK-09 | Progression | Optional XP, credits, cosmetics |
| BLK-10 | QA and security | Multiplayer and exploit validation |
| BLK-11 | Showcase | Polish and demonstration |
| BLK-12 | Immersive interaction | Hybrid world interaction framework |

## Ticket requirements
Every issue states objective/value, scope/exclusions, testable acceptance criteria, dependencies/source refs, deliverables, validation/evidence, size, and risk. Epics are containers, never directly assigned to workers.

## Foundation
### BLK-01-01 — Prove Roblox development toolchain (P0, M)
Document Studio/version, source synchronization (Rojo or verified alternative), test runner, launch/playtest, CI/assets, manual steps, and OH limitations. Demonstrate a small Luau change can sync, run, and be validated. Do not assume tools exist.

### BLK-01-02 — Repository conventions and structure (P0, S)
Define source/test/assets layout, naming, formatting, and validation command after toolchain inspection.

### BLK-01-03 — Luau test baseline (P0, M)
Select a supported runner, add one passing deterministic test, document local/CI invocation.

## Core gameplay
### BLK-02-01 — Round state model (P0, M)
Explicit lobby, role assignment, preparation, active, results states; reject invalid transitions; server owns transitions; tests cover valid/invalid paths.

### BLK-02-02 — Player eligibility and lifecycle (P0, M)
Handle insufficient players and disconnects; resolve and return to lobby; test multiplayer cases.

### BLK-03-01 — Secret role assignment (P0, M)
Assign Infected, Sentinel, Operative according to approved player-count rules; disclose role only to relevant player; tests verify no role leakage.

### BLK-04-01 — Elimination contract (P0, M)
Validate role, phase, target, range, cooldown, eligibility; reject duplicate/stale requests; client cannot eliminate directly; negative tests.

### BLK-05-01 — Sabotage service (P1, M)
Validate role/phase/cooldown; change authoritative facility state; deterministic effect expiry; test one sabotage.

### BLK-06-01 — Recovery objective contract (P1, M)
Validate eligibility/task state; prevent forged progress; idempotent completion; allow objective to resolve round.

## Hybrid interaction workstream BLK-12
### BLK-12-01 — Define interaction contracts (P1, S)
Trusted target/action identity, client intent schema, server validation responsibilities; UI owns no game rules.

### BLK-12-02 — Server interaction registry (P1, M)
Register known targets; reject unknown IDs; do not trust client definitions; tests for registration/lookup.

### BLK-12-03 — Validated interaction gateway (P1, M)
Validate player, target, action, range, role, phase, and rate; dispatch approved actions; invalid requests cause no state change.

### BLK-12-04 — Contextual interaction prompt (P1, M)
Show action/target/input binding; reusable by two stations; never imply success before server confirmation.

### BLK-12-05 — Cyberpunk UI tokens/components (P1, M)
Define color, typography, spacing, icon rules; reusable panel/button/status/prompt; preserve readability.

### BLK-12-06 — Reusable terminal framework (P1, M)
One terminal shell with data-driven station content, lifecycle/focus handling, server-confirmed updates.

### BLK-12-07 — Armory/equipment selection (P1, M)
Inspect/select permitted equipment; server validates eligibility/ownership; reject invalid selection.

### BLK-12-08 — Operations board (P1, M)
Present match/deployment state; validate selection; reflect authoritative queue/deployment state.

### BLK-12-09 — Context-sensitive radial menu (P2, L)
Reliable open/close; actions from permitted context; no hidden-role leakage; input alternatives; server validates state changes.

### BLK-12-10 — Role-aware match HUD (P1, M)
Show phase/timer/permitted objectives; disclose role-specific data only to authorized player; essential information available without terminals.

### BLK-12-11 — Input accessibility (P1, L)
Support essential interactions on agreed input modes; visible focus/selection; legible target sizes; test evidence.

## QA
### BLK-10-01 — Multiplayer scenario matrix (P1, M)
Round start/end, disconnects, role privacy, sabotage, recovery, win conditions; reproducible steps and expected outcomes.

### BLK-10-02 — Exploit-boundary matrix (P1, M)
Malformed remotes, forged targets, out-of-range requests, cooldown bypass, role spoofing, duplicate rewards, stale requests; expected server behavior.

## Backlog governance
Backlog Architect deduplicates, preserves human priorities, distinguishes design status, decomposes oversized work, records dependencies/blockers, avoids busywork tickets, and requires evidence before closure. This seed plan must be reconciled against the actual repository and verified Roblox toolchain before issues are created.