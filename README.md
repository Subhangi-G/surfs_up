# surfs_up

## Overview of Project 

### Purpose
The purpose of this analysis is to generate summary statistics from the temperature data for the months of June and December, in Oahu. Obtaining information about the temperature trends in summer, and in winter will help determine if the surf and shake shop can be sustainable year-round in Oahu.

### Resources used
- Data Source : hawaii.sqlite
- Software : Python 3.7.9, Jupyter Notebook 6.1.4, Pandas 1.1.3, Numpy 1.17.0, Anaconda 1.7.2, 


## Results
### Tables showing the summary statistics for the temperatures in a summer month (June), and a winter month (December).

Month of June:
(fig)

Month of December:
(fig)

## Analysis
At first glance, we observe from the summary statistics that the average temperatures in both June and December are very similar.\
However there are key differences too. These are highlighted by looking at the graphs plotted for the temperature data for June and December in Oahu. These graphs were analysis done beyond what the challenge instructions asked for, to understand the data better.
 
1. Comparison of the Box-and-Whisker plots for June and December (refer to Fig. below):
We observe that the median temperature of June is higher than the interquartile range in December.\
The interquartile range in December is slighly bigger than in June, and the number of outliers towards the lower temperatures is higher in December.\
This implies that June may have higher temperatures for a longer period compared to December.

2. Comparing histogram plots of temperature distribution for June and December:\
We observe that in December (Fig. below), the graph is symmetric around the peak of 72-73F. However we notice a sharp decline in number of counts as we move away from the peak, to almost half the value, and another sharp decline below 67F, and above 77F.\
Most of the data is aggregated around the peak, which would also explain the greater number of outliers below the first quartile in the box and whisker plot.
<Fig for december>
In comparison, the temperature distribution in June (Fig. below) is also approximately bell shaped, with a peak around 76, and it gradually falls away on either side.\  
Making the assumptions that temperatures are recorded at the same time every day throughout the year, this might imply that in December temperature changes occur much faster.\  
Note however that number of counts in June (1700) is higher than the number of counts (1517) in December. More accurate conclusions can be drawn by knowning how the measurements were recorded in December and in June.

3. A quick query to obtain the count for temperatures above 70F in December returned 1036. (An example of the code is below.)
```
dec_count = session.query(func.count(Measurement.tobs).filter(extract('month', Measurement.date) == '12').filter(Measurement.tobs >= 70.0)).all()
print(dec_count)
```
The same query for June returns 1611.\ 
Making the assumption that the same number of measurments are taken everyday, the above numbers would imply that around 28 days in June record 70F or above, whereas 21 days in December recorded 70F or above. This implies that the whole month of June will experience ideal surfing temperatures as compared to just three weeks in December.

## Summary 

As commented above, better conclusions can be drawn if the details of the recordings were known like if temperatures were recorded evenly across the day, if night-time temperatures are also reported, if the manner of taking measurements is the same in June and December.\
Purely from a temperature standpoint however, it appears that December has around three weeks of warm weather, and a surf and shake shop will flourish in the same manner as it would in June if the store manages it's inventory to serve enthusiastic surfers, taking into account the finer details about the changes in the weather.\
For example, stocking appropriate wet-suits, and other accesories like boots, gloves, and hood, and offering warm drinks like hot chocolate along with icecreams and shakes.

The following queries will help in better understanding or fine tuning the weather details in June and December.
1. A query returning temperatures in the months of June and December from stations grouped by the altitude of their location.\
For surfers to experience comfortable surfing conditions, temperatures at sea-level is required to be warmer, preferably over 70F. Lower temperatures at higher altitudes is not a contributing factor and can be eliminated.

2. A query returning precipitation scores in the month of June, and December.\
Knowing the occurrence of rainy days, despite warm weather will help in deciding if a surf store will bring in revenue. Afterall W. Avy's intial investment was "rained out of existence"!
