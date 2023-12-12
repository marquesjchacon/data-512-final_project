# The Impact of Wildfires on Idaho Falls, ID

## Background

Over the past couple decades, wildfires have become increasingly more common in the western US, destroying large areas of land and displacing many people. In addition to the immediate impacts of fire danger, there has been an increasing problem with chronic smoke inhalation from these fires, with people being forced to adapt to this new reality. There is a large concern about rising cases of emphysema, asthma, and other breathing disorders, as a result of chronic smoke inhalation. Even moreso, the economic impacts are unknown, and there is concern about how local economies are affected, particularly in tourism.

## Goal

The goal for this project is to analyze the impact of wildfires on human populations by considering a case study on the city of Idaho Falls, Idaho. The attached notebook and report in this repository will detail the insights I have discovered while analyzing this data. More specifically, it will emphasize the urgency to take action, as I predict not only more smoke in the coming years, but worse economic outcomes as well. Ideally, these findings could be built upon by others and lead to policy discussions and concrete steps to address the rising smoke epidemic.

## Licenses

According to AirNow, access to their API is available to the public, and the data pulled from it should be used for reporting and forecasting. You can read more about their policies [here](https://docs.airnowapi.org/). In addition, much of the code that I used in my notebook was adapted from Dr. David McDonald. That code is allowed to be reused and shared, under the Creative Commons CC-BY license.

The Bureau of Transportation Statistics, which holds the data related to airline traffic, has publicly accessible data, but they require researchers to share a license that allows the Department of Transportation to redistribute and share my analysis. Thus, this repository uses an MIT License to authorize others to modify and distribute my work. You can read more about their public access plan [here](https://ntl.bts.gov/ntl/public-access/faqs)

## Relevant Data

The input GeoJSON file I used in the notebook was pulled from [ScienceBase](https://www.sciencebase.gov/catalog/item/61aa537dd34eb622f699df81). Specifically, I downloaded the GeoJSON Files zip folder, then extracted the contents and retrieved the [USGS_Wildland_Fire_Combined_Dataset.json](USGS_Wildland_Fire_Combined_Dataset.json) file. This file is located within the same directory as this repository.

This repository also contains a user module called `wildfire`, which was developed by Dr. David McDonald. This module contains a Reader object that is designed to quickly read through the JSON file, allowing me to extract the data that I need.

I also pulled data from the US EPA Air Quality System API to generate the AQI data in my notebook. The documentation can be found [here](https://docs.airnowapi.org/).

You will also find CSV files in this repository that start with "Detailed_Statistics_Arrivals". These are 11 different CSV files that were pulled from the Department of Transportation Statistics' [page](https://www.transtats.bts.gov/ONTIME/Arrivals.aspx) on arrival delays for individual flights. The reason for the amount of files is due to the the nature of the filter on their webpage. We can select the destination airport (in this case, Idaho Falls Regional) but it forces us to filter by airline, so I had to pull individual data for each airline.

There is also an XLSX file called [Passengers_11_15_2023 8_08_43 PM.xlsx]("Passengers_11_15_2023 8_08_43 PM.xlsx") which houses data on the monthly number of passengers into Idaho Falls since October 2002. This data was pulled from the BTS website as well, and you can find this filter at the following [link](https://www.transtats.bts.gov/Data_Elements.aspx?Qn6n=F). This specific data was created by setting the destination airport to Idaho Falls Regional.

## Models Used

This analysis uses two widely utilized models for time series forecasting — ARIMA and VAR.
- ARIMA assumes that there are no known predictor variables, and that the time series are weakly stationary. More information about assumptions can be found [here](https://stats.stackexchange.com/questions/77374/what-are-the-assumptions-of-arima-box-jenkins-modeling-for-forecasting-time-seri). To incorporate ARIMA in Python, I followed this [tutorial](https://www.machinelearningplus.com/time-series/arima-model-time-series-forecasting-python/) for guidance.
- VAR assumes that the time series variables are correlated with each other. In the context in which I use it, I assume that wildfire smoke is correlated with flight delays, which is correlated with the number of passengers flying into the city, and vice versa. The assumptions as well as tutorials for VAR are found at this [link](https://www.machinelearningplus.com/time-series/vector-autoregression-examples-python/).

## Special Considerations
My Jupyter notebook version is 6.5.2, and it utilizes Python version 3.9.16. Make sure to check the version that you are running under to make sure that the functions are compatible. Finally, when generating the list of dictionaries by iterating through the JSON file, be wary of the time it takes to generate them. Since we are utilizing over 135000 function calls to calculate geodetic distances, it will take a couple hours to iterate through the whole file.