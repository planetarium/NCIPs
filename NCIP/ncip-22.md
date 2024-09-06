---
NCIP: 22
Title: A system for continuously crafting the desired equipment: Custom Craft
Type: Core
Author: Jaeho Lee <jaeho@planetariumhq.com>, Jonghyeon Moon <hyeon@planetariumhq.com>, Seonmin Kim <kimsm@planetariumhq.com>
Created: 2024-09-06
---


## Abstract

By introducing a new equipment crafting system, players can create equipment with specs that continuously grow and a wide range of skills. This allows players to design equipment in the form they desire and obtain equipment with their preferred appearance. I would like to hear various opinions on this system.

## Motivation

- To reduce the excessive cost burden caused by the repetitive addition of world content.
- The addition of diverse content has led to an increased demand for various types of equipment setups.
- To overcome the limitations of the current system, where equipment appearance is determined by its specs, and to allow players to choose appearances that suit their preferences.

## Rational

- Establishment of a system that grows repeatedly with a long-term goal.
- Breaking away from the constraints of building content environments based on predefined specifications.
- Creation of NFTs that reflect one's preferences to the maximum extent in both appearance and performance.

## Specification

### **Crafting Materials**

The materials needed for crafting equipment are "Scrolls" and "Circles."

- **Scroll (Short for Design Scroll):**
    - Obtained through *Monster Collection (NCG - Staking)*.
    - **Tradable**.
- Circle (Short for Circle of Fate)
    - Can be obtained as stage rewards, world boss rewards, and first-clear rewards from adventure boss content.
    - **Tradable**.

### **Crafting Process (Flow)**

1. **Workshop**: Perform basic tasks required for crafting equipment.
2. **Custom Craft**: Set the desired appearance and stats of the equipment.
3. **Craft**: Create the equipment based on the configured settings.
4. **Relationship Added**: Produce more powerful equipment through repeated increases in intimacy.

### **Detailed Crafting Menu**

- **Weapons**: Displayed with animations.
- **Necklaces, Rings, etc.**: Displayed with the image of the item.

When crafting equipment, detailed information about the equipment to be crafted is displayed:

- **Equipment Information**:
    - Name (e.g., Custom + Weapon Name format)
    - Expected Block
    - Experience Points to be Gained
    - Level Requirement to Equip
    - Total Craft Count for the equipment crafted in this appearance
- **Equipment Option Information**:
    - Basic Stats
    - Sub-stat CP Range
    - Random Attribute (randomly determined from None, Fire, Water, Wind, or Earth)
    - Skill List
        - Custom equipment has a 100% chance to acquire skills, and the skill list and probability are determined based on the type of equipment.
- **Required Materials**:
    - Scrolls + Circles are required by default.
    - NCG or additional materials may be required once when reaching certain intimacy levels.

### **Custom Equipment Crafting Features**

- **Relationship System**: The avatar gains "Relationship" points based on the number of times it is crafted.
    - Each custom craft increases relationship by 1.
    - As relationship increases beyond a certain point, the selectable appearances and sub-stat CP that can be obtained increase.
        - Create equipment that best fits the strategic meta you wish to adopt.
- **Sub-stat Distribution Method**:
    - The total sub-stat CP is determined randomly during crafting.
    - CP is distributed according to predetermined stat ratios based on the randomly determined options.
    - The final stats are determined by applying a CP conversion formula.
- There are unique appearances that can only be selected through the random appearance selection.
- More than 30 new appearances will be added, revealed for the first time through custom crafting.

### **Expected Schedule**

- **September 6**: Previewnet open testing begins (9c) - Play with the community.
    - [Previewnet GUIDE(240902)](https://planetarium.notion.site/Previewnet-GUIDE-240902-7eb96e8e0631443bb119e0c58cbc2ca7)
- **September 13**: Collect community feedback and distribute the second build.
- **September 23**: Final version development completion and QA start.
- **September 30**: Mainnet release.

## **Backwards Compatibility**

- A new custom equipment crafting action will be added, and all nodes will need to be updated to interpret this action.
- No additional migration is required.
