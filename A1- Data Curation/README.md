# English Wikipedia Page Views

This project is part of the assignment A1 : Data Curation for the course DATA 512 Human Centered Data Science.  

**Goal:**  
•	The goal of this project is to construct, analyze, and publish a dataset of monthly traffic on English Wikipedia from January 1 2008 through September 30 2018.  
•	The final result is a reproduction of  the English Wikipedia Page Views plot, originally created by Rex Thompson.  
•	This data analysis and visualization follows the best practices for reproducibility of open scientific research, thus making it easily reproducible by others – from data collection to data analysis.  

**Data:**  
The data used for this analysis is sourced from two APIs:  
1.	The Legacy Pagecounts API ([documentation](https://wikitech.wikimedia.org/wiki/Analytics/AQS/Legacy_Pagecounts), [endpoint](https://wikimedia.org/api/rest_v1/#!/Pagecounts_data_(legacy)/get_metrics_legacy_pagecounts_aggregate_project_access_site_granularity_start_end)) provides access to desktop and mobile traffic data from December 2007 through July 2016.   
2.	The Pageviews API ([documentation](https://wikitech.wikimedia.org/wiki/Analytics/AQS/Pageviews), [endpoint](https://wikimedia.org/api/rest_v1/#!/Pageviews_data/get_metrics_pageviews_aggregate_project_access_agent_granularity_start_end)) provides access to desktop, mobile web, and mobile app traffic data from July 2015 through last month.    
 **License** :  Unless otherwise specified in the endpoint documentation above, content accessed via this API is licensed under the [CC-BY-SA 3.0](https://creativecommons.org/licenses/by-sa/3.0/) and [GFDL](https://www.gnu.org/copyleft/fdl.html) licenses.  

**Files:**
  
The code and data files are described below:  
1)	**English_Wikipedia_Page_Views_2007-2018.ipynb** :  All the code from data collection to data visualization is included in the this Jupyter notebook. The notebook begins with making calls to the two API endpoints to collect Wikipedia page views data from Dec 2007 till Sep 2018. The data is cleaned, merged and prepared for the analysis. A time series plot is created using matplotlib which shows the trends in the pageviews across time.   
2)	**data**: This folder contains all the intermediate files which can be used for reproducing exact results.  

      *apiname_accesstype_firstmonth-lastmonth.json*: It contains the 5 json files with this naming convention which contain the raw data   from the api calls made in October 2018.  

      *en-wikipedia_traffic_200712-201809.csv* : This file contains the final merged dataset which was used to create the final plot.  

**Data Visualization:**   
The final visualization is available as a jpeg file - English Wikipedia PageViews Graph.jpg    



