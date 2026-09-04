# web-scraping-eda-project

# GitHub Trending Repository Analysis

### A Data-Driven Study of Developer Traction Across Repository Categories

An end-to-end **Web Scraping, Exploratory Data Analysis, Statistical Analysis, and Data Insights** project that analyzes GitHub trending repositories across multiple technology categories and programming languages.

The project uses GitHub repository **Stars as the primary popularity metric** to investigate developer traction, category-level differences, programming-language distributions, repository naming patterns, and statistically significant relationships within the dataset.

---

## 📌 Project Overview

GitHub contains a continuously evolving ecosystem of repositories across thousands of technologies, frameworks, and development domains. Manually monitoring this ecosystem to identify which categories and technologies are gaining developer attention is difficult to scale.

This project addresses that challenge by building a data-driven pipeline that:

* Scrapes GitHub trending repository information
* Organizes repositories into technology categories and topics
* Cleans and validates the collected data
* Detects and analyzes statistical outliers
* Performs univariate, bivariate, and multivariate EDA
* Engineers additional analytical features
* Analyzes programming-language distributions
* Compares repository popularity across categories
* Examines correlations between repository characteristics and Stars
* Applies statistical hypothesis tests
* Converts analytical findings into actionable insights

The overall workflow follows:

**Data Collection → Data Cleaning → Validation → EDA → Feature Engineering → Statistical Analysis → Insights**

---

## 🎯 Business Problem

The volume of repositories appearing in GitHub's trending ecosystem makes manual monitoring impractical.

The core business questions addressed by this project are:

1. Which technology categories receive the highest developer traction?
2. Which programming languages are most frequently represented?
3. How does repository popularity vary across categories?
4. Are repository Stars heavily affected by extreme outliers?
5. Do repository naming characteristics have a meaningful relationship with popularity?
6. Is the difference in popularity between programming languages statistically significant?
7. Is repository category associated with programming-language choice?
8. Are differences in repository popularity across categories statistically significant?

The objective is to replace subjective assumptions with **data-backed evidence**.

---

## 🎯 Project Objectives

### 1. Data Collection

Scrape GitHub repositories and capture repository-level information with **Stars as the core popularity metric**.

### 2. Data Cleaning

Prepare the scraped dataset by handling missing values, duplicate records, inconsistent values, invalid numerical values, and formatting issues.

### 3. Exploratory Data Analysis

Perform:

* Univariate Analysis
* Bivariate Analysis
* Multivariate Analysis
* Distribution Analysis
* Category Analysis
* Programming Language Analysis
* Correlation Analysis

### 4. Statistical Validation

Use statistical hypothesis testing to determine whether observed differences and relationships are statistically significant.

### 5. Business Insights

Translate the analytical results into practical recommendations for technology-focused training and curriculum planning.

---

## 🛠️ Technology Stack

| Area                    | Technologies            |
| ----------------------- | ----------------------- |
| Programming Language    | Python                  |
| Web Scraping            | Requests, BeautifulSoup |
| Data Manipulation       | Pandas, NumPy           |
| Visualization           | Matplotlib, Seaborn     |
| Statistical Analysis    | SciPy                   |
| Development Environment | Jupyter Notebook        |
| Data Format             | CSV                     |

The project uses a Python-centric analytics pipeline combining web scraping, data processing, visualization, and statistical testing.

---

# 🔄 Data Pipeline

```text
GitHub Trending
       ↓
Web Scraping
       ↓
Raw Repository Data
       ↓
Data Cleaning
       ↓
Data Validation
       ↓
Feature Engineering
       ↓
Exploratory Data Analysis
       ↓
Statistical Analysis
       ↓
Insights & Recommendations
```

### Web Scraping

The collection pipeline uses:

* `Requests` for HTTP requests
* `BeautifulSoup` for HTML parsing
* Custom parsing logic for GitHub Star counts
* Automated category/topic loops
* Error handling for unsuccessful HTTP responses

The Star parser converts abbreviated values such as `k` and `m` into usable numerical values for analysis.

---

# 📊 Dataset

After data preparation and validation, the project contains:

* **781 validated repository records**
* **7 primary attributes**
* Missing values addressed
* Duplicate records removed
* Numerical values validated

The dataset focuses on repository-level information such as:

* Category
* Topic
* Repository
* Owner
* Repository URL
* Programming Language
* Stars

The final dataset was validated before proceeding to exploratory analysis.

---

# 🧹 Data Cleaning & Validation

The notebook performs multiple data-quality checks before analysis.

### Missing Values

Missing programming-language values are handled during preprocessing.

### Duplicate Records

Duplicate records are checked and removed where necessary to prevent repository counts and popularity statistics from being distorted.

### Numerical Validation

Repository Stars are converted into numeric values and invalid numerical entries are identified.

### Category & Language Consistency

String values are standardized by removing unnecessary whitespace and checking unique language values.

### Data Validation

The final dataset is validated using:

* `info()`
* Missing-value checks
* Duplicate checks
* Descriptive statistics
* Data-type validation
* Invalid-value checks

---

# 📈 Exploratory Data Analysis

## 1. Repository Star Distribution

The Star distribution is **strongly right-skewed**.

Most repositories are concentrated at relatively low Star counts, while a small number of highly successful repositories receive exceptionally large numbers of Stars.

This creates substantial variance and makes outlier analysis important.

The project applies a **Log10 transformation**:

```python
Log_Stars = log10(Stars + 1)
```

This transformation helps compress the extreme range of the Star distribution and makes the variable more suitable for visual and statistical analysis.

### Star Distribution

| Star Range | Repository Count |
| ---------- | ---------------: |
| 0–1K       |              520 |
| 1K–5K      |              165 |
| 5K–20K     |               62 |
| 20K–50K    |               24 |
| 50K+       |               10 |

---

# 💻 Programming Language Analysis

The analysis identifies the most frequently represented programming languages among the collected repositories.

### Top Programming Languages

| Language   | Repository Count |
| ---------- | ---------------: |
| TypeScript |              210 |
| Python     |              178 |
| JavaScript |              156 |
| Go         |               88 |
| Rust       |               64 |
| Java       |               52 |
| C++        |               41 |
| Ruby       |               33 |
| PHP        |               27 |
| Other      |               85 |

**TypeScript, Python, and JavaScript** form the largest language groups in the analyzed dataset.

---

# 🏆 Category-Level Popularity

Repository popularity was compared across technology categories using GitHub Stars.

### Average Stars by Category

| Category        | Average Stars |
| --------------- | ------------: |
| Web Development |           42K |
| Data Science    |           35K |
| Mobile          |           22K |
| DevOps          |           18K |
| UI/UX           |            9K |
| Cybersecurity   |            7K |

**Web Development** shows the highest average Star engagement, followed by **Data Science**.

The analysis also uses boxplots to examine the distribution and dispersion of Stars across categories.

---

# 🔬 Multivariate Analysis

Additional features were engineered to investigate whether repository characteristics are associated with popularity.

### Engineered Features

* `Log_Stars`
* `Repo_Name_Length`
* `Owner_Name_Length`
* `Repo_Word_Count`

A pairplot/scatter-matrix was used to visually examine relationships between these variables.

The analysis shows a strong relationship between repository name length and repository word count, but repository name length does **not** show a meaningful linear relationship with final Star count.

---

# 🔗 Correlation Analysis

The correlation matrix produced the following key relationships:

| Variable Pair                       | Correlation |
| ----------------------------------- | ----------: |
| Repository Name Length ↔ Stars      |       -0.08 |
| Word Count ↔ Stars                  |       -0.05 |
| Owner Name Length ↔ Stars           |       -0.02 |
| Repository Name Length ↔ Word Count |        0.87 |

### Key Finding

The **0.87 correlation** between repository name length and word count is strong, as expected.

However, repository name length has an approximately **-0.08 correlation with Stars**, indicating that repository naming length alone is not a useful predictor of repository popularity.

Owner-name length also shows an approximately zero relationship with Stars.

---

# 🧪 Statistical Hypothesis Testing

To move beyond descriptive analysis, the project applies statistical hypothesis testing.

## Independent T-Test

An independent T-test compares the Star distributions of:

**Python repositories vs. Java repositories**

The analysis reports a statistically significant difference at:

**p < 0.05**

This indicates that the observed difference in the analyzed Python and Java repository Star distributions is statistically significant under the test performed.

---

## ANOVA

One-way ANOVA is used to compare repository Star distributions across technology categories.

**Result: p < 0.05**

This provides statistical evidence that the observed differences in repository popularity across the analyzed categories are not attributable solely to random variation under the assumptions of the test.

---

## Chi-Square Test

A Chi-Square test of independence examines the relationship between:

**Repository Category × Programming Language**

**Result: p < 0.05**

This indicates a statistically significant association between repository category and programming-language choice in the analyzed dataset.

---

# 💡 Key Insights

### 1. Web Development Leads Developer Traction

Web Development repositories demonstrate the highest average Star engagement among the analyzed categories.

### 2. Data Science Shows Strong Developer Interest

Data Science ranks second in average Star engagement, highlighting its strong representation in the trending ecosystem.

### 3. TypeScript, Python & JavaScript Dominate

These three languages account for the largest repository volumes in the analyzed dataset.

### 4. GitHub Popularity Is Highly Skewed

A small number of breakout repositories accumulate exceptionally high Star counts, creating significant statistical dispersion.

### 5. Repository Naming Does Not Explain Popularity

Repository name length and owner-name length show very weak relationships with Stars.

### 6. Category Differences Are Statistically Significant

ANOVA indicates statistically significant variation in repository popularity across the analyzed categories.

### 7. Category and Language Are Associated

The Chi-Square test indicates a statistically significant association between repository category and programming-language selection.

---

# 📌 Business Recommendations

Based on the observed repository trends, the project proposes:

### Technology Curriculum Prioritization

Increase emphasis on:

* Web Development
* Data Science
* TypeScript
* Python
* JavaScript

These areas demonstrate strong representation and developer traction within the analyzed GitHub dataset.

### Dynamic Trend Monitoring

Standardize the scraping pipeline so emerging technologies and frameworks can be monitored continuously.

### Modernize Student Projects

Encourage capstone projects that use contemporary technologies and real-world codebases.

### Evidence-Based Resource Allocation

Use repository trend data as one input for determining which technology modules deserve greater training and infrastructure investment.

The presentation specifically proposes standardizing the scraping pipeline, updating capstone projects, and reallocating resources based on observed technology traction.

---

# 📁 Repository Structure

```text
GitHub-Trending-Repository-Analysis/
│
├── EDA GITHUBmain .ipynb
├── github_topics_scraped.csv
├── Innomatics_GitHub_Trending_Repos_18slides.pptx
└── README.md
```

### Files

**`EDA GITHUBmain .ipynb`**
Complete Python notebook containing the scraping workflow, data preparation, EDA, feature engineering, visualizations, correlation analysis, and hypothesis testing.

**`github_topics_scraped.csv`**
Processed repository dataset used for analysis.

**`Innomatics_GitHub_Trending_Repos_18slides.pptx`**
Project presentation containing the methodology, visualizations, statistical findings, business insights, and recommendations.

---

# 🚀 How to Run the Project

### 1. Clone the repository

```bash
git clone <YOUR-GITHUB-REPOSITORY-URL>
cd GitHub-Trending-Repository-Analysis
```

### 2. Install dependencies

```bash
pip install requests pandas numpy beautifulsoup4 tqdm matplotlib seaborn scipy jupyter
```

### 3. Launch Jupyter Notebook

```bash
jupyter notebook
```

### 4. Open

```text
EDA GITHUBmain .ipynb
```

### 5. Run the notebook

Execute the notebook cells sequentially to reproduce the data preparation, analysis, visualizations, and statistical tests.

---

# 📊 Analytical Techniques Used

### Data Collection

* Web Scraping
* HTML Parsing
* Automated Category Collection
* Custom Star Parsing
* Error Handling

### Data Preparation

* Missing-Value Handling
* Duplicate Detection
* Data-Type Conversion
* String Standardization
* Invalid-Value Detection
* Data Validation
* IQR-Based Outlier Analysis

### EDA

* Univariate Analysis
* Bivariate Analysis
* Multivariate Analysis
* Distribution Analysis
* Boxplots
* Histograms
* Pairplots
* Heatmaps
* Pivot Tables

### Statistics

* Mean
* Median
* Mode
* Standard Deviation
* Variance
* Covariance
* Correlation
* Independent T-Test
* One-Way ANOVA
* Chi-Square Test

---

# 🎓 Skills Demonstrated

This project demonstrates practical experience in:

* Python for Data Analytics
* Web Scraping
* Data Collection Automation
* Data Cleaning
* Exploratory Data Analysis
* Statistical Analysis
* Hypothesis Testing
* Feature Engineering
* Data Visualization
* Business Insight Generation
* Analytical Storytelling

---

# 🧠 Project Takeaway

This project demonstrates how raw web data can be transformed into actionable intelligence through a structured analytics workflow.

Rather than simply identifying which repositories are popular, the analysis investigates **why popularity patterns differ**, whether observed differences are statistically significant, and what those patterns can imply for technology adoption and training decisions.

The final workflow connects:

**Web Data → Clean Data → Statistical Evidence → Business Insight → Strategic Decision**

The project demonstrates the principle of using evidence instead of assumptions to understand technology trends.

---

# 👨‍💻 Project Context

**Project:** GitHub Trending Repository Analysis
**Organization:** Innomatics Research Labs
**Domain:** Data Science / Data Analytics
**Focus:** Web Scraping · EDA · Statistics · Technology Trend Analysis

---

## ⭐ If You Find This Project Useful

Feel free to explore the notebook, review the analysis, and use the methodology as a reference for GitHub trend analysis and data-driven technology research.

**From Data to Decisions.**
