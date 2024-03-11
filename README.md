# Bike Rental Prediction Project
> Predicting bike rental counts based on environmental and seasonal factors.


## Table of Contents
* [Handling Missing Values](#handling-missing-values)
* [Managing Duplicates](#managing-duplicates)
* [Dropping Unnecessary Columns](#dropping-unnecessary-columns)
* [Mapping Feature Numerical Columns to Categorical Columns](#mapping-feature-numerical-columns-to-categorical-columns)
* [Univariate Analysis](#univariate-analysis)
* [Bivariate Analysis](#bivariate-analysis)
* [Feature Scaling](#feature-scaling)
* [Model Development](#model-development)
* [Observations](#observations)

## Handling Missing Values
- Identifying and addressing empty cells, represented as "NaN" in numerical data or blanks in spreadsheets.

## Managing Duplicates
- Detecting and resolving duplicate rows or entries.

## Dropping Unnecessary Columns
- `instant` has only index for the row, `dteday` has date which can be compensated by year and month column,
- `casual` and `registered` seem to be the breakup by category for `cnt` column.

## Mapping Feature Numerical Columns to Categorical Columns
- Convert the numerical values in the 'season' column to categorical string values representing the seasons (e.g., 1 to 'Spring', 2 to 'Summer', etc.).
- Convert the numerical values in the 'weathersit' column to categorical string values representing different weather conditions (e.g., 1 to 'Clear', 2 to 'Cloudy', etc.).
- Define a mapping dictionary to convert numerical representations of months into their corresponding names (e.g., 1 to 'January', 2 to 'February', etc.).
- Define a mapping dictionary to convert numerical representations of days into their respective names (e.g., 0 to 'Monday', 1 to 'Tuesday', etc.).

# Univariate Analysis
## Target Variable
- The target variable exhibits an almost normal distribution.
- The first quartile (Q1) is approximately 3000, while the third quartile (Q3) is around 6000. This yields an interquartile range (IQR) of 3000.
- The median is approximately 4500, indicating that the distribution is centered around this value.

## Numerical Independent Variables (Box Plot)
- The first quartile (Q1) and third quartile (Q3) of the temperature (temp) variable are distributed around 14 and 27, respectively, with a median value of approximately 21.
- Similarly, for the 'feeling' temperature (atemp) variable, the first quartile (Q1) and third quartile (Q3) are distributed around 17 and 31, respectively, with a median value of approximately 24.
- Humidity (hum) and windspeed (windspeed) appear to have outliers in their distributions.

## Numerical Independent Variables (Dist Plot)
- The distribution plots (displot) for temperature (temp) and feeling temperature (atemp) reveal double peaks.
- Humidity (hum) and windspeed (windspeed) exhibit left and right skewness, respectively.

## Categorical Independent Variables (Dist Plot)
- The fall season witnessed a higher influx of bookings.
- Bookings exhibit a distinct trend, peaking during the summer months (June, July, August, and September), followed by a decline from October to December.
- Clear weather conditions coincide with higher booking rates.
- Thursday through Sunday observe a higher number of bookings compared to the earlier days of the week.
- Bookings are relatively lower on non-holiday dates, indicating a preference for spending time at home or with family during holidays.
- In 2019, there was a noticeable uptick in bookings compared to the previous year, reflecting positive growth for the business.

# Bivariate Analysis
## Continuous Independent Variable
- Temperature (temp) and feeling temperature (atemp) exhibit a direct relationship. As temperature increases, the feeling temperature also tends to increase.
- Humidity (hum) and windspeed (windspeed) demonstrate an inversely proportional relationship. Higher humidity levels correlate with lower windspeeds, and vice versa.

## Categorical Independent Variable
- Maximum demand is observed during the fall season, surpassing the demand seen in the spring season.
- August, June, and September experience the highest demand.
- Demand peaks on Fridays, Saturdays, and Sundays.
- Clear days witness higher demand compared to other weather conditions.
- There's a noticeable increase in business from 2018 to 2019.
- Average temperature and feeling temperature tend to be higher during the fall season compared to other seasons, indicating an unusual pattern.
- Winter exhibits lower average temperature and feeling temperature compared to other seasons.
- Humidity levels are highest during the winter season, followed by fall, summer, and spring.
- Windspeed is highest in the spring season, followed by summer.
- Temperature (temp) and feeling temperature (atemp) exhibit the highest mean values when the weather conditions range from clear to partly cloudy, followed by light rain.
- Humidity (hum) shows the highest mean value during light rain, followed by misty conditions and clear skies.
- Windspeed tends to have higher mean values during light rain.
- The overall maximum number of days is observed under the weather condition 'Clear to Partly Cloudy', followed by 'Misty' and 'Cloudy'.
- July has the highest occurrence of 'Clear to Partly Cloudy' days, followed by June and August.
- The maximum number of 'Misty' days is observed in December, followed by January, March, May, and October.

# Feature Scaling
- To address outliers in our dataset, we select Min-Max Scaling. This method scales the features to a range between 0 and 1, which can mitigate the impact of outliers. 
- Each independent column is scaled accordingly.
- Apply Min-Max Scaling to the specified columns in the training and test datasets.

# Model Development
## Automated Selection
- The above result shows the suggestions given by the RFE function to retain 15 features.
- Whenever the boolean returned by rfe.support_ is True, it indicates the feature suggested by RFE to be included in the model.
- Filter the feature selection result to get the features with support and ranking equal to 1.

## Manual Selection
- Variance Influence Factor: To handle multicollinearity, we will consider a threshold of 5 and above.
- Ordinary Least Squares (OLS): We will use the statsmodels library to develop the linear regression model using OLS with a significance level threshold of 0.05.

# Observations
- The above linear regression model demonstrates an R-squared value of 0.827, suggesting that approximately 82.7% of the variance in the dependent variable is explained by the independent variables included in the model.
- The adjusted R-squared value, at 0.823, provides a more precise assessment of the model's goodness of fit, considering the number of predictors present in the model.
- Y test and y test pred values show a strong visual resemblance, indicating that our predictions are evaluated as a healthy fit even in the presence of outliers.
- The R2 score of the test data prediction is 0.77852, indicating that approximately 77.85% of the variance in the target variable is explained by the model.
- The R2 score of the train data prediction is 0.76618, suggesting that approximately 76.62% of the variance in the target variable is explained by the model when trained on the training data.
- The absolute difference between the R2 scores of the test and train data predictions is 0.01234, indicating a slight variance between the model performance on the test and train datasets.
- Positive Impact on Bike Count:
  - The features yr (Year), temp (Temperature), winter, and September have a positive impact on bike count.
- Negative Impact on Bike Count:
  - Conversely, holiday, spring, December, November, Sunday, and Light Snow have a negative impact on bike count.
- Neutral Impact on Bike Count:
  - The windspeed feature does not significantly impact bike count.


## Technologies Used
- Pandas - version 1.2.3
- NumPy - version 1.19.2
- Matplotlib - version 3.3.4
- Seaborn - version 0.11.1
- Scikit-learn - version 0.24.1


<!-- As the libraries versions keep on changing, it is recommended to mention the version of library used in this project -->

## Acknowledgements
Give credit here.
- This project was inspired by...
- References if any...
- This project was based on [this tutorial](https://www.example.com).


## Contact
Created by [@jitesh-rathod] - feel free to contact me!


<!-- Optional -->
<!-- ## License -->
<!-- This project is open source and available under the [... License](). -->

<!-- You don't have to include all sections - just the one's relevant to your project -->