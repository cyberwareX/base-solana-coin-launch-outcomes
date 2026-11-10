# Base and Solana new coin launches: first-day outcomes (free sample)

What happens to a new coin in its first day? This repo holds a free sample of our dataset of new Base and Solana
coins, each with its price change 1 hour, 6 hours, 24 hours and 7 days after our recorder first saw it, plus a rug flag.

- `sample.csv` / `sample.json`: 50 rows, the 25 newest coins per chain whose 24 hour reading is already in.
- `wallet-report-sample.json`: free sample of our smart-money wallet report (addresses masked).
  Bots, exchanges, scam and wash wallets are left out, and so are wallet farms: many wallets fed by one
  funder that buy the same coins (build 2026-11-10 11:01 UTC).

## Whole table (build 2026-11-10 09:41 UTC)

Window: coins first seen 2026-10-04 09:35 to 2026-11-10 08:50 UTC (37 days; the recorder started on 2026-10-04).
Counted from all 6,345 rows, not a sample.

| Chain  | Coins | With a 24 h reading | Up at 24 h    | Down 90% or more at 24 h |
|--------|------:|--------------------:|--------------:|-------------------------:|
| Base   | 2,054 | 1,976               | 83 (4.2%)     | 1,877 (95.0%)            |
| Solana | 4,291 | 4,091               | 444 (10.9%)   | 1,538 (37.6%)            |

Shares are of coins with a 24 h reading. Base here means coins our recorder picked up on Base;
it is not every token deployed on Base.

## Columns

| Column | Meaning |
|---|---|
| chain | base or solana |
| token | contract address (Base) or mint (Solana) |
| symbol | ticker as listed |
| first_seen_utc | when our recorder first saw the coin, UTC |
| liquidity_usd_first_seen | pool liquidity in USD at first sight |
| fdv_usd_first_seen | fully diluted value in USD at first sight |
| ret_1h, ret_6h, ret_24h | price change after 1, 6, 24 hours, as a fraction (-1 = zero, 0.5 = +50%); empty = not read |
| ret_7d | same at 7 days; empty for coins younger than 7 days |
| max_ret_seen | best of the 1h/6h/24h/7d readings (not the intraday high) |
| rugged_any | 1 = pool drained or price near zero at any reading, 0 = not, empty = never read |

Returns are measured from the price at first sight, not from the first block.

## Get the whole table

- Full CSV, every coin we have (up to 60 days back; today that is 37 days, about 6,300 rows): 15 USDC.
  - Pay from any wallet holding USDC on Base: https://chain.cyberwarex.com/buy
  - Or with an x402 client: `GET https://chain.cyberwarex.com/launch-dataset?days=60` (default is 30 days)
- One coin's row: 0.01 USDC, `GET https://chain.cyberwarex.com/launch-outcome?token=<address or mint>`
- Free samples, always fresh: https://chain.cyberwarex.com/launch-dataset/sample and
  https://chain.cyberwarex.com/wallet-report/sample
- Details and FAQ: https://cyberwarex.com/answers/token-launch-outcomes-dataset-base-solana
  and https://cyberwarex.com/answers/smart-money-wallet-report-base-solana

The files here are a snapshot from the date above. The live sample endpoints are refreshed every hour.

## License

Sample files: CC BY 4.0. Credit "CyberWareX launch outcomes dataset" with a link to this repo.

Not financial advice. Data is what our recorder read; a missing reading is left empty, never filled in.
