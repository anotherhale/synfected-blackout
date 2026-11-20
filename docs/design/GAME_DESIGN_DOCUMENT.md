# SYNFECTED: BLACKOUT — Game Design Document

**Version:** 0.1 | **Status:** Initial project design baseline | **Platform:** Roblox  
**Parent product:** SYNFECTED: RESISTANCE | **Target:** 30-day playable vertical slice  
**Working title:** BLACKOUT; name clearance required before public release.

## Document status
FOUNDATIONAL = inherited franchise direction. APPROVED FOR BLACKOUT = adopted project decision. PROPOSED = requires playtesting/technical validation. EXPLORATORY = uncommitted. IMPLEMENTED = verified in the running game and repository.

This product-specific document does not overwrite SYNFECTED GDD v0.2.

# 1. High concept
A Resistance facility has been infiltrated by alien intelligence. Communications are compromised, critical systems are failing, and one player is secretly Infected. The remaining players must identify the threat, restore systems, and survive before the facility is fully compromised.

**Tagline:** TRUST NO SIGNAL.

BLACKOUT is a fast-round multiplayer social-deduction game with asymmetric roles, environmental sabotage, cooperative recovery objectives, and a cyberpunk facility setting.

## Goals
- Immediately understandable multiplayer loop.
- Tension from incomplete information and player behavior.
- Facility systems are meaningful gameplay.
- Replayability through role variation, maps, and progression.
- Showcase autonomous development with testable evidence.

## Non-goals
No open-world exploration, persistent NPC populations, player-run businesses, complex crafting, advanced syndicate management, AI executives, SIN, blockchain, or player trading in the MVP.

# 2. Player experience
Players gather in a Resistance staging facility, enter a match, receive secret roles, and pursue competing objectives. They interpret clues, observe behavior, and decide whom to trust. The experience should be social, replayable, non-graphic, fair, and accessible across supported Roblox input devices.

# 3. Round structure
Initial timing is PROPOSED and must be balanced through playtests.

| Phase | Initial duration | Purpose |
|---|---:|---|
| Lobby / queue | 20 sec | Gather eligible players |
| Role assignment | 5 sec | Assign secret roles |
| Preparation | 15 sec | Orient and move |
| Active round | Up to 180 sec | Competing objectives |
| Results | 15 sec | Outcome and rewards |

Round manager owns lifecycle; transitions are deterministic and server-authoritative.

**Resistance wins** when Infected is stopped or recovery reaches its completion threshold. **Infected wins** when Resistance is eliminated or facility compromise reaches its threshold before recovery. Player-count scaling and thresholds remain open.

# 4. Roles

## Infected
Objective: compromise the facility and prevent recovery. Proposed capabilities: eliminate opponents through a constrained server-validated action; sabotage selected systems; use temporary disruption to evade identification. Sabotage has cooldowns and counterplay. Identity remains secret.

## Sentinel
Objective: identify and stop Infected. Proposed capabilities: one limited-use energy pulse weapon and selected security tools. Weapon use validates role, range, cooldown, target, and round state. Sentinel information must not automatically reveal Infected.

## Operative
Objective: restore systems, gather evidence, and survive. Complete recovery tasks, observe/report suspicious behavior, and assist teammates. Operatives need meaningful contributions without direct confrontation.

# 5. Signature mechanic: Facility Blackout
Infected disrupts facility systems; Resistance restores them through physical terminals or contextual interactions.

Candidate sabotage: power disruption (reduced visibility), communications disruption, security disruption (camera/display outage). Candidate recovery: power restoration sequence, communications configuration puzzle, security reboot task. Start with two sabotage actions and two recovery task types. Expand only after the loop is fun and reliable.

All sabotage, cooldowns, task progress, and win-condition changes are authoritative server state.

# 6. Maps and environment
MVP: one compact facility map; second map is stretch. Provide readable landmarks, multiple routes/sightlines, distinct power/communications/security/operations zones, uncertainty without confusing navigation, and stations that encourage movement. Candidate zones: operations center, communications room, power control, security station, research wing, storage/maintenance corridors.

# 7. Hybrid immersive interface
**APPROVED FOR BLACKOUT — BLK-DD-004**

Principle: **The world is the interface.** Prefer physical, contextual interactions embedded in the facility when they improve immersion. Use overlays and radial access for speed, clarity, and accessibility.

### Visual direction
Cyberpunk Resistance technology:
- Near-black #080B0D.
- Neon teal #42E8C5 primary.
- Terminal green #39FF70 success.
- Crimson #FF334F alerts.
- Muted #91A8A8 secondary text.
- Restrained holographic/glitch effects, terminal typography, clear iconography.

Effects must not impair readability or performance.

### In-world stations
| Station | Function |
|---|---|
| Operations board | Match selection and briefing |
| Armory/equipment locker | Equipment selection |
| Communications console | Party and squad management |
| Intelligence terminal | Evidence and service records |
| Training station | Guided onboarding |
| Records display | Achievements/progression |
| Deployment console | Enter a match |

Stations share a reusable interaction framework, not unique bespoke systems.

### Contextual prompts
Show target, available action, and input binding. Support keyboard/mouse, controller, and touch.

### Radial quick-access menu
Proposed segments: Scanner, Equipment, Communications, Objectives, Records, Emotes, Settings. Actions are context- and role-aware. The wheel is presentation/input, not an authority boundary; it must not expose hidden role data or bypass server validation.

### Overlays
Use for role reveal, match timer/state, objectives, confirmation dialogs, essential status, settings/accessibility, and tutorials. No essential function is available only through a diegetic interaction.

# 8. Progression and rewards
PROPOSED and secondary to the core loop: XP/level, earnable credits, commendations/achievements, cosmetic unlocks, daily assignments. Rewards are calculated/granted by the server. Purchases must not create mandatory competitive advantages. Monetization needs separate platform-policy and product review.

# 9. Onboarding
Teach through short contextual activities: use a facility terminal; understand role objectives; complete a recovery interaction; observe sabotage; understand match resolution. Track tutorial completion to avoid repeating forced guidance.

# 10. Audio and feedback
Audio communicates system failure/recovery, appropriate role events, interaction success/failure, phase transitions, and results. Essential information must also have visual feedback.

# 11. Safety and platform constraints
Use stylized non-graphic elimination. Keep communication and user-generated content within Roblox policies and age-appropriate constraints. No unmoderated open-ended AI dialogue. Avoid unnecessary personal data. Design for fair play and exploit resistance. Review monetization and platform-dependent features before release.

# 12. Technical gameplay principles
Server owns roles, round state, elimination, sabotage, objectives, rewards, and persistence. Clients send intent; server validates type, state, role, distance, cooldown, rate, and ownership as applicable. UI/local effects are presentation only. No runtime LLM dependency.

# 13. MVP scope
Required: reproducible Roblox workflow; lobby/round lifecycle; three roles; one facility map; server-authoritative elimination/win conditions; two sabotage and two recovery types; role reveal/HUD/objective feedback/results; reusable contextual interaction; operations board and armory; input accessibility; multiplayer and exploit-boundary tests.

Stretch: second map, full radial menu, persistent XP/credits, achievement/service record, daily assignments, dynamic facility displays.

Out of scope: trading, guild economy, open world/procedural maps, persistent NPCs, AI players, runtime LLM, complex inventory, multiple modes, blockchain/crypto.

# 14. Proposed 30-day sequence
| Days | Focus | Exit evidence |
|---|---|---|
| 1–3 | Toolchain proof, architecture, bootstrap | Reproducible build and validated Luau change |
| 4–8 | Lobby and round state machine | Full placeholder round resolves |
| 9–14 | Roles, combat, sabotage, recovery | Complete playable core loop |
| 15–20 | Map, UI, hybrid interactions, onboarding | New player understands a round |
| 21–25 | Multiplayer, exploit, persistence, regression | Critical scenarios pass |
| 26–30 | Balance, polish, showcase | Reproducible playable vertical slice |

# 15. Open questions
Minimum player count; role scaling; sabotage cooldowns/recovery durations; Sentinel information; compromise threshold; initial supported inputs; second-map feasibility; progression scope; verified Roblox Studio synchronization and test workflow.

# 16. IP and originality
BLACKOUT is an original SYNFECTED experience. Use genre inspiration, not another game's name, branding, characters, maps, assets, text, UI artwork, or distinctive presentation. Working title requires clearance before public release.