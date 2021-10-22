# surfs_up
SQLite, SQLAlchemy, and Flask for weather analysis

# Investing in a Surf and Shake Shop based on Weather Analysis

### Introduction 

Our analysis is for a potential investor of ours, W. Avy, a influencer in the surf sphere. Our weather analysis will determine if the island of Oahu is suitable for our project. We will be looking at data such as temperature and percipitation to determine if it is too cold or wet for possible investors to be interested in our business venture. The project is more to set up the framework of the data analysis and how it is passed on to investors rather than a quantitative result.

### Data Analysis

##### Data

The data given to us by W. Avy comes as an SQLite database. This means as it is a flat file we can work with it locally and it is convenient that everything is stored in one file. The only disadvantage to this is we might have some redundant data, but that's something to look for in the analysis. Everything will be executed in a Jupyter Notebook. We will use Flask to display the results of our code to a local webpage that investors can view to see our results rather than being sent multiple files.

##### Analysis


### Results

![June](https://github.com/roeggealissa/surfs_up/blob/bfe2c66151b625f025a9b5a120769430474f6455/June_df_describe.png)
![](https://github.com/roeggealissa/surfs_up/blob/bfe2c66151b625f025a9b5a120769430474f6455/dec_df_describe.png)

First point of note is that there are more measurements in the month of June versus the month of December, which may affect some of the statstics. It might be useful to look at the data and see what stations performed differently between the months. The mean in December is 3.9 degrees lower than the mean in June but a quick t-test shows that the difference in the means is not statistically significant. The maximumum values between the months is also not significantly different. The minimums between the months is the most different with the minimum recorded temperature in December being 8 degrees lower than that of June. On the surface that seems like a result, but a closer look at the data shows that there are only 6 recorded temperatures under 60 degrees, so that minimum only points to a single cold day out of third one. 

Taking a step back, it's important to recognize where we're getting the data from. The weather stations we've been given are on the Oahu island of Hawaii, but we aren't given any description as to where on the island they are. Further research shows that while most of them are on the north or southeast shore of the island, one station is located in Pearl Harbor and two are on moutains. The data from the two mountain stations is useful to understanding the weather of Hawaii as a whole but for our purpose the data was unnecessary. The Pearl Harbor data is fine for our uses, but if we had additional data such as wind, the data would not be as useful.

Additionally querying the database for precipitation for June and December allows us to see the statistics for rainfall for the given stations on the island. The highest rainfall in December was higher than the highest rainfall in June, but beyond that the two datasets aren't statstically different. The data itself actually paints a better picture, showing that there were more measurements of rainfall over 2 inches in December versus days in June. Given that two of the stations are loacted inland however we would have to remove those from the dataset to see if this holds.

To seriously attract investors who are involved in the surf industry however, we need to consider getting station data that includes data about the wind. We would need both wind speed and wind direction to determine if the wind is coming from offshore or onshore, and that it's both producing waves but isn't too fast to safely surf in.
