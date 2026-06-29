# Customer Personality Analysis - Data Cleaning & Preprocessing

## Project Overview
When dealing with real-world datasets, the raw information is rarely ready for immediate analysis. This project focuses on the essential first step of any data science workflow: **Data Cleaning and Preprocessing**. 

Using Python and the Pandas library, I took a messy, tab-separated raw marketing dataset and transformed it into a clean, structured, and reliable version ready for data analysis, business intelligence dashboards, or machine learning models.

---

## The Raw Data Challenges
Upon initial inspection of the `Customer marketing.csv` file, several structural and formatting issues were identified:
* **Incorrect Delimiter:** The dataset used tabs (`\t`) instead of commas, causing standard CSV readers to misalign the data columns.
* **Messy Column Headers:** Headers contained a mix of upper and lower cases, along with spaces that made coding cumbersome.
* **Missing Values:** The `income` column had blank records that needed logical handling.
* **Inconsistent Categorical Text:** Columns like `marital_status` and `education` contained redundant or fragmented categories (e.g., "YOLO", "Absurd", "Alone").
* **Flawed Data Types:** Date strings were formatted inconsistently, causing parsing errors because days and months were flipped across rows.

---

## Step-by-Step Data Cleaning Pipeline

Here is how I resolved these issues step-by-step in the Jupyter Notebook (`analysis.ipynb`):

### 1. Correcting the Layout & Headers
* Forced Pandas to read the tab-separated layout correctly by applying `sep='\t'`.
* Standardized all column headers to lowercase and replaced spaces with underscores (`snake_case`) for clean, uniform syntax.

### 2. Resolving Missing Values & Duplicates
* Discovered 24 missing values in the `income` column. Rather than deleting these records and losing valuable customer data, I filled them using the column's **median** value to keep the distribution realistic.
* Ran a check for identical duplicate rows across the entire dataset to eliminate any redundancy.

### 3. Standardizing Text Categories
* **Marital Status:** Grouped vague or chaotic entries like `Alone`, `YOLO`, and `Absurd` under a single, clean category: `Single`.
* **Education:** Streamlined five separate degree types into three intuitive tiers: `Undergraduate`, `Graduate`, and `Postgraduate`.

### 4. Fixing Date Formats
* Converted the `dt_customer` column from a generic text string into an actual `datetime64` framework, explicitly passing `dayfirst=True` to stop parsing crashes caused by regional date formats.

---

## Deliverables in This Repository
* **`Customer marketing.csv`**: The original, unedited dataset.
* **`analysis.ipynb`**: The step-by-step Python code walking through the entire cleaning process.
* **`cleaned_customer_personality.csv`**: The final, completely structured dataset ready for production.

---

## Key Takeaways
By completing this task, I gained practical experience in handling common data issues independently. Fixing data types, standardizing text inputs, and handling missing data points logically are critical safeguards—because the insights you get out of your charts are only as good as the data you put in.
