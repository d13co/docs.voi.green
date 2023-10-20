# Fee Structure

## Mint & Burn fees

Minting, burning and early unmninting do not incur any platform fees. The only fees you will be charged during these operations are network transaction fees.

The mint and burn rates will be at the dVOI/VOI rate at the time of transaction - see the [Rate section](/rate.html) for an explanation.

*Note: This is subject to change while the protocol is in design.*

Early unminting will return the VOI deposited to mint dVOI at that rate, regardless of the current dVOI:VOI exchange rate.

## Reward fees

The platform takes fees on each rewards distribution. The percentage is configurable throughout the lifetime of the contract, and can be seen under the global storage key `fee_rate`. This value is per-mille (%%) so you can divide by 10 to get the percent fee. The initial value `185` corresponds to `18.5%`.

There are mechanisms in place to protects dVOI users from the operator changing fees abruptly, see [Immutability - Fee Rate](/immutability.html#fee-rate).

As an example of the allocation of a rewards payment:

- Rewards deposited: 1,000 VOI
- Fee Rate: 18.5% 
- Fee purse increase: 185 VOI
- Withdrawable balance increase: 815 VOI
  - This balance is the denominator in the dOVI/VOI exchange rate.

## Execution of rewards distribution

The contract keeps tracck of the last known balance of its escrow address. It will upodate the withdrawable and fee balances when it is called to mint, burn or update_balances.

Minting immediately after a rewards distribution - while the contract hasn't updated the tracked balances yet - is supported, and will update the balances and exchange rate before the mint/burn operation.
