# Sagebrush Ecosystem Modeling

This repository explores the accuracy of 1x1m LIDAR Canopy Height Models, 30x30m multispectral, and 30x30m hyperspectral imagery in reconstructing sagebrush ecosystems in the western United States. It will produce workflows that analyze vegetation structure through CHM models and vegetation composition via spectral imagery. The objective of this repository is to determine the percent coverage of sagebrush/shrub and grass/low-growing vegetation coverage as well as the diversity of grass and/or forbs in historically sagebrush territories. Data is sourced from the National Ecological Observatory Network's (NEON) insitu and aerial records, NASA and JPL's Airborne Visible/Infrared Imaging Spectrometer (AVIRIS) images, and the United States Geological Survey's (USGS) LANDSAT images

# Relevance
Sagebrush ecosystems cover much of the western United States and parts of southwestern Canada. Sagebrush ecosystems provide essential forage and habitat for approximately 350 other species of plants an animals, some of which, like the Greater Sage Grouse, are found only in sagebrush habitat. Sagebrush ecosystems are increasingly fragmented through anthropogenic land use, invasive species, and changes in wildfire duration and frequency which are amplified by climate change. While sagebrush still covers much of the western United States, only 10% of current habitats are considered unaffected by fragmentation. Consequently, many plants and animals associated with sagebrush are losing essential habitat and some qualify as endangered or threatened species per the Endangered Species Act. Conservation efforts targeted to sagebrush ecosystems are costly as they require the surveillance and upkeep of millions of acres of public and private land.

This repository offers an alternative to traditional land monitoring strategies through its unique focus on and analyses of sagebrush ecosystems. We expect this code to be useful to other analysts because of its reproducible foundation, which will allow it to be applied to other research areas. While we are using it here to examine sagebrush habitat, the same processes can be run on other sites covered by the aforementioned agencies, allowing versatile analyses of vegetation structure and composition across the United States.

# Workflow Requirements
## Tools and Packages
See the scripts folder for functions written in Jupyter Notebook that are useful to different tasks.  This folder will be updated as the project progresses.  The current functions in this folder are designed to retrieve and analyze NEON *insitu* and canopy height model data.

1) data_grabber.ipynb
This file contains three functions: open_ecosystem_structure (canopy height model data), open_NEON_presence_cover_plant (percent of plant cover data) and open_woody_veg_structure (*insitu* vegetation data).  With a site name and date specified by the user, these functions will retrieve the data specific to your needs from the NEON website using an API call.

2) function_scratchscripts.ipynb
This file contains a scratch pad, exploring the NEON API process and identifying the urls required in the data_grabber.ipynb function.

3) Site_Analysis.ipynb
This file will contain the function necessary to create GeoDataFrames with buffered points derived from the *insitu* vegetation plots (40m diameter), using the site name and coordinate reference system specified by the user.

4) Site_Overlap_Identification.ipynb
This file will contain the function necessary to identify the canopy height model tiles that overlap with 100% overlap of buffered plot points.  Using a list of raster tiles specified by the user (typically determined by site name and date), this function will convert the tiles to polygons and derive their extents.  Then, it will use the intersection function to select only the tiles necessary for further analysis.

See the presentations directory for descriptive output of our research and analyses.  Currently, there is only one blog (in both Jupyter Notebook and HTML format) that details our first steps in this project - comparing the measurements of vegetation found in the canopy height model data with the *insitu* vegetation plot data.

See the environment.yml file for a current list of required packages. The environment can be forked and cloned to activate locally.

## Data Sources and Formats
The data currently required are entirely found on <a href="https://www.neonscience.org/">NEON's website</a> and are retrieved using NEON's API through the code represented in this repository.  The table below represents all data we retrieved to create our blog (found in the 'presentations' folder).

| PRODUCTS                                                               | DATA TYPE    | NEON PAGE             | PURPOSE                         |
|------------------------------------------------------------------------|--------------|-----------------------|---------------------------------|
| NEON Terrestrial Field Site Boundaries - Shapefile                     | polygons     | Spatial Data & Maps   | Site boundary polygon           |
| NEON Terrestrial Observation System sampling locations - Shapefiles v7 | points       | Spatial Data & Maps   | Buffered plot boundary polygons |
| Woody Plant Vegetation Structure                                       | GeoDataFrame | Explore Data Products | *Insitu* data                   |
| Ecosystem Structure                                                    | raster tiles | Explore Data Products | CHM data                        |

These functions we created were designed to run using a variety of sources, but we have yet to test these function outside of NEON products.  We will revisit this possibility later.

## Run Instructions
The current repository is not executable using the functions, but the blog post can be run to see our preliminary results comparing canopy height measurements and *insitu* measurements of vegetation.  The code is demonstrated using NEON's Central Plain Experimental Range (CPER), the Onaqui Mountains site (ONAQ) and the Great Smokey Mountain site (GRSM).  

To run the Jupyter Notebook version of the blog located in the presentations directory, activate the environment.yml.  You will then have all of the packages required to run the code from the first cell to the last.

Alternatively, should you want to merely visualize our approach and results, you can also see our blog in HTML format, also found in the presentations directory.
