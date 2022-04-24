+++
title = "Binance basics"
description = "Foundation of a binance bot with websocket"
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

Ik heb mijn crypto trading geautomatiseerd om het missen van nachtelijke low of highs te voorkomen. Je kan support en resistance programmatisch bepalen (meer over dat onderwerp in een toekomstige post) en profit en loss limits op die niveaus instellen. Maar een snellere en gemakkelijkere manier om je eerste cryptobots te maken, is door het Websockets-pakket van Binance te gebruiken.

## Gebruik websockets om koers data op te vragen bij Binance

Het voordeel van WebSockets is dat uw programma niet constant de webserver hoeft te pollen, maar elke keer geactiveerd wordt wanneer er een verandering op de server is. Daarom is het minder zwaar voor de CPU en mogelijk ook sneller qua reactietijd.

Onderstaande code Snippet is een eenvoudige applicatie die het principe toont:

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

Als je nog geen Binance account hebt, overweeg dan alsjeblieft om deze [affiliate link](https://accounts.binance.com/en/register?ref=376981966) te gebruiken.