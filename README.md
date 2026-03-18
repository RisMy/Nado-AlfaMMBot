# Nado-AlfaMMBot

Automated market making system for Nado Protocol (Ink L2).

## Overview

Multi-pair liquidity provision bot designed for Nado's CLOB perpetual markets. Provides two-sided quotes across multiple pairs simultaneously, improving orderbook depth and trading efficiency.

## Features

- **Multi-pair quoting** — simultaneous liquidity across 10+ perpetual pairs
- **Quadratic inventory skew** — Avellaneda-Stoikov based position management
- **Market regime detection** — adapts strategy for trending/sideways markets
- **Volatility-adjusted spread** — EWMA-based dynamic spread calculation
- **Index price integration** — Binance/Bybit reference pricing
- **Funding rate signal** — bias based on funding rate differentials
- **Automated pair rotation** — scans and selects most profitable pairs
- **Risk management** — 5 risk modes from normal to kill switch

## Architecture

**Market Data Layer** → Nado WebSocket + Binance/Bybit index pricing

**Pair Scanner** → scans all pairs, selects top by net spread every 30 min

**Quote Engine** → calculates fair price + inventory skew + regime bias + funding signal

**Risk Manager** → 5 risk modes (Normal → Caution → One-Sided → Reduce Only → Kill Switch)

**Execution** → post-only limit orders via Nado Python SDK

## Stack

- Python 3.11+ / asyncio
- Nado Protocol Python SDK
- VPS deployment (Amsterdam, low-latency)

## Status

Live on mainnet. Actively developing and optimizing.

## Contact

For inquiries: graand.store@gmail.com
