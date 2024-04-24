# Extracting images to be annotated from Puhti

## A very short introduction to Puhti and CSC

### Background

[Puhti](https://docs.csc.fi/computing/systems-puhti/) is a supercomputer hosted by [CSC](https://www.csc.fi/en/) - the Finnish IT Center for Science. Puhti, as well as most other resources and services provided by CSC, are free to use for research purposes. In order to use the resources, a research group needs to create a project. Each project is given a specific amount of billing units. Using the CSC resources consumes these billing units and thus they are essentially a way to regulate the amount of resources a specific CSC project can use. The DRYTREE project has two CSC projects:

`Project number 2008436` - A project for managing data related to the DRYTREE project

`Project number 2004205` - A project for running computations related to the DRYTREE project

### The Puhti filesystem

There are three main disk areas in Puhti:

`home` - The home directory of a specific Puhti user. This is the default directory you end up in when you log into Puhti. Only you have access to this directory.

`projappl` - A project-specific directory for storing code related to the project. The directory can be accessed by all project members.

`scratch` - A project-specific directory for storing project-related data that is constantly used. The directory can be accessed by all project members and is supposed to be only used as a short-term data storage. CSC has other services, such as [Allas](https://docs.csc.fi/data/Allas/) for long-term data storage.

## Extracting US aerial imagery from Puhti

### General information

The directory `/scratch/project_2004205/USA` in Puhti contains US aerial images to be annotated. Currently, the directory contains imagery from the states of Washington and Oregon. The imagery was extracted from the [Box storage](https://nrcs.app.box.com/v/naip/) maintained by the [National Agriculture Imagery Program](https://naip-usdaonline.hub.arcgis.com/). Some preprocessing steps were applied to convert the original images to GeoTIFF format and split the images into smaller tiles. The height and width of each tile in pixels is $\frac{3000}{res} - \mod(\frac{3000}{res},32)$, where $res$ is the pixel resolution in meters. In other words, the tile heights and widths are as close as possible to 3000 meters ensuring that the tile heights and widths in pixels are divisible by 32 (divisibility by 32 is required by the machine learning model that detects dead trees). Depending on the year, the resolution of the images is either 1 or 0.6 meters.

### Directory and file structure

The directory structure has the following logic:

1. The directory `/scratch/project_2004205/USA` contains several subdirectories, each containing aerial imagery from a specific year.
2. Each year-specific directory contains subdirectories containing aerial imagery from a specific state (*wa* for Washington and *or* for Oregon). Depending on data availability, some years only include imagery for one of these two states and others include imagery for both states.
3. Each state-specific directory contains subdirectories for a specific imagery type (*c* for infrared images and *n* for RGB images). Only RGB imagery is available for years between 2006 and 2017, whereas both RGB and infrared imagery is available starting from year 2018.
4. Each imagery type-specific directory contains the actual images for a specific year, state, and imagery type. For example, the directory `/scratch/project_2004205/USA/2023/wa/c` contains the infrared images for the state of Washington acquired in 2023. Each imagery type-specific directory should contain exactly 100 images. These images are a random subset of all image tiles available for a specific year, state, and imagery type.

The names of the image files follow a specific structure as well. As an example, the filename `wa065_2023_c_06_25.tif` can be decoded as follows:

- `wa` is the abbreviation of the state within which the image is located
- `065` is the [code of the county](https://www.nrcs.usda.gov/wps/portal/nrcs/detail/national/home/?cid=nrcs143_013697) within which the image is located.
- `2023` is the image acquisition year.
- `c` is the imagery type (infrared in this case).
- `06` and `25` represent the position (row and column) in the original untiled image from which the specific tile was extracted. Each original untiled image in the [Box storage](https://nrcs.app.box.com/v/naip/) covers a whole county.

**NOTE!** The original untiled images cover whole counties. Some of these images exceed the county boundaries and the values of the pixels exceeding the boundaries have been set to zero. As a result, some image tiles might be partly or even fully black.

**NOTE!** The images located under the subdirectories of `/scratch/project_2004205/USA` are a **random** subset of all images from the states of Washington and Oregon. Hence, you can expect many of the images to contain little to no forest.

### Downloading the images

Follow these steps to download the images:

1. [Connect to Puhti using a graphical file transfer program](https://docs.csc.fi/data/moving/graphical_transfer/), such as FileZilla or WinSCP.
2. Navigate to the directory `/scratch/project_2004205/USA` or any of its subdirectories depending on whether you want to extract the whole dataset or a specific subset. The size of the whole dataset is 59 GB.
3. Download the files to your own computer.





