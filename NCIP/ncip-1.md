---
NCIP: 1
Title: NCIP Purpose and Guidelines
Status: Active
Type: Ecosystem
Author: Edward Thomson <edward@planetariumhq.com.>, Kijun Seo <kijun@planetariumhq.com>, et al.
Created: 2021-02-26
---

# What is an NCIP?

NCIP stands for Nine Chronicles Improvement Proposal. An NCIP is a design document providing information to the Nine Chronicles community, or describing a new feature for Nine Chronicles software. An NCIP should aim to provide a concise technical specification of the feature and a rationale for the feature.

We intend NCIPs to be the primary mechanisms for proposing new features, for collecting community input on an issue, and for documenting the design decisions that have gone into Nine Chronicles. The NCIP author should make reasonable efforts to build consensus within the community and document dissenting opinions. Once NCIP is accepted, we will work together on creating a reference implementation.

Because the NCIPs are maintained as text files in a versioned repository, their revision history is the historical record of the feature proposal.

# NCIP Types

There are currently 3 kinds of NCIP:

- A **Core NCIP** describes any change that affects most or all Nine Chronicles implementations, such as a change to the network protocol, a new game feature, change in block or transaction validity rules, or any change or addition that affects the interoperability of applications built upon Nine Chronicles.
- An **Ecosystem NCIP** describes any change that may not directly impact the Nine Chronicles implementation, but still affects the wider community. This includes process surrounding Nine Chronicles development as well. Examples: building a bridge to other decentralized networks, changing the procedures, guidelines, decision-making process, changing the tools or environment used in Nine Chronicles development, or updating the grant program.
- An **Informational NCIP** describes a design issue, or provides general guidelines or information to the Nine Chronicles community, but does not propose a new feature. Informational NCIPs do not necessarily represent community consensus or recommendation, so users and implementers are free to ignore Informational NCIPs or follow their advice.

It is recommended that a single NCIP contains a single key proposal or new idea.

# NCIP Work Flow

## 1. Ideation and Discussion

Each potential NCIP must have a lead author — someone who writes the NCIP using the style and format described below, shepherds the discussions in the appropriate forums, and attempts to build community consensus around the idea. It is highly recommended that a single NCIP contain a single key proposal or new idea.

The lead author should first attempt to ascertain whether the idea can be implemented. Discussing ideas with the community and developers on [Discord](https://discord.com/invite/planetarium) is the best way to go about this. Vetting an idea publicly before going as far as writing a NCIP is meant to save both the potential author and the wider community time.

The NCIP process does not replace the Suggestions channels (#suggestions and #suggestions-voting). It is best to discuss and propose ideas there. Larger proposals can be made into NCIPs, but small enhancements or patches probably don't need to follow the NCIP process.

## 2. Draft

Once the lead author has asked the community as to whether an idea has any chance of acceptance, a draft NCIP should be presented on Discord's #proposals channel, which will be reviewed by the core devs from Planetarium and the Nine Chronicles community. The draft should be in the correct format with all of the basic necessary details.

Ideas which are accepted as a complete draft can then be published as an NCIP.

Drafts which are not accepted at this stage will be **withdrawn**.

## 3. Accepted

Once a NCIP has been **accepted**, the reference implementation must be completed. When the reference implementation is complete and accepted by the community, the status will be changed to "**Final**".

Creating a reference implementation will often require developer skills, but it does not need to be done by a Planetarium employee. [Nine Chronicles Software Grant Program](https://docs.nine-chronicles.com/grant) can also be utilized to finance the reference implementation. The code should be prepared as a pull request to the relevant code repository on GitHub.

### 3.1 Rejected

An NCIP can still be rejected. Perhaps after all is said and done it was not a good idea. It is still important to have a record of this fact.

## 4. Final

NCIPs marked as final have been **accepted** by the community and have an appropriate reference implementation. In addition, the work has been merged into the main code base of Nine Chronicles.

### 4.1 Replaced

An NCIP can also be superseded by a different NCIP, rendering the original obsolete. This is intended for Informational NCIPs, where version 2 of (e.g.) an API can replace version 1.

## Work Flow Diagram

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/9f97f9fe-53f6-415a-8ad5-3a118628e57c/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/9f97f9fe-53f6-415a-8ad5-3a118628e57c/Untitled.png)

Source: [BIP-1](https://github.com/bitcoin/bips/blob/master/bip-0001.mediawiki).

# What belongs in a successful NCIP?

Each NCIP should have the following parts:

- **Preamble** -- RFC 822 style headers containing meta-data about the NCIP, including the NCIP number, a short descriptive title, the names, and optionally the contact info for each author, etc.
- **Abstract** -- a short (~200 word) description of the issue being addressed.
- **Copyright**/public domain -- Each NCIP must either be explicitly labelled as placed in the public domain (see this NCIP as an example) or licensed under the Open Publication License.
- **Motivation** -- The motivation is critical for NCIPs that want to change the underlying protocol. It should clearly explain why the existing protocol specification is inadequate to address the problem that the NCIP solves.
- **Specification** -- The technical specification should describe the syntax and semantics of any new feature. The specification should be detailed enough to allow future competing, interoperable implementations of Nine Chronicles.
- **Rationale** -- The rationale fleshes out the specification by describing what motivated the design and why particular design decisions were made. It should describe alternate designs that were considered and related work, e.g. how the feature is supported in other games or protocols.
  - The rationale should provide evidence of consensus within the community and discuss important objections or concerns raised during discussion.
- **Backwards Compatibility** -- All NCIPs that introduce backwards incompatibilities must include a section describing these incompatibilities and their severity. The NCIP must explain how the author proposes to deal with these incompatibilities.
- **Reference Implementation** -- The reference implementation must be completed before any NCIP is given status "Final", but it need not be completed before the NCIP is accepted. It is better to finish the specification and rationale first and reach consensus on it before writing code.
  - The final implementation must include test code and documentation appropriate for the Nine Chronicles tech stack. Planetarium and the core devs can help with this!

# NCIP Formats and Templates

NCIPs should be written in [markdown](https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet) format. There is a template to follow:

```
NCIP: <NCIP number>
Title: <NCIP title>
Author: <list of authors' names and optionally, email address>
Status: <Draft | Active | Accepted | Deferred | Rejected | Withdrawn | Final | Superseded>
Type: < Core | Ecosystem | Informational >
Created: <date created on, in ISO 8601 (yyyy-mm-dd) format>
* Post-History: <dates of postings to Discord channel>
* Replaces: <NCIP number>
```

# NCIP Editors and Responsibilities

The current NCIP editors are:

- Kijun Seo (@kijun)
- JC Kim (@jckdotim)
- Swen Mun (@longfin)
- Yujeong Nam (@Namyujeong)
- Caesty (@caesty)
- Edward Thomson (@EdwardAThomson)

For each new NCIP that comes in, an editor does the following:

- Read the NCIP to check if it is ready: sound and complete. The ideas must make technical sense, even if they don’t seem likely to get to final status.
- The title should accurately describe the content.
- Check the NCIP for language (that it is clear enough), markup (GitHub-flavored Markdown), code style.

If the NCIP isn’t ready, the editor will send it back to the author for revision, with specific instructions.

Once the NCIP is ready for the repository, the NCIP editor will:

- Assign an NCIP number (generally the PR number or, if preferred by the author, the Issue # if there was discussion in the Issues section of this repository about this NCIP)
- Merge the corresponding pull request
- Send a message back to the NCIP author with the next step.

Many NCIPs are written and maintained by developers with write access to the Nine Chronicles codebase. The NCIP editors monitor NCIP changes, and correct make suggestions for structure, grammar, spelling, or markup mistakes.

The editors assist with administrative & editorial duties, but this is likely done in collaboration with the NCIP author.

# History

This document was derived from [Bitcoin’s BIP-0001](https://github.com/bitcoin/bips) written by Amir Taaki, and [Ethereum's EIP-1](https://eips.ethereum.org/EIPS/eip-1) written by Martin Becze, Hudson Jameson, et. al, which in turn were derived from [Python’s PEP-0001](https://www.python.org/dev/peps/). In some places text was simply copied and modified.

# Copyright

Copyright and related rights waived via [CC0](https://creativecommons.org/publicdomain/zero/1.0/).
