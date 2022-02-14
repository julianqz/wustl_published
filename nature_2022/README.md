# Code associated with Kim & Zhou et al., *Nature*, 2022

These scripts are for reproducing the figures and analyses that were based on NGS data in [Kim & Zhou et al., *Nature*, 2022]().

[`analysis_gex`](./analysis_gex.ipynb) covers gene expression analysis.

[`analysis_bcr`](./analysis_bcr.Rmd) covers BCR repertoire analysis.

*Note: The code here generates the core essence of the figures. For the published versions, finer aesthetic details such as text labels and legends were finalized in Adobe Illustrator by co-author W Kim.*

## Setup

### 1) Directory structure

The scripts assume the following directory structure:

```
.
├── assets
│   ├── gex_b_cells_umap_anno.tsv.gz
│   └── igphyml_output
│       ├── 368-01a@G1772_3.fasta_igphyml_tree_HLP.txt
│       └── etc.
├── c2b2
│   ├── bcr_alluvial.R
│   └── etc.
├── WU368_kim_et_al_nature_2022_gex_all_cells.h5ad
├── WU368_kim_et_al_nature_2022_gex_b_cells.h5ad
└── WU368_kim_et_al_nature_2022_bcr_heavy.tsv.gz
```

### 2) Data

The `WU368_` files contain processed NGS data and can be downloaded from [Zenodo](https://doi.org/10.5281/zenodo.5895181).

`gex_b_cells_umap_anno.tsv.gz` is generated at the end of `analysis_gex`. A copy is provided in [`assets`](./assets) in case any one would like to skip downloading the `h5ad` files or running `analysis_gex`.

The `txt` files in [`igphyml_output`](./assets/igphyml_output) contain tree topology outputs from `IgPhyML` and are used for visualizing phylogenetic trees in `analysis_bcr`.


### 3) Code from `c2b2`

`analysis_bcr` sources code from the [`c2b2` repo](https://github.com/julianqz/c2b2).

Download the `c2b2` repo to the directory from which you plan to run the scripts. 

You can also clone the repo: `git clone https://github.com/julianqz/c2b2.git`

This step can be skipped if only `analysis_gex` is to be run.


### 4) Docker containers

To run `analysis_gex`, use the `cimm` container version `ref_0.1.1_lsf`:

`docker pull julianqz/wu_cimm:ref_0.1.1_lsf`

To run `analysis_bcr`, use the following R container with specific versions of packages installed:

`docker pull julianqz/wu_pub:r_4.1.0`

Of course, you don't have to use these containers. However, reproducibility cannot be guaranteed without using the same versions of the packages/libraries as in the containers.

* `wu_cimm:ref_0.1.1_lsf`: Python 3.8.8, scanpy 1.7.2, anndata 0.7.6, pandas 1.2.3
* `wu_pub:r_4.1.0`: R 4.1.0, ggplot2 3.3.5, circlize 0.4.13, ape 5.6-1, ggtree 3.0.4, vioplot 0.3.6, alakazam 1.1.0

[*More info on the Docker containers*](https://github.com/julianqz/wustl_docker/blob/main/README.md)

## Contact

For questions, feel free to [open an issue](https://github.com/julianqz/wustl_published/issues) on GitHub or drop a line at `jqzhou` at `wustl` dot `edu`.
