# BLACKOUT Development Workflow

## 1. Prove the toolchain first
Inspect Studio/version, Luau source sync (Rojo or verified alternative), test framework, local launch/playtest, CI/assets, manual steps, and OH capabilities. Demonstrate a small source change can sync, run, and be validated. Do not assume tools or integrations exist.

## 2. Issue lifecycle
Backlog Architect creates/updates a small issue; CIPHER checks priority/dependencies/duplicates; Implementation Worker uses isolated branch/workspace; worker implements and tests; independent QA validates acceptance; independent reviewer checks correctness/security/architecture/scope; CIPHER coordinates authorized integration; docs update when behavior/decisions change.

## 3. Branch conventions
- feat/blk-<issue>-short-description
- fix/blk-<issue>-short-description
- docs/blk-<issue>-short-description

PR includes issue reference, summary/scope, design/ADR refs, test commands/results, screenshots/video for visual changes where practical, security/authority notes, and known limitations.

## 4. Definition of Ready
Clear objective; testable acceptance; scope/exclusions; dependencies; source references; known validation method; small enough for one execution.

## 5. Definition of Done
Acceptance met; tests pass or limitations documented; no unrelated changes; independent review; no unresolved critical security defect; evidence attached; docs updated where appropriate.

## 6. Human approval boundaries
Do not assume permission to merge protected branches, publish a Roblox experience, spend money/purchase assets, change monetization, introduce third-party services, add runtime AI, or collect additional player data.