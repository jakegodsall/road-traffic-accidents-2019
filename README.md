# Road Traffic Accidents 2019

## Introduction

The following report is an analysis of traffic accidents in the United Kingdom during 2019, based on the freely available data published by the Department for Transport ADD REF.


## Table of Contents

### Data Sources

Department for Transport (2022). Road Safety Data. [https://data.gov.uk/dataset/cb7ae6f0-4be6-4935-9277-47e5ce24a11f/road-safety-data/.]

Simple Maps (2021). United Kingdom Cities Database. [https://simplemaps.com/data/gb-cities.]

Sunrise (2021). Sunrise and Sunset Longon 2019. [https://www.sunrise-and-sunset.com/en/sun/united-kingdom/london/2019.]

English Premier League Fixtures 2019/20 Fixture and Results [https://fixturedownload.com/results/epl-2019.]

Doogal (2022). UK Football Stadiums. [https://www.doogal.co.uk/FootballStadiums.php.]

### Data Cleaning

Twenty-eight samples from the Road Safety Data was missing its coordinate data. However, the samples did have associated local district information. By use of Beautiful Soup REF, the coordinate data for all towns and cities in the UK were mined from REF and imputed where necessary.

To impute missing time values, the sunrise and sunset times for London during the year 2019 were scraped from REF. According to the light_conditions feature of the sample (darkness/light), the median time between sunrise and sunset or between sunset and sunrise was imputed.

### Exploratory Data Analysis

Clustering analysis based around eight cluster centres shows that the vast majority of accidents occur in densley populated areas, as should be expected.

ADD FIGURE 1

Considering the temporal dimension of the data, it was determined that there exist two primary peaks in accident frequency within the ranges 8:00 am to 10:00 am, and then again from 3:00 pm to 7:00 pm

FIGURE 2 A

Further, it can be seen from figure 2(b) that the frequency of traffic accidents is generally higher during the weekdays, with the maximum on Friday and the minimum on Sunday. This further supports the hypothesis that there is a significant increase in accidents during work-commute periods.

FIGURE 2 B

### Hypothesis Testing

Hypotheses

1. **Is there a significant number of accidents in rural areas caused by or involving drivers who do not live in the vicinity, and which type of vehicles are involved?**


As shown in figure 5, by plotting the geospatial data for the accident occurring in rural areas by people not living there, and comparing it against the accidents in urban locations, it can be seen that a significant number of accidents occurring in rural areas of Wales, the South East, North Yorkshire and Scotland are caused by people who do not live in such areas.
Next, the ratio of accidents in rural areas involving people not living in those areas to the total frequency of accidents, parametrised by vehicle type, were determined (figure 6).

Hence, it was shown that the most significant increase in accidents in rural areas exists for goods vehicles, motorcyclists of 500cc and higher, horse riders and mobility scooter riders. However, after taking the absolute magnitudes of these values into account, motorcyclists of all engine ratings were the highest group at risk.

This could be due to the fact that motorcyclists are more likely to ride in more rural areas for recreation (Department for Transport, 2016), leading to a significant increase in accidents.


2. **Are there more accidents at the same time of day during periods of the year after which the sun has gone down compared to when it is still light?**


The hypothesis to be tested was that the ratio of the average number of accidents per day in darkness would be higher than that in daylight for the same time delta over the entire year. As can be seen in figure 7, the period tested for sunrise was between 7:00 am and 8:00 am, and for sunset between 8:30 pm and 9:30 pm.

FIGURE 7

To simplify the problem, The dates for which there were days of daylight and darkness in the specified time period were not included. Graphically, this means, for example in figure 7(a), that only dates were analysed to the left and right of the outermost red dashed lines, as well as the dates included between the inner lines.
It was found that there was a total of 4938 accidents between 7:00 am and 8:00 am across the year, 2254 of which occurred during 155 days of daylight, and 2684 occurred in 146 days of darkness. This leads to an average number of accidents per day in daylight of 14.54, and 18.38 in darkness. Hence, there is a 26% increase in accidents during darkness during the hours of 7:00 am to 8:00 am.
An equivalent analysis was done for the hours of 8:30 pm to 9:30 pm. A total of 3623 accidents occurred, 1054 of which were during 97 days of day- light, and the remaining 2569 accidents occurred during 204 days of darkness. The average number of accidents per day in daylight for this period is 10.87, compared to 12.59 in darkness. This leads to a 16% increase in accidents during darkness during the hour of 8:30 pm to 9:30 pm.

3. **Are there more accidents in the vicinity of football grounds on days when Premier League football matches take place?**

A test case was first carried out for the football match taking place at Old Trafford on Sunday 24th February 2019. Considering any accident within five kilometres of the stadium as being connected to the event, the accident count was compared against the number of accidents in this region every other Sunday during the year. On the day of the match, the number of accidents was 1.30 standard deviations from the mean. This was taken to be significant and worthy of further investigation.
Taking the Premier League fixtures of 2019 (Fixture, 2021), along with the coordinates of every Premier League club stadium (Doogal, 2022), the previous process was done iteratively for a total of 126 football matches during the year at 15 unique stadiums.

FIGURE 8

When summarised for every match, the z-score appears to be slightly below the average number of accidents. Although there is a significant dif- ference in the number of accidents for different stadiums, on average the analysis implies that there is not a statistically significant rise in the number of accidents on the day of a football match compared to the typical same day of the week in the region.
The table above (figure 9) shows the summary statistics for Premier League football matches. The Accidents 1 column shows the average number of accidents in the area of the stadium on days when there is a match, and the Accidents 2 column shows the average number of accidents on the same day of the week when there is not a match being played.

### Predictive Model
