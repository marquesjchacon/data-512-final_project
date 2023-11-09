# The Impact of Wildfires Across the United States

## Background

Over the past couple decades, wildfires have become increasingly more common in the western US, destroying large areas of land and displacing many people. In addition to the immediate impacts of fire danger, there has been an increasing problem with chronic smoke inhalation from these fires, with people being forced to adapt to this new reality. There is a large concern about rising cases of emphysema, asthma, and other breathing disorders, as a result of chronic smoke inhalation.

## Goal

The goal for this project is to analyze the impact of wildfires on human populations by considering a case study for analysis. The attached notebook for this repository will detail the insights I have discovered while analyzing this data. Ideally, these ideas could be built upon by others and lead to policy discussions and concrete steps to address the rising smoke epidemic.

## Licenses

According to AirNow, access to their API is available to the public, and the data pulled from it should be used for reporting and forecasting. You can read more about their policies [here](https://docs.airnowapi.org/). In addition, much of the code that I used in my notebook was adapted from Dr. David McDonald. That code is allowed to be reused and shared, under the Creative Commons CC-BY license.

## Relevant Data

The input GeoJSON file I used in the notebook was pulled from [ScienceBase](https://www.sciencebase.gov/catalog/item/61aa537dd34eb622f699df81). Specifically, I downloaded the GeoJSON Files zip folder, then extracted the contents and retrieved the [USGS_Wildland_Fire_Combined_Dataset.json](USGS_Wildland_Fire_Combined_Dataset.json) file. This file is located within the same directory as this repository.

This repository also contains a user module called `wildfire`, which was developed by Dr. David McDonald. This module contains a Reader object that is designed to quickly read through the JSON file, allowing me to extract the data that I need.

I also pulled data from the US EPA Air Quality System API to generate the AQI data in my notebook. The documentation can be found [here](https://docs.airnowapi.org/).

## Special Considerations
My Jupyter notebook version is 6.5.2, and it utilizes Python version 3.9.16. Make sure to check the version that you are running under to make sure that the functions are compatible. Finally, when generating the list of dictionaries by iterating through the JSON file, be wary of the time it takes to generate them. Since we are utilizing over 135000 function calls to calculate geodetic distances, it will take a couple hours to iterate through the whole file.