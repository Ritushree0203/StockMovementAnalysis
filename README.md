# Reddit Sentiment Analysis for Stock Mentions

This project analyzes sentiment and mentions of stocks on Reddit, focusing on specific stocks like TSLA, NVDA, AMZN, AAPL, and MSFT.

## Prerequisites

- Python 3.7+
- pip (Python package installer)
- Jupyter Notebook

## Setup

1. Clone the repository or download the source code.

2. Navigate to the project directory:
   ```
   cd path/to/project
   ```

3. Create a virtual environment (optional but recommended):
   ```
   python -m venv venv
   source venv/bin/activate  # On Windows, use `venv\Scripts\activate`
   ```

4. Install the required packages:
   ```
   pip install -r requirements.txt
   ```

5. Install Jupyter Notebook if you haven't already:
   ```
   pip install jupyter
   ```

## Reddit API Setup

Before running the code, you need to set up your Reddit API credentials:

1. Go to https://www.reddit.com/prefs/apps
2. Click on "create app" or "create another app"
3. Fill in the details:
   - Name: Choose a name for your app
   - Select "script"
   - Description: Optional
   - About url: Optional
   - Redirect uri: http://localhost:8080
4. Click "create app"
5. Note down your client_id and client_secret

## Running the Code

The analysis is split into two main Jupyter notebook files. Follow these steps in order:

1. Open `dataCollect.ipynb`:
   ```
   jupyter notebook dataCollect.ipynb
   ```
   - Update the Reddit API credentials in the notebook:
     ```python
     reddit = praw.Reddit(
         client_id="YOUR_CLIENT_ID",
         client_secret="YOUR_CLIENT_SECRET",
         user_agent="YOUR_USER_AGENT"
     )
     ```
   - Run all cells in this notebook to collect data from Reddit.

2. After the data collection is complete, open and run `redditV2.ipynb`:
   ```
   jupyter notebook redditV2.ipynb
   ```
   - This notebook contains the sentiment analysis and visualization code.
   - Run all cells to perform the analysis on the collected data.

## Output

The `redditV2.ipynb` notebook will generate various visualizations and output, including:

- Sentiment scores for different stocks
- Frequency of stock mentions over time
- Correlation between sentiment and stock prices
- Word clouds of frequently mentioned terms

These will be displayed within the notebook and can be saved as image files if desired.

## Notes

- The analysis is based on Reddit posts collected during the data collection phase and may not reflect real-time data.
- Stock price data is fetched using the yfinance library and may have a slight delay.
- Sentiment analysis is performed using the VADER sentiment analyzer, which is specifically attuned to sentiments expressed in social media.

## Troubleshooting

If you encounter any issues with NLTK data, you may need to download additional NLTK resources. Run the following in a Python console:

```python
import nltk
nltk.download('punkt')
nltk.download('stopwords')
```

For any other issues, please check the error message and ensure all dependencies are correctly installed.

