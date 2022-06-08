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

A statistical model was developed to predict the conditions under which acci- dents are most likely to occur in, as well as the severity of injuries sustained.

The purpose of developing such a model is to be able to predict when an accident will occur, to aid in providing recommendations.

The author assumes that the subset of all data samples that do not con- tain a single unknown value in the initial predictors of interest is sufficient for training the model. After doing so there were 98,654 samples, 33.38% of the original merged data sets. A second assumption made was that the nominal, ordinal and binary categorical predictors could all be treated equivalently during the feature selection process.

To choose the most suitable features on which to train the model, all the features that seemed to be of value were joined into a single data set. Categorical features were evaluated according to an ANOVA hypothesis test (Sthle and Wold, 1989).

FIGURE 10

on these methods. The scores can be visualised in figure 10.
The data was heavily imbalanced on accident severity, on the order of 50:10:1 for slight, serious and fatal injuries respectively. In order to accommo- date for this imbalance, an auxiliary data set was produced by oversampling the minority class by using the Synthetic Minority Oversampling (SMOTE) technique (Chawla et al., 2002). This provided a balanced set on which the
model could be trained.
A host of classification models were evaluated by cross-validation on a
repeated stratified k-fold of the samples.
Decision tree-based models were by far the most accurate models em-
ployed, with the greatest accuracy coming from a random forest model.

FIGURE 11


As can be seen in figure 11, a stacked model achieved 92.62% accuracy during the cross-validation process.
However, it should be noted that when the model was later trained on the original dataset, the accuracy regressed to 84.2%.
In addition to the STATS19 data sets, the Department for Transport provided model probabilities at the record-level for the accidents with the binary classes of being a serious or slight injury (Transport, 2019).
The government model was based on a binary logistic regression and trained on many of the same features employed in the training of the random forest model referenced in this report.
To compare the models, a previously unseen validation set of approx- imately 22,000 samples were passed to the trained random forest model. Using the accident index as a foreign key, the probabilities for those same samples were extracted from the government model.
A mean-squared error function was then employed to determine the dis- tance between the predicted values of the random forest model and the gov- ernment model.
For both the serious and slight accident predictions, the mean-squared error result was under 15%, giving a significant level of confidence in the predictive capabilities of the random forest model developed.

### Predictions

The author makes the following recommendations based on the analysis delivered.
• To increase awareness of the dangers of traffic accidents for cyclists, targeting both the cyclist and the driver.
• To increase awareness of the dangers of high-speed motorcycle use in rural areas.
• To consider better lighting conditions during the early hours of the morning and late at night depending on the time of year.
• To further investigate the reasons why there is a relative increase in accidents involving taxis during the early hours of the morning. This could suggest that overworking and tiredness are playing a key role.