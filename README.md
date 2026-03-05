# Intro
This project sets up a basic UV environment to download and process pollution data
from NASA's portal. To get started you must have UV installed on your system.

# Running the notebook.
You can launch the jupyter lab environment by running:

```shell
uv run jupyter lab
```

from within the project folder. This will launch the server and open up a browser
window that opens up to `http://localhost:8888/`. From there you can navigate to 
the notbooks folder and open the project notebooks.

You can also open jupyter lab and the notbook with a single command using:

```shell
uv run jupyter lab notebooks/EarthDataDownloader.ipynb
```

# Downloading data
## Set up your account
In order to download data from NASA's Earth Data portal, you need to set up an account
at https://urs.earthdata.nasa.gov/.

## Getting your list of URLs
You can download a subset of the [time-averaged 2-dimensional monthly mean data](https://disc.gsfc.nasa.gov/datasets/M2TMNXAER_5.12.4/summary)
by navigating to the link and selecting "Subset / Get Data" on the right navigation.

Set the download method to "Get Original Files" (Default), and select the required 
data range. The output format is fixed (i.e., netCDF). 

Select "Get Data" and wait for NASA to generate the list of links. At the bottom of the
popup window you'll see "Download Links List." This will produce a text file with a list
of links to the requested data. 

**Note:** This will download data for the entire world which can then later be subest. 
Each month is approximately 481 MB, so it would be worth subsetting your data if you
only need a smaller region or specific variables. If this is the case, ensure you
select "Get File Subsets using OPeNDAP" or "Get File Subsets using the GES DISC 
Subsetter." This will allow you to select a more narrow region and choose specific
variables. This will significantly reduce the download sizes, but you will require
a new download if you requirements change. 


## Logging in
You must have an account with user credentials to download data from the NASA Earth 
Observational Data portal.

Once you log in, the script will create .netrc, .urs_cookies, and .dodsrc in your 
user folder, and copy the .dodsrc file to your workingn directory.
