# BLACKOUT Project Charter

**Parent product:** SYNFECTED: RESISTANCE  
**Platform:** Roblox  
**Target:** 30-day playable vertical slice  
**Status:** Initial project baseline

## Mission
Build an original, replayable multiplayer social-deduction game in the SYNFECTED universe while demonstrating a repeatable autonomous development workflow coordinated by CIPHER and executed through OpenHands (OH).

## Outcomes
1. Deliver a playable experience with a complete round loop, distinctive facility atmosphere, clear roles, sabotage/recovery decisions, and onboarding.
2. Demonstrate specialized autonomous workers delivering bounded changes with independent validation and traceable evidence.
3. Measure completed work, test results, defects, rework, human intervention, execution failures, and cost where available.

## Product boundaries
BLACKOUT is a focused SYNFECTED: RESISTANCE experience, not a replacement for the franchise GDD and not a Syndicate simulation. It does not inherit Syndicate's advanced NPC, economy, or SIN systems.

## MVP scope
- Multiplayer round lifecycle and three roles.
- One compact facility map initially; second map is stretch.
- Server-authoritative elimination and win conditions.
- At least two sabotage actions and two recovery task types.
- Lobby, role reveal, round HUD, results.
- Hybrid in-world interactions and accessible overlays.
- Multiplayer, exploit-boundary, and regression testing.
- Basic progression only if the core loop is stable.

Out of scope: open world, procedural maps, trading, guild economy, persistent NPC populations, AI-controlled players, runtime LLM, complex inventory, multiple modes, paid competitive advantages, blockchain/crypto.

## Operating principles
- CIPHER coordinates and delegates; it is not the monolithic implementer.
- OH remains the execution/orchestration substrate.
- Deterministic game services authorize authoritative transitions.
- No worker approves its own implementation.
- Human priorities and approval constraints take precedence.
- No merge, publish, or release authority is implied.
- Completion claims require code and test evidence.
- Proposed ideas are not silently promoted to approved design.

## Success measures
A new player can understand and complete a round; full rounds reliably resolve; role, combat, sabotage, objective, and reward authority is server-side; tested multiplayer scenarios pass; critical defects are addressed; agent work is traceable; intervention, rework, and cost are measured.

## Risks
| Risk | Mitigation |
|---|---|
| Roblox Studio workflow unproven | Prove source sync, Studio integration, tests, and repeatability first |
| Multiplayer state defects | Server authority and early multiplayer tests |
| Scope creep | Protect vertical-slice boundary |
| Worker conflicts | Isolated branches/workspaces and task claims |
| Backlog inflation | Deduplication and acceptance-quality gate |
| UI polish delays gameplay | Round loop remains critical path |
| Diegetic UI accessibility | Provide overlay/input alternatives |
| IP imitation | Original names, assets, maps, text, and presentation |

## Initial exit criteria
Documents, architecture boundaries, decision log, workflow, agent contract, and actionable backlog exist; a small Luau task has been completed and validated through the actual OH/Roblox toolchain.