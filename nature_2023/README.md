# Code associated with Alsoussi & Malladi et al., *Nature*, 2023

These scripts are for reproducing the figures and analyses that were based on NGS data in [Alsoussi & Malladi et al., *Nature*, 2023](https://doi.org/10.1038/s41586-023-06025-4).

The JupyterLab notebook [`analysis_betaDelta_gex.ipynb`](./analysis_betaDelta_gex.ipynb) with its output [html](./analysis_betaDelta_gex.html) cover gene expression analysis.

The R notebooks [`analysis_betaDelta_bcr.Rmd`](./analysis_betaDelta_bcr.Rmd) and [`analysis_omicron_bcr.Rmd`](./analysis_omicron_bcr.Rmd) with their corresponding output htmls cover BCR repertoire analysis.

*Note: The code here generates the core essence of the figures. For the published versions, finer aesthetic details such as text labels and legends were finalized in Adobe Illustrator by co-author JS Turner.*

## Setup

### 1) Directory structure

The scripts assume the following directory structure:

```
.
├── c2b2
│   ├── bcr_alluvial.R
│   └── etc.
├── WU382_alsoussi_et_al_nature_2023_betaDelta_gex_all_cells.h5ad
├── WU382_alsoussi_et_al_nature_2023_betaDelta_gex_b_cells.h5ad
├── WU382_alsoussi_et_al_nature_2023_betaDelta_gex_b_cell_umap.tsv.gz
├── WU382_alsoussi_et_al_nature_2023_betaDelta_bcr_heavy.tsv.gz
└── WU382_alsoussi_et_al_nature_2023_omicron_bcr_heavy.tsv.gz
```

### 2) Data

The `WU382_` files contain processed NGS data and can be downloaded from [Zenodo](https://doi.org/10.5281/zenodo.7719030).

`gex_b_cell_umap.tsv.gz` is generated at the end of `analysis_betaDelta_gex` for use in conjunction with `analysis_betaDelta_bcr`. A copy is provided on Zenodo in case any one would like to skip downloading the `h5ad` files or running `analysis_betaDelta_gex`.


### 3) Code from `c2b2`

`analysis_betaDelta_bcr` and `analysis_omicron_bcr` source code from the [`c2b2` repo](https://github.com/julianqz/c2b2).

Download the `c2b2` repo to the directory from which you plan to run the scripts. 

You can also clone the repo: `git clone https://github.com/julianqz/c2b2.git`

This step can be skipped if only `analysis_betaDelta_gex` is to be run.


### 4) Docker containers

To run `analysis_betaDelta_gex`, use the `cimm` container version `ref_0.1.1_lsf`:

`docker pull julianqz/wu_cimm:ref_0.1.1_lsf`

To run `analysis_betaDelta_bcr` and `analysis_omicron_bcr`, use the following R container with specific versions of packages installed:

`docker pull julianqz/wu_pub:r_4.1.0`

Of course, you don't have to use these containers. However, reproducibility cannot be guaranteed without using the same versions of the packages/libraries as in the containers.

* `wu_cimm:ref_0.1.1_lsf`: Python 3.8.8, scanpy 1.7.2, anndata 0.7.6, pandas 1.2.3
* `wu_pub:r_4.1.0`: R 4.1.0, ggplot2 3.3.5, circlize 0.4.13, ape 5.6-1, ggtree 3.0.4, vioplot 0.3.6, alakazam 1.1.0

[*More info on the Docker containers*](https://github.com/julianqz/wustl_docker/blob/main/README.md)

## Contact

For questions, feel free to [open an issue](https://github.com/julianqz/wustl_published/issues) on GitHub or drop a line at `jqzhou` at `wustl` dot `edu`.
