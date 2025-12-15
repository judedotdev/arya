# Protocol Adapters

Arya integrates with multiple DeFi lending and borrowing protocols via a standardized **Protocol Adapter** system. These adapters abstract away the complexity of different protocol interfaces and enable seamless routing, deposits, and withdrawals — all through a unified backend.

***

### What Is a Protocol Adapter?

A **Protocol Adapter** is a modular smart contract component that connects Arya to an external lending/borrowing protocol. It translates the generic actions (e.g., deposit, withdraw, get APY) into the protocol-specific implementation under the hood.

Each adapter conforms to a shared interface and can be added, removed, or upgraded **without modifying core logic.**

***

### Key Functions of an Adapter

| Function            | Description                                                                |
| ------------------- | -------------------------------------------------------------------------- |
| `deposit()`         | Supplies assets into the underlying protocol                               |
| `withdraw()`        | Withdraws assets from the protocol and returns them to the StrategyManager |
| `getCurrentAPY()`   | Returns the current lending or borrowing rate (depending on the mode)      |
| `getProtocolName()` | Returns a human-readable name for the protocol                             |

These functions allow Arya to interact with any integrated protocol in a consistent way, no matter how different their underlying smart contracts are.

***

### Adapter Interface

All adapters implement a base interface like the following (Solidity-style):

```solidity
solidityCopyEditinterface IProtocolAdapter {
    function deposit(uint256 amount) external;
    function withdraw(uint256 amount) external;
    function getCurrentAPY() external view returns (uint256);
    function getProtocolName() external view returns (string memory);
}
```

This ensures each adapter remains **interchangeable**, enabling dynamic routing and modular scaling.

***

### Supported Protocols (Initial Phase)

Arya includes built-in adapters for major DeFi protocols:

* **Aave Adapter**
* **Silo**
* **Euler**

Each adapter is built with rigorous testing and fallback protections to ensure safety during interaction.

***

### Benefits of Using Adapters

* **Plug-and-Play Architecture**\
  Add new protocols without redeploying core contracts.
* **Protocol Diversity**\
  Access a broader spectrum of interest rates and features.
* **Upgrade Flexibility**\
  Upgrade or replace individual adapters without disrupting user positions.
* **Gas Optimization**\
  Each adapter is optimized for low-overhead interactions with its target protocol.

***

### Adapter Lifecycle

1. **Deployment**\
   The adapter is deployed with a reference to its protocol’s relevant smart contracts.
2. **Registration**\
   The adapter is registered with the StrategyManager contract.
3. **Integration**\
   Once verified, it becomes part of the routing engine and can receive user funds.
4. **Maintenance**\
   If a protocol changes, the adapter can be swapped out with a new version safely.

***

### Example: Aave Adapter Flow

1. User deposits USDC
2. StrategyManager selects Aave Adapter based on yield
3. Aave Adapter calls `LendingPool.deposit()`
4. Funds are now earning yield in Aave, managed by Arya
