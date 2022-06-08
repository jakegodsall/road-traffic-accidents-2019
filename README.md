# Road Traffic Accidents 2019

This repository was submitted as an assignment for the Big Data and Data Mining module of the MSc in Artificial Intelligence and Data Science from the University of Hull, 2022.

## Introduction

The following report is an analysis of traffic accidents in the United Kingdom during 2019, based on the freely available data published by the Department for Transport ADD REF.


## Table of Contents

1. [Data Sources](https://github.com/jakegodsall/road-traffic-accidents-2019#data-sources)
2. [Data Cleaning](https://github.com/jakegodsall/road-traffic-accidents-2019#data-cleaning)
3. [Report](https://github.com/jakegodsall/road-traffic-accidents-2019#report)


### Data Sources

Department for Transport (2022). Road Safety Data. [https://data.gov.uk/dataset/cb7ae6f0-4be6-4935-9277-47e5ce24a11f/road-safety-data/.]

Simple Maps (2021). United Kingdom Cities Database. [https://simplemaps.com/data/gb-cities.]

Sunrise (2021). Sunrise and Sunset Longon 2019. [https://www.sunrise-and-sunset.com/en/sun/united-kingdom/london/2019.]

English Premier League Fixtures 2019/20 Fixture and Results [https://fixturedownload.com/results/epl-2019.]

Doogal (2022). UK Football Stadiums. [https://www.doogal.co.uk/FootballStadiums.php.]

### Data Cleaning

Twenty-eight samples from the Road Safety Data was missing its coordinate data. However, the samples did have associated local district information. By use of Beautiful Soup package, the coordinate data for all towns and cities in the UK were mined from the websites above and imputed where necessary.

To impute missing time values, the sunrise and sunset times for London during the year 2019 were scraped from the web. According to the **light_conditions** feature of the sample (darkness/light), the median time between sunrise and sunset or between sunset and sunrise was imputed.

## Report

### Exploratory Data Analysis

An initial exploratory data analysis was performed to determine any fundamental geospatial and temporal patterns in the accident data.

### Hypothesis Testing

Three specific hypotheses were tested:

1. **Is there a significant number of accidents in rural areas caused by or involving drivers who do not live in the vicinity, and which type of vehicles are involved?**

2. **Are there more accidents at the same time of day during periods of the year after which the sun has gone down compared to when it is still light?**

3. **Are there more accidents in the vicinity of football grounds on days when Premier League football matches take place?**

### Predictive Model

A predictive model was developed to be able to predict the severity of an accident given a number of predictors. 

Feature selection was performed by ANOVA and the imbalance in the labels of the data was accounted for by SMOTE oversampling.

A host of methods were deployed and evaluated by cross-validation.

The model was then tested against the official government model.

### Predictions

Finally, a handful of predictions were offered as methods for reducing the most severe accidents found on UK roads during the period.