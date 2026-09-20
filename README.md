# Google Data Analytics Professional Certificate – Capstone Project (Track B)

**By Abdu Samad Azeez**

### Introduction: 
This case study aims to showcase the useful skills and knowledge I have developed throughout the Courses 1 – 7 and to apply them to complete the Capstone Project for Course 8. I will be performing a data analysis on a football dataset for a fictional football community and social media brand, FootyStories. I will progress through each stage of the Data Analysis process ,i.e., Ask, Prepare, Process, Analyze, Share and Act to successfully complete the given task and deliver meaningful insights.

### Scenario:
I am an Aspiring Data Analyst, who is part of a popular football community and social media page, FootyStories. The team wants me to find some insights, from the previous season football statistics across the Top 5 UEFA leagues, to make a post on some interesting findings from the previous seasons. My task is to analyze data from the Top 5 European leagues to capture the anomalies that are unknown to the fans and produce data visualisations that tell a story. 


## Ask Phase:

**Business Task:** 
Identify and analyze the hidden statistical facts and trends of player performances across Top 5 European Leagues in the season 2025 – 26, to present as an engaging visual content for posting on social media.

**Key Stakeholders:**
FootyStories Content Team: The team responsible for making content, who requires clear, visual and shareable insights to be created for social media posts.
FootyStories Audience(The Fans): The viewers, who look for captivating and engaging content that shows the performance levels and efficiency of players from leagues they follow. 

**Objectives:**
1.	Identify forwards that exhibit high shot accuracy and shot-to-goal conversion rates.
2.	Identify players who lead in playmaking and goal contributions for their teams.
3.	Identify defenders that stand out in having exceptional defensive work rates alongside their high disciplinary risks
4.	Identify goalkeepers that achieve high save percentages despite facing high shots on target.


## Prepare Phase:

For the purpose of gathering the relevant datasets to work with. I researched and extracted datasets from FBRef.com, which is a popular website that contains football statistics and data across 100+ teams from both men and women’s football. All the data was collected directly from FBRef. The data is used strictly for non commercial, educational and portfolio purposes. Full credit attributed to FBRef as the original owners of the data. 

I extracted the raw data from FBRef, for football statistics for the season 2025-2026, in CSV format and then copy pasted the same on my MS Excel workbook. I used Text to Columns feature on MS Excel to transform the data into structured rows and columns by using commas ( , ) as the delimiter.

[Raw Dataset](./FootballPlayers2025-26DatabyMe.xlsx)

The workbook is structured into 4 different worksheets containing the following datasets-
1.	Standard Stats (2839 rows, 27 columns): Contains data relating goals, assists and goal contribution metrics.
2.	Shooting Stats (2839 rows, 21 columns): Contains data relating to shot accuracy, shots on target and goals per shot.
3.	Goalkeeping Stats (194 rows, 29 columns): Contains data relating to goals conceded, shots on target faced and saves made.
4.	Defensive Stats (2839 rows, 29 columns): Contains data relating to defensive work rates and disciplinary conduct.

To assess and evaluate the data integrity and reliability of the data. I have used and applied the ROCCC framework for the data I have collected:

* Reliable: The data was sourced from FBRef, which is a widely recognized database for historical football and sports analytics, ensuring reliability.
* Original: The data is collected directly from official and live match tracking systems.
* Comprehensive: Covers all data from all players registered across all Top 5 European Leagues (Premier League, La Liga, Serie A, Bundesliga and Ligue 1) for the 2025-26 season.
* Current: The data is collected and up to date of the previous season.
* Cited: The data collected is sourced with full credit to FBRef.


## Process Phase:

In this phase, I started standardising and cleaning the data from all datasets using MS Excel. For the purpose of data cleaning, I created a copy of the workbook to keep the cleaned data separate and the original datasets intact. I also added a new sheet to the new copied workbook called “Audit Log” which was to record the changes and alterations I have made in the workbook for processing stage. I have undertaken the following steps to perform the data cleaning process:
1.	Standardising Primary Positions
 * 	Issue: Raw FBRef data contained dual position strings of 9 categorical groups in Pos column which can make it difficult to aggregate data accurately by using main positional roles.
 * 	Action Taken: Standardised positions across all sheets (except Goalkeeping Stats) by creating a new column called “Primary_Pos” and used the text extraction function ‘=LEFT(D2, 2) to extract the primary roles.
 * 	Result: Reduced position categories from 9 messy variations to 4 categorical groups (FW, MF, DF, GK).
2.	Deleted Redundant Columns
 * 	Issue: Raw Data consisted of useless and redundant columns called “Matches” (which held no records except the info ‘Matches’ for every single record) and “-9999” (which had useless unique tagcodes for each record that were not beneficial for analysis).
 * 	Action Taken: Deleted those 2 columns across every dataset.
 * 	Result: Datasets no longer contain those trailing columns.
3.	Renamed Duplicate Column Name
 * 	Issue: Goalkeeping Stats had 2 columns under the same name “Save%” which can lead to confusion.
 *  Action Taken: Renamed the 2nd column with same name,which was under the category of Penalty, to “Save%PK”.
 * 	Result: The dataset no longer contains 2 columns with same name. Save% represents Open Play Saves and Save%PK represents Penalty Saves.
4.	Renamed Duplicate Columns 
 * 	Issue: Standard Stats had columns under same name and different category that was not specified.
 * 	Action Taken: Renamed all the duplicate columns and columns that needed specifications(Gls -> Gls/90 , Ast -> Ast/90 , G+A -> G+A/90 , G-PK -> G-PK/90 , G+A-PK -> G+A-PK/90).
 * 	Result: The dataset no longer contains columns with same names and has added context to avoid confusion.
As I was looking into the data through Filter to check whether any column consisted of blank values. I came across many columns having missing values. To fix this, I performed the following 2 steps-
5.	Replaced missing values across demographic data-
 * 	Issue: All datasets, except goalkeeping stats, had missing values for the columns ‘Nation’ , ‘Age’ and ‘Born’.
 * 	Action Taken: Used Find & Replace function to replace all missing values in ‘Nation’ column with Unknown and in ‘Age’ and ‘Born’ values with 0.
 * 	Result: The datasets no longer contains any blank demographic values.
6.	Replaced missing values across Performance data-
 * 	Issue: Some datasets had no values for certain metrics, which were for ‘SoT%’ , ‘G/Sh’ and ‘GSoT’ in Shooting Stats and ‘Save%’ , ‘CS%’ and ‘Save%PK’ in Goalkeeping Stats.
 * 	Action Taken: Used Find & Replace function to replace all missing values in those columns to 0.
 * 	Result: The datasets no longer contains any missing performance metrics. 
7.	Dataset had columns with no data
 * 	Issue: Defensive Stats had 2 columns ‘PKwon’ and ‘PKcon’ which had no actual values.
 * 	Action Taken: Deleted both the columns.
 * 	Result: Dataset no longer contains empty columns.

The workbook has been examined fully and cleaned of any missing values, redundant columns and spelling mistakes. Now the data is ready to be exported for the further analysis stage. 

[Cleaned Data](./CleanedFDataWIP.xlsx)


## Analysis Phase:

I will be using SQL for analysing the data. Before beginning with the data analysis process, I had to upload the cleaned data from excel to BigQuery databases. The cleaned data had to be converted to .csv files as BigQuery does not read .xlsx excel file format. For this purpose, I have exported all of the worksheets from the cleaned data excel workbook in .csv file format for uploading it to BigQuery databases. 

* [Standard Stats CSV File](./StandardStats.csv)
* [Shooting Stats CSV File](./ShootingStats.csv)
* [Goalkeeping Stats CSV File](./GoalkeepingStats.csv)
* [Defensive Stats CSV File](./DefensiveStats.csv)

Now the .csv files are ready to be uploaded and added to BigQuery databases as tables under datasets. I uploaded all of the datasets to BigQuery to perform the analysis process.

Note: The cleaned datasets in .csv format contained special characters in its columns (i.e. slashes / ) that BigQuery didn’t allow to be uploaded to its databases. To counter this, I went to the Advanced Settings under the Create Table options and changed the Column Name Character Map from “Default” to “V2”.  This option automatically changed the special characters to SQL readable form, which were replacing them with underscores (like converting G/Sh -> G_Sh)

<img width="1468" height="705" alt="bqfootysets" src="https://github.com/user-attachments/assets/caecca97-46ef-4a63-a717-ee98f2cb8aaf" />

To delve into the analysis and extract meaningful insights from the dataset, I will be structuring the SQL queries to be run around the 4 objectives of this project that are-
1.	Identify forwards that exhibit high shot accuracy and shot-to-goal conversion rates.
2.	Identify players who lead in playmaking and goal contributions for their teams.
3.	Identify defenders that stand out in having exceptional defensive work rates alongside their high disciplinary risks
4.	Identify goalkeepers that achieve high save percentages despite facing high shots on target.

### Objective 1 

**Forward Shooting Efficiency & Goal Conversion**

To evaluate the most clinical forwards across Europe’s Top 5 Leagues, I will be using table shootingstats to run an SQL query on it. The analysis here focused on the terms Goal Conversion Rate (G_Sh) and Shot Accuracy (SoT%).

To eliminate skewness and small sample bias, I focused strictly on high volume starting forwards, So I set up a minimum volume threshold and filters requiring a minimum playing time 15 full matches (90s >= 15.0) and more than 40 shots taken (Sh > 40)

SQL Query-

```sql
SELECT 
  Player,
  Nation,
  Squad,
  Comp AS League,
  `90s`,
  Sh as Total_Shots,
  `SoT%` AS Shot_Accuracy_Percentage,
  Gls AS Goals,
  G_Sh AS Goals_Per_Shot,
  G_SoT AS Goals_Per_Shot_On_Target
FROM 
  `abdu-project-2026.footystories_data.shootingstats`
WHERE
  Primary_Pos = 'FW'
  AND `90s` >= 15.0
  AND Sh > 40
ORDER BY 
  G_Sh DESC
LIMIT 10
```

Output-

<img width="1176" height="395" alt="obj1op" src="https://github.com/user-attachments/assets/eb143a60-0ce2-4481-8e2e-637f3dfb80ad" />


Key Findings-
*	Ermedin Demirović leads in the list among all qualifying starting forwards across the Top 5 European leagues. He boasts an impressive 0.27 conversion rate while also maintaining 53% shot accuracy, meaning over half of the shots he has taken hit the goal target.
*	Pavel Šulc, despite having a lower shot accuracy of 40.9%, has the highest goals per shot on target with a staggering 61% conversion rate, showing his lethal finishing ability when his shots are target.
*	Harry Kane stands out as an extremely high volume striker, despite taking nearly double the average shots of other players in the list and still maintaining a conversion rate of 0.22, shows his world class finishing capability.
*	The presence of 2 Barcelona players on the list, Ferran Torres and Robert Lewandowski, shows exceptional efficiency in Barca’s frontline, supported with high quality playmakers like Lamine Yamal, Raphinha and Pedri.
*	João Pedro being on the list supports his rightful individual achievement he earned where he was named Chelsea’s Men’s Player of the Season. 


## Objective 2 

**Best Playmakers and Creative Players**

To examine the top creative playmakers and contributers for the team, The table standardstats will be used as it consists of goal contribution metrics. The analysis here focused on Goals, Assists and Goal Contributions Per 90 Minutes.

I have applied filters of Primary position being limited to only MF and a minimum playing time of 15 full matches (90s >= 15.0)

Another important thing to note is although it was specifically mentioned for the query to be limited to only MF (Midfield) filter. The Primary_Pos “MF” included players who operate as central and wide attacking playmakers. In modern tactically fluid football, Wide attacking midfielders and wingers are considered as midfielders while operating as primary chance creators. As the objective specifically seeks offensive capabilities of players, the table will be populated by attacking playmakers than just central holding or defensive midfielders.

SQL Query-

```sql
SELECT
  Player,
  Nation,
  Squad,
  Comp AS League,
  `90s`,
  Gls AS Goals,
  Ast AS Assists,
  `G+A` AS Goal_Contributions,
  `G+A_90` AS Goal_Contributions_Per_90_Mins
FROM
  `abdu-project-2026.footystories_data.standardstats`
WHERE
  Primary_Pos = 'MF'
  AND `90s` >= 15.0
ORDER BY
  `G+A_90` DESC
LIMIT 10
```

Output-

<img width="1158" height="442" alt="obj2op" src="https://github.com/user-attachments/assets/77060b28-16b4-456f-b887-8fcb3f679f59" />

Key Findings-
*	Michael Olise tops the list among all the top 10 playmakers here with an extraordinary stat of 1.32 goal contributions per 90 minutes. He finished off the season with 34 goals contributions (15 goals + 19 assists) which is an exceptional stat for a natural playmaker. He also outperforms the average goal contribution per 90 minutes among the list(which is 0.94 as shown in the query below) by 40%, solidifying his position as the most impactful overall playmaker in the season.

```sql
SELECT 
  ROUND(AVG(`G+A_90`),2) AS Average_Goals_Contributions_Per_90_Minutes
FROM
  ( SELECT
      `G+A_90`
    FROM
      `abdu-project-2026.footystories_data.standardstats`
    WHERE
      Primary_Pos = 'MF'
      AND `90s` >= 15.0
    ORDER BY
      `G+A_90` DESC
    LIMIT 10
  )
```

<img width="655" height="557" alt="obj2q1" src="https://github.com/user-attachments/assets/a5b7c1af-b515-4ead-abbd-4ca8a9926c40" />

*	The presence of 2 Bayern Munich players, Luis Díaz and Michael Olise, topping the list side by side, signifies their elite stance by reaching double digits in both goals and assists, in the same campaign. This also supports Harry Kane’s statistics in the Objective 1 findings as a high volume striker. It goes to say how much of a deadly attacking trio - Olise, Kane, Diaz – is across European Championships. 
*	Barcelona featuring 3 players on the list, Yamal, Raphinha and Rashford, showcases the remarkable playmaking capability of Barca. This, along with Objective 1 findings which featured 2 barca players, highlights the attacking brilliance of Barcelona. 
*	Bruno Fernandes recorded the highest assists among the list, being the only player to get over 20 assists across Europe’s Top 5 Leagues, highlighting his role as a high volume playmaker for Manchester United.
*	Federico Dimarco stands out on the list as a unique entry, delivering 7 goals and 16 assists while operating as a wide midfield/wide back position from Inter Milan.



