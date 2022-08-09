# Trends in Covid-19 Cases and Vaccinations: An Analysis of Two Covid-19 Datasets.
## Contents
A repository containing two Jupyter Notebooks utilizing information from two Covid-19 datasets.
|Notebooks  | Description |
| ------------- | ------------- |
| [Data Exploration/Clean Up](Data_Exploration_and_Clean_Up.ipynb)  | The notebook containing our dataset import, dataframe creation, and dataframe cleaning. |
| [Data Analysis and Summary](Final_Analysis.ipynb)  | The notebook containing the visualization and analysis of the dataframes we created in the Data Exploration notebook  | 

|Datasets  | Description |
| ------------- | ------------- |
| [COVID-19 World Vaccination Progress](Resource/country_vaccinations.csv)  | Recorded vaccination data on a global scale by country |
| [COVID-19 dataset](Resource/covid-data.csv) | A large range of useful Covid-19 datapoints on a global scale by country. |

## What is this and why?
This repository contains a data analysis project using both a Covid-19 dataset on World Vaccination progress and a Covid-19 dataset on Covid-19 World case data.

We wanted to determine if analysis of Worldwide Covid-19 vaccination progress alongside Worldwide case data would allow us to observe a noticable relationship between the two. We provide relationships both on a global scale and on a country-by-country basis. 

From these relationships we wanted to determine: 
1. What is the relationship between total Covid-19 vaccinations vs total Covid-19 cases for the entire dataset?
   
2. What is the relationship between countries with highest and lowest number of vaccination vs total Covid-19 cases per hundred?

## How?
This is a project utilizing the tools provided by Jupyter Notebook, pandas, and Matplotlib to clean, organize, visualize, and analyze two Covid-19 datasets found on Kaggle, built from data sourced from [Our World In Data](https://github.com/owid/covid-19-data/tree/master/public/data). From these datasets we aim to: 

- [x] [Create and Clean dataframes from datasets](https://github.com/oiwuoni/group-repo-project-1/edit/jacob/README.md#create-and-clean-dataframes-from-datasets)
  - [x] Create dataframes from the csv files found in the datasets.

  - [x] Clean vaccination dataset by removing columns unnecessary for analysis, and find max number of cases and max vaccinations per country and analyze the top 5 countries with max number of cases.
  - [x] Merge datasets on country code

- [x] [Data Analysis](https://github.com/oiwuoni/group-repo-project-1/edit/jacob/README.md#data-analysis)

  - [x] Answer research questions 1 by creating visuals for the entire cleaned dataset using chart visualization. 

  - [x] Also include our linear regression showing a correlation b/w vaccination and cases?
  - [x] Establish parameters for high and low vaccinations per hundred groups and group data by each parameter.
  - [x] Answer question 2 by creating visuals for grouped dataset, possibly creating a visual for each separate group
- [x] [Summarize findings, acknowledge limits to our analysis based on available data.](https://github.com/oiwuoni/group-repo-project-1/edit/jacob/README.md#findings-summary-and-limitations)

---

## *Create and Clean dataframes from datasets*

<details>
    <summary>Dataset Explanation and Initial Dataframe Cleaning and Creation </summary>

**[COVID-19 World Vaccination Progress](https://www.kaggle.com/datasets/gpreda/covid-world-vaccination-progress)**: 
Recorded vaccination data on a country scale. Includes two csv files within its dataset, one for `Country/Vaccination` data and one for Country/Vaccination by Manufacuter. We chose to only use `Country/Vaccination` data. From this csv we created a pandas Dataframe from these columns:
> `[country]`, `[date]`, `[iso_code]`, `[people_vaccinated]`,`[daily_vaccinations]`, `[people_vaccinated_per_hundred]`

**[COVID-19 dataset](https://www.kaggle.com/datasets/georgesaavedra/covid19-dataset)**: A dataset containing one csv file and 67 columns worth of data, any of which could be relevant depending on what question you want to ask. For our usage case, we created a pandas DataFrame from these columns: 
> `[location]`, `[date]`, `[iso_code]`, `[total_cases]`, `[new_cases]`, `[total_deaths]`, `[new_deaths]`, `[population]`, `[total_cases_per_million]`, `[new_cases_per_million]`

And created our own column using the `[total_cases]` and `[population]` columns: 
>`['total_cases_per_hundred']`

</details>

<details>
    <summary>Dataframe Summary</summary>

We have these DataFrames. Dataframes nested are based off the Dataframe above:
1. `covid_vacc_df`: Vaccination data Dataframe from COVID-19 World Vaccination Progress
    - `world_df`: Dataframe based on iso code matching OWID_WRL, a summary of info on the entire world.
2. `covid_cases_df`: Case data Dataframe from COVID-19 dataset  
3. `max_covid_vacc_df`:DataFrame grouped by ISO code sorted by maximum vaccinations. 
4. `max_covid_case_df`: DataFrame grouped by ISO code sorted by maximum cases.
   - `sort_covid_case_per_hund_df`: Maximum cases sorted by cases per 100 people
   - `sort_most_covid_case_df`: Maximum cases sorted by total cases
5. `merge_df`: DataFrame outer-merging the main two DataFrames on `iso_code` and `date`
   -  `large_countries_df`:Top 30 Countries. Based on populations exceeding a cutoff of 47,000,000 


</details>

---

## *Data Analysis*

From the cleaned and organized DataFrames we were now able to visually represent any trends observed in the data. 
<details> 
    <summary> World Data Figures </summary>

`Worldwide Reported Covid Cases plotted Alongside New Cases`: Stackplot to visualize timewise relationship.  

`Worldwide Reported Covid Cases`: Stackplot of exclusively new cases.

</details>


<details>
    <summary>Country Data Figures </summary>

Country Data all used bar charts to represent their data. All countries plotted fell within the top 30 countries for population. (>47,000,000)

## Top 3 countries by people vaccinated per 100

`Daily Vaccinations vs New Cases: China`: People Vaccinated Per Hundred: 87.89%


`Daily Vaccinations vs New Cases: South Korea`: People Vaccinated Per Hundred: 87.48%
 

`Daily Vaccinations vs New Cases: Italy`: People Vaccinated Per Hundred: 83.91%. 


## Bottom 3 countries by people vaccinated per 100
`Daily Vaccinations vs New Cases: Nigeria`: People Vaccinated Per Hundred: 8.39% 



`Daily Vaccinations vs New Cases: Tanzania`: People Vaccinated Per Hundred: 5.24%



`Daily Vaccinations vs New Cases: Democratic Republic of Congo`: People Vaccinated Per Hundred: 0.82%

## USA and Brazil

`Daily Vaccinations vs New Cases: USA`: People Vaccinated Per Hundred: 76.63%

`Daily Vaccinations vs New Cases: Brazil`: People Vaccinated Per Hundred: 83.28%

</details>


<details>
    <summary>Statistical Figures</summary>

## Linear Regression of Daily Vaccinations vs Daily New Cases for World Data

`Daily Vaccinations vs New Cases: World`: Scatter plot with linear regression calculated using stats.lingregress. Kept to illustrate our progression through finding a statistical model that would work for our needs. 

`Daily Vaccinations vs New Cases: World`: A scatterplot using a dataframe specfically made to address problems found from the previous plot. We set a cutoff date of `2021-11-01` applied to our `world_df` dataframe in order to exclude data that might include the omnicron variant for Covid-19. We then ran a linear regression on this plot and found an r<sup>2</sup> of 0.0365. 


</details>

## *Findings Summary and Limitations*

Firstly, it must be stated that this data cannot be without error. The datasets we used were reliant on a country to reliably report its data accurately and timely, but that should expected to be impossible to count on. Our judgements on our results should reflect that idea. 

Next, our statistical linear regression test returned an r<sup>2</sup> value of 0.0365, meaning there is little correlation in our linear statistics model. We believe that there is no error here, and we believe that a low value should be expected, as we believe a linear statistical model is not a good model to use for the data we were testing. In the future we would use a non-linear regression test, or model an ANOVA hypothesis test. (Question 1)

From observation of our visual models, the stories each plot tells range in clarity. Not every plot shares the same resolution. For example, a plot like China's whose Daily Vaccinations plot pushes into the tens of millions(1e7), inflating our stackplot represeting worldwide data, shows an entirely different resolution than our next closest plots of Brazil and USA, who both push into the millions(1e6). Both the USA and Brazil are still able to show us a comparative look at their new case data ploted alongside daily vaccination data, as well as our stackplot which is scaled to 1e7 in accomodation, while new case data is not visable at any point on our plot for China. The same can almost be said for South Korea's timeline, which at a smaller scale shows a similar visual trend until 2021 into 2022 when cases pick up and spike as the omnicron variant spreads. Instances of poor or questionable resolution are also found in one of our bottom performing countries, Tanzania. Tanzania is our most visually odd and interesting plot to look at, and is one that we cannot offer an explanation. (Question 1 and 2)

One visual takeaway that can be seen, regardless of resolution for the majority of plots is that each had an incredibly sharp spike when, as we assumed, and later concluded with help from TA Colin B., the omnicron variant spread in earnest. Further, external research may be done into the core reasons why for those curious - however a summary on currently availible PubMed searches tells Omnicron is highly transmissible comparatively and has vaccine-escape mutations. (Question 1 and 2) 

In conclusion, we learned a lot about the scale of data analysis from this project, how we would like to approach a problem like this in the future, and further questions on data analysis and data science we want to learn the answers to.  

---
## References

##### [1] GABRIEL P, 2022, March, COVID-19 World Vaccination Progress, [Version 249], Retrieved [July 28th 2022]. https://www.kaggle.com/datasets/gpreda/covid-world-vaccination-progress 

##### [2] GEORGE S., 2022, February, COVID-19 dataset, [Version 1], Retrieved [July 28th 2022]. https://www.kaggle.com/datasets/georgesaavedra/covid19-dataset

#### Both data sets used data sourced from the OWID github; 

##### [3] Mathieu, E., Ritchie, H., Ortiz-Ospina, E. et al. A global database of COVID-19 vaccinations. Nat Hum Behav (2021). https://doi.org/10.1038/s41562-021-01122-8
