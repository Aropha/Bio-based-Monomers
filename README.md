# Aropha: Leading the Frontier of Polymer Informatics

Aropha is positioning itself as a leader in polymer informatics by driving innovation in data integration and curation for polymer research and science. We have expertly incorporated the [HELM repository](https://github.com/PistoiaHELM/HELMMonomerSets)—a rigorously curated database of bio-based polymers—alongside Aropha’s own extensive library of commonly used monomer units in bio-based polymer synthesis. This unified resource provides researchers and material scientists with a comprehensive foundation for in-silico polymer design, enabling the exploration and optimization of polymer structures for biodegradation properties. Aropha is empowering a new era of data-driven polymer informatics focused on accelerating sustainable material innovation and enhancing material science discovery.

For a curated list of bio-based monomers, please explore the [Monomers](https://aropha.github.io/Bio-based-Monomers/) page.

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
