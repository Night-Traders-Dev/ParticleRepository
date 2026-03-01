# Element File Format (.ppel)

Binary format for storing a single element (atom with its constituent particles).

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

## Naming Convention

Files use isotope notation: `{Symbol}-{A}.ppel` where A is the mass number (Z + N).

Examples:
- `H-1.ppel` — Hydrogen (1 proton, 0 neutrons)
- `C-12.ppel` — Carbon-12 (6 protons, 6 neutrons)
- `Fe-56.ppel` — Iron-56 (26 protons, 30 neutrons)
- `U-238.ppel` — Uranium-238 (92 protons, 146 neutrons)

## Generation

Use `ppel_gen` to create element files:

```bash
# Single element (by symbol, name, or atomic number)
ppel_gen gen output.ppel Fe
ppel_gen gen output.ppel Iron
ppel_gen gen output.ppel 26

# Specific isotope
ppel_gen gen Deuterium.ppel H --neutrons 1

# All 118 elements
ppel_gen gen-all elements/

# Inspect
ppel_gen dump Fe-56.ppel
ppel_gen validate Fe-56.ppel

# List periodic table
ppel_gen list
```

## Example

A Helium-4 atom (2 protons, 2 neutrons, 2 electrons) would have:
- Z=2, N=2, electrons=2
- 6 particles total (2p + 2n + 2e)
- Protons and neutrons clustered near (0,0) in a hex-packed layout
- Electrons in the first shell at ~12px radius

## Limits

| Limit | Value |
|-------|-------|
| Max particles per element | 10000 |

## Repository Contents

The repository contains all 118 elements of the periodic table as their most
common stable isotope, from Hydrogen (H-1, 2 particles) to Oganesson (Og-294,
412 particles).
