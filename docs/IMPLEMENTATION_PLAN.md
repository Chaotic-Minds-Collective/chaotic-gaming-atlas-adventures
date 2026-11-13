# CG Adventures — Implementation Plan

## Purpose
Quest, challenge and progression system integrated with identity, tribes, events and rewards.

## Feature scope
- Quest chains, objectives and prerequisites
- Daily/weekly challenges and seasonal events
- Progression tracks and skill unlocks where supported
- Player/tribe leaderboards
- Rewards through Core entitlements and leased delivery
- Admin quest editor and versioned events

## Dependencies
- Core identity, event outbox, entitlements and reward delivery
- ATLAS adapter: verified player/tribe/death/kill/crafting/exploration events
- Player for progression; Tribes for group objectives
- Commerce for rewards; Connect for announcements

## Data ownership
Adventures owns quest definitions, progress, completions, seasons, leaderboard snapshots and anti-abuse metadata. Core owns identity, entitlements and reward jobs.

## Milestones
1. Define quest schema and idempotent progress engine
2. Build offline simulation and validation
3. Use supported Core events first; extend ingestion later
4. Add player/tribe objectives
5. Deliver rewards through Core worker contract
6. Add seasons, leaderboards and scheduled events

## Technical gates and risks
- Core event API currently supports joined/left/chat, server start/stop and death only; other events need API expansion
- Reward delivery awaits confirmed ATLAS grant implementation
- Prevent replay and cross-grid duplicate progress

## Shared engineering requirements
- Use authenticated, least-privilege Core APIs; no direct database credentials in plugins.
- Preserve provider identifiers as strings; display names are not identifiers.
- Carry cluster, grid and server context on applicable records/events.
- Use stable event IDs, idempotency keys and correlation IDs.
- Keep network work off game-critical threads; use bounded timeouts, retries and circuit breakers.
- Keep secrets out of source control and separate credentials per server/integration.
- Add unit tests, fake-adapter contract tests and isolated runtime compatibility tests.
- Gate unsupported features behind explicit capabilities; fail closed for privileged actions.
- Do not deploy to production or change live server configuration during repository planning.

## Current readiness
Documentation and planning scaffold. Exact ATLAS server build, loader, SDK, callbacks and feature-specific capabilities require isolated reproducible validation.
