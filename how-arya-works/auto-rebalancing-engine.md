# Auto-Rebalancing Engine

### Smart Liquidity Movement, Without Manual Intervention

Arya's **Auto-Rebalancing Engine** is the logic layer responsible for continuously optimizing user positions by reallocating assets across integrated lending/borrowing protocols. It enables both **yield maximization** and **cost minimization**, with minimal friction or user input.

***

### Why Rebalancing Matters

DeFi markets are dynamic — rates fluctuate block by block, and optimal positions can change in minutes. Without rebalancing, funds may sit in **suboptimal protocols**, leading to:

* **Lower APY** for lenders
* **Higher APR** for borrowers
* **Reduced collateral efficiency**

Auto-rebalancing solves this by actively monitoring protocol metrics and **reacting to market changes** in real time or near-real time.

***

### Key Rebalancing Objectives

* **Maximize Return on Idle Deposits**
* **Minimize Borrowing Cost Over Time**
* **Reduce Risk Exposure (e.g., over-utilization)**
* **Ensure Protocol Diversification (if configured)**

***

### How It Works

The Auto-Rebalancing Engine operates as a **background service** triggered by either **on-chain activity** or **scheduled checks**.

#### Step-by-Step Flow

1. **Monitor Rates:**\
   The Rate Oracle continuously tracks lending APYs and borrowing APRs across all connected protocols.
2. **Compare Thresholds:**\
   A configurable threshold (e.g., 0.30% yield difference) determines when a rebalancing action is justified.
3. **Calculate Net Benefit:**\
   The engine estimates gas costs, slippage (if any), and timing to ensure rebalancing is profitable.
4. **Execute Reallocation:**\
   Funds are withdrawn from the underperforming adapter and re-deposited into a better-performing protocol.
5. **Emit Rebalance Event:**\
   The system logs the rebalancing activity for transparency and historical auditing.

***

### Rebalancing Triggers

| Trigger Type        | Description                                               |
| ------------------- | --------------------------------------------------------- |
| **Time-based**      | Rebalances every X hours (e.g., 6h, 12h)                  |
| **Rate-based**      | Triggers if a better APY/APR exceeds threshold            |
| **Manual override** | Admins or users with permissions can force it             |
| **Risk-based**      | Activated if protocol utilization crosses safe thresholds |

***

### Example: Lending Rebalance

> A user’s USDC is earning 3.5% in Compound. The Rate Oracle flags that Morpho now offers 4.3%.\
> Gas costs are low and the rate difference is above the configured threshold.
>
> The Auto-Rebalancing Engine withdraws the USDC from Compound and deposits it into Morpho — increasing the user’s returns with no action needed on their part.

***

### Rebalancing Policy Parameters

These can be configured per asset, per user segment, or globally:

* **Minimum Rate Difference:** e.g., 0.25%
* **Cooldown Period:** e.g., no rebalancing within 3 hours of last action
* **Max Gas Fee Cap:** rebalancing won’t execute if gas exceeds preset amount
* **Rate Volatility Filter:** smooths out temporary spikes

***

### Gas Efficiency Measures

To avoid unnecessary gas costs:

* Rebalancing is **batched** when possible
* **Gas-efficient adapters** reduce interaction overhead
* **Simulation layer** ensures profitable execution before action
* Users can opt in/out of auto-rebalancing for individual positions

***

### Smart Contract Integration

Rebalancing logic is built into the `StrategyManager` contract and can interact with:

* `Vault` for asset movement
* `ProtocolAdapter` contracts
* `RateOracle` for input rates
* `AutomationTrigger` (e.g., Gelato or Chainlink Keepers)

***

### Transparency & Auditing

All rebalancing actions:

* Emit on-chain events
* Include before/after rate snapshots
* Are visible on the user dashboard
* Can be exported via CSV or API
