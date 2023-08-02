# SORA Validator Payout Bot Development

## Problem we see

We are a supporter of Sora project and we currently run a validator. We also run validators in Kusama, Polkadot and Polkadex. Over the past few months, we have observed that the Sora's validator community is not healthy relative to other chains. Not a lot of validators compete to get into the active set, and many validators do not process payouts in a timely fashion and often batch them together with a long delay, if they process the payout at all.

The key issue we see is the lack of economic incentive. While staking rewards are paid in VALs, all the transaction fees incurred by validators are in XORs. Based on the current swap price in Polkaswap, it is not economically worthwhile for potential validators to join and for current validators to trigger payouts in a timely fashion.

## Request for proposal

Proposal Due Date: Oct 31, 2021

Proposal Overview: Make a Sora treasury supported payout bot to shift the burden of payout from validators.

Proposal Goal: 1) Improve Sora validators' economic incentive; 2) Make nominators happy because they will never miss a payout.

Scope of Work: 1) Develop an open-source bot script, 2) Host a server with cron jobs to trigger the payout script each era.

Current Roadblocks and Barriers to Success: None at this moment.

Evaluation Metrics and Criteria: 1) A developer can run the bot after following the instruction on README. 2) The payout script is triggered by the host server each era for all active Sora validators.

Submission Requirements: An open-source GitHub repo

Submission Method: An open-source GitHub repo

######################################

## Polkachu's Proposal

We (Polkachu) have been running validators in Kusama, Polkadot and Polkadex for a while. We have a payout bot to trigger rewards payouts after each era automatically. We are not running the bot in Sora currently for the reason stated above. Rather, we batch payouts in Sora after a few days of delay.

We propose to adapt our payout bot script for Sora so it triggers payout for all active Sora validators after each era. The proposal has two components:

1. Develop bot script: We will write the script in node.js with Polkadot API using Sora's custom types. When triggered, the bot will pay out rewards for all active Sora validators. The script will be open source so anyone can run it.

2. Maintain bot server: We will maintain a server with cron jobs that triggers payouts 4 times a day after each era. There is nothing to open source here, since it is just a server with a cron job.

## Why we qualify

We (Polkachu) have been running validators in Kusama, Polkadot, Polkadex and Sora. We have a payout bot to trigger rewards payouts for our own nodes. We are active in many blockchain communities. We open-source many of our projects on Github. For more information, please see:

- [Our website](https://polkachu.com)
- [Our GitHub repo](https://github.com/polkachu)

## Project Planning

### Phase 1: Develop bot script

- Development Timeline: 1 week.
- Deliverable: An open-sourced Github repo
- Success Criteria: A developer can run the bot after following the instruction on README
- Budget: 40 hours x $80/hour = $3,200. Payment will be in XOR. At $250 for each XOR, it is about 12.8 XORs.

## Phase 2: Maintain bot server

- Development Timeline: Negligible.
- Deliverable: A server that runs the bot maintained by Polkachu
- Success Criteria: Payouts are triggered after each era automatically
- Budget: No setup cost. On the monthly basis, Polkachu will submit a report for pre-payment that covers the server maintenance and payout transaction cost. The server maintenance is $150 (roughly two hours of engineering time each month plus cloud hosting). Payout transaction cost = transaction cost of batch payout for all 69 active validators x 4 batches per day x ~30 days per month.

## Other considerations

1. The two Phases of the project can be reviewed separately. It is perfectly fine if Sora team wants to run the bot themselves while Polkachu will only complete Phase 1
2. We think that it will be beneficial to the community if we mutually release a blog post on Medium and Twitter to announce this development once the project completes.
3. We have noticed that Sora use custom types extensively on the basis of Substrate. We might need some dev support from Sora team to make sure we get those types right.

Please feel free to reach out to us if you have questions: hello@polkachu.com
