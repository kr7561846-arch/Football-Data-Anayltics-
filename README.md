#  Comprehensive Football Data Analysis
# A Multi-Dimensional Data Science Capstone Project

---

##  Project Overview

This capstone project presents a comprehensive, end-to-end data science analysis of professional football, covering player performance, fan engagement, market valuation, referee behavior, stadium attendance, and match dynamics. The project applies the full data science lifecycle - from raw data ingestion and cleaning through exploratory analysis, statistical testing, machine learning modeling, and interactive dashboard visualization.

The core motivation is to demonstrate how "data-driven decision making"can empower coaches, club management, scouts, and stakeholders with evidence-based insights by replacing intuition with measurable, reproducible intelligence.

> Tools Used: Python, MySQL, Microsoft Excel, Tableau, Scikit-Learn, Pandas, NumPy, Matplotlib, Seaborn

---

##  Repository Structure

```
 Football-Data-Analysis/
├──   Kumudha_football_project.ipynb         # Main analysis notebook (ML models, EDA, visualization)
├──  Capstone_project_cleaned_data.ipynb      # Data cleaning & preprocessing pipeline
├──  Capstone_Project.sql                    # MySQL database schema & queries
├──  capstone_excel.xlsx                      # Cleaned dataset (Excel format for Tableau)
├─   Kumudha1_Capstone_project.twbx          # Tableau workbook with interactive dashboards
├──  kumudhal_Capstone_project.pptx          # Full project presentation
└──  README.md
```

---

##  Objectives

- Analyze football data to uncover key success factors across 10 research domains
- Apply supervised and unsupervised machine learning to predict and segment player/match behavior
- Perform rigorous "statistical testing" (hypothesis testing, probability analysis, CLT)
- Build "interactive Tableau dashboards" for real-time stakeholder decision support
- Translate complex analytical findings into clear, actionable narratives

---

##  Research Domains Covered

| # | Domain | Key Question |

| 1 | Performance Analysis : Which positions and players contribute most to goals and assists? 
| 2 | Player Profile & Market Value : How do country strategies and positions affect market investment? 
| 3 | Team Comparison : How do home vs. away goals differ across seasons and clubs? 
| 4 | Attendance & Stadium Analysis : What drives fan engagement across stadiums and competition types? 
| 5 | Referee Analysis : Which referees show distinct disciplinary and match patterns? 
| 6 | Substitution Patterns : How do mid-match substitutions affect win/loss outcomes? 
| 7 | Event Analysis : When do goals, cards, and substitutions cluster within a match? 
| 8 | Competition Analysis : How do goal volumes differ across domestic vs. international competitions? 
| 9 | Player Attributes & Demographics : How do height, foot preference, and position correlate with performance? 
| 10 | Contract Management : When do player contracts expire and how does position affect timing? 

---

##  Tech Stack & Architecture

```
Raw Data (Excel/CSV)
        │
        ▼
┌─────────────────────┐
│  Data Cleaning      │  Python · Pandas · NumPy
│  & Preprocessing    │  (Capstone_project_cleaned_data.ipynb)
└────────┬────────────┘
         │
         ▼
┌─────────────────────┐
│  MySQL Database     │  Centralized storage, SQL queries,
│  (Structured Store) │  Python-SQL integration via SQLAlchemy
└────────┬────────────┘
         │
    ┌────┴────┐
    ▼         ▼
┌────────┐ ┌──────────────────────┐
│Tableau │ │  Python Analysis     │
│Dashbd  │ │  EDA · Stats · ML    │
│(.twbx) │ │  (Main Notebook)     │
└────────┘ └──────────────────────┘
```

---

##  Phase 1 - Data Cleaning & Preprocessing

The raw football dataset contained missing values, inconsistent formatting, non-standard encodings, and outliers across multiple tables. The cleaning pipeline:

- Handle missing values using domain-aware imputation strategies
- Removed duplicate records and resolved inconsistent player/club naming
- Standardized data types across numerical and categorical columns
- Applied feature engineering to derive new metrics (e.g., goals-per-match, contribution scores)
- Exported the final cleaned dataset to Excel (for Tableau) and MySQL (for structured querying)
- Connected Python to MySQL using SQLAlchemy for seamless pipeline integration

---

##  Phase 2-9 : Exploratory & Descriptive Analysis

### 1. Performance Analysis
Attacking players consistently outperform midfielders and defenders in goals and assists. Christian Pulisic emerged as the top performer overall. John Anthony Brooks led defenders, while Weston McKennie topped midfielders.

### 2. Player Profile & Market Value
- Countries differ in positional investment: USA invests across all three positions; England, Italy, Netherlands focus on specific roles; Germany concentrates on attack and defense.
- Midfielders attract the highest market investment due to tactical versatility — able to contribute to both attack and defense.
- Defenders have significantly lower market valuation compared to midfielders and attackers.

### 3. Team Comparison
- Home teams consistently scored more goals than away teams across seasons (2015-2016 trend confirmed).
- Real Madrid leads fan attendance (~80k), followed by FC Bayern Munich (~75k) and Tottenham Hotspur (~71k) - all significantly above the rest of the league.

### 4. Attendance & Stadium Analysis
- Santiago Bernabeu ranks #1 in average attendance, followed by Allianz Arena.
- Domestic league and international cup matches attract the highest fan turnout - indicating that competition format is a significant driver of audience engagement behavior.

### 5. Referee Analysis
- Felix Zwayer: most matches officiated, most yellow cards issued - consistent high-discipline approach.
- Michael Oliver : officiated matches with the highest average goals scored - suggesting a more permissive, fluid match-management style.

### 6. Substitution Patterns
- Substitutions increase the probability of winning compared to draw or loss.
- Christian Pulisic had the highest substitution impact: 700+ matches, 322 wins / 126 draws / 224 losses.
- John Anthony Brooks (defender) contributed to 65 wins out of 150 matches post-substitution.

### 7. Event Analysis
- Most substitutions occur in the last 20 minutes of matches (70-80th minute).
- Yellow cards peak in the early second half  players more aggressive after halftime.
- Goals are scored in regular 10-minute intervals throughout the match.
- Right-footed players dominate goals, cards and substitution events across all categories.

### 8. Competition Analysis
- Domestic league generates the highest total goals (1,361), driven by match frequency.
- Domestic cup: 251 goals | International cup: 105 goals.
- Individual match attendance is highest in international competitions despite fewer total goals.

### 9. Player Attributes & Demographics
- Defenders are the tallest group overall.
- Attackers show the widest range in both height and market value - high variability and highest upside.
- Midfielders show tight clustering in market value - consistent, predictable investment profile.

### 10. Contract Management
- Contract expirations peak in **2018 and 2019** across all positions.
- Attacking player contracts clustered heavily in 2018–2019; defenders showed peaks in 2013 and 2019.

---

##  Statistical Analysis

### Probability Analysis
- Calculated the probability that a player received a yellow card AND played as a substitute in the same match: 7.53%
- Demonstrated the Central Limit Theorem: sample mean approximates population mean when sample size ≥ 30, confirming the dataset's distributional properties.

### Hypothesis Test 1 - Home vs. Away Goals (t-test)
```
H₀: No significant difference in home vs. away goals per season
H₁: Significant difference exists

Test: Two-tailed t-test (population mean unknown, n < 30)
T-statistic: 0.2054 | P-value: 0.8381 | T-critical: 2.0106

Result: ACCEPT H₀ - no statistically significant difference found
```

### Hypothesis Test 2 - Player Scoring Rate (z-test)
```
H₀: Players score ≤ 0.5 goals per match
H₁: Players score > 0.5 goals per match (right-tailed)

Test: Z-test (population std = 0.8, known)
Z-statistic: -1.1859 | P-value: 0.1178 | Z-critical: 1.6449

Result: ACCEPT H₀ - insufficient evidence that players score > 0.5 goals/match on average
```

---

##  Machine Learning Models

### Model 1 - Logistic Regression (Yellow Card Prediction)
Question: Is a player's country of birth related to their likelihood of receiving a yellow card?

Features: Country of birth, position, foot preference, minutes played, competition type  
Target: Yellow card (binary)

| Metric | Score | Interpretation |
|--------|-------|----------------|
| ROC-AUC  | 0.776| Fairly strong - model ranks positive cases correctly 77.6% of the time |
| Accuracy | 0.70 | 70% correct predictions overall |
| Precision| 0.32 | Conservative in flagging yellow card risk |
| Recall | 0.75 | Captures 75% of actual yellow card events |
| F1 Score | 0.45 | Moderate balance; recall-heavy model |

Pipeline: Data scaling → train/test split → Logistic Regression → ROC evaluation

---

### Model 2 - Linear & Multiple Regression (Player Height Prediction)
Question: How do a player's position, performance, and background influence their height?

| Metric | Value | Interpretation |
|--------|-------|----------------|
| R² Score | 0.491 | Model explains 49.1% of height variance - moderate fit |
| RMSE | 0.734 cm | Average prediction deviation of only ~0.73 cm |
| MSE | 0.539 | Low squared error |
| MAE | 0.535 cm | Predictions off by ~0.53 cm on average - high precision |

Correlation check: No features exceeded 0.7 correlation - multicollinearity not a concern.

---

### Model 3 - KNN Classification (Attendance Prediction)
Question: Can we predict whether a match will have above-average attendance?

Features: Home club name, competition type, home club league position  
Target: Above/below average attendance (binary)  
Optimal k: k=4 (lowest error rate ~17.3%, identified via error rate curve)

| Metric | Score | Interpretation |
|--------|-------|----------------|
| Accuracy | 0.782 | 78.2% correct predictions |
| F1 Score | 0.783 | Strong precision-recall balance |
| Recall   | 0.774 | Captures 77.4% of high-attendance matches |
| Precision| 0.795 | Low false positive rate |
| ROC-AUC  | 0.837 | Excellent discrimination between high and low attendance |

Pipeline: Data scaling → k selection via error rate → KNN training → ROC-AUC evaluation

---

### Model 4 — K-Means Clustering (Player Segmentation)
Question: Can we cluster players by physical attributes and performance stats?

Features: Position, height, foot preference, total contributions (goals + assists)  
Optimal k:k=4 (identified via Elbow Curve — distortion reduction slows at k=4)

| Metric | Value | Interpretation |
|--------|-------|----------------|
| Silhouette Score        | 0.643 | Well-defined, distinct clusters (>0.6 is strong) |
| Calinski-Harabasz Score | 3828.01| High → clusters are compact and well-separated |
| Davies-Bouldin Score    | 0.60 | Low → minimal overlap between clusters |

Result: Players meaningfully segment into 4 distinct profiles — applicable to scouting, squad planning, and position-specific strategy design.

---

##  Tableau Dashboards

Interactive dashboards were built in Tableau Desktop and connected to MySQL + Excel:

- Performance Dashboard— Goals, assists, and contribution metrics by player and position
- Fan Engagement Dashboard — Stadium attendance trends by club, season, and competition type
- Market Value Dashboard - Investment distribution by country, position, and club
- Match Outcome Dashboard - Home vs. away trends, substitution impact, and seasonal performance
- Referee Dashboard - Card issuance frequency, match count, and goals-per-match by referee

All dashboards are available in `Gururahul_Capstone_project.twbx` (Tableau Public or Tableau Desktop required).

---

##  How to Run

### Prerequisites
```bash
pip install pandas numpy scikit-learn matplotlib seaborn sqlalchemy jupyter
```

### Steps
```bash
# 1. Clone the repository
git clone https://github.com/kr7561846-arch/football-data-analysis.git
cd football-data-analysis

# 2. Run data cleaning first
jupyter notebook Capstone_project_cleaned_data.ipynb

# 3. Run main analysis and ML models
jupyter notebook kumudha_Capstone_project.ipynb

# 4. Set up MySQL database
mysql -u root -p < Capstone_Project.sql

# 5. Open Tableau dashboard
# Open Gururahul_Capstone_project.twbx in Tableau Desktop or Tableau Public
```

---

##  Key Insights Summary

| Domain | Key Finding |
|--------|-------------|
| Performance | Attackers dominate goals; Christian Pulisic is top performer |
| Market Value | Midfielders most valued for tactical flexibility |
| Fan Behavior | Real Madrid leads global attendance; domestic cups drive highest turnout |
| Attendance | KNN model predicts high-attendance matches with 83.7% AUC |
| Substitutions | Mid-match substitutions significantly increase win probability |
| Match Events | Most goals and substitutions cluster in final 20 minutes |
| Player Clusters | 4 distinct player profiles identified via K-Means |
| Yellow Cards | Country of birth and position have moderate predictive power (AUC 77.6%) |
| Statistics | No significant home/away goal difference confirmed via hypothesis testing |
| Contracts | 2018–2019 are peak contract expiry years across all positions |

---

##  Future Scope

- Integrate real-time match data via football APIs (e.g., API-Football, Transfermarkt)
- Apply deep learning models (LSTM) for time-series match outcome prediction
- Expand NLP analysison player reviews, social media sentiment, and fan commentary
- Build a web application (Streamlit/Flask) to serve predictions interactively
- Incorporate transfer market prediction using advanced regression with more features

---

##  Author

Kumudha R  
B.Tech - ECE with Data Science Specialization  
SRM Institute of Science and Technology, Chennai  
 kr7561846@gmail.com  
 [LinkedIn](https://linkedin.com/in/kumudha-rameshkumar-a47983335) | [GitHub](https://github.com/kr7561846-arch)

---

##  License

This project is for academic and educational purposes.

---

*If you find this project useful, please star the repository!*
