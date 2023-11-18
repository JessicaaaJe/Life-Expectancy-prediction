# Serengeti Species Count Analysis Using Zero-Inflated Poisson Models

## Abstract
This project examines the influence of environmental factors on the count of three species (Thomson's gazelles, topi, and zebras) in the Serengeti National Park. Utilizing data from Wake Forest University’s long-term research, we explore how variables like vegetation greenness, proximity to rivers, and risk of lion predation affect species counts.

## Introduction
The primary research question focuses on the relationship between various environmental factors and species counts. The study uses Zero Inflated Poisson (ZIP) models to analyze data from camera traps installed across 19 different sites in the Serengeti.

## Data
The dataset comprises 966 observations, each containing 15 key pieces of information, including site ID, date, NDVI (Normalized Difference Vegetation Index), counts of the three species, fire presence, distance to the nearest river, termite mound count, tree count within 50 meters, and lion predation risk.

## Exploratory Data Analysis (EDA)
EDA involved analyzing the distribution of species counts and the relationship between these counts and continuous environmental factors. This analysis revealed the necessity of using ZIP models due to the excess of zero counts in the data.

## Modeling
### Gazelle Thomson Model
The final model for Gazelle Thomson’s count (gazelleThomsonFinal) includes NDVI, distance to the nearest river, lion predation risk, tree count, and fire presence. These variables variously influence the probability of Gazelle Thomson presence and count.

### Topi Model
The final model for topi count (topiFinal) considers distance to the nearest river and log-transformed lion predation risk, impacting the likelihood of topi presence and count.

### Zebra Model
The final model for zebra count (zebraFinal) includes NDVI, distance to the nearest river, lion predation risk, termite mound count, and tree count. These factors contribute differently to the probability of zebra presence and count.

## Discussion
This analysis demonstrates that environmental factors significantly influence the counts of different species in the Serengeti. Interestingly, the same environmental variable can have varying impacts on different species. The study suggests the need for more extensive data collection and the inclusion of additional environmental variables for future research to enhance model accuracy and insights.

