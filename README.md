#  Hurst Exponent Trading Strategy Implementation

A comprehensive implementation of the Cornell Data Science paper: **"Optimizing Returns Using the Hurst Exponent and Q-Learning on Momentum and Mean Reversion Strategies"** by Chang, Lizardi, and Shah.

##  Project Overview

This project demonstrates how to use the **Hurst exponent** to intelligently switch between momentum and mean reversion trading strategies. The key insight: different strategies work better under different market conditions, and the Hurst exponent can help identify which strategy to use when.

###  What We Explore
- **100 carefully selected large-cap stocks** from diverse sectors
- **Hurst exponent calculation** to classify market behavior (trending vs mean-reverting)
- **SMA crossover strategy** for trending assets (momentum trading)
- **Bollinger Bands strategy** for mean-reverting assets (mean reversion trading)
- **Risk-return optimization** through dynamic boundary adjustment

###  Key Research Finding
> Different trading strategies have **opposite characteristics**. By using the Hurst exponent to identify whether a stock is trending or mean-reverting, we can apply the most suitable strategy and optimize our risk-return profile.

##  Quick Start Options

### Option 1: Download and run on Google Colab (Recommended)
1. **Download** the `AADITYA_hurstExponent_implementation.ipynb` file from this repository
2. **Upload** to [Google Colab](https://colab.research.google.com)
3. **Follow** the step-by-step instructions below

### Option 2: Download and Run Locally
1. **Download** the `AADITYA_hurstExponent_implementation.ipynb` file from this repository
2. Run locally in preferred environment.

### Option 3: Direct Google Colab Access (find link below)
- https://colab.research.google.com/drive/1sHADqFqJv8XX2qytNZn5r5xPjYTy29Ja?usp=sharing

##  Prerequisites

- **Google account** (for Google Colab access)
- **Internet connection** (for downloading stock data)
- **No programming experience required** - all code is provided and explained

###  Required Libraries
The notebook automatically installs all required packages:
```python
!pip install yfinance hurst ta --quiet
```

## 🔧 How to Run the Notebook

### Step 1: Open in Google Colab
- Go to [colab.research.google.com](https://colab.research.google.com)
- Upload the `.ipynb` file or use the direct link.
- You'll see 8 cells ready to execute

### Step 2: Execute Cells Sequentially
** IMPORTANT: Run cells in order (1 → 8) and wait for each to complete**

##  Cell-by-Cell Guide

###  **Cell 1: Project Introduction**
**What it does:** Provides project overview and research context
- **Runtime:** Instant
- **Output:** Formatted introduction text
- **Action:** Simply read through the introduction

###  **Cell 2: Stock Selection & Data Setup**
**What it does:** Loads 100 pre-selected stocks and explains methodology
- **Runtime:** 2-3 seconds
- **Output:** Stock list by sector, data source information
- **What to expect:** 
  ```
   Sector Diversification (100 stocks):
    Technology: 23 stocks
    Healthcare: 15 stocks
    ...
  ```

###  **Cell 3: Hurst Exponent Calculation**
**What it does:** Downloads first half of 2024 data and calculates Hurst exponents
- **Runtime:** 3-5 minutes (downloads data for 100 stocks)
- **Output:** Table showing each stock's Hurst exponent and classification
- **What to expect:**
  ```
   Hurst Exponent Results:
  Symbol | Hurst_Exponent | Classification
  AAPL   | 0.547         | Trending
  MSFT   | 0.423         | Mean Reverting
  ...
  ```
- ** Be patient:** This cell downloads real market data

###  **Cell 4: SMA Crossover Strategy (Momentum)**
**What it does:** Applies momentum trading strategy to all 100 stocks
- **Runtime:** 4-6 minutes
- **Output:** Performance statistics and histogram visualization
- **What to expect:**
  ```
   SMA CROSSOVER STRATEGY PERFORMANCE:
  Mean Return      : 0.0234 (2.34%)
  Median Return    : 0.0156 (1.56%)
  Standard Deviation: 0.0890 (8.90%)
  ```
- **Visual:** Blue histogram showing return distribution

###  **Cell 5: Bollinger Bands Strategy (Mean Reversion)**
**What it does:** Applies mean reversion trading strategy to all 100 stocks
- **Runtime:** 4-6 minutes
- **Output:** Performance statistics and side-by-side comparison with SMA
- **What to expect:**
  ```
   BOLLINGER BANDS STRATEGY PERFORMANCE:
  Mean Return      : 0.0445 (4.45%)
  Standard Deviation: 0.1234 (12.34%)
  ```
- **Visual:** Orange histogram + comparison charts

###  **Cell 6: Balanced Hurst Strategy**
**What it does:** Combines both strategies using Hurst exponent (0.5 boundary)
- **Runtime:** 1-2 minutes
- **Output:** Comprehensive performance comparison of all three approaches
- **What to expect:**
  ```
  STRATEGY PERFORMANCE COMPARISON:
  Strategy         | Mean Return | Std Deviation | Sharpe Ratio
  SMA Crossover    | 2.34%      | 8.90%        | 0.263
  Bollinger Bands  | 4.45%      | 12.34%       | 0.361
  Balanced Hurst   | 3.12%      | 10.15%       | 0.307
  ```
- **Visual:** Four-panel comparison charts

###  **Cell 7: Analysis of Results**
**What it does:** Explains why results might be unexpected and introduces risk-return concepts
- **Runtime:** Instant
- **Output:** Theoretical explanation and insights
- **Key insight:** The balanced strategy positions itself between the two pure strategies, demonstrating risk-return trade-offs

###  **Cell 8: Interactive Risk-Return Optimization**
**What it does:** Provides interactive slider to explore different risk preferences
- **Runtime:** 2-3 minutes
- **Output:** Interactive widget + dynamic visualizations
- **What to expect:** 
  - Slider widget (0.1 to 0.9)
  - Real-time charts updating based on your risk preference
  - Personalized portfolio performance metrics

** How to use:** Move the slider to adjust your risk tolerance:
- **0.1-0.4:** Conservative (more mean reversion)
- **0.4-0.6:** Balanced 
- **0.6-0.9:** Aggressive (more momentum)

##  Expected Results

Based on the Cornell paper methodology, you should see:

| Strategy Type | Expected Characteristics |
|---------------|-------------------------|
| **SMA (Momentum)** | Lower returns, lower risk, frequent small losses with occasional large gains |
| **Bollinger Bands (Mean Reversion)** | Higher returns, higher risk, frequent small wins with occasional large losses |
| **Balanced Hurst** | Interpolated performance between the two pure strategies |

##  Troubleshooting

### Common Issues:

**"Module not found" errors:**
- Ensure Cell 1 (package installation) completed successfully
- Restart runtime: `Runtime → Restart and run all`

**"Download failed" for some stocks:**
- Normal behavior - some stocks may have data issues
- The notebook handles this gracefully and continues with available data

**Widgets not displaying in Cell 8:**
- Refresh the page and re-run Cell 8
- Ensure you're using Chrome/Firefox for best compatibility

**Slow execution:**
- Normal for data-intensive operations
- Each data download cell (3, 4, 5) takes several minutes
- **Do not interrupt** - let cells complete fully

##  Educational Value

This notebook teaches:
- **Quantitative finance concepts** (Hurst exponent, Sharpe ratio, trading strategies)
- **Python data analysis** (pandas, numpy, matplotlib)
- **Financial data handling** (yfinance, time series analysis)
- **Risk management principles** (portfolio optimization, statistical analysis)
- **Interactive visualization** (widgets, dynamic charts)

##  Academic Foundation

This implementation is based on:
- **Cornell Data Science Research Paper** (2022)
- **Peer-reviewed methodology** for Hurst exponent application
- **Real market data** from Yahoo Finance API
- **Statistical rigor** following academic standards

##  Contributing

Feel free to:
- **Report issues** in the GitHub Issues tab
- **Suggest improvements** via pull requests
- **Share your results** and insights


##  Additional Resources

- **Original Paper:** "Optimizing Returns Using the Hurst Exponent and Q-Learning on Momentum and Mean Reversion Strategies"
- **Google Colab Documentation:** [colab.research.google.com](https://colab.research.google.com)

**📞 Questions?** Open an issue in this repository and we'll help you get started!

**⭐ Found this useful?** Please star this repository to help others discover it!
