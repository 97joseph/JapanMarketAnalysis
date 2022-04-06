# JapanMarketAnalysis
![t54gr](https://user-images.githubusercontent.com/33089347/161894745-c3375263-53c2-43e5-a1bb-d7fd27c7a122.PNG)


**Index Market Analysis**

Success in any financial market requires one to identify solid investments. When a stock or derivative is undervalued, it makes sense to buy. If it's overvalued, perhaps it's time to sell. While these finance decisions were historically made manually by professionals, technology has ushered in new opportunities for retail investors. Data scientists, specifically, may be interested to explore quantitative trading, where decisions are executed programmatically based on predictions from trained models.

There are plenty of existing quantitative trading efforts used to analyze financial markets and formulate investment strategies. To create and execute such a strategy requires both historical and real-time data, which is difficult to obtain especially for retail investors. This competition will provide financial data for the Japanese market, allowing retail investors to analyze the market to the fullest extent.

Japan Exchange Group, Inc. (JPX) is a holding company operating one of the largest stock exchanges in the world, Tokyo Stock Exchange (TSE), and derivatives exchanges Osaka Exchange (OSE) and Tokyo Commodity Exchange (TOCOM). JPX is hosting this competition and is supported by AI technology company AlpacaJapan Co.,Ltd.
![cdsef](https://user-images.githubusercontent.com/33089347/161895114-5afe3777-1412-41a8-ad62-eb8a4c45905a.PNG)

This competition will compare your models against real future returns after the training phase is complete. The competition will involve building portfolios from the stocks eligible for predictions (around 2,000 stocks). Specifically, each participant ranks the stocks from highest to lowest expected returns and is evaluated on the difference in returns between the top and bottom 200 stocks. You'll have access to financial data from the Japanese market, such as stock information and historical stock prices to train and test your model.


All winning models will be made public so that other participants can learn from the outstanding models. Excellent models also may increase the interest in the market among retail investors, including those who want to practice quantitative trading. At the same time, you'll gain your own insights into programmatic investment methods and portfolio analysis―and you may even discover you have an affinity for the Japanese market.

**Evaluation**

Submissions are evaluated on the Sharpe Ratio of the daily spread returns. You will need to rank each stock active on a given day. The returns for a single day treat the 200 highest (e.g. 0 to 199) ranked stocks as purchased and the lowest (e.g. 1999 to 1800) ranked 200 stocks as shorted. The stocks are then weighted based on their ranks and the total returns for the portfolio are calculated assuming the stocks were purchased the next day and sold the day after that. You can find a python implementation of the metric here.

You must submit to this competition using the provided python time-series API, which ensures that models do not peek forward in time. To use the API, follow this template in Kaggle Notebooks:

**Code Tester**

import jpx_tokyo_market_prediction
env = jpx_tokyo_market_prediction.make_env()   # initialize the environment
iter_test = env.iter_test()    # an iterator which loops over the test files
for (prices, options, financials, trades, secondary_prices, sample_prediction) in iter_test:
    sample_prediction_df['Target'] = np.arange(len(sample_prediction))  # make your predictions here
    env.predict(sample_prediction_df)   # register your predictions
You will get an error if you:

Use ranks that are below zero or greater than or equal to the number of stocks for a given date.
Submit any duplicated ranks.
Change the order of the rows.

**Timeline**

This is a forecasting competition with an active training phase and a second period where models will be run against real market data.
Training Timeline

April 4, 2022 - Start Date

June 28, 2022 - Entry deadline. You must accept the competition rules before this date in order to compete.

June 28, 2022 - Team Merger deadline. This is the last day participants may join or merge teams.

July 5, 2022 - Final submission deadline.
All deadlines are at 11:59 PM UTC on the corresponding day unless otherwise noted. The competition organizers reserve the right to update the contest timeline if they deem it necessary.

**Code Requirements**

Submissions to this competition must be made through Notebooks. In order for the "Submit" button to be active after a commit, the following conditions must be met:

CPU Notebook <= 9 hours run-time

GPU Notebook <= 9 hours run-time

Internet access disabled

Freely & publicly available external data is allowed, including pre-trained models

Submission file must be named submission.csv. The API will generate this submission file for you.

Please see the Code Competition FAQ for more information on how to submit. And review the code debugging doc if you are encountering submission errors
