# Contract Storage

## Global Storage

The global storage of the dVOI contract stores the following values:

| field                | type           | description                                                                                                                                                                                      |
| -------------------- | -------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| updatable_by         | Byte (address) | Administrator address field. Power to update the contract code. When empty: the code is immutable. While this is set: the admin can rug.                                                         |
| fee_admin            | Byte (address) | Operator address field. Has the power to 1) withdraw collected fees 2) update fee_rate and mint_time_lock parameters (with a [1 week time lock](/immutability.html) and 3) change the fee_admin  |
| next_params_update   | Byte           | [Scheduled time-locked updates](/immutability.html) of fee_rate and/or mint_time_lock parameters. Structure documented [here](/immutability.html#changing-scheduled-updates).                    |
| fee_rate             | Number         | [Fee rate](/fees.html) in permille. E.g. 185 means fees of 18.5% on all distributed rewards                                                                                                      |
| mint_time_lock       | Number         | [Mint vesting period](/minting.html#vesting-period) in seconds                                                                                                                                   |
| init_balance         | Number         | Initial seed balance of contract escrow. 1 VOI. Used to calculate balances and rewards.                                                                                                          |
| circulating          | Number         | Circulating dVOI (including vesting dVOI). Used in [rate](/rate.html) calculations.                                                                                                              |
| withdrawable_balance | Number         | VOI balance available to withdraw by burning dVOI. Used in [rate](/rate.html) calculations.                                                                                                      |
| fees_balance         | Number         | Accumulated protocol fees. Withdrawable by "fee admin".                                                                                                                                          |
| last_known_balance   | Number         | The last escrow balance seen by the contract. Used to calculate when rewards have been distributed before a mint or a burn.                                                                      |

## Box Storage

Boxes are used to store vesting dVOI per user.

The box name is the user's address. The value is a concatenation of a uint32 timestamp of vesting, and a uint64 amount of VOI paid for the dVOI, which is used for early unmint refunds.
