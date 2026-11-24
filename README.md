1. Project Overview

An end-to-end Data Science and Machine Learning project focused on analyzing FIFA 20 football player performance, discovering skill-based player archetypes, identifying statistical patterns, and developing predictive classification models.

The project utilizes the FIFA 20 Career Mode dataset containing 18,278 player records and 104 attributes to perform data exploration, statistical inference, feature engineering, dimensionality reduction, unsupervised clustering, and supervised machine learning.

The primary objective is to transform raw football player data into actionable analytical insights and develop computationally efficient machine learning models for player profiling and positional classification.


Domain: Sports Analytics
Project Type: End-to-End Data Science & Machine Learning

2. Business Objectives

Analyze player demographics, technical attributes, physical characteristics, and financial metrics.

Identify performance patterns and relationships among player attributes.

Segment football players into meaningful skill-based archetypes using unsupervised learning.

Investigate country-wise player distribution and age-related performance trends.

Statistically evaluate wage differences across offensive playing positions.

Develop and benchmark multiple machine learning classification algorithms.

Select production-suitable models based on predictive performance, computational efficiency, and scalability.

3. Dataset Description

Attribute

Description

Dataset

FIFA 20 Career Mode Players

Records

18,278

Features

104

Data Format

CSV

Target Domain

Football Player Analytics

Data File

players_20.csv

Feature Categories

Category

Attributes

Player Identification

sofifa_id, short_name, long_name

Demographics

age, nationality, height_cm, weight_kg

Performance

overall, potential

Technical Skills

passing, finishing, dribbling, ball control

Physical Skills

acceleration, sprint speed, stamina, strength

Defensive Skills

marking, interceptions, standing tackle

Goalkeeping

diving, handling, reflexes, positioning

Financial

value_eur, wage_eur

Positional Information

player_positions, team_position

Player Characteristics

preferred_foot, weak_foot, skill_moves, work_rate

4. Technical Architecture & Workflow

The project follows a structured analytical pipeline:

Data ingestion and validation

Exploratory Data Analysis

Data cleaning and preprocessing

Feature engineering and encoding

Statistical analysis and hypothesis testing

Feature standardization and dimensionality reduction

Unsupervised player segmentation

Supervised position classification

Model benchmarking and evaluation

Model selection and production recommendations

5. Data Preprocessing & Feature Engineering

Implemented a systematic preprocessing pipeline to improve data quality and ensure compatibility with statistical and machine learning algorithms.

Data quality management

Inspected missing-value distributions and duplicate records.

Identified structurally missing values, particularly goalkeeper-specific and outfield-specific attributes.

Removed identifier columns, redundant composite features, and columns with more than 80% missing values.

Preserved meaningful player attributes without introducing artificial values through inappropriate imputation.

Feature engineering

Converted positional ratings stored as strings (e.g., 89+2) into numerical values.

Extracted primary playing positions from multi-valued position fields.

Derived four major position groups: GK, DEF, MID, and FWD.

Encoded preferred foot and attacking/defensive work rates.

Converted market value into millions of euros and wages into thousands of euros.

Selected relevant technical and physical attributes for clustering and classification.

Numerical preprocessing

Applied feature standardization to address differences in feature scales.

Used PCA to reduce dimensionality and mitigate multicollinearity.

6. Exploratory Data Analysis (EDA)

Performed comprehensive univariate, bivariate, and multivariate analysis.

Analytical techniques

Descriptive statistical analysis.

Distribution analysis using histograms and KDE.

Categorical frequency analysis.

Correlation matrix and heatmap analysis.

Outlier detection using the Interquartile Range (IQR) method.

Position-wise and age-wise comparative analysis.

Key analytical observations

Player market values and wages exhibit substantial positive skewness.

Technical attributes such as reactions, ball control, passing, and dribbling show meaningful relationships with player performance.

Highly correlated skill attributes require dimensionality reduction to prevent redundant feature weighting.

Financial outliers represent genuine high-value players and should not automatically be removed.

7. Unsupervised Learning – Player Archetype Discovery

Implemented a two-stage clustering strategy to identify football player archetypes based on technical and physical skill profiles.

Algorithms Evaluated

K-Means Clustering

Agglomerative Hierarchical Clustering (Ward Linkage)

Gaussian Mixture Model (GMM)

Methodology

Selected 39 relevant player skill attributes.

Excluded overall rating, potential, and positional ratings to avoid target leakage.

Standardized the selected features.

Applied Principal Component Analysis (PCA).

Retained components representing 90% of the variance.

Evaluated cluster configurations using multiple internal validation metrics.

Applied a two-stage clustering approach, separating goalkeepers from outfield players.

Interpreted clusters using skill profiles and position distributions.

Identified Player Archetypes

Archetype

Characteristics

Physical Centre-Backs

Strength, heading, tackling, and defensive capabilities

Defensive All-Rounders

Aggression, stamina, interceptions, and defensive versatility

Strikers & Wide Forwards

Acceleration, sprint speed, finishing, and attacking positioning

Elite Creative Attackers & Playmakers

Ball control, dribbling, vision, passing, and composure

Goalkeepers

Specialized goalkeeping attributes and performance profiles

Clustering Evaluation

The K-Means model achieved:

Silhouette Score: approximately 0.17

Davies-Bouldin Index: approximately 1.67

Lowest computational cost among the evaluated clustering approaches.

Model Selection: K-Means with standardized PCA-transformed features was selected for its computational efficiency, cluster compactness, and suitability for assigning archetypes to new player records.

Technical consideration: The relatively low silhouette score indicates overlapping player skill distributions. The resulting archetypes are analytical profiles rather than strictly separated football positions.

8. Statistical Analysis & Business Intelligence

Three business-oriented analytical questions were investigated.

Q1. Which countries contribute the highest number of FIFA 20 players?

Analyzed nationality distributions and identified the top 10 countries by player count.

Country

Player Count

England

1,667

Germany

1,216

Spain

1,035

France

984

Argentina

886

Brazil

824

Italy

732

Colombia

591

Japan

453

Netherlands

416

Insight: England contributes the largest number of players, while player count and player quality are not necessarily correlated.

Q2. How does player overall rating vary with age?

Analyzed age-wise average overall ratings.

Compared overall rating against potential.

Examined performance progression and plateau patterns.

Insight: Average player development slows around ages 26–28, followed by a relatively stable performance period and a decline among older players.

Q3. Which offensive position receives the highest wages?

Compared the weekly wages of:

Strikers (ST)

Right-Wingers (RW)

Left-Wingers (LW)

Statistical techniques

Mean and median comparison.

Kruskal-Wallis hypothesis testing.

Mann-Whitney testing.

Log-wage regression controlling for overall rating, age, and international reputation.

Results:

Position

Average Weekly Wage

Right-Winger (RW)

€15.9K

Left-Winger (LW)

€14.2K

Striker (ST)

€10.3K

Statistical conclusion: Although right-wingers have the highest average wages, the Kruskal-Wallis test returned p = 0.86. There is insufficient statistical evidence of a significant wage difference among the three positions.

The observed average wage difference is influenced by high-earning superstar players rather than a systematic positional salary premium.

9. Supervised Machine Learning – Position Classification

Developed a multi-algorithm classification pipeline to predict player position groups.

Algorithms Implemented

Algorithm

Test Macro-F1

Support Vector Machine (RBF)

0.910

Histogram Gradient Boosting

0.909

Random Forest

0.905

Logistic Regression

0.905

K-Nearest Neighbors

0.887

Evaluation Methodology

Stratified training and testing.

Cross-validation.

Macro-F1 evaluation.

Classification performance comparison.

Prediction latency benchmarking.

Computational cost assessment.

Production Model Selection

Recommended model: Histogram Gradient Boosting Classifier

Evaluation Metric

Result

Test Macro-F1

0.909

Inference Time

0.013 ms/player

Main Advantage

Non-linear classification

Deployment Consideration

Computational efficiency and retraining flexibility

Although the RBF SVM achieved the highest macro-F1 score of 0.910, Histogram Gradient Boosting provides a more practical trade-off between predictive performance and inference efficiency.

Logistic Regression was retained as an interpretable baseline and fallback model.

10. Model Evaluation & Deployment Strategy

The project includes a player scoring workflow that combines supervised classification and unsupervised archetype assignment.

Prediction Pipeline

Input: Player skill attributes

Stage 1 – Position Classification

Load the trained position classifier.

Predict the player's primary position group.

Identify whether the player belongs to GK, DEF, MID, or FWD.

Stage 2 – Archetype Assignment

For outfield players, apply the saved scaler and PCA transformation.

Assign the player to a K-Means archetype.

Return the corresponding player profile.

For goalkeepers, return the goalkeeper category directly.

Output:

Predicted player role.

Skill-based player archetype.

This provides a reusable framework for player profiling and analytical decision support.

11. Challenges & Technical Solutions

Challenge

Technical Solution

High percentage of missing values

Structural missing-value analysis and selective column removal

Positional ratings stored as strings

Custom numerical parsing and transformation

Multi-valued categorical features

Primary-position extraction and categorical encoding

Highly skewed financial attributes

Log transformation, median analysis, and non-parametric testing

High multicollinearity

StandardScaler and PCA

Goalkeeper dominance in clustering

Two-stage clustering architecture

No ground-truth cluster labels

Silhouette, Davies-Bouldin, Calinski-Harabasz, and interpretability analysis

Target leakage risk

Exclusion of overall, potential, positional ratings, and position from clustering inputs

High computational complexity

Sample-based benchmarking and silhouette evaluation

12. Technology Stack

Area

Tools & Libraries

Programming

Python

Data Manipulation

Pandas, NumPy

Data Visualization

Matplotlib, Seaborn

Statistical Analysis

SciPy

Machine Learning

Scikit-learn

Dimensionality Reduction

PCA

Clustering

K-Means, Agglomerative Clustering, GMM

Classification

SVM, Random Forest, Logistic Regression, KNN, Histogram Gradient Boosting

Model Serialization

Joblib

Development Environment

Jupyter Notebook

13. Repository Structure

FIFA20-Player-Analytics/
│
├── FIFA20_Capstone_Project.ipynb
│
├── players_20.csv
│
├── models/
│   ├── position_classifier.joblib
│   └── outfield_archetype_clusters.joblib
│
├── README.md
│
└── requirements.txt

The model files are generated by the notebook's model-training workflow. Include them in the repository only after exporting them successfully.

14. Installation & Execution

Prerequisites

Python 3.x

Jupyter Notebook

Git

15. Future Scope

Develop an interactive football analytics dashboard using Streamlit.

Implement player similarity search using vector-based representations.

Build player market valuation and wage prediction models.

Extend analysis across multiple FIFA editions for longitudinal comparisons.

Develop player recommendation and scouting systems.

Deploy classification and clustering pipelines through REST APIs using Flask or FastAPI.

Implement model monitoring, data drift detection, and automated retraining.

16. Conclusion

This project demonstrates the practical application of statistical analysis, feature engineering, unsupervised learning, and supervised machine learning within the sports analytics domain.

By combining player segmentation, statistical hypothesis testing, and predictive classification, the project transforms raw football data into structured player insights.

The final model evaluation identifies K-Means for skill-based player segmentation and Histogram Gradient Boosting for position classification as the recommended production approaches.

The project highlights the importance of not only achieving predictive accuracy but also considering model interpretability, computational efficiency, scalability, and analytical validity.

