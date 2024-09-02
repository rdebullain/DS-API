# Project 02: Statistical Modelling with Python

## Project/Goals
The goal of this project is to analyze the relationship between the characteristics of Points of Interest (POIs) and the number of bikes available at bike stations using data from APIs like CityBikes, Foursquare, and Yelp. This project also aims to compare the data quality between Foursquare and Yelp and build a regression model to identify key predictors of bike availability.

## Process
### Part 1: Connecting to CityBikes API
1. **Explored API Structure:**
   - Familiarized with CityBikes API.
2. **Queried CityBikes API:**
   - Retrieved bike station data for Izmir, Turkey.
3. **Parsed JSON Data:**
   - Parsed JSON data into a Pandas DataFrame.

### Part 2: Connecting to Foursquare and Yelp APIs
1. **Connected to Foursquare and Yelp APIs:**
   - Queried both APIs using a 1000m radius around bike stations.
2. **Parsed API Responses:**
   - Parsed the JSON responses into Pandas DataFrames for both APIs.
3. **Data Quality Comparison:**
   - Compared Foursquare and Yelp data in terms of coverage and quality.

### Part 3: Joining Data
1. **Joined Data from Part 1 and Part 2:**
   - Joined bike station data with POI data based on proximity (latitude and longitude).
2. **Validated Data Before and After Join:**
   - Row counts and missing value analysis before and after the join.

### Part 4: Building a Regression Model
1. **Model Building:**
   - Built an OLS regression model to demonstrate the relationship between POI characteristics and the number of bikes at bike stations.
2. **Model Interpretation:**
   - Provided insights based on significant predictors from the model.

### Part 5: Storing Data in an SQLite3 Database
1. **Created SQLite3 Database:**
   - Stored data before and after the join in an SQLite3 database.
2. **Tables Created:**
   - `bike_stations`: Contains bike station data.
   - `foursquare_pois`: Contains Foursquare POI data.
   - `yelp_pois`: Contains Yelp POI data.
   - `cleaned_bike_stations_pois`: Contains the final cleaned and joined data.

## Results
### Row Count Increase
The row count increased from 634 (POIs) to 2133 in the joined table due to multiple POIs per bike station.

### Missing Data Analysis
#### Rating
- **Before Join:** 26 POIs were missing ratings.
- **After Join:** 46 POIs are missing ratings.
- **Reason:** Some bike stations have multiple POIs, leading to more rows with missing ratings.

#### Price
- **Before Join:** 246 POIs were missing price data.
- **After Join:** 746 rows are missing price data.
- **Reason:** The join operation led to the replication of POIs, resulting in more rows with missing price data.

#### Address
- **Before Join:** 27 POIs were missing addresses.
- **After Join:** 65 rows are missing addresses.
- **Reason:** Similar to the above, replication of POIs due to the join operation resulted in more rows with missing addresses.

### Regression Model Summary
**Model Summary:**
The regression model demonstrates the relationship between the characteristics of POIs and the number of bikes at bike stations.

**Key Observations:**
- **poi_rating:** Not a statistically significant predictor.
- **poi_latitude:** Statistically significant predictor.
- **poi_longitude:** Statistically significant predictor.

## Challenges
1. **API Query Rate Limits:** Encountered rate limits while querying APIs.
2. **Data Quality Issues:** Significant missing values, particularly for POI price data.
3. **Join Operation Complexity:** Difficult to accurately join POIs with bike stations due to inconsistent proximity.

## Future Goals
1. **Improve Data Quality:**
   - Find additional data sources to enrich POI data and fill missing values.

2. **Advanced Analysis Techniques:**
   - Implement clustering to categorize POIs and their relationship with bike stations.
   - Explore spatial analysis techniques for more accurate mapping.

3. **Model Enhancement:**
   - Experiment with more advanced machine learning models.
   - Include additional predictors like demographics and weather data.

