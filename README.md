# Credit-Risk-Wholesale-PD-Forecasting-Model
##Objective
Estimate the probability that a corporate borrower will default in the next six months. The goal was to give credit and risk teams an early warning signal so they can adjust exposure, pricing, or limits before performance deteriorates, rather than reacting after the fact.

##What I Built
I built a probability of default (PD) model in Python using financial statement data. The process included:
Normalizing company financials into comparable ratios (profitability, leverage, liquidity, coverage) so small and large firms could be evaluated on the same scale.
Engineering features known to drive credit quality.
Creating a forward-looking label using S&P-equivalent ratings six months ahead, so the model predicts future deterioration instead of just current state.
Removing any “future knowledge” such as post-default data to avoid look-ahead bias and make the model realistic for production use.

##Model Approach
I tested each financial ratio individually (using R² and AUC) to measure how predictive it was. Then I selected a small set of factors that were both:
Strong signals of credit deterioration, and
Not too correlated with each other.
Using those factors, I trained a four-factor logistic regression model in Python (pandas, NumPy, scikit-learn). Logistic regression was chosen intentionally because:
It’s explainable (credit and audit can understand how each factor influences risk),
It’s controllable,
It’s easy to document and defend.
I then validated the model on out-of-time data to confirm it generalized and wasn’t just memorizing.

##Results / Impact
The model produced portfolio-level PD estimates with clear lift versus baseline, meaning it could better separate strong credits from weak credits.
Counterparties could be ranked by risk level, which supports actions like tightening terms, reviewing exposure, or escalating higher-risk names.
I delivered final outputs as clear visuals and a model card (purpose, inputs, assumptions, limitations) so decision-makers could actually use it.

##Why It Matters to the Business
Turns raw financials into a decision-ready risk signal.
Brings consistency to credit decisions instead of relying only on judgment.
Is built in a way that’s transparent enough for governance, audit, and regulators.
