# Dynamic Routing & Auto-Rebalancing

> Capital that moves where it performs best — automatically.

***

### What is Dynamic Routing?

Dynamic Routing in DeFi means directing funds to the best protocol **in real-time**, based on continuously changing factors like:

* Interest rates (APY/APR)
* Protocol liquidity
* Gas costs
* Risk metrics
* Asset demand/supply

In traditional aggregators, routing happens **once** — when you first deposit.\
In **Arya**, routing is **ongoing**.

***

### **Example:**

Let’s say you deposit DAI.

1. At the time of deposit, Aave offers the highest APY → Arya routes your DAI to Aave.
2. A few days later, Morpho overtakes Aave with better rates.
3. Arya **automatically migrates your position** to Morpho — no action needed.

✅ **Always earning the best yield — without switching manually.**

***

### What is Auto-Rebalancing?

Auto-rebalancing is the **automated movement of your assets** between protocols to maintain optimal performance.

Unlike static positions, Arya constantly asks:

* Is there a better rate now?
* Has risk in the current protocol increased?
* Would another pool offer better efficiency?
* Is the gas cost worth the move?

If the answer is **yes**, it initiates a rebalance.

***

### How It Works Under the Hood

1. **Rate Engine**\
   Continuously fetches live APY/APR data from integrated protocols.
2. **Risk Scanner**\
   Monitors health scores, liquidity, slippage, and protocol status.
3. **Strategy Evaluator**\
   Checks user preferences (e.g., "minimum rebalance delta", "max gas limit").
4. **Rebalancer**\
   Moves the position when it meets the threshold for gain or efficiency.

⏱️ All of this happens within seconds — per block.

***

### Non-Custodial, Permissionless

You remain in full control.\
Arya uses **non-custodial smart contracts** — you can withdraw anytime, and rebalancing does **not** require Arya to ever own your funds.

***

### Intelligent Routing Engine in Action

| Event                             | Arya Reaction                         |
| --------------------------------- | --------------------------------------- |
| Protocol B offers 0.5% better APY | Rebalance to Protocol B                 |
| Protocol A’s liquidity drops      | Exit and route to safer pool            |
| Gas fee spikes                    | Delay move until cost-benefit justifies |
| Stablecoin demand rises           | Prioritize lending in high-demand pool  |

***

#### Visual Workflow (Text Version)

```
[ User Deposit ]
        ↓
[ Aggregator Layer → Best APY ]
        ↓
[ Optimizer Layer → Strategy Engine ]
        ↓
[ Dynamic Routing → Protocol A ]
        ↓
( Monitors continuously )
        ↓
[ Protocol B offers better rate? ]
        → Yes → Auto-rebalance
        → No  → Stay
```
