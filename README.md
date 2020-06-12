# Stack Overflow 2019 Survey Analysis: The Data Scientists Tribe
### Who are they? What do they know? Do they know things? Let's Find Out!
<br>

## Motivation
The motivation behind this analysis is to gain more insights about the role of a Data Scientist and how it compares to other developers. As it is a relatively new role compared to others, there is often no clear understanding of what the job of a data scientist involves or what the background of a data scientist is, a fact that is reflected in the job description in many job postings asking for a data scientist. In addition, we would like to compare the data scientists with the other developer roles in terms of women representation in the field. Finally, we would like to see if data scientists are actually paid more than other developers and what correlates with a higher salary for a data scientist.
<br>

## Dataset

The dataset is made publicly available by Stack Overflow [here](https://insights.stackoverflow.com/survey).

## Development
The analysis was conducted using Python 3.7.7. In order to run the notebook, the packages that need to be installed are :
`numpy`, `pandas`, `matplotlib`, `seaborn` and `sklearn` 

## Overview

So we are asking the data:

###  QUESTION 1. What is the educational background of data scientists and how is it different from developers in general?
- Do more data scientists have degrees higher than a Bachelor's degree (Master's or PhDs) compared to other developers?
- Are there more data scientists coming from a non-CS background than other developers? 

We expect that there are more data scientists who have completed a Master's or a Ph.D. degree than developers in general and that more people in data science have majors other than computer science and software engineering than developers in general

### QUESTION 2. Is the gender gap smaller in data scientists than in other developer roles?
- Are data scientists doing better in terms of gender balance in the workspace?

The developer's word is still very male-dominated. Maybe data scientists as a relatively new role are doing a bit better in terms of gender balance.

### QUESTION 3. Are data scientists paid more than other developers? What characteristics of a data scientist correlate with a higher salary?
- Do data scientists get paid more than other roles? Compare each salary vs years of professional coding experience for each role.
- How does the level of education correlate with salary? Does a Ph.D. pay more?
- Does a software engineering background leads to a higher salary for data scientists compared to other educational backgrounds?
- Which combination of role titles gets paid more? What company size pays data scientists more?

We expect that Data Scientists are among the highest-paid role.

## Methodology

- For the scope of this analysis, we are only interested in professional developers. Therefore I exluded from the dataset the
respondents who are currelntly students, which is about 1/4 of the respondents.
- For Question 1, data scientists were compared to the average of all developers.
- For Question 2, we compared the ratio of the respondent who identified as men to those identified as women, leaving out other gender options. Another option,
could be to compare the ration of those who identify as men to those who not.
- For Question 2 and 3,  the subset `["Data Scientist", "DevOps Specialist", "Full-stack Developer", "Front-End Developer",
"Site Reliability Engineer", "Designer", "Mobile Developer", "System Administrator","Data Engineer", "Data Analyst"]`  
was selected to illustrate the differences among different developer roles, although more developer roles were available in the dataset.
- For Question 3, we used the column `ConvertedComp` as salary, which is the `Salary converted to annual USD salaries using the exchange rate on 
2019-02-01, assuming 12 working months and 50 working weeks.`, provided by the dataset.
we removed columns with NaNs in the `ConvertedComp` and `YearsCodePro` columns.
- For Question 3, the subset `['ConvertedComp','YearsCodePro','Country','DevType','OrgSize','EdLevel','UndergradMajor',
'Hobbyist','OpenSourcer']` was selected to explore correlations with salary.
- For Question 3, as the distribution of salary was severely skewed to the right due to outliers on the high-end spectrum
of the salary, we selected a maximum threshold of 300k USD and removed the top salaries, which corresponded to the top 7% of salaries.
Also all rows with zero salaries were removed. Other options would be to use the 95th quantile as threshold, replace outliers with the
threshold instead of removing them or use a larger minimum threshold.
- For Question 3, a LinearRegression model was used to explore the correlations between salary and different features.

## Summary


Overall, we gained some very interesting insights about data scientists:

### Educational background

#### Data Scientists have a different educational background compared to other developer roles.
- Regarding the highest level of formal education obtained, **39% of Data Scientists have completed a Master's or a Ph.D. degree** compared to **28%** of the developers in general.
- Regarding the undergraduate major, **48% of Data Scientists have completed a Computer Science or Software Engineering related degree** compared to **61%** of the developers in general.
- There is no difference between data scientists and other developers regarding other types of non-degree education that they have participated in.


### Gender gap

#### Data Scientists are one of the most gender-balanced developers, but there is still a long way to go.
- Only **8%** of all professional developers and **8.3% of Data Scientists identified as women**. There was a big gender gap in all developer roles.
- **Front-end Developers**, as well as **Data Scientists, had the best ratio of men to women**. Sadly this was that a data scientist is 12 times more likely to be a man than a woman. 
- The developer roles with the **least representation of female developers** were **DevOps Specialists and System Administrators** with a ratio of around **30 men to one woman**.

### Salary

#### Data Scientists are paid more than other developer roles
- In absolute terms, the median **global annual salary of data scientists is 66k USD** while the median for all developers is **58.5k USD**.
- Overall, data scientists are **one of the top-earning roles**, after SREs, DevOps, and Data Engineers.
- Also, **among developers with the least average professional experience, data scientists were the highest-paid!**
- Data Scientist was also the **second highest paying role over all the different experience levels**

#### Salary correlations
- The top correlated feature with salary was the **country of residence**, where countries like the USA, Switzerland, UK, Canada, Australia, Israel, and Denmark have a positive correlation, and others like Russia and India were negatively correlated.
- There is a positive correlation between a **doctoral degree** (Ph.D., Ed.D, etc.) and a high salary for data scientists. 
- On the other hand, when the data scientist role is combined with that of an **academic researcher**, there is a negative correlation. So, **a Ph.D. may pay more.. as long as you finish it!**
- Working for **organizations with more than 10k employees** or working as a **freelancer** was positively correlated to salary. So, **go big..or go home!**


## Future improvements

Although the results of the Stackoverflow 2020 Survey are [out](https://insights.stackoverflow.com/survey/2020), the dataset is not yet available, so the dataset 2019 was used. This reflects trends in the salary of 2 or more years ago.
In the future, we could use the most recent dataset, as well as incorporate data from previous years to explore overall trends.

In the future, I would like to try different algorithms to predict salary. Also, it would be interesting to explore the relation of salary to more features, like the languages, tools, and technologies a data scientist uses.
