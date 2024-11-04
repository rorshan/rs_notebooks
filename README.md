# Tutorial notebooks in Python for remote sensing

## Getting Started

There are a variety of ways to use these notebooks, but unelss you're using a server with the notebooks pre-loaded, it all starts with:

### Cloning the repo
```
git clone git@forgemia.inra.fr:beyond/remote_sensing_notebooks.git
```

From here, here are the options:

### Local installations

#### Using conda

For this type of install you will need to have [miniconda](https://docs.conda.io/projects/miniconda/en/latest/), [conda](https://docs.conda.io/en/latest/), or [miniforge](https://github.com/conda-forge/miniforge) installed. Please follow the relevant links for installation instructions

```
cd remote_sensing_notebooks
```

Installing the conda environment (replace conda with mamba if applicable). Note that this can take a few minutes to complete.

```
conda env create --name rs_notebooks --file environment_jupyterlab.yml
```
To launch the notebooks after installation:

1. Activate the envionment:
```
conda activate rs_notebooks
```
2. Launch Jupyterlab:

```
jupyter lab
```
3. Click one of the links to open Jupyter Lab in a browser.

As an alternative you can also open the notebooks directly in a program which supports Python notebooks (Visual Studio Code, PyCharm, etc.), but make sure that the right conda environment is selected.

#### Using Docker

The repositroy includes two Dockerfiles to create Docker images. The first image is for a Jupyter Hub client installation. Most users should instead use the Dockerfile for Jupyter Lab.

```
cd remote_sensing_notebooks
```

Building the docker image (this can take a few minutes):

```
sudo docker buildx build --tag rs_notebooks --file Dockerfile_jupyterlab .
```

To launch the enotebooks after installation:

1. Run the docker image
```
sudo docker run -tp 8888:8888 rs_notebooks
```

2. Click one of the links to open Jupyter Lab in a browser.

### Using on a remote server

It is quite possible to import and run these notebooks on a remote Jupyter notebook servers. Two publicly available options are [Google Colab](https://colab.research.google.com/) and [Microsoft Planetary Computer Hub](https://pccompute.westeurope.cloudapp.azure.com/compute/hub/login?next=%2Fcompute%2Fhub%2F). Here are a few key characteristics for each of these services:

#### Google Colab:
- free to use with a Google account
- easy to share notebooks with others
- limited compute power
- can [access Google Drive](https://colab.research.google.com/notebooks/io.ipynb#scrollTo=c2W5A2px3doP) to enable data persistence

#### Microsoft Planetary Computer Hub
-  free to use (at the time of writing) but access must be requested
- easier access to the Microsoft Planetary Computer STAC Catalog which is the dedicated method to access satellite images utilized in these notebooks.
- includes QGis

>**Note:** Some Python packages are not included in the default environment of Google Colab or Planetary Computer Hub. When this is the case, the missing packages will be installed upon executing the notebooks. 

## Notebook list

1. Discovery of Satellite Data Through a STAC Catalog    
    - What is a STAC catalog?
    - Opening GeoJSON files
    - Exploring a STAC catalog and some sattelite metadata
    - Querying  a STAC catalog from a vector file/coordinates
    - Displaying extents and GeoJSON layers on a map
2. Opening a Sentinel-2 Image With rasterio
    - Obtaining an Asset and looking at its properties
    - Getting the relevant part of a satellite image
    - Adjusting the contrast for visuals
    - Color composites
    - Contrast
    - Visualizing and manipulating cloud cover masks
3. Opening a Sentinel-2 image with `Xarray`
    - Creating a data cube from a STAC object
    - Xarray overview
    - Indexing and selecting
    - Plotting data
4. Zonal statistics, spectral signatures and vegetation index
    - Loading vector data and converting to a raster to delimit zones
    - Computing of zonal statistics
    - Spectral signatures
    - Band math and vegetation index
5. Time series (part 1)
    - Building a times series data cube (spatial extent and time period)
    - Operations on the time dimension
6. Time series: visualization
    - Plotting time series images
    - Gap Filling
    - Variations and change in a time series
7. Image classfication with a machine learning algorithm
    - Data pre-processing
    - Classification with machine learning methods
    - Plotting results