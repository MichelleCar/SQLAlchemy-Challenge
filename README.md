# Python SQLAlchemy - A Match Made in Heaven!

## Case Study: Surf's Up
![dude_muti](https://user-images.githubusercontent.com/115101031/212117257-641e3f6d-b207-47aa-9c8e-c11b8b8e0005.gif)

### Backgroud
SQLAlchemy is a powerful Object Relational Mapper that gives application developers the tools and flexibility of SQL, providing efficient and high-performing database access, adapted into a simple and Pythonic domain language.

SQLAlchemy provides a “Pythonic” means of interacting with databases, as a kind of universal translator between different dialects of traditional SQL such as MySQL or PostgreSQL.  Developers can leverage the Pythonic framework of SQLAlchemy to streamline their workflow and more efficiently query data.  For example, SQLAlchemy can be used to automatically load tables from a database using reflection, which allows the developer to read the database and build metadata based on that information all written in Python.

In simple terms, You can write a query in the form of a string or chain Python objects for similar queries. Working with objects provides developers flexibility and allows them to build high-performance SQL-based applications. 

In the simplest form, it allows users to connect databases using Python language, run SQL queries using object-based programming, and streamline workflow by working in a single framework.

This functionality extends to the development of web-based applications.  For example, in web applications, you may use a database to store and maintain data that needs to be retrieved and manipulated. You can add data to this database, retrieve it, modify it, or delete it, depending on different requirements and conditions; you can analyze data by creating APIs replete with JSON-built lists/dictionaries. Flask is a straightforward Python web framework that provides useful tools and features for creating web applications in the Python Language. Combined with SQLAlchemy and Python, Flask allows you to build web apps in Python. Flask provides an easy tool for developers because there is little boilerplate code for getting a simple app up and running.

![Python-and-Sqlite-and-SqlAlchemy-Oh-My_Watermarked](https://user-images.githubusercontent.com/115101031/212124991-d526f639-ba43-4dbc-a629-f07b1d85c672.jpg)

Sources:
https://sqlalchemy.org/
https://towardsdatascience.com/sqlalchemy-python-tutorial-79a577141a91
https://www.datacamp.com/tutorial/sqlalchemy-tutorial-examples
https://www.digitalocean.com/community/tutorials/how-to-use-flask-sqlalchemy-to-interact-with-databases-in-a-flask-application


### Case Study Details
Having decided to treat myself to a bucket-list holiday in Hawaii, I don't want to leave anything to chance.  To help with trip planning, I have decided to develop a climate assessment of the area around Honolulu.  This will involve two key approaches:
* Analyzing and exploring the climate data, including precipitation and temperatures across various weather stations across a period of 12 months
* Designing a climate APP to share my results

### Methodology
#### Part 1: Analyze and Explore the Climate Data
I will use Python and SQLAlchemy to do a basic climate analysis and data exploration of my climate database. Specifically, I'll use SQLAlchemy ORM queries, Pandas, and Matplotlib to complete the following steps:
* Use the SQLAlchemy create_engine() function to connect to SQLite database of collected climate data.
* Use the SQLAlchemy automap_base() function to reflect the tables into classes, and then save references to the classes named station and measurement.
* Link Python to the database by creating a SQLAlchemy session.
* Perform precipitation analysis by: finding the most recent date in the dataset, using that date, get the previous 12 months of precipitation data by querying the previous 12 months of data, selecting only the "date" and "prcp" values, loading the query results into a Pandas DataFrame, and setting the index to the "date" column, sorting the DataFrame values by "date", plotting the results by using the DataFrame plot method, and using Pandas to print the summary statistics for the precipitation data.
* Perform station analysis by: designing a query to calculate the total number of stations in the dataset, designing a query to find the most-active stations (that is, the stations that have the most rows) by listing the stations and observation counts in descending order and identifying which station id has the greatest number of observations, designing a query that calculates the lowest, highest, and average temperatures that filters on the most-active station id found in the previous query, and finally, designing a query to get the previous 12 months of temperature observation (TOBS) data by filtering by the station that has the greatest number of observations, querying the previous 12 months of TOBS data for that station, and plotting the results as a histogram .

#### Part 2: Design Your Climate App
Now that the initial analysis is complete, I’ll design a Flask API based on the queries that were developed. To do so, I will use Flask to create the routes as follows:
* A homepage.
* List all the available routes, including:
1) /api/v1.0/precipitation - this API converts the query results from the precipitation analysis for the last 12 months of data to a dictionary (in JSON format) using "date" as the key and "prcp" as the value.
2) /api/v1.0/stations - this returns a JSON list of stations from the dataset.
3) /api/v1.0/tobs - this returns a JSON list of temperature observations for the previous year of the most-active station for the previous year of data.
4) /api/v1.0/<start> and /api/v1.0/<start>/<end> - returns a JSON list of the minimum temperature, the average temperature, and the maximum temperature for a specified start or start-end range.
  
### Observations

#### Precipitation Analysis
Analyzing total precipitation over a period of 12 months showed that, on average, Honolulu experiences a consistent level of precipitation, with the average precipitation being 0.18 inches, and standard deviation results showing that 68% of precipitation fell within 0.5 inches from the mean (in either direction).  Only during two dates within the 12-month period of observations did the precipitation exceed 6 inches.
  
![precipitation](https://user-images.githubusercontent.com/115101031/212152161-18928220-d4d1-4932-bec2-320617000376.jpg)
![stats](https://user-images.githubusercontent.com/115101031/212155246-f17e3ef3-2ce6-4186-8c93-26c8add93817.jpg)
  
#### Station Analysis
After finding the most active station (Station# USC00519281, with 2772 collected values), and therefore relying on the largest data set we could locate.  The results indicated that regardless of the timing of our planned trip, at most points in the year, the temperatures in Honolulu held steady in the 70's (farenheit), and peaked at about 75-76 degrees farenheit.  This offered us a lot of flexibility in planning our trip if we hope for nice weather.
    
![temperature](https://user-images.githubusercontent.com/115101031/212157724-314bc7a2-3cae-44e1-915e-5847dea19fbf.jpg)

#### Climate API
Having the opportunity to venture into some basic web development by compiling the data analysis into JSON dictionaries is a great way to share the results of the analysis.
