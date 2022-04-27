## Due Date
May 2022

## Overview
[SubSquare](https://www.subsquare.io/) is a governance platform designed for substrate based blockchains. It scans the 
governance, normalize the on-chain data and provide interfaces for community users to go ahead with the governance
workflow by discussion, voting, proposing, etc. We propose to integrate SORA solo chain which we think will greatly help 
its governance workflow.

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
- Overview and discussions feature

## Current roadblocks and barriers to success
None.

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
