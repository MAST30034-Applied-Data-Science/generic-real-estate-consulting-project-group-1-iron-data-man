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
 - `models`: Should contain all models, but since our group all use jupyter notebook, so this folder is empty.
 - `notebook`: Contains notebooks for Downloading, Preprocessing, Visualisation, and Modelling.
    - `Scrape_Data.ipynb`  scrape all rental property data from [Domain](https://www.domain.com.au/?mode=rent) by postcode.
    - `Download_External.ipynb` download all external data, then rename them and unzip the zip file.
    - `Data_Cleaning_Property.ipynb`  clean useless data and extract floor, postcode and suburb
    - `Data_Cleaning_External.ipynb`  try to merge all external data to property data, find the suburb for each place and unified the suburb name.
    - `Preprocessing.ipynb`  delete the outliers and calculate distances.
    - `Correlation.ipynb`  use linear correlations and feature importance to discover the relations between weekly rent and other features.
    - `Modelling.ipynb` predict the next 5 years rental price, population and income by training different models.
    - `Visualisation.ipynb` draw the plot and calculate growth rate.
    - `Summary.ipynb` overall summary


To run the pipeline, please visit the `notebooks` directory and run the files in order:
1. `Download_External.ipynb`: This downloads all external data into the `data/raw` directory.
2. `Scrape_Data.ipynb`: This scrape property data and save as json file stored in `data/raw` directory.
3. `Data_Cleaning_Property.ipynb`: Here ahs some basic data cleaning and save the result in `data/curated` directory.
4. `Data_Cleaning_External.ipynb`: This try to merge all datasets together and save into the in `data/curated` directory.
5. `Preprocessing.ipynb`: The notebook is to delete outlier and calcautes distances between property and features.
6. `Correlation.ipynb`: The notebook is to exploring the relations between weeekly rent and other features.
7. `Modelling.ipynb`: This is used to run the model for analysing and make the prediction for next 5 years.
8. `Visualisation.ipynb`: This is for calculate the growth rate and draw the plots and all the plots will stored in `plots` directory.


## Dataset

**Data Crawling**
1. Rental Property from [Domain](https://www.domain.com.au/?mode=rent)
2. Suburb from corresponding postcode from [AU Post](https://auspost.com.au/postcode)

**Download Automatically**
1. Sport Recreational Facilities from [VIC Open Data](https://www.data.vic.gov.au/)
2. Cemetery detail from [VIC Open Data](https://www.data.vic.gov.au/)
3. Median Rental Price Quarterly Report by Suburb from [VIC Open Data](https://www.data.vic.gov.au/)
4. Affordable Letting from [VIC Open Data](https://www.data.vic.gov.au/)
5. Median House Price by Time Series from [VIC Open Data](https://www.data.vic.gov.au/)
6. Feature of Interest from [VIC Open Data](https://www.data.vic.gov.au/)
7. Postcode information from [Matthew Proctor](https://www.matthewproctor.com/)
8. Land and Housing Supply Indicator from [Australian Bureau of Statistics](https://www.abs.gov.au/)
9. Regional Population from [Australian Bureau of Statistics](https://www.abs.gov.au/)
10. Personal Income Australia from [Australian Bureau of Statistics](https://www.abs.gov.au/)
11. Victoria Suburb Shapefile from [Australian Open Government Data](https://data.gov.au/)
12. Bus Stop Location from [Public Transport Victoria](https://www.ptv.vic.gov.au/footer/data-and-reporting/datasets/)
13. Tram Stop Location from [Public Transport Victoria](https://www.ptv.vic.gov.au/footer/data-and-reporting/datasets/)
14. Train Station Location from [Public Transport Victoria](https://www.ptv.vic.gov.au/footer/data-and-reporting/datasets/)


**Data Explaination**
- There are multiple geographical dimension
    1. sa2
    2. locality
    3. Suburb
    4. Local Governmant Area
- NOT ALL the external datasets can be merged with property data

## API
**OpenRouteServices**
- For calculate distance and duration by driving 
- Example on [GitHub Address](https://github.com/GIScience/openrouteservice-py/blob/master/examples/basic_example.ipynb)
````
import openrouteservice as ors
import folium

client = ors.Client(key='')
m = folium.Map(location=[52.521861, 13.40744], tiles='cartodbpositron', zoom_start=13)

# Some coordinates in Berlin
coordinates = [[13.42731, 52.51088], [13.384116, 52.533558]]

route = client.directions(
    coordinates=coordinates,
    profile='foot-walking',
    format='geojson',
    options={"avoid_features": ["steps"]},
    validate=False,
)
folium.PolyLine(locations=[list(reversed(coord)) 
                           for coord in 
                           route['features'][0]['geometry']['coordinates']]).add_to(m)
    
m
````

**GoogleMaps**
- For both calculate distance and duration by driving and reverse coordinate to usual address
- Example on [GitHub Address](https://github.com/googlemaps/google-maps-services-python)
````
import googlemaps
from datetime import datetime

gmaps = googlemaps.Client(key='Add Your Key here')

# Geocoding an address
geocode_result = gmaps.geocode('1600 Amphitheatre Parkway, Mountain View, CA')

# Look up an address with reverse geocoding
reverse_geocode_result = gmaps.reverse_geocode((40.714224, -73.961452))

# Request directions via public transit
now = datetime.now()
directions_result = gmaps.directions("Sydney Town Hall",
                                     "Parramatta, NSW",
                                     mode="transit",
                                     departure_time=now)
````

**Geopy**
- For reverse coordinate to usual address
- Example on [GitHub Address](https://github.com/geopy/geopy)
````
from geopy.geocoders import Nominatim

geolocator = Nominatim(user_agent="specify_your_app_name_here")
location = geolocator.reverse("52.509669, 13.376294")
print(location.address)
>>> Potsdamer Platz, Mitte, Berlin, 10117, Deutschland, European Union

print((location.latitude, location.longitude))
>>> (52.5094982, 13.3765983)

print(location.raw)
>>> {'place_id': '654513', 'osm_type': 'node', ...}
````

## Correlation

There are totally 9 algorithms to select top 15 features via linear correlations and features importance.

**Algorithms**
1. Pearson Correlation
2. Mutual Information
3. Chi-Squared
4. Recursive Feature Elimination
5. Embedded Method: Lasso regression
6. Embedded Method: Tree-based RandomForest
7. Lightgbm
8. Embedded Method: Tree-based Extra Trees
9. Embedded Method: Tree-based DecisionTree



## Model

There are 3 main methods.

**Algorithms**
1. Simple Linear Regression - Ordinary Least Square
2. AutoRegression
3. Random Forest Regressor

## References

- Easton, M. G., Saldais, M., Smith, R., Dumovic, V., & Machar, C. (2016). Oxford Big Ideas Humanities 8 Victorian Curriculum. Oxford University Press.

- Hwang, Eunju & Glass, Anne & Gutzmann, Jon & Shin, Kyeng. (2008). The Meaning of a Livable Community for Older Adults in the United States and Korea. Journal of Housing for the Elderly. 22. 216-239. 10.1080/02763890802232055.

**Dataset Format**
Author, A. A. (year). Title of data set [Data set]. Publisher Name or Source of Unpublished Data. URL

