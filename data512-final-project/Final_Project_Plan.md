# Seattle – A Story of Growth
## Building Permits Data Analysis
  
  
### Introduction
  
According to a recent [article](https://www.seattletimes.com/seattle-news/data/114000-more-people-seattle-now-this-decades-fastest-growing-big-city-in-all-of-united-states/) in *“The Seattle Times”*, Seattle is now the decade’s fastest-growing big city in the United States. As of July 2017, Seattle has grown by a staggering 18.7 percent in the last seven years which ranks as the fastest rate of growth among the 50 largest U.S. cities<sup>[1](https://www.seattletimes.com/seattle-news/data/114000-more-people-seattle-now-this-decades-fastest-growing-big-city-in-all-of-united-states/)</sup>. Another interesting way of measuring the growth of the city can be in terms of the number of new construction projects. The constant sight of construction cranes has now become an integral part of Seattle’s skyline. 
  
The [Seattle Department of Construction and Inspections (SDCI)](http://www.seattle.gov/sdci) has made available the data on building permits to the public through the [Open Data Program](http://www.seattle.gov/tech/initiatives/open-data). The dataset includes all building permits issued or in progress within the city of Seattle since 1986.
  
For my final project for DATA 512: Human Centered Data Science, I plan to analyze this dataset in order to gain a better understanding of the growth of Seattle in terms of real estate. I hope to discover any interesting trends or patterns from the data and find answers to some specific research questions listed [here](#research).  

### Motivation

I moved to the city of Seattle in 2017 and have seen it grow explosively in the last one year. After reading recent news articles on the construction boom happening in Seattle, I have been intrigued by the rapid growth of the city. It would be interesting to analyze the different ways in which the city is growing.   
My analysis can be useful for any resident of Seattle who is interested in investing their hard-earned money in real estate by identifying the fast-growing regions within Seattle. It might turn out to be useful to the city of Seattle government to gain a different perspective of  the city based on the building permits issued by them.  

### <a name="research"></a>Research Questions
  
I have several research questions that I would like to answer using this dataset:  
1)	What is the distribution of construction projects across residential and non-residential uses?   
2)	Is there more demand for apartment condos or single-family homes?  
3)	How has the city grown in the last five years as compared to previous decade?  
4)	Which are the fastest growing neighborhoods within Seattle?  
5)	How many of these projects are demolition projects?  
6)	What are the highest and lowest projected costs of these projects across different segments – residential, commercial?  
  
This study is more of an exploratory analysis to discover interesting patterns and insights from the data. It is also aims to test the hypothesis that Seattle has grown rapidly in the past five years and continues to grow at an increasing rate.  

### Data Sources
  
The main dataset used for this analysis is the Building Permits data made publicly available by the City of Seattle on their [website](https://data.seattle.gov/Permitting/Building-Permits/76t5-zqzr).  
The dataset has around 120K rows and 24 columns. The dataset is updated on a daily basis and can be accessed via the [Socrate API](https://dev.socrata.com/foundry/data.seattle.gov/k44w-2dcq). It can also be directly downloaded as a csv from the same API website under the Download & Export section.  
  
For more information about the API and dataset, refer : https://dev.socrata.com/foundry/data.seattle.gov/k44w-2dcq  
  
The column descriptions are listed below:  
  
|Column Name|Description|Type|  
|---|---|---|  
|PermitNum|The tracking number used to refer to this permit in SDCI's tracking system.|Plain Text|  
|PermitClass|	The permit class tells you the type of project.|	Plain Text
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

The above dataset seems to be enough to answer my research questions as of now. But in case I find some interesting finding and want to dig further in that direction, I might supplement the dataset using other data sources.   
  
### Data Analysis
  
I will be using Python (pandas library) and Jupyter Notebooks to perform the data cleaning, data transformations and data analysis. For data visualizations, I will be using the python libraries – matplotlib and seaborn. The data needs to be cleaned and prepared before it can be used for analysis. There are several missing values which need to be handled. I will perform some initial exploratory analysis to understand the data and check for any outliers.  
  
Once the data is prepared, I plan to do statistical analysis to answer the research questions. I would be  using plots and visualizations to convey my results and outcomes.  
  
By the end of analysis, I hope to answer some of my research questions, find some interesting trends in the growth of Seattle and generate useful visualizations for the end user.  
   
### Data Limitations
The data is about building permits which were submitted to the Seattle Department of Construction (SDCI) for approvals. There is no information about whether the project was completed or not. There might be cases where the permit was issued but the project was scrapped due to some reason. Since I did not find a publicly available dataset having information about completed projects, for the sake of simplicity I will make an assumption that most of the proposed projects with an issued permit were completed.  
  
Another point to emphasize is that the estimated project costs from the dataset provides the estimated cost at the time of applying for permit and can potentially be very different than actual costs. Builders might not want to expose the true costs of their projects or the cost might exceed the budgets by a large magnitude.   
  
Any results from this analysis need to be interpreted by taking the above assumptions and limitations into account.  
  
### License:

The data is owned by Seattle Department of Construction (SDCI) and is made available to the public  under the Public Domain License (https://wiki.creativecommons.org/wiki/Public_domain) which allows free use by anyone for any purpose without restriction under copyright law.  
  
The City of Seattle Government requires the users of this data to include the following disclaimers: 

*"The data made available here has been modified for use from its original source, which is the City of Seattle. Neither the City of Seattle nor the Office of the Chief Technology Officer (OCTO) makes any claims as to the completeness, timeliness, accuracy or content of any data contained in this application; makes any representation of any kind, including, but not limited to, warranty of the accuracy or fitness for a particular use; nor are any such warranties to be implied or inferred with respect to the information or data furnished herein. The data is subject to change as modifications and updates are complete. It is understood that the information contained in the web feed is being used at one's own risk."*  
  
### Human Centered Design Considerations  

#### Privacy and consent
  
The data includes addresses of each construction project, granular up to the street level. However, it does not specify the apartment number. This might be acceptable for buildings but in case of single-family homes, these addresses can be enough to identify the house and hence the owner. The projected costs provide further sensitive information which has a potential for misuse. Did the permit applicants consent to the release of this data? Even if the data does not include direct personally identifiable information, it is not very difficult to derive the associations to individual owners. This is an example of data which should be considered for further anonymization before release.  

#### Human-centered approach
I aim to make this study completely reproducible by following the best practices for performing and sharing open research. I will also include human centered design considerations in my study in the following ways:  
•	This analysis is centered on the users – Seattle residents who are interested in understanding the growth of the city they live in from a larger perspective. The visualizations and results will be presented by taking into consideration the end user.  
•	Wherever possible, performing qualitative research to understand user requirements, user testing and evaluation to improve the results.  

#### References:  
  
<sup>1</sup>https://www.seattletimes.com/seattle-news/data/114000-more-people-seattle-now-this-decades-fastest-growing-big-city-in-all-of-united-states/  
http://www.seattle.gov/sdci   
https://data.seattle.gov/Permitting/Building-Permits/76t5-zqzr  
https://dev.socrata.com/foundry/data.seattle.gov/k44w-2dcq  
