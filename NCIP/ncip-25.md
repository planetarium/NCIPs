---
NCIP: 25
Title: Improvement of World Boss Reward System
Type: Core
Author: Jaeho Lee <jaeho@planetariumhq.com>, ChunUng Yang <yang@planetariumhq.com>, Eugene Hong <eugene@planetariumhq.com>
Created: 2025-02-18
---

## Abstract

Transition from an admin-controlled reward distribution system to a user-driven claim system where all users can claim rewards according to predefined rules.

## Motivation

The manual processing part of the world boss reward system imposes a load on the chain and incurs continuous costs for the development team. We aim to improve this part to create a system that operates more efficiently overall.

## Specification

To simplify the process, a new action `ClaimWorldBossReward` has been added, allowing users to claim rewards using their avatar address.

The plain value is stored in Dictionary format like other actions. The schema is as follows.
```
{
  "type_id": "claim_world_boss_reward",             # action type name.
  "values": [
    AvatarAddress                                   # target avatar address will claim reward.
  ]
}
```

- Change the season rewards received by users after the season ends from rank-based to a fixed total amount distributed according to contribution (like Adventure Boss).
- Instead of distributing rewards all at once after the season ends, allow individual claims over a certain period.
  - Claim period is available during the 2-week off-season.


### Reward Distribution(TBD)
- Total Reward Amount
  - Specify total reward amount per boss in a patch table to allow changes based on circumstances.
    - Draft of reward balance (TBD)
  - World Boss - Fenrir

  | Rune Fragment 1 | Rune Fragment 2 | Rune Fragment 3 | Golden Dust | Crystal | AP Potion |
  | --- | --- | --- | --- | --- | --- |
  | 300340 | 45740 | 5125 | 24600 | 14976300000 | 1270 |
  - World Boss - Saehrimnir

  | Rune Fragment 1 | Rune Fragment 2 | Rune Fragment 3 | Golden Dust | Crystal | AP Potion |
  | --- | --- | --- | --- | --- | --- |
  | 300340 | 45740 | 5125 | 24600 | 14976300000 | 1270 |

- Rune Information Provided as Rewards

| ID | Name | Ticker |
| --- | --- | --- |
| 10004 | Fenrir DHP Rune | RUNESTONE_FENRIR4 |
| 10005 | Fenrir SHT Rune | RUNESTONE_FENRIR5 |
| 10006 | Fenrir SPD Down Rune | RUNESTONE_FENRIR6 |
| 10014 | Saehrimnir AS Rune | RUNESTONE_SAEHRIMNIR4 |
| 10015 | Saehrimnir HPA Rune | RUNESTONE_SAEHRIMNIR5 |
| 10016 | Saehrimnir Skill Rune 2 | RUNESTONE_SAEHRIMNIR6 |

- Reward Processing Rules
  - Contribution % Calculation Formula
    - Total damage dealt during the season / Total damage dealt during the season * 100
      - Calculate Contribution % up to 4 decimal places (minimum 0.0001%).
  - Determine the quantity of rewards based on the Contribution %, truncating any decimal values.
    - If the total reward is 1M Rune Fragment 1, 10K Rune Fragment 2, and 1B Crystal, a user with a Contribution % of 0.01% receives 100 Rune Fragment 1, 10 Rune Fragment 2, and 10K Crystal.

### Additional Changes

- Due to too many perfect scorers in the world boss, change the required scores for A rank and S rank.
- As season rewards change from rank-based to contribution-based, fix the ticket purchase price at 1ncg.
  - Fixed at 1ncg up to the maximum number.

## Backward Compatibility

* This proposal requires hard-forks for the following reasons:
  - A new action type `claim_world_boss_reward` is added, and all nodes need to be updated to interpret the action.
  - A new sheet type `WorldBossContributionRewardSheet` is added for reward information.
  - `WorldBossState` will be record season's `ToTalDamage` for calculate each user's contribution.
