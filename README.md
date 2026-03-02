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

## Repository Contents

### Elements (140+ files)

All 118 elements (most common isotope) plus common isotopes:

| Isotope | File | Notes |
|---------|------|-------|
| Deuterium | `H-2.ppel` | Stable, used in heavy water |
| Tritium | `H-3.ppel` | Radioactive, fusion fuel |
| Helium-3 | `He-3.ppel` | Rare, fusion candidate |
| Carbon-13 | `C-13.ppel` | Stable, NMR applications |
| Carbon-14 | `C-14.ppel` | Radioactive, carbon dating |
| Nitrogen-15 | `N-15.ppel` | Stable isotope tracer |
| Oxygen-18 | `O-18.ppel` | Stable isotope tracer |
| Cobalt-60 | `Co-60.ppel` | Radioactive, medical/industrial |
| Strontium-90 | `Sr-90.ppel` | Radioactive, nuclear fallout |
| Iodine-131 | `I-131.ppel` | Radioactive, thyroid treatment |
| Cesium-137 | `Cs-137.ppel` | Radioactive, nuclear fallout |
| Uranium-235 | `U-235.ppel` | Fissile, reactor fuel |
| Plutonium-239 | `Pu-239.ppel` | Fissile, reactor fuel |
| Thorium-229 | `Th-229.ppel` | Nuclear clock candidate |

### Molecules (200+ files)

Categories include:
- **Simple molecules**: H2O, CO2, NH3, NaCl, etc.
- **Organic compounds**: methanol, ethanol, acetone, benzene, glucose
- **Amino acids**: glycine, alanine, valine, tryptophan, etc.
- **DNA/RNA**: nucleobases, sugars, nucleosides, ATP/ADP/AMP
- **Pharmaceuticals**: aspirin, ibuprofen, acetaminophen, penicillin, amoxicillin, etc.
- **Psychoactive compounds**: caffeine, nicotine, serotonin, dopamine, melatonin
- **Controlled substances**: amphetamine, cocaine, LSD, MDMA, psilocybin, fentanyl, etc.
- **More pharmaceuticals**: fluoxetine (Prozac), sertraline (Zoloft), diazepam (Valium), omeprazole, sildenafil, etc.
- **Hormones**: testosterone, estradiol, epinephrine, norepinephrine
- **Acids & bases**: citric acid, lactic acid, pyridine, aniline
- **Semiconductors**: GaAs, SiC, BN, GaN, ZnO, CdSe, InP, TiO2
- **Superconductors**: MgB2, NbN, Nb3Sn, NbTi, V3Si
- **Fullerenes**: C60 (Buckminsterfullerene), C24, C20
- **Industrial chemicals**: ammonium nitrate, sodium carbonate, copper sulfate, etc.

## Generating Files

Use the tools included with Particle Playground:

```bash
# Generate element
ppel_gen gen H-2.ppel H --neutrons 1

# Generate all 118 elements
ppel_gen gen-all elements/

# Generate molecule from chemical formula
ppmol_gen gen water.ppmol H2O

# Inspect files
ppel_gen dump element.ppel
ppmol_gen dump molecule.ppmol
```

See the main repository [docs/](https://github.com/Night-Traders-Dev/EmergentEvolution/tree/main/docs) for full documentation.

## License

MIT License - see [LICENSE](LICENSE)
