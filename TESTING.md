# VoidCore 0.8 testing matrix

## 0.8 release-critical scenarios

1. **Universal signal configuration:** place representative processors, passive infrastructure, and network blocks. Sneak-right-click each with a Signal Crystal and verify G0–G7, CH0–CH15, and all three gate states cycle and persist through restart and legitimate break/replacement.
2. **Closed-loop automation:** configure an Automation Terminal with a non-Always condition, a target group/channel, and at least one endpoint on the same group/channel with `Require High` or `Require Low`. Verify computation is consumed on both HIGH and LOW evaluations, the machine's run permission changes correctly, and Closed-Loop Automation is awarded only from a HIGH non-trivial drive with a matching gated target.
3. **Grouped remote operations:** put at least three endpoints in the terminal's selected group on one resolved Phase network. Confirm Remote Operations; move one endpoint to another group and confirm a fresh player cannot receive the experiment until the selected group again has three endpoints.
4. **Network-first timing:** toggle a signal condition and confirm the resolved signal/control policy affects machine processing in that same once-per-second simulation pass rather than one full machine tick later.
5. **Per-item production ledger:** produce multiple custom outputs on one machine, restart, break/replace the machine, and verify the item→count ledger survives and Diagnostics retains the top entries.
6. **Void Core singularity modes:** cycle Contained/Compressed/Extraction/Quiescent. Confirm speed, Flux, Entropy, and wear behavior changes; confirm Quiescent blocks active Void Core recipes without deleting staged inputs/progress.
7. **Upgrade chambers:** place powered Stabilization/Compression/Extraction chambers within range and verify diagnostics count only active nearby support. Confirm Compressed Void Seed requires a supported Compressed/Extraction state and Dimensional Kernel requires Extraction plus compression + extraction support.
8. **Dimensional anchors:** build matching-frequency loaded anchors in two worlds, feed both sufficient computation, and confirm one cross-dimensional network resolves. Remove computation, change one frequency, unload/remove an anchor, and verify the virtual edge disappears safely.
9. **Dimensional transport economics:** route Flux/Entropy/items across the dimensional edge and verify configured extra loss/bandwidth accounting and dimensional-transfer telemetry. Confirm local transport is unchanged.
10. **Project Nullstar:** satisfy the configured lifetime cycles, compressed-seed/kernel production, two-world anchor infrastructure, stable complete core, and terminal cross-dimensional network. Commission once; verify Project Nullstar completes, exactly one quality-100 Ascendant Core is awarded/discovered, and repeated clicks cannot duplicate it.
11. **Research reachability:** from a progressed 0.7-style player state, verify Stable Void Core Run + Field Visualization unlock Automation Architecture; Signal Automation + Remote Operations + Core Upgrade unlock Dimensional Infrastructure; Dimensional Link + Refined Void Seed + Project Nullstar unlock Ascendant Engineering. Confirm there is no circular gate.
12. **UI capacity:** verify all 19 research nodes are visible, all 37 experiments span the paginated experiment UI, all 23 machine/network types fit the Machine Index, and all 61 material/component entries span Material Index pages.
13. **Database migration:** migrate v4→v5, restart twice, and confirm no duplicate-column failure. Validate 46 explicit machine columns, 46 placeholders/bindings, and exact restoration of automation/singularity/chamber/ledger state.
14. **0.7 regression:** rerun observer programs, Control Matrix fallback, spatial field calculation, Void Core geometry/incidents, Entropy/Computation routing, topology caching, maintenance/fault recovery, pressure/thermal/catalyst systems, item routing, break/explosion protections, and output/byproduct blocking.

Run these checks on a disposable Paper 26.3 test world before production use.

## 0.7 regression scenarios

1. **Observer programming:** cycle all five Phase Observer programs in both directions, restart, and confirm the selected program persists. Verify celestial/sculk/dimensional/entropy-watch programs produce different signals in appropriate environments.
2. **Control broadcast:** attach a Control Matrix, Observer, and at least two processor endpoints. Select Throughput/Efficiency/Stability and confirm Network Diagnostics reports the policy and controlled endpoint count. Drain computation and confirm safe fallback to Balanced.
3. **Spatial field:** place a powered Field Stabilizer at several distances and confirm field contribution decreases with distance. Create entropy-heavy nearby equipment and confirm field falls. Confirm Stability policy raises and Throughput lowers the measured field.
4. **Spatial recipe gate:** attempt Stabilized Condensate below 80% field and confirm `FIELD_UNSTABLE`; raise the field to >=80% and confirm processing resumes without consuming a partial batch.
5. **Void Core geometry:** verify the controller alone reports an incomplete 34-position surrounding lattice. Build all 16 ring, 8 pylon, 8 lens, upper focus, and lower sink blocks; confirm the 35-block total assembly commissions. Remove/restore one block during a cycle and verify pause/resume behavior.
6. **Void Core resource routing:** load valid Void Seed feed into a networked core with insufficient local Entropy/Computation. Confirm Phase Logistics routes a bounded Entropy working buffer and computation to the core, and that the process begins only after all registered resource conditions are satisfied.
7. **Spatial incident:** while a Void Core has an active process, hold field below the configured desync threshold long enough to reach Field Desync, then below collapse threshold long enough to reach Field Collapse. Confirm no arbitrary world blocks are destroyed, nearby machinery receives stress, incident count increments, and Spatial Anchor repair clears the fault.
8. **Relocation exploit:** break a programmed observer, configured Control Matrix, and faulted/used Void Core; replace them and confirm program/directive, lifetime counters, Entropy, fault identity/timer, quality, and wear are preserved.
9. **Production history:** complete >=25 cycles on one machine, inspect it, and confirm Industrial History. Verify Machine Diagnostics and Network Diagnostics report lifetime counters and that values persist through restart.
10. **Database migration:** migrate a v3 database to v4, restart twice, and verify no duplicate-column failure. Validate 39 machine fields and all process inventory BLOBs.
11. **Topology/control determinism:** place two Control Matrices on one network with different quality. Confirm the higher-quality controller wins; use equal quality and confirm stable address tie-breaking.


Run these checks on a disposable Paper 26.3 test world before production use.

## 1. Upgrade + persistence

- Upgrade a populated 0.6/schema-v3 database; confirm schema v4 starts without duplicate-column errors.
- Restart with machines containing entropy, computation, faults, observer programs, Control Matrix directives, lifetime counters, process inventories, upgrades, pressure, filters, and frequencies; confirm exact restoration.
- Force/interrupt a test migration after one v4 column exists, restart, and confirm idempotent completion to all 39 fields.
- Trigger periodic async saves while modifying machines; confirm a stale successful write cannot clear newer dirty state.

## 2. Entropy accumulation

- Run each advanced processor long enough to generate entropy.
- Confirm entropy survives restart.
- Confirm elevated entropy increases wear pressure.
- Confirm an attached condenser network removes donor entropy above its reserve.
- Confirm entropy throughput scales with Flux Bus count and hop loss increases on longer routes.

## 3. Fault-chain timing

- Raise Pressure Vessel/Observer/Condenser entropy above drift threshold for less than the onset window; drain it and confirm no fault.
- Sustain the threshold and confirm Coherence Drift appears.
- Confirm Drift still allows processing but degrades cycle behavior/output quality.
- Hold >=85% entropy through the configured escalation interval; confirm Entropy Surge hard-locks processing.
- Hold >=95% through the next interval; confirm Containment Breach.
- Repair with the correct component; confirm one item is consumed in Survival, quality is retained, entropy is reduced to a recoverable level, and the fault clears.
- Confirm entropy-chain repair advances Cascade Arrest.

## 4. Break/replace anti-reset

- Break a machine with wear, entropy, a soft/hard fault, and nonzero fault ticks.
- Confirm stored process items/upgrades drop exactly once.
- Inspect the machine item: quality, wear, entropy, and fault must be represented.
- Place it again; confirm entropy/fault/fault-timer state is restored rather than reset.
- Repeat through explosion recovery where applicable.

## 5. Phase Observer

- Attach an Observer to a powered Flux Bus network.
- Compare baseline, open-sky, clear-night, dense-sculk, Nether, and End yields.
- Confirm Flux is consumed only while computation capacity has room.
- Confirm observation creates a small entropy load.
- Accumulate >=250 computation and interact with the Observer; confirm Correlated Observation completes.

## 6. Computation routing

- Put Observer and Entropy Condenser on the same physical network.
- Confirm computation moves only from Observer to Condenser and obeys per-bus bandwidth.
- Separate them by frequency without a splitter; confirm no transfer.
- Bridge frequencies with a splitter; confirm transfer resumes and bridge diagnostics increment.

## 7. Entropy Condenser multiblock

- Place controller alone; confirm 0/17-style incomplete diagnostics and blocked multiblock process state.
- Build lower layer: blackstone-brick diagonal corners + copper-grate cardinals.
- Build upper layer: amethyst diagonal corners + tinted-glass cardinals + lightning rod over controller.
- Confirm 17/17 and Array Commissioning experiment.
- Remove one frame block during a process; confirm processing pauses safely without consuming a completed batch.
- Restore it; confirm processing can resume.

## 8. Waste reclamation loop

- Route at least 42 entropy and 100 computation into a complete condenser.
- Supply 3 Thermal Residue + 1 Pressurized Matrix and sufficient Flux/heat.
- Confirm output is 3 Recovered Feedstock and byproduct is Entropy Condensate.
- Recover the output and confirm Closed Waste Loop experiment.
- Craft recovered Cryo Salt and Pyrogel; confirm duplicate-output recipes remain visible/selectable in the Codex without corrupting other recipes.

## 9. Environmental predicates

- Attempt Void-Tempered Containment Plate in the Overworld; confirm Environment Blocked.
- Move/rebuild the required Induction Heater in the End and satisfy heat/material conditions; confirm the process can complete.
- Recover the plate and confirm Environmental Constraint experiment.

## 10. Cross-tick topology cache

- Build a stable graph with several endpoint pairs; open diagnostics for several seconds.
- Confirm the first pass reports topology rebuild/misses, then later passes report topology reuse and increasing cache age/hits.
- Change a bus frequency or add/remove a network block; confirm cache age resets and paths are recomputed.
- Change only a route priority/filter; confirm topology remains reusable because graph edges did not change.

## 11. Network history + bottlenecks

- Intentionally starve Flux; confirm rolling telemetry identifies Flux starvation.
- Saturate several processors with entropy while condenser capacity is inadequate; confirm Entropy saturation classification.
- Block producer outputs; confirm blocked-output metrics/history respond.
- Starve a condenser of computation while a computation-cost process is selected; confirm computation-starved endpoint count.
- Let the problem recover; confirm rolling averages decay toward healthy over the configured history window.

## 12. UI/regression

- Confirm all 14 research nodes are visible.
- Confirm all 23 experiments are visible.
- Confirm all 16 machine types fit the Machine Index.
- Confirm 51 material/component entries span two Material Index pages and page navigation returns the correct recipe.
- Confirm Entropy Condenser process recipes show the new station icon and condition/resource lore.
- Repeat shift-click, drag, hopper, piston, break, explosion, restart, output-block, and byproduct-block checks on new systems.
