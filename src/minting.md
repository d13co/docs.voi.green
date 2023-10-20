# Minting

Users can mint dVOI by depositiing VOI to the protocol.

The deposited VOI will be used to participate in the Voi Testnet consensus protocol, and receive rewards.

Part of the Voi testnet consensus rewards are fixed (node health rewards) and the remaining rewards are proportional to participation in block production, which in turn is proportional to online stake.

The dVOI token and protocol allows users to get exposure to these rewards, as dVOI will appreciate in value against VOI with each rewards distribution. 

## Vesting Period

**Minting dVOI currently has a vesting period of 1 week**, during which the dVOI is allocated to the user but not withdrawable. The exchange rate is fixed at the time of minting, but the dVOI is locked in the contract until the week elapses.

### Why?

On the Voi testnet, consensus rewards distributions currently take place weekly at a fixed time (Mondays.) 

As such, a well designed delegation token needs a way to ensure that users claiming rewards have contributed meaningfully to the generation of said rewards.

Without a dVOI vesting period, users could mint dVOI on the day of rewards distribution, wait for rewards to be distributed, and then burn back to VOI. This would be problematic, as they would not contribute to the online stake meaningfully over the week (and thus protocol consensus rewards), but only for a few hours.


## Claim vested dVOI

After the vesting period has elapsed, users will be able to claim their dVOI from the contract, or alternatively a backend service will be able to call the contract on their behalf and airdrop their dVOI to their wallet - assuming they remain opted in to dVOI, which will be part of the minting process.

Note: the vested dVOI will only be sent directly to the user who minted it, regardless of who issues the transaction to the contract - user or a backend service.

Users who wish to back out of their vesting dVOI will be able to [unmint early](/early-unmint.html) and forfeit any rewards.
