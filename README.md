# Employee Sentiment Analysis Project

This project analyzes employee sentiment over time using email data. The primary goals include parsing and preprocessing email data, aggregating sentiments, performing exploratory data analysis (EDA) to uncover trends, identifying potentially unhappy or flight-risk employees, and building predictive models to forecast sentiment scores.

## Table of Contents
1.  [Methodology]
    * [Data Processing & Scoring]
    * [Exploratory Data Analysis (EDA)]
    * [Employee Ranking]
    * [Flight Risk Identification]
    * [Predictive Modeling]
2.  [Setup]
    * [Prerequisites]
    * [Dependencies]

---

## Methodology

The project follows a multi-step approach to analyze and predict employee sentiment:

### Data Processing & Scoring
1.  **Parsing & Preprocessing:** Email data is parsed to extract key fields such as sender, date, and the original message content (from which sentiment is derived).
2.  **Sentiment Aggregation:** Sentiments (positive, neutral, negative) are assigned numerical values (+1, 0, -1 respectively).
3.  **Monthly Sentiment Score Calculation:** For each employee, a monthly sentiment score is calculated by summing the scores of their messages within that month:
    score = (+1 * Number of Positive Messages) + (0 * Number of Neutral Messages) + (-1 * Number of Negative Messages)

### Exploratory Data Analysis (EDA)
EDA was performed to understand message trends and sentiment distributions. Key findings from the EDA included:
* Most employees had a higher volume of neutral messages.
* Positive and negative message volumes fluctuated over time.
* Specific periods (e.g., October-November) showed a noticeable drop in sentiment scores across the board.

### Employee Ranking
Employees are ranked based on their calculated monthly scores to identify:
* **Top Positive Employees:** Highest scores.
* **Most Negative Employees:** Lowest scores.

**Example Rankings (Jan 2010):**
* **Top 3 Positive Employees:**
    * john.arnold@enron.com
    * don.baughman@enron.com
    * eric.bass@enron.com
* **Top 3 Negative Employees:**
    * patti.thompson@enron.com
    * sally.beck@enron.com
    * bobette.riner@ipgdirect.com

### Flight Risk Identification
Employees are identified as potential flight risks based on criteria such as:
* Consistently low average sentiment scores across months.
* Presence of repeated negative monthly scores.
* Large drops in sentiment over time.

**Identified Flight Risk Employees:**
* patti.thompson@enron.com
* eric.bass@enron.com
* lydia.delgado@enron.com
* bobette.riner@ipgdirect.com
* rhonda.denton@enron.com
* don.baughman@enron.com
* kayne.coulter@enron.com
* sally.beck@enron.com
* john.arnold@enron.com
* johnny.palmer@enron.com

### Predictive Modeling
Two types of regression models were developed to forecast sentiment scores:

1.  **Linear Regression:**
    * **Feature:** `month_num` (numerical representation of the month).
    * **Performance:** The model did not perform well, indicating a poor linear relationship.
        * $R^2$ Score: -0.18
        * Mean Squared Error (MSE): 3.58

2.  **Random Forest Regressor:**
    * **Features:** `message count`, `Positive_message_counts`, `Negative_message_counts`, `Neutral_message_counts`, `month_num`.
    * **Performance:** This model showed significantly improved performance.
        * $R^2$ Score: 0.956
        * Mean Squared Error (MSE): 0.132
    * Feature importance analysis from this model highlighted message volume and polarity distribution as key drivers of sentiment scores.

---

## Setup

### Prerequisites
* Python 3.x
* pip (Python package installer)

### Dependencies
The project relies on several Python libraries. 
### Dependencies

The project relies on several Python libraries. 

**Key Libraries:**

* **pandas:** For handling and transforming tabular data.
* **matplotlib:** For plotting and visualizations.
* **seaborn:** For enhanced exploratory data analysis (EDA) visualizations.
* **scikit-learn (sklearn):**  For building the Linear Regression model (`LinearRegression`).
* **transformers:** Used for sentiment analysis (specifically, the Hugging Face pipeline).
* **textblob:** Used to calculate sentiment polarity, particularly for identifying neutral messages.

**Installation Command Example:**
```bash
pip install pandas matplotlib seaborn scikit-learn transformers textblob
