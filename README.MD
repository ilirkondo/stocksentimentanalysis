# Stock Market Snetiment Analysis and Prediction: 
* Gather financial news articles, social media sentiment data, and historical stock prices. 
* Develop a sentiment analysis model to assess market sentiment's influence on stock price movements. 
* Predict stock price trends or volatility based on sentiment
  
## EODHD Document Classification Example:
```json
    {
        "date": "2025-03-10T22:15:00+00:00",
        "title": "Tesla CEO Elon Musk May Have Hit His Limit. That's Bad News for the Stock.",
        "content": "Tesla CEO Elon Musk met with Fox Business' Larry Kudlow on Monday. Investors probably won't like what they heard.\n\nContinue Reading\n\nView Comments",
        "link": "https://finance.yahoo.com/m/89528423-f8f4-3453-847a-8934ec39f194/tesla-ceo-elon-musk-may-have.html",
        "symbols": [
            "1TSLA.MI",
            "TL0.BE",
            "TL0.F",
            "TL0.XETRA",
            "TL01.F",
            "TSLA.MX",
            "TSLA.US",
            "TSLA34.SA"
        ],
        "tags": [],
        "sentiment": {
            "polarity": 0.361,
            "neg": 0,
            "neu": 0.898,
            "pos": 0.102
        }
    },
```
EODHD API provides insights into the emotional tone of the financial news. Here's how to interpret it:

* Polarity: This is a measure that calculates the overall sentiment, ranging from -1 (very negative) to 1 (very positive). A value of 0.361 indicates a slightly positive sentiment overall.

* Negative (neg): This represents the proportion of text that falls under a negative sentiment. A value of 0.058 means that only about 5.8% of the text is perceived as negative.

* Neutral (neu): This shows the proportion of text that is neither positive nor negative. With a value of 0.836, approximately 83.6% of the text is considered neutral.

* Positive (pos): This measures the proportion of text that is perceived as positive. A value of 0.106 indicates that about 10.6% of the text is seen as positive.

In summary, the sentiment of the financial news is slightly positive, with a significant portion being neutral. The negative sentiment is minimal.


# List of notebooks
1. definitions
2. sourcing_data
3. data_analysis
4. model_fitting

# Observations and Ideas for Improvement
* Model Overprediction:
  * The model tends to overpredict, likely due to the long look-back period.
    * Fine-Tuning the Look-Back Period: A one-month period might be optimal. Consider redoing fine-tuning with additional reg_alpha values.
* Feature Expansion:
  * Experiment with adding more features, such as:
    * Day-of-week
    * Negative, positive, and neutral news sentiments (beyond polarity)
    * Other stock performance metrics from different sources
* Incorporating News Data: Explore using news data from other sources, like social media.
* Sentiment Analysis: Use models like  [distilroberta](https://huggingface.co/mrm8488/distilroberta-finetuned-financial-news-sentiment-analysis) to calculate sentiments.
* Sentiment Polarity Calculation:
  * Conduct further research on calculating sentiment polarity from negative, positive, and neutral sentiment scores.
* Code Refactoring:
  * Refactor the code to reduce repetition and eliminate hard-coding.
* Run A/B test with other algorithms, such as time series forcasting, LSTM
---
* High-level requirements for productionizing the model:
  * Generalize the model for any ticker
  * Identify model *aging*
    * How frequent should the model get refreshed
  * Feature-store requirements
  * Latency requirements

## References
1. [EODHD](https://eodhd.com/)
2. [distilroberta](https://huggingface.co/mrm8488/distilroberta-finetuned-financial-news-sentiment-analysis)
3. [XGBoost](https://xgboost.readthedocs.io/en/stable/)
4. [Stock Price Forcasting](https://github.com/das-amlan/Stock-Price-Forecasting)
5. [Tweet Sentiment Analysis to Predict Stock Market, Christian Palomo](https://web.stanford.edu/class/archive/cs/cs224n/cs224n.1234/final-reports/final-report-170049613.pdf?t)
6. [Sentiment Analysis and Stock Data Prediction Using Financial News Headlines Approach, Shraddha R. Khonde et al.](https://www.iieta.org/journals/ria/paper/10.18280/ria.380325)