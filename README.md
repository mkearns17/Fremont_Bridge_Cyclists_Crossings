# Fremont Bridge Cyclists Crossings
by Michael Kearns

![bike symbol](https://www.seattle.gov/images/Departments/SDOT/BikeProgram/cycletrack2.jpg)

# Business Understanding
Seattle is home to many cyclists who ride for both recreational or commuting purposes. Seattle has already developed extensive infrastructure that include designated walking paths and protected bike lines. Unique to Seattle geography is that North Seattle and Downtown are split by bodies of water that connect the Puget Sound to Lake Washington. This requires riders who travel from North Seattle to Downtown to cross a bridge that motor vehicles also use. I would like to build a model that can predict the number of cyclists that cross a bridge dependent on the daily weather. This project will specifically look at the Fremont Bridge, which has direct access to the South Lake Union and Downtown areas that host many major companies and business districts. The goal is this model could be used by the Seattle Department of Transportation to help improve or provide safer travel for cyclists across this bridge.

# Data Understanding
Data for this project will be collected from multiple sources. First, the city of Seattle tracks the number of cyclists that cross the Fremont bridge in both the northbound and southbound directions. To review the source in more depth, please follow this [link](https://data.seattle.gov/Transportation/Fremont-Bridge-Bicycle-Counter/65db-xm6k/about_data). Second, historical weather data from the National Center for Environmental Information (NCEI) is collected that includes daily temperature, precipitation levels, and snow levels. To review the datasource in more depth, please follow this [link](https://www.ncei.noaa.gov/access). The data will range between 2013-2024.

## Data Preparation
A key difference between the two datasets is the cyclist dataset has hourly recordings and the weather data is recorded daily.  Therefore, the cycling dataset will need to be converted to report daily numbers. All data considered will be numerical, and will have to be cleaned for possible cases of missing data or incorrectly recorded values.

# Exploratory Data Analysis

![bike_hist](https://github.com/mkearns17/Fremont_Bridge_Cyclists_Crossings/blob/main/images/bike_hist.jpg)

The histogram plot above shows that the frequency of cyclists is somewhat uniformly distributed.

# Modeling

# Final Model

# Conclusion
## Limitations
## Recommendations
## Next Steps
