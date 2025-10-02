# Trader-Behavior-Insights---Primetrade.ai

🎯 Project Goal
This project aims to investigate the relationship between collective trader performance on the Hyperliquid exchange and the external Bitcoin Market Sentiment (Fear/Greed Index). The core objective is to uncover behavioral patterns and deliver statistically backed insights that can inform smarter, sentiment-driven trading strategies.

📊 Data Sources
Two primary, time-series datasets were utilized:

Bitcoin Market Sentiment Data (fear_greed_index.csv)

Columns: timestamp, value (0=Extreme Fear, 100=Extreme Greed), classification, date.

Frequency: Daily.

Hyperliquid Historical Trader Data (historical_data.csv)

Columns: High-frequency trade records including Account, Side, Execution Price, Size USD, Timestamp IST, and the crucial performance metric: Closed PnL.

Frequency: High-frequency/event-driven.

⚙️ Methodology
The analysis followed a four-stage process, primarily implemented using Python (Pandas, NumPy, Matplotlib/Seaborn, SciPy):

Data Cleaning and Standardization: Converted all date columns to standardized datetime objects and handled missing Closed PnL values.

Daily Performance Aggregation: The high-frequency trader data was aggregated to a daily level to calculate key performance indicators (KPIs) for the entire trader base:

Daily Total PnL: Sum of all closed PnL for the day.

Daily Win Rate: Percentage of trades with PnL > 0.

Data Fusion: The daily performance KPIs were merged with the daily sentiment data based on the shared Date index.

Statistical Analysis:

Grouping by Sentiment Classification (Fear, Greed, etc.) to compare mean PnL and Win Rate.

Calculating T-Test to determine the statistical significance of the difference in mean PnL between "Fear" and "Greed" days.

Calculating Correlation between the numerical Sentiment Value and performance metrics to identify linear trends.

💡 Key Findings & Strategic Insights
The analysis demonstrated a statistically significant contrarian relationship where collective profitability peaks during times of market fear.

Sentiment Classification

Avg Daily Total PnL (USD)

Avg Daily Win Rate

Extreme Fear

$52,793.59

32.73%

Fear

$36,891.82

32.91%

Greed

11,140.57

33.60%

Primary Conclusion
The difference in Mean PnL between Fear days and Greed days was found to be statistically significant (P-Value: 0.0217).

Actionable Strategy Recommendations
Contrarian Capital Allocation: Increase risk exposure (size/leverage) when sentiment is in the Fear or Extreme Fear zones, as these periods provide the highest statistical edge for large PnL returns.

Risk Mitigation in Greed: Reduce trading size and frequency during "Greed" periods. The low PnL during these phases suggests the market edge is weak, despite a tendency toward slightly higher win rates (indicative of low-impact scalping).

Sentiment Filter: Use the Extreme Fear classification (Index Value <25) as a primary filter for identifying high-conviction, high-impact trading opportunities.

💻 Setup and Execution
To replicate this analysis, follow these steps:

Clone the repository:

git clone [YOUR_REPO_LINK]
cd crypto-trader-sentiment-analysis

Download Data:

Place the fear_greed_index.csv and historical_data.csv files into the root directory of the project.

Install Dependencies:

pip install pandas numpy matplotlib seaborn scipy

Run the Notebook:
Execute the cells in the Trader_Behavior_Insights.ipynb Jupyter notebook sequentially to perform the data processing, aggregation, merging, and final statistical analysis.
