# VoidCore migration

## 0.7.x → 0.8.0-alpha

0.8 upgrades SQLite from schema v4 to **v5**. Startup adds the following columns only when missing:

- `automation_group INTEGER NOT NULL DEFAULT 0`
- `signal_channel INTEGER NOT NULL DEFAULT 0`
- `signal_gate TEXT NOT NULL DEFAULT 'ignore'`
- `automation_rule TEXT NOT NULL DEFAULT 'always'`
- `singularity_mode TEXT NOT NULL DEFAULT 'contained'`
- `core_chamber_mode TEXT NOT NULL DEFAULT 'stabilization'`
- `production_ledger TEXT NOT NULL DEFAULT ''`

Existing 0.7 machines therefore default to group G0, CH0, signal gating disabled, Always-High terminal policy, Contained Void Core mode, Stabilization chamber mode, and an empty per-item ledger. Existing inventories, process state, quality, wear, Entropy, Computation, faults/timers, routes, observer program, Control Matrix policy, and lifetime aggregate counters remain intact.

The current repository explicitly writes **46 columns with 46 JDBC bindings**. Migration uses the same `addColumnIfMissing` invariant as earlier versions; a simulated v1→v5 upgrade applied twice remains valid and accepts a complete 46-field insert.

### Machine-item relocation

0.8 machine drops additionally preserve automation group/channel/gate, Automation Terminal rule, Void Core singularity mode, upgrade-chamber mode, and the encoded per-item production ledger. Old 0.7 machine items simply lack those PDC keys and place with the safe defaults above.

### Network behavior changes

0.8 adds cross-dimensional graph edges only between **loaded Dimensional Anchors** that:

- are in different worlds,
- share the same primary frequency,
- are not maintenance-locked,
- and each have enough computation to sustain the link.

The feature does not migrate or rewrite existing frequencies. A normal 0.7 network remains local until the player deliberately builds powered anchors.

### Recommended upgrade procedure

1. Stop the server cleanly and back up the world plus `plugins/VoidCore/voidcore.db`.
2. Replace the old JAR with the shaded 0.8 JAR built under Java 25.
3. Start the server and verify the 0.8 enabled message appears without SQLite errors.
4. Inspect representative 0.7 machines for inventory, quality, wear, Entropy, fault state, observer program, and lifetime counters.
5. Inspect Machine Diagnostics and confirm new automation values begin at G0 / CH0 / Ignore.
6. Only then build Automation Terminals, Upgrade Chambers, and Dimensional Anchors.

### Rollback warning

A 0.7 binary does not understand all v5 gameplay semantics. If rollback is necessary, restore the pre-upgrade database backup rather than continuing to write the migrated v5 database with an older plugin binary.

## 0.6.x → 0.7.0-alpha

0.7 upgrades SQLite from schema v3 to **v4**. Startup adds the following columns only when missing: `observer_program`, `control_directive`, `lifetime_cycles`, `lifetime_items_produced`, `lifetime_flux_consumed`, `lifetime_entropy_processed`, and `incident_count`. Defaults preserve old-world behavior: broad-spectrum observers, Balanced control policy, and zeroed lifetime counters.

Existing 0.6 machines, inventories, Entropy, Computation, faults, route policy, heat/pressure state, quality, and wear remain intact. The migration is transactional and column-idempotent. The current repository explicitly writes 39 columns with 39 JDBC bindings.

Spatial field stability and active network policy are intentionally **not** database columns because they are derived from current loaded topology each simulation pass. Breaking/replacing a machine preserves observer program, selected control directive, lifetime counters, Entropy, fault state/timer, wear, and quality through PDC on the custom machine item.

### Recommended upgrade procedure

1. Stop the server cleanly and back up `plugins/VoidCore/voidcore.db`.
2. Replace the old JAR with the shaded 0.7 JAR built under Java 25.
3. Start the server and verify the log reaches the 0.7 enabled message without SQLite errors.
4. Inspect one existing observer, condenser, logistics network, and pressure machine.
5. Build Spatial Engineering hardware only after confirming the migrated factory is operating normally.

## Historical: 0.5.x → 0.6.0-alpha

## Supported path

0.6 is designed to migrate existing 0.5 SQLite worlds in place.

1. Stop the server cleanly.
2. Back up the world and the complete `plugins/VoidCore/` directory.
3. Replace the old plugin JAR with the 0.6 shaded JAR.
4. Start the server and inspect the log for migration/database errors.
5. Open representative machines and network diagnostics before resuming normal play.

## Database schema

VoidCore 0.6 uses **schema version 3**.

v2 → v3 adds:

- `entropy REAL NOT NULL DEFAULT 0`
- `computation INTEGER NOT NULL DEFAULT 0`
- `fault_ticks INTEGER NOT NULL DEFAULT 0`

Each `ALTER TABLE` is guarded by a column-existence check, so a partially applied migration can be retried without duplicate-column failure.

Existing machines receive zero Entropy, zero Computation, and zero fault ticks. Existing fault identity, pressure, routing policy, inventories, quality, wear, frequencies, and process state remain intact.

## Machine-item relocation state

0.6 machine drops carry new PDC fields for entropy + fault state. Old 0.5 machine items simply lack those keys and therefore place with zero entropy/no fault. This is backward-compatible.

## Network behavior changes

No network block migration is required. The 0.6 resolver adds:

- cross-tick topology/path caching,
- entropy transport to condenser controllers,
- computation transport from Phase Observers,
- rolling in-memory telemetry.

Frequency semantics and physical adjacency remain compatible with 0.5.

## Research/player data

Research/experiment state remains stored in player PDC. New nodes and experiments are additive. Existing unlocked research does not get revoked.

The Material Index is now paginated because the 0.6 material/component catalog exceeds one 54-slot inventory page.

## Rollback warning

Do not expect a 0.5 binary to understand all schema-v3 gameplay semantics. If rollback is necessary, restore the pre-upgrade database backup rather than pointing 0.5 at an actively used 0.6 database.
