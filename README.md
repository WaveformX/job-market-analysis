# job-market-analysis
📊 Job market analysis for Data Analysts using Python, API data, and skill extraction

# 📊 Job Market Analysis for Data Analysts

## 📌 Overview
This project analyzes real job postings for Data Analyst roles using the Adzuna API.  
The goal is to identify the most in-demand skills and explore job market trends using real-world data.

---

## 🔧 Project Workflow
1. Data Collection  
   - Fetched job postings using REST API (Adzuna)
   - Implemented multi-page data extraction in Python  

2. Data Cleaning  
   - Removed duplicates and missing values  
   - Standardized job data using Pandas  

3. Skill Extraction  
   - Extracted key skills from job descriptions:
     - Python
     - SQL
     - Excel  

4. Data Analysis & Visualization  
   - Counted skill frequency  
   - Visualized demand using Matplotlib  

---

## 📈 Key Insights
- Python and SQL are the most requested skills in job postings  
- Excel remains relevant but less dominant  
- Real-world job data contains inconsistencies and requires cleaning  

---

## 🛠️ Tech Stack
- Python  
- Pandas  
- Requests  
- Matplotlib  
- REST API (Adzuna)

---

## 🚀 How to Run
```bash
pip install -r requirements.txt
python main.py
