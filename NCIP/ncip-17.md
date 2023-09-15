---
NCIP: 17
Title: Revise `ClaimStakeReward` 
Status: Draft
Type: Core
Author: Swen Mun <swen@planetariumhq.com>, Nine Chronicles DX team <game-dx@planetariumhq.com> et al.
Created: 2023-09-05
---
# Abstract

This proposal addresses a fairness problem on staking system, by a new reward scheme with slightly modifications for chain states and related actions.

# Motivation

When staking reward policy changes from `A` to `B`, current calculation for staking reward is,

`Total Reward` = `A(Expiration Block Index of A - Staked Block Index)` + `B(Current Block Index - Expiration Block Index of A)`

Although it seems quite accurate, there're two problems as below.

- **Fairness**
  - When users stake with `A`, there is no information about `B` for users.
  - This is not a problem when `B`'s reward size is greater than `A`'s, but it isn't otherwise.
- **Complexity**
  - To keep current scheme, we need to assign expiration block index for each reward policy.
  - Also, we must perform a hard-fork for that action changes, per each revision of reward policy, regardless its complexity.

To eliminate fairness and complexity concern, this proposal suggests more simplified reward scheme that, only applied `A` if users saw and staked upon `A`, not `B` (or any other future changes).

# Specification

To simplify, `ClaimStakeReward` action should know reward policy for each users. specifically, the following changes are required:

## `Stake`
`Stake` action needs to record the reward policy at the time of staking. To accomplish this, we need to keep reward policy as immutable and dedicate state address per reward policy. To keep reward policy as immutable, it stores the reward policy in a new state model called `StakeStateV2`.

### `StakeStateV2`

`StakeStateV2` is a new state model to store its staking Contract in the state.

From `StakeStateV2`, a `Contract` is created with the information at the time of the staking contract and stored in the state. This is to be used when receiving rewards.

The state is stored in List format rather than Dictionary. The schema is as follows.
```
[
  "stake_state",              # Constant string. state type name.
  2,                          # Constant number. state type version.
  serialized(Contract),       # A contract to keep the reward policy as immutable.
  StaredBlockIndex,           # The block index when the staking contract has been started.
  ReceivedBlockIndex,         # The block index when the staking rewards were claimed most recently.
]
```

### `Contract`

For sake of ease, the new state model called `Contract` will be needed. The `Contract` model consists of for fields as below:

- `StakeRegularFixedRewardSheetTableName` (`string`)
- `StakeRegularRewardSheetTableName` (`string`)
- `RewardInterval` (`long`)
- `LockupInterval` (`long`)

The state is stored in List format rather than Dictionary. The schema is as follows.

```
[
  "stake_contract",           # Constant string. state type name.
  1,                          # Constant number. state type version.
  StakeRegularFixedRewardSheetTableName,        # The `StakeRegularFixedRewardSheet` tablesheet's name from `StakePolicySheet` when the staking contract was signed.
  StakeRegularRewardSheetTableName,       # The `StakeRegularRewardSheet` tablesheet's name from `StakePolicySheet` when the staking contract was signed.
  RewardInterval,    # The block interval to claim staking rewards of this staking contract.
  LockupInterval,    # The block interval to cancel this staking contract.
]
```

## `ClaimStakeReward`

![image](https://github.com/planetarium/NCIPs/assets/128436/7a291498-209e-41dc-a9fa-3efa705916a9)

`ClaimStakeReward` action needs to be processed based only recorded policy, without any other aggregation.

# Backward Compatibility

* This proposal requires the hard-forks as like below reasons:
  - The proposed `Stake` action will produce different output state due to additional fields.(i.e., reward policy)
  - The proposed `ClaimStakeReward` action will produce different output state since it wouldn't aggregate based upon previous policies anymore.
* It means that, every nodes in the network must be updated to apply this changes.
