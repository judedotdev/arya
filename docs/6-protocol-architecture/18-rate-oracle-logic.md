# Rate Oracle Logic

### Accurate, Reliable, Real-Time Rate Intelligence

At the heart of Arya’s optimization engine lies the **Rate Oracle** — a modular on-chain system responsible for collecting, standardizing, and delivering the latest interest rate data from multiple lending and borrowing protocols. This component is essential for making precise and timely allocation decisions.

***

### Why a Dedicated Rate Oracle?

DeFi interest rates are volatile and protocol-specific. Each platform (Aave, Compound, Morpho, etc.):

* Uses different methods for calculating APY/APR
* Updates rates on different block intervals
* May use either stable or variable rate models

A generic rate-fetching approach isn’t enough. Arya’s Rate Oracle normalizes these inconsistencies into a **standardized, comparable format** — ensuring the optimization engine always acts on clean, accurate data.

***

### Key Objectives

* **Unified Rate Format**\
  Normalize all protocol rates into comparable APY and APR metrics.
* **Real-Time Tracking**\
  Monitor rate changes per block or with minimal delay.
* **Risk Awareness**\
  Include volatility, utilization rate, and liquidity context with each rate.
* **Optimization-Ready**\
  Output is consumed directly by StrategyManager and BorrowingEngine contracts.

***

### Core Components

#### 1. **RateFetcher Module**

Each protocol has a custom rate fetcher that reads from:

* LendingPool contracts (e.g., `getReserveData()` in Aave)
* InterestRateModels (e.g., in Compound)
* Protocol subgraphs (for on-chain/off-chain hybrid feeds)

The fetched data includes:

* Supply APY
* Borrow APR
* Utilization Rate
* Emission/Incentives (if any)

***

#### 2. **RateNormalizer**

Once fetched, raw rate data is normalized into a consistent format:

```solidity
solidityCopyEditstruct NormalizedRateData {
    address protocol;
    address asset;
    uint256 supplyAPY;  // in basis points
    uint256 borrowAPR;  // in basis points
    uint256 utilization;
    uint256 timestamp;
}
```

This allows rates from different protocols to be compared and ranked.

***

#### 3. **Oracle Aggregator**

A central contract aggregates all NormalizedRateData entries across supported protocols.

Responsibilities:

* Store latest values per asset/protocol
* Provide `getBestRate(asset, mode)` interface
* Enable querying by any contract (StrategyManager, UI, alerts)
* Emit events on significant rate changes (for frontend display & automation)

***

### Smart Contract Interface Example

```solidity
solidityCopyEditinterface IRateOracle {
    function getSupplyAPY(address protocol, address asset) external view returns (uint256);
    function getBorrowAPR(address protocol, address asset) external view returns (uint256);
    function getBestLendingRate(address asset) external view returns (address protocol, uint256 apy);
    function getBestBorrowingRate(address asset) external view returns (address protocol, uint256 apr);
}
```

***

### Data Freshness & Update Triggers

* Rates are updated **on deposit/withdrawal events**
* Manual or scheduled updates (e.g., via Keepers or Gelato) can also be triggered
* Oracle tracks block timestamps for freshness validation
* Frontend displays “last updated” time for full transparency

***

### Risk & Stability Considerations

* **Fallbacks:** If a protocol becomes unresponsive, a cached rate is used for short-term stability
* **Rate Spikes:** High volatility is flagged for optional rate smoothing
* **Protocol Pauses:** If a protocol halts borrowing/lending, it’s automatically de-prioritized

***

### Sample Use Case: Best Lending Rate

```solidity
solidityCopyEdit(address bestProtocol, uint256 bestApy) = rateOracle.getBestLendingRate(USDC);

// StrategyManager then allocates funds to that protocol’s adapter.
```

***

### Summary

The Rate Oracle in Arya acts as a real-time intelligence engine that powers dynamic capital allocation and borrowing optimization
