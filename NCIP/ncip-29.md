---
NCIP: 29
Title: Progress-based Automatic Opening of New Hard Worlds (Request for Community Input)
Status: Draft
Type: Core
Author: Jaeho <jaeho@planetariumhq.com>
Created: 2026-10-06
Related: NCIP-28 (Hard/Hell Mode Expansion)
---

## Abstract

This proposal changes how new Hard Worlds open: **instead of opening on a fixed date, each new stage range opens automatically based on how far adventurers have progressed in the previous world.**

Stage and equipment data for upcoming worlds will be deployed to the chain in advance. When server-wide progress indicators reach their thresholds, the next stage range opens without a separate patch.

**This NCIP is published without deciding which indicators will be used.** We are asking the community which of the candidate indicators below to use, how to combine them, and what thresholds feel right. The results will be reflected in this NCIP before it is finalized.

## Motivation

Starting in December 2026, a new Hard World will be added roughly every six months. Each world opens in two parts: the first half (20 stages) and the second half (30 stages).

| Planned Period | World | Stages |
| --- | --- | --- |
| 2026-12 | 11 Alfheim - Hard | 521–550 |
| 2027 H1 | 12 Svartalfheim - Hard | 551–570 → 571–600 |
| 2027 H2 | 13 Asgard - Hard | 601–620 → 621–650 |
| 2028–2029 | 14 Muspelheim – 17 Hel - Hard | 651–850 |

Until now, new worlds have opened on a set date through a patch. This has two drawbacks.

- **Openings ignore actual progress.** Sometimes a new world opens before top players have cleared the previous one; other times players clear everything and then wait for months.
- **Adventurers' efforts don't influence when content opens.** Hard Worlds are built so that leading adventurers clear the path first, and their output (equipment, materials) flows to those who follow. It is natural for the opening of the next path to be decided by that same progress.

## Framework (Decided in This NCIP)

Regardless of which indicators are chosen, the following framework is fixed by this NCIP.

| # | Principle | Description |
| --- | --- | --- |
| 1 | **Open by progress** | When server-wide progress indicators in the previous world reach their thresholds, the opening of the next range is confirmed |
| 2 | **Earliest opening point** | No matter how quickly thresholds are reached, content will not open before this point (prevents rushing, e.g., via multiple accounts) |
| 3 | **Latest opening point** | Even if thresholds are not reached, content will always open at this point (prevents content from never opening) |
| 4 | **Grace period after confirmation** | Once an opening is confirmed, content actually opens about 3 days later, leaving time for announcements and preparation |
| 5 | **No rollback** | A confirmed opening is never cancelled |
| 6 | **Separate evaluation for Odin / Heimdall** | Player populations differ, so each chain has its own thresholds |
| 7 | **Existing worlds unchanged** | Worlds 1–10, Mimisbrunnr, and the already-open range of World 11 are unaffected |

## 🗳️ Community Input Requested

### Candidate Indicators

The following can be measured precisely on-chain. **One or more of them can be combined** into opening conditions. You may also propose indicators not on this list, as long as they can be measured from on-chain actions.

| # | Indicator | What It Counts | Who Drives It | Strengths | Concerns |
| --- | --- | --- | --- | --- | --- |
| M1 | **Final stage clears** | Number of adventurers who cleared the final stage of the previous world (or range) for the first time | Top players | Clear and simple: "Once N adventurers conquer it, the next world opens" | Only a small group of top players contributes |
| M2 | **Mid-stage arrivals** | Number of adventurers who reached a specific mid-point stage in the previous world | Top to upper-mid players | More adventurers contribute | Too easy or too hard depending on which stage is chosen |
| M3 | **Mid-range play count** | Cumulative plays and sweeps in a specific range of the previous world | Highly active players | Rewards steady play | Can be inflated by a few players repeating plays |
| M4 | **Final weapon crafts** | Cumulative crafts of the previous world's top-grade weapon | Crafting and economic activity | Tied to equipment supply in the market | Can be heavily swayed by a few resource-rich players |

### How Indicators Can Be Combined

| Method | Meaning | Example |
| --- | --- | --- |
| **AND** | All conditions must be met | M1 ≥ A adventurers **and** M4 ≥ B crafts |
| **OR** | Any one condition is enough | M1 ≥ A adventurers **or** M3 ≥ C plays |
| **Mixed** | OR between groups, AND within a group | (M1 ≥ A **and** M4 ≥ B) **or** M2 ≥ D |

### Example Combinations (For Reference)

These are not decided options, only starting points for discussion.

| Example | Condition | Character |
| --- | --- | --- |
| A. Vanguard | M1 | The next path opens the moment top players conquer the world |
| B. Joint progress | M2 **AND** M4 | Opens only when both progression and equipment supply are in place |
| C. All-out effort | M1 **OR** M3 | Opens when either conquest or steady play fills up |
| D. Balanced | M1 **AND** M2 | Both the leaders and the following group must reach a certain level |

### Questions for the Community

| # | Question |
| --- | --- |
| Q1 | Which indicators (M1–M4, or a new one) should be used? |
| Q2 | If multiple indicators are used, should they be combined with AND, OR, or a mix? |
| Q3 | What threshold level feels right? (e.g., "when the top N players clear it", "when X% of active adventurers reach it") |
| Q4 | Should progress (a gauge) be shown in-game? Exact numbers / in 10% steps / hidden |
| Q5 | How wide should the window between the earliest and latest opening points be? (Reference: about ±1 month around the previous schedule) |
| Q6 | Should the first half (20 stages) and second half (30 stages) use the same indicators or different ones? |

### Feedback and Decision Process

| Step | Description |
| --- | --- |
| 1 | Publish this NCIP and announce it (Discord, Developer Portal) |
| 2 | **Two-week** feedback period — this NCIP's GitHub discussion / designated Discord channel |
| 3 | Publish a summary of feedback (number of responses per opinion, and reasons for adoption or non-adoption) |
| 4 | Reflect the adopted indicators, combinations, and thresholds in this NCIP's Specification and finalize it |
| 5 | Apply from World 12 (2027 H1). The second half of World 11 (521–550) opens on its existing schedule, and its progress data will be used to set thresholds |

## Specification

So that any chosen combination can be supported, the structure separates **indicators, conditions, and openings** and defines them as data. The community's decision will be applied as values in the sheets below, without further code changes.

### 1. New Sheets

#### `GlobalCounterSheet` — Indicator Definitions

| Column | Description |
| --- | --- |
| `id` | Indicator ID |
| `type` | `STAGE_FIRST_CLEAR` (M1, M2) / `STAGE_PLAY` (M3) / `RECIPE_CRAFT` (M4) |
| `target_begin`, `target_end` | Target stage or recipe range |
| `min_avatar_level` | Avatars below this level are excluded from counting |

| Type | Incremented In | Rule |
| --- | --- | --- |
| `STAGE_FIRST_CLEAR` | `HackAndSlash` | +1 when an avatar clears a target stage for the **first time** (determined via existing `WorldInformation`; once per avatar) |
| `STAGE_PLAY` | `HackAndSlash`, `HackAndSlashSweep` | + the number of actual plays / sweeps |
| `RECIPE_CRAFT` | `CombinationEquipment` | +1 per successful craft |

M2 (mid-stage arrivals) is expressed by targeting `STAGE_FIRST_CLEAR` at the stage just before the mid-point stage.

#### `WorldOpenSheet` — Opening Definitions

| Column | Description |
| --- | --- |
| `id` | Opening ID |
| `world_id` | Target world |
| `stage_end` | Once opened, stages up to this one can be entered |
| `prerequisite_open_id` | Prerequisite opening (first half → second half) |
| `min_block_index` | Earliest opening point |
| `fallback_block_index` | Latest opening point |
| `effective_delay_block` | Delay from confirmation to opening (default 32,400 blocks ≈ 3 days) |

#### `WorldOpenConditionSheet` — Opening Conditions

| Column | Description |
| --- | --- |
| `open_id` | `WorldOpenSheet.id` |
| `condition_group` | Same group = **AND**, different groups = **OR** |
| `counter_id` | `GlobalCounterSheet.id` |
| `threshold` | Threshold value |

An opening with no condition rows opens at `fallback_block_index` (equivalent to a fixed schedule).

### 2. New State

| Account | Key → Value |
| --- | --- |
| `GlobalCounter` | `counter_id` → cumulative value |
| `WorldOpen` | `open_id` → block at which the opening was confirmed |

### 3. Evaluation

- **Confirmation**: Within the action that increments an indicator, check whether that indicator crossed its threshold and whether the other conditions in the same group are met. If so, record the confirmation block in `WorldOpen`. Most actions only read and exit.
- **Whether an opening is applied** (computed at read time):

```
IsApplied(open, block) :=
    block >= open.fallback_block_index
 || ( WorldOpen.Contains(open.id)
      && block >= max(WorldOpen[open.id] + open.effective_delay_block,
                      open.min_block_index) )
```

- **Entry check**: The stage range check in `HackAndSlash` and `HackAndSlashSweep` is replaced with "the highest `stage_end` among currently applied openings." Worlds with no rows keep using the existing `WorldSheet` range.
- If no unconfirmed opening references an indicator, increments (writes) for that indicator are skipped.

### 4. Pre-deployed Data

For each new world, `WorldSheet` (final range), `WorldUnlockSheet`, `StageSheet`, `StageWaveSheet`, `CharacterSheet`, `WorldQuestSheet`, and equipment sheets are deployed in advance. Equipment recipes unlock under the existing `unlock_stage` rule, so they become available only after the stage opens and is cleared.

Items that require changing existing values (e.g., lowering sweep requirements for the previous range, raising World Boss baselines) are outside the scope of this structure and will continue to be patched at opening time.

### 5. Client

- Show locked state for unopened ranges, and the expected opening time once confirmed.
- Show the progress gauge and the latest opening point (visibility depends on the result of Q4).
- Resources and localization for pre-deployed ranges are included in a client build released before the pre-deployment patch.

## Backward Compatibility

- Worlds 1–10, Mimisbrunnr, and the already-open range of World 11 have no rows in the new sheets and behave exactly as before.
- If the new sheets do not yet exist on-chain, they are treated as empty, so code and sheet deployment can happen in any order.
- The World 10-specific auto-unlock branch is generalized to use `WorldUnlockSheet`, with regression tests guaranteeing identical results.
- Indicators only count actions performed after code deployment, so indicator targets are set to ranges no one has reached at deployment time.
- Because entry into unopened stages is rejected, a client build supporting this change will be set as the minimum required version.
- Query fields for indicator and opening state will be added to the headless node for third-party tools.

## Security Considerations

| Risk | Mitigation |
| --- | --- |
| Reaching headcount indicators early with multiple accounts | Reaching the end of the previous world is already very costly per account; plus `min_avatar_level` and the earliest opening point |
| Inflating count-based indicators through repetition by a few players | Combining them with headcount indicators via AND is recommended (to be reviewed alongside Q2) |
| Content never opening because thresholds are not met | Latest opening point is mandatory |
| Traffic spikes as thresholds approach | Adjust gauge visibility; grace period after confirmation |
| Pre-deployed data being visible early | On-chain data is publicly readable, so its contents will be officially announced at pre-deployment |
| Pre-deployed rows lost in later sheet patches | Generate patches from the live baseline and verify that row counts do not decrease |
| Determinism | Only block height and on-chain state are used; the 3-day grace period is far longer than any reorg depth |
