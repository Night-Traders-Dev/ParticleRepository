# Element File Format (.ppel)

Binary format for storing a single element (atom or nucleus with its constituent particles).

## Header

| Offset | Size | Type | Description |
|--------|------|------|-------------|
| 0 | 4 | uint32 | Magic: `0x4C455050` ("PPEL" LE) |
| 4 | 4 | uint32 | Version: `1` |
| 8 | 4 | int32 | Z (atomic number / proton count) |
| 12 | 4 | int32 | N (neutron count) |
| 16 | 4 | int32 | Electron count |
| 20 | 4 | uint32 | Particle count |

## Per-Particle Data (repeats `particle_count` times)

| Offset | Size | Type | Description |
|--------|------|------|-------------|
| 0 | 4 | float | dx — X offset from nucleus center |
| 4 | 4 | float | dy — Y offset from nucleus center |
| 8 | 4 | float | vx — velocity X |
| 12 | 4 | float | vy — velocity Y |
| 16 | 4 | float | energy |
| 20 | 4 | uint32 | type — particle type index |
| 24 | 16 | float[4] | genome: [charge, spin, color_charge, decay_rate] |

Total per-particle: 40 bytes.

## Byte Order

All values are little-endian.

## Type Indices

| Index | Particle |
|-------|----------|
| 0 | Proton |
| 1 | Neutron |
| 2 | Electron |
| 3 | Photon |
| 4 | Positron |
| 5 | Antiproton |

See the simulation source for the full type table (68 types).

## Example

A Helium-4 atom (2 protons, 2 neutrons, 2 electrons) would have:
- Z=2, N=2, electrons=2
- 6 particles total (2p + 2n + 2e)
- Protons and neutrons clustered near (0,0) with small offsets
- Electrons in orbital shells at larger radii
