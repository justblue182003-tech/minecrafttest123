# Changelog

## 0.8.0-alpha

### Added

- Universal machine automation coordinates: 8 machine groups, 16 signal channels, and Ignore/Require-High/Require-Low gates.
- Signal Crystal configuration panel available from any understood VoidCore machine.
- Automation Terminal with condition-driven rules for entropy, Flux, blocked output, field stability, wear, faults, and computation.
- Persistent per-machine/per-item production ledger.
- Void Core singularity operating modes: Contained, Compressed, Extraction, and Quiescent.
- Void Core Upgrade Chamber with Stabilization, Compression, and Extraction specializations.
- Compressed Void Seed and Dimensional Kernel Void Core processes.
- Dimensional Anchors that bridge loaded, matching-frequency Phase graphs across worlds while consuming computation.
- Cross-dimensional Flux/Entropy loss and higher item-routing bandwidth cost.
- Project Nullstar Terminal and non-consumptive server-scale commissioning objective.
- Quality-100 Ascendant Core commissioning reward with immediate material discovery.
- Automation Architecture, Dimensional Infrastructure, and Ascendant Engineering research nodes.
- Closed-Loop Automation, Remote Operations, Core Upgrade, Refined Singularity, Dimensional Phase Link, Visible Stability, and Project Nullstar experiments.
- Player-local spatial field visualization from Machine Diagnostics.
- Expanded/paginated late-game Research, Experiment, Machine, and Material surfaces.
- SQLite schema v5 fields for automation coordinates/rules, singularity/chamber modes, and encoded per-item production ledger.

### Changed

- Phase-network evaluation now runs before spatial-field and machine simulation so current signals/control policy affect the same production second.
- Conditional Automation Terminal rules consume computation even when their evaluated output is LOW.
- Remote Operations requires at least three endpoints in the terminal's selected automation group.
- Closed-Loop Automation requires a HIGH output from a non-trivial terminal rule and a gated target on the same group/channel.
- Void Core process tuning and field-fault pressure now depend on singularity mode and active support chambers.
- Dimensional links require healthy, loaded anchors with matching primary frequency and sustained computation on both ends.
- Project Nullstar validates persistent production history and active infrastructure rather than deleting milestone materials.
- CI artifact metadata now publishes `VoidCore-0.8.0-alpha`.

### Integrity / migration

- v4→v5 migration uses `addColumnIfMissing` for every new column and remains safe to retry after partial migration.
- Machine drops preserve automation group/channel/gate, terminal rule, singularity mode, chamber mode, and production ledger in addition to existing quality/wear/entropy/fault/history state.
- Dimensional transport remains bounded by the local physical graph and does not create globally addressable wireless inventories.
- Project Nullstar reward is one-time per player through the persistent experiment completion state.

### Validation

- Static enum/reference checks cover 91 custom item identities, 19 research nodes, 37 experiments, and 23 machine/network types.
- Recipe registry contains 92 unique Codex recipe IDs, including 16 generated process recipes.
- Material/component index contains 61 entries and remains paginated.
- SQLite v5 contract aligns 46 explicit machine columns, 46 placeholders, and JDBC bindings 1–46.
- Simulated v1→v5 migration can be applied twice and still executes a valid 46-column machine insert.
- Full local compile-oriented pass reaches expected missing Paper/Adventure symbols in the Java-21 offline environment; Java-25 authoritative build remains configured in CI.

## 0.7.0-alpha

### Added

- Spatial field stability as a live 0–100 engineering variable computed from physical factory layout.
- Field Stabilizer machine with distance-falloff coherence projection and continuous Flux/Entropy/wear cost.
- Five persistent Phase Observer programs: Broad Spectrum, Celestial Tracking, Sculk Correlation, Dimensional Baseline, and Entropy Watch.
- Control Matrix network block with Balanced, Throughput, Efficiency, and Stability directives.
- Computation-backed deterministic factory-wide control broadcast with safe Balanced fallback.
- Bounded Entropy routing to active entropy-consuming processors, allowing the Void Core to receive its registered synthesis resource without turning it into a bulk Entropy sink.
- Persistent lifetime machine counters for cycles, produced items, consumed Flux, processed Entropy, and incidents.
- Factory graph production ledger aggregated in Network Diagnostics.
- Minimum spatial-field requirement in generic process recipes and `FIELD_UNSTABLE` process state.
- Stabilized Condensate endgame recycling process.
- Spatial Anchor, Control Matrix Core, Void Casing, Stabilized Condensate, Void Seed, Field Stabilizer, Control Matrix, and Void Core custom items/machines.
- 35-block Void Core containment lattice.
- Void Seed synthesis requiring multiblock validity, heat, Flux, Entropy, Computation, and >=82% spatial stability.
- Field Desync → Field Collapse recoverable incident chain during an active Void Core cycle; incidents stress nearby machinery without griefing world blocks.
- SQLite schema v4 with observer program, selected control directive, and lifetime production/incident counters.
- Spatial falloff/clamping regression tests.

### Changed

- Spatial Engineering now provides both stabilizer and Control Matrix infrastructure, eliminating circular progression before Singularity Containment.
- Singularity Containment requires a demonstrated control broadcast and >=80% field calibration.
- Machine, Research, and Experiment index layouts were expanded so all 0.7 entries remain visible.
- Engineering and machine diagnostics now expose spatial field, active control policy, multiblock-specific geometry, and lifetime production history.
- Network diagnostics now expose Control Matrix count, active directive, controlled endpoint count, and persistent aggregate production history.
- Codex-generated process descriptions include spatial-field requirements; recipe station handling includes the Void Core.
- Machine relocation PDC now also preserves Observer program, Control Matrix directive, lifetime production counters, and incident count.
- CI artifact metadata now publishes `VoidCore-0.7.0-alpha`.

### Integrity / validation

- 82 custom item identities resolve.
- 83 unique Codex recipe IDs; 14 are data-driven process definitions.
- 16 research nodes fit 16 assigned research slots.
- 30 experiments fit 31 experiment slots.
- 19 machine/network types fit 19 machine-index slots.
- 56 material/component entries remain covered by the paginated Material Index.
- SQLite v4 simulation reaches 39 columns and successfully executes the repository's 39-column / 39-placeholder INSERT after idempotent v1→v4 migration.
- Full local source parsing reports no Java syntax/parser errors; unresolved diagnostics are limited to unavailable Paper/Adventure dependencies in this Java-21 environment.


## 0.6.0-alpha

### Added

- Persistent machine Entropy as an engineering resource generated and consumed by generic process definitions.
- Phase Observer with environment-sensitive computation generation and network-exportable computation storage.
- Entropy Condenser Controller and the first physical 17-block VoidCore multiblock array.
- Entropy routing from processors toward condensers with independent per-bus bandwidth and hop loss.
- Computation routing from Phase Observers toward computation-aware consumers.
- Generic process environmental predicates: unrestricted, open sky, clear night, sculk field, Nether, and End.
- Recovered Feedstock / Entropy Condensate waste-reclamation loop.
- Void-Tempered Containment Plate process requiring End operation.
- Coherence Drift -> Entropy Surge -> Containment Breach staged fault chain for entropy-aware high-energy machines.
- Coherence Damper and Containment Fuse repair components.
- Sustained entropy-pressure onset/escalation timers rather than single-tick fault transitions.
- Cross-tick topology signatures and shortest-path cache reuse for unchanged Phase Logistics graphs.
- Rolling per-network history for Flux, items, Entropy, Computation, starvation, blocked output, and bottleneck classification.
- Entropy/Computation/fault visibility in engineering diagnostics and network endpoint diagnostics.
- SQLite schema v3 fields for Entropy, Computation, and fault escalation ticks.
- PDC-backed machine-item relocation state for quality, wear, Entropy, fault identity, and fault timer.
- Material Index pagination for the expanded component catalog.
- Network-history regression tests and expanded 0.6 verification coverage.

### Changed

- Generic process execution now supports Entropy generation/cost, Computation cost, environmental predicates, and multiblock requirements.
- Singularity Containment progression now passes through Entropy Condensation and Observational Computation evidence.
- Entropy-aware soft faults degrade throughput/efficiency/output quality before hard containment failure.
- Phase Logistics now transports three infrastructural resources: Flux, Entropy, and Computation, while preserving frequency isolation.
- Stable network topologies reuse path results across graph passes; topology/frequency changes invalidate the cache deterministically.
- Entropy fault onset uses a configurable grace interval so a healthy condenser network can drain brief local spikes before failure begins.
- Advanced machine break/replacement no longer clears Entropy or fault progression.
- The Codex exposes environmental, multiblock, Entropy, and Computation requirements from the same process registry used at runtime.
- CI artifact metadata now publishes `VoidCore-0.6.0-alpha`.

### Integrity / migration

- v2 -> v3 SQLite migration uses column-existence checks and is safe to retry after a partially applied migration.
- Machine relocation persists the non-volatile state needed to prevent break-to-reset exploits while process inventories/upgrades continue to drop safely.
- Entropy transport keeps a donor reserve and targets bounded condenser fill levels; Computation transport similarly preserves observer reserve.
- Entropy Condenser recipes pause safely if the physical array becomes invalid, without prematurely consuming a completed batch.
- Cross-tick topology caches expire after absent graphs and invalidate on physical/frequency topology changes.
- Priority Buffers remain excluded as direct destinations for other Priority Buffers, preserving the 0.5 anti-ping-pong invariant.

### Validation

- Static source reference checks: 74/74 custom item IDs resolve; 14 research nodes, 23 experiments, and 16 machine/network types fit their menus.
- Recipe registry check: 74 unique Codex recipe IDs, including 12 generated process recipes.
- Material Index check: 51 material/component entries paginate across 36-entry pages without hiding late-game content.
- SQLite v3 check: 32 machine columns/fields align with all 32 repository bindings.
- Pure-Java regression sources compile under the local JDK; full source parsing reaches only expected missing Paper/JUnit/API symbols in this Java-21 offline environment.
- Authoritative Paper 26.3 / Java 25 compile-test-build remains configured in GitHub Actions.

## 0.5.0-alpha

### Added

- Phase Router with endpoint priority and exact custom-item filtering.
- Priority Buffer as a network-visible staging inventory.
- Frequency Splitter with explicit primary/secondary frequency domains.
- Deterministic route ranking by priority, shortest path, then stable endpoint address.
- Per-graph-evaluation shortest-path cache with diagnostics hit/miss counters.
- Player-local visual route tracing for the last successful transfer path.
- Pressure Vessel engineering processor.
- Persistent current/target pressure and powered compression/passive equalization.
- Pressure windows in generic `ProcessRecipe` definitions and `ProcessEngine` validation.
- Pressure accuracy as an output-quality and wear input.
- Pressurized Matrix and Dense Phase Composite process chain.
- Pressure Dynamics research node.
- Deterministic Priority, Frequency Bridge, Pressure Synthesis, and Fault Recovery experiments.
- Repair Parts, Pressure Seal, Routing Core, Filter Matrix, and new logistics components.
- Machine hard-fault model with bearing failure, thermal runaway, seal leak, and routing-desync identities.
- Pressure-seal fault generation and explicit repair-item consumption.
- SQLite schema v2 fields for pressure, faults, secondary frequency, route priority, and route filter.
- Immutable `MachineSnapshot` capture for async database writes.
- Revision-aware dirty-state handling so stale async writes cannot mark newer state clean.

### Changed

- Entropy Condensation now follows Pressure Dynamics and requires pressure/fault-recovery evidence.
- Phase Logistics can route through mixed-frequency components only when a Frequency Splitter physically bridges the domains.
- Endpoint selection is deterministic rather than relying on collection iteration order.
- Endpoints touching multiple network blocks use a stable canonical attachment, removing hash-iteration route drift.
- Priority Buffers do not route directly into other Priority Buffers, preventing idle buffer-to-buffer ping-pong.
- Network diagnostics expose frequency domains, routers/buffers/splitters, policy traffic, bridge traffic, path-cache behavior, and route tracing.
- Engineering machine UI exposes pressure controls and pressure-low/high/faulted process states.
- Machine diagnostics expose the pressure model for pressure-capable processors.
- Persistence interval uses asynchronous snapshot writes while retaining synchronous shutdown durability.
- CI artifact metadata now publishes `VoidCore-0.5.0-alpha`.

### Integrity / migration

- v1→v2 SQLite migration checks for existing columns before altering the table, making partial migration recovery idempotent.
- Async persistence serializes Bukkit item state during main-thread snapshot capture; the worker phase contains JDBC/data primitives only.
- Filters are checked before producer output is removed. Failed delivery returns staged output to the producer.
- Frequency isolation remains the default; splitters are the only implemented cross-domain bridge.

### Validation

- Static source reference checks: 65/65 custom item references resolve; 13 research nodes and 18 experiments fit their menus; 14 machine types fit the Machine Index.
- Recipe registry check: 64 unique Codex recipe IDs, including 10 generated process recipes.
- SQLite schema/29-field repository INSERT simulation succeeds under SQLite.
- Local Java parser pass reports no Java syntax diagnostics before expected missing Paper/JUnit dependency errors.
- Authoritative Paper 26.3/Java 25 compilation remains configured in GitHub Actions.

## 0.4.0-alpha

### Added

- SQLite machine persistence through Xerial `sqlite-jdbc`, shaded into the distributable JAR.
- Versioned `vc_meta` schema table and v1 `machines` schema.
- Transactional migration from legacy `machines.yml` when the SQLite table is empty.
- NBT-byte ItemStack persistence for machine inventories/upgrades.
- Secondary process-input port.
- Dedicated byproduct output port.
- Explicit selected-process identity on machines.
- Multi-input and byproduct fields in `ProcessRecipe`.
- Machine wear from process cycles, thermal stress, and heat-exchanger operation.
- Service lockout at critical wear.
- Precision Maintenance Kit and quality-scaled servicing.
- Cooling Jacket upgrade module.
- Phase Interface upgrade module.
- Powered active cooling and negative-temperature targets.
- Cryogenic Column.
- Thermal Exchanger with adjacent heat recovery and transfer losses.
- Reactive Slurry, Purified Matrix, Cryo Salt, Thermal Residue, Superheated Phase Glass, Phase Thread, Address Crystal, and related 0.4 components.
- Four new advanced process definitions, bringing the advanced registry to eight processes.
- Thermal Infrastructure research node.
- Coupled Feed, Cold Fraction, Preventive Maintenance, and Shared Load experiments.
- Flux Bus network block.
- Address Node network block.
- Frequency-isolated network graph discovery.
- Hop-aware Flux loss and throughput-constrained load balancing.
- Phase-Interface-gated automatic item routing between compatible process ports.
- Network address generation and live endpoint diagnostics.
- Phase Logistics diagnostics GUI with starvation, throughput, loss, item movement, and route-depth data.
- Shift-click frequency adjustment by ±10.
- Pure `EngineeringMath` calculations and JUnit test fixtures.
- Shadow build configuration for a server-ready JAR containing SQLite.

### Changed

- Research path now inserts Thermal Infrastructure before Quantum Routing.
- Quantum Routing now requires thermochemical/cold-separation evidence.
- Entropy Condensation now requires a successful network load-balancing experiment.
- Engineering GUI now supports primary feed, secondary feed, catalyst, main output, byproduct, process selection, maintenance state, and projected quality.
- Cryogenic and hot processes share the same generic process engine.
- Flux Crucible now accumulates wear and exposes service lockout in its UI.
- Machine Index now supports all ten implemented machine/network types.
- Material Index capacity expanded for the larger 0.4 catalog.
- Research and Experiment menu slot maps expanded to show every 0.4 entry.
- Thermal Exchanger no longer advertises inaccessible upgrade sockets.
- Flux Bus endpoints are restricted to actual flux/process machines rather than passive infrastructure.
- Network bandwidth is based on Flux Bus count rather than all network-node blocks.
- Recipe matching retains a process definition when a required secondary input is missing, allowing the UI to report the correct missing-feed state.
- Failed SQLite snapshot writes now leave machine state marked dirty for a future retry.

### Safety / integrity

- Secondary-input and byproduct slots are included in break/explosion persistence handling.
- Output and byproduct insertion are rejected by the engineering UI.
- Network routing returns a taken output to the producer when no compatible consumer accepts it.
- Legacy YAML is renamed only after a successful SQLite migration transaction.
- Existing piston and hopper protections remain active for all new machine/network blocks.

### Validation

- Source-wide Java syntax pass performed with the locally available compiler; no syntax diagnostics were found before dependency resolution failures.
- Pure engineering/network math is covered by JUnit fixtures.
- Full Paper 26.3 compile/test remains configured in GitHub Actions with Java 25.

## 0.3.0-alpha

- Added persistent 0–100 component/machine quality.
- Added engineering quality grades and quality propagation.
- Added generic advanced process registry/engine/tuning architecture.
- Added temperature windows, thermal inertia, powered heating, and diagnostics.
- Added Cycle Governor, Flux Regulator, Thermal Coupler, and Catalyst Filter upgrades.
- Added Induction Heater, Catalytic Reactor, and Matrix Purifier.
- Added reusable Catalyst Matrices with contamination and purification.
- Added Thermal Engineering and catalytic experiments.
- Added restart-safe completed-process identity for experiment credit.

## 0.2.0-alpha

- Added Prototype Bench, Spectrum Analyzer, centralized recipe browser, Material/Machine indices, research experiments, and expanded Tier-I progression.

## 0.1.0-alpha

- Initial research/Insight framework, Void Codex, Resonant Fragment discovery, Flux Crucible, custom items, persistence, recipes, and admin/debug commands.
