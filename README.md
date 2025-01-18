# Delta Hedging Bot

A Python-based bot that dynamically manages delta exposure in Uniswap liquidity pools by leveraging Binance perpetual futures. The primary goal is to mitigate impermanent loss while maximizing trading fee returns.

---

## **Objective**
To reduce the risk of impermanent loss in a Uniswap liquidity pool by dynamically hedging delta exposure using Binance futures.

---

## **Core Components**

1. **Initialization**
   - Import required libraries (`ccxt`, `web3`, `pandas`, etc.).
   - Configure API keys and endpoints for Binance and Uniswap.
   - Define constants such as rebalancing thresholds and funding rate update intervals.

2. **Price Fetching**
   - Fetch the ETH/USDC price from Uniswap using `web3`.
   - Retrieve ETH/USDT perpetual futures prices from Binance using `ccxt`.

3. **Delta Calculation**
   - Calculate delta exposure based on the ETH and USDC holdings in the liquidity pool.

4. **Hedging Logic**
   - Execute trades on Binance futures when delta exceeds a defined threshold.

5. **Backtesting**
   - Simulate strategy performance using historical data and assess the results.

6. **Result Visualization**
   - Plot key metrics, including ETH prices, delta exposure, and cumulative hedge positions.

---

## **Core Concept: Impermanent Loss**

Impermanent loss occurs when the price ratio of assets in an AMM diverges from the time of deposit. This bot uses delta hedging to reduce its impact by maintaining neutral exposure to price changes while still earning pool fees.

---

## **Workflow**
1. Configure API keys, endpoints, and thresholds.
2. Fetch ETH prices from Uniswap and Binance.
3. Compute delta exposure and evaluate if rebalancing is necessary.
4. Hedge using Binance futures to neutralize delta exposure.
5. Repeat and log results for visualization and analysis.

---

## **Flowchart**

```text
Start
  |
  v
[Initialization]
  |
  v
[Fetch Uniswap Price] ---> [Fetch Binance Price]
  |
  v
[Compute Delta]
  |
  v
[Is |Delta| > Threshold?] -- No --> [Log Results & Wait for Next Interval]
  | Yes
  |
  v
[Determine Trade Direction]
  |
  v
[Execute Hedge on Binance]
  |
  v
[Update Cumulative Position]
  |
  v
[Log Results]
  |
  v
[Next Interval or End Backtest]
```

---

## **Code**

The bot's implementation includes detailed Python code that:
- Integrates Binance API via `ccxt`.
- Fetches Uniswap data using `web3`.
- Computes delta and executes hedging trades.
- Visualizes performance metrics.

Access the complete code on `bot.ipynb` file on this repository.

---

## **Installation**
1. Clone the repository:
   ```bash
   git clone https://github.com/your-username/delta-hedging-bot.git
   cd delta-hedging-bot
   ```
2. Install dependencies:
   ```bash
   pip install -r requirements.txt
   ```
3. Set up your API keys in a `.env` file:
   ```
   BINANCE_API_KEY=your_binance_api_key
   BINANCE_SECRET_KEY=your_binance_secret_key
   UNISWAP_ENDPOINT=https://mainnet.infura.io/v3/your_project_id
   ```

---

## **Backtesting and Visualization**
Use the provided scripts to simulate the strategy using historical data. The backtest results include:
- ETH prices over time.
- Delta exposure.
- Cumulative hedge positions.

Visualization is done via `matplotlib` with a multi-plot layout.

---

## **Acknowledgments**
- [ccxt](https://github.com/ccxt/ccxt)
- [Web3.py](https://github.com/ethereum/web3.py)
- Uniswap and Binance APIs
