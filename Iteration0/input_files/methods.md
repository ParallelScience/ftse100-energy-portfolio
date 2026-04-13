1. **Data Preprocessing and Normalization**
   - Load the multi-index CSV and extract the OHLCV price series.
   - Convert all price columns (Open, High, Low, Close) from GBX to GBP by dividing by 100 immediately upon loading.
   - Calculate daily log returns for each of the seven tickers.
   - Construct two sub-sector indices: "Integrated/Utility" (SHEL.L, BP.L, SSE.L, CNA.L) and "E&P Pure-Plays" (ITH.L, HBR.L, ENOG.L) using an equal-weighted average of their log returns, noting this as a descriptive choice to prevent large-cap dominance.

2. **Robust Variance Estimation**
   - Implement a Huber M-estimator to calculate daily realized variance for each individual stock and the two sub-sector indices.
   - Apply the estimator to the returns within a 5-day rolling window to preserve data points given the 62-day sample size, ensuring the "burn-in" period is handled correctly.
   - Use this estimator to mitigate the impact of discrete price jumps (potential ex-dividend events) on volatility estimates.

3. **Variance Decomposition Framework**
   - Define the total sector variance as $Var(w_A R_A + w_B R_B) = w_A^2\sigma_A^2 + w_B^2\sigma_B^2 + 2w_A w_B Cov(R_A, R_B)$.
   - Decompose the total realized variance into three components: the variance contribution of the Integrated/Utility sub-sector, the E&P sub-sector, and the interaction (covariance) term.

4. **Volatility Budgeting Calculation**
   - Calculate the "Volatility Budget" for each sub-sector by allocating the covariance term equally between the two sub-sectors.
   - Express these as percentages of the total sector variance to quantify the relative risk weight of each sub-sector over the 62-day period.

5. **Idiosyncratic vs. Systematic Risk Mapping**
   - Construct an aggregate energy sector index as the equal-weighted average of all seven stocks.
   - Regress the returns of each individual stock against this aggregate index to isolate idiosyncratic risk (the residual variance).
   - Characterize the proportion of each stock's total variance that is idiosyncratic versus systematic to identify which sub-sector is more prone to independent shocks.

6. **Temporal Regime Identification and Visualization**
   - Generate a stacked area chart of the volatility budget over the 62-day timeline to visualize the shifting risk composition.
   - Identify specific temporal clusters where the E&P sub-sector's contribution to total variance spikes relative to the Integrated/Utility sub-sector.

7. **Tail Risk and Drawdown Analysis**
   - Calculate the maximum drawdown for each sub-sector index over the 3-month period.
   - Correlate these drawdown events with the identified spikes in the volatility budget to determine if E&P-specific tail risk is the primary driver of sector-wide instability.

8. **Statistical Validation and Reporting**
   - Perform a sensitivity analysis by varying the Huber M-estimator tuning constant to ensure the robustness of the variance decomposition.
   - Summarize findings into a final "Risk Profile" table, contrasting the volatility contribution and idiosyncratic risk levels of the two sub-sectors, framing results as a descriptive characterization of current energy sector instability.