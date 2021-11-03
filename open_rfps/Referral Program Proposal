**Proposal Due Date**
January 2022
**Proposal Overview**
Referral system that enables accounts to specify which account invited them.

**Proposal Goals (list with explanations where possible)**
Implement a system to encourage network use through referral rewards
From the 50% of network transaction fees intended to be burnt, 10% to be reserved
as referral rewards

**Scope of Work (describe the scope of work in as much detail as possible)**
An account that wants to be a referrer has to reserve (via the reserve extrinsic) some
balance of their account. An account that wants to set their referrer should call the
extrinsic set_referrer.
This extrinsic is free for the referral, but it uses the special balance of the referrer.
With the implementation of the functions:
reserve - to Transfer balance from the the account to the special account.
This balance can be used by referrals to pay the fee
with input parameters- balance: Balance
outputs- DispatchResultWithPostInfo
and
set_referrer- which Sets referrer to be their referrer if the account doesn’t have a referrer yet.
This extrinsic is paid by the special balance of the referrer if the referree doesn’t have a
referrer, otherwise the extrinsic fails and the fee is paid by the referree
with input parameters- referrer: T::AccountId
outputs-  DispatchResultWithPostInfo
Storage method is Referrers- which Returns the referrer of the referree
with input parameters- referree: T::AccountId
outputs Option<T::AccountId>

**Current Roadblocks and Barriers to Success**
No system implemented yet to establish referrer/referral status in an account

**Evaluation Metrics and Criteria (definition of done should be as clear as possible)**
When a referred account pays a fee, 10% of that goes to their referrer.

**Submission Requirements**
Fulfill evaluation metrics and criteria.
Pull requests to paths as outlined within Submission Method done before Due Date.

**Submission Method (which folder on GitHub to submit a proposal to)** [https://github.com/sora-xor/rfps](https://github.com/sora-xor/rfps)

**Project Due Date**

January 2022

**Budget amount**
120 XOR
