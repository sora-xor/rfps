## Due Date
May 2022

## Overview
[SubSquare](https://www.subsquare.io/) is a governance platform designed for substrate based blockchains. It scans the 
governance, normalize the on-chain data and provide interfaces for community users to go ahead with the governance
workflow by discussion, voting, proposing, etc. We propose to integrate SORA solo chain which we think will greatly help 
its governance workflow.

The advantage of subsquare compared to polkassembly and commonwealth include:
- More accurate on chain events monitor and extraction.
- More detailed timeline.
- Fast team response time.
- All in all, the UI/UX is better.
- We have plans to make it a web3 apps and decentralized, but it will be long termed work.
- OpenSquare other products support in high priority, including off-chai voting, bounties, paid QA, etc.

Please check features catalog doc [here](https://opensquare.feishu.cn/docs/doccnv8EGKC5QtegMnmHnNZcK5f) which includes 
the basic features and advantage of subsquare.

## Proposal goals
Enhance SORA solo chain's governance visualization and workflow.

## Scope of work
- Scan SORA solo chain governance data and save the normalized data to database.  
- SORA related fronted design and backend configuration.
- A restful server which will serve SORA identities which will be used by subsquare to show the identity.
- Deploy SORA subsquare implementation.

The basic features of this implementation will include:

- Democracy proposals/referendums visualization and discussion.
- Council/Technical committee motion visualization and discussion.
- Overview and discussions feature.

## Current roadblocks and barriers to success
- Not sure whether there are proper types which can works well with polkadot.js to decode all SORA blocks.
- Not implementation yet, we have to scan all the data to see whether SubSquare current code covers all the possible business.

## Evaluation Metrics and Criteria
- Users can register account on https://sora.subsquare.io.
- Users can create posts to have discussions about governance.
- Users can view history democracy public proposals and referendums.
- Users can view history Council/Technical committee motions.
- Democracy public proposals' authors can edit the post corresponding to the proposal.
- Council/Technical committee motion author can edit the corresponding motion post.
- Users can have discussions under the corresponding democracy proposals and motions.

## Submission requirements
We may need some technical help if there are errors with block scanning. It will depend on whether SORA works well with
the latest @polkadot/api.

## Submission Method
open_rfps

## Budge Amount

Generally our fund request include following items:

- Basic setup fee, $10k.
- Monthly maintenance fee $500 - $1000, including the server fee and labor fee for maintenance. The range may change when basic infrastructure and labor cost change in a limited scope.
- Customization fee which depends on the customized feature request from projects.

Request table for SORA:

| Items      | Budget | Note |  Cost  |
| ----------- | ----------- | ----------- | -----------    |
| Basic setup      | $10,000 |        | $10,000
| Monthly maintenance |  $500/month  | 05.2021 - 07.2022    | $1,500  |
| Total     |  |    |  $11,500   |  

The payment can be done with #XOR tokens with the in time conversion rate.
