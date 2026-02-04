# Sniper HUD - Project Walkthrough
**Repository**: [CS-O-SC/Sniper-HUD](https://github.com/CS-O-SC/Sniper-HUD)

## Overview
The **Sniper HUD** is a specialized Pine Script v6 strategy interface designed for **15-minute Bitcoin Binary Wagers** and short-term scalping. Unlike traditional indicators that issue binary "Buy/Sell" alerts, Sniper HUD calculates a real-time **Conviction Score (0-100%)** based on Bayesian probability, market regime, and session context.

It answers one question: *"Is this mean-reversion trade valid RIGHT NOW?"*

## Visuals
![Sniper HUD Chart View](assets/preview_1.png)
*Main Chart with Strike Line and Indicator Pane*

![Sniper HUD Close Up](assets/preview_2.png)
*Close-up of Signals and Strike Line*

## Key Features

### 1. The Conviction HUD (Top-Right Panel)
A live dashboard providing instant situational awareness:
-   **Conviction**: The weighted probability score (0-100%).
-   **Regime**: Current Market Trend (BULLISH / BEARISH).
-   **Session**: Active Volume Weight (e.g., AMERICA, ASIA).
-   **Gap X**: Exact distance from the Strike Price.
-   **Time Left**: Countdown for the current 15m candle.
-   **Wager**: Identifies if the current window is in/out of the money.

### 2. Trend Regime Filter ("The Wind")
Prevents "fighting the escalator."
-   **Logic**: Monitoring the **5-minute EMA (50)** slope.
-   **Bullish Regime**: Blocks SELL signals. Allow only "Dip Buys" (RSI < 35).
-   **Bearish Regime**: Blocks BUY signals. Allow only "Rally Sells" (RSI > 65).
-   *Effect*: Filters out the most common cause of binary losses—betting against a strong breakout.

### 3. Session-Aware Volume
Recognizes that not all volume is equal.
-   **AMERICA (13-21 UTC)**: **1.4x** Weight (High Confidence).
-   **EUROPE (07-13 UTC)**: **1.2x** Weight (Standard).
-   **ASIA (23-07 UTC)**: **0.7x** Weight (Noise Filter).
-   **WEEKEND**: **0.35x** Weight (Heavy Penalty for low liquidity).

### 4. Smart Time Decay ("The Cliff")
Signals are penalized based on how much time is left in the wager window.
-   **0-9 mins**: Safe Zone (100-80% Strength).
-   **10-11 mins**: Caution Zone (80-60% Strength).
-   **12-13 mins**: **The Cliff** (Drops to 25% Strength).
-   **14 mins**: The Floor (10% Strength - Ignore).

### 5. The "Strike Line"
-   **Logic**: Anchors the Open Price at 00, 15, 30, and 45.
-   **Visual**: Plots a **Stepline** that turns **Green** (Winning) or **Red** (Losing) in real-time.

## Technical Stack
-   **Language**: Pine Script v6
-   **Core Oscillators**: RSI (14), WaveTrend (10, 21)
-   **Logic Engine**: Weighted Sum Model with Veto Guards (Regime/Time).

## Installation
1.  Open TradingView -> Pine Editor.
2.  Copy and paste the `Sniper-HUD.pine` code.
3.  Click "Save" and "Add to Chart".

## License
© 2026 ChiamakaS. This project is for educational and personal use only. Trading involves significant risk; always validate signals against your own risk management protocols.

## Repo Meta-Tags
`pinescript-v6`, `binary-options`, `bayesian-inference`, `regime-filter`, `market-sessions`, `wavetrend`, `tradingview-indicator`, `scalping-strategy`, `rsi-divergence`, `market-microstructure`, `tradingview`
