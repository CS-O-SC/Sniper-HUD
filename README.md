# Sniper HUD - Project Walkthrough
**Repository**: [CS-O-SC/Sniper-HUD](https://github.com/CS-O-SC/Sniper-HUD)

## Overview
The **Sniper HUD** is a specialized Pine Script v6 indicator designed for **15-minute Bitcoin Wagers**. It combines momentum, volume, and time-based logic to provide a clear "YES/NO" signal for binary outcomes. It is engineered by aligning RSI, WaveTrend, and Adaptive Volume.

## Key Features

### 1. The "Strike Line" (Wager Context)
- **Logic**: Automatically detects the start of a new 15-minute window (00, 15, 30, 45).
- **Visual**: Plots a **Stepline** at the Open Price of the 15m window.
- **Dynamic Coloring**:
    - **Yellow**: Historical windows (closed).
    - **Green**: Current Live Price > Strike (Winning "YES").
    - **Red**: Current Live Price <= Strike (Winning "NO").
- **Overlay**: Forces this line onto the main chart for instant context.

### 2. Sniper Signals (Momentum + Volume)
Combines three indicators to filter high-probability setups:
- **RSI (14)**: Identifies Overbought (>65) and Oversold (<35) zones.
- **WaveTrend**: Normalized to fit the RSI scale. Provides crossover signals.
- **Adaptive Volume (RVOL)**: Ensures volume is significantly higher than average (Threshold: 1.25x).

### 3. Clean "HUD" Pane
- **Visuals**:
    - RSI (Blue)
    - WaveTrend Fast (Green Transparent)
    - WaveTrend Slow (Red Transparent)
    - Kill Zones (Shaded 35-65 Band)
- **Signals**: "Sniper YES" (Green Label) and "Sniper NO" (Red Label) appear when all conditions align.
- **Dual-Layer HUD**:
    - *Main Chart*: Step-line overlays for window tracking and historical strike zones.
    - *Indicator Pane*: Clean, transparency-weighted visual of RSI (Solid) vs. WaveTrend (Faded) for rapid decision-making.

## Technical Stack
- **Language**: Pine Script v6
- **Primary Oscillators**: RSI (14), WaveTrend (10, 21)
- **Volume Logic**: SMA-based Adaptive RVOL
- **Alerts**: JSON-ready placeholders for automated "YES" and "NO" setups.

## Installation
1.  Open TradingView -> Pine Editor.
2.  Copy and paste the `Sniper-HUD.pine`.
3.  Click "Save" and "Add to Chart".

## License
© 2026 ChiamakaS. This project is for educational and personal use only. Trading involves significant risk; always validate signals against your own risk management protocols.

## Repo Meta-Tags (For Discoverability)
`pinescript-v6`, `tradingview-indicator`, `scalping-strategy`, `rsi-divergence`, `wavetrend`, `market-microstructure`
