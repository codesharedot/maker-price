# maker price

Get maker price in Python [https://pythonbasics.org](https://pythonbasics.org).
See [https://codesharedot.github.io/maker-price/](https://codesharedot.github.io/maker-price/)

```python
import requests
import json
from forex_python.converter import CurrencyRates
import os

c = CurrencyRates()
rate = c.get_rate('USD', 'EUR') 
print(rate)

maker_api_url = 'https://api.coinmarketcap.com/v1/ticker/maker/'
response = requests.get(maker_api_url)
response_json = response.json()
print(response_json)

for coin in response.json():
    price = coin.get('price_usd', 'U$S Price not provided')
    coin_price = float(('{0:.2f}').format(float(price)))
    print('$ ' + str(coin_price))
    
    coin_price_eur = float(('{0:.2f}').format(float(price)*rate))   
    print('€ ' + str(btc_price_eur))
    
    if coin_price_eur > 9000:
           os.system('notify-send trade btc')
           
```
