# Lending Aggregation Flow

When a user deposits an asset into Arya (e.g., USDC), the protocol:

1. Automatically finds the best lending platform offering the highest APY.
2. Routes the funds to that protocol via smart contract adapters.
3. Continuously monitors for better rates.
4. Rebalances the funds to a higher-yielding protocol when necessary.
