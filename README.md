# Complete List of Ticker Sectors in U.S. Stock Market

## Init
I was testing the use of some REST API calls and this is only a toy idea.
However, this is a relatively complete list of U.S. market stocks with
their corresponding sector ETF symbols. I thought this might be helpful
for some people.

## API
``` python
import yfinance as yf

def get_yf_sector(ticker):
    try:
        info = yf.Ticker(ticker).info
        if 'sector' in info:
            if info['sector'] == '':
                return 'N/A'
            return info['sector']
        elif 'quoteType' in info and 'ETF' in info['quoteType']:
            return 'ETF'
    except Exception as e:
        print(f'Failed to get sector from yfinance {ticker}: {e}')

    return 'N/A'

test_list = ['SPY', 'NVDA', 'AMD', 'TSLA']
for ticker in test_list:
    print(get_yf_sector(ticker))
```

As you can see, the real ETF tickers are marked with `ETF`.

## Contribute
If this is useful to you, please consider helping enlarge this list by adding
new tickers or modifying the incorrect sectors. However, please do NOT remove
tickers even they were out of the market now (for example `FB`) because then it 
will make the list incomplete. Also, do NOT add any `N/A` entries.
