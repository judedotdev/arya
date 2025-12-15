# For Active Debt Managers

## Who This Is For

Arya is built for **experienced DeFi users** who actively manage borrowed positions, run leverage or yield strategies, and care deeply about borrow efficiency, risk, and execution quality.

These are users who:

- Actively manage large debt positions
- Use borrowing strategically (not casually)
- Run leverage, yield farming, looping, or arbitrage strategies
- Want granular control — without operational friction

**Think:** DeFi traders, yield farmers, protocol arbitrageurs — not casual borrowers.

---

## The Core Value Proposition

You're skilled enough to manage complex debt strategies.  
You just shouldn't waste time on operational grunt work.

**Arya gives you professional-grade tools and automation by default — with the ability to take full manual control whenever you want.**

> Default: automated optimization  
> Optional: manual overrides and custom strategies  
> Always: full visibility and control

---

## What Sets Arya Apart for Active Debt Managers

### 1. Unified Protocol Access  

**One Dashboard for All Your DeFi Debt — Past, Present, and Future**

#### The Problem Today

Active debt managers often have positions scattered across multiple protocols:

- $50K borrowed on Aave
- $30K borrowed on Compound
- $20K borrowed on Morpho

Managing this requires:

- Multiple websites
- Multiple wallet connections
- Multiple interfaces
- Manual tracking and missed optimization opportunities

#### With Arya

Connect your wallet and Arya instantly displays **all your existing borrow positions**, even ones opened before you started using Arya.

```txt
Total Borrowed: $100K across 3 protocols
Average APR: 5.1%
Total Annual Interest: $5,100

Aave:     $50K @ 5.2% APR | Collateral: 15 ETH | Health: 1.45
Compound: $30K @ 4.8% APR | Collateral: 8 ETH  | Health: 1.52
Morpho:   $20K @ 4.5% APR | Collateral: 5 wBTC | Health: 1.68
```

#### Manage Everything From One Interface

No more switching dashboards. From Arya, you can:

- Add or withdraw collateral
- Increase or repay debt (partially or fully)
- Monitor health factors in real time
- Set alerts for liquidation risk

**Example:**  
Your Aave health factor drops to 1.3  

- Old way: open Aave → connect wallet → navigate UI → add collateral  
- With Arya: click position → "Add 2 ETH" → confirm

Done in seconds.

#### Migrate to Optimized Positions (When Ready)

Once you see all your positions in one place, Arya analyzes them and identifies optimization opportunities:

```txt
💡 Optimization Available

Current State:
- 3 positions across 3 protocols
- Average APR: 5.1%
- Annual interest: $5,100

Optimized State:
- Consolidated position on best protocol
- APR: 4.3%
- Annual interest: $4,300

Potential Savings: $800/year
```

**How migration works:**

When you click "Optimize Positions," Arya uses flash loans to migrate your debt atomically:

1. Flash borrow the debt amount
2. Repay all existing loans across protocols
3. Withdraw and consolidate your collateral
4. Open new optimized position on the best protocol
5. Repay the flash loan (small fee added to new debt)

**Example:**

- Current total debt: $100K across 3 protocols
- Flash loan fee: ~$90 (0.09%)
- New debt: $100,090 on optimal protocol
- Annual savings: $800
- Break-even: ~41 days

**You control the timing** — migrate immediately, later, or continue managing positions manually. Arya simply shows you the opportunity.

#### New Borrows: Automatically Optimized

Going forward, all new borrows through Arya are automatically routed to the best protocol:

**Example:**  
Request: "Borrow $10K USDC"  
→ Arya scans all protocols in real-time  
→ Evaluates APR, LTV, liquidation threshold, and gas  
→ Routes to optimal protocol automatically  

You always get the best available terms without research.

---

### 2. Real-Time Borrow Rate Comparisons  

**Make Informed Decisions With Live Data**

#### The Problem

To compare borrowing options today, you must:

- Check APRs across multiple protocols
- Manually calculate collateral requirements
- Estimate health factors
- Factor in gas costs
- Do the math yourself

This takes time — and mistakes are expensive.

#### With Arya

See all relevant data **side by side**, in real time:

| Protocol | APR  | Collateral Needed | Your Health Factor | Gas Cost |
|----------|------|-------------------|-------------------|----------|
| Morpho   | 4.5% | $13,000 ETH       | 1.52              | $8       |
| Compound | 4.8% | $13,500 ETH       | 1.48              | $15      |
| Aave     | 5.2% | $12,800 ETH       | 1.55              | $12      |

Decision time: **seconds, not minutes**.

---

### 3. Precision Execution  

**Advanced Tools for Sophisticated Strategies**

Arya is built for more than basic borrowing.

#### Partial Debt Refinancing

Move only part of your debt when it makes sense.

**Example:**

- $100K borrowed on Aave @ 6%
- Compound offers 4.5%
- Refinance $60K, keep $40K on Aave for strategic reasons

#### Multi-Collateral Position Management

Allocate collateral intentionally across protocols.

**Example:**

- Use wBTC on Compound (better wBTC terms)
- Use ETH on Aave (e-mode efficiency)
- Rebalance without unwinding positions

#### Looped Positions

Recursive leverage strategies such as:

- Deposit ETH → borrow USDC → buy ETH → repeat

Arya tracks health factors across all loop layers and helps you manage risk proactively.

#### Hedged Structures

Use borrowed capital as part of hedged strategies:

- Long ETH spot
- Short ETH perp
- Borrowed stablecoins fund the hedge

Arya optimizes the borrowed leg to maximize hedge profitability.

---

### 4. Automated Optimization (Default) — With Manual Control (Optional)

Arya operates in **two modes**. You choose how much control you want.

---

#### 🔹 Default: Automatic Optimization

By default, Arya operates in full automation mode:

**For new borrows:**

- Scans all supported protocols in real time
- Routes to the best available option automatically
- Evaluates APR, LTV, liquidation threshold, and gas

**For positions managed through Arya:**

- Continuously monitors rates across protocols
- Auto-migrates debt when better rates appear (using flash loans)
- Optimizes without manual intervention
- Only migrates when savings justify costs (flash loan fees + gas)

**For pre-existing positions (opened before using Arya):**

- Displays all positions in unified dashboard
- Identifies optimization opportunities
- Shows potential savings
- Migration requires your explicit approval

**Example of automatic optimization:**

```txt
You borrowed $50K USDC through Arya on Compound @ 5%

Rate change detected:
- Morpho now offers 4.2% (0.8% improvement)
- Annual savings: $400
- Migration cost: $45 flash loan fee + $30 gas = $75
- Break-even: 68 days

Arya's decision: ✅ Auto-migrate
Action: Debt moved to Morpho overnight
```

**You stay informed:** Arya notifies you of all optimizations and shows transaction details.

---

#### 🔹 Optional: Manual Mode & Custom Triggers

At any time, you can override automation.

**Manual controls include:**

- Explicit protocol selection
- Custom collateral allocation
- Trigger-based rebalancing
- Gas cost limits
- Risk constraints (health factor, volatility)

**Example Trigger:**

```txt
Only migrate my debt if:

* Rate improves by at least 1%
* Health factor remains above 1.5
* Gas cost < $50
* Market volatility < 30%
```

Automation executes **only** when your conditions are met.

---

### Control Without Complexity

**The DeFi Dilemma**

- Simple platforms → no control
- Full control → write your own contracts

**Arya bridges the gap.**

You express intent and constraints.  
Arya handles monitoring and execution.

| Feature                      | What It Means                      | Example                                      |
|------------------------------|-----------------------------------|----------------------------------------------|
| Manual Protocol Selection    | Choose exactly where to borrow    | "Use Aave e-mode for this position"         |
| Custom Collateral Allocation | Decide which assets back which loans | "Use wBTC here, ETH there"                |
| Trigger-Based Rebalancing    | Automate risk responses           | "If ETH drops 15%, reduce leverage by 25%"  |
| Gas Cost Awareness           | See costs before acting           | "$45 gas saves $600/year"                   |
| Performance Metrics          | Measure efficiency                | "Interest saved vs baseline"                |

---

## Ideal Use Cases

### Leveraged Trading

Borrow cost directly impacts returns.

**Example:**

- $200K borrowed
- 6% APR → $12K/year
- 4.5% APR → $9K/year  
**$3K saved annually**

Arya automatically routes and migrates debt to preserve margins.

---

### Yield Farming With Borrowed Capital

- Borrow $100K @ 5% → $5K cost
- Earn 12% → $12K revenue
- Net: $7K

Optimize borrow rate to 4%:

- Cost drops to $4K
- Net rises to $8K

---

### Protocol Arbitrage

- Borrow USDC @ 4%
- Lend USDC @ 6%
- Capture 2% spread

Arya monitors spreads and helps execute efficiently.

---

### Collateral Looping

Recursive leverage increases exposure — and risk.

Arya:

- Tracks health factors in real time
- Alerts before danger zones
- Supports one-click or automatic deleveraging

**Example:**

```txt
ETH drops 20%
Health factor falls below 1.25
→ Auto-unwind 2 loop layers
→ Health factor restored to 1.52
→ Liquidation avoided
```

---

## The Bottom Line

You're a power user.  
You don't need hand-holding — but you shouldn't fight infrastructure.

**Arya is your co-pilot:**

- Automates optimization by default
- Gives you full control when you want it
- Saves time, gas, and interest
- Keeps risk visible and manageable

**Think of Arya as:**  
**The Bloomberg Terminal for DeFi debt management.**

---
