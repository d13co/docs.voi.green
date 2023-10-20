# Immutability

Upon initial launch and during a brief testing period, the contract will be mutable (update/delete) by the admin (D13). This functionality will be gated by the value of a contract global storage field - `updatable_by`. The contract will be updatable for as long as this value is set.

After the `updatable_by` field is cleared, the contract's code will be permanently immutable. Changes to certain configuration values of the contract will still be possible by the `fee_admin` address and in a controlled manner.

Configuration changes to the contract will be time-delayed. The fee admin will be able to change the fee rate value, but there will be a time delay of at least 1 week (subject to change) before this change will take effect. Certain values may also have restrictions on the change delta, e.g. the fee rate may only be changed +/- 5% of its current value. As such, the fee admin would not be able to immediately change the fee rate to 100%, which would compromise dVOI holders' rewards.

## Fee Rate

The fee rate value `fee_rate` will be mutable with by the `fee_admin` address with a 1 week delay.

The updated fee rate value must be within 50 points of the previous one (up to +/- 5% rate change at a time)

## Mint Lock Duration

The minting process' dVOI lock duration value `mint_time_lock` will be mutable with by the `fee_admin` address with a 1 week delay.

The updated value will not have restrictions.

## Fee admin

The fee admin address `fee_admin` will be mutable by the `fee_admin` with immediate effect.

## Changing scheduled updates

If an update is scheduled but not vested yet, updating the scheduled values will reset the update timer to the initial value of 1 week.

Updates can also be staggered, e.g. the fee rate and the mint time lock values can be part of the same update. The last update value will reset the timer to 1 week, as before.

The update will not apply automatically. When its timestamp elapsed, it will either be applied by the fee admin by calling the contract, or they will be able to dismiss the change.

Scheduled updates will be stored as a JSON object in the `next_config_update` global storage value.

The structure will include `ts` for the timestamp after which the configuration can be applies, as well as key and value pairs for the updates to apply.
