**Proposal Due Date**
15th October, 2021 20:00 CET

**Proposal Overview**
XSTs are the synthetic assets for the SORA ecosystem. Unlike other synths which are backed by some collateral token, XST is backed by the special liquidity source of XOR. XST may be created by burning XOR, which will mint XST through an oracle. A single XST(USD) is a claim for 1 US$ worth of XOR, and not a claim for actual US$.

**Proposal Goals (list with explanations where possible)**
As long as confidence is good, in tough market conditions people will burn XOR to get synthetic assets, instead of exiting XOR

**Scope of Work (describe the scope of work in as much detail as possible)**
See "Evaluation Metrics and Criteria" and "Submission Method"

**Current Roadblocks and Barriers to Success**
Don’t overcollateralize the creation of synthetic assets, but instead just socialize risks (and possible gains) across all XOR holders. This is justifiable because burning or locking up XOR reduces the circulating supply, which can lead to supply shortages and price of XOR going up

**Evaluation Metrics and Criteria (definition of done should be as clear as possible)**
Implement a stablecoin backed by XOR being creating a token called XST(USD), then create a XST(USD)-XOR liquidity source. This will be a special liquidity source where the price that buyers pay never deviates more than 1% higher or lower than the price of XOR-DAI. If the XST(USD)-XOR price goes lower than DAI-XOR, then when the user is buying, new XOR will be minted and used to fill the order (similar to the token bonding curve). When buying XST(USD) with XOR, then new XST(USD) can be minted/deminted when filling the orders, in order to maintain the peg.

**Submission Requirements**
Fulfill evalualuation metrics and criteria
Pull requests to paths outlined within Submission Method before due date

**Submission Method (which folder on GitHub to submit a proposal to)**

[https://github.com/sora-xor/rfps/tree/master/open_rfps](https://github.com/sora-xor/rfps/tree/master/open_rfps)

**Project Due Date**

1st December 2021 

**Development Fee**

666 XOR
