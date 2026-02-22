# Panic_Attack-
The purpose of this project is to see if panic severity across age group and within a population is determined by factors such as sleep hours, lifestyle behaviours, exercising, and medical history.

### Table of Content
- [Data Sources](Data-Sources)

- [Dataset Summary](Dataset-Summary)

### Data Sources
The dataset used for this analysis is the "panic_attack_dataset.csv" which was from an online source.

### Dataset Summary

There population size is 1,200. and the distribution are Young youth (41.5%), Youth (33.33%) , Middle age(15.08%) and Elderly 10.08% 
The gender distribution is 45.75 Female, 44.75% Male and 9.5% Binary. The average age of the dataset is 41.


### Tools
- Excel : Data Cleaning 
- SQL : Analysis
- PowerBI : Reporting 

### Exploratory Data Analysis

The dataset was explored to answer questions such as : 
1. How frequent are panic attacks across the dataset?
2. Does exercise affect panic attack frequency?
3. Does high panic score or heart rate  affect the frequency of panic attack?
4. What is the relationship between lifestyle behaviours and panic severity?
5. What is the Panic Difference?

### Data Analysis

```EXCEL```

a. Null values were checked and removed.

b. Data types were standadized across the columns.

c. Outliers were checked and validated to be necessary or removed. 

```POWERBI```


a. DATA GROUPS: Age, Alcohol, Exercise, Caffeine, Smokers Group were created for analysis. 

E.g 

Age_Group = 
SWITCH(
    TRUE(),
panic_attack_dataset[Age]>=18 && panic_attack_dataset[Age]<=24,"Youth (18-24)",
panic_attack_dataset[Age]>=25 && panic_attack_dataset[Age]<=44,"Young Youth (25-44)",
panic_attack_dataset[Age]>=45 && panic_attack_dataset[Age]<=59,"Middle Age (45-59)",
panic_attack_dataset[Age]>=60 && panic_attack_dataset[Age]<=74,"Elderly (60-74)",
panic_attack_dataset[Age]>75,"Seniors (75+)"
)


Exercise Group = 
SWITCH(
    TRUE(),
    panic_attack_dataset[Exercise_Frequency] <=1, "Low Exercise(0-1days)",
    panic_attack_dataset[Exercise_Frequency] >=4, "High Exercise (4-6days)",
    "Medium Exercise (2-3days)"
)


Panic Score Diff = 
VAR LowExercise =
    CALCULATE(
        [Avg Panic Score],
        panic_attack_dataset[Exercise_Frequency] <= 1
    )
VAR HighExercise =
    CALCULATE(
        [Avg Panic Score],
        panic_attack_dataset[Exercise_Frequency] >= 4
    )
RETURN
LowExercise - HighExercise


Avg Age = 
AVERAGE(panic_attack_dataset[Age])


### Results/Findings

1. Most of the people have high Panic attack records which averagely means 4 episodes per week

2. The relationship is slightly weak. This means more exercise is associated with slightly lower panic frequency. 
3. Panic score increases and heart rate increases. This is a positive correlation 

4. 

a. Using average values, individuals in the high caffeine intake group consistently exhibit higher panic scores across age groups compared to those with low or moderate caffeine intake, indicating a strong positive association between caffeine consumption and panic severity.

b. The relationship between alcohol consumption and panic duration appears weak,While heavy drinkers show a slight tendency toward longer panic episodes, alcohol intake alone does not strongly predict panic duration.

5. Panic Difference level measures numerically if exercise reflects on Panic scores severity

i. Positive value = Low exercise group has higher panic scores

ii. Negative value = High exercise group has higher panic scores

### Recommendations
1. Promote physical activities as part of preventive mental health strategy
2. Medication alone does not seem to panic sevrity, it can be combined with other preventitve interventions. 
3. Sleep optimization and recommendation to panic attack patients can be effective. 
4. Caffeine intake can be modified or controlled by the patients.
   
### Limitations
1. The Dataset was a record of 1200 rows, this is considered a small population for analysis of such social influence

