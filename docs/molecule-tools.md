# Molecule Tools (ppmol_gen)

Two versions of the molecule generator are included with Particle Playground:

- **C++ version**: `tools/ppmol/ppmol_gen` (standalone, no dependencies)
- **Python version**: `tools/ppmol/ppmol_gen.py` (supports PubChem, RDKit)

## Building the C++ Tool

```bash
./build.sh tools
# Output: build/ppmol_gen
```

## C++ Usage

### Generate from Formula

```bash
ppmol_gen gen <output.ppmol> <formula> [options]
```

Options:
- `--seed N` — Random seed for layout
- `--scale F` — Inter-atom spacing (default: 36.0)
- `--no-particles` — Skip sub-particle generation (positions only)

Examples:
```bash
ppmol_gen gen water.ppmol H2O
ppmol_gen gen glucose.ppmol C6H12O6
ppmol_gen gen caffeine.ppmol C8H10N4O2
```

Supported elements: H, He, Li, Be, B, C, N, O, F, Ne, Na, Mg, Al, Si, P, S, Cl, Ar, K, Ca, Fe, Cu, Zn, Br, I, U

### Inspect a File

```bash
ppmol_gen dump <file.ppmol>
```

### Validate Integrity

```bash
ppmol_gen validate <file.ppmol>
```

### Render to PNG

```bash
ppmol_gen render <file.ppmol> <output.png> [--width N] [--height N] [--scale F]
```

### Copy (Round-Trip Test)

```bash
ppmol_gen copy <input.ppmol> <output.ppmol>
```

## Python Usage

The Python version supports additional input sources:

### From Chemical Formula

```bash
python3 ppmol_gen.py --formula-only H2O --out water.ppmol
```

### From PubChem

```bash
# By name
python3 ppmol_gen.py --pubchem-name caffeine --out caffeine.ppmol

# By CID
python3 ppmol_gen.py --pubchem-cid 2519 --out caffeine.ppmol
```

### From SDF/MOL Files

```bash
python3 ppmol_gen.py --sdf molecule.sdf --out molecule.ppmol
python3 ppmol_gen.py --mol molecule.mol --out molecule.ppmol
```

### From SMILES (requires RDKit)

```bash
python3 ppmol_gen.py --smiles "CC(=O)Oc1ccccc1C(=O)O" --out aspirin.ppmol
```

### Python Options

- `--out <path>` — Output .ppmol path (required)
- `--formula <label>` — Chemical formula label
- `--normalize` — Center and scale 2D coordinates
- `--coord-scale <float>` — Inter-atom spacing (default: 36.0)
- `--electrons-from-charge` — Electron count from Z minus formal charge

## File Format

See [Molecule Format](molecule-format.md) for the binary .ppmol specification.
