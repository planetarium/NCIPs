--- 
NCIP: 28
Title: Hard / Hell Mode Expansion and Resource Structure Overhaul
Status: Draft
Type: Core
Author: Jaeho Lee <jaeho@planetariumhq.com)
Created: 2026-03-12
---

## Abstract

This proposal aims to extend the endgame growth loop by introducing Hard and Hell modes built upon the existing Worlds 1–9.

Key components of this proposal are as follows:

- Addition of Hard / Hell modes to existing worlds
- Introduction of Hard-exclusive materials with a dual-consumption structure (AP + materials)
- Separation of Normal / Premium crafting paths for Hard equipment
- Introduction of a material linkage structure with the NCU (Nine Chronicles Universe) project

Rather than adding large amounts of new content, this proposal reinterprets existing content as an upper-tier growth layer.

---

## Motivation

### 1. Strengthening Endgame Progression Incentives

After completing the Normal World 1–9 story, there is a structural need to incentivize continued stat growth. Hard mode provides a clear reason for repeated play.

### 2. Reducing Tension Caused by AP Oversupply

As the supply of AP potions has increased, the weight of decision-making has diminished even in upper-tier equipment acquisition. Hard mode seeks to restore tension through a structured resource consumption system.

### 3. Separation from Crystal Inflation

Growth beyond Hard mode is designed so that crystal cannot serve as a substitute, maintaining a play-based growth bottleneck.

### 4. Structural Integration with the NCU Ecosystem

By linking select crafting and progression materials to NCU projects, this proposal strengthens the expandability of the Nine Chronicles Universe.

---

## Rationale

### 1. Reuse of Existing Content

Instead of adding new worlds, existing Worlds 1–9 are repurposed as higher-difficulty layers.

### 2. Minimizing Learning Overhead

- Monster appearances and patterns remain unchanged
- Rule changes are kept to a minimum
- Difficulty increases are perception-based

### 3. Dual Tension Structure

Hard mode introduces two forms of tension:

1. **Entry resource tension**: AP + exclusive materials consumed simultaneously
2. **Crafting decision tension**: Normal vs. Premium crafting path selection

This creates a choice-based growth structure rather than simple repetition.

---

## Specification

### 1. Mode Structure

### Mode Types

| Mode | Description |
| --- | --- |
| Normal | Existing progression |
| Hard | Upper-tier repeatable growth mode |
| Hell | Future expansion mode |

### Unlock Conditions

- Clearing the final stage of Normal World 9 unlocks Hard World 1
- The first world of each mode is free
- Subsequent worlds are unlocked with Crystals

---

### 2. Hard Mode Entry Structure

When progressing through Hard mode stages:

> AP and Hard-exclusive new materials are consumed simultaneously.
> 

Applicable to:

- Challenge
- Sweep

Purpose:

- Add meaningful context to AP consumption
- Strategize automated repeat play

---

### 3. Hard-Exclusive Progression Materials

### Acquisition Sources

- Initially added to Patrol rewards for the worlds preceding Hard difficulty
    - Subsequent acquisition will be designed through various content including NCU integration described below
- Additional acquisition based on Monster Collection completion rate

### Supply Cap

> Additional acquisition from Monster Collection must not exceed 2× the base acquisition rate.
> 

### Properties

- Cannot be substituted with Crystals
- Transfer-restricted
- Exclusive to Hard stage progression

---

### 4. Hard Equipment Crafting Structure

- Existing crafting UI is retained
- Existing materials are replaced with materials dropped exclusively from Hard stages

---

### 5. Normal / Premium Crafting Separation

Two options are provided when crafting Hard equipment:

### Normal Crafting

- Consumes **Golden Dust**
- Lower option grant probability
- Same maximum option value
- Lower minimum option value

→ High-iteration crafting path

### Premium Crafting

- Consumes **Emerald Dust**
- Higher option grant probability
- Same maximum option value
- Higher minimum option value

→ Increased average expected value with reduced risk

### Design Principles

- Maximum option values are identical across both paths
- Differentiation lies in average expected value and stability
- Pay-to-Win structure is avoided

---

### 6. Transcendent Grade (Hard World 1 Signature Equipment)

Hard World 1 introduces a **"Transcendent Grade"** equipment tier above the existing Epic grade.

Visual effects applied without modifying Spine assets:

- Fragment orbiting effect
- Attack afterimage
- Distortion effect on hit

This tier serves as a symbolic milestone for entering Hard mode.

---

### 6-1. Hard-Exclusive Equipment Enhancement Structure and NCG Consumption Design

Hard-exclusive equipment (including Transcendent Grade) is designed so that base stat differences from existing Mythic grade equipment are not dramatic, to avoid suddenly devaluing existing gear.

However, Hard-exclusive equipment features the following enhancement structure:

### Enhancement Growth Structure

- Growth percentage (%) per enhancement level is set higher than existing equipment
- Higher investment required at the same enhancement stage
- Significant perceived growth at high enhancement tiers

### Enhancement Cost Structure

- NCG costs for enhancement are set higher than existing equipment
- Each enhancement attempt is designed to represent a meaningful investment

### Design Intent

This structure is not a simple difficulty increase, but part of a long-term tokenomics design to strengthen in-game NCG consumption. Goals include:

1. Expand meaningful NCG sinks in post-Hard content
2. Reinforce the value of investment at high enhancement tiers
3. Maintain long-term NCG value stability
4. Strengthen the connection between progression and investment

Hard equipment differentiates itself not through **base stat gaps**, but through **growth potential driven by investment**.

### Reward Design Direction

As enhancement costs increase, players will be compensated as follows:

- Significant perceived performance gains at high enhancement tiers
- Increased efficiency for progressing into upper Hard / Hell content
- Clear and satisfying rewards for long-term investment

### Economic Perspective

The Hard equipment enhancement structure follows these principles:

- NCG functions as both a consumable asset and a growth investment asset
- Prevents NCG from accumulating without being spent in upper-tier content
- Gap between high-investment and general players is based on "time + investment"

This design is not a short-term measure to prop up NCG value, but a long-term strategy to create a healthy consumption cycle in the endgame.

---

### 7. NCU Integration Structure

### 7.1 Rationale for NCU Integration

Hard mode is designed not merely as a difficulty increase, but as an upper-tier growth hub connecting the entire Nine Chronicles Universe. Reasons for linking Hard mode resources with NCU projects include:

1. Forming a genuine connection between the main game and external projects
2. Expanding event-based growth loops
3. Enabling community-driven operational experiments
4. Strengthening short-term meta variation and participation incentives

Rather than immediately integrating Hard economics directly, a **phased expansion of integration scope** is adopted.

---

### 7.2 Phased Integration Structure

### Phase 1: New Rune Fragment–Centered Integration

Initially, **new Rune Fragments** (rather than Hard-exclusive materials) are used as the primary NCU reward resource.

- New Rune Fragments are obtainable only through specific NCU projects
- Provide strong effects in the main game for a limited period
- Indirectly affect Hard mode entry and progression

Purpose:

- Reinforce event participation incentives without causing direct inflation in Hard economics
- Provide a sense of cross-universe connection

---

### Phase 2: Partial Hard World Entry Material Integration

Once stability is verified, **a limited portion of Hard world entry materials may be provided as NCU rewards**.

- Only a portion of total supply is externally linked
- Strict minting quantity limits
- Distributed on a per-season/event basis

Purpose:

- Expand access opportunities to Hard mode
- Allow progression acceleration through event participation
- Prevent excessive economic distortion

---

### Phase 3: Partial Hard Crafting Material Integration

Final expansion scope may include:

- Some materials for Hard equipment crafting
- Supplementary materials that do not replace the core crafting bottleneck

Design principles:

- Hard core bottleneck remains play-based
- NCU rewards serve an "acceleration" role only
- Crafting structure is not undermined

---

### 7.3 Operator Minting Structure

- New Rune Fragments and select Hard materials are minted in limited quantities via operator privileges
- Distributed to specific NCU projects
- Those projects distribute within defined limits

Reasons for this structure:

- Prevents unlimited issuance
- Enables supply control
- Allows phased economic experimentation
- Minimizes inflation risk

Minting quantities and distribution methods are disclosed in advance via NCIP.

---

### 7.4 Garage Token–Based Transfer Structure

Materials and Rune Fragments:

- Can be transferred between accounts by consuming Garage tokens

Design purposes:

1. Prevent unlimited free transfers
2. Assign cost to resource movement
3. Maintain economic friction
4. Prevent event abuse

Garage tokens serve not merely as transaction fees, but as a **responsibility cost for resource movement**.

---

### 7.5 NCU Integration Example – PETPOP Season 12

- 1,000 new Rune Fragments issued (limited)
- Distributed exclusively as PETPOP S12 ranking rewards
- Powerful limited BUFF applied for 4 weeks after season end

Potential future expansion:

- Partial Hard entry material distribution in specific seasons
- Limited Hard crafting supplementary material distribution

---

### 7.6 Expected Effects

The phased integration is expected to deliver the following:

1. NCU integration without abrupt distortion to Hard economics
2. Stronger event participation incentives
3. Tangible connection between the main game and NCU
4. Facilitated consumption of Hard resources
5. Establishment of a universe-wide growth structure

---

### 7.7 Risks and Mitigation

**Anticipated risks:**

- Economic distortion from excessive minting
- Benefits concentrated in specific projects
- Risk of Hard bottleneck collapse

**Mitigation measures:**

- Phased integration expansion
- Strict minting quantity limits
- Pre-disclosure via NCIP
- Time-limited effect application
- Immediate halt mechanism if needed

---

## Security Considerations

- **Minting authority control**: Operator-level minting of Rune Fragments and Hard materials must be strictly access-controlled to prevent unauthorized issuance.
- **Supply cap enforcement**: Monster Collection–based additional acquisition must not exceed 2× the base rate; this must be enforced at the contract/game logic level.
- **NCU project vetting**: Projects eligible to receive Hard-linked materials should be vetted to prevent manipulation or concentration of benefits.
- **Garage token abuse prevention**: Transfer friction via Garage tokens must be calibrated to prevent botting or multi-account exploitation during events.

---

## Backward Compatibility

- Existing Normal mode progression is unaffected.
- Hard mode is additive and does not alter any existing action types or state structures.
- No hard fork is required unless new on-chain action types (e.g., entry material consumption) are introduced. In that case, a coordinated network upgrade will be required.

---

## Expected Effects

- Recovery of AP tension
- Establishment of an upper-tier growth loop
- Formation of a play-based bottleneck separate from Crystal economics
- Natural insertion of monetization structure
- Expansion of the NCU ecosystem
- Reinforcement of choice-based endgame structure

---

## Expected Schedule (Tentative)

- Internal balancing and simulation
- Community feedback collection
- Revision based on feedback
- Phased rollout (Hard → Stabilization → Hell)