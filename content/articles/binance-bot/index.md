+++
title = "Binance basics"
description = "Foundation of a binance bot with websockets"
author = "Piraeus West Jr."
date = "2022-04-24"
tags = ["Crypto", "bot", "python", "websockets"]
categories = ["Crypto", "Affiliates"]
[[images]]
  src = "img/skyscraper.jpg"
  alt = "Bitcoin image"
  stretch = "stretchH"
+++

# BOT BUILDING BASICS

I have been automating my crypto trading to prevent missing nightly lows or highs. You can determine support and resistance programmatically (more on that topic in a future post) and place take profit and stop loss limits on those levels. But a faster and easier way to start your crypto bot is by using the websockets package of Binance. 

## Use websockets to get ticker data

The advantage of websockets is that your program does not need to poll the webserver constantly, but it gets triggered everytime a change on the server happens. Therefore it is less computationally expensive and potentially more responsive.

Below code snippet is a simple skeleton application that shows the principle:


```
from binance.client import Client
from binance.enums import *
from binance.exceptions import BinanceAPIException, BinanceOrderException
from binance import ThreadedWebsocketManager


def ticker_handler(message):    
    if msg['e'] != 'error':    
            ticker = msg["s"]  
            value = float(msg['c'])     
            print(f'{ticker}: {value}')
        else:
            print('error')

twm = ThreadedWebsocketManager(api_key="", api_secret="")
twm.start()
sts = twm.start_symbol_ticker_socket(callback=ticker_handler, symbol="BTCUSDT")

```

If you do not yet have a Binance account, please consider supporting me by using this [affiliate link](https://accounts.binance.com/en/register?ref=376981966).

