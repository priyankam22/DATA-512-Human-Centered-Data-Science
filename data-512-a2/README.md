# Analysis of bias in data on Wikipedia
  
This analysis is done as part of the assignment A2:Bias in Data for the course DATA 512: Human Centered Data Science. I have provided all the documentation and explanation of data and code to enable full reproducibility of this work.  
  
The purpose of this study is to explore bias in data on Wikipedia by analyzing Wikipedia articles on politicians from different countries. We will look at two metrics for this analysis - political coverage on Wikipedia as compared to the population of the country and the proportion of high quality articles.  
  
## Data Sources   
  
We will combine the below two datasets for our analysis:  
    
1) **Wikipedia articles** :   
  
Available from - Keyes, Oliver (2017): Politicians by Country from the English-language Wikipedia. figshare. Fileset.  
  
This dataset contains information on English language Wikipedia articles from the category "Category:Politicians by nationality" and its subcategories. This dataset can be downloaded from [figshare](https://figshare.com/articles/Untitled_Item/5513449). Click on the Download link and extract the "page_data.csv" from the data folder in the downloaded zip file. A downloaded version of the  "page_data.csv" (downloaded on 28th Oct 2018) is also uploaded to the data folder under [git](https://github.com/priyankam22/DATA-512-Human-Centered-Data-Science/tree/master/data-512-a2) repository for easier reproducibility.  
  
LICENSE: This dataset is released under the CC-BY-SA 4.0 license by the owner on Figshare.  
  
Column|Description
---|---
page|Article Title
country|	Country of origin
rev_id|last revision id of the edit to the article
  
  
2) **Country Population** : This dataset contains a list of countries and their populations till mid-2018 in millions. This dataset is sourced from the [Population Reference Bureau](https://www.prb.org/data/). As the dataset is copyrighted, it is not available on this repository. The data might have changed when you extract it from the website. For reproducibility, i have included the intermediate merged file for the final analysis.  
  
Column|Description
---|---
Geography|Country name
Population mid-2018 (millions)|The population of the country till mid-2018 in millions
  
## File structure

The data and code required for reproducing this analysis are available in this repository under the below folder structure.  
  
1) **data folder** - This folder contains all the raw data files used for analysis and the final prepared dataset.  
  
	*page_data.csv* : This is the Wikipedia articles dataset from Figshare.  
	*wiki_articles_country_pop.csv* : This is the final merged dataset which has been created by merging and cleaning data from above two datasets including the quality of articles from ORES. This dataset can be created using the code in the IPython notebook OR it can be used directly for the final analysis steps to esnure dull reproducibility.  
	  
2) **code** - This folder has all the code required for thr analysis.  
  
  *hcds-a2-bias.ipynb:* This Jupyter notebook has the complete code for cleaning and merging the raw datasets, getting the quality of articles using the API for ORES and the final analysis using the two metrics - number of articles on politicians as compared to the country population and the proportion of high quality articles.  
  
### Quality of Articles:  
  
To get the quality score of Wikipedia articles, we will use the machine learning system called [ORES](https://www.mediawiki.org/wiki/ORES) ("Objective Revision Evaluation Service"). ORES estimates the quality of a given Wikipedia article by assigning a series of probabilities that the article belongs to one of the six quality categories and returns the most probable category as the prediction. The quality of an article (from best to worst) can be categorized into six categories as below.  
    
1. FA    - Featured article
2. GA    - Good article
3. B     - B-class article
4. C     - C-class article
5. Start - Start-class article
6. Stub  - Stub-class article
    
For the purpose of this analysis, "high quality" articles are articles classified as "FA" or "GA".  
  
More details about these categories can be found at [Wikipedia: Content Assessment](https://en.wikipedia.org/wiki/Wikipedia:Content_assessment#Grades)  
  
We will use a Wikimedia RESTful API endpoint for ORES to get the predictions for each of the Wikipedia articles. Documentation for the API can be found [here](https://ores.wikimedia.org/v3/#!/scoring/get_v3_scores_context_revid_model).  
  
The ORES system is available under the licence [Creative Commons Attribution-ShareAlike License](https://creativecommons.org/licenses/by-sa/3.0/).  
  
## Results  
  
#### 10 highest-ranked countries in terms of number of politician articles as a proportion of country population
  
Country|Population till mid-2018 (in millions)|Total Articles|Articles Per 100 Persons
---|---|---|---|
0|Tuvalu|0.01|55|55.000000
1|Nauru|0.01|53|53.000000
2|San Marino|0.03|82|27.333333
3|Monaco|0.04|40|10.000000
4|Liechtenstein|0.04|29|7.250000
5|Tonga|0.10|63|6.300000
6|Marshall Islands|0.06|37|6.166667
7|Iceland|0.40|206|5.150000
8|Andorra|0.08|34|4.250000
9|Federated States of Micronesia|0.10|38|3.800000
  
#### 10 lowest-ranked countries in terms of number of politician articles as a proportion of country population  
  
Country|Population till mid-2018 (in millions)|Total Articles|Articles Per 100 Persons
---|---|---|---|
0|India|1371.3|986|0.007190
1|Indonesia|265.2|214|0.008069
2|China|1393.8|1135|0.008143
3|Uzbekistan|32.9|29|0.008815
4|Ethiopia|107.5|105|0.009767
5|Zambia|17.7|25|0.014124
6|Korea, North|25.6|39|0.015234
7|Thailand|66.2|112|0.016918
8|Bangladesh|166.4|323|0.019411
9|Mozambique|30.5|60|0.019672
  
#### 10 highest-ranked countries in terms of number of GA and FA-quality articles as a proportion of all articles about politicians from that country
  
Country|Total Articles|Good Quality Articles|Proportion Of Good Quality Articles (%)
---|---|---|---|
0|Korea, North|39|7|17.948718
1|Saudi Arabia|119|16|13.445378
2|Central African Republic|68|8|11.764706
3|Romania|348|40|11.494253
4|Mauritania|52|5|9.615385
5|Bhutan|33|3|9.090909
6|Tuvalu|55|5|9.090909
7|Dominica|12|1|8.333333
8|United States|1092|82|7.509158
9|Benin|94|7|7.446809
  
#### 10 lowest-ranked countries in terms of number of GA and FA-quality articles as a proportion of all articles about politicians from that country¶
  
Country|Total Articles|Good Quality Articles|Proportion Of Good Quality Articles (%)
---|---|---|---|
0|Sao Tome and Principe|22|0|0.0
1|Mozambique|60|0|0.0
2|Cameroon|105|0|0.0
3|Guyana|20|0|0.0
4|Turkmenistan|33|0|0.0
5|Monaco|40|0|0.0
6|Moldova|426|0|0.0
7|Comoros|51|0|0.0
8|Marshall Islands|37|0|0.0
9|Costa Rica|150|0|0.0

## Observations
  
By comparing the highest and lowest ranking countries using the two metrics described above, we can get a fair idea of bias in the data on Wikipedia. Before the analysis, I was expecting to find some bias in the data due to various economic and cultural reasons. Wikipedia contributions would be more common in developed countries with easy access to computers and higher educatioon levels. Developing countries with large populations usually have large economic disparities in terms of education, income, infrastructure. Such factors will affect the Wikipedia representation at the country level.  
  
As seen in the tables above, there is a huge variation in the proportion of Wikipedia articles on politicians with respect to the population of the country. Countries with very low populations have a higher proportion of political coverage as compared to countries with large populations like India, China. This is in agreement to my expectations as discussed above. Another source of bias can be the fact that Engish is not the primary language in many countries and hence the Wikipedia articles about politicians might be contributed in other languages.   

The results using the second metric of high quality articles is somewhat suprising. Countries like Saudi Arabia, Central African Reuplic, Bhutan have a higher proportion of higher quality articles than United States. Given the higher education levels and larger research community in the United States, I would have expected it to have more quality contributions to Wikipedia. This raises the question of how good is the ORES system at predicting quality. Unfortunately, I did not get a chance to assess the reliability of the ORES system and how much can we trust the quality predicted by the machine learning model. As a future steps, I would like to go through the documentation of the system in detail and find out about how reliable it is before making any final conclusions.  


## Final Comments
  
This analysis helped me in understanding how to look for bias in datasets. It is a useful and important learning for a data scientist. Before we make inferences based on datasets, we must consider the bias built into the dataset due to various factors.  
This exercise also reinforced my understanding of the steps in creating a reproducible research.   

