
# Seattle – A Story of Growth
## Building Permits Data Analysis
  

For my final project for DATA 512: Human Centered Data Science, I performed a quantitative data analysis to analyze the growth of Seattle in recent years using the Buildings Permit dataset. I visualized the trends in new permits for single-family/duplex homes as compared to multifamily/apartment homes over the last two decades. I have also created an informative choropleth of Seattle indicating the fastest growing neighboprhoods in recent years by using the total number of new permits applied in last six years.

All the code, analysis and graphs for this analysis can be found in the [DATA512_Final_Project.ipynb](DATA512_Final_Project.ipynb) notebook.
  
### Reproducibility
  
This analysis is intended to be completely reproducible by following the best practices for performing and sharing open research. By following the notebook and instructions below, it is possible for anyone to reproduce this analysis.

For complete reproducibility, clone the repository from github alongwith the data files.
git clone https://github.com/priyankam22/DATA-512-Human-Centered-Data-Science/tree/master/data512-final-project
 
### Data Sources
  
The below two data sources were used for this analysis. The corresponding downloaded files are located under the data folder of this repository for complete reproducibility.
  
**1) Building Permits Data:** 

File name: **data/Building_Permits.csv**
  
The main dataset used for this analysis is the Building Permits data made publicly available by the City of Seattle on their [website](https://data.seattle.gov/Permitting/Building-Permits/76t5-zqzr). The dataset has around 120K rows and 24 columns. The dataset is updated on a daily basis and can be accessed via the [Socrate API](https://dev.socrata.com/foundry/data.seattle.gov/k44w-2dcq). It can also be directly downloaded as a csv from the same API website under the Download & Export section.  
  
For more information about the API and dataset, refer : https://dev.socrata.com/foundry/data.seattle.gov/k44w-2dcq  
  
The column descriptions are listed below:  
  
|Column Name|Description|Type|  
|---|---|---|  
|PermitNum|The tracking number used to refer to this permit in SDCI's tracking system.|Plain Text|  
|PermitClass|	The permit class tells you the type of project.|Plain Text
|PermitClassMapped|	A description of whether the permit is for a residential or non-residential project.|	Plain Text
|PermitTypeMapped|	The type of permit that we have issued or that is in progress.|	Plain Text
|PermitTypeDesc|	Additional information about the type of permit. For example, whether it is an addition/alternation or a new project.	|Plain Text
|Description|	A brief description of the work that will be done under this permit. This description is subject to change before SDCI issues the permit. The description is generally more stable if we have issued the permit. Very long descriptions have been truncated.	|Plain Text
|HousingUnits|	The number of housing units included at the beginning of the project.	|Number
|HousingUnitsRemoved|	The number of housing units removed during the project.	|Number
|HousingUnitsAdded|	The number of housing units added during the project.	|Number
|EstProjectCost|	The estimated project cost of the work being proposed is based on fair market value (parts plus labor). The estimated cost (if any) represents the best available information to date, and is subject to change if the project is modified. We do not collect the estimated project cost for all permit types.	|Number
|AppliedDate|	The date SDCI accepted the application as a complete submittal.	|Plain Text
|IssuedDate|	The date SDCI issued the permit. If there is an Application Date but no Issue Date, this generally means the application is still under review.	|Plain Text
|ExpiresDate|	The date the application is due to expire. Generally, this is the date by which work is supposed to be completed (barring renewals or further extensions). If there is not an Expiration Date, this generally means the permit has not been issued.	|Plain Text
|CompletedDate|	The date the permit had all its inspections completed. If there is an Issue Date but not a Completed Date, this generally means the permit is still under inspection.	|Plain Text
|StatusCurrent|	The current status in the application/review/inspection life cycle. This status shows the most recent process step that was fully completed.	|Plain Text
|OriginalAddress1|	The street name and number of the project.	|Plain Text
|OriginalCity|	The city for the project's address.	|Plain Text
|OriginalState|	The state for the project's address.|	Plain Text
|OriginalZip|	The Zip code for the project's address.	|Plain Text
|ContractorCompanyName|	The contractor(s) associated with this permit.	|Plain Text
|Link|	A link to view full details and current status information about this permit at SDCI's website.	|Plain Text
|Latitude|	Latitude of the worksite where permit activity occurs. May be missing for a small number of permits considered "unaddressable."	|Number
|Longitude|	Longitude of the worksite where permit activity occurs. May be missing for a small number of permits considered "unaddressable."	|Number

**2) Seattle Neighborhoods:**  

File name: **Neighborhoods.shp**

This is the Neighborhoods shape file under the `data\Neighborhoods\WGS84` folder. This dataset is used to get the neighborhood names for the building permits. It contains geospatial delineation of neighborhood boundaries used by the City Clerks Office. It is publicly available on the Seattle Government website [here](https://data.seattle.gov/dataset/Neighborhoods/2mbt-aqqx) and can be downloaded directly as a zip file. 
Note that we need all  the other files under the WGS84 folder as well in order to read the shape file as the shape file has dependencies on these files. WGS84 is a standard for representing geospatial data. If you download the Neighborhoods dataset from the website, you will notice another folder 'StatePlane' which can be ignored for this analysis.
  
There are 119 rows and 13 columns. Each row corresponds to a neighborhood in Seattle.
  
The file has below column names:
'OBJECTID', 'AREA', 'PERIMETER', 'HOODS_', 'HOODS_ID', 'S_HOOD','L_HOOD', 'L_HOODID', 'SYMBOL', 'SYMBOL2', 'SHAPE_AREA', 'SHAPE_LEN',
'geometry'.
  
The relevant columns are :
  
|Column Name|Description|Type|  
|---|---|---| 
|L_HOOD|Region in Seattle|Plain Text|
|S_HOOD|Sub-Region in Seattle|Plain text|
|geometry|Boundary coordinates of Polygon Shape|Plain text|
     
### Data Limitations
  
The data is about building permits which were submitted to the Seattle Department of Construction (SDCI) for approvals. There is no information about whether the project was completed or not. There might be cases where the permit was issued but the project was scrapped due to some reason. Since I did not find a publicly available dataset having information about completed projects, for the sake of simplicity I will make an assumption that most of the proposed projects with an issued permit were completed.  
  
Any results from this analysis need to be interpreted by taking the above assumptions and limitations into account.  
  
### License:

**1) Building Permits Data:** The data is owned by Seattle Department of Construction (SDCI)

**2) Neighborhoods Data:** The data is provided by Seattle Public Utilities and owned by the Seattle City GIS Program.

Both the datasets above are made available to the public under the Public Domain License which allows free use by anyone for any purpose without restriction under copyright law.

The City of Seattle Government requires the users of this data to include the following disclaimers:

"The data made available here has been modified for use from its original source, which is the City of Seattle. Neither the City of Seattle nor the Office of the Chief Technology Officer (OCTO) makes any claims as to the completeness, timeliness, accuracy or content of any data contained in this application; makes any representation of any kind, including, but not limited to, warranty of the accuracy or fitness for a particular use; nor are any such warranties to be implied or inferred with respect to the information or data furnished herein. The data is subject to change as modifications and updates are complete. It is understood that the information contained in the web feed is being used at one's own risk." 
  
  
### Findings

![](https://github.com/priyankam22/DATA-512-Human-Centered-Data-Science/blob/master/data512-final-project/images/permits_by_year.png)
  
![](https://github.com/priyankam22/DATA-512-Human-Centered-Data-Science/blob/master/data512-final-project/images/permits_by_class.png)  
As seen above, there has been a steady increase in new building permits for multifamily homes till 2016 and a slight decrease for single family homes till 2016. A shapr rise is seen in 2017 in both these permit types in 2017. Since the year used in this analysis is the year in which the permit was applied, we can make a reasonable assumption that this increase in permits in 2017 will translate or might have translated into an increase in ongoing construction projects. This gives us a very clear picture of the growth of Seattle in recent years.
  
![](https://github.com/priyankam22/DATA-512-Human-Centered-Data-Science/blob/master/data512-final-project/images/choropleth.png)  
By looking at the number of new completed building permits, we can estimate that the fastest growing neighborhoods in recent years are the Adams in Old Ballard, Greenwood and Fremont in North Seattle. In South Seattle, Columbia City and other neighboring regions in Rainier Valley are seeing significant number of new permits, indicating newly developed neighborhoods. The significantly higher number of building permits in these areas can be a clear indication of where people are moving to or buying/building new houses.
  
The above findings are based on a messy dataset with multiple shortcomings. Specifically the dates column had missing values which might have led to skipping some valid permits. There is no way of knowing if any other permits are missing from the original dataset due to reasons unknown. More information about the data collection and representation should be obtained from the data owner in order to validate these findings. This work can be expanded if data about completed construction projects can be made available. Future work can include augmenting this dataset with data about schools, parks, traffic to understand and address the main issues with urban planning.

#### References:  
  
<sup>1</sup>https://www.seattletimes.com/seattle-news/data/114000-more-people-seattle-now-this-decades-fastest-growing-big-city-in-all-of-united-states/  
http://www.seattle.gov/sdci  
https://data.seattle.gov/Permitting/Building-Permits/76t5-zqzr  
https://dev.socrata.com/foundry/data.seattle.gov/k44w-2dcq  
https://gis.stackexchange.com/questions/244677/performing-spatial-join-match-points-from-dataframe-to-polygons-using-python   https://towardsdatascience.com/lets-make-a-map-using-geopandas-pandas-and-matplotlib-to-make-a-chloropleth-map-dddc31c1983d
