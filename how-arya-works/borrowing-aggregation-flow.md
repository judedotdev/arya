# Borrowing Aggregation Flow

When a user wants to borrow an asset:

1. The user supplies collateral through Arya.
2. Arya checks borrowing rates, LTV ratios, and risk profiles across platforms.
3. It selects the protocol with the **lowest APR** and most favorable terms.
4. If a better rate appears later, Arya can migrate the debt position.
