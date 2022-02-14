# Code associated with Turner & O'Halloran et al., *Nature*, 2021

The R notebook [`analysis_bcr`](./analysis_bcr.Rmd) is for reproducing the figures and analyses that were based on NGS data in [Turner & O'Halloran et al., *Nature*, 2021](https://doi.org/10.1038/s41586-021-03738-2). The corresponding [html](./analysis_bcr.nb.html) provides a finished look of the notebook *when opened in a web browser*.

*Note: The code here generates the core essence of the figures. For the published versions, finer aesthetic details such as text labels and legends were finalized in Adobe Illustrator by co-author JS Turner.*

## Setup

### 1) Directory structure

The scripts assume the following directory structure:

```
.
├── assets
│   └── mufreq_turner_et_al_nature_2020.tsv.gz        
├── c2b2
│   ├── bcr_alluvial.R
│   └── etc.
└── WU368_turner_et_al_nature_2021_bcr.tsv.gz
```


### 2) Data

The `WU368_` file contains processed NGS data and can be downloaded from [Zenodo](https://doi.org/10.5281/zenodo.5042252).

`mufreq_turner_et_al_nature_2020.tsv.gz` is provided in [`assets`](./assets) and contains somatic hypermutation frequency data from [Turner & Zhou & Han et al., *Nature*, 2020](https://doi.org/10.1038/s41586-020-2711-0).


### 3) Code from `c2b2`

`analysis_bcr` sources code from the [`c2b2` repo](https://github.com/julianqz/c2b2).

Download the `c2b2` repo to the directory from which you plan to run the scripts. 

You can also clone the repo: `git clone https://github.com/julianqz/c2b2.git`


### 4) Docker containers

To run `analysis_bcr`, use the following R container with specific versions of packages installed:

`docker pull julianqz/wu_pub:r_4.1.0`

Of course, you don't have to use the container. However, reproducibility cannot be guaranteed without using the same versions of the packages/libraries as in the containers.

* `wu_pub:r_4.1.0`: R 4.1.0, igraph 1.2.5, vioplot 0.3.6

[*More info on the Docker container*](https://github.com/julianqz/wustl_docker/blob/main/README.md)

## Contact

For questions, feel free to [open an issue](https://github.com/julianqz/wustl_published/issues) on GitHub or drop a line at `jqzhou` at `wustl` dot `edu`.
