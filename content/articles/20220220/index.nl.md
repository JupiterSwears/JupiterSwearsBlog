+++
title = "Binance basics"
description = "Foundation of a binance bot with websocket"
author = "Piraeus West Jr."
date = "2022-02-20"
tags = ["Crypto", "bot", "python"]
categories = ["Crypto", "Affiliates"]
[[images]]
  src = "img/skyscraper.jpg"
  alt = "Bitcoin image"
  stretch = "stretchH"
+++

# BOT BUILDING BASICS

## Use websockets to get ticker data

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
