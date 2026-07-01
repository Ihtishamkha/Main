# EDA of EGFR Bioactivity Data

Exploratory data analysis of bioactivity data for the **Epidermal Growth Factor Receptor (EGFR)**, a well-known drug target in cancer research. The dataset combines ChEMBL bioactivity values with Lipinski molecular descriptors to explore relationships between compound physicochemical properties and biological activity (active vs. inactive).

## Overview

This notebook performs EDA on a curated EGFR compound dataset (`EGFR_final.csv`), examining:

- Distribution of compounds across **bioactivity classes** (active / inactive)
- Relationships between **molecular weight (Mw)**, **LogP**, and **pIC50**
- Comparison of **Lipinski descriptors** (Mw, LogP, number of H-bond donors, number of H-bond acceptors) between active and inactive compounds
- Statistical significance testing using the **Mann-Whitney U test**

## Dataset

The input file `EGFR_final.csv` is expected to contain the following columns:

| Column | Description |
|---|---|
| `Bioactivity class` | Compound classification: `active` or `inactive` |
| `Mw` | Molecular weight |
| `LogP` | Octanol-water partition coefficient |
| `NumHDonors` | Number of hydrogen bond donors |
| `NumHAcceptors` | Number of hydrogen bond acceptors |
| `pIC50` | Negative log of IC50 (potency measure) |

> The dataset is derived from bioactivity data retrieved via the [ChEMBL](https://www.ebi.ac.uk/chembl/) database.

## Requirements

```bash
pip install chembl_webresource_client rdkit pandas numpy scikit-learn matplotlib seaborn scipy
```

## Analysis Steps

1. **Load data** — read `EGFR_final.csv` into a pandas DataFrame.
2. **Class distribution** — bar plot of compound counts per bioactivity class.
3. **Chemical space plot** — scatter plot of Mw vs. LogP, colored by bioactivity class and sized by pIC50.
4. **pIC50 comparison** — box plot of pIC50 across active/inactive classes.
5. **Lipinski descriptor comparisons** — box plots and Mann-Whitney U tests for:
   - Molecular weight (Mw)
   - LogP
   - Number of H-bond donors
   - Number of H-bond acceptors
6. **Statistical testing** — a custom `mannwhitney()` function tests whether each descriptor differs significantly between active and inactive compounds.

## Outputs

Running the notebook generates the following plots (saved as PNG files):

- `Bioactivity_class.png`
- `MW_vs_LogP.png`
- `pIC50.png`
- `Mw.png`
- `LogP.png`
- `NumHDonors.png`
- `NumHAcceptors.png`

## Usage

1. Place `EGFR_final.csv` in the working directory (update the file path in the notebook if needed).
2. Open `EDA_of_EGFR.ipynb` in Jupyter Notebook / JupyterLab / Google Colab.
3. Run all cells sequentially.

## Key Insight

The analysis uses the **Mann-Whitney U test** (a non-parametric test) to statistically compare descriptor distributions between active and inactive compound classes, helping identify which physicochemical properties are meaningfully associated with EGFR bioactivity.

## License

Specify your license here (e.g., MIT).
