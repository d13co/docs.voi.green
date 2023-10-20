# How it Works

The dVOI contract [escrow address](https://voi.observer/explorer/account/DELEGATEDW322SS7PBDKGZ6WCMU5NE2MC33KO4JX252SNUQNC7U5J5ZSOQ/) participates in consensus and receives consensus rewards. Part of those rewards are proportional to the VOI staked. dVOI allows users who are unable to run a node to participate in the consensus rewards of the Voi Testnet network.

To [mint dVOI](/minting.html), users can delegate their VOI to the contract will be allocated the equivalent dVOI according to the dVOI:VOI rate at the time of minting.

The allocated dVOI remains locked in the contract for the duration of the dVOI vesting period - 1 week. This mechanism protects the protocol from users dipping in to dVOI before the rewards are distributed, and then burn back to VOI immediately, thus diluting honest users' rewards without participating meaningfully in the online stake that generates those rewards.

After receiving their dVOI tokens, users can claim their rewards at any time by [burning their dVOI for VOI](/burning.html). Since the vesting period overlaps the consensus participation rewards period, users should always be able to exchange their dVOI for more VOI than they minted it with.

The rate of dVOI to VOI remains constant through minting and burning - the only thing that should change the exchange rate offered by the dVOI contract is disbursement of rewards. This ensures that dVOI holder rewards are not diluted by other users minting or burning dVOI.

As such, the rate of dVOI to VOI will start at 1:1 before any consensus rewards are distributed to the dVOI escrow account, and then dVOI will appreciate with each consensus rewards disbursement.

The mechanism of minting is only way dVOI enters circulation. No dVOI is allocated to "the team", or any other such back-handed nonsense.

Minting and burning dVOI does not incur any fees. The protocol takes fees from the distributed rewards.
