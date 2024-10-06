# Modern-Portfolio-Theory  
**1. Introduction**  
In this project, I will implement Modern Portfolio Theory (MPT), also known as mean-variance analysis, using a portfolio composed of stocks from the five largest companies by market capitalization: **AAPL, MSFT, NVDA, GOOG, and AMZN**. Basically, MPT is a mathematical approach to portfolio construction that aims to maximize expected returns for a given level of risk or minimize risk for a target level of expected return. You can find more detailed information about MPT in the following link: [Link](https://en.wikipedia.org/wiki/Modern_portfolio_theory#:~:text=Modern%20portfolio%20theory%20(MPT),%20or%20mean-variance%20analysis,%20is).  

**2. Implementation**  
First, I retrieved the stock data for the 5 companies using the yfinance library in Python, with the start date set to five years ago and the end date being the most recent available. The images below display the stock price trends for each company over the years: ![Stock Prices](https://drive.google.com/uc?id=1lq-tYVQ9bo7gTwyiRFlI5bnudLcC2qEk)    
Next, I calculated the log returns of the five stocks and plotted their histograms to examine the distribution: ![Returns](https://drive.google.com/uc?id=1iBqabVagxIttpQpR04AlNEW3fhAKqBrU)  
Based on the graphs, it quite hard to determine whether the log returns adhere to a normal distribution. If the normality assumption is violated, it could result in deviations from the expected outcomes of Modern Portfolio Theory (MPT), potentially leading to suboptimal portfolio solutions. To clarify this, I will further examine the QQ plot. ![QQ Plot](https://drive.google.com/uc?id=1Dcmzl5WDMFNVH9HxyOPZ6V6jwrxfCZNT)
I also performed a normality test in my code, and the results consistently indicate that real-life stock returns rarely meet the normality assumption. However, for the purposes of this project, I will assume that my stocks conform to this assumption.  

**Modern Portfolio Theory**  
To apply Modern Portfolio Theory (MPT), I first need to calculate the expected returns and variance of my portfolio for various weight combinations. The weights are generated using a uniform distribution, ensuring that the sum of all weights equals one. Additionally, I assume investors can only take long positions, meaning the weights are restricted to the range [0, 1]. By adjusting these weight combinations, the portfolio will exhibit different expected returns and variances, reflecting the trade-off between risk and return.  

Next, we'll determine the two optimal portfolios: one with the maximum Sharpe ratio and the other with the minimum volatility, while also constructing the Efficient Frontier. Using the SciPy library, we can optimize the portfolios with constraints ensuring the weights sum to 1 and are bounded between 0 and 1 (long-only positions). For the Efficient Frontier, I set a target returns range between 20% and 60%, and for each target return, I calculate the portfolio with the minimum volatility. The resulting Efficient Frontier is displayed below:  ![QQ Plot](https://drive.google.com/uc?id=1T3ivmV1uVl3HR3xBk2p24EBt-M0LcGc3)

**What if investors are allowed to take short positions on stocks?**  
In reality, investors are not limited to long positions; they can also take short positions, which may boost the returns of their portfolios. To reflect this, I will adjust the weight constraints to be between -1 and 1, allowing for both long and short positions. The process for identifying the two optimal portfolios remains the same as in the previous case.  

**Comparison between 2 cases**  
Finally, we will compares the PnL of different portfolios in the 2 cases: ![QQ Plot](https://drive.google.com/uc?id=1fxX-n8HIH3PYofZpyfio600ogVLHwSbH)
It's clear that when investors are allowed to both long and short stocks, the two optimal portfolios demonstrate better performance compared to when only long positions are permitted.  

**Drawback**  
The main drawback of Modern Portfolio Theory (MPT) is its assumption that log returns follow a normal distribution, which is rarely observed in real-world markets. When log returns deviate from normality, the resulting "optimal" portfolios may not accurately represent reality, potentially leading to suboptimal investment decisions and an imprecise efficient frontier.





