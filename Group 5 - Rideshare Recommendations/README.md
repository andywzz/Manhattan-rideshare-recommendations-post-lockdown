# Ride-sharing Neighborhood Recommendations
Using [MTA](http://web.mta.info/developers/turnstile.html) turnstile data, we sought to provide neighborhood recommendations for targeted ride-sharing advertisements in the Manhattan borough.

## Background
A popular ride-sharing company is looking to expand their outreach following the New York City shutdown.

## Project Pipeline

#### Data Acquisition

We used 7 different data sources:

1. [NYC MTA](http://web.mta.info/developers/turnstile.html) turnstile data of March-June 2019 and 2020
2. [2015 Uber Calls](https://github.com/andywzz/uber-tlc-foil-response/tree/master/uber-trip-data)
3. [NYC Subway Station
Coordinates](http://web.mta.info/developers/data/nyct/subway/Stations.csv)
4. [NYC NTA Boundaries](https://data.cityofnewyork.us/City-Government/NTA-map/d3qk-pfyz)
5. [2016 NYC Census](https://data.cityofnewyork.us/City-Government/Demographic-Profiles-of-ACS-5-Year-Estimates-at-th/8cwr-7pqn)
6. [2010 NYC Total Housing Units](https://www1.nyc.gov/site/planning/planning-level/nyc-population/census-2010.page)
7. [Taxi Zone Data](https://data.cityofnewyork.us/Transportation/NYC-Taxi-Zones/d3c5-ddgc)

By combining station locations with neighborhood boundary coordinates, we were able to assign MTA turnstile stations to neighborhoods in New York City. This allowed us to track changes in ridership per neighborhood, as well as quantify the effect of the shutdown on city  transportation.

From this data, we first selected the 5 neighborhoods with greatest MTA ridership loss. We then  validated that those neighborhoods matched the ride-share user demographic and demonstrated the greatest percent increase in ridership during reopening.

Further analysis on housing density distribution and Uber ridership data allowed us to further refine our choices to 2 neighborhoods that represent prime targets.


#### Data Processing
- Identifying anomalies (e.g., negative entries, unlikely entries, etc.)
 * Developed 3 criteria for identification of outliers
 * Used median imputation based on weekly station groupings
- Normalizing station names across data sets with fuzzy string match and handling multiple match cases
- Calculation of housing density from neighborhood coordinates
- Classifying target demographics
- Calculation of percent changes over time

#### Exploration and visualization
All visualizations can be found in the [presentation slides](Presentation/mta_rideshare.pdf) and Jupyter [notebooks](Notebooks/)

## Deliverables

#### Notebooks

[MTA Data Processing & Visualization](Notebooks/MTA_processing_visulization.ipynb)

[Station Matching](Notebooks/Project_1_Grouping_Stations.ipynb)

[Demographic Data](Notebooks/Project_1_Demographic_Data.ipynb)

[Demographic Figures](Notebooks/Project_1_Figures.ipynb)

[Percent Increases and Uber](Notebooks/percent_increase_and_uber.ipynb)


#### Presentation
[MTA Rideshare Presentation](Presentation/mta_rideshare.pdf)

## Team
- [Kaitlin Chaung](https://github.com/kaitlinchaung/)
- [Andrew Wu](https://github.com/andywzz/)
- [Bryan Ross](https://github.com/rossbj92)


## Additional Information

#### Folders
```Notebooks``` - all Jupyter notebooks used for the project.

```Data```

- ```manhattan_station_nta.csv``` - Manhattan station/neighborhood mappings
- ```top_10_nta_changes.csv``` - Manhattan neighborhoods with most percent decrease
- ```borough_nta_polygons.csv``` - columns of interest selected from NYC NTA Boundaries data source
- ```manhattan_daily_stations_2020.csv``` - grouped Manhattan daily station data
- ```taxi-zone-lookup.csv``` - location IDs to be used with Uber data
- ```time_period_top_5.csv``` - used for appendix visualization

```Fonts``` - custom plot fonts.

### Methods Used
* Exploratory Data Analysis
* Data Visualization
* Fuzzy String Matching

### Technologies Used
* Jupyter Notebook
* Python
* Pandas
* Numpy
* Matplotlib
* Fuzzywuzzy
* Shapely
* Tableau


