# MAST30034 Project 2 Real Estate Industry Project README.md


# Calculate distance and duration between properties and train stations code is in Preprocessing.ipynb file.
# Including 10 examples

- Name: Jie Zeng (Lucinda), Hao Guan, Feiyu Lin, Xiaoyang Peng, Jiayao Lu
- Student ID: 980320, 1174227, 1068799, 1021601, 1079059

## Industry Project Overview

### Predicting Rental Prices
This industry project aims to provide students with an opportunity to help predict rental prices for
both residential properties and apartments throughout Australia. The overall goal is for students to
investigate the role of both internal and external variables on rental prices, and recommend where
they are most likely to increase.

The overall aim is to determine the appropriate level of rent an online real estate company should be
listing their properties, as well as which properties are most likely to increase in the next five years.
Students can scrape property and internal attributes (number of bedrooms, land size, car park spots,
etc) from a website of their choosing (e.g. www.domain.com.au).

Students are also expected to find external attributes such as population demographics (affluence and
population growth of an SA2 district) and geospatial attributes (proximity to train stations, closest
schools, parks, etc).

In other words, students should aim to answer the following questions:
1. What are the most important internal and external features in predicting rental prices?
2. What are the top 10 suburbs with the highest predicted growth rate?
3. What are the most liveable and affordable suburbs according to your chosen metrics?

## Timeline:
The timeline for the research area is from Jan to March and Oct to Dec, 2019

 ## Dependencies
 - <img src="https://iconape.com/wp-content/files/zt/11663/png/python.png" width="18" height="18"/> Language: Python 3.8.10
 - <img src="https://iconape.com/wp-content/files/lw/17759/png/cib-anaconda.png" width="18" height="18"/> Environment: Conda 4.13.0
 - <img src="https://iconape.com/wp-content/files/zt/11663/png/python.png" width="18" height="18"/> Python Libraries: 
   1. urllib3
   2. pandas
   3. numpy
   4. matplotlib
   5. seaborn
   6. scipy
   7. sklearn
   8. statsmodels
   9. geopandas
   10. folium
   11. selenium

 ## Directory
 - `data/raw_data`: Contains most raw data files downloaded from the Internet, but part of the raw data are not allowed to access directly and it is too large to upload, so those raw data will not be included in this folder.
 - `data/curated`: Contains all curated / transformed data after preprocessing.
 - `plots`: Contains all visualisation plot from this project.
 - `scripts`: Contains all `.py` scripts, which include helper functions and modules with relevant `__init__.py`
 - `notebook`: Contains notebooks for Downloading, Preprocessing, Visualisation, and Modelling.
    - `download.ipynb` for Download TLC dataset from the Internet.
    - `preprocess-taxi.ipynb` for Cleaning and Preprocessing raw taxi data.
    - `preprocessing-external.ipynb` for Cleaning and Preprocessing raw external data.
    - `analysis.ipynb` for Visualisation and Analysis curated data.
    - `Modelling&Map.ipynb` for Statistical Modelling curated data and generated map figures.


To run the pipeline, please visit the `scripts` directory and run the files in order:
1. `download.ipynb`: This downloads the raw data into the `data/raw` directory.
2. `preprocess-taxi.ipynb`: This notebook details all preprocessing steps for taxi data and outputs it to the `data/curated` directory.
3. `preprocess-external.ipynb`: This notebook details all preprocessing steps for external data and outputs it to the `data/curated` directory.
4. `analysis.ipynb`: This notebook is used to conduct analysis on the curated data.
5. `Modelling&Map.ipynb`: The script is used to run the model for analysing and discussing the model, also generates map figures.



 ## Dataset

 **Download Manually**
 1. Central Park weather data comes from the [National Climatic Data Center](https://www.ncdc.noaa.gov/cdo-web/datasets/GHCND/stations/GHCND:USW00094728/detail)


**Download Automatically**
1. Taxi zone data from [TLC](https://www1.nyc.gov/site/tlc/about/tlc-trip-record-data.page)
2. [TLC Trip Record Data](https://www1.nyc.gov/site/tlc/about/tlc-trip-record-data.page)
3. [Aggregated Data](https://www1.nyc.gov/site/tlc/about/aggregated-reports.page) for New York Taxi
4. The Bike data comes from [NYC Open Data Bicycle Counts](https://data.cityofnewyork.us/Transportation/Bicycle-Counts/uczf-rk3c)
5. [Vehicle, Snowmobile, and Boat Registrations](https://data.ny.gov/Transportation/Vehicle-Snowmobile-and-Boat-Registrations/w4pv-hbkt) in NYC

Actually all the dataset except climatic data are allowed to download automatically. However, due to the limitation of Chinese Internet Firewall, it takes very long time and may has connection error. So, large file I will download manually

**Data Explaination**
- [Taxi Fare](https://www1.nyc.gov/site/tlc/passengers/taxi-fare.page)
- Bicycle Count Status
  - 0 = raw

- National Climatic Data Types
  - SNOW - Snowfall


## References


**Dataset Format**
Author, A. A. (year). Title of data set [Data set]. Publisher Name or Source of Unpublished Data. URL

