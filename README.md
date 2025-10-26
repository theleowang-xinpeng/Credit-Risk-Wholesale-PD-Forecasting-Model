# Credit Risk Probability of Default (PD) Model

## Objective
Estimate the probability that a corporate borrower will default within the next 6 months.  
Goal: give credit and risk teams an early warning signal so they can adjust exposure, pricing, or limits proactively.

## Data & Feature Engineering
- Sourced company financial statement data.
- Normalized financials into comparable, size-neutral ratios (profitability, leverage, liquidity, coverage) so large and small firms can be evaluated on the same scale.
- Engineered features commonly associated with credit deterioration.
- Created a forward-looking label using S&P-equivalent credit ratings 6 months ahead to predict future deterioration, not just current status.
- Removed any post-default or future information to avoid look-ahead bias and keep the model realistic for production use.

## Modeling Approach
1. Performed single-factor analysis on candidate features using:
   - R² (for explanatory strength)
   - AUC (for rank-ordering power)
2. Selected a small, non-redundant set of features by:
   - Keeping only factors with strong predictive signal
   - Controlling multicollinearity (capping pairwise correlation)
3. Trained a 4-factor logistic regression model (`scikit-learn`), using:
   - `pandas` and `NumPy` for data prep
   - `scikit-learn` for modeling / validation
4. Validated on out-of-time data to confirm generalization and avoid overfitting.

Why logistic regression?
- Interpretable: easy to explain which factors drive PD.
- Documentable: aligns with credit/audit expectations.
- Controllable: supports governance and policy use.

## Outputs
- Probability of Default (PD) scores at the counterparty level.
- Portfolio-level view of risk concentration.
- Rank-ordered list of higher-risk names for review/escalation.
- Visualizations (lift charts, factor impact plots).
- A model card documenting purpose, inputs, assumptions, and limitations.

## Business Impact
- Converts raw financial statements into an actionable early warning signal.
- Brings consistency to credit decisions (not just judgment-based).
- Supports exposure management, pricing, and limit-setting.
- Produces artifacts suitable for audit, model governance, and regulatory review.

## Tech Stack
- Python
- pandas / NumPy (data cleaning, feature engineering)
- scikit-learn (model training and validation)
- matplotlib / seaborn (visualization and reporting)

## Key Skills Demonstrated
- End-to-end model development (data prep → modeling → validation → reporting)
- Credit risk thinking (default prediction, forward-looking labels, avoiding leakage)
- Documentation and communication for stakeholders (risk, credit, audit)
- Building something that is usable by decision-makers, not just technically accurate
