# Capstone Project: Customer Segmentation for a Sports Betting Platform

This repository contains the complete analysis for a data science capstone project focused on customer segmentation. Using the CRISP-DM framework, this project analyzes transactional betting data to identify distinct customer segments, moving from a reactive "one-size-fits-all" business model to a proactive, data-driven strategy.

The final model successfully segments all customers into four actionable groups, providing clear recommendations for risk management and marketing.

## 📁 Files in This Repository

* `capstone_project.ipynb`: The main Jupyter Notebook containing all Python code, analysis, and visualizations.
* `capstone_project.html`: A static HTML export of the notebook for easy viewing in any browser.
* `bets.csv`: The raw, transactional dataset used for this analysis.
* `capstone_project_presentation.pdf`: A high-level PDF slide deck that summarizes the key findings and recommendations for a non-technical, executive audience.
* `capstone_project_presentation.mp4`: Video presentation of the slides.
* `README.md`: This file.

## 1. Business Problem

The company's current strategy for customer management is inefficient and unsustainable. It faces two core challenges:

1.  **Inefficient Marketing:** The "one-size-fits-all" approach to bonuses and retention wastes budget on the wrong customers.
2.  **Reactive Risk Management:** High-cost, high-risk winning customers are often identified *after* they have already caused significant financial damage.

This project's goal is to solve this by building a segmentation model that identifies and profiles these key groups *before* it's too late.

## 2. Methodology (CRISP-DM)

This project follows the CRISP-DM framework from business understanding to evaluation.

1.  **Data Preparation:** The raw, transactional `bets.csv` file (100,000 bets) was aggregated into a customer-level view of 5,000 unique users.
2.  **Feature Engineering:** Six key behavioral features were created for each customer: `total_bets`, `total_staked`, `net_gain_loss`, `avg_odds`, `win_rate`, and `multiple_bet_ratio`.
3.  **Exploratory Data Analysis (EDA):** Initial visualizations revealed clear patterns in betting styles and value concentration, confirming the segmentation hypothesis.
4.  **Modelling:** An unsupervised clustering approach was applied:
    * Features were scaled using `StandardScaler`.
    * Dimensionality was reduced using `PCA` (2 components).
    * Segments were identified using `K-Means Clustering` (K=4, validated by the Elbow Method).
5.  **Evaluation:** The model was validated technically with a **Silhouette Score of 0.384** (indicating distinct clusters) and, more importantly, through a deep-dive business impact analysis.

## 3. Key Findings: The Four Customer Segments

The model successfully identified four distinct, actionable customer segments. The key finding is that our financial risk is dangerously concentrated.

* **"Frequent Winners" (20.2% of users):**
    * **The "Volume" Problem.** This large group is the single biggest financial drain, responsible for **$4.97 Million** in total costs (41.6% of all costs).

* **"High-Stakes Winners" (3.5% of users):**
    * **The "Risk" Problem.** This tiny group is a "time bomb." Each user costs an average of **$14,780**—three times more than any other group.

* **"Smart & Cautious Winners" (39.0% of users):**
    * **The "Skilled Base."** This is the largest group, but their cautious style makes them a manageable, low-level cost ($1,236 per user).

* **"Lottery-Style Players" (37.3% of users):**
    * **The "Healthy" Segment.** This group is the least costly. Their high-risk, low-win-rate behavior is the most favorable for the company's bottom line.

## 4. Actionable Recommendations

This segmentation model allows us to stop treating all customers the same and implement a precise, cost-effective strategy.

| Segment | Business Recommendation |
| :--- | :--- |
| **High-Stakes Winners ("Time Bombs")** | **1. MANAGE RISK:** Apply strict, individual bet limits. <br> **2. EXCLUDE:** Remove from all marketing & bonus lists immediately. |
| **Frequent Winners ("Volume Drain")** | **1. MONITOR:** Proactively flag for risk review. <br> **2. SHIFT MARKETING:** Move promotions from generic bonuses to higher-margin bets (e.g., parlays). |
| **Smart & Cautious Winners ("Skilled Base")** | **1. ENGAGE:** Use "Bet-Get" campaigns to increase volume without significantly increasing risk. |
| **Lottery-Style Players ("Healthy Segment")** | **1. ENCOURAGE:** Target with all jackpot, parlay, and "long-shot" promotions to reinforce their favorable behavior. |

## 5. How to Run This Project

1.  **Clone the Repository:**
    ```bash
    git clone [Your-Repo-URL]
    ```
2.  **Create a Virtual Environment** (Recommended):
    ```bash
    conda create -n capstone python=3.9
    conda activate capstone
    ```
3.  **Install Required Libraries:**
    ```bash
    pip install pandas numpy scikit-learn plotly nbformat
    ```
4.  **Launch Jupyter Notebook:**
    ```bash
    jupyter notebook capstone_project.ipynb
    ```

## 6. Next Steps (Future Scope)

This project is the foundation for a proactive risk system. The next logical step is to **build a predictive classification model** (e.g., Logistic Regression or Random Forest) using these segments as the target. This would allow the business to predict a new user's segment *at the moment of sign-up* and apply risk rules *before* they can become a $14,000 problem.