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


## Troubleshooting

Conda is notoriously tricky when it comes to a complex set of dependencies such as here. Installing GDAL and Tensorflow alongside each other with their complex dependencies can easily break things, and it is a constant hassle to come up with conda recipes. You may have to tinker with conda to get it to work on your platform.

### "Transformers library did not load"

You probably have to install `torch` (see [here](https://stackoverflow.com/questions/70622895/transformers-model-from-hugging-face-throws-error-that-specific-classes-couldn-t) ). Try this:

```
pip uninstall transformers
pip uninstall doodleverse-utils
pip install torch torchvision 
pip install transformers
pip install doodleverse-utils
```

## Errors when running `from transformers import TFSegformerForSemanticSegmentation`

```
pip uninstall h5py
conda install -c conda-forge h5py
```

It may also sometimes be necessary to make a prefered kernel:

```
conda install -c conda-forge ipykernel
python -m ipykernel install --user --name csdms
```

Then in jupyterlab, select the kernel named `csdms` to use


## Google Eath Engine Credential errors

Install `gcloud` by installing this: https://cloud.google.com/sdk/docs/install

Then, restart, then install the GEE API and authenticate it (requires a Google login)

```
conda install -c conda-forge earthengine-api
earthengine authenticate
```


## 💭 Feedback and Contributing

Please use github issues! Emails will not be responded to. Thanks!
