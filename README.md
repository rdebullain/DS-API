# Project 02: Statistical Modelling with Python

## Project/Goals
The goal of this project is to analyze the relationship between the characteristics of Points of Interest (POIs) and the number of bikes available at bike stations using data from APIs like CityBikes, Foursquare, and Yelp. This project also compares the data quality between Foursquare and Yelp and builds a regression model to identify key predictors of bike availability. Additionally, the project explores classification techniques and the use of SQLite databases for efficient data storage and querying.

## Process
### Part 1: Connecting to CityBikes API
1. **Explored API Structure:**
   - Familiarized with the CityBikes API and retrieved bike station data.
2. **Queried CityBikes API:**
   - Retrieved data for bike stations in Izmir, Turkey.
3. **Parsed JSON Data:**
   - Converted JSON data into a Pandas DataFrame for further analysis.

### Part 2: Connecting to Foursquare and Yelp APIs
1. **Connected to Foursquare and Yelp APIs:**
   - Queried both APIs using a 1000m radius around bike stations.
2. **Parsed API Responses:**
   - Extracted relevant POI data (e.g., name, location, rating, price).
   - Addressed discrepancies in rating scales between Foursquare (10-point) and Yelp (5-point), normalizing Foursquare ratings to a 5-point scale.
   - Converted Yelp’s price categories from symbols (`₺`) to numeric values (1-4).
3. **Data Quality Comparison:**
   - Compared Foursquare and Yelp data in terms of completeness, price, and rating distribution.

### Part 3: Data Joining and Cleaning
1. **Joined Data from Part 1 and Part 2:**
   - Joined the bike station data with POI data based on proximity (latitude and longitude).
2. **Validated Data Before and After Join:**
   - Audited row counts, missing values, and data types before and after the join.
3. **Data Cleaning:**
   - Handled missing data by filling in missing POI categories and prices with “Unknown.”
   - Removed duplicate rows and ensured proper formatting of latitude/longitude coordinates.

### Part 4: Exploratory Data Analysis (EDA) and Visualization
1. **Exploratory Data Analysis:**
   - Visualized the distribution of POI ratings and prices by source (Foursquare vs. Yelp).
   - Identified key patterns, such as a higher number of bikes correlating with higher-rated POIs, with some differences between Foursquare and Yelp.
2. **Visualization Enhancements:**
   - Improved the clarity of visualizations by normalizing Foursquare’s rating scale and converting Yelp’s price levels to numeric values.
   - Added scatter plots, histograms, and category distribution visualizations for clearer insights.

### Part 5: Building a Regression Model
1. **Regression Model:**
   - Built an Ordinary Least Squares (OLS) regression model to explore the relationship between POI characteristics and the number of bikes available at nearby bike stations.
2. **Model Interpretation:**
   - The model explains 37% of the variation in the number of bikes.
   - Statistically significant predictors include `poi_latitude` and `poi_longitude`, while `poi_rating` had a significant but negative relationship with the number of bikes.

### Part 6: Classification Model
1. **Classification Model:**
   - Developed a logistic regression model to classify whether a bike station had a high number of bikes (more than 20) based on POI characteristics.
2. **Model Metrics:**
   - Achieved an accuracy score of 0.86, but recall and F1 score indicate room for improvement in predicting true positives.

### Part 7: Storing Data in an SQLite3 Database
1. **SQLite3 Database:**
   - Stored data from all stages in an SQLite3 database for efficient querying and validation.
2. **Database Tables:**
   - `bike_stations`: Contains bike station data.
   - `foursquare_pois`: Contains Foursquare POI data.
   - `yelp_pois`: Contains Yelp POI data.
   - `cleaned_bike_stations_pois`: Contains the final cleaned and joined data.

## Results
### Data Insights
- **Row Count Increase:** The row count increased from 634 (POIs) to 2133 in the joined table due to multiple POIs being associated with individual bike stations.
- **Missing Data Analysis:** 
  - Ratings, price, and address data increased in missing values post-join due to the replication of POIs for multiple bike stations.
  
### Regression Model Summary
- **Model Summary:**
  - The regression model explains 37% of the variation in the number of bikes.
- **Key Predictors:**
  - Statistically significant predictors include `poi_latitude` and `poi_longitude`, while `poi_rating` has a significant but negative relationship.

### Classification Model Summary
- **Model Summary:**
  - The logistic regression model achieved high accuracy (0.86) but lower recall (0.25), indicating a need for further improvements.

## Challenges
1. **API Query Rate Limits:** Rate limits posed challenges in querying large amounts of data from Foursquare and Yelp APIs.
2. **Data Quality Issues:** Significant missing data for price information in the POI datasets, requiring imputation.
3. **Join Operation Complexity:** Accurate joining of bike stations and POIs was challenging due to discrepancies in proximity and geolocation precision.

## Future Goals
1. **Enhancing Data Quality:**
   - Supplement the current dataset with additional sources for more complete POI data.
2. **Advanced Analytical Techniques:**
   - Apply clustering techniques for better categorization of POIs and more accurate predictions.
   - Integrate weather, demographic, and other location-specific data into the analysis.
3. **Model Improvement:**
   - Implement advanced machine learning algorithms, such as random forests or gradient boosting, to improve predictive power.

