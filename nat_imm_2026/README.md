# Code associated with Matz et al., *Nature Immunology*, 2026

These scripts are for reproducing the figures and analyses that were based on NGS data in [Matz et al., *Nature Immunology*, 2026](TODO: update URL).

The JupyterLab notebook [`analysis_gex.ipynb`](./analysis_gex.ipynb) with its output [html](./analysis_gex.html) cover gene expression analysis.

The R notebook [`analysis_bcr.Rmd`](./analysis_bcr.Rmd) with its corresponding output html cover BCR repertoire analysis.

*Note: The code here generates the core essence of the figures. For the published versions, finer aesthetic details such as text labels and legends were finalized in Adobe Illustrator by co-author HC Matz.*

## Setup

### 1) Directory structure

The scripts assume the following directory structure:

```
.
├── assets
│   ├── WU397_matz_et_al_nat_imm_2026_gex_b_cell_umap.tsv.gz
│   └── igphyml_output
│       ├── 397-06@G17730_1.fasta_igphyml_tree_HLP.txt
│       └── etc.
├── c2b2
│   ├── bcr_alluvial.R
│   └── etc.
├── WU397_matz_et_al_nat_imm_2026_gex_all_cells.h5ad
├── WU397_matz_et_al_nat_imm_2026_gex_b_cells.h5ad
├── WU397_matz_et_al_nat_imm_2026_bcr_heavy.tsv.gz
└── WU397_matz_et_al_nat_imm_2026_bcr_light.tsv.gz
```

### 2) Data

The `WU397_` files contain processed NGS data and can be downloaded from [Zenodo](https://doi.org/10.5281/zenodo.13929847).

`gex_b_cell_umap.tsv.gz` is generated at the end of `analysis_gex` for use in conjunction with `analysis_bcr`. A copy is provided on Zenodo in case any one would like to skip downloading the `h5ad` files or running `analysis_gex`.


### 3) Code from `c2b2`

`analysis_bcr` sources code from the [`c2b2` repo](https://github.com/julianqz/c2b2).

Download the `c2b2` repo to the directory from which you plan to run the scripts. 

You can also clone the repo: `git clone https://github.com/julianqz/c2b2.git`

This step can be skipped if only `analysis_gex` is to be run.


### 4) Docker containers

To run `analysis_gex`, use the `cimm` container version `ref_0.2.2_lsf`:

`docker pull julianqz/wu_cimm:ref_0.2.2_lsf`

To run `analysis_bcr`, use the following R container with specific versions of packages installed:

`docker pull julianqz/wu_pub:r_4.1.0`

Of course, you don't have to use these containers. However, reproducibility cannot be guaranteed without using the same versions of the packages/libraries as in the containers.

* `wu_cimm:ref_0.2.2_lsf`: Python 3.9.7, scanpy 1.8.2, anndata 0.9.1, pandas 1.3.4
* `wu_pub:r_4.1.0`: R 4.1.0, ggplot2 3.3.5, circlize 0.4.13, ape 5.6-1, ggtree 3.0.4, vioplot 0.3.6, alakazam 1.1.0

[*More info on the Docker containers*](https://github.com/julianqz/wustl_docker/blob/main/README.md)

## Contact

For questions, feel free to [open an issue](https://github.com/julianqz/wustl_published/issues) on GitHub or drop a line at `jqzhou` at `wustl` dot `edu`.
