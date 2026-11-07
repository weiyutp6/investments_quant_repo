# Multi-Asset Market Data Toolkit (Python)

A small, modular Python toolkit that pulls historical market data across five asset classes through one interactive entry point. It is the data layer for my derivatives and systematic-trading research.

| Asset class | Script | Data source |
|---|---|---|
| Equities (daily bars) | `fetch_stock_data.py` | Alpaca Market Data API |
| Options (contract reference data) | `fetch_options_data.py` | Polygon.io |
| Futures | `fetch_futures_data.py` | Quandl |
| Bonds | `fetch_bond_data.py` | Quandl |
| FX (about 37 pairs, including TWD crosses) | `fetch_currency_data.py` | OANDA-style REST API |

Instrument universes are kept in YAML (`stock_symbols.yaml`, `futures_codes.yaml`, `bond_codes.yaml`, `currency_pairs.yaml`), so adding a symbol needs no code change.

## What is implemented today

- A uniform `get_<asset>_data(symbol, start, end)` interface that returns a pandas `DataFrame`.
- `main.py`: a menu-driven runner (stock, bond, futures, options, currency) with date validation.
- Symbol universes defined in YAML.

## Research roadmap (not yet in this repo)

These are the research directions the data layer is built for. They are listed as plans, not as finished work:

- Black-Scholes pricing, Greeks and implied-volatility utilities
- Implied-volatility percentile screens for systematic options strategies (for example a paper-traded wheel strategy)
- Rules-based portfolios built from implied-volatility bands
- Backtesting with transaction-cost assumptions

## Setup

```bash
git clone https://github.com/weiyutp6/investments_quant_repo.git
cd investments_quant_repo
pip install requests pandas pyyaml alpaca-trade-api
```

### API credentials

Use your own keys from each provider. Do not commit them. Set them as environment variables or read them from an untracked config file.

| Provider | Variable |
|---|---|
| Alpaca (paper trading endpoint) | `APCA_API_KEY_ID`, `APCA_API_SECRET_KEY` |
| Polygon.io | `POLYGON_API_KEY` |
| Quandl | `QUANDL_API_KEY` |
| FX provider | key in an untracked config file |

## Known limitations

- Work in progress. Script paths and credentials are being moved to configuration.
- No tests yet.
- Data is for research. Nothing here is investment advice.

## Skills demonstrated

REST API integration, pandas data handling, multi-asset data modelling (equity, options, futures, rates, FX), config-driven design.
