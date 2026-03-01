# ParticleRepository

Community repository for sharing element and molecule files for [Particle Playground](https://github.com/Night-Traders-Dev/EmergentEvolution).

## File Types

| Extension | Description | Format |
|-----------|-------------|--------|
| `.ppel` | Single element (atom/nucleus with particles) | [Element Format](docs/element-format.md) |
| `.ppmol` | Molecule (multiple atoms with bonds) | [Molecule Format](docs/molecule-format.md) |

## Naming Conventions

- **Elements**: `{Symbol}-{MassNumber}.ppel` (e.g., `H-1.ppel`, `He-4.ppel`, `U-238.ppel`)
- **Molecules**: `{Formula}.ppmol` (e.g., `H2O.ppmol`, `NaCl.ppmol`, `C6H12O6.ppmol`)

## Using the Repository

### In-Game Browser

Particle Playground has a built-in repository browser:

1. Open the **Tools** menu (wrench icon) and select **Online Repository**
2. Or open the **Pause Menu** (Escape) and click **Repository**
3. Browse the **Elements** or **Molecules** tab
4. Click **Download** to cache a file locally
5. Click **Import** to spawn it in your simulation

### Manual Download

Download files directly from the `elements/` or `molecules/` directories and import them via:
- **Tools > Import Element** (.ppel)
- **Tools > Import Molecule** (.ppmol)

## Contributing

See [Contributing Guide](docs/contributing.md) for details on how to add files.

### Quick Start

**In-Game Upload** (for collaborators):
1. Open Repository dialog
2. Expand "GitHub Token" section and paste your Personal Access Token
3. Expand "Upload to Repository" section
4. Enter the path to your local `.ppel` or `.ppmol` file
5. Click Upload

**Via Pull Request** (for everyone):
1. Fork this repository
2. Add your `.ppel`/`.ppmol` files to the appropriate directory
3. Follow the naming conventions above
4. Open a Pull Request

## Generating Molecules

Use the `ppmol_gen` tool included with Particle Playground:

```bash
# Generate from chemical formula
ppmol_gen gen water.ppmol H2O

# Download from PubChem (Python version)
python3 ppmol_gen.py --pubchem-name caffeine --out caffeine.ppmol

# Inspect a file
ppmol_gen dump molecule.ppmol
```

See [Molecule Tools](docs/molecule-tools.md) for full documentation.

## License

MIT License - see [LICENSE](LICENSE)
