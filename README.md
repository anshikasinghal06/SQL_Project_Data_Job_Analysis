# SQL Project: Data Job Market Analysis

An end-to-end SQL analytics project analyzing **787,000+ real job postings** to uncover which Data Analyst roles pay the most, which skills are most in demand, and where high salaries and high demand overlap — using **PostgreSQL and VS Code** to move from raw data to career-focused insights.

## Skills Demonstrated

- **SQL (PostgreSQL):** aggregate functions, JOINs across multiple tables, subqueries, CTEs (`WITH` clauses), date functions (`EXTRACT`), conditional logic (`CASE WHEN`), `UNION ALL` for combining datasets
- **Database Design:** understanding and navigating a star schema with fact and dimension tables connected via a bridge table
- **Business Analysis:** translating open-ended career questions into structured SQL queries and actionable insights
- **Git & GitHub:** version control and project sharing via command line

## Project Overview

This project analyzes the 2023 data analyst job market using real job posting data from [Luke Barousse's SQL Course](https://lukebarousse.com/sql). The goal is to answer five key career questions — from which companies pay the most to which skills offer the best return on learning investment.

**Dataset:** 787,000+ job postings — job titles, salaries, locations, companies, schedule types, and required skills across 4 related tables (`job_postings_fact`, `company_dim`, `skills_job_dim`, `skills_dim`)

## Database Schema

```
job_postings_fact ──► skills_job_dim ──► skills_dim
       │                (bridge)
       ▼
  company_dim
```

---

## The Analysis

### 1. Top-Paying Data Analyst Jobs

**What this solves:** Identifies the highest-paying remote Data Analyst roles so job seekers know which companies and titles to target.

**Result:**

![Top Paying Jobs](image/1.Top-Paying%20Data%20Analyst%20Jobs.png)

**Breakdown:**
| Finding | Detail |
|---|---|
| Highest salary | $650,000 at Mantys |
| Salary range | $184,000 – $650,000 across top 10 roles |
| Schedule type | All Full-time remote positions |
| Top employers | Mantys, Meta, AT&T, Pinterest, SmartAsset |

- The salary gap between rank 1 ($650K) and rank 2 ($336K) is enormous — the top role is a true outlier
- **Meta and AT&T** appear in the top 3, showing large tech and telecom companies offer premium remote analyst pay
- **SmartAsset** appears twice, indicating it's a consistent high-payer for data roles

---

### 2. Skills Required for Top-Paying Jobs

**What this solves:** Reveals exactly which skills employers are paying the most for — so you know what to prioritize learning.

**Result:**

![Top Paying Job Skills](image/2.Skills%20Required%20for%20Top-Paying%20Jobs.png)

**Breakdown:**
- **SQL** is the most required skill, appearing across the highest-paying roles including AT&T and Pinterest
- **Python** follows closely — essential for roles at AT&T ($255K) and Pinterest ($232K)
- **AT&T's Associate Director role** requires the widest skill set: SQL, Python, R, Azure, Databricks, AWS, Pandas, PySpark, Jupyter, Excel, Tableau, Power BI, and PowerPoint
- **Cloud skills** (Azure, AWS, Databricks) appear in the highest-paying roles, confirming cloud knowledge boosts salary
- Visualization tools like **Tableau and Power BI** appear alongside core technical skills — analysts need both

---

### 3. Most In-Demand Skills for Data Analysts

**What this solves:** Shows which skills appear most frequently across ALL Data Analyst remote job postings — not just top-paying ones — revealing what the market broadly expects.

**Result:**

![Top Demanded Skills](image/3.Most%20In-Demand%20Skills%20for%20Data%20Analysts.png)

**Breakdown:**

| Skill    | Demand Count | What it tells us |
|----------|-------------|-----------------|
| SQL      | 7,291       | Non-negotiable foundation skill |
| Excel    | 4,611       | Still heavily used across industries |
| Python   | 4,330       | Programming is now a core analyst skill |
| Tableau  | 3,745       | Data visualization is expected |
| Power BI | 2,609       | Microsoft BI tool widely adopted |

- **SQL dominates** with nearly 2x the demand of the next skill — it is the single most important skill to master
- **Excel remains relevant** despite newer tools, especially in traditional industries
- **Python nearly matches Excel** — coding is no longer optional for analysts
- **Two visualization tools** (Tableau + Power BI) in the top 5 confirms that presenting data visually is a core expectation

---

### 4. Skills Associated with Higher Salaries

**What this solves:** Identifies which specific skills are linked to the highest average salaries — helping you understand which niche skills command a premium.

**Result:**

![Skills Based on Salary](image/4.Skills%20Associated%20with%20Higher%20Salaries.png)

**Breakdown:**
- **PySpark leads at $208,172** — Big Data processing skills are the highest paid in analytics
- **DevOps-adjacent tools** (Bitbucket $189K, GitLab $154K) show that analysts who understand engineering workflows earn significantly more
- **ML/AI tools** (DataRobot $155K, Jupyter $152K, Pandas $151K) confirm that data science-adjacent skills boost analyst salaries
- **Cloud and infrastructure** (Kubernetes $132K, Airflow $126K, GCP $122K) are increasingly expected at senior levels
- Traditional tools like **SQL and Excel** don't appear here — they're the baseline, not the differentiator for salary

---

### 5. Most Optimal Skills to Learn

**What this solves:** Combines demand AND salary to find the sweet spot — skills that appear frequently in job postings AND pay well. This is the most strategic query for career planning.

**Result:**

![Optimal Skills](image/5.Most%20Optimal%20Skills%20to%20Learn.png)

**Breakdown:**
- **Cloud platforms dominate the sweet spot** — Snowflake (37 jobs, $112K), Azure (34 jobs, $111K), AWS (32 jobs, $108K), BigQuery (13 jobs, $109K) all offer high demand AND high salary
- **Python (236 jobs, $101K) and R (148 jobs, $100K)** are the highest-demand skills overall — essential for any analyst role
- **Tableau (230 jobs, $99K)** is the go-to visualization tool — high demand and solid pay
- **Looker (49 jobs, $103K)** punches above its demand count in salary — worth learning for modern BI stacks
- **Go and Confluence** appear at the top by salary but have low demand counts — niche but lucrative

---

## What I Learned

This project pushed my SQL skills significantly further:

- **CTEs (`WITH` clauses)** — Writing clean, multi-step queries without nesting subqueries inside subqueries
- **Multi-table JOINs** — Navigating a star schema with a bridge table (`skills_job_dim`) connecting jobs to skills
- **Aggregate + Filter combination** — Using `HAVING` to filter after aggregation, not `WHERE`
- **`UNION ALL` for combining datasets** — Merging monthly job tables (Jan/Feb/Mar) into a single Q1 dataset
- **Date functions** — Using `EXTRACT(MONTH/QUARTER FROM date)` to filter by time periods
- **Real-world thinking** — Turning career questions into structured SQL and reading the results as business insights

---

## Key Insights Summary

| Question | Key Finding |
|---|---|
| Top-paying jobs | Remote DA roles pay up to $650,000; Meta, AT&T, SmartAsset are top payers |
| Skills for top pay | SQL (8/10 jobs), Python (7/10), Tableau (6/10) dominate top-paying roles |
| Most in-demand skills | SQL (7,291), Excel (4,611), Python (4,330) — these 3 are non-negotiable |
| Highest-paying skills | PySpark ($208K), Bitbucket ($189K), Couchbase ($160K) — niche skills pay premium |
| Most optimal to learn | Cloud platforms (Snowflake, Azure, AWS) + Python + Tableau = best ROI |

---

## Repository Structure

```
├── advance_sql/
│   └── practice problems and advanced queries
├── project_sql/
│   ├── 1_top_paying_jobs.sql
│   ├── 2_top_paying_job_skills.sql
│   ├── 3_top_demanded_skills.sql
│   ├── 4_skills_based_on_salary.sql
│   └── 5_optimal_skills.sql
├── sql_load/
│   └── database setup and table creation scripts
├── images/
│   └── query result screenshots
├── .gitignore
└── README.md
```

## How to Run This Project

1. Clone the repository:
   ```bash
   git clone https://github.com/anshikasinghal06/SQL_Project_Data_Job_Analysis.git
   ```

2. Set up PostgreSQL and create the database:
   ```bash
   psql -U postgres -f sql_load/1_create_database.sql
   psql -U postgres -f sql_load/2_create_tables.sql
   psql -U postgres -f sql_load/3_modify_tables.sql
   ```

3. Load the dataset from [lukeb.co/sql_project_csvs](https://lukeb.co/sql_project_csvs)

4. Open any `.sql` file from `project_sql/` in VS Code with the SQLTools extension connected to your PostgreSQL database and run the queries

