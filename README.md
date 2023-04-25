# MappingSand_CSDMS2023_epub
An EPUB for the 2023 CSDMS meeting. Part of [The Doodleverse](https://github.com/Doodleverse)

## 🚀 Usage

### ✍️ Authors

* [@dbuscombe-usgs](https://github.com/dbuscombe-usgs)
* [@2320sharon](https://github.com/2320sharon)
* [@venuswku](https://github.com/venuswku)
* [@ebgoldstein](https://github.com/ebgoldstein)

## ⬇️ Installation

If you are running this notebook locally, we advise creating a new conda environment to run the program. We recommend [miniconda](https://docs.conda.io/en/latest/miniconda.html)

1. Clone the repo:

```
git clone --depth 1 https://github.com/Doodleverse/MappingSand_CSDMS2023_epub.git
```

(`--depth 1` means "give me only the present code, not the whole history of git commits" - this saves disk space, and time)

2. Create a conda environment called `csdms`


Install the conda env:

[OPTIONAL] First you may want to do some conda and pip housekeeping (recommended)

```
conda update -n base conda
conda clean --all
pip install --upgrade pip
```

[OPTIONAL] Set mamba to the default installer:

```
conda install -n base conda-libmamba-solver
conda config --set solver libmamba
```

Install: 

`conda env create --file env.yml`

Activate the conda env: 

`conda activate csdms`

3. Launch the notebook using: 

`jupyter lab MappingSand_epub.ipynb`


## 💭 Feedback and Contributing