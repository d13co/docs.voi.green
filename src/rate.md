# dVOI:VOI Rate

The dVOI:VOI rate starts at 1:1, with:
- all dVOI in the contract 
  - dVOI circulation: 0
- no VOI balance to "back" the circulating dVOI
  - withdrawable balance: 0

Users who mint dVOI before any rewards are distributed will receive 1 dVOI for each VOI they deposit.

As rewards are distributed, the VOI corresponding to each circulating dVOI will increase, so the dVOI price in VOI will also increase.

Minting and burning rates are calculated with a formula that maintains the current dVOI/VOI rate. This aims to protect earlier users' accumulated rewards from being diluted by later users.

Aside from rewards distributions, the process of [early unminting](/early-unmint.html) may also affect the dVOI:VOI rate (in dVOI holders' favor). This would be apparent if unvested dVOI is early-unminted after rewards have been distributed, or more subtly if the unvested dVOI contributed to increased block production during its tenure in the escrow account but unminted before the rewards distribution.

## Rate formula

The formula used to calculate the rate of dVOI to VOI is:
m
\\[\frac{Circulating\ dVOI}{Withdrawable\ VOI}\\]

Where: 

- "Circulating dVOI" is the total amount of minted dVOI (both vested and unvested.)
- "Withdrawable VOI" is the VOI held in the contract that is redeemable to users via burning. It comprises of user VOI deposits, and the rewards distributed to the contract (minus the fees that the protocol subtracts from each rewards distribution.)

## Mint rate formula

The formula used to mint new dVOI without affecting the dVOI:VOI rate is:

\\[Minted\ dVOI=\frac{(Withdrawable\ VOI + Deposit) * Circulating\ dVOI}{Withdrawable\ VOI} - Circulating\ dVOI\\]

Where:

- Minted dVOI: The amount of dVOI allocated to the user for their deposit
- Withdrawable VOI: The amount of withdrawable VOI before the user deposit
- Deposit: The amount of VOI the user is sending to mint some dVOI
- Circulating dVOI: The previous circulating dVOI amount

## Burn rate formula

The VOI returned when burning dVOI is calculated with this formula:

\\[Return\ VOI=Withdrawable\ VOI-\frac{(Circulating\ dVOI - Burned) * Withdrawable\ VOI}{Circulating\ dVOI}\\]

Where:

- Return VOI: The amount of VOI the user receives for their burn deposit
- Withdrawable VOI: The amount of withdrawable VOI before the dVOI burn
- Burned: The amount of dVOI the user is burning/exchanging for VOI
- Circulating dVOI: The previous circulating dVOI amount
