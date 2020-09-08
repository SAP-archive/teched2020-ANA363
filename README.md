# ANA363 - Advanced Wrangling and Modeling in SAP Analytics Cloud
## Description


Introduction / Lorem ipsum dolor sit amet, consectetaur adipisicing elit, sed doeiusmod tempor incididunt ut labore et dolore magna aliqua. Utenim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit labore et dolore magna aliqua. Utenim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Nam liber te conscient to factor tum poen legum odioque civiuda

## Overview

Lorem blah blah

## Requirements

To do the following exercises, you will need to use an SAP Analytics Cloud partner or preview tenant with at least 2020.14.  Your preview or partner tenant should already have this.  Customer production/development tenants will need to be on at least 2020.Q3, which will be deployed to customer tenants in August 2020.

It is presumed that you are already familiar with the classic data wrangling experience in SAP Analytics cloud, so some of the steps will me mentioned in abbreviated form.

ECDC Covid-19 worldwide daily summary (used in Exercise 1)

This public dataset is updated daily by the European Centre for Disease Prevention and Control and is available for download at https://www.ecdc.europa.eu/en/publications-data/download-todays-data-geographic-distribution-covid-19-cases-worldwide

It contains daily covid-19 statistics for every country in the world and includes a continent column.  It is available in xlsx and csv formats, along with other formats not directly consumable by SAP Analytics Cloud’s data upload connector (XML and JSON).  We recommend using the xlsx format.  If you elect to use the csv, you will have to manually rename it and add the .csv extension, before uploading it.  

If you don’t want to acquire the latest version yourself, there is a snapshot from July 13, 2020 in the file COVID-19-geographic-disbtribution-worldwide-2020-07-09.xlsx



The New York Times Coronavirus (Covid-19) Data in the United States dataset (used in Exercise 2)

This is the dataset behind the New York Times’s daily statistical charts and is maintained by the NYT data science team.  It specific to the United States, although recent updates are starting to include non-US locations.  The data used by the NYT comes from the Center for Disease Control (CDC) and various state and local agencies.  Both the dataset and extensive documentation are available on GitHub at 
https://github.com/nytimes/covid-19-data

This dataset is interesting, because it is quite granular and for most states goes to the county level.  

If you don’t want to acquire the latest version of the dataset from GitHub, the workshop data contains a snapshot of the file us-counties.csv, dated July 13, 2020.

US National Park Service (NPS) Public Use Statistics (used in Exercise 3)

The NPS has a query builder webpage ( https://irma.nps.gov/STATS/SSRSReports/National%20Reports/Query%20Builder%20for%20Public%20Use%20Statistics%20(1979%20-%20Last%20Calendar%20Year)
 ).  This query builder allows you to explore visitation statistics for any complete year since 1979 for any unit within the NPS system.  The data includes recreational visitors, overnight stays of various types and is granular to the month level.  As the database is very large if you try to include too many parks or park types, you’ll overshoot the query size limits.  If you want to view National Park and National monument data at the same time in the query builder, you’ll need to select the Annual Summary Only option.

If you don’t want to play with the query builder yourself, the file Query Builder for Public Use Statistics (1979 - Last Calendar Year) (2).csv contains visitation data for all US National parks, recreation areas, lakeshores and seashores.


## Exercises

There are three exercises, and each will demonstrate different features of Smart Wrangling.  

Exercise 1: will use a worldwide covid-19 dataset, updated daily by the European Centre for Disease Prevention and Control.  It will be used to demonstrate the following features:
*Wrangling Basics
*Creating Level Hierarchies
*Geo Dimensions at the country level
*
Exercise 2: will use another covid-19 dataset, specific to the United States, which will be used to demonstrate geo dimensions at a far more granular level.  

Exercise 3: will use a dataset containing visitation statistics in the United States National Park system from 1979 to 2019.  It will be used to demonstrate the Wrangling Expression language.  


## How to obtain support

Support for the content in this repository is available during the actual time of the online session for which this content has been designed. Otherwise, you may request support via the [Issues](../../issues) tab..

## License

Copyright (c) 2020 SAP SE or an SAP affiliate company. All rights reserved. This file is licensed under the Apache Software License, version 2.0 except as noted otherwise in the [LICENSE](LICENSE) file.
