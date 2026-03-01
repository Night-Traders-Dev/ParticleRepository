# Molecule File Format (.ppmol)

Binary format for storing molecules — multiple atoms with inter-atomic bonds.

## Header

| Offset | Size | Type | Description |
|--------|------|------|-------------|
| 0 | 4 | uint32 | Magic: `0x4D4F4C50` ("PLOM" LE) |
| 4 | 4 | uint32 | Version: `2` |
| 8 | 4 | uint32 | Formula string length |
| 12 | N | char[] | Formula string (e.g., "H2O") |
| 12+N | 4 | uint32 | Name string length (v2+) |
| 16+N | M | char[] | Name string (e.g., "Water") — may be 0-length |
| 16+N+M | 4 | uint32 | Atom count |
| 20+N+M | 4 | uint32 | Bond count |

### Version History

- **v1**: Original format — formula, atoms, bonds only
- **v2**: Added name field after formula. Readers should accept both v1 and v2.

## Per-Atom Data (repeats `atom_count` times)

| Offset | Size | Type | Description |
|--------|------|------|-------------|
| 0 | 4 | int32 | Z (atomic number) |
| 4 | 4 | int32 | N (neutron count) |
| 8 | 4 | int32 | Electron count |
| 12 | 4 | float | cx_offset — X offset from molecule center of mass |
| 16 | 4 | float | cy_offset — Y offset from molecule center of mass |
| 20 | 4 | uint32 | Particle count for this atom |

### Per-Particle Data (repeats per atom)

Same as the element format:

| Offset | Size | Type | Description |
|--------|------|------|-------------|
| 0 | 4 | float | dx — X offset from atom center |
| 4 | 4 | float | dy — Y offset from atom center |
| 8 | 4 | float | vx |
| 12 | 4 | float | vy |
| 16 | 4 | float | energy |
| 20 | 4 | uint32 | type |
| 24 | 16 | float[4] | genome |

## Bond Data (repeats `bond_count` times)

| Offset | Size | Type | Description |
|--------|------|------|-------------|
| 0 | 4 | int32 | atom_a — index of first atom |
| 4 | 4 | int32 | atom_b — index of second atom |

## Limits

| Limit | Value |
|-------|-------|
| Max atoms per molecule | 1000 |
| Max bonds per molecule | 10000 |
| Max formula length | 256 characters |
| Max name length | 256 characters |
| Max particles per atom | 10000 |

## Byte Order

All values are little-endian.

## Example

Water (H2O) with 3 atoms and 2 bonds:
- Formula: "H2O" (length 3)
- Name: "Water" (length 5)
- Atom 0: O (Z=8, N=8, e=8), at center (0, 0)
- Atom 1: H (Z=1, N=0, e=1), offset (-17.4, 13.4)
- Atom 2: H (Z=1, N=0, e=1), offset (17.4, 13.4)
- Bond 0: atom 0 ↔ atom 1 (O-H)
- Bond 1: atom 0 ↔ atom 2 (O-H)

## Naming Convention

Files in the repository use the chemical formula as filename: `{Formula}.ppmol`

The common name is stored inside the binary and auto-detected for known molecules
by `ppmol_gen`. Custom names can be set with `--name`:

```bash
ppmol_gen gen Water.ppmol H2O                    # auto-detects "Water"
ppmol_gen gen MyMolecule.ppmol C4H8 --name "Cyclobutane"  # explicit name
```
