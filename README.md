# surfs_up
SQLite, SQLAlchemy, and Flask for weather analysis

# Investing in a Surf and Shake Shop based on Weather Analysis

### Introduction 

Our analysis is for a potential investor of ours, W. Avy, a influencer in the surf sphere. Our weather analysis will determine if the island of Oahu is suitable for our project. We will be looking at data such as temperature and precipitation to determine if it is too cold or wet for possible investors to be interested in our business venture. The project is more to set up the framework of the data analysis and how it is passed on to investors rather than a quantitative result.

### Data Analysis

##### Data

The data given to us by W. Avy comes as an SQLite database. This means as it is a flat file we can work with it locally and it is convenient that everything is stored in one file. The only disadvantage to this is we might have some redundant data, but that's something to look for in the analysis. Everything will be executed in a Jupyter Notebook. We will use Flask to display the results of our code to a local webpage that investors can view to see our results rather than being sent multiple files.

##### Analysis

For our analysis, we are using the Python package SQLalchemy to access the SQLite database we've been given. There are additional dependances in SQLalchemy we also import to create a database later on, e.g., automap, session, create_engine, and func. All of these imports will allow us to query the SQLite database and create our own tables and thus database down the line. One of the keys to the system working is ORM, or object relational mapping. This allows us to detangle coupled data into objects that can be used and accessed and manipulated on their own without interupting the rest of the database. This also allows to easier lines of code used to query this "virtual" database we create rather than complex lines of loops. Overall, so long as we understand what's in the database and the limits of our queries this is an easy and lightweight way to manipulate databases in Python. 

We start accessing the database by using the create_engine and automap_base functions to create a path to the database and reflect it's contents into a structure we can use it in. The class we established with automap_base, Base, is where we reflect the SQLite database to via the path created by the engine. Now rather than being stored in tables, the data is now stored in classes which we access and set to their own variables for faster access. We then pass our engine to the Session, which allows us to fully converse with the SQLite database and query it.

For our analysis we specifically wanted to look at the months of June and December. To that end we create a query that asks the SQLite database for all the dates and temperature obersations, but then to filter to only look for those with a date where the month matches "6" or "12" for June or December respectively. The results of that query are then placed in a Pandas dataframe for the purpose of using the describe function to obtain statistics.


### Results

![June](https://github.com/roeggealissa/surfs_up/blob/bfe2c66151b625f025a9b5a120769430474f6455/June_df_describe.png)
![](https://github.com/roeggealissa/surfs_up/blob/bfe2c66151b625f025a9b5a120769430474f6455/dec_df_describe.png)

First point of note is that there are more measurements in the month of June versus the month of December, which may affect some of the statstics. It might be useful to look at the data and see what stations performed differently between the months. The mean in December is 3.9 degrees lower than the mean in June but a quick t-test shows that the difference in the means is not statistically significant. The maximumum values between the months is also not significantly different. The minimums between the months is the most different with the minimum recorded temperature in December being 8 degrees lower than that of June. On the surface that seems like a result, but a closer look at the data shows that there are only 6 recorded temperatures under 60 degrees, so that minimum only points to a single cold day out of thirty one. 

Taking a step back, it's important to recognize where we're getting the data from. The weather stations we've been given are on the O'ahu island of Hawaii, but we aren't given any description as to where on the island they are. Further research shows that while most of them are on the north or southeast shore of the island, one station is located in Pearl Harbor and two are on moutains. The data from the two mountain stations is useful to understanding the weather of Hawaii as a whole but for our purpose the data was unnecessary. The Pearl Harbor data is fine for our uses, but if we had additional data such as wind, the data from this location would not be as useful since it's protected from the coast.

Additionally querying the database for precipitation for June and December allows us to see the statistics for rainfall for the given stations on the island. The highest rainfall in December was higher than the highest rainfall in June, but beyond that the two datasets aren't statstically different. The data itself actually paints a better picture, showing that there were more measurements of rainfall over 2 inches in December versus days in June. Given that two of the stations are loacted inland however we would have to remove those from the dataset to see if this holds.

To seriously attract investors who are involved in the surf industry however, we need to consider getting station data that includes data about the wind. We would need both wind speed and wind direction to determine if the wind is coming from offshore or onshore, and that it's both producing waves but isn't too fast to safely surf in.
