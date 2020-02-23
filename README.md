# WebDataAnalytics

——————————FOLDER——————————
Codes -> All .ipynb File.
DataFile -> All .csv File.
Analysis -> Minitab and R file
————————————————————————


—————————————————————CODE RUN STEPS—————————————————————
1.	Scrape Kickstarter Project Name.ipynb 
2.	User and Project Details.ipynb
3.	Twitter.ipynb
4.	Twitter_Sentiment.ipynb
5.	YoutubeScrape.ipynb 
6.	Youtube_Sentiment.ipynb
7.	Youtube_Merge.ipynb
8.	DataPreparation.ipynb
———————————————————————————————————————————————————


—————————————————————SCRAPING—————————————————————
Scrape Kickstarter Project Name.ipynb -> Run the code to get the list of 600 live projects that have crossed 100% mark before the deadline and 600 live projects that have not crossed 75% mark. All output will be exported to “kickstarter.csv” file.

User and Project Details.ipynb -> Running the code will take all the projects from “kickstarter.csv”. Additional details of the project such as Number of Projects by the owner, whether the user has facebook linked to the profile or not, number of backers for the project are scrapped from this file. The code are inside tryExcept, for code to automatically go to rest if kickstarter blocks the scrapper for some time. All the scrapped data will be exported to 'kickstarter_details.csv’ file.

Twitter.ipynb -> Will take project details from “kickstarter.csv” and search for its tweets on Twitter for last 7 days. Please put your Twitter credentials in the second block of the code. The code have been built to adapt with the Twitter limit per hour and will go on rest as required. All tweets will be exported to 'tweets_report.csv' file.

YoutubeScrape.ipynb -> Will take project details from “kickstarter.csv” and search for its video on Youtube. It uses Selenium so chromeDriver needs to be setup. All the comment of the video tagged with the projectId will be exported to “youtube_doc.csv”.

Youtube_Merge.ipynb -> Since scraping from youtube took lot of time, we had ran multiple scrapers parallel. Therefore this file will take all the 'youtube_nlp.csv’ file that has sentiment score of the youtube comment, append all the files and find the mean of all the comment projectwise. The final dataframe will be exported to ‘youtube_sentiment.csv’.
————————————————————————————————————————————————



—————————————————————SENTIMENT ANALYSIS—————————————————————
Twitter_Sentiment.ipynb -> This file will take 'tweets_report.csv’ as its input and do a sentiment analysis on those tweets using Google NLP. Please input the fileName of your Google Credentials in the 2nd block of the code. The code is adjusted to limit of Google NLP. All output will be exported to 'twitter_sentiment.csv’.

Youtube_Sentiment.ipynb -> It will take youTube comment from “youtube_doc.csv” and do a sentiment analysis on those comments using Google NLP. Please input the fileName of your Google Credentials in the 3rd block of the code. All the sentiment score of the comments will be exported to 'youtube_nlp.csv’.
—————————————————————————————————————————————————————



—————————————————————DATA PREPARATION—————————————————————

DataPreparation.ipynb -> This file will take in all the all the final files, i.e "kickstarter.csv”, "kickstarter_details.csv”, "twitter_sentiment.csv” and "youtube_sentiment.csv”. All the data from those files will be merged using ProjectId. New Required column will be created like length of the project, and also Boolean values will be converted to 1 and 0. Only required column for the model will be filtered and exported to “Modal_data.csv”.

Details on the columns of the final dataset is :-
___________________________________________________________________________________
|Column No	| Title 			| Description
|	1	| project_id		| Primary Key of the Data
|	2	| pledged		| Total funding of the Project till Date
|	3	| backers_count	| Number of people who have funded the project till date
|	4	| percent_funded	| Percentage of Pledged to the Goal of the project
|	5	| Followers		| Sum of followers of people who has Twitted about the Project
|	6	| project_category	| Category where project Belongs
|	7	| user_TotalProject	| Total number of project by the creator of the Project
|	8	| Sentiment_Result	| Weighted Average of the Twitter Sentiment of the Tweets
|	9	| Day			| Total number of days for the project open in Kickstarter
|	10	| Success		| 1 if the Project has more than 90% funding else 0
|	11	| Goal			| Total Amount asked for the Project
|	12	| Facebook		| If the owner of the Project has facebook linked to the profile or not
|	13	| hasTweets		| 1 if tweets have been found for the project else 0
|	14	| daysRemaining	| Days remaining for the project to end
|	15	| has_Youtube	| 1 if it has Youtube video else 0
|	16	| youtube_sentiment| Average Sentiment of the comment of the Youtube
——————————————————————————————————————————————



—————————————————————STATISTICAL ANALYSIS—————————————————————
Web_data_Minitab.mpx -> Minitab will take “Modal_data.csv”.  Minitab File has all the Regression Analysis Tested to build a conclusion.

Analysis.R -> Conduct various T-test in models from Minitab. 
—————————————————————————————————————————————————————



—————————————————————DATA FILES—————————————————————
kickstarter.csv		-> File with basic project information from KickStarter
kickstarter_details.csv	-> Additional Detail about the project and its Owner
tweets_report.csv		-> Project wise Tweets
youtube_doc.csv		-> Project wise Youtube comment
twitter_sentiment.csv	-> Twitter Sentiment Result
youtube_<x>nlp.csv		-> Youtube Sentiment Result. x Represents file number
youtube_sentiment.csv	-> Merge all Youtube Sentiment File
Modal_data.csv		-> File dataset after Merging data from various files
————————————————————————————————————————————————


