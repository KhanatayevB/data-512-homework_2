# data-512-homework_2
Bazham Khanatayev 10. 14.2023

Purpose of this assignment is to explore the concept of bias in data using Wikipedia articles. This assignment will consider articles about cities in different US states. For this assignment, you will combine a dataset of Wikipedia articles with a dataset of state populations, and use a machine learning service called ORES to estimate the quality of the articles about the cities.


## Given Files

* us_cities_by_state_SEPT.2023.csv - The Wikipedia Category: Lists of cities in the United States by state was crawled to generate a list of Wikipedia article pages about US cities from each state. The file columns are:  <img width="563" alt="image" src="https://github.com/KhanatayevB/data-512-homework_2/assets/72726814/923a5462-02d9-4253-9b72-eba397294ef8">

* NST-EST2022-POP.xlsx - The US Census Bureau provides updated population estimates for every US state. You can find State Population Totals and Components of Change: 2020-2022 from their website. This file a header that looks like this: <img width="547" alt="image" src="https://github.com/KhanatayevB/data-512-homework_2/assets/72726814/7fd3083a-c5a1-471b-806a-1c2aeb591025">

* US States by Region - US Census Bureau.xlsx - The regional and divisional agglomerations as defined by the US Census Bureau. Columns are: REGION	DIVISION	STATE

## Generated Files
* article_data.csv - File generated in the page requests notebook, adding a revision ID to the us_cities file. The columns are: <img width="587" alt="image" src="https://github.com/KhanatayevB/data-512-homework_2/assets/72726814/ec1988c0-dd2d-45c0-bb7f-499be60583d3">
* article_data_clean.csv - File generated after running the Cleaning article data notebook. It has the same columns as article_data.csv.
* quality_scores_pred.csv - Output of the ORES request notebook, gives you the titles that had no issues with the API. The columns are: <img width="875" alt="image" src="https://github.com/KhanatayevB/data-512-homework_2/assets/72726814/94c6440d-fdf7-4e37-a454-44e2b1179c76">
* issue_quality_scores.csv - Output of the ORES request notebook. Gives you the article titles that did not get a quality score. Columns are: <img width="641" alt="image" src="https://github.com/KhanatayevB/data-512-homework_2/assets/72726814/54c306bf-42ef-48cc-a97b-64544f862080">
* wp_scored_city_articles_by_state.csv - This file is the output of the data preprocessing notebook. It has the data nicely prepared for analysis. The columns are:<img width="533" alt="image" src="https://github.com/KhanatayevB/data-512-homework_2/assets/72726814/b76fb798-5035-4f3d-900f-2d16841fdc54">





## Flow of the Analysis

1. Run the Page_Info_Request_Notebook_Bazham_Khanatayev.ipynb notebook. It will take the us_cities_by_state_SEPT.2023.csv files and grab the page information requests from the API. It will then output the article_data.csv file.
2. The article_data.csv is the input for the Cleaning_article_data_csv_Notebook_Bazham_Khanatayev.ipynb. which the notebook that you will run next. This notebook prepares the data for the ORES API removing titles that do not make sense for this task. The output of the notebook is article_data_clean.csv.
3. Next, we will run the ORES_Request_Predication_Notebook_Bazham_Khanatayev.ipynb which takes the article_data_clean.csv and gets the quality scores. It outs two csv's one for the articles that were able to get a score and a csv for the articles that were not able to.
4. Run the Pre_Analysis_Data_Combination_Preperation_Bazham_Khanatayev.ipynb which takes in the US States by Region - US Census Bureau.xlsx excel file, the NST-EST2022-POP.xlsx file and the quality_scores_pred.csv. It then cleans and prepares data from all three csv's and outputs the wp_scored_city_articles_by_state.csv file. 





