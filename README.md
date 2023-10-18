# data-512-homework_2

Purpose of this assignment is to explore the concept of bias in data using Wikipedia articles. This assignment will consider articles about cities in different US states. For this assignment, you will combine a dataset of Wikipedia articles with a dataset of state populations, and use a machine learning service called ORES to estimate the quality of the articles about the cities.


## Given Files

* us_cities_by_state_SEPT.2023.csv - The Wikipedia Category: Lists of cities in the United States by state was crawled to generate a list of Wikipedia article pages about US cities from each state. The file columns are: state	page_title	url <img width="563" alt="image" src="https://github.com/KhanatayevB/data-512-homework_2/assets/72726814/923a5462-02d9-4253-9b72-eba397294ef8">

* NST-EST2022-POP.xlsx - The US Census Bureau provides updated population estimates for every US state. You can find State Population Totals and Components of Change: 2020-2022 from their website.
* US States by Region - US Census Bureau.xlsx - The regional and divisional agglomerations as defined by the US Census Bureau

## Generated Files
article_data.csv - File generated 
article_data_clean.csv

## Flow of the Analysis

1. Run the Page_Info_Request_Notebook_Bazham_Khanatayev.ipynb notebook. It will take the us_cities_by_state_SEPT.2023.csv files and grab the page information requests from the API. It will then output the article_data.csv file.
2. The article_data.csv is the input for the Cleaning_article_data_csv_Notebook_Bazham_Khanatayev.ipynb. which the notebook that you will run next. This notebook prepares the data for the ORES API removing titles that do not make sense for this task. The output of the notebook is article_data_clean.csv





