---
NCIP: 20
Title: NCG Staking-Based NCG Distribution
Status: Draft
Type: Core
Author: Jaeho Lee <jaeho@planetariumhq.com.>.
Created: 2024-08-14
---



### Abstract

A system is scheduled to be released that will distribute NCG generated from validation rewards and NCG used by players on the chain to users currently staking NCG through the GUILD system and PoS release. During the preparation process for this system, there will be three manual distributions starting from August, along with related preparations.

### Context

Nine Chronicles ecosystem is preparing for a transition to PoS (Proof of Stake). One of the preparations for this transition is the development of the Guild system. A key feature of the GUILD system being developed is that "members of the GUILD will receive rewards for block validation (limited to the ODIN chain) and a portion of the NCG used by users on the chain will be distributed among the Guild, validators, and players in a specific ratio."

### Rationale

Please refer to NCIP-19 for a detailed explanation of the GUILD system.

### Specification

As we are preparing for the transition to PoS, we would like to manually proceed with the NCG distribution feature, which is one of the related functions.

- Some operations of the Monster Collection will be modified, and players will receive NCG in addition to the current items when claiming rewards.
- During Q3 and Q4 of 2024, there will be three manual distributions to test this reward system.
    - The final distribution process in the system will be different from these manual distributions. However, before the system is implemented, we will proceed with a preliminary distribution based on the NCG used within the Monster Collection.
    - Currently, Planetarium Labs and Nine Corporation are staking 10 million NCG per chain, and the rewards generated from this staking are being used to sell as mobile packages. Although this represents 28% to 34% of the NCG staking per chain, for this manual distribution, the maximum ratio applied will be limited to 25%, allowing for a more significant portion to be distributed to the players.
    - The first distribution is scheduled for mid-August, and it will calculate the NCG distribution based on the amount of NCG used from July to the snapshot taken before the distribution, including a portion of the NCG used for Adventure Boss bounties and floor unlocks. The distribution ratio will be determined based on the amount of NCG staked.
    - After the first distribution in August, the second distribution will take place in September, with a potential third distribution depending on the development schedule. In the second distribution, in addition to the NCG used for adventure bosses, all NCG used by players across the chain will be redistributed. The sections where NCG usage will be redistributed are as follows:
        
        
        | Distribution | Timing | Source of Distributed NCG |
        | --- | --- | --- |
        | 1st | Mid-August | NCG used for Adventure Boss from July to mid-August |
        | 2nd | Mid-September | NCG used for adventure bosses from mid-August to mid-September + 9C gameplay NCG from July to mid-September |
        | 3rd | Mid-October | NCG used for adventure bosses from mid-September to mid-October + 9C gameplay NCG from September to mid-October |
        - 9C gameplay NCG spent on the following:
            - Shop Fee
            - Item Enhancement
            - Arena Ticket
            - World Boss Ticket
            - Event Dungeon Ticket
            - Rune Enhancements
            - Rune Slot Unlock
            - Pet Enhancements
            - Adventure Boss Bounty
            - Adventure Boss Floor Unlock
    - The minimum unit for this distribution will be 0.01 NCG, and any player allocated less than 0.01 NCG will be excluded from the distribution.
    - For the ODIN chain, only users who have migrated after Monster Collection V2 or started staking after block 4286628 will be eligible for distribution.
- After the initial manual distributions, an automated system for NCG distribution based on the GUILD system will be released. When this system is released, a more detailed explanation will be provided, but the current plan is to calculate the amount of NCG to be claimed up to that point when players perform a Monster Collection claim action, allowing them to receive NCG along with the item rewards.