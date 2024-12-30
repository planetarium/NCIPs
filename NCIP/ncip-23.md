---
NCIP: 23
Title: Another way to obtain higher-tier equipment - the Synthesis System.
Type: Core
Author: Jaeho Lee <jaeho@planetariumhq.com>, ChunUng Yang <yang@planetariumhq.com>, Eugene Hong <eugene@planetariumhq.com>
Created: 2024-12-16
---


## Abstract

The new synthesis system allows players to collect a specified number of equipment for each rarity tier and attempt to craft a higher-rarity piece of the same type. After a probability check:

On success, a higher-rarity equipment (one tier above) is crafted.
On failure, a new piece of equipment of the same rarity as the materials is crafted and immediately obtained.

## Motivation

- The equipment experience points provided by each rarity tier were set with significant differences to maintain the value of resources and activity levels upon entering each world. As a result, lower-rarity equipment did not hold much value as experience materials.
- Additionally, grinding, which serves as one of the use cases for unused equipment, struggled to deliver satisfaction proportional to the cost of obtaining it, making it challenging to balance effectively.
- These two factors contributed to a lack of incentives for the summoning system to function as a recurring part of the overall user experience. Consequently, the player's growth became overly reliant on specific systems.

## Rational

- Encouraging consistent use of the summoning system.
- Enhancing accessibility to low-probability equipment, as the summoning system operates as an independent event.
- Supporting diverse user activities to complete various collections.

## Specification

### **Synthesis Process (Flow)**

1. Acess Workshop 
2. Access the Synthesis Menu
3. Select Materials for Synthesis
4. Execute Synthesis

### **Synthesis Features**

**Synthesis Available Types**

- For existing equipment, guaranteed crafting is possible through recipes. Therefore, synthesis will initially be opened for the **Aura** and **Grimoire** types, which are obtained through summoning.

**Synthesis Materials and Success Rates**

- Each synthesis attempt consumes **5 AP** along with the required materials.
- The number of materials needed per attempt and the success rate for each execution are as follows, based on the equipment type and rarity:
    - Aura
    
    | rarity | number of materials | success rate(%) |
    | --- | --- | --- |
    | normal | 10 | 80 |
    | rare | 10 | 75 |
    | epic | 12 | 50 |
    | unique | 10 | 40 |
    | legend | 6 | 25 |
    | sacred | 3 | 0 |
    - Grimoire
    
    | rarity | number of materials | success rate(%) |
    | --- | --- | --- |
    | epic | 8 | 80 |
    | unique | 6 | 60 |
    | legend | 5 | 20 |
    | sacred | 3 | 0 |
- Each attempt can only process one type of equipment at a single rarity, up to a maximum of **12 attempts**.
- **On success**, equipment of the next rarity is obtained. **On failure**, equipment of the current rarity is re-obtained.
- Equipment meeting the following criteria **cannot be selected as materials**:
    - 1st Anniversary event equipment (Aura, Grimoire)
    - Currently equipped equipment
- Equipment meeting the following criteria **cannot be produced as results**:
    - 1st Anniversary event equipment (Aura, Grimoire)
    - Legend Lord aura equipment

### **Expected Schedule**

- **December 16**: Previewnet open testing begins (9c) - Play with the community.
     https://planetarium.notion.site/Previewnet-GUIDE-241216-15ded889905f8048b84afbab68ee81e6
- **December 18**: Collect community feedback
- **December 19**: Final version previewnet release completion.
- **December 20**: Mainnet release.

## **Backwards Compatibility**

- A new s**ynthesis** action will be added, and all nodes will need to be updated to interpret this action.
- No additional migration is required.

