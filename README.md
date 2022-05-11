### Exploratory Data Analysis of NYC MTA Transit Traffic and How Weather Impacts Trends
#### Abstract
An exploration into NYC’s MTA turnstile data, merged with NOAA daily weather data, revealed that the transit stations reporting highest traffic, which occur in Manhattan, do not change significantly with the weather. This exploration was conducted on behalf of a mobile food vender with an interest in targeting the areas proximal to the busiest NYC transit stations. The vender’s business model changes the marketed product depending on the weather. Another key exploration was changes in transit traffic on weekends compared to weekdays, and holidays compared to non-holidays.

#### Design

NYCider Merchant, a mobile food vender, sells cider icees in mild to hot weather (60-100F), sells hot cider in cool to very cold weather (<40F), and does not operate when weather is between 40-60F. They wanted to understand whether or not to change locations depending on the weather, as well is if they should reduce inventory for certain kinds of weather (at this level, reduced subway traffic is used as a proxy for reduced sales potential). Likewise, my client was interested in understanding how transit traffic changes on weekends vs week days.  
The exploration focused on these questions:

**Which stations experience the highest traffic on hot, mild, cool, and cold days?**

**Does transit traffic change significantly on weekends vs weekdays?**

**What stations record the highest traffic at end-of-year holiday times, and on the 4th of July?**

#### Data

The data used for this project included MTA turnstile data from 2019, 2020, and 2021. This was obtained from NYC’s MTA turnstile data website. The project also incorporated historical weather data for the same window of time (2019-2021), obtained from NOAA’s past weather by zip code database. The zip code used was 10019 for a weather station located in Central Park. This data exploration assumed temperature and weather patterns do not vary drastically across the NYC transit area. 

#### Algorithms

Key code utilized in the execution of this project included code to clean the MTA data, filter and sum the traffic data, merge the transit data with weather data, normalize the data, and visualize trends.

- **Cleaning the data** involved replacing negative counting turnstile records with positive values, and anomalously high counts with max possible counts in a day. Both of these data cleaning steps have the potential to introduce bias; however, without these steps, the data are less reliable. Removing the unreliable data from the dataset was an option, however, almost 28% of the data was faulty and removing such a large fraction of the data would result in greater bias than approximating and imputing data in a conservative manner.  

- **Filtering and summing data** involved converting date data to a date/time format, creating unique identifiers for each station, calculating the new traffic at each turnstile and summing all entry and exit data recorded at each station on each day.  

- **Merging MTA data** with NOAA weather data was conducted using an inner join on DATE for both datasets. The max temperature was used to classify the weather days into “hot” (80-100F) (no days reported a max temp greater than 100F), “nice” (60-80F), “cool” (40-60F), “cold” (20-40F), and “very cold” (<20F). These classifications labels are subjective (one person's "nice" weather day might be another person's "hot" weather day) and are based on the comfort range of the individual data scientist creating the model.  

- **Normalizing the data** relied on the equation (x - xminimum)/(range of x), where x is the recorded traffic per day at a given station, xminimum is the smallest recorded total new traffic for a station within a weather day classification, and range of x is the xmaximum minus the previously described xminimum. This normalization equation was applied to the data to account for the difference in the number days with different kinds of weather. The resulting normalized data can be plotted on the same axes as data from other weather days to give more robust results.

- **Visualizing data** was conducted using matplotlib, primarily, and was instrumental in arriving at recommendations delivered to the client. 

#### Tools

This exploratory data analysis used DB Browser for SQLite for the initial procurement of the MTA data. After obtaining the data, Jupyter notebook, python, pandas, numpy, matplotlib, and seaborn were used to conduct the data exploration described above.

#### Communication

Please see accompanying presentation slides and code for additional information regarding this project. 

