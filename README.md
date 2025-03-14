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

![bike_daily](https://github.com/mkearns17/Fremont_Bridge_Cyclists_Crossings/blob/main/images/Daily%20Average%20Cyclists%20Across%20Fremont%20Bridge.jpg)

This plot makes sense as it showns higher temperatures during the summer months compared to the winter months.

![temp_daily](https://github.com/mkearns17/Fremont_Bridge_Cyclists_Crossings/blob/main/images/Daily%20Average%20Temperature%20(%C2%B0F)%20in%20Seattle.jpg)

![precip_daily](https://github.com/mkearns17/Fremont_Bridge_Cyclists_Crossings/blob/main/images/Daily%20Average%20Precipitation%20(in)%20in%20Seattle.jpg)

![snow_daily](https://github.com/mkearns17/Fremont_Bridge_Cyclists_Crossings/blob/main/images/Daily%20Average%20Snowfall%20(in)%20in%20Seattle.jpg)

The daily plots confirm the weather patterns of more rain or snow during the winter months and higher temperatures during the summer months. This indicates a possible positive relationship between temperature and the number of cyclists, and a possible negative relationship between precipitation/snow and the number of cyclists.

![scattered_1](https://github.com/mkearns17/Fremont_Bridge_Cyclists_Crossings/blob/main/images/scatter_filtered_0.jpeg)
![scattered_2](https://github.com/mkearns17/Fremont_Bridge_Cyclists_Crossings/blob/main/images/scatter_filtered_1.jpeg)
![scattered_3](https://github.com/mkearns17/Fremont_Bridge_Cyclists_Crossings/blob/main/images/scatter_filtered_2.jpeg)

These scatter plots confirm that there may be a positive linear relationship between number of cyclists and temperature. There may be an argument that there is a negative linear relationship with snowfall and preciption, but these two relationships look much less linear. Outliers are removed from these plots.

# Modeling
## Baseline Model
As a first baseline and simple model, a linear regression model will be used. To evaluate the model and future models, the RMSE value will be calculated on the training and test data. The RMSE value is acceptable to use as the model is trying to predict a continuous value. Using an error value in terms of number of cyclists will make it easier to understand the model's performance as well.

Features are in different units and therefore in very different scales. Scaling the data should improve results. As noted before all features do not appear to be perfectly linear. Using polynomial features should help with this as well.

RMSE on Training Data: 742.04
RMSE on Test Data: 720.42
Cross Validation RMSE: 762.37

Performance is okay with the baseline model but it appears the model is too simple. There appears to be some aspects and features not being captured in this model. Different types of models that can handle more complex and nonlinear data will be tested here. 

An article posted by PubMed Central shows a study on using Machine Learning to predict Traffic Flow. This article has similar intentions to this project, and it shows that Random Forest and XGBoost models were the best performing ML models. Therefore, both types of models will be tested here to see if they have any improvements comapred to the linear regression model. To learn more about this study, follow on this [link](https://pmc.ncbi.nlm.nih.gov/articles/PMC11014399/#sec6-sensors-24-02348).

## Model Type II: Random Forest

After optimizing the parameters of Random Forest Regressor Model using GridsearchCV, the following error scores were calculated:

Train RMSE: 711.93
Test RMSE: 713.97
Val RMSE: 690.03

TThe Random Forest model is performing better than the Linear Regression Model. It is better at picking up the nonlinearity in the data. After using GridsearchCV, the train and test model have very close RMSE values. This shows the model is not overfitting or underfitting too much. The RMSE score on the validation set also shows that the parameters selected are performaing similary and are appropriately chosen. 

Next XGBoost model will be used to see if it can performa any better than the Random Forest Model. 

## Model Type III: XGBoost

Similar to before, the parameters of the XGBoost Regressor model was optimized using GridsearchCV, the following error scores were calculated:

Train RMSE: 705.89
Test RMSE: 701.52
Val RMSE: 690.84

# Final Model

The XGBoost Model above resulted in the best performance and will be chosen as the final model. There was still som improvement compared to the Random Forest model. 

# Conclusions

The XGBoost model had the best performance. The RMSE on the test data shows that the error on predictions is approximately 701 cyclicsts. The validation set RMSE was similar meaning that the parameters of the model are selected well. 

This model can be used by the city of Seattle to have a prediction of number of cyclists across the Fremont Bridge on a give day based on the forecasted weather. Using this information they can be informed to allow for more or less vehicular traffic, or even limit the number of times the bridge is raised to allow for continuous traffic flow.

## Limitations

A major limitation to this model is that weather is not the only factor to the number of cyclists. Holidays, major public events, off school days, races, and many other factors could impact the number of cyclists. As this model does not consider these, the performance will always be limited. 

Another limitation is that weather data used for this model is daily weather recorded near the Sea-Tac International Airport weather station. This is some miles aways away and exact weather numbers could differ at the bridge. As well as the bike data collected is hourly and that hourly data could be more insightful.


## Next Steps

Next steps would be to incorparate additional features into the model and expand upon the amount of weather data provided. 

Using a time series model may be worth exploring here as there is some seasonality factors to the data. 

# Presentation
Presentation slides can be found [here]()

# Repository Structure
├── data
├── images
├── .gitignore
├── README.md
├── presentation.pdf
└── notebook.ipynb