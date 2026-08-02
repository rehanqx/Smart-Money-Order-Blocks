# 📦 Smart Money Concepts V3.2 — Order Block Engine

![Pine Script Version](https://img.shields.io/badge/Pine_Script-v6-blue?style=for-the-badge&logo=tradingview)
![TradingView](https://img.shields.io/badge/TradingView-Indicator-00897B?style=for-the-badge&logo=tradingview)
![License](https://img.shields.io/badge/License-MIT-green?style=for-the-badge)

An institutional-grade **Smart Money Concepts (SMC) Order Block & Breaker Block Engine** written in **Pine Script v6** for TradingView.

V3.2 utilizes custom **User-Defined Types (UDTs)**, dynamic box rendering, ATR displacement expansion models, and state-machine lifecycle tracking to identify, validate, and track high-probability institutional supply and demand zones in real time.

---

## 🔥 Key Features

* **⚡ Impulse Displacement Filtering:** Validates order blocks only when accompanied by true impulse candle body expansions relative to ATR volatility and Volume Moving Averages.
* **🔄 Full Order Block Lifecycle Tracking:**
  `CREATED ➔ CONFIRMED ➔ ACTIVE ➔ MITIGATED ➔ BREAKER ➔ RETESTED ➔ ARCHIVED`
* **🧱 Breaker Block Flip Detection:** Automatically tracks broken bullish/bearish order blocks that transform into institutional Breaker Blocks (`col_breaker`).
* **📦 Dynamic UDT Memory Heap:** Tracks top/bottom zone coordinates, strength scores (0–100), retest counts, and bar ages using Pine Script v6 UDT objects (`OrderBlock`).
* **📊 Realtime OB Dashboard:** On-screen HUD displaying nearest active OB levels, mitigation states, confluence scores, breaker statuses, and displacement quality.
* **🔌 Inter-Module Output API:** Standardized variable exports (`export_NearestOrderBlock`, `export_OrderBlockStrength`, `export_ConfluenceScore`, `export_BreakerStatus`) designed to integrate seamlessly with Fair Value Gaps (V3.3) and BOS/CHoCH (V3.4) engines.

---

## 📊 Dashboard Overview

The built-in master status HUD displays key structural order block parameters:

| Metric | Description |
| :--- | :--- |
| **Nearest Active Order Block** | Type (*Bullish OB, Bearish OB*) and direction of closest active memory block |
| **OB Level (Top / Bottom)** | Precision upper and lower boundary bounds for risk-defined entry and stop placing |
| **Lifecycle State** | Live lifecycle status (*ACTIVE, MITIGATED, BREAKER, ARCHIVED*) |
| **Block Strength & Quality** | Multi-factor rating (0–100) incorporating volume, trend regime, and displacement |
| **Confluence Score** | Consolidated score combining block quality and ADX trend strength |
| **Mitigation & Breaker Status**| Real-time alerts for retested, mitigated, or flipped breaker blocks |
| **Active Memory Allocation** | Memory usage counter relative to `max_active_blocks` limits |

---

## 🛠️ Configuration & Settings

### 1. Order Block Engine Settings
* `Pivot High/Low Length` *(Default: 10)*: Structural swing lookback window.
* `Displacement Multiplier` *(Default: 1.5x)*: Candle body expansion multiplier relative to ATR.
* `Minimum Order Block Strength` *(Default: 70)*: Minimum score threshold (0–100) required to draw an active OB box.
* `Maximum Active Blocks` *(Default: 15)*: Maximum number of active zones retained in the memory heap.
* `Order Block Expiration` *(Default: 150 bars)*: Expiration limit before mitigated zones are archived.

### 2. Visual & Color Standards
* Individual toggles for Bullish OB, Bearish OB, Breaker Blocks, OB Labels, and Dashboard HUD.
* Dynamic color mapping for active, mitigated, breaker, and invalidated zones.

---

## 💻 Installation & Usage

1. Open **[TradingView](https://www.tradingview.com)**.
2. Open the **Pine Editor** tab at the bottom of your workspace.
3. Create a new script, clear the default code, and paste the code from `SMC_Order_Block_Engine_v3_2.pine`.
4. Click **Save** and then select **Add to Chart**.

---

## ⚡ Real-Time Alerts Included

Includes native TradingView alert conditions for automated workflows:
* ⚡ **New Bullish Order Block Created**
* ⚡ **New Bearish Order Block Created**
* 🔥 **Order Block Mitigated**
* ⚠️ **Breaker Block Detected**
  
---

## 📜 License

This project is open-source and released under the [MIT License](LICENSE).
