# Immutability

Upon initial launch and during a brief testing period, the contract will be mutable (update/delete) by the admin (D13). This functionality will be gated by the value of a contract global storage field - `updatable_by`. The contract will be updatable for as long as this value is set.

After the `updatable_by` field is cleared, the contract's code will be permanently immutable. Changes to certain configuration values of the contract will still be possible by the `fee_admin` address and in a controlled manner.

Configuration changes to the contract will be time-delayed. The fee admin will be able to change the fee rate value, but there will be a time delay of at least 1 week (subject to change) before this change will take effect. Certain values may also have restrictions on the change delta, e.g. the fee rate may only be changed +/- 5% at a time. As such, the fee admin would not be able to immediately change the fee rate to 100%, which would compromise dVOI holders' rewards.

## Fee Rate

The fee rate value `fee_rate` will be mutable with by the `fee_admin` address with a 1 week delay.

The updated fee rate value must be within 50 points of the previous one (up to +/- 5% rate change at a time)

## Mint Lock Duration

The minting process' dVOI lock duration value `mint_time_lock` will be mutable with by the `fee_admin` address with a 1 week delay.

The update delta does not have any restrictions.

## Changing scheduled updates

If an update is issued while a previous update is scheduled, the timer will reset to the initial value of 1 week.

Updates can also be staggered, e.g. the fee rate and the mint time lock values can be part of the same update. The last update value will reset the timer to 1 week, as before.

The update will not apply automatically. When its timestamp elapsed, it will either be applied by the fee admin by calling the contract, or they will be able to dismiss the change.

Scheduled updates will be stored as in the `next_params_update` global storage value.

The structure of this field is:

```
0: [4 bytes] timestamp_applicable uint32
4: [2 bytes] fee_rate uint16
6: [4 bytes] mint_time_lock uint32
```
## Immediately updatable parameters

### Fee admin

The fee admin address `fee_admin` will be mutable by the `fee_admin` with immediate effect.
