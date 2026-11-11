---
name: binance-us-trading
description: Query Binance.US market data and, with the user's explicit approval, manage orders, wallets, staking and OTC trades through the binance-us MCP server. Use for Binance.US prices, order books, account balances or order management.
---

# Binance.US MCP

The plugin starts `npx -y @nirholas/binance-us-mcp-server` (bin `binance-us-mcp`, stdio). It talks to `https://api.binance.us`.

## Credentials

Public market tools need no key. Signed tools read two environment variables, inherited from the shell that started Claude Code:

- `BINANCE_US_API_KEY`
- `BINANCE_US_API_SECRET`

The user must export both in their own shell before launching Claude Code. Never ask the user to paste a secret into chat and never write it to a file. If a signed call fails with "API credentials required", tell the user to export the variables and restart. Prefer an API key without withdrawal permission.

## Tools (all prefixed `binance_us_`)

- System: `ping`, `server_time`, `system_status`, `exchange_info`.
- Market data: `order_book`, `recent_trades`, `historical_trades`, `agg_trades`, `klines`, `avg_price`, `ticker_price`, `ticker_book`, `rolling_window`.
- Account: `account_info`, `my_trades`, `rate_limits`, `trade_fee`, `trade_volume`.
- Spot trading: `test_order`, `new_order`, `get_order`, `cancel_order`, `cancel_replace`, `open_orders`, `all_orders`, `cancel_all_open_orders`, plus OCO: `new_oco`, `get_oco`, `cancel_oco`, `open_oco`, `all_oco_orders`.
- Wallet: `asset_config`, `deposit_address`, `deposit_history`, `withdraw_history`, `withdraw_crypto`, `withdraw_fiat`.
- Staking: `staking_asset_info`, `staking_balance`, `staking_history`, `staking_rewards`, `staking_stake`, `staking_unstake`.
- OTC: `otc_coin_pairs`, `otc_quote`, `otc_place_order`, `otc_get_order`, `otc_all_orders`, `ocbs_orders`.
- Sub-account, user data stream, custodial solution and credit line tools also exist; the last two need special API key types.

## Safe workflow

1. Read first: `binance_us_ticker_price` with a symbol such as `BTCUSD`, then `binance_us_order_book` or `binance_us_klines`.
2. Before any order, call `binance_us_test_order` with the same parameters. It posts to `/api/v3/order/test` and validates without trading.
3. Money-moving calls (`new_order`, `cancel_all_open_orders`, `withdraw_crypto`, `withdraw_fiat`, `staking_stake`, `staking_unstake`, `otc_place_order`) are real. Show the user the symbol, side, quantity, price and account effect, and wait for an explicit yes every time.
4. Report exchange error text back verbatim and do not retry a failed order blindly.

Binance.US has no futures, margin or lending, so those requests have no tool.
