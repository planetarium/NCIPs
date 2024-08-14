---
NCIP: 21
Title: Improvements to the Selection of Adventure Bosses for Seasonal Bosses
Status: Draft
Type: Core
Author: Jaeho Lee <jaeho@planetariumhq.com.>.
Created: 2024-08-14
---




## **Abstract**

We propose two improvements to the method of selecting Adventure Bosses each season. After discussing these options with the community, we plan to proceed based on the consensus. Additionally, we seek approval for temporary measures until a final decision is made.

## **Motivation**

- The Adventure Boss system was initially designed to randomly select bosses at the start of each season, aiming to generate reward value based on varying circumstances.
    - However, relying solely on randomness has led to issues. For instance, in the Heimdall chain, it took 20 seasons before Hela appeared as a boss, despite the system being in place for three weeks.
    - We are considering changes to address this issue, but the next update won't be available until the end of August due to the current release schedule, which avoids overlapping with Arena periods.
    - Therefore, we are seeking community input on two approaches: a temporary solution through an event and a long-term solution through system upgrades.

## **Specification**

### Temporary Solution Through an Event

- To give more players access to the newly introduced resources, Emerald Dust and Critical Runes, we propose changing the guaranteed rewards for Surtr and Laufey bosses from Golden Dust and Ruby Dust to Critical Runes and Emerald Dust for a two-week event.
    - If this event is approved, it will run from August 16 to August 30, 2024.
    - During the event, the guaranteed rewards for Adventure Bosses on the Odin and Heimdall chains will be changed as follows:
        
        
        | Boss | Current Guaranteed Reward | New Guaranteed Reward |
        | --- | --- | --- |
        | Surtr | Golden Dust | Critical Rune |
        | Laufey | Ruby Dust | Emerald Dust |
    - We welcome your support for this proposal or suggestions for alternative approaches.

### Long-Term Solution Through System Upgrades

- Please indicate your preference between the following two options or suggest an alternative approach:
    1. A minor adjustment to ensure that the same World Boss does not appear consecutively.
        1. This option maintains the fun of random selection while adding a small control to prevent consecutive appearances.
    2. A major adjustment where World Bosses appear in a fixed, repeating order.
        1. This option minimizes the possibility of the current issue by removing randomness from the sequence, leaving only the combination of random rewards.

### Decision-Making Process for Proposed solutions

- A dedicated channel for discussion will be created on Discord, where the contents from the NCIP will be shared as they are.
    - Please proceed with discussions on the issues within the channel, and I will monitor and provide responses as needed.
    - A vote will be conducted in the channel, and the results, along with progress updates, will be added to the NCIP for further action.

## **Backward Compatibility**

- This proposal requires a hard fork and a temporary table patch for the following reasons:
    - The action that determines the seasonal Adventure Boss will be reconfigured.
    - During the event, the reward sheets for Adventure Bosses, **AdventureBossWantedRewardSheet** and **AdventureBossContributionRewardSheet**, will be updated to reflect the event-specific changes.