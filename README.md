# CG Adventures

Quest, challenge and progression system integrated with identity, tribes, events and rewards.

This Chaotic Gaming-specific module extends [Chaotic Gaming Core](https://github.com/Chaotic-Minds-Collective/chaotic-gaming-core) and the [ATLAS integration adapter](https://github.com/Chaotic-Minds-Collective/chaotic-gaming-atlas); it does not replace either foundation.

## Feature scope
- Quest chains, objectives and prerequisites
- Daily/weekly challenges and seasonal events
- Progression tracks and skill unlocks where supported
- Player/tribe leaderboards
- Rewards through Core entitlements and leased delivery
- Admin quest editor and versioned events

## Architecture and dependencies
- Core identity, event outbox, entitlements and reward delivery
- ATLAS adapter: verified player/tribe/death/kill/crafting/exploration events
- Player for progression; Tribes for group objectives
- Commerce for rewards; Connect for announcements

Core remains authoritative for shared identity, authorization and platform records. ATLAS-native calls pass through the shared adapter. This module owns its domain state and must not connect directly to PostgreSQL.

## Implementation plan
See [docs/IMPLEMENTATION_PLAN.md](docs/IMPLEMENTATION_PLAN.md) for data ownership, milestones and technical gates.

## Readiness
Planning scaffold only. Native ATLAS compatibility and feature-specific callbacks are not yet verified on an isolated server. No production deployment is implied.
