# NWCX API Routes

## Notes

These are the currently publicly available routes, they require no authentication and aren't rate limited, but don't take the piss.

## Endpoints

### User and Cash Info

#### GET /list/nations

Gives 25 of the nation type accounts registered in the exchange, along with their cash balances and net worths.
Headers: N/A
Example Response:

```json
{
  "Nations": [
    {
      "Name": "Kevlapodia",
      "CashInHand": 31000,
      "NetWorth": 31000
    },
    {
      "Name": "Sosonia",
      "CashInHand": 31000,
      "NetWorth": 31000
    },
    {
      "Name": "Frellor",
      "CashInHand": 31150,
      "NetWorth": 31150
    },
    {
      "Name": "Central Birdland",
      "CashInHand": 31100,
      "NetWorth": 31100
    },
    {
      "Name": "His Excellency",
      "CashInHand": 10100,
      "NetWorth": 10100
    },
    {
      "Name": "Gelezia",
      "CashInHand": 10034.5,
      "NetWorth": 10034.5
    },
    {
      "Name": "Gallaton",
      "CashInHand": 0.77,
      "NetWorth": 17291.75
    }
  ]
}
```

#### GET /cash/details/{acctName}

Gives the cash balances, net worth and all cash transactions (sent and received) of the specified account.
Path Values: "acctName" is the, non-sluggified, name of any account, nation or region, registered on the exchange.
Example Response:
Request: /cash/details/Gallaton

```json
{
  "handCash": 0.77,
  "escrowCash": 0,
  "netWorth": 17291.75,
  "transactions": [
    {
      "timecode": "2025-01-06T21:35:35Z",
      "sender": "Gallaton",
      "receiver": "Simdemocracy",
      "value": 0.66,
      "message": "SMD Trade"
    },
    {
      "timecode": "2025-01-06T21:35:27Z",
      "sender": "Gallaton",
      "receiver": "Simdemocracy",
      "value": 7.26,
      "message": "SMD Trade"
    },
    {
      "timecode": "2025-01-06T21:33:38Z",
      "sender": "Gallaton",
      "receiver": "Simdemocracy",
      "value": 15.4,
      "message": "SMD Trade"
    },
    {
      "timecode": "2025-01-06T21:00:06Z",
      "sender": "Gallaton",
      "receiver": "Aurora",
      "value": 79.44,
      "message": "AUR Trade"
    },
    {
      "timecode": "2025-01-06T20:59:55Z",
      "sender": "Gallaton",
      "receiver": "Aurora",
      "value": 503.12,
      "message": "AUR Trade"
    },
    {
      "timecode": "2025-01-06T20:59:21Z",
      "sender": "Gallaton",
      "receiver": "Aurora",
      "value": 3573.45,
      "message": "AUR Trade"
    },
    {
      "timecode": "2025-01-06T20:53:17Z",
      "sender": "New West Conifer",
      "receiver": "Gallaton",
      "value": 2000,
      "message": "NWC Trade"
    },
    {
      "timecode": "2025-01-06T20:48:40Z",
      "sender": "New West Conifer",
      "receiver": "Gallaton",
      "value": 2000,
      "message": "NWC Trade"
    },
    {
      "timecode": "2025-01-06T20:44:21Z",
      "sender": "Gallaton",
      "receiver": "Britannia",
      "value": 791.35,
      "message": "BRIT Trade"
    }
  ]
}
```

#### /cash/quick/{acctName}

Gives the account name and cash balance of the specified user.
Path Values: "acctName" is the non-sluggified name of any nation or region registered on the exchange.
Headers: N/A
Example Response:
Request: GET /cash/quick/Gallaton

```json
{ "AcctName": "Gallaton", "CashInHand": 0.77 }
```

### Stocks and Shares Info

#### GET /shares/quote

Gives a short quote for all listed shares on the exchange.
Headers: N/A
Example Response:

```json
{
    "allStocks": [
        {
            "ticker": "COL",
            "region": "Commonwealth of Liberty",
            "marketPrice": 353.61,
            "marketCap": 353605950,
            "totalVolume": 1000000
        },
        {
            "ticker": "TNP",
            "region": "The North Pacific",
            "marketPrice": 347.56,
            "marketCap": 347564160,
            "totalVolume": 1000000
        },
        {
            "ticker": "CMC",
            "region": "Communist Cartel",
            "marketPrice": 298.03,
            "marketCap": 298030880,
            "totalVolume": 1000000
        },
        {
            "ticker": "NWI",
            "region": "New West Indies",
            "marketPrice": 277.37,
            "marketCap": 277372700,
            "totalVolume": 1000000
        },
        {
            "ticker": "LNM",
            "region": "Laraniem",
            "marketPrice": 252.49,
            "marketCap": 252486380,
            "totalVolume": 1000000
        },
        {
            "ticker": "BRD",
            "region": "Blue Ridge",
            "marketPrice": 231.71,
            "marketCap": 231714190,
            "totalVolume": 1000000
        },
        {
            "ticker": "RNB",
            "region": "The Region That Has No Big Banks",
            "marketPrice": 225.8,
            "marketCap": 225801520,
            "totalVolume": 1000000
        },
        {
            "ticker": "NUK",
            "region": "New United Kingdom",
            "marketPrice": 218.9,
            "marketCap": 218903460,
            "totalVolume": 1000000
        }
        {
            "ticker": "REF",
            "region": "Refugia",
            "marketPrice": 172.76,
            "marketCap": 172764940,
            "totalVolume": 1000000
        },
        {
            "ticker": "NWC",
            "region": "New West Conifer",
            "marketPrice": 171.48,
            "marketCap": 171477260,
            "totalVolume": 1000000
        },
        {
            "ticker": "BRIT",
            "region": "Britannia",
            "marketPrice": 167.03,
            "marketCap": 167032700,
            "totalVolume": 1000000
        }
    ]
}
```

#### GET /shares/quote/{ticker}

Gives a short quote for the specified ticker.
Path Values: "ticker" is the ticker for a region's stock on the exchange.
Headers: N/A
Example Response
Request: /shares/quote/NWC

```json
{
  "ticker": "NWC",
  "region": "New West Conifer",
  "marketPrice": 171.48,
  "marketCap": 171477260,
  "totalVolume": 1000000
}
```

#### GET /shares/book/{ticker}

Gives the current order book for the specified ticker.
Path Values: "ticker" is the ticker for a region's stock on the exchange.
Headers: N/A
Example Response:
Request: /shares/book/NWC

```json
{
  "CurrentQuote": {
    "ticker": "NWC",
    "region": "New West Conifer",
    "marketPrice": 171.48,
    "marketCap": 171477260,
    "totalVolume": 1000000
  },
  "BookDepth": 2,
  "Buys": null,
  "Sells": [
    {
      "TradeId": "40",
      "Ticker": "NWC",
      "Sender": "New West Conifer",
      "Direction": "sell",
      "Quantity": 299975,
      "PriceType": "market",
      "Price": 171.48
    },
    {
      "TradeId": "49",
      "Ticker": "NWC",
      "Sender": "Gallaton",
      "Direction": "sell",
      "Quantity": 10,
      "PriceType": "limit",
      "Price": 200
    }
  ]
}
```

#### GET /shares/trade/{tradeId}

Gives the details of a specified trade.
Path Values: "tradeId" is the numbered trade id
Headers: N/A
Example Response
Request: /shares/trade/40

```json
{
  "TradeId": "",
  "Ticker": "NWC",
  "Sender": "New West Conifer",
  "Direction": "sell",
  "Quantity": 299975,
  "PriceType": "market",
  "Price": 171.48
}
```

#### GET /shares/recentprices/{ticker}

Gives the last of half-hourly logged prices.
Path values: "ticker" is the ticker for a region's stock on the exchange
Headers: N/A
Example Response
Request: /shares/recentprices/NWC

```json
{
  "RecentPrice": [
    {
      "Timecode": "2025-01-04T01:30:00Z",
      "LogPrice": 186.28
    },
    {
      "Timecode": "2025-01-04T02:00:00Z",
      "LogPrice": 186.28
    },
    {
      "Timecode": "2025-01-04T02:30:00Z",
      "LogPrice": 186.28
    },
    {
      "Timecode": "2025-01-04T03:00:00Z",
      "LogPrice": 186.28
    },
    {
      "Timecode": "2025-01-04T03:30:00Z",
      "LogPrice": 186.28
    },
    {
      "Timecode": "2025-01-04T04:00:00Z",
      "LogPrice": 186.28
    },
    {
      "Timecode": "2025-01-04T04:30:00Z",
      "LogPrice": 186.28
    },
    {
      "Timecode": "2025-01-04T05:00:00Z",
      "LogPrice": 186.28
    },
    {
      "Timecode": "2025-01-04T05:30:00Z",
      "LogPrice": 186.28
    },
    {
      "Timecode": "2025-01-04T06:00:00Z",
      "LogPrice": 186.28
    },
    {
      "Timecode": "2025-01-04T06:30:00Z",
      "LogPrice": 186.28
    },
    {
      "Timecode": "2025-01-04T07:00:00Z",
      "LogPrice": 186.28
    },
    {
      "Timecode": "2025-01-04T07:30:00Z",
      "LogPrice": 186.28
    },
    {
      "Timecode": "2025-01-04T08:00:00Z",
      "LogPrice": 186.28
    },
    {
      "Timecode": "2025-01-04T08:30:00Z",
      "LogPrice": 186.28
    },
    {
      "Timecode": "2025-01-04T09:00:00Z",
      "LogPrice": 186.28
    },
    {
      "Timecode": "2025-01-04T09:30:00Z",
      "LogPrice": 186.28
    },
    {
      "Timecode": "2025-01-04T10:00:00Z",
      "LogPrice": 186.28
    },
    {
      "Timecode": "2025-01-04T10:30:00Z",
      "LogPrice": 186.28
    },
    {
      "Timecode": "2025-01-04T11:00:00Z",
      "LogPrice": 186.28
    },
    {
      "Timecode": "2025-01-04T11:30:00Z",
      "LogPrice": 186.28
    },
    {
      "Timecode": "2025-01-04T12:00:00Z",
      "LogPrice": 186.28
    },
    {
      "Timecode": "2025-01-04T12:30:00Z",
      "LogPrice": 186.28
    },
    {
      "Timecode": "2025-01-04T13:00:00Z",
      "LogPrice": 186.28
    },
    {
      "Timecode": "2025-01-04T13:30:00Z",
      "LogPrice": 186.28
    },
    {
      "Timecode": "2025-01-04T14:00:00Z",
      "LogPrice": 186.28
    },
    {
      "Timecode": "2025-01-04T14:30:00Z",
      "LogPrice": 186.28
    },
    {
      "Timecode": "2025-01-04T15:00:00Z",
      "LogPrice": 186.28
    },
    {
      "Timecode": "2025-01-04T15:30:00Z",
      "LogPrice": 186.28
    },
    {
      "Timecode": "2025-01-04T16:00:00Z",
      "LogPrice": 186.28
    },
    {
      "Timecode": "2025-01-04T16:30:00Z",
      "LogPrice": 186.28
    },
    {
      "Timecode": "2025-01-04T17:00:00Z",
      "LogPrice": 186.28
    },
    {
      "Timecode": "2025-01-04T17:30:00Z",
      "LogPrice": 186.28
    },
    {
      "Timecode": "2025-01-04T18:00:00Z",
      "LogPrice": 186.28
    },
    {
      "Timecode": "2025-01-04T18:30:00Z",
      "LogPrice": 186.28
    },
    {
      "Timecode": "2025-01-04T19:00:00Z",
      "LogPrice": 186.28
    },
    {
      "Timecode": "2025-01-04T19:30:00Z",
      "LogPrice": 186.28
    },
    {
      "Timecode": "2025-01-04T20:00:00Z",
      "LogPrice": 186.28
    },
    {
      "Timecode": "2025-01-04T20:30:00Z",
      "LogPrice": 186.28
    },
    {
      "Timecode": "2025-01-04T21:00:00Z",
      "LogPrice": 186.28
    },
    {
      "Timecode": "2025-01-04T21:30:00Z",
      "LogPrice": 186.28
    },
    {
      "Timecode": "2025-01-04T22:00:00Z",
      "LogPrice": 186.28
    },
    {
      "Timecode": "2025-01-04T22:30:00Z",
      "LogPrice": 186.28
    },
    {
      "Timecode": "2025-01-04T23:00:00Z",
      "LogPrice": 186.28
    },
    {
      "Timecode": "2025-01-04T23:30:00Z",
      "LogPrice": 186.28
    },
    {
      "Timecode": "2025-01-05T00:00:00Z",
      "LogPrice": 186.28
    },
    {
      "Timecode": "2025-01-05T00:30:00Z",
      "LogPrice": 186.97
    },
    {
      "Timecode": "2025-01-05T01:00:00Z",
      "LogPrice": 186.97
    },
    {
      "Timecode": "2025-01-05T01:30:00Z",
      "LogPrice": 186.97
    },
    {
      "Timecode": "2025-01-05T02:00:00Z",
      "LogPrice": 186.97
    },
    {
      "Timecode": "2025-01-05T02:30:00Z",
      "LogPrice": 186.97
    },
    {
      "Timecode": "2025-01-05T03:00:00Z",
      "LogPrice": 186.97
    },
    {
      "Timecode": "2025-01-05T03:30:00Z",
      "LogPrice": 186.97
    },
    {
      "Timecode": "2025-01-05T04:00:00Z",
      "LogPrice": 186.97
    },
    {
      "Timecode": "2025-01-05T04:30:00Z",
      "LogPrice": 186.97
    },
    {
      "Timecode": "2025-01-05T05:00:00Z",
      "LogPrice": 186.97
    },
    {
      "Timecode": "2025-01-05T05:30:00Z",
      "LogPrice": 186.97
    },
    {
      "Timecode": "2025-01-05T06:00:00Z",
      "LogPrice": 186.97
    },
    {
      "Timecode": "2025-01-05T06:30:00Z",
      "LogPrice": 186.97
    },
    {
      "Timecode": "2025-01-05T07:00:00Z",
      "LogPrice": 186.97
    },
    {
      "Timecode": "2025-01-05T07:30:00Z",
      "LogPrice": 186.97
    },
    {
      "Timecode": "2025-01-05T08:00:00Z",
      "LogPrice": 186.97
    },
    {
      "Timecode": "2025-01-05T08:30:00Z",
      "LogPrice": 186.97
    },
    {
      "Timecode": "2025-01-05T09:00:00Z",
      "LogPrice": 186.97
    },
    {
      "Timecode": "2025-01-05T09:30:00Z",
      "LogPrice": 186.97
    },
    {
      "Timecode": "2025-01-05T10:00:00Z",
      "LogPrice": 186.97
    },
    {
      "Timecode": "2025-01-05T10:30:00Z",
      "LogPrice": 186.97
    },
    {
      "Timecode": "2025-01-05T11:00:00Z",
      "LogPrice": 186.97
    },
    {
      "Timecode": "2025-01-05T11:30:00Z",
      "LogPrice": 186.97
    },
    {
      "Timecode": "2025-01-05T12:00:00Z",
      "LogPrice": 186.97
    },
    {
      "Timecode": "2025-01-05T12:30:00Z",
      "LogPrice": 186.97
    },
    {
      "Timecode": "2025-01-05T13:00:00Z",
      "LogPrice": 186.97
    },
    {
      "Timecode": "2025-01-05T13:30:00Z",
      "LogPrice": 186.97
    },
    {
      "Timecode": "2025-01-05T14:00:00Z",
      "LogPrice": 186.97
    },
    {
      "Timecode": "2025-01-05T14:30:00Z",
      "LogPrice": 186.97
    },
    {
      "Timecode": "2025-01-05T15:00:00Z",
      "LogPrice": 186.97
    },
    {
      "Timecode": "2025-01-05T15:30:00Z",
      "LogPrice": 186.97
    },
    {
      "Timecode": "2025-01-05T16:00:00Z",
      "LogPrice": 186.97
    },
    {
      "Timecode": "2025-01-05T16:30:00Z",
      "LogPrice": 186.97
    },
    {
      "Timecode": "2025-01-05T17:00:00Z",
      "LogPrice": 186.97
    },
    {
      "Timecode": "2025-01-05T17:30:00Z",
      "LogPrice": 186.97
    },
    {
      "Timecode": "2025-01-05T18:00:00Z",
      "LogPrice": 186.97
    },
    {
      "Timecode": "2025-01-05T18:30:00Z",
      "LogPrice": 186.97
    },
    {
      "Timecode": "2025-01-05T19:00:00Z",
      "LogPrice": 186.97
    },
    {
      "Timecode": "2025-01-05T19:30:00Z",
      "LogPrice": 186.97
    },
    {
      "Timecode": "2025-01-05T20:00:00Z",
      "LogPrice": 186.97
    },
    {
      "Timecode": "2025-01-05T20:30:00Z",
      "LogPrice": 186.97
    },
    {
      "Timecode": "2025-01-05T21:00:00Z",
      "LogPrice": 186.97
    },
    {
      "Timecode": "2025-01-05T21:30:00Z",
      "LogPrice": 186.97
    },
    {
      "Timecode": "2025-01-05T22:00:00Z",
      "LogPrice": 186.97
    },
    {
      "Timecode": "2025-01-05T22:30:00Z",
      "LogPrice": 186.97
    },
    {
      "Timecode": "2025-01-05T23:00:00Z",
      "LogPrice": 186.97
    },
    {
      "Timecode": "2025-01-05T23:30:00Z",
      "LogPrice": 186.97
    },
    {
      "Timecode": "2025-01-06T00:00:00Z",
      "LogPrice": 186.97
    },
    {
      "Timecode": "2025-01-06T00:30:00Z",
      "LogPrice": 187.31
    },
    {
      "Timecode": "2025-01-06T01:00:00Z",
      "LogPrice": 187.31
    },
    {
      "Timecode": "2025-01-06T01:30:00Z",
      "LogPrice": 187.31
    },
    {
      "Timecode": "2025-01-06T02:00:00Z",
      "LogPrice": 187.31
    },
    {
      "Timecode": "2025-01-06T02:30:00Z",
      "LogPrice": 187.31
    },
    {
      "Timecode": "2025-01-06T14:00:00Z",
      "LogPrice": 187.31
    },
    {
      "Timecode": "2025-01-06T14:30:00Z",
      "LogPrice": 187.31
    },
    {
      "Timecode": "2025-01-06T15:00:00Z",
      "LogPrice": 187.31
    },
    {
      "Timecode": "2025-01-06T15:30:00Z",
      "LogPrice": 187.31
    },
    {
      "Timecode": "2025-01-06T16:00:00Z",
      "LogPrice": 187.31
    },
    {
      "Timecode": "2025-01-06T16:30:00Z",
      "LogPrice": 187.31
    },
    {
      "Timecode": "2025-01-06T17:00:00Z",
      "LogPrice": 187.31
    },
    {
      "Timecode": "2025-01-06T17:30:00Z",
      "LogPrice": 187.31
    },
    {
      "Timecode": "2025-01-06T18:00:00Z",
      "LogPrice": 187.31
    },
    {
      "Timecode": "2025-01-06T18:30:00Z",
      "LogPrice": 187.31
    },
    {
      "Timecode": "2025-01-06T19:00:00Z",
      "LogPrice": 187.31
    },
    {
      "Timecode": "2025-01-06T19:30:00Z",
      "LogPrice": 187.31
    },
    {
      "Timecode": "2025-01-06T20:00:00Z",
      "LogPrice": 187.31
    },
    {
      "Timecode": "2025-01-06T20:30:00Z",
      "LogPrice": 187.31
    },
    {
      "Timecode": "2025-01-06T21:00:00Z",
      "LogPrice": 187.32
    },
    {
      "Timecode": "2025-01-06T21:30:00Z",
      "LogPrice": 187.32
    },
    {
      "Timecode": "2025-01-06T22:00:00Z",
      "LogPrice": 187.32
    },
    {
      "Timecode": "2025-01-06T22:30:00Z",
      "LogPrice": 187.32
    },
    {
      "Timecode": "2025-01-06T23:00:00Z",
      "LogPrice": 187.32
    },
    {
      "Timecode": "2025-01-06T23:30:00Z",
      "LogPrice": 187.32
    },
    {
      "Timecode": "2025-01-07T00:00:00Z",
      "LogPrice": 187.32
    },
    {
      "Timecode": "2025-01-07T00:30:00Z",
      "LogPrice": 172.07
    },
    {
      "Timecode": "2025-01-07T01:00:00Z",
      "LogPrice": 172.07
    },
    {
      "Timecode": "2025-01-07T01:30:00Z",
      "LogPrice": 172.07
    },
    {
      "Timecode": "2025-01-07T02:00:00Z",
      "LogPrice": 172.07
    },
    {
      "Timecode": "2025-01-07T02:30:00Z",
      "LogPrice": 172.07
    },
    {
      "Timecode": "2025-01-07T03:00:00Z",
      "LogPrice": 172.07
    },
    {
      "Timecode": "2025-01-07T03:30:00Z",
      "LogPrice": 172.07
    },
    {
      "Timecode": "2025-01-07T04:00:00Z",
      "LogPrice": 172.07
    },
    {
      "Timecode": "2025-01-07T04:30:00Z",
      "LogPrice": 172.07
    },
    {
      "Timecode": "2025-01-07T05:00:00Z",
      "LogPrice": 172.07
    },
    {
      "Timecode": "2025-01-07T05:30:00Z",
      "LogPrice": 172.07
    },
    {
      "Timecode": "2025-01-07T06:00:00Z",
      "LogPrice": 172.07
    },
    {
      "Timecode": "2025-01-07T06:30:00Z",
      "LogPrice": 172.07
    },
    {
      "Timecode": "2025-01-07T07:00:00Z",
      "LogPrice": 172.07
    },
    {
      "Timecode": "2025-01-07T07:30:00Z",
      "LogPrice": 172.07
    },
    {
      "Timecode": "2025-01-07T08:00:00Z",
      "LogPrice": 172.07
    },
    {
      "Timecode": "2025-01-07T08:30:00Z",
      "LogPrice": 172.07
    },
    {
      "Timecode": "2025-01-07T09:00:00Z",
      "LogPrice": 172.07
    },
    {
      "Timecode": "2025-01-07T09:30:00Z",
      "LogPrice": 172.07
    },
    {
      "Timecode": "2025-01-07T10:00:00Z",
      "LogPrice": 172.07
    },
    {
      "Timecode": "2025-01-07T10:30:00Z",
      "LogPrice": 172.07
    },
    {
      "Timecode": "2025-01-07T11:00:00Z",
      "LogPrice": 172.07
    },
    {
      "Timecode": "2025-01-07T11:30:00Z",
      "LogPrice": 172.07
    },
    {
      "Timecode": "2025-01-07T12:00:00Z",
      "LogPrice": 172.07
    },
    {
      "Timecode": "2025-01-07T12:30:00Z",
      "LogPrice": 172.07
    },
    {
      "Timecode": "2025-01-07T13:00:00Z",
      "LogPrice": 172.07
    },
    {
      "Timecode": "2025-01-07T13:30:00Z",
      "LogPrice": 172.07
    },
    {
      "Timecode": "2025-01-07T14:00:00Z",
      "LogPrice": 172.07
    },
    {
      "Timecode": "2025-01-07T14:30:00Z",
      "LogPrice": 172.07
    },
    {
      "Timecode": "2025-01-07T15:00:00Z",
      "LogPrice": 172.07
    },
    {
      "Timecode": "2025-01-07T15:30:00Z",
      "LogPrice": 172.07
    },
    {
      "Timecode": "2025-01-07T16:00:00Z",
      "LogPrice": 172.07
    },
    {
      "Timecode": "2025-01-07T16:30:00Z",
      "LogPrice": 172.07
    },
    {
      "Timecode": "2025-01-07T17:00:00Z",
      "LogPrice": 172.07
    },
    {
      "Timecode": "2025-01-07T17:30:00Z",
      "LogPrice": 172.07
    },
    {
      "Timecode": "2025-01-07T18:00:00Z",
      "LogPrice": 172.07
    },
    {
      "Timecode": "2025-01-07T18:30:00Z",
      "LogPrice": 172.07
    },
    {
      "Timecode": "2025-01-07T19:00:00Z",
      "LogPrice": 172.07
    },
    {
      "Timecode": "2025-01-07T19:30:00Z",
      "LogPrice": 172.07
    },
    {
      "Timecode": "2025-01-07T20:00:00Z",
      "LogPrice": 172.07
    },
    {
      "Timecode": "2025-01-07T20:30:00Z",
      "LogPrice": 172.07
    },
    {
      "Timecode": "2025-01-07T21:00:00Z",
      "LogPrice": 172.07
    },
    {
      "Timecode": "2025-01-07T21:30:00Z",
      "LogPrice": 172.07
    },
    {
      "Timecode": "2025-01-07T22:00:00Z",
      "LogPrice": 172.07
    },
    {
      "Timecode": "2025-01-07T22:30:00Z",
      "LogPrice": 172.07
    },
    {
      "Timecode": "2025-01-07T23:00:00Z",
      "LogPrice": 172.07
    },
    {
      "Timecode": "2025-01-07T23:30:00Z",
      "LogPrice": 172.07
    },
    {
      "Timecode": "2025-01-08T00:00:00Z",
      "LogPrice": 172.07
    },
    {
      "Timecode": "2025-01-08T00:30:00Z",
      "LogPrice": 177.73
    },
    {
      "Timecode": "2025-01-08T01:00:00Z",
      "LogPrice": 177.73
    },
    {
      "Timecode": "2025-01-08T01:30:00Z",
      "LogPrice": 177.73
    },
    {
      "Timecode": "2025-01-08T02:00:00Z",
      "LogPrice": 177.73
    },
    {
      "Timecode": "2025-01-08T02:30:00Z",
      "LogPrice": 177.73
    },
    {
      "Timecode": "2025-01-08T03:00:00Z",
      "LogPrice": 177.73
    },
    {
      "Timecode": "2025-01-08T03:30:00Z",
      "LogPrice": 177.73
    },
    {
      "Timecode": "2025-01-08T04:00:00Z",
      "LogPrice": 177.73
    },
    {
      "Timecode": "2025-01-08T04:30:00Z",
      "LogPrice": 177.73
    },
    {
      "Timecode": "2025-01-08T05:00:00Z",
      "LogPrice": 177.73
    },
    {
      "Timecode": "2025-01-08T05:30:00Z",
      "LogPrice": 177.73
    },
    {
      "Timecode": "2025-01-08T06:00:00Z",
      "LogPrice": 177.73
    },
    {
      "Timecode": "2025-01-08T06:30:00Z",
      "LogPrice": 177.73
    },
    {
      "Timecode": "2025-01-08T07:00:00Z",
      "LogPrice": 177.73
    },
    {
      "Timecode": "2025-01-08T07:30:00Z",
      "LogPrice": 177.73
    },
    {
      "Timecode": "2025-01-08T08:00:00Z",
      "LogPrice": 177.73
    },
    {
      "Timecode": "2025-01-08T08:30:00Z",
      "LogPrice": 177.73
    },
    {
      "Timecode": "2025-01-08T09:00:00Z",
      "LogPrice": 177.73
    },
    {
      "Timecode": "2025-01-08T09:30:00Z",
      "LogPrice": 177.73
    },
    {
      "Timecode": "2025-01-08T10:00:00Z",
      "LogPrice": 177.73
    },
    {
      "Timecode": "2025-01-08T10:30:00Z",
      "LogPrice": 177.73
    },
    {
      "Timecode": "2025-01-08T11:00:00Z",
      "LogPrice": 177.73
    },
    {
      "Timecode": "2025-01-08T11:30:00Z",
      "LogPrice": 177.73
    },
    {
      "Timecode": "2025-01-08T12:00:00Z",
      "LogPrice": 177.73
    },
    {
      "Timecode": "2025-01-08T12:30:00Z",
      "LogPrice": 177.73
    },
    {
      "Timecode": "2025-01-08T13:00:00Z",
      "LogPrice": 177.73
    },
    {
      "Timecode": "2025-01-08T13:30:00Z",
      "LogPrice": 177.73
    },
    {
      "Timecode": "2025-01-08T14:00:00Z",
      "LogPrice": 177.73
    },
    {
      "Timecode": "2025-01-08T14:30:00Z",
      "LogPrice": 177.73
    },
    {
      "Timecode": "2025-01-08T15:00:00Z",
      "LogPrice": 177.73
    },
    {
      "Timecode": "2025-01-08T15:30:00Z",
      "LogPrice": 177.73
    },
    {
      "Timecode": "2025-01-08T16:00:00Z",
      "LogPrice": 177.73
    },
    {
      "Timecode": "2025-01-08T16:30:00Z",
      "LogPrice": 177.73
    },
    {
      "Timecode": "2025-01-08T17:00:00Z",
      "LogPrice": 177.73
    },
    {
      "Timecode": "2025-01-08T17:30:00Z",
      "LogPrice": 177.73
    },
    {
      "Timecode": "2025-01-08T18:00:00Z",
      "LogPrice": 177.73
    },
    {
      "Timecode": "2025-01-08T18:30:00Z",
      "LogPrice": 177.73
    },
    {
      "Timecode": "2025-01-08T19:00:00Z",
      "LogPrice": 177.73
    },
    {
      "Timecode": "2025-01-08T19:30:00Z",
      "LogPrice": 177.73
    },
    {
      "Timecode": "2025-01-08T20:00:00Z",
      "LogPrice": 177.73
    },
    {
      "Timecode": "2025-01-08T20:30:00Z",
      "LogPrice": 177.73
    },
    {
      "Timecode": "2025-01-08T21:00:00Z",
      "LogPrice": 177.73
    },
    {
      "Timecode": "2025-01-08T21:30:00Z",
      "LogPrice": 177.73
    },
    {
      "Timecode": "2025-01-08T22:00:00Z",
      "LogPrice": 177.73
    },
    {
      "Timecode": "2025-01-08T22:30:00Z",
      "LogPrice": 177.73
    },
    {
      "Timecode": "2025-01-08T23:00:00Z",
      "LogPrice": 177.73
    },
    {
      "Timecode": "2025-01-08T23:30:00Z",
      "LogPrice": 177.73
    },
    {
      "Timecode": "2025-01-09T00:00:00Z",
      "LogPrice": 177.73
    },
    {
      "Timecode": "2025-01-09T00:30:00Z",
      "LogPrice": 177.92
    },
    {
      "Timecode": "2025-01-09T01:00:00Z",
      "LogPrice": 177.92
    },
    {
      "Timecode": "2025-01-09T01:30:00Z",
      "LogPrice": 177.92
    },
    {
      "Timecode": "2025-01-09T02:00:00Z",
      "LogPrice": 177.92
    },
    {
      "Timecode": "2025-01-09T02:30:00Z",
      "LogPrice": 177.92
    },
    {
      "Timecode": "2025-01-09T03:00:00Z",
      "LogPrice": 177.92
    },
    {
      "Timecode": "2025-01-09T03:30:00Z",
      "LogPrice": 177.92
    },
    {
      "Timecode": "2025-01-09T04:00:00Z",
      "LogPrice": 177.92
    },
    {
      "Timecode": "2025-01-09T04:30:00Z",
      "LogPrice": 177.92
    },
    {
      "Timecode": "2025-01-09T05:00:00Z",
      "LogPrice": 177.92
    },
    {
      "Timecode": "2025-01-09T05:30:00Z",
      "LogPrice": 177.92
    },
    {
      "Timecode": "2025-01-09T06:00:00Z",
      "LogPrice": 177.92
    },
    {
      "Timecode": "2025-01-09T06:30:00Z",
      "LogPrice": 177.92
    },
    {
      "Timecode": "2025-01-09T07:00:00Z",
      "LogPrice": 177.92
    },
    {
      "Timecode": "2025-01-09T07:30:00Z",
      "LogPrice": 177.92
    },
    {
      "Timecode": "2025-01-09T08:00:00Z",
      "LogPrice": 177.92
    },
    {
      "Timecode": "2025-01-09T08:30:00Z",
      "LogPrice": 177.92
    },
    {
      "Timecode": "2025-01-09T09:00:00Z",
      "LogPrice": 177.92
    },
    {
      "Timecode": "2025-01-09T09:30:00Z",
      "LogPrice": 177.92
    },
    {
      "Timecode": "2025-01-09T10:00:00Z",
      "LogPrice": 177.92
    },
    {
      "Timecode": "2025-01-09T10:30:00Z",
      "LogPrice": 177.92
    },
    {
      "Timecode": "2025-01-09T11:00:00Z",
      "LogPrice": 177.92
    },
    {
      "Timecode": "2025-01-09T11:30:00Z",
      "LogPrice": 177.92
    },
    {
      "Timecode": "2025-01-09T12:00:00Z",
      "LogPrice": 177.92
    },
    {
      "Timecode": "2025-01-09T12:30:00Z",
      "LogPrice": 177.92
    },
    {
      "Timecode": "2025-01-09T13:00:00Z",
      "LogPrice": 177.92
    },
    {
      "Timecode": "2025-01-09T13:30:00Z",
      "LogPrice": 177.92
    },
    {
      "Timecode": "2025-01-09T14:00:00Z",
      "LogPrice": 177.92
    },
    {
      "Timecode": "2025-01-09T14:30:00Z",
      "LogPrice": 177.92
    },
    {
      "Timecode": "2025-01-09T15:00:00Z",
      "LogPrice": 177.92
    },
    {
      "Timecode": "2025-01-09T15:30:00Z",
      "LogPrice": 177.92
    },
    {
      "Timecode": "2025-01-09T16:00:00Z",
      "LogPrice": 177.92
    },
    {
      "Timecode": "2025-01-09T16:30:00Z",
      "LogPrice": 177.92
    },
    {
      "Timecode": "2025-01-09T17:00:00Z",
      "LogPrice": 177.92
    },
    {
      "Timecode": "2025-01-09T17:30:00Z",
      "LogPrice": 177.92
    },
    {
      "Timecode": "2025-01-09T18:00:00Z",
      "LogPrice": 177.92
    },
    {
      "Timecode": "2025-01-09T18:30:00Z",
      "LogPrice": 177.92
    },
    {
      "Timecode": "2025-01-09T19:00:00Z",
      "LogPrice": 177.92
    },
    {
      "Timecode": "2025-01-09T19:30:00Z",
      "LogPrice": 177.92
    },
    {
      "Timecode": "2025-01-09T20:00:00Z",
      "LogPrice": 177.92
    },
    {
      "Timecode": "2025-01-09T20:30:00Z",
      "LogPrice": 177.92
    },
    {
      "Timecode": "2025-01-09T21:00:00Z",
      "LogPrice": 177.92
    },
    {
      "Timecode": "2025-01-09T21:30:00Z",
      "LogPrice": 177.92
    },
    {
      "Timecode": "2025-01-09T22:00:00Z",
      "LogPrice": 177.92
    },
    {
      "Timecode": "2025-01-09T22:30:00Z",
      "LogPrice": 177.92
    },
    {
      "Timecode": "2025-01-09T23:00:00Z",
      "LogPrice": 177.92
    },
    {
      "Timecode": "2025-01-09T23:30:00Z",
      "LogPrice": 177.92
    },
    {
      "Timecode": "2025-01-10T00:00:00Z",
      "LogPrice": 177.92
    },
    {
      "Timecode": "2025-01-10T00:30:00Z",
      "LogPrice": 177.89
    },
    {
      "Timecode": "2025-01-10T01:00:00Z",
      "LogPrice": 177.89
    },
    {
      "Timecode": "2025-01-10T01:30:00Z",
      "LogPrice": 177.89
    },
    {
      "Timecode": "2025-01-10T02:00:00Z",
      "LogPrice": 177.89
    },
    {
      "Timecode": "2025-01-10T02:30:00Z",
      "LogPrice": 177.89
    },
    {
      "Timecode": "2025-01-10T03:00:00Z",
      "LogPrice": 177.89
    },
    {
      "Timecode": "2025-01-10T03:30:00Z",
      "LogPrice": 177.89
    },
    {
      "Timecode": "2025-01-10T04:00:00Z",
      "LogPrice": 177.89
    },
    {
      "Timecode": "2025-01-10T04:30:00Z",
      "LogPrice": 177.89
    },
    {
      "Timecode": "2025-01-10T05:00:00Z",
      "LogPrice": 177.89
    },
    {
      "Timecode": "2025-01-10T05:30:00Z",
      "LogPrice": 177.89
    },
    {
      "Timecode": "2025-01-10T06:00:00Z",
      "LogPrice": 177.89
    },
    {
      "Timecode": "2025-01-10T06:30:00Z",
      "LogPrice": 177.89
    },
    {
      "Timecode": "2025-01-10T07:00:00Z",
      "LogPrice": 177.89
    },
    {
      "Timecode": "2025-01-10T07:30:00Z",
      "LogPrice": 177.89
    },
    {
      "Timecode": "2025-01-10T08:00:00Z",
      "LogPrice": 177.89
    },
    {
      "Timecode": "2025-01-10T08:30:00Z",
      "LogPrice": 177.89
    },
    {
      "Timecode": "2025-01-10T09:00:00Z",
      "LogPrice": 177.89
    },
    {
      "Timecode": "2025-01-10T09:30:00Z",
      "LogPrice": 177.89
    },
    {
      "Timecode": "2025-01-10T10:00:00Z",
      "LogPrice": 177.89
    },
    {
      "Timecode": "2025-01-10T10:30:00Z",
      "LogPrice": 177.89
    },
    {
      "Timecode": "2025-01-10T11:00:00Z",
      "LogPrice": 177.89
    },
    {
      "Timecode": "2025-01-10T11:30:00Z",
      "LogPrice": 177.89
    },
    {
      "Timecode": "2025-01-10T12:00:00Z",
      "LogPrice": 177.89
    },
    {
      "Timecode": "2025-01-10T12:30:00Z",
      "LogPrice": 177.89
    },
    {
      "Timecode": "2025-01-10T13:00:00Z",
      "LogPrice": 177.89
    },
    {
      "Timecode": "2025-01-10T13:30:00Z",
      "LogPrice": 177.89
    },
    {
      "Timecode": "2025-01-10T14:00:00Z",
      "LogPrice": 177.89
    },
    {
      "Timecode": "2025-01-10T14:30:00Z",
      "LogPrice": 177.89
    },
    {
      "Timecode": "2025-01-10T15:00:00Z",
      "LogPrice": 177.89
    },
    {
      "Timecode": "2025-01-10T15:30:00Z",
      "LogPrice": 177.89
    },
    {
      "Timecode": "2025-01-10T16:00:00Z",
      "LogPrice": 177.89
    },
    {
      "Timecode": "2025-01-10T16:30:00Z",
      "LogPrice": 177.89
    },
    {
      "Timecode": "2025-01-10T17:00:00Z",
      "LogPrice": 177.89
    },
    {
      "Timecode": "2025-01-10T17:30:00Z",
      "LogPrice": 177.89
    },
    {
      "Timecode": "2025-01-10T18:00:00Z",
      "LogPrice": 177.89
    },
    {
      "Timecode": "2025-01-10T18:30:00Z",
      "LogPrice": 177.89
    },
    {
      "Timecode": "2025-01-10T19:00:00Z",
      "LogPrice": 177.89
    },
    {
      "Timecode": "2025-01-10T19:30:00Z",
      "LogPrice": 177.89
    },
    {
      "Timecode": "2025-01-10T20:00:00Z",
      "LogPrice": 177.89
    },
    {
      "Timecode": "2025-01-10T20:30:00Z",
      "LogPrice": 177.89
    },
    {
      "Timecode": "2025-01-10T21:00:00Z",
      "LogPrice": 177.89
    },
    {
      "Timecode": "2025-01-10T21:30:00Z",
      "LogPrice": 177.89
    },
    {
      "Timecode": "2025-01-10T22:00:00Z",
      "LogPrice": 177.89
    },
    {
      "Timecode": "2025-01-10T22:30:00Z",
      "LogPrice": 177.89
    },
    {
      "Timecode": "2025-01-10T23:00:00Z",
      "LogPrice": 177.89
    },
    {
      "Timecode": "2025-01-10T23:30:00Z",
      "LogPrice": 177.89
    },
    {
      "Timecode": "2025-01-11T00:00:00Z",
      "LogPrice": 177.89
    },
    {
      "Timecode": "2025-01-11T00:30:00Z",
      "LogPrice": 171.48
    },
    {
      "Timecode": "2025-01-11T01:00:00Z",
      "LogPrice": 171.48
    }
  ]
}
```

(I haven't truncated this for my own amusement)
