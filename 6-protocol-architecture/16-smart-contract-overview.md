# Smart Contract Overview

### Modular, Secure, and Extensible by Design

Arya is built on a modular smart contract architecture that enables flexible interaction with multiple lending/borrowing protocols while maintaining strong security guarantees and upgradeability.

This section provides an overview of the core contracts, how they interact, and the roles they play within the Arya system.

***

### Architecture Highlights

* **Protocol-Agnostic:** Arya uses adapters to integrate with various money markets.
* **Dynamic Routing Engine:** Contracts route funds based on optimization logic.
* **Role Separation:** Clear distinction between user-facing vaults and backend managers.
* **Upgradeable:** Proxy patterns are used where needed to allow for future enhancements.

***

### Core Contract Modules

#### 1. **Vault Contract**

**Purpose:**\
Manages user deposits, withdrawals, and token balances.

**Key Functions:**

* Accepts deposits of supported assets
* Issues vault shares to users
* Interfaces with the StrategyManager for routing

**Security:**\
Non-custodial design; only interacts with verified protocol adapters.

***

#### 2. **StrategyManager**

**Purpose:**\
Routes funds to the optimal underlying protocol based on real-time yield/borrow analysis.

**Responsibilities:**

* Evaluate APYs/APRs
* Allocate or migrate funds
* Execute rebalancing logic periodically or on trigger

**Features:**

* Can split funds across multiple strategies
* Includes rebalancing thresholds to avoid gas inefficiencies

***

#### 3. **Protocol Adapters**

**Purpose:**\
Abstract the interface of external lending/borrowing protocols (e.g., Aave, Compound, Morpho).

**Design Pattern:**\
Each adapter conforms to a standardized interface:

```solidity
solidityCopyEditinterface IProtocolAdapter {
    function deposit(uint256 amount) external;
    function withdraw(uint256 amount) external;
    function getCurrentAPY() external view returns (uint256);
}
```

**Advantage:**\
New protocols can be added by deploying a new adapter without changing core contracts.

***

#### 4. **DebtManager**

**Purpose:**\
Handles user borrowing positions and manages health factor calculations.

**Functions:**

* Tracks collateral and borrowed amounts
* Executes auto-repay or refinance logic
* Integrates with pricing oracles to monitor liquidation risk

***

#### 5. **Oracle Integration**

**Purpose:**\
Fetch accurate and secure price feeds for supported assets.

**Common Integrations:**

* Chainlink
* Redundant fallback sources for reliability

**Use Cases:**

* LTV enforcement
* Health factor calculations
* Liquidation thresholds

***

#### 6. **Automation Contracts (Optional)**

**Purpose:**\
Enable auto-migration, rebalancing, and user-defined triggers.

**Triggered By:**

* Time intervals
* Yield differential thresholds
* Borrow cost spikes
* Health factor warnings

***

### Security & Upgradeability

* **Audit-Ready:** Designed with formal verification and auditability in mind.
* **Upgradeable Where Needed:** Vault logic is upgradable via proxy, but adapters follow a plug-and-play model to minimize attack surface.
* **Access Control:** Uses `Ownable` and `RoleBasedAccessControl` patterns to restrict sensitive functions.

***

### Diagram Overview (for GitBook visual embedding)

```
scssCopyEditUser
  ↓
Vault (Deposits / Shares)
  ↓
StrategyManager
  ↓           ↓           ↓
Adapter-A   Adapter-B   Adapter-C
 (Aave)     (Compound)  (Morpho)
```
