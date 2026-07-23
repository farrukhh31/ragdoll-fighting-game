# Ragdoll Fighting Game

Physics-based local 2-player fighting game built in Unreal Engine 5, blending animation-driven combo combat with real-time ragdoll physics.

## Overview

Ragdoll Fighting Game replaces the stiff, choreographed feel of traditional fighters with unpredictable, physics-driven interactions. Every strike is computed in real-time — the direction, force, and momentum of each hit directly determines how the struck character's body reacts. Players fight on a floating island arena and win by knocking their opponent unconscious or knocking them off the edge of the map.

**Design Philosophy:** Every technical decision was made in service of one goal — making each match feel different from the last. Physics unpredictability isn't a bug, it's the core feature.

## Features

- **Local 2-Player Multiplayer** — single shared Character Blueprint driving two independently controlled instances
- **Ragdoll Physics System** — built on Unreal's Physical Animation Component, blending animation and physics per-bone
- **Combo Attack System** — 3-hit chain (Jab → Cross → Haymaker) with animation-notify-driven combo windows
- **Knockout Force Accumulation** — force builds up per hit, decays over time, and triggers a passive ragdoll KO state at threshold
- **Ring-Out & Knockout Win Conditions** — knock your opponent out or off the floating island
- **Minimal UI** — clean HUD with an end-game screen and instant restart flow

## Tech Stack

| Component | Technology |
|---|---|
| Engine | Unreal Engine 5 |
| 3D Modelling & Rigging | Blender 3.x |
| UI | Unreal Motion Graphics (UMG) |
| Platform | PC (Windows) |

## Project Scope

| Metric | Detail |
|---|---|
| Player Count | 2 (Local Multiplayer) |
| Win Condition | Knockout accumulation OR ring-out |
| Core Mechanic | Physics-based ragdoll combat with combo system |
| Character Count | 1 (shared blueprint, two instances) |
| Arena Count | 1 (Floating Island) |
| Attack Animations | 3 custom animations per player |

## Core Systems

- **Local Multiplayer Architecture** — single Character Blueprint with dual Player Controllers, each maintaining independent Knockout Force, Health, and Ragdoll state
- **Physical Asset Construction** — capsule/box/sphere colliders per bone, tuned joint constraints (hinge, ball & socket), and orientation strength/damping values arrived at via playtesting
- **Character Pipeline** — modeled and rigged in Blender following UE5 humanoid bone-naming conventions, exported via FBX with baked transforms
- **Knockout Sequence** — force accumulates per hit, crosses a threshold to trigger passive ragdoll, decays at 0.92/sec if unhit, with a recovery blend back to player control
- **Arena Design** — floating island with height fog for atmosphere/performance, and a box-collision-based out-of-bounds trigger for ring-outs

## Roadmap

Planned future improvements include additional characters and arenas, blocking/parry mechanics, special moves, online multiplayer, a replay system, and an AI opponent. See the full technical report for priority and complexity estimates.

## Documentation

Full technical documentation — including physics tuning tables, bone naming conventions, combo timing data, technical challenges & solutions, and playtesting findings — is available in the [Technical Report](./docs/GDD-Project_Technical-Report.pdf).

## Course Context

Developed as a project for the Game Design & Development course, CTGA department,NED University, May 2026.
