---
NCIP: 15
Title: Usage based transaction limiting, and migrating from activation system
Status: Draft
Type: Core
Author: Swen Mun <swen@planetariumhq.com>, Gilhwan Cheong <gil@planetariumhq.com>, Libplanet Team <libplanet@planentariumhq.com> et al.
Created: 2023-06-23
---

# Abstract
This proposal introduces new metering system based on usages logically, for transaction execution, to encourage systemic approach about transaction limiting other than current identity-based activation system.
Furthermore, it also explains migration plans from current activation based system.

# Motivation
## Preventing abuses
The main motivation of this proposal is, preventing abuses on protocol-level systemically. 

Of course, it is technically possible to prevent this kind of abuse even with the activation system. however, current system does not fit the other mission of gradually reducing Planetarium's dependencies, and ironically,  there are concerns that doing the best at preventing abuse could lead to strengthening these dependencies.

## Seamless migration
At the same time, this proposal aims to leave the current experience in normal cases unchanged as much as possible. to this end, we are including proposals in a direction that seems more centralized in the short term, but in the long run we think it is more valuable to be able to handle access rights in a way that is transparent and known to all.

# Rationale

## Determining "abuse", on public & permission-less network
* The Nine Chronicles is designed to be a "permission-less" decentralized game where anyone can participate and play on the network. The concept of permission-less nature is considered an important attribute of decentralized networks, so we started by simply emulating it.
* However, this permission-less nature does not mean that anyone can join the network without any restrictions. In many blockchain networks, including Nine Chronicles, the blockchain is considered a type of database and if this database can be used without any constraints, it could be vulnerable to attacks that fill the database with meaningless data.
    * Additionally, if a game like Nine Chronicles generates in-game assets through gameplay, it isn't only a game design concern but also an economic issue for the entire ecosystem.
* Therefore, when we refer to a decentralized network as "permission-less," it means that it operates based on rules that define the permission to use the blockchain network, and anyone can inspect and utilize these rules.
    * A prominent example of such rules is the concept of gas in Ethereum. anyone can create an Ethereum account, but without preparing the gas fees to be provided to block creators, they cannot use the network.
    * In the case of Nine Chronicles, the network participation permission has been managed through "Activation Codes" (also known as "Invitation Codes").
* This can be seen as a kind of "selection" problem where we determine "which users/transactions are beneficial to the network." as mentioned earlier, decentralized networks do not completely avoid such "selection." in most cases, they incentivize the "selection" through economic motivations. the reason they are still considered decentralized networks is that they aim to decentralize the process of "selection" itself, rather than refusing to make any "selection" at all.

## Centralization and Incentive
* During the early stages of development, when the "Activation Code" was not even referred to as an "Invitation Code" but rather as an `ActivationCode`, Nine Chronicles and Libplanet took a cautious approach towards fee policies. The idea was that if someone can operate a network where even well-intentioned individuals don't receive fees, then it should be possible to establish such a system. 
* The consideration of "Activation Code" was primarily focused on controlling network usage in this context.
* However, fees serve as both a restriction on user participation and a means for those who make the selection to exert sufficient influence. Many fee systems are designed as incentives so that the users creating transactions are motivated to include their own transactions. If such influence is not taken into account at the protocol level, block creators may act altruistically in some cases, but they may also engage in selfish behavior in other cases.

## per Account vs per Transaction
* Even in public blockchain projects, it is not that there was no access to the account system instead of fees. A system such as [EOS](https://eos.io/) is a representative example. However, the number is absolutely small compared to the transaction-based approach, and there are not too many examples to refer to for decentralization.
* First of all, the accounts of Nine Chronicles itself can be considered as "generator" that determine the production of items or other in-game goods. Account-level asset creation is a natural direction for general games, but account activation (actual creation), locking, and unlocking methods must be considered, which requires implementation of complex dependencies in the protocol and is difficult to make flexible.
* Also, simple account-level access control itself does not guarantee any incentives to block producers. of course, we could design a separate incentive system for this, but in that case it would make sense to use those incentives to control access at the transaction level and handle accounts on top of it.

## About "fill-in"
* The proposed measurement, collection, and replacement of transaction usage in this document, as well as the replacement of the activation code, can significantly impact the overall ecosystem of Nine Chronicles as it changes the fundamental assumptions of the game.
    * Therefore, to minimize negative impacts, it is important to have a separate testnet and an ample testing period.
* However, at the same time, it may be necessary to go beyond testing at the testnet level, as it can have a significant impact on various aspects of the ecosystem. This is because testnets often lack the economic incentives of the mainnet, making it difficult to obtain sufficient information about the same changes from a design perspective.
* In the short term, this proposal suggests a more centralized "fill-in" approach that relies more on the Migrator. This is done to verify the fee pricing and collection model on the mainnet before proceeding to the next stage.

# Specification

## Concepts
### Gas & Gas Price
* **Gas** is logical units to measure action execution. 
    * Gas can be defined on policy per action.
    * Gas will be determined during action evaluation.
* **Gas Price** is tagged price by transaction signer. 
    * Gas Price represents the willing to pay of signers.
    * Gas Price can be any fungible asset values upon data type level.
    * Gas Price can be zero or null. in that case, no charges are deducted regardless of the amount of gas consumed.
    * Gas Price will be referred by validators while block proposal.

Basically, execution measuring and charging is similar to other public blockchain network, such as [Ethereum](https://ethereum.org/en/).

### Mead
* **Mead** is a new fungible token for transaction fee system.
* it has different lifecycle and economics per phases. (see also "Phases" section)
* During "fill-in" phase, Mead is simple fungible asset value and can be defined as below
    ```python
    {
        'decimalPlaces': b'\x12', 
        'minters': None, 
        'ticker': 'Mead'
    }
    ```

### Pledge, between Agent and Patron
**Pledge** system is introduced to mimic current free to play experience, based on transaction fee system. it can be considered as a sort of fee-delegation.

* **Agent** is Nine Chronicle accounts that receives Mead from **Patron**.
* **Patron** is also Nine Chronicle accounts that provides Mead to **Agent**.
    * Agent can be Patron for other player (after Validator Centric phase)
* **Pledge** is a sort of contract between Agent and Patron.
    * It's stored as chain state per Agent.
    * It contains detail specs for Mead providing.
* When Agent's Mead balance reaches threshold described its Pledge, configured amount of Mead will be transferred from Patron to Agent automatically.

### Migrator
* **Migrator** is a patron having special purpose.
    * As name suggests, it's be designed for "fill-in" phase migration only.
    * After Validator Centric phase, all Migrators will turn to normal patron.
* Migrator should contract *all* accounts in the network and provide Mead automatically until end of "fill-in" phase.

## Phases
### 1. "fill-in" (2023 Q3)
In "fill-in" phase, activation system will be replaced with transaction fee system, without any other economic changes.

* From this phase, previous activation checking will not be used in protocol level.
* In this phase, Mead will be created for Migrator only.
* All action expect transfer Mead uses 1 Gas.
    * To prevent accumulating Mead by non-Migrator account, transferring action uses 4 Gas (higher value than charge amount described in Pledge)

### 2. Validator Centric (2024 H1)
After confirming fee system works well, we should move the focus to its creation and distribution. its main purpose is, incentivize validators and delegators by protocol reward. 

* From this phase, every Mead should be created as block rewards, instead of manual minting.
    * To achieve, detailed token economics for Mead should be designed completely.
* Also, it should be defined that more detailed Gas usages instead of static values (i.e., 1 or 4).

### 3. Market Building (2024 H2)
In the long run, the fee-based limiting system is strongly dependent on the value of Mead. so we should creates buying demand and building channel for exchange so that validators and delegators can secure its value.

* Patrons (like portals or guilds) who supply Mead to Agents need to upgrade their Pledge so that they can obtain long-term benefits.
* Helping create a market by making exchanges between Mead and NCG easier is also matter.

## Migrations
### Current (Phase 0) → "fill-in"
* During "fill-in" phase, Migrator who will be responsible for the migration should be chosen.
* After choosing Migrator, the calculated maximum amount of Mead that can be used during the "fill-in" will be transferred to the Migrator.
    * Calculation: `4` (max gas usages) * `7200` (blocks per day) * `100` (transactions per block) * `365` (expected days for "fill-in")
* Previous activated accounts will be contracted with Migrator upon its Pledge.
    * For proceeding with the Pledge publicly, Migrator should provide APIs and compatible client implementation as public.
    * Pledge should be configured as providing `4` Mead, since current major mempool policy is allowing 4 transactions from one account per block.

### "fill-in" → Validator Centric
* To prevent confusing, all of previous Mead will be removed from system.
* Because Migrators can no longer receive Mead in a special way, they must delegate a sufficient amount of NCG to receive Mead through block rewards.

# Backward compatibility 
* This proposal requires additional actions for Pledge, and new currency for Mead. 
    * Therefore it requires hard-fork and every nodes in the network must be updated to apply this changes.
* Also, this proposal brings some changes for transaction data structure and semantics.
    * Every transaction should specifies `MaxGasPrice` field (`0x6c`, `'m'`) as `1 * Mead`, and `GasLimit` field(`0x6d`, '`l`') as `4` during "fill-in" phase.
        * Example with `MaxGasPrice` and `GasLimit` (using [bencodex-python][])
            ```python
            {
                # Signature
                b'S': b'0E\x02!\x00\xf5\xbeH\x80-\xb7\x1b\xad\xd7:\xf8\xb5\x9b\xe9\x10BESL\xed\x8a\xdc\x94Y\xad\x0c,\xb8\x85\x84\xc4\x02 B\x88\xd1\xe9\x10P:\xcc\xbf-D\xcer\xce\x05"\x15Sd`&H)\x05\x96\xf8\xd6o\xcc\xe0\x0e\x03',
                # Raw action value
                b'a': [
                    {
                        'type_id': 'create_avatar8',
                        'values': {
                            'ear': 0,
                            'hair': 0,
                            'id': b'Bs-\x81\x88\r\x0cG\x94G\x88~\xa0_\x96\xc0',
                            'index': 0,
                            'lens': 0,
                            'name': 'x1ng1',
                            'tail': 0
                        }
                    }
                ],
                # Genesis block hash
                b'g': b'E\x82%\r\r\xa3;\x06w\x9a\x84u\xd2\x83\xd5\xdd!\x0ch;\x9b\x99\x9dt\xd0?\xacOX\xfak\xce',
                # GasLimit
                b'l': 4,
                # MaxGasPrice (see also Mead section for the currency spec)
                b'm': [{'decimalPlaces': b'\x12', 'minters': None, 'ticker': 'Mead'},
                        1000000000000000000],
                # Nonce
                b'n': 1,
                # Public key
                b'p': b"\x04SL&\xd2\x9f &\xd0+c'V\x0c\xb83\x18\xa8\x05\x8e\x13\xad\xbb\x13\xcb_\xb7|i14\xcb\xc8\x08oi\x81\x11\xb3\xdd\x1b^(\x083\x8e\xe3\xb66\xc4\x1c\xf5\xa5\x17\x13\x92~/\x1c\x97\x87\xf8\x06\xb6\x8d",
                # Signer
                b's': b'\xd8\x18\xe4\t\xf1x\x8bB\xa7[\x80\xd7\xce\x90\xcblNC\\o',
                # Timestamp
                b't': '2023-06-22T12:28:55.484240Z',
                # Updated addresses
                b'u': []
            }
            ```
    * For sake of previous chain compatibility, `MaxGasPrice` and `GasLimit` fields are null-able and omittable.
        * But after applying this proposal, Any tx that doesn't have `MaxGasPrice` and `GasLimit`, will be ignored by validator.
* At least "fill-in" phase, every new account requires the Pledge with Migrator account to acquire Mead.
* Despite of sunsetting activation system, `ActivateAccount` can be submitted. (act as no-op).
* Even after fork, we don't have to keep validation codes for previous activation system since current canonical chain hadn't accepted inactivated user's transactions.

[bencodex-python]: https://github.com/planetarium/bencodex-python