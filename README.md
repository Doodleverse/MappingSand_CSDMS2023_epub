# MappingSand_CSDMS2023_epub
An EPUB for the 2023 CSDMS meeting. Part of [The Doodleverse](https://github.com/Doodleverse), an
ecosystem of software, data, and trained models for geoscientific image segmentation.


## 🚀 Usage

This notebook carries out the following tasks:

* It downloads a time-series of high-resolution orthomosaic imagery tiles, using Google Earth
Engine (GEE), from a Region-of-Interest (ROI) provided by a geojson format file.

* It uses GDAL to create a seamless orthomosaic of the image tiles, then chops up that or-
thomosaic again into tiles small enough for model application. We make the tiles with 50%
overlap in each direction, so we are able to create pixelwise averages of model outputs.

* It downloads a specified Zoo model for semantic segmentation of this imagery, from a public
archive on Zenodo. The model architecture is provided via HuggingFace, and has been trained
using the Segmentation Gym toolbox.

* It then uses this model to identify sand pixels in tiled imagery.

* It uses GDAL to orthomosaic image labels by mosaicing model outputs.

* Finally, we carry out time-series analysis on outputs from multiple years using xarray.

Play with the model some more on this [demo](https://huggingface.co/spaces/dbuscombe/MappingSand)

### ✍️ Authors

* [@dbuscombe-usgs](https://github.com/dbuscombe-usgs)
* [@2320sharon](https://github.com/2320sharon)
* [@venuswku](https://github.com/venuswku)
* [@ebgoldstein](https://github.com/ebgoldstein)
* [@CameronBodine](https://github.com/CameronBodine)

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

Please use github issues! Emails will not be responded to. Thanks!
