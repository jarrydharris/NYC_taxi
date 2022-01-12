# NYC Taxi Data Assessment
 
## Summary
 
This project is an analysis of one months data from the NYC Taxi and Limousine commission in 2013.
 
In the report we looked at the distribution of:
 
- Passengers per trip
- Payment type
- Fare amount
- Tip amount
- Total amount (Fares, tips, taxes and tolls)
- The busiest times and locations
- The most consistent fares and inconsistent trips
 
A number of open questions were also discussed:
 
- When is it appropriate to use the mean as a statistic to analyse the properties of trips
- Can we model fares and tips given pickup and dropoff coordinates, time of day and day of week?
- How can we maximize our earnings in a day?
- How can we minimize our hours worked while retaining average wages?
- If you ran a company with 10 taxis, how would you maximize earnings?
 
To answer the first group of questions exploratory data analysis (EDA) was performed. It was found that the most common number of passengers per trip is 1, with a sharp decline of 2-4 passengers, and a slight bump at 5-6 passengers signifying the use of larger taxis. 60% of customers pay with credit and 40% cash. The distribution of fare, tips and total amounts were heavily right skewed due to a large presence of outliers. The busiest hours of the day were between 6pm and 10pm. The busiest locations were zones within the Manhattan borough, for example Upper East Side South. The trip with the most consistent fares is Hamilton Heights to JFK Airport with a  flat rate of $52.
 
To answer the second set of questions power analysis was performed on the trip data and it was determined that to be 95% confident of the mean $\pm 1$ fare estimate we would need 338 observations of a trip. Linear and random forest models were trained and improved upon predicting the average fare. A mix of interpreting the linear model coefficients, previous EDA, analysing head maps of fares given day and time, and earnings given time spent, it was determined that the biggest factor to earning a maximum for the day is working long hours, you can also increase your rate of earning by taking airport trips at 4am, and spending the busy periods of the day in Manhattan. In order to minimize hours worked but still make the median wage, focusing on trips to and from the Airports is a must to capitalize on the high flat rates. Finally to maximize the earnings between 10 taxis it was recommended a split between low frequency but high fare trips to the airports, and high frequency and moderate fare trips in Manhattan.
 
## Tools used
 
- Python
- Pandas
- Geopandas
- Dask
- BokehJS
- Seaborn
- Scipy
- Jupyter-lab
 
## Challenges, Limitations and Future Ideas

**Memory and Dask**
 
I made the decision to work with the entire dataset provided, which was about 1.4gb after preprocessing. For the more complex computations the amount of memory needed for pandas to handle everything was exceeding 16gb. To handle this I used Dask, which lazily (only when needed) handles the data in partitioned dataframes. This solved the issue of fitting large dataframes into memory.
 
**Jupyter and the Garbage Collector**
 
One of the unexpected issues I ran into was with the way jupyter notebooks create a number of invisible variables that don't get removed by pythons garbage collector. This would lead to filling up my ram after running a cell and outputting plots. If I ran the same cell multiple times (say to tweak a plot), none of the old variables were removed. To fix this I had to make manual calls to the garbage collector within each cell that involved outputting a plot.
 
**Time**
 
My biggest limitation with this project was time, there was a huge amount of data with a lot of potential depths to explore. Some of the things I would like to do in the future include:
 
- Look at the difference between high and low earners who have roughly the same hours worked.
- Look at the distribution of pickups and dropoffs per hour for each day of the week, integrate this with the average fare for that time.
- Look at the tipping differences between large and small sized taxis.
- Perform a deeper analysis of how much money can be made working the airports vs busy zones.
- Interpret the random forest model.
- Include more features in the modeling process.
 
**Dashboard Application**
 
An app which displays historical data for a given day and time might be helpful for taxi drivers trying to plan where they pick up clients next.

