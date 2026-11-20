# BLACKOUT Technical Architecture

**Version:** 0.1 | **Status:** Proposed baseline | **Runtime:** Roblox/Luau  
**Development orchestration:** OpenHands (OH), coordinated by CIPHER

## 1. Goals
Server-authoritative multiplayer simulation; client/server separation; modular gameplay domains; testable state transitions; reusable world interaction/UI; cost-conscious vertical slice; reproducible source-to-Studio workflow.

## 2. System context
Clients handle input, camera, UI/effects, local affordance discovery, and intent requests. Roblox server owns round lifecycle, role assignment, combat/elimination, sabotage, objectives, rewards/progression, interaction authorization, and persistence boundary. Roblox platform services provide player/session, persistence, and server infrastructure. CIPHER/OH are development-time systems, not runtime game components.

## 3. Logical modules
| Module | Responsibility |
|---|---|
| RoundManager | Round lifecycle and phase transitions |
| RoleAssignmentService | Role distribution and secrecy |
| CombatService | Validated elimination |
| SabotageService | Sabotage, cooldowns, effects |
| ObjectiveService | Recovery tasks and progress |
| FacilityStateService | Power, communications, security |
| RewardService | Server-calculated rewards |
| ProgressionService | Progression and unlock validation |
| InteractionService | Server-authorized world interactions |
| PersistenceAdapter | Encapsulates Roblox persistence APIs |

Keep these logical modules initially; do not introduce microservices without demonstrated need.

## 4. Authority boundary
Client: input, presentation, local affordance discovery, intent requests, safe cosmetic prediction.  
Server: authoritative state, validation, transitions, rewards, persistence.

Never trust client-supplied role, price, reward, ownership, eligibility, distance, or completion status.

## 5. Hybrid interaction architecture
Approved model: in-world terminals/contextual interactions plus overlays and radial quick access.

Proposed components:
- InteractionRegistry: server-owned target definitions.
- InteractionController: local input and affordance presentation.
- InteractionPrompt: reusable prompt.
- RadialMenuController: quick-access UI.
- TerminalView: reusable terminal shell and data-driven content.
- InteractionGateway: client intent transport.
- InteractionValidator: server authorization.
- FacilityInteractionService: dispatch to domain services.

Illustrative Luau types:

    type InteractionDefinition = {
        Id: string,
        DisplayName: string,
        Category: string,
        Prompt: string,
        MaxDistance: number,
        RequiredRole: string?,
        AvailableActions: {string},
    }

    type InteractionRequest = {
        TargetId: string,
        ActionId: string,
    }

The server resolves targets from trusted server-owned definitions. Validate target existence, distance, role, phase, action, cooldown, and rate. Delegate successful requests to domain services.

## 6. UI architecture
Shared visual tokens/components; contextual prompts; reusable terminal framework; radial menu as optional fast access; role-aware match HUD; overlays for essential information/accessibility; input abstraction for keyboard/mouse, controller, touch. Never make an essential function available only through a physical terminal.

## 7. State/event flow
Client requests an action at a registered target. Server resolves player/target, validates range/phase/role/task state, applies authoritative transition through domain service, and publishes resulting state. Client updates presentation from server-confirmed result.

## 8. Persistence
Persistence is a boundary, not gameplay authority. Save only server-approved progression and cosmetic ownership. Do not persist transient round state without an explicit design decision.

## 9. Security
Validate every RemoteEvent payload; rate-limit; validate proximity server-side; enforce role/phase; calculate rewards server-side; prevent duplicate completion/replay; do not trust client timestamps/counters; log important outcomes; test malformed, unauthorized, out-of-range, and stale requests.

## 10. Testing
Pure Luau tests for deterministic rules where supported; service-level state tests; server/client integration; multiplayer scenarios; negative RemoteEvent tests; manual Studio playtests for feel and device behavior. Select runner only after inspecting actual toolchain.

## 11. Toolchain validation gate
Before broad implementation prove Luau version control, source synchronization into Studio/chosen environment, a small worker change, launch/test, evidence capture, and repeatability. Do not assume OH directly controls Roblox Studio until demonstrated.