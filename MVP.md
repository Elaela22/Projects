# MVP
## Navigating mass transit safely

### Purpose
My client is a software start-up creating a brand-new navigation app with female safety in mind. Their first project involves NYC mass transit. They want to know which MTA stations are unusually dangerous for women, so they can include that information in their routing algorithms.

### Definitions
A **complaint** is any complaint made to the police at each MTA station, which are tracked here:
[https://data.cityofnewyork.us/Public-Safety/NYPD-Complaint-Data-Historic/qgea-i56i](https://data.cityofnewyork.us/Public-Safety/NYPD-Complaint-Data-Historic/qgea-i56i)

I'm filtering complaints by the "victim sex" column to look at crimes specifically against women. I'm also filtering by **offense description**, to narrow down offenses to those types that are committed more typically against women:

* HARRASSMENT
* SEX CRIMES
* ASSAULT 3 & RELATED OFFENSES
* OFFENSES AGAINST THE PERSON

**Entries** refers to the number of people entering each subway station over the given time range. This involves summing entries at all turnstiles at a given station, and then summing total entries over the specified time range for each station.

### Date range
I'm looking at data from **March - May 2019**, pre-pandemic.

### Results 
#### Correlating traffic with complaints
The correlation between complaint counts and total entries per station is **0.686580**. It's safe to say as traffic increases, complaint counts increase, but also that other factors play into the frequency of complaints per station. Below is a scatterplot of complaints versus total entries, with a line of best fit plotted to more easily view the average trajectory.

![](https://raw.githubusercontent.com/Elaela22/Projects/main/complaints_MTA.png)

### Recommendations
1. One station in particular should be heavily penalized in the navigation app, because its complaint percentage falls more than two standard deviations from mean:

	BROAD CHANNEL
	
	* Complaints:	24
	* Total entries: 24599.0	
	* Complaints as percentage of entries: 0.097565%

2. Below are the 20 most dangerous stations for women as a bar chart. Each station has a complaint percentage above .005%, well above the mean of .003%. I recommend that when a route goes through any of these stations, a warning is shown to the user. For Broad Channel, the warning should be even more emphatic.

![](https://raw.githubusercontent.com/Elaela22/Projects/main/barh_dangerous_stations.png)

Data as a table:
![](https://raw.githubusercontent.com/Elaela22/Projects/main/total%20results.jpg)
