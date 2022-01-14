# Written Description

## Abstract
Mass transit is an efficient way to get around big cities, but navigating it can be dangerous, especially for women. In this project I analyzed the relative safety of each subway station in NYC, considering traffic, victim sex, and type of crime reported. For September through November 2019, I found that the number of complaints at each station correlates at a rate of 73% with subway traffic as measured by daily entries, and that a subset of stations are unusually dangerous in a statistically significant way. Furthermore, at most stations, the proportion of sex-related crimes against women varies directly with the proportion of crimes generally.

## Components
### Design

My client is a software start-up aiming to help female users safely navigate mass transit systems in major cities. As a first step, they're developing a navigation app for New Yorkers that will incorporate crime data for each station when suggesting possible routes to the user's destination. For example, the app would avoid routing women through the most dangerous stations if there's a reasonable alternative route.

After controlling for the volume of traffic going through each transit station, I assessed the safety of each station both generally and for women specifically, given official NYC complaint records.

### Data
I'm using 3 months of data (September through November 2019) from the following datasets:

* [MTA turnstiles data](http://web.mta.info/developers/turnstile.html)
* [NYPD complaints data](https://data.cityofnewyork.us/Public-Safety/NYPD-Complaint-Data-Historic/qgea-i56i)

I also found a [statistic from the MTA](https://new.mta.info/document/28971) on female ridership (52% of riders are women).

### Algorithms
* Data preview and loading via SQL and SQLalchemy
* Cleaning data, including standardization of station names using dictionaries and mapping, correcting incorrectly entered dates, diffing cumulative entry totals for true daily entry data, dropping rows with null values for required columns
* Aggregation of two data sets using pd.merge() on station name
* Calculation of complaint numbers involving sex-related crimes against women vs. all complaints using offense description column and victim sex column
* Visualizations, including bar plots, horizontal bar plots, scatterplots, line of best fit, and boxplot
* Outlier detection and analysis using boxplot, standard deviation

### Tools
* Extracted, transformed, and loaded the raw MTA data into a SQL database
* Queried from that database into Python via SQLAlchemy with some exploratory analysis including GROUP BY, WHERE, HAVING, AND / BETWEEN, and a subquery
* Exploratory data analysis in pandas; loaded complaints dataset using pandas
* Python visualization via matplotlib and Plotly libraries

### Communication
* 5 minute slide presentation to client (software startup making navigation app for women to safely use mass transit)
*   Recommendations:
*     Score potential routes by averaging safety score across included stations
*     All else being equal, default to routes with safer stations
*     Display warning to users for "very dangerous" stations
