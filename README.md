# Data Cleaning Python

## Project Overview

This project was my first time working with python code, so i decided to flex my data cleaning skill this time using python. It was abit tough, but with the aid of YouTube and google, i saw the end of it. By the way, i got a project where i used SQL to clean data. You can check that out [here](https://github.com/StephenTheAnalyst/Data-Cleaning-SQL)

## Data Overview

This dataset contains information on customers and their choices of being contacted or not. I got the dataset from a YouTuber's Github repository. I am not sure if it is okay to tag him, but he was a good tutor and i learnt a lot from him. The dataset contains 8 columns, which are:

 1. **CustomerID** 
 2. **First_Name**
 3. **Last_Name**
 4. **Phone_Number**
 5. **Address**
 6. **Paying Customer**
 7.	**Do_Not_Contact**
 8.	**Not_Useful_Column**

## Tools

 - Jupyter Notebook

## Data Cleaning/Preparation 

 1. Dropped Duplicate
 2. Did some striping in the "last name" column
 3. Cleaned the "phone number" column and standardized the numbers(This took the longest. I was trying to use the replace function, until i figured it wasn't going to work, then i had to go watch some YouTube videos on lambda) 
 4. Standardized the "address" column
 5. Standardized the "pay customer" and "do not contact" columns( I spent a lot of time figuring this part out too. I was trying to use replace function again, but i wasn't getting what i wanted, then 'map' came to the rescue) 😅
 6. I dropped the "not useful column", because it was not 'useful' 😂
 7. Then i shortlisted the list to the customers that don't mind being contacted
 8. Then i reset the index

## Results/Finding 

Click [here](https://github.com/StephenTheAnalyst/DataCleaningPython/blob/main/Data%20Cleaning.md) to see how i went through with all those.
