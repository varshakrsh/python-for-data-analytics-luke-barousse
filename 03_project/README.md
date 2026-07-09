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

## Data Cleaning:
Before starting the analysis, each notebook starts with the same cleaning steps as the original dataset needed some reshaping to make it usable and reliable.

- I converted the `job_posted_date` column from a string into datetime format, so that the data can be grouped by month for trend analysis.
- The `job_skills` column came in as a string that looked like a list (for eg: `'[SQL, python]'`), so I used `ast.literal_eval()` function to convert each entry into an actual list. I also included a check for NA values to ensure that the code doesn't break upon encountering empty entries.
- For specific notebooks, I filtered the postings to specific countries and specific roles to ensure a focused analysis without mixing up with irrelevant entries.
- Once the `job_skills` column was converted into a list, I used the `.explode()` function to convert each skill into a separate row. This made it possible to group and count the frequency of skills instead of treating each job's associated skill list as an entire unit.
- For salary-related analysis, I dropped postings with missing salary values as there was nothing to analyse without those numbers.


