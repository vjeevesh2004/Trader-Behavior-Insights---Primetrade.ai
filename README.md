# Trader-Behavior-Insights---Primetrade.ai

## 🎯 Project Goal  
This project investigates the relationship between **collective trader performance** on the Hyperliquid exchange and the external **Bitcoin Market Sentiment (Fear/Greed Index)**.  
The core objective is to uncover **behavioral patterns** and deliver **statistically backed insights** that can inform smarter, sentiment-driven trading strategies.  

---

## 📊 Data Sources  

### 1. Bitcoin Market Sentiment Data (`fear_greed_index.csv`)  
- **Columns:** `timestamp`, `value` (0 = Extreme Fear, 100 = Extreme Greed), `classification`, `date`  
- **Frequency:** Daily  

### 2. Hyperliquid Historical Trader Data (`historical_data.csv`)  
- **Columns (key):** `Account`, `Side`, `Execution Price`, `Size USD`, `Timestamp IST`, `Closed PnL`  
- **Frequency:** High-frequency / Event-driven  

---

## ⚙️ Methodology  

The analysis followed a **four-stage process**, implemented in **Python** (`Pandas`, `NumPy`, `Matplotlib/Seaborn`, `SciPy`):  

1. **Data Cleaning & Standardization**  
   - Converted all date columns to datetime objects  
   - Handled missing `Closed PnL` values  

2. **Daily Performance Aggregation**  
   Aggregated high-frequency trades into daily KPIs:  
   - **Daily Total PnL:** Sum of all closed PnL per day  
   - **Daily Win Rate:** % of trades with `Closed PnL > 0`  

3. **Data Fusion**  
   - Merged daily trader KPIs with daily sentiment data on `date`  

4. **Statistical Analysis**  
   - **Grouped by sentiment classification (Fear/Greed/etc.)** → compared mean PnL & win rates  
   - **T-Test** → checked significance of mean PnL differences between Fear vs Greed days  
   - **Correlation** → tested linear relationship between sentiment value and trader performance  

---

## 💡 Key Findings & Strategic Insights  

The analysis revealed a **contrarian relationship** where collective profitability **peaks during times of Fear**.  

### 📊 Summary Table  

| Sentiment Classification | Avg Daily Total PnL (USD) | Avg Daily Win Rate |
|--------------------------|---------------------------|------------------|
| Extreme Fear             | $52,793.59               | 32.73%           |
| Fear                     | $36,891.82               | 32.91%           |
| Greed                    | $11,140.57               | 33.60%           |

- The difference in **Mean PnL** between *Fear days* and *Greed days* was **statistically significant**  
  - *T-Test Result → P-Value: 0.0217*  

---

## 📌 Strategic Recommendations  

1. **Contrarian Capital Allocation**  
   - Increase exposure (size/leverage) in **Fear/Extreme Fear** zones → highest edge for large PnL returns.  

2. **Risk Mitigation in Greed**  
   - Reduce trade size/frequency during **Greed** periods → lower profitability despite slightly higher win rates.  

3. **Sentiment Filter**  
   - Use **Extreme Fear (Index < 25)** as a filter to identify **high-conviction trade opportunities**.  

---
