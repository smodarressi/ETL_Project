# ETL_Project
Brewery Ratings in California
Collaborated with Camha Nguyen

ETL Homework Technical Doc
Extract:
Data sources came from multiple locations:
Yelp data as json using Yelp API call.
Brewery data locations in California as json using Open Brewery API.
California Cities from https://www.downloadexcelfiles.com/us_en/download-excel-file-list-cities-california-state as csv to get around the Open Brewery API limitations of 20 results total per call

Transform:
Brewery data: Clean up required a reconversion to json since the data from the API call was all in single quotes and in multiple lists. It was first saved as a text file and them converted to json to error handle what was wrong with it. There were multiple no result lists that needed to be removed and random quotations breaking the json format.  Using pandas, the data was converted json to dataframe.
Yelp data: Using the lat, long, and name of brewery from the Open Brewery API, a call was made to get all the Yelp Business ID associated with each brewery. This ID was then recalled to see if the listing matched the ID received. It was then saved as a csv to be accessed later in a pandas data frame and merged with the brewery data. 
Merge Yelp and Brewery data into one dataframes to be loaded to the mysql database

Load:
Merged data loaded into mysql database under table name “brewery_data”
It was used since a lot of the data is relational, and don’t have that many of it
