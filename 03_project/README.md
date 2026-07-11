# Data Job Market Analysis
## Introduction
This project dives deep into the data job market using a large dataset of job postings to answer practical questions as follows:
- What skills are in demand?
- How does the demand shift over the year?
- What do these jobs pay?
- How does learning the optimal skills pay off?

The point of this project was to take everything that I learned through the exercises including cleaning, analysing, and visualising and apply it on a dataset that's messy and large enough to resemble real analytics work. The code used throughout this project is split across 5 notebooks, starting with an overview of the dataset to a fairly targeted answer to all the questions.

## Dataset
The dataset used across all 5 notebooks is a large collection of real data-related roles like data analyst, data engineer, data scientist which was pulled in through the `datasets` library. Each posting comes with various details like job location, country, posted date, salary, skills, and more. The dataset can also be accessed [here](https://huggingface.co/datasets/lukebarousse/data_jobs).

## Tools Used
- Python: Backbone of the project
- Pandas: For cleaning, merging, and grouping data.
- Matplotlib and Seaborn: For building visualisations.
- VS code: Where all the analysis took place.

## Data Cleaning
Before starting the analysis, each notebook starts with the same cleaning steps as the original dataset needed some reshaping to make it usable and reliable.

- I converted the `job_posted_date` column from a string into datetime format, so that the data can be grouped by month for trend analysis.
- The `job_skills` column came in as a string that looked like a list (for eg: `'[SQL, python]'`), so I used `ast.literal_eval()` function to convert each entry into an actual list. I also included a check for NA values to ensure that the code doesn't break upon encountering empty entries.
- For specific notebooks, I filtered the postings to specific countries and specific roles to ensure a focused analysis without mixing up with irrelevant entries.
- Once the `job_skills` column was converted into a list, I used the `.explode()` function to convert each skill into a separate row. This made it possible to group and count the frequency of skills instead of treating each job's associated skill list as an entire unit.
- For salary-related analysis, I dropped postings with missing salary values as there was nothing to analyse without those numbers.

## Analysis
1. [Exploratory data analysis](03_project/01_eda_intro.ipynb):
   
To get an idea of what's in the dataset, I started by narrowing in on business analyst jobs in the US and identified where these jobs are posted, which companies are hiring the most, and some basic conditions like whether the role is remote, if a degree is explicitly required, and whether health insurance is provided. This was done to get more comfortable with the dataset before proceeding with the hard questions.

### Insights
<img width="600" height="375" alt="image" src="https://github.com/user-attachments/assets/5ebdd2d8-c223-4c86-bb29-e73cda3b5e09" />


<img width="600" height="375" alt="image" src="https://github.com/user-attachments/assets/fa7f4a57-648c-4b4a-ad99-2e839945d9f1" />


<img width="551" height="186" alt="image" src="https://github.com/user-attachments/assets/5020c196-4ff9-491e-bc5d-818278183d37" />

- Remote postings indicated by "Anywhere" outnumber any single city, with Atlanta, Chicago, and Tampa leading the on-site listings.
- Only about 8% of postings are explicitly work-from-home and around 35% mention health insurance, so most listings leave benefits unstated.
- Only a small fraction of the listings require a degree, which indicates that the job market is more accessible.
- The companies that hire the most are staffing agencies like Robert Half and Dice, not direct employers.

2. [Skill demand](03_project/02_skill_demand.ipynb):
   
For this analysis, I looked into which skills show up the most for the top 3 data jobs- data analyst, data scientist, and data engineer. I did this by exploding out the skills column and calculating what percentage of postings for each role mention each skill. This was helpful in highlighting the differences between the three jobs.

### Insights
<img width="700" height="500" alt="image" src="https://github.com/user-attachments/assets/aa0df546-e922-4b66-ae58-d88c8a89d8ca" />

- SQL is the one skill that shows up consistently across the 3 data jobs, while the rest of the skills diverge sharply.
- Data Analyst roles lean on skills like Excel and Tableau, Data engineer roles require cloud and pipeline tools like AWS and Spark, and Data scientists lean on Python and R.
- This shows that there isn't a single universal skillset across data roles, ultimately depending on the track that you are aiming for.

3. [Skill trends](03_project/03_skill_trends.ipynb):

Demand for skills is not static, so this notebook analyses how the demand for top skills required for business analyst jobs change through the year, by creating a pivot table indexed by month. This can help us identify if the demand for a skill is steady, increasing, or diminishing over the year.

### Insights
<img width="623" height="464" alt="image" src="https://github.com/user-attachments/assets/aa50094e-bf2e-4aca-8882-4dfa5c930d13" />

- The demand for top skills remained relatively stable, with Excel and SQL holding the top spots almost every month.
- Excel started strong, peaking early in the year, then drifted downward before rising again towards December.
- Tableau followed a similar downward pattern over the year, while Python and Power BI stayed clustered near the bottom the whole time.
- This shows that the demand for the top skills isn't flat and changes periodically. So, it's worth rechecking the numbers periodically to understand what's in demand and how to take advantage of the pattern.

4. [Salary analysis](03_project/04_salary_analysis.ipynb):

This notebook shifts from "what are the requirements?" to "what does the job pay?". I compared salary distributions across the top 6 most posted jobs in the US and narrowed down to data analyst roles to compare the skills that pay the most against skills that are demanded the most, which as it turns out, aren't the same skills.

### Insights
<img width="717" height="457" alt="image" src="https://github.com/user-attachments/assets/9077c913-94ec-4406-ade2-6231b4bd94b1" />

<img width="624" height="463" alt="image" src="https://github.com/user-attachments/assets/5b39435f-15bc-496a-a395-fe30b332f35b" />

- Seniority and role type clearly drive salary. As we can see, data engineer and data scientists are paid more than data analysts. And, senior titles sit well above the non-senior counterparts across each role type.
- Upon focusing on data analyst jobs, I saw that the top paid skills are rare and specialised tools rather than basic foundational tools. They also barely overlap with the in-demand skills which are basic routine tools like SQL and Excel.
- This tells us that well paid and most requested skills pull in different directions. The skills that guarantee you interviews do not necessarily come with high salaries and vice-versa.

5. [Optimal skills](03_project/05_optimal_skills.ipynb):

The final analysis pulls the demand and salary aspects together. For data analyst jobs, I plotted the skills that are requested the most against their associated median salaries. I also color coded the skills according to their technology stack (like analyst tools, programming, cloud etc.). This was done to identify the skills that are well paid as well as in demand, and hence worth-learning to stand out well in the job market.

### Insights
<img width="629" height="470" alt="image" src="https://github.com/user-attachments/assets/783d469a-3282-40da-baa9-5a047f107ad2" />

- Python stood out as the most optimal skill which is solidly in demand as well as near the top of the pay skill.
- Tools like Excel and Word were common but paid less, and niche tools like Oracle paid well but were rarely requested.

## Conclusion











