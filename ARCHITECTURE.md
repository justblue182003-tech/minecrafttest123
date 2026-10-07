# VoidCore 0.8 Architecture

## Service/tick ownership

`VoidCorePlugin` owns the service graph. The once-per-second simulation order is:

1. Phase Logistics graph evaluation, Flux/Entropy/Computation balancing, dimensional-link sustain, deterministic Control Matrix selection, automation signal evaluation, and item routing,
2. recompute loaded-machine spatial field stability using the freshly resolved factory policy and support chambers,
3. machine-local simulation (automation gate, fuel, heat, pressure, entropy stress, programmable observation, field faults, processes, wear, multiblock validation),
4. live UI/diagnostic refresh,
5. periodic main-thread `MachineSnapshot` capture followed by asynchronous SQLite persistence.

The network-first order is intentional in 0.8: current signal/channel state and the selected Control Matrix policy affect the same machine-production second. Network-delivered resources still naturally represent the latest resolved graph state, while sustained fault-onset windows protect against one-pass spikes.

## Authoritative machine state

`MachineInstance` remains authoritative. Persistent state now includes:

- location/type,
- Flux and process progress,
- heat/target heat,
- pressure/target pressure,
- engineering quality and wear,
- entropy,
- computation,
- fault identity + fault/escalation ticks,
- primary/secondary/catalyst/fuel/output/byproduct ports,
- upgrades,
- selected/completed process IDs,
- network frequency/secondary frequency,
- route priority/filter,
- observer program and requested control directive,
- automation group, signal channel/gate, Automation Terminal rule,
- Void Core singularity mode and upgrade-chamber specialization,
- per-item production ledger,
- lifetime cycles/items/Flux/processed-Entropy/incident counters.

`activeDirective` and `fieldStability` are runtime-derived values and are deliberately not persisted: they are recomputed from the current physical factory topology.

GUIs are views/editors. They are never an independent state store.

## Itemized machine relocation

Placed-machine SQLite state is removed when a block is legitimately broken. The resulting custom machine item preserves the state that must not be reset by relocation:

- engineering quality,
- wear,
- entropy,
- fault identity,
- fault/escalation timer,
- observer program / selected Control Matrix directive,
- automation group/channel/gate and terminal rule,
- singularity/chamber mode,
- per-item production ledger,
- lifetime production, Flux, Entropy, and incident counters.

Heat, pressure, Flux, computation, and process inventory are deliberately handled separately: stored inventory is dropped safely, and volatile operating conditions are recommissioned after placement. This prevents “break to erase entropy/faults” without turning machine items into portable live reactors.

## SQLite schema v5

v5 retains all v4 state and adds `automation_group`, `signal_channel`, `signal_gate`, `automation_rule`, `singularity_mode`, `core_chamber_mode`, and `production_ledger`. The repository contract is 46 explicit columns / 46 JDBC bindings. Migrations use `addColumnIfMissing`, so interrupted/manual partial upgrades do not fail on duplicate-column errors.

Snapshots are captured on the server thread. ItemStacks are serialized to bytes during capture; the asynchronous JDBC stage receives immutable primitive/byte-array data only. A captured revision may mark state clean only if no newer revision appeared while the save was in flight.

## Generic process model

`ProcessRecipe` supports:

- machine type,
- primary/secondary inputs,
- reusable catalyst,
- main output/byproduct,
- cycle duration + Flux cost,
- temperature window,
- pressure window,
- catalyst contamination/purification,
- wear per cycle,
- entropy generated,
- entropy consumed,
- computation consumed,
- environmental predicate,
- multiblock requirement,
- minimum spatial-field stability,
- research gate,
- completion experiment,
- process mode.

The Codex derives process documentation from the same registry used by runtime execution.

## Entropy model

Entropy is persistent local process disorder. Ordinary processors can accumulate it and suffer additional wear. Selected high-energy systems support the explicit entropy fault chain.

Phase Logistics transfers entropy primarily toward Entropy Condensers, but an active registered process with a nonzero Entropy cost may also request a bounded working buffer. The Void Core uses this path for Void Seed synthesis. Donors keep a reserve, transfer bandwidth scales with Flux Bus count, and transport incurs bounded hop loss. This makes local factory topology relevant to waste handling without filling every machine indiscriminately.

## Fault chain

High-energy entropy-aware machines support:

1. `COHERENCE_DRIFT` — soft degraded operation,
2. `ENTROPY_SURGE` — hard lock,
3. `CONTAINMENT_BREACH` — hard lock.

A configurable sustained threshold is required before Drift starts. Escalation then requires both elevated entropy load and sustained time. Repairs consume fault-specific custom components; quality is not rerolled.

## Observation/computation

`PHASE_OBSERVER` is a powered sensor, not an item processor. It evaluates environmental predicates and converts signal richness into computation. It also creates a small entropy load.

Computation has its own graph bandwidth. Current consumers include Entropy Condensers, Control Matrices, and the Void Core. Control Matrices continuously spend routed computation when broadcasting any non-Balanced policy.

## Environmental predicates

`ProcessEnvironment` is the canonical condition layer:

- `ANY`
- `OPEN_SKY`
- `NIGHT_SKY`
- `SCULK_FIELD`
- `NETHER`
- `END`

Recipes reference predicates rather than embedding world checks inside machine implementations.

## Entropy Condenser multiblock

`EntropyCondenserStructure` validates a 17-position frame around the controller every machine tick while the controller chunk is loaded. Process recipes may independently declare `requiresMultiblock`; the generic process engine blocks execution if the cached structure state is invalid.

The validator is deterministic and reports matched/required counts plus the first invalid position for UI diagnostics.

## Phase Logistics cache model

Network components are still discovered from loaded physical network blocks each graph pass. Each component receives:

- a stable network ID from canonical coordinate + frequency domains,
- a topology signature including every network block, type, primary frequency, and splitter secondary frequency,
- a cross-tick pairwise shortest-path cache.

If the signature is unchanged, the path map survives into the next graph pass. A changed signature creates a fresh cache. Stale component caches expire after a short absence window.

Endpoint changes do not require invalidating graph paths because cached paths are only between canonical network-block attachment points.

## Rolling telemetry

`NetworkHistory` stores bounded in-memory aggregate samples. It is diagnostic, not authoritative gameplay state. The summary classifies dominant pressure in this order: entropy saturation, computation starvation, Flux starvation, blocked outputs, excessive route loss, then healthy/no-dominant-bottleneck.

This separation keeps restart durability focused on gameplay state while still giving players enough historical signal to optimize a factory.

## Spatial field model

`SpatialFieldService` recalculates field stability once per server second from loaded physical machinery. The baseline is 50%. Powered Field Stabilizers contribute with a 12-block linear falloff; complete Void Cores reinforce the field; observers and entropy-heavy nearby equipment create interference. Values clamp to 0–100%. The simulation reads the previously resolved network control directive, preventing the field system from becoming a second independent policy store.

## Factory control policy

Control Matrices are network blocks and computation consumers. `NetworkService` deterministically chooses the highest-quality controller (stable network-address tie-break), pays the configured computation cost for non-balanced modes, then writes an ephemeral `activeDirective` onto attached endpoints. Machine process tuning consumes those multipliers; the persistent selected directive remains only on the controller.

## Void Core incident invariant

A spatial fault onset is evaluated only after a Void Core cycle has actually accumulated process progress. Merely loading valid feed into an idle/field-blocked controller cannot create Field Desync.

A spatial incident never destroys arbitrary world blocks. Sustained low field causes `FIELD_DESYNC`; continued collapse escalates to `FIELD_COLLAPSE`, increments the persistent incident counter, adds local/nearby wear and Entropy, and resets in-progress cycles. The machine item preserves the fault/timer and lifetime statistics, so breaking the core is not an incident-reset exploit.
## Automation signal invariant

Automation is scoped by physical network, **group**, and **channel**. An Automation Terminal evaluates one selected rule for one group/channel. Conditional rules always pay their configured computation cost before producing either HIGH or LOW. Multiple terminals may drive the same channel; HIGH is OR-composed deterministically. Each endpoint then applies its persisted `SignalGate` locally. `IGNORE` never blocks production; `REQUIRE_HIGH` and `REQUIRE_LOW` gate process admission without destroying partial progress or inputs.

Signal state itself is transient because it is derived every network pass. Group/channel/gate/rule configuration is persistent.

## Singularity + chamber invariant

Void Core singularity mode is persistent controller intent. Active upgrade chambers are physical support equipment within the configured local radius and must be powered. High-end Void Core recipes validate the required mode/chamber combination before process advancement. Compression and Extraction increase throughput but also raise Flux, Entropy, wear, and field-fault pressure; Quiescent mode intentionally suppresses active Void Core recipes.

## Dimensional-link invariant

A cross-world Phase edge exists only between loaded Dimensional Anchors with matching primary frequency and sufficient computation on both ends. Local physical adjacency remains the graph root: the anchor does not expose arbitrary world/global inventory lookup. Cross-dimensional Flux and Entropy incur configured extra loss; item movement consumes additional bandwidth. Link sustain is charged every network pass.

## Project Nullstar invariant

Project Nullstar is a server-scale **commissioning check**, not a consumptive recipe. Its terminal reads authoritative production ledgers, loaded anchor-world count, active cross-dimensional network metrics, and current complete/stable Void Core state. Completion is persisted per player through the existing experiment system, making the quality-100 Ascendant Core reward one-time without maintaining a second reward database.

