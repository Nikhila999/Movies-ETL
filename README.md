# Movies-ETL

## Overview of the Analysis

The purpose of this anaysis is to create an automated pipeline that takes in new data, perform the appropriate transformations and loads the data into existing tables. In this analysis, we are creating a function to load files and perform ETL process and load the cleaned data into Postgress database.


## Resources
Software: PG Admin Version 5.6, Postgress Database, Python 3.7.11, VS Code 1.60 (to write SQL queries and access .csv data files).


## Results

In this analysis we are performing four steps:

1. Extract: Create an ETL Function to load the raw data files into pandas dataframe to perform transformations in python. We are using wiki_movies json file, kaggle and ratings csv files.

2. Clean/Transform Wiki Movies data: This is a crucial step of an ETL process. We wanted to get the data as clean as possible to load into the tables, the analysis we perform and conclusions we draw depends on the data manipulations we perform here.

     - Create a function to merge columns with same/similar data.
        
     - Filter out TV shows data and preserve the movies data.
        
     - Capture IMDB ID from the url and put it in a separate column.
        
     - Remove columns with null values.
        
     - Clean 'box_office', 'budget', 'release_date' and 'running_time' columns using regular expressions.
        
3. Clean/Transform Kaggle and Ratings data: Continue cleaning the remaining datasets.

     - Remove adult movies.
     
     - Convert the data types of columns. 'video' to boolean, budget, popularity and id columns to numeric and set error to raise, so we will know when if there is any data that cannot be converted to numeric and release date to date time.
     
     - Merge the two datasets and remove duplicate columns, reorder and rename columns.
     
     - Transform the ratings dataset by grouping by on movies and ratings and pivot the dataset to give number of ratings by movie after merging it with the joined dataset in previous step.

4. Load: The final step of the ETL process is to load the cleaned dataframes into the database tables. Here we are loading the merged dataset as movies table and ratings table form csv directly into postgress tables.


## Summary

After performing the ETL process we have 6052 records in Movies table.

![](https://github.com/Nikhila999/Movies-ETL/blob/main/Resources/movies_query.png)

