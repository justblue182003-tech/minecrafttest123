# VoidCore

VoidCore is an original long-form survival technology plugin for **Paper 26.3**. Its identity is research-driven industrial occultism: players discover anomalous matter, prove concepts through experiments, build process infrastructure, then optimize interacting systems rather than simply unlock a larger crafting table.

Version **0.8.0-alpha** is the automation, dimensional-infrastructure, singularity-refinement, and server-scale commissioning milestone.

## Target

- Minecraft Java Edition: **26.3**
- Server: **Paper 26.3**
- Java toolchain: **25**
- Build: Gradle Kotlin DSL / Gradle 9.x
- Persistence: SQLite, with `sqlite-jdbc` shaded into the deployable JAR
- Plugin descriptor: `plugin.yml`, API version `26.3`

## 0.8 gameplay systems

### Factory automation is physical and inspectable

Every placed VoidCore machine can now carry three automation coordinates: an **automation group** (`G0`–`G7`), a **signal channel** (`CH0`–`CH15`), and a gate mode (`Ignore`, `Require High`, or `Require Low`). Sneak-right-clicking a known VoidCore machine while holding a **Signal Crystal** opens the universal signal configuration panel. The configuration is persistent and survives legitimate machine relocation.

An **Automation Terminal** evaluates one selected factory condition and drives its selected channel for its selected group. Implemented rules include Always High, Entropy High, Flux Low, Output Blocked, Field Unstable, Wear High, Fault Active, and Computation Low. Conditional rules consume computation whether they resolve HIGH or LOW, so closed-loop control has a real infrastructure cost rather than becoming free logic.

The machine simulation now evaluates Phase-network control/signals **before** the spatial and machine ticks, so signal gates and Control Matrix policy affect that same production second.

### Remote operations + production history

Network diagnostics now expose signal state, groups, channels, gated endpoints, automation terminals, dimensional links, and the existing rolling Flux/Entropy/Computation telemetry. Individual machines also persist a **per-item production ledger**, allowing diagnostics and endgame objectives to prove what a factory has actually produced instead of relying only on lifetime cycle counts.

The Research, Experiment, Machine, and Material interfaces were expanded/paginated so late-game content is never hidden by a fixed 54-slot layout.

### Void Core operating states + upgrade chambers

The Void Core now has four explicit singularity operating states:

- **Contained** — safe baseline,
- **Compressed** — faster and more aggressive, with higher Flux/Entropy/wear,
- **Extraction** — maximum output pressure and the highest stability burden,
- **Quiescent** — reduced activity for safer recovery/maintenance.

Nearby **Void Core Upgrade Chambers** can be specialized for Stabilization, Compression, or Extraction. Chamber state is powered, persistent, and spatial: high-end singularity recipes require the correct active chamber mix rather than a menu-only checkbox. Stabilization chambers also reduce core wear and incident pressure.

Two new Void Core processes extend the endgame chain: **Compressed Void Seed** and **Dimensional Kernel**. Their recipes require increasingly aggressive singularity modes, active chambers, high field stability, routed computation, routed Entropy, and the existing complete Void Core multiblock.

### Cross-dimensional Phase infrastructure

A **Dimensional Anchor** can form a virtual Phase edge with a loaded matching-frequency anchor in another world. Both anchors must be healthy and continuously sustain the configured computation budget. Cross-dimensional movement is therefore not free wireless transport: it remains part of the physical local Phase graph, consumes computation, and adds extra Flux/Entropy transport loss. Item transfer over a dimensional edge also consumes additional network bandwidth.

The dimensional topology is visible in Network Diagnostics and is used by the `Dimensional Phase Link` experiment and the Project Nullstar objective.

### Project Nullstar

The **Project Nullstar Terminal** is the first server-scale commissioning objective. It verifies infrastructure instead of consuming a giant pile of materials. By default it requires:

- at least 500 lifetime server production cycles,
- at least 3 produced Compressed Void Seeds,
- at least 1 produced Dimensional Kernel,
- loaded Dimensional Anchors across at least 2 worlds,
- a complete, non-faulted Void Core at 85%+ field stability,
- and a cross-dimensional Phase graph connected to the terminal.

Commissioning advances the Project Nullstar experiment and awards one quality-100 **Ascendant Core** per player. The reward is immediately registered in that player's material discovery state.

### SQLite schema v5

Schema v5 persists automation group/channel/gate, Automation Terminal rule, Void Core singularity mode, upgrade-chamber mode, and the per-item production ledger. The machine repository now writes **46 explicit columns with 46 JDBC bindings**. v5 migration remains column-idempotent, so a partially applied migration can safely be retried.

## 0.7 gameplay systems

### Spatial coherence is a process variable

Every loaded machine now receives a recomputed **field stability** value. Nearby powered Field Stabilizers increase coherence with distance falloff; observation hardware and entropy-heavy equipment create interference. A Control Matrix running **Stability** policy can reinforce the field, while **Throughput** policy slightly destabilizes it. Spatial recipes are hard-gated by a minimum field percentage rather than merely receiving a cosmetic quality bonus.

The new **Stabilized Condensate** process requires a complete Entropy Condenser Array and at least 80% field stability. The base Void Seed process requires at least 82%.

### Programmable Phase Observers

Phase Observers can now be switched in their GUI between five programs:

- Broad Spectrum,
- Celestial Tracking,
- Sculk Correlation,
- Dimensional Baseline,
- Entropy Watch.

Programs change what environmental signals contribute to computation generation instead of treating every observer as identical. Program identity persists through SQLite and legitimate machine relocation.

### Factory-wide Control Matrix

A **Control Matrix** joins a physical Phase Logistics graph and deterministically broadcasts one policy:

- Balanced — neutral baseline,
- Throughput — faster cycles for higher Flux, wear, and Entropy,
- Efficiency — lower Flux/Entropy with a small speed penalty,
- Stability — lower throughput in exchange for reduced wear/Entropy and stronger local field stability.

Non-balanced policies continuously consume routed computation. If the selected controller cannot pay that computation cost, the network safely falls back to Balanced. When multiple matrices share a graph, controller selection is deterministic by quality and network address.

### Persistent production ledger

Machines now persist lifetime completed cycles, produced items, consumed Flux, processed Entropy, and recoverable incident count. Machine Diagnostics shows the local lifetime ledger; Network Diagnostics aggregates those counters across the currently resolved factory graph. The counters survive restart and legitimate break/replacement.

### Recoverable spatial incidents

Operating a complete Void Core with insufficient coherence can progress through:

`Field Desync → Field Collapse`

Field Desync is a degraded warning stage. A sustained collapse triggers a recoverable industrial incident: the core gains Entropy/wear, nearby machinery receives scaled stress, and active progress is reset without griefing world blocks. Recovery consumes a Spatial Anchor rather than forcing the player to rebuild the controller.

### 35-block Void Core lattice

The **Void Core Controller** is the first VoidCore-scale multiblock. Including the controller, the structure contains 35 blocks. The 34 surrounding requirements are:

- a 5×5 `REINFORCED_DEEPSLATE` perimeter at controller Y (16 blocks),
- upper/lower cardinal `COPPER_BLOCK` field pylons (8 blocks),
- upper/lower diagonal `TINTED_GLASS` phase lenses (8 blocks),
- `AMETHYST_CLUSTER` directly above the controller,
- `SCULK_CATALYST` directly below the controller.

A stable, complete core can consume Stabilized Condensate + Containment Plate, routed Entropy, routed Computation, heat, Flux, and field stability to synthesize a **Void Seed**.

### SQLite schema v4

Schema v4 adds observer program, selected control directive, and lifetime production/incident counters. The migration remains column-idempotent, so interrupted/manual partial upgrades can be retried safely.

## 0.6 gameplay systems

### Entropy is now a real factory variable

Advanced processes generate persistent **Entropy**. High entropy increases wear; high-energy late-tier machines can enter a staged coherence-failure chain. Entropy does not disappear just because a GUI closes or the server restarts.

A Flux Bus graph can extract excess entropy from attached processors and route it toward an **Entropy Condenser Array** or a currently active processor whose registered recipe explicitly consumes Entropy, such as the Void Core. Condensers remain the bulk sink; active process consumers request only a bounded working buffer. Entropy transport has its own graph bandwidth and hop loss, so a badly designed factory can still saturate even when raw Flux supply is adequate.

Breaking a machine is not an entropy reset exploit: the dropped VoidCore machine item preserves its entropy load, fault stage, escalation timer, wear, and engineering quality.

### Observation + computation

The **Phase Observer** converts environmental correlation into a persistent computation buffer while consuming Flux. Yield reacts to:

- open sky,
- clear night sky,
- local sculk density,
- the End,
- the Nether,
- machine quality and coherence state.

Computation is routed over the physical Phase Logistics graph to computation-aware consumers. In 0.7, Entropy Condensers, Control Matrices, and the Void Core can all consume routed computation for reclamation, factory policy, or containment work.

### First physical multiblock

The **Entropy Condenser Controller** only processes multiblock recipes while its 17-block surrounding array is valid.

At controller Y:

- four diagonal corners: `POLISHED_BLACKSTONE_BRICKS`
- four cardinal blocks: `COPPER_GRATE`

At Y + 1:

- four diagonal corners: `AMETHYST_BLOCK`
- four cardinal blocks: `TINTED_GLASS`
- center above controller: `LIGHTNING_ROD`

The controller itself is the custom Beacon block. A Flux Bus can attach below the controller.

The first condenser process consumes captured Entropy + routed Computation to reclaim **Thermal Residue** into **Recovered Feedstock**, while condensing part of the waste state into **Entropy Condensate**.

### Closed material loops

Recovered Feedstock can be reconditioned into Cryo Salt and Pyrogel. The point is not a free-resource generator: the loop converts prior waste back into useful industrial feedstock while demanding infrastructure, Flux, computation, pressure-era materials, and entropy handling.

### Environmental process predicates

The generic process definition can now require a real world/environment condition. The first gated production process is **Void-Tempered Containment Plate**, which must run in the End. The predicate system already supports unrestricted, open-sky, clear-night, sculk-field, Nether, and End conditions.

### Chained faults

Entropy-aware high-energy machines can progress through:

`Coherence Drift → Entropy Surge → Containment Breach`

Coherence Drift is a soft fault: the machine still runs, but throughput, Flux efficiency, wear, and output quality degrade. Later stages hard-lock processing and require explicit repair components. A sustained-onset window prevents a one-second entropy spike from creating an immediate fault before a healthy condenser network can drain it.

### Network analytics + cross-tick path caching

Phase Logistics now keeps a rolling in-memory telemetry window per resolved network and reports:

- average delivered Flux,
- average item movement,
- average captured Entropy,
- average routed Computation,
- Flux loss percentage,
- Flux-starved endpoints,
- entropy-stressed endpoints,
- computation-starved condensers,
- blocked producer outputs,
- a dominant bottleneck classification.

Physical graph topology receives a deterministic signature. If topology/frequency configuration is unchanged on the next graph pass, previously computed shortest paths are reused across ticks. Any network-block/frequency topology change invalidates that component cache.

## Progression path

`Resonance Theory → Field Fabrication → Flux Handling → Spectral Analysis → Harmonic Engineering → Resonant Metallurgy → Thermal Engineering → Catalytic Matrices → Thermal Infrastructure → Quantum Routing → Pressure Dynamics → Entropy Condensation → Observational Computation → Spatial Engineering → Singularity Containment → Void Core Architecture → Automation Architecture → Dimensional Infrastructure → Ascendant Engineering`

0.8 extends that evidence chain with field visualization, closed-loop signal automation, grouped remote operations, supported singularity upgrades, Void Seed refinement, dimensional linking, and Project Nullstar commissioning. Research continues to require demonstrated gameplay behavior, not only Insight currency.

## Building

```bash
gradle clean build
```

The deployable artifact is the **unclassified shaded JAR** in `build/libs/`. Do not deploy the `*-plain.jar`; it intentionally omits the SQLite runtime dependency.

GitHub Actions is configured for Temurin Java 25 + Gradle 9.1 and uploads only the shaded artifact.

## Alpha notes

- Back up the world and `plugins/VoidCore/` before upgrading.
- SQLite is authoritative for placed-machine state.
- 0.8 migrates the database to schema v5 automatically; the migration remains idempotent at the column level.
- Network telemetry history is intentionally in-memory analytics; authoritative machine resources remain persisted in SQLite.
- Run `TESTING.md` before using the alpha on a valuable survival world.

See `ARCHITECTURE.md`, `MIGRATION.md`, `DESIGN.md`, `CHANGELOG.md`, and `TESTING.md` for implementation invariants and verification coverage.
