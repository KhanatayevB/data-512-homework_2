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
* problematic_titles_log.csv - These are the articles that have titles that do not make sense for the analysis: <img width="611" alt="image" src="https://github.com/KhanatayevB/data-512-homework_2/assets/72726814/6408632a-b1c0-4dde-b2cb-849b0a0f098f">






## Flow of the Analysis

1. Run the Page_Info_Request_Notebook_Bazham_Khanatayev.ipynb notebook. It will take the us_cities_by_state_SEPT.2023.csv files and grab the page information requests from the API. It will then output the article_data.csv file.
2. The article_data.csv is the input for the Cleaning_article_data_csv_Notebook_Bazham_Khanatayev.ipynb. which the notebook that you will run next. This notebook prepares the data for the ORES API removing titles that do not make sense for this task. The output of the notebook is article_data_clean.csv.
3. Next, we will run the ORES_Request_Predication_Notebook_Bazham_Khanatayev.ipynb which takes the article_data_clean.csv and gets the quality scores. It outs two csv's one for the articles that were able to get a score and a csv for the articles that were not able to.
4. Run the Pre_Analysis_Data_Combination_Preperation_Bazham_Khanatayev.ipynb which takes in the US States by Region - US Census Bureau.xlsx excel file, the NST-EST2022-POP.xlsx file and the quality_scores_pred.csv. It then cleans and prepares data from all three csv's and outputs the wp_scored_city_articles_by_state.csv file.
5. Run the Results_Bazham_Khanatayev.ipynb that takes in wp_scored_city_articles_by_state.csv and creates the required tables. The questions for each table are all clearly documneted in the notebook.


## Write Up Reflections

I've worked with many large data sets before and I always expect there to be some type of a bias. Usually, there are certain judgements that must be made throughout the data retrievel, preprocessing and analysis steps. These judgement calls are based on the discretion of the team or person doing the analysis and therefore introduces bias. Often times, it is related to data omission and data manipulation. There may be some data that we deem to be less useful or too much of an effort to wrangle. But, the data may have some important additional insight that we cannot predict beforehand. I'm thinking along the lines of long tail biases or outliers. 

In this case, we have some sources of bias. The first scenario here where I see some potential bias is in the cleaning process right after the revision ID's were pulled from the API. When cleaning, I essentially removed titles that were not clearly tied to an entire state and I also removed rows that had Nan's. Obviously, I checked to make sure that not too much data was being lost and it ended up being a small enough portion where we stil had lots of data. But, what if there was something wrong with the API for certain regions or states only? I was assuming the errors were more randon but it could have not been. This is exactly the same issue with the ORES predicted quality scores. There were many titles that did not get a score and it could be random. But, there could also be some systematic temporay or long term issue with the API that was only affecting a certain type of article. We then use the data to generate our analysis not knowing that the reason a certain region might have low article quality is because the API had some bug with those specific states. There may even be variation in the quality of the information we get from different API's or the overall quality might be similar but we have different data. That is all possible and can easily lead to concusions that did not use the entire picture. The process of documenting the analysis clearly helps with the process of identifying potential areas for Bias. 

Lets say that a researcher wanted to measure the changes in the article quality among the states as a proxy for the general popularity of states. The researcher has to consider that the quality data might be bias due to technical errors from the API. More importantly, the researcher might not be aware that certain states are having very large population increases in cities where many people do not speak english as their first language. Therefore, there might be many articles being puplished that are not in English and will Skew the results of the study. Also, what if there were articles published before Wikipedia existed or some other website that the populations there prefer to use to post articles.




