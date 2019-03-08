# Surfs-Up


## Background

Climate Analysis and Data Exploration of Climate Database Using Python (Pandas, Matplotlib), SQLAlchemy (ORM Queries) and Flask


## Objectives

### Step 1 - Climate Analysis and Exploration

Use Python and SQLAlchemy to do basic climate analysis and data exploration of your climate database. All of the following analysis should be completed using SQLAlchemy ORM Queries, Pandas, and Matplotlib.

#### Precipitation Analysis

* Design a Query to Retrieve the Last 12 Months of Precipitation Data Selecting Only the `date` and `prcp` Values
* Save the Query Results as a Pandas DataFrame, Set the Index to the Date Column and Sort the Dataframe Values by `date`
* Use Pandas Plotting with Matplotlib to `plot` the Data
* Use Pandas to Calculate the Summary Statistics for the Precipitation Data

#### Station Analysis

* Design a Query to Find the Most Active Stations
    * List the Stations and Counts in Descending Order
    * Which Station Had the Highest Number of Observations?
* Using the Station ID from the Previous Query, Calculate the Lowest Temperature Recorded, Highest Temperature Recorded, and Average Temperature of the Most Active Station
* Choose the Station with the Highest Number of Temperature Observations
    * Design a Query to Retrieve the Last 12 Months of Temperature Observation Data for this Station
    * Plot the Results as a Histogram with `bins=12`

#### Temperature Analysis

* Use the `calc_temps` Function to Calculate the min, avg, and max Temperatures for Your Trip Using the Previous Year's Data for Those Same Dates
* Plot the min, avg, and max Temperatures from the Previous Query as a Bar Chart
    * Use "Trip Average Temperature" as the Title
    * Use the Average Temperature for the y Value
    * Use the Peak-to-Peak (max-min) Value as the y Error Bar (yerr)

#### Rainfall Analysis

* Calculate the Rainfall per Weather Station Using the Previous Year's Matching Dates
    * Sort in Descending Order by Precipitation Amount and List the Station (Name, Latitude, Longitude and Elevation)
* Create a Query That Will Calculate the Daily Normals (i.e. Averages for min, max, and avg for All Historic Data Matching a Specific Month and Day)
* Calculate the Daily Normals
    * Push Each Tuple of Calculations Into a List Called `normals`
    * Set the Start and End Date of the Trip
    * Use the Start and End Date to Create a Range of Dates
    * Strip Off the Year and Save a List of %m-%d Strings
    * Loop Through the List of %m-%d Strings and Calculate the Normals for Each Date
* Load the Previous Query Results (List of Daily Normals) Into a Pandas DataFrame and Add the `trip_dates` Range as the `date` Index
* Use Pandas to Plot the Daily Normals as an Area Plot With `stacked=False`



### Step 2 - Climate App

Design a Flask API based on the queries that have been developed.
* Use FLASK to create the routes

#### Routes
* `/api/v1.0/precipitation`
  * Convert the query results to a Dictionary using `date` as the key and `prcp` as the value
  * Return the JSON representation of the dictionary

* `/api/v1.0/stations`
  * Return a JSON list of stations from the dataset

* `/api/v1.0/tobs`
  * Query for the dates and temperature observations from a year from the last data point
  * Return a JSON list of Temperature Observations (tobs) for the previous year

* `/api/v1.0/<start>` and `/api/v1.0/<start>/<end>`
  * Return a JSON list of the minimum temperature, the average temperature and the max temperature for a given start or start-end range
  * When given the start only, calculate `TMIN`, `TAVG`, and `TMAX` for all dates greater than and equal to the start date
  * When given the start and the end date, calculate the `TMIN`, `TAVG`, and `TMAX` for dates between the start and end date inclusive

