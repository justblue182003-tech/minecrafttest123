# VoidCore — Full Game Design Blueprint

## Implementation status — 0.8.0-alpha

The live alpha now implements the complete Chapter-I foundation, the Chapter-II thermochemical stack, a substantial Chapter-III logistics/pressure layer, an integrated Chapter-IV entropy/observation layer, and the Chapter-V spatial-control/Void-Core stack plus the first Chapter-VI automation/dimensional systems:

- research prerequisites + experiment gates,
- canonical fabrication/recipe browser and paginated material discovery,
- Prototype Bench and Spectrum Analyzer,
- Flux Crucible,
- scalar immutable engineering quality (0–100),
- quality-aware machine performance and upgrade sockets,
- generic primary/secondary-feed process recipes with byproducts,
- persistent heat, active cooling, target temperature, and thermal inertia,
- reusable catalyst contamination,
- Induction Heater, Catalytic Reactor, Matrix Purifier,
- Cryogenic Column and Thermal Exchanger,
- machine wear, service lockout, maintenance kits, and staged fault identities,
- SQLite machine persistence + versioned idempotent migrations,
- Flux Bus and Address Node graph discovery,
- frequency-isolated Flux routing with throughput/hop loss,
- Phase-Interface-gated automatic process-port item routing,
- Phase Router priority/filter policy, Priority Buffers, and Frequency Splitter bridges,
- deterministic shortest-path-aware routing and visual route tracing,
- pressure as a persistent second process envelope with powered compression/venting,
- Pressure Vessel and pressure-bound synthesis,
- persistent Entropy generation/consumption plus network Entropy capture,
- Phase Observer environmental computation and network Computation transport,
- generic environmental process predicates,
- Entropy Condenser as the first physical VoidCore multiblock structure,
- closed industrial waste-recovery loops,
- Coherence Drift → Entropy Surge → Containment Breach fault escalation,
- cross-tick topology/path reuse and rolling network bottleneck telemetry,
- revision-aware asynchronous SQLite snapshot persistence,
- machine relocation state that prevents break-to-reset Entropy/fault exploits,
- thermal/process/network/structure diagnostics UI,
- persistent programmable Phase Observer modes,
- spatial field stability with powered Field Stabilizers and machine interference,
- deterministic Control Matrix policies backed by routed Computation,
- persistent lifetime production/incident analytics,
- recoverable Field Desync → Field Collapse spatial incidents,
- bounded Entropy delivery to entropy-consuming endgame processes,
- 35-block Void Core containment lattice and Void Seed synthesis.

Tier IV is established as an integrated infrastructure layer; Tier V now includes spatial stability, factory control, and the first Void-Core-scale containment structure; and 0.8 begins the automation/dimensional endgame with persistent signal control and server-scale commissioning. The blueprint below remains the long-term target. Features beyond these implemented slices are design commitments, not claims that they already exist in 0.8.

## Vision

VoidCore should feel like discovering a forbidden engineering discipline inside survival Minecraft. The player is not handed a giant recipe list. They observe anomalies, formulate research, build prototypes, discover failure modes, then automate increasingly interconnected systems.

The design goal is depth through **interacting constraints**, not artificial grind. Long sessions should happen because the player has another experiment, bottleneck, optimization, or unlock they genuinely want to solve—not because a timer forces them to remain online.

## Core progression loop

**Discover → Research → Prototype → Stabilize → Automate → Optimize → Integrate → Transcend**

Each tier introduces one new engineering variable. Old variables never become irrelevant.

- Tier I introduces **Flux**.
- Tier II introduces **Heat** and catalyst health.
- Tier III introduces **Frequency**, network bandwidth, deterministic routing policy, and **Pressure**.
- Tier IV introduces **Entropy** and reversible waste chains.
- Tier V introduces **Stability** across multi-block structures.

## Chapter I — Resonance Engineering

Theme: detecting and stabilizing information-rich matter.

### Materials

- Resonant Fragment
- Charged Resonance
- Copper Lattice
- Flux Coil
- Harmonic Lens
- Stabilized Matrix
- Phase Glass
- Resonant Alloy

### Machines

1. **Flux Crucible** — converts raw resonance into a stable component.
2. **Harmonic Press** — applies pressure/frequency recipes; bad tuning lowers yield.
3. **Lattice Winder** — produces coils with quality values.
4. **Spectrum Analyzer** — identifies unknown samples and reveals research clues.
5. **Prototype Bench** — crafts machines whose recipes are too complex for a vanilla grid.

### Player lesson

Energy is not a binary “has power / no power” system. Power quality and throughput matter.

## Chapter II — Thermochemical Systems

Theme: reactions with temperature windows and catalysts.

### New variables

- Heat, measured as machine temperature.
- Thermal inertia.
- Catalyst activity and contamination.
- Cooling capacity.

### Materials

- Catalytic Core
- Pyrogel
- Cryo Salt
- Tempered Resonant Alloy
- Ceramic Insulator
- Reactive Slurry
- Purified Matrix
- Superheated Phase Glass

### Machines

6. **Catalytic Reactor** — multi-input reactions with catalyst sockets.
7. **Induction Heater** — adds controllable heat to nearby/process-connected machines.
8. **Cryogenic Column** — separates compounds at low temperature.
9. **Thermal Exchanger** — recycles heat between two process lines.
10. **Matrix Purifier** — removes contamination at a material cost.
11. **Pressure Vessel** — batch processing with pressure/temperature curves.

### Failure design

Failure should usually create an engineering problem, not destroy a base. Examples:

- contaminated batch,
- reduced yield,
- overheated machine shutdown,
- damaged catalyst,
- entropy waste,
- temporary lockout requiring maintenance.

Catastrophic explosions should be opt-in end-game behavior only.

## Chapter III — Phase Logistics

Theme: routing power/items/data through frequency-addressed networks.

### New variables

- Frequency channels.
- Bandwidth.
- Packet priority.
- Buffer pressure.
- Signal interference.

### Materials

- Phase Thread
- Address Crystal
- Quantum Relay
- Coherent Matrix
- Encoded Core
- Void-Fiber Cable

### Machines and network blocks

12. **Phase Router** — configurable item routing by tag/item/category.
13. **Flux Bus** — transports flux with throughput and loss constraints.
14. **Address Node** — names a machine endpoint.
15. **Priority Buffer** — stores and prioritizes packets.
16. **Frequency Splitter** — bridges or isolates network channels.
17. **Network Analyzer** — visualizes congestion, loss, and idle capacity.
18. **Remote Terminal** — reads machine status from another location.

### UX goal

Players should be able to diagnose a network visually. A professional interface should answer:

- What is blocked?
- Why is it blocked?
- What is consuming bandwidth?
- Which machine is starved?
- Where is flux being lost?

No hidden “it just stopped working” states.

## Chapter IV — Entropy Computation

Theme: turning waste, decay, and information into resources.

### New variables

- Entropy load.
- Computation cycles.
- Reversibility efficiency.
- Environmental conditions.

### Materials

- Entropy Crystal
- Memory Slag
- Null Dust
- Temporal Residue
- Compressed Noise
- Recursive Matrix
- Observer Core

### Machines

19. **Entropy Condenser** — transforms waste streams into usable matter.
20. **Decay Chamber** — time-based recipes that continue while chunks are loaded; no forced online timers.
21. **Pattern Computer** — executes recipe programs using computation cycles.
22. **Observer Array** — samples biome/weather/moon/dimension conditions.
23. **Matter Reconstructor** — expensive reversible recipes with losses.
24. **Noise Filter** — cleans network/data noise generated by high-end systems.

### Research experiments

Research stops being purely a currency tree. Nodes may require observations such as:

- record a thunderstorm at high altitude,
- stabilize a reactor within a narrow heat window,
- process a batch with >95% efficiency,
- route three materials through one frequency without congestion,
- collect a sample from each dimension,
- deliberately create and then recycle an entropy byproduct.

The Codex tracks these as explicit experiments with progress bars and exact conditions.

## Chapter V — Void-Core Engineering

Theme: coordinated multi-block infrastructure with real system-level constraints.

### New variable

**Stability** is computed from the entire structure and its operating environment.

### Materials

- Contained Singularity
- Event-Horizon Mesh
- Zero-Point Lattice
- Void Core
- Causal Anchor
- Perfect Resonance

### End-game structures

25. **Singularity Containment Ring** — multi-block structure with shielding and cooling requirements.
26. **Zero-Point Tap** — extreme flux source with stability costs.
27. **Causal Anchor** — prevents instability propagation inside a defined system.
28. **Matter Compiler** — programmable high-cost manufacturing.
29. **Void Foundry** — end-game alloy processing.
30. **The Void Core** — server-scale project integrating flux, heat, network bandwidth, entropy disposal, and stability.

The final structure is not “place block and win.” It is a system engineering challenge.

## Research Matrix

The research UI should have five layers:

1. **Theory** — conceptual unlocks.
2. **Materials** — discovered matter families.
3. **Machines** — fabrication/processing technology.
4. **Infrastructure** — logistics, power, diagnostics.
5. **Experiments** — behavioral achievements proving mastery.

Research nodes have:

- prerequisite nodes,
- Insight cost,
- discovery requirements,
- optional experiment requirements,
- unlock rewards,
- readable technical notes,
- recipe/machine links.

The player should always know *why* a node is locked.

## Insight economy

Insight is not intended to become another XP bar.

Sources should be weighted toward novelty and skill:

- first discovery bonuses,
- successful experiments,
- high-efficiency batches,
- discovering new environmental conditions,
- scanning rare structures/materials,
- solving research objectives.

Repeated ore mining can provide a small baseline but should have diminishing importance after Tier I.

## Machine quality system

### Implemented foundation (0.5)

Quality-bearing components, upgrades, process outputs, and Tier-II machines can carry one immutable **engineering quality** score from 0–100. The value is generated by the fabrication/process chain and feeds directly into cycle speed, flux efficiency, thermal response, contamination control, and output-quality calculations. Small Prototype Bench tolerance variance exists, but the system is not a colored RPG rarity ladder: better process inputs and better process control are the main route to better hardware.

Machine items preserve quality through placement/breaking. Catalyst purification changes contamination but never rerolls quality.

### Planned multidimensional model

Later releases can split the scalar foundation into process-specific properties when the extra dimensions create actual decisions:

- Purity
- Conductivity
- Thermal tolerance
- Coherence
- Stability

Example end-state: a Flux Coil made from high-conductivity copper and a high-coherence matrix may lose 2% energy, while a rushed coil loses 11%. The 0.5 scalar score deliberately proves the persistence/performance architecture before introducing five correlated statistics.

## Recipes as processes

Avoid thousands of arbitrary crafting-table recipes. Advanced recipes define a **process**:

- inputs,
- catalyst,
- temperature range,
- flux/tick,
- duration,
- minimum machine tier,
- environmental predicates,
- outputs,
- byproducts,
- quality formula.

This makes the recipe browser useful rather than decorative.

## UI/UX specification

### Visual language

- Dark neutral background.
- Purple = research/void systems.
- Aqua = information/resonance.
- Red = power/heat warnings.
- Gold = active processing/high-value output.
- Green = completed/healthy.
- Gray = unavailable/inactive.

Colors must always be reinforced with text/icons so color is not the only status channel.

### Interaction rules

- Left click: primary action.
- Right click: details/context where useful.
- Shift click: batch/alternate action.
- Escape/back arrow: predictable navigation.
- No essential information hidden exclusively in chat.
- Destructive actions require a confirmation state.
- Errors explain both the problem and the corrective action.

### Machine screen anatomy

Every machine UI reserves consistent regions for:

- input,
- catalyst/upgrade,
- process visualization,
- output,
- energy/heat/stability status,
- diagnostics,
- recipe selection,
- network state.

Players should learn one machine UI and understand the rest quickly.

## Multiplayer design

VoidCore supports specialization without hard class locks.

Natural roles emerge:

- prospector/scientist,
- process engineer,
- network engineer,
- reactor operator,
- architect/infrastructure builder.

Teams can share infrastructure while research remains configurable as per-player or shared-team progression in a later module.

## Server-performance design

The plugin should scale without scanning every block every tick.

Rules:

- persistent registry of machine locations,
- tick machines in buckets rather than every machine every tick,
- skip unloaded chunks,
- event-driven network invalidation,
- cached network graphs,
- bounded work per tick,
- asynchronous file/database I/O only after immutable snapshots are created,
- no NMS unless a feature has no stable Paper API equivalent,
- metrics for machine count, tick cost, queue depth, and network rebuild time.

Large servers should be able to reduce simulation frequency without breaking recipes because processing uses elapsed simulation units rather than fragile per-tick assumptions.

## Persistence

Recommended production model:

- PDC for lightweight player/item identity.
- SQLite by default for research, discoveries, machine state, teams, and networks.
- Optional MySQL/PostgreSQL adapter for networks of servers.
- Schema migrations with explicit versioning.
- Machine state writes buffered and flushed safely.
- World/block identity cross-checked to prevent ghost machines after edits.

0.4 moved authoritative machine state to SQLite. 0.5 adds immutable main-thread snapshot capture, asynchronous transactional batch writes, revision-aware dirty-state clearing, and schema v2 migration. Before a large public release, add delta/incremental writes, backpressure/queue telemetry, and schema-level integration tests.

## Resource pack

A resource pack is optional for the core mechanics but recommended for the polished release.

Use it for:

- unique item icons,
- machine block models,
- GUI glyphs,
- status icons,
- animated machine states,
- consistent typography assets where appropriate.

Server logic must remain functional if a player declines the pack; vanilla fallback materials should still communicate state.

## Anti-frustration principles

- No mandatory real-money-style daily loops.
- No arbitrary multi-hour online timers.
- No irreversible base destruction from ordinary mistakes.
- No hidden recipes as the only source of difficulty.
- No “bigger number = better machine” progression by itself.

Difficulty comes from understanding and combining systems.

## Release roadmap

### 0.1 — Foundation

Implemented in the current project:

- custom item identity,
- Resonant Fragment world discovery,
- Insight,
- persistent research matrix,
- Flux Crucible,
- machine persistence,
- recipe gating,
- Codex/research/machine GUIs,
- admin/debug commands.

### 0.2 — Real Tier I

Implemented in the current project:

- Prototype Bench,
- Spectrum Analyzer,
- 20+ Tier I recipes,
- 20+ Tier I materials/components,
- material acquisition + spectral-scan states,
- recipe browser,
- research experiments,
- expanded research graph,
- machine index and generalized machine placement.

Deferred from 0.2: localization. The current priority is completing the simulation architecture before externalizing every message.

### 0.3 — Thermochemical — implemented foundation

Implemented in the current alpha:

- generic process recipe engine,
- persistent heat simulation and thermal inertia,
- reusable catalyst slots with contamination/purification,
- scalar quality plus upgrade-driven performance,
- Induction Heater, Catalytic Reactor, and Matrix Purifier,
- shared engineering and diagnostics UI.

0.3 established the thermal/process engine that 0.4 extends rather than replacing.

### 0.4 — Factory Infrastructure — implemented alpha slice

- Multi-input process ports and byproduct streams.
- Powered active cooling and cryogenic processing.
- Thermal Exchanger heat recovery.
- Machine wear, service lockout, and quality-aware maintenance.
- SQLite machine-state persistence and YAML migration.
- Flux Bus / Address Node physical graphs with frequency isolation.
- Throughput/hop-loss Flux balancing.
- Phase Interface item routing between compatible process ports.
- Network diagnostics and load-balancing research experiment.

### 0.5 — Phase Logistics depth + pressure engineering — implemented alpha slice

Implemented:

- Phase Router with exact custom-item filters and endpoint priorities,
- Priority Buffer staging endpoints,
- Frequency Splitter bridges between two isolated domains,
- deterministic shortest-path-aware route scoring,
- per-evaluation path caching + route trace diagnostics,
- Pressure Vessel with pressure curves and process pressure windows,
- pressure-sensitive quality/wear, hard machine faults, and repair parts,
- async-safe immutable SQLite snapshot batches + schema v2.

Still deferred from the broader 0.5/scale vision:

- cross-tick topology cache with incremental invalidation,
- long-term network history/bottleneck graphs,
- automated waste recycling chains,
- database/Paper integration-test harness.

### 0.6 — Entropy — implemented alpha slice

- waste/recycling loop,
- environment predicates,
- routed computation and Phase Observer mechanics,
- Entropy Condenser multiblock, staged entropy faults, and cross-tick network telemetry.

### 0.7 — Spatial containment — implemented alpha slice

- spatial-field stability and visual diagnostics,
- Field Stabilizer and Control Matrix policy,
- persistent production/incident analytics,
- recoverable spatial incident chain,
- 35-block Void Core and initial Void Seed synthesis.

### 1.0 — Production hardening target

- production-grade migration backups and recovery tooling,
- optional resource-pack models/animations,
- permissions, localization, and deeper admin tooling,
- profiling/public-server hardening,
- broader integration tests and compatibility validation.
### 0.8 — Automation + dimensional infrastructure — implemented alpha slice

Implemented:

- G0–G7 machine groups, CH0–CH15 signal channels, and persistent endpoint gates,
- condition-driven Automation Terminals with real computation cost,
- universal Signal Crystal configuration UI,
- per-item production history,
- Void Core singularity states and powered support chambers,
- multi-stage singularity refinement into Compressed Void Seeds and Dimensional Kernels,
- loaded/computation-sustained cross-dimensional Phase links,
- Project Nullstar as a non-consumptive server-scale infrastructure objective,
- SQLite schema v5 and relocation persistence for all new configuration.

Still deliberately deferred:

- multi-valued/analog logic and user-authored rule expressions,
- chunk-ticket ownership for dimensional anchors (0.8 only links loaded anchors),
- graphical time-series charts beyond the current rolling diagnostic summaries,
- resource-pack models/animations and localization,
- production-grade public-server profiling and integration-test harness.

