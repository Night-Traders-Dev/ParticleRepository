# Contributing to ParticleRepository

## Adding Files

### Via Pull Request

1. Fork this repository on GitHub
2. Create your `.ppel` or `.ppmol` files
3. Place them in the correct directory:
   - Elements: `elements/{Symbol}-{MassNumber}.ppel`
   - Molecules: `molecules/{Formula}.ppmol`
4. Open a Pull Request with a brief description

### Via In-Game Upload

If you have collaborator access:

1. Generate a [GitHub Personal Access Token](https://github.com/settings/tokens) with `repo` scope
2. In Particle Playground, open the Repository dialog
3. Expand "GitHub Token" and paste your token
4. Expand "Upload to Repository"
5. Enter the full path to your file and click Upload

## Guidelines

### Elements

- Use standard isotope notation: `H-1`, `He-4`, `C-12`, `Fe-56`, `U-238`
- Export directly from the simulation using the element card's export button
- Verify the element loads correctly before submitting

### Molecules

- Use standard chemical formulas: `H2O`, `NaCl`, `C6H12O6`
- Generate with `ppmol_gen` for best compatibility
- Test import in the simulation before submitting
- Complex molecules should include proper bond topology

### Quality

- Files should load without errors in the current version
- Elements should have correct proton/neutron/electron counts
- Molecules should have physically reasonable atom positions and bonds

## Creating Files

### Elements

In the simulation:
1. Spawn an atom (use the periodic table in the Spawn Menu)
2. Open its element card (click the atom in select mode)
3. Click "Export" to save as `.ppel`

### Molecules

Option A — In-game:
1. Build a molecule by bonding atoms together
2. Open the molecule card
3. Click "Export" to save as `.ppmol`

Option B — ppmol_gen tool:
```bash
# From formula
ppmol_gen gen caffeine.ppmol C8H10N4O2

# From PubChem (Python version, requires internet)
python3 ppmol_gen.py --pubchem-name aspirin --out aspirin.ppmol
```

See [Molecule Tools](molecule-tools.md) for detailed usage.
