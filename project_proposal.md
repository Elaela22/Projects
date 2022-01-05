# Project proposal
## EDA for a navigation app start-up
### Question/need:
* *What is the framing question of your analysis, or the purpose of the model/system you plan to build?*

After controlling for the volume of traffic going through each transit station, can a relative safety score for each station reliably be determined, given official NYC complaint records?

* *Who benefits from exploring this question or building this model/system?*

My client is a software start-up aiming to help their users safely navigate mass transit systems in major cities. As a first step, they're developing a navigation app for New Yorkers that will incorporate crime data for each station when suggesting possible routes to the user's destination. For example, the app would avoid routing users through the most dangerous stations if there's a reasonable alternative route.

### Data description:
* *What dataset(s) do you plan to use, and how will you obtain the data?*

I plan to use both MTA transit data and NYC's official complaint records ("complaints" being the term for any record logged with NYPD for offenses such as harassment, assault, rape, theft, etc.). Both datasets are publicly available online. I'd like to look at data from at least one full year to ensure I haven't selected unrepresentative periods of time (such as months with major holidays, summer tourism, etc.). I'll collect the data using SQL, converting into Python via SQLAlchemy.

http://web.mta.info/developers/turnstile.html

https://data.cityofnewyork.us/Public-Safety/NYPD-Complaint-Data-Historic/qgea-i56i
Rows - 7.38M
Columns - 35

* *What is an individual sample/unit of analysis in this project? What characteristics/features do you expect to work with?*

The unit of analysis for the complaints dataset is each complaint logged at each station. For the transit data, the unit of analysis is the logged entries and exits for each time increment for each station. Features will include station, traffic volume (as indicated by entries and exits) and possibly boroughs or other indication of broader location.

### Tools:
* *How do you intend to meet the tools requirement of the project?*

I'll use SQL for ingestion, storage, and extraction of the data into Python via SQLAlchemy. I'm comfortable with Python packages such as pandas, matplotlib, and seaborn for cleaning, aggregating, and visualizing the data, though I may explore other options as well. The complaints database seems to be too large to store on my local computer, so I may need to look into data hosting options.

* *Are you planning in advance to need or use additional tools beyond those required?*

No specific plans to do so, but open to using whatever translates my findings best.

### MVP goal:
* *What would a minimum viable product (MVP) look like for this project?*

A minimum viable product would consist of a ranked list of stations by safety score, with an analysis on how that score is impacted by traffic volume. The client can then choose how heavily to weight that safety score in their routing algorithms.
