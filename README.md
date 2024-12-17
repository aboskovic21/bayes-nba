# Bayesian Modeling of NBA MVP Shares

In this project, we fit a model to predict the NBA's MVP for a particular season based on their playing statistics. The NBA chooses the MVP via a voting system, and the player with the highest amount of points, the maximum of which varies by year and ranges from 1000 to 1400, wins MVP. A sensible way to boil down this problem is to predict the vote share of each potential candidate and assign the predicted winner to whoever won the majority vote for that year.

### Data Acquisition
We acquired data on MVP status for players from the MVP page of [basketball-reference.com](basketball-reference.com) for each year by webscraping it with Beautiful Soup in Python. We fit the model based on the year range 2000-2021.

### Model
After cleaning the data and a model selection process, we choose the following model:

$$Y_i | X_i, \beta,\phi \sim \text{Beta}(a_i, b_i)$$

$$\text{logit}(\mu_i) = \beta_0 + \beta_1X_1 +\dots+ \beta_{11}X_{11}$$

$$a_i = \mu_i \times \phi$$

$$b_i = (1 - \mu_i) \times \phi$$

We fit this model using JAGS via `rjags`, a Bayesian model fitting software. More details about the data cleaning, model choice, model fit, and testing are given in the report, `report.pdf`

### Summary of repository
1. `2022_dat.txt`: 2022 MVP dataset used for prediction.
2. `Code_Appendix.Rmd`: Additional code. 
3. `model_code.Rmd`: Code to fit the model and do some model checks.
4. `mvpdata.csv`: MVP dataset from 2000-2021 scraped from basketball reference.
5. `report.pdf`: Full, formal report describing the model-fitting process.
6. `scrape_nba.ipynb`: code for scraping MVP data from basketball reference.
