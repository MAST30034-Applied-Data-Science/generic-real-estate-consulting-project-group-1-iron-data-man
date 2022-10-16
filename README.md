# MAST30034 Project 2 Real Estate Industry Project README.md
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
4. Any Business Recommdations?


 ## Dependencies
 - <img src="https://iconape.com/wp-content/files/zt/11663/png/python.png" width="18" height="18"/> Language: Python 3.8.10
 - <img src="https://iconape.com/wp-content/files/lw/17759/png/cib-anaconda.png" width="18" height="18"/> Environment: Conda 4.13.0
 - <img src="https://iconape.com/wp-content/files/zt/11663/png/python.png" width="18" height="18"/> Python Libraries: 
   1. re
   2. os
   3. bs4
   4. json
   5. time
   6. scipy
   7. numpy
   8. geopy
   9. folium
   10. pandas
   11. sklearn
   12. IPython
   13. seaborn
   14. tushare
   15. zipfile
   16. difflib
   17. urllib3
   18. requests
   19. selenium
   20. datetime
   21. warnings
   22. lightgbm
   23. geopandas
   24. haversine
   25. googlemaps
   26. matplotlib
   27. statsmodels
   28. collections
   29. openrouteservice
   30. webdriver_manager


 ## Directory
 - `data/raw_data`: Contains all raw data files downloaded from the Internet and scrape from domain website.
 - `data/curated`: Contains all curated / transformed data after preprocessing.
 - `plots`: Contains all visualisation plot from this project.
 - `scripts`: Contains all `.py` scripts, which include helper functions and modules with relevant `__init__.py`
 - `notebook`: Contains notebooks for Downloading, Preprocessing, Visualisation, and Modelling.
    - `scrape_data.ipynb`  scrape all rental property data from [Domain](https://www.domain.com.au/?mode=rent) by postcode.
    - `Download_external.ipynb` download all external data, then rename them and unzip the zip file.
    - `data_cleaning_property.ipynb`  clean useless data and extract floor, postcode and suburb
    - `data_cleaning_external.ipynb`  try to merge all external data to property data, find the suburb for each place and unified the suburb name.
    - `Preprocessing.ipynb`  delete the outliers and calculate distances.
    - `Correlation.ipynb`  use linear correlations and feature importance to discover the relations between weekly rent and other features.
    - `Modelling.ipynb` predict the next 5 years rental price, population and income by training different models.
    - `Visualisation.ipynb` draw the plot and calculate growth rate.


To run the pipeline, please visit the `scripts` directory and run the files in order:
1. `scrape_data.ipynb`: This scrape property data and save as json file stored in `data/raw` directory.
2. `Download_external.ipynb`: This downloads all external data into the `data/raw` directory.
3. `data_cleaning_property.ipynb`: Here ahs some basic data cleaning and save the result in `data/curated` directory.
4. `data_cleaning_external.ipynb`: This try to merge all datasets together and save into the in `data/curated` directory.
5. `Preprocessing.ipynb`: The notebook is to delete outlier and calcautes distances between property and features.
6. `Correlation.ipynb`: The notebook is to exploring the relations between weeekly rent and other features.
7. `Modelling.ipynb`: This is used to run the model for analysing and make the prediction for next 5 years.
8. `Visualisation.ipynb`: This is for calculate the growth rate and draw the plots and all the plots will stored in `plots` directory.



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

- Easton, M. G., Saldais, M., Smith, R., Dumovic, V., & Machar, C. (2016). Oxford Big Ideas Humanities 8 Victorian Curriculum. Oxford University Press.

- Hwang, Eunju & Glass, Anne & Gutzmann, Jon & Shin, Kyeng. (2008). The Meaning of a Livable Community for Older Adults in the United States and Korea.
Journal of Housing for the Elderly. 22. 216-239. 10.1080/02763890802232055.

**Dataset Format**
Author, A. A. (year). Title of data set [Data set]. Publisher Name or Source of Unpublished Data. URL

