# Coinpaprika-API
This script uses the Coinpaprika API to fetch the top N cryptocurrencies by market capitalization
import requests

def get_top_cryptocurrencies(n):
    url = f'https://api.coinpaprika.com/v1/tickers/?start=1&limit={n}'
    response = requests.get(url)
    data = response.json()
    if isinstance(data, list):
        return data
    return None

# Example usage
top_n = 10

cryptocurrencies = get_top_cryptocurrencies(top_n)
if cryptocurrencies:
    print(f"Top {top_n} cryptocurrencies by market capitalization:")
    for currency in cryptocurrencies:
        print(f"Name: {currency['name']}")
        print(f"Symbol: {currency['symbol']}")
        print(f"Rank: {currency['rank']}")
        print(f"Market Cap: ${currency['market_cap_usd']}")
        print("------------------------")
else:
    print("Failed to retrieve top cryptocurrencies")
