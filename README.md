# Aropha: Leading the Frontier of Polymer Informatics

Aropha is establishing itself as a leader in polymer informatics by advancing methodologies for data integration and curation in polymer research and science. As part of this effort, we have incorporated the [HELM repository](https://github.com/PistoiaHELM/HELMMonomerSets)—a rigorously curated dataset of bio-based monomers—with Aropha’s proprietary library of monomer units commonly employed in both bio-based and synthetic polymer synthesis. This consolidated and standardized resource provides a robust foundation for *in-silico* polymer design to facilitate the systematic exploration and optimization of polymer architectures with respect to biodegradability and other critical performance metrics. Through this initiative, Aropha is aiming to provide a new paradigm in data-driven polymer informatics to accelerate the development of sustainable materials and driving innovation at the intersection of computational chemistry, materials science, and environmental sustainability.

For a curated list of bio-based and synthetic monomers, please explore the [Monomers](https://aropha.github.io/Bio-based-Monomers/) page.

---

## PolyKnit Package for In-Silico Polymer Structure Synthesis

Our proprietary **PolyKnit** package is used to create in-silico structures of polymers for a deep computational analysis. This package requires SMILES strings with wildcard asterisks to represent the reactive sites on the monomer building blocks.

If you have the BigSMILES of your polymer structure, you can convert it into SMILES with wildcards using this simple script below.

```python
# Read BigSMILES from a text file
txtBigSMILES = '.../common_monomers.txt'

with open(txtBigSMILES, 'r') as f:
    content = f.read()

lines = content.split('\n')

# Convert BigSMILES into a dictionary mapping cleaned monomer names to SMILES strings with wildcards
bigsmiles_dict = {}
for i in range(3, len(lines)):
    monomer_name = lines[i]
    if monomer_name and monomer_name.startswith('[#'):
        # Remove the '[#' prefix and trailing ']' from the monomer name
        key = monomer_name.replace('[#', '').replace(']', '')
        # Assume the corresponding SMILES string is on the next line; remove spaces and encapsulate with wildcard asterisks
        smiles_str = lines[i + 1].replace(' ', '')
        bigsmiles_dict[key] = f'*{smiles_str}*'

# The dictionary 'bigsmiles_dict' now holds the mapping from monomer names to formatted SMILES strings.
