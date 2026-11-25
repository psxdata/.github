# psxdata: Free Pakistan Stock Exchange (PSX) Data API & Python Library

**psxdata** is a free, open-source way to get **Pakistan Stock Exchange (PSX) data**: historical stock prices (OHLCV), live quotes, **KSE-100** index constituents, sector performance, the PSX stock screener, company fundamentals, and debt market data. Use it as a **Python library**, a **REST API**, an **MCP server for AI assistants**, or a **dbt analytics warehouse**.

📖 [Read the psxdata documentation](https://docs.psxdata.org) · 🐍 [psxdata on PyPI](https://pypi.org/project/psxdata/) · 🌐 [Live PSX REST API](https://psxdata-api.fastapicloud.dev)

## Which psxdata project do you need?

| You want to… | Project | Get started |
| --- | --- | --- |
| Download PSX historical stock data in Python or pandas | [psxdata: Python library for PSX data](https://github.com/psxdata/psxdata) | `pip install psxdata` |
| Get PSX stock prices over HTTP from any language | [psxdata-api: PSX REST API](https://github.com/psxdata/psxdata-api) | [psxdata-api.fastapicloud.dev](https://psxdata-api.fastapicloud.dev) |
| Ask Claude, Cursor or VS Code about Pakistani stocks | [psxdata-mcp: PSX MCP server](https://github.com/psxdata/psxdata-mcp) | `claude plugin install psxdata@psxdata-mcp` |
| Use PSX data in Claude without Docker, with warehouse marts | Hosted psxdata connector (invite-only) | [Join the waitlist](https://join.psxdata.org) |
| Run SQL analytics on modelled, tested PSX data | [psx-warehouse: PSX dbt data warehouse](https://github.com/psxdata/psx-warehouse) | dbt + BigQuery or MotherDuck |

## Download PSX historical stock prices in Python

```python
import psxdata

# Daily OHLCV history for a PSX-listed company
df = psxdata.stocks("ENGRO", start="2024-01-01", end="2024-12-31")
df.to_csv("engro_history.csv")   # export PSX data to CSV / Excel

kse100 = psxdata.indices("KSE100")  # KSE-100 index constituents
quote = psxdata.quote("LUCK")       # live PSX stock quote
screener = psxdata.screener()       # P/E, dividend yield, market cap
```

## Get PSX stock data from the REST API

```bash
curl "https://psxdata-api.fastapicloud.dev/stocks/ENGRO/historical?start=2024-01-01&end=2024-12-31"
curl "https://psxdata-api.fastapicloud.dev/indices/KSE100"
curl "https://psxdata-api.fastapicloud.dev/stocks/OGDC/quote"
```

The JSON API needs no API key and works from JavaScript, R, Excel Power Query, Google Sheets or any HTTP client.

## What PSX data is available?

- **Historical stock prices**: daily open, high, low, close and volume for 1,000+ PSX tickers
- **Live quotes**: current price and volume for any PSX-listed stock
- **Stock indices**: constituents of all 18 PSX indices, including KSE-100, KSE-30, KMI-30 and KMI All Shares
- **Sectors**: summaries for all 37 PSX sectors, such as banking, cement, fertilizer, and oil & gas
- **Stock screener**: P/E ratio, dividend yield and market capitalization for about 729 symbols
- **Fundamentals**: financial reports filed by listed companies
- **Debt market**: TFCs, Sukuks and other listed debt instruments
- **Margin trading**: margin-eligible scrips

## How the psxdata projects fit together

```
          Pakistan Stock Exchange (dps.psx.com.pk)
                          │
        psxdata Python library: scraping, validation, caching
           ┌──────────────┼─────────────────┐
     psxdata-api     psxdata-mcp       psx-warehouse
     (REST API)    (AI assistants)    (dbt + BigQuery)
```

## FAQ

### Is there a free API for Pakistan Stock Exchange data?

Yes. [psxdata-api](https://github.com/psxdata/psxdata-api) is a free, public REST API for PSX data at `psxdata-api.fastapicloud.dev`. It's rate-limited to 60 requests per minute per IP. For heavier use you can self-host it with Docker.

### How do I download KSE-100 historical data?

Run `pip install psxdata`, then call `psxdata.indices("KSE100")` for the constituents and `psxdata.stocks(symbol, start, end)` for each stock's daily price history. Save the results with `df.to_csv()`.

### Can I get PSX data in Python with pandas?

Yes. Every [psxdata](https://github.com/psxdata/psxdata) function returns a pandas DataFrame.

### Are PSX prices adjusted for dividends and splits?

No. Prices are raw PKR closing prices as published by PSX. They are not adjusted for splits, bonus shares or dividends.

### Can AI assistants like Claude or ChatGPT analyse Pakistani stocks?

Yes, any assistant that supports the Model Context Protocol (MCP) can. [psxdata-mcp](https://github.com/psxdata/psxdata-mcp) loads PSX data into a local DuckDB database so the assistant can answer questions with SQL. A hosted version, with no Docker and with the warehouse marts, is invite-only: join the waitlist at [join.psxdata.org](https://join.psxdata.org).

## Contributing

All psxdata projects are MIT-licensed open source. Issues, feature requests and pull requests are welcome in each repository. ⭐ Star the repos if they're useful to you.

---

<sub>psxdata is an independent open-source project. It is not affiliated with or endorsed by the Pakistan Stock Exchange Limited. Data is provided as-is and is not investment advice.</sub>
