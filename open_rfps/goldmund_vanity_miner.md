**Proposal Due Date**

August 28th, 2021. 20:00 GMT+0

**Proposal Overview**

The Goldmund Vanity Miner utility lets you input a desired address pattern and outputs mined public key addresses that start with cnPATTERN 

Additionally it gives you the 12 word mnemonics for backup and portability purposes.

It's already possible to mine vanity substrate addresses but no mnemonics for easy backup and portability: 

https://github.com/paritytech/substrate/tree/013c1ee167354a08283fb69915fda56a62fee943/bin/utils/subkey

https://polkadot.js.org/apps/?rpc=wss%3A%2F%2Fws.sora2.soramitsu.co.jp#/accounts/vanity

And there is no compiled executables with documented compilation for easy sha256 verification for everyday community members.

**Proposal Goals (list with explanations where possible)**

The SORA community has access to an open-source utility under Apache License 2.0 to mine for special public keys to their liking.

Executables are compiled for easy access and the compilation guides together with a simple wiki-page explaining their use is part of the deliverables.

**Scope of Work (describe the scope of work in as much detail as possible)**

See "Evaluation Metrics and Criteria" and "Submission Method"

**Current Roadblocks and Barriers to Success**

I have developed a multithreaded c code wrapper "quick and dirty" that compiles into .bin binaries already.

It has to be ported and optimized for Rust for later use in WebAssembly Web, Apps (destop+mobile).

Proper user documentation is important for usability and trust. Most users are not able to install rust, subkey, ...

Trusted offline binaries with SHA256 hashes to them, wiki guide, rust source code and compile guides are the way to go.

**Evaluation Metrics and Criteria (definition of done should be as clear as possible)**

Rust crate / source code should be compilable into .exe and .bin by following the compile docs and the published SHA256 hash should match the binaries.

Linux terminal or Windows cmd executables should output values in the following format... 

Public Key:   cn...
Private Key:  0x...
Seed:         bla1 bla2 bla3 ... bla12

... when called in the following way:

EXAMPLE 1:

cmd:
.\goldmund.exe VAL \<ENTER\>


Public Key:   cnVAL...
Private Key:  0x...
Seed:         bla1 bla2 bla3 ... bla12

terminal:
.\goldmund.bin VAL \<ENTER\>


Public Key:   cnVAL...
Private Key:  0x...
Seed:         bla1 bla2 bla3 ... bla12

The search string 'VAL' has been chosen as one of two examples.

Note that the cn... address is limitted to start with one of the following characters after 'cn' R,S,T,U,V,W,X.

EXAMPLE 2: 

I am actually not entirely sure if the sample outputs are valid, because some characters appear less frequently than others.
The general idea is that if the string does not start with any of R,S,T,U,V,W,X then the first character after cn is treated as any of them.

cmd:
.\goldmund.exe CER \<ENTER\>

Public Key:   cnVCER...
Private Key:  0x...
Seed:         bla1 bla2 bla3 ... bla12

Public Key:   cnSCER...
Private Key:  0x...
Seed:         bla1 bla2 bla3 ... bla12

Public Key:   cnRCER...
Private Key:  0x...
Seed:         bla1 bla2 bla3 ... bla12

terminal:
.\goldmund.bin VAL \<ENTER\>


Public Key:   cnVAL...
Private Key:  0x...
Seed:         bla1 bla2 bla3 ... bla12


**Submission Requirements**

Fulfill evaluation metrics and criteria.

Pull requests to paths as outlined within Submission Method done before Due Date.

**Submission Method (which folder on GitHub to submit a proposal to)**

Scope of work includes 
- Rust crate, Rust source code,
- Windows (.exe) and Linux (.bin) command line exectuables, 
- their SHA256 hashes, 
- compile guides for Windows and Linux.

https://github.com/sora-xor/community-resources/goldmund-address-miner/bin/goldmund.exe

https://github.com/sora-xor/community-resources/goldmund-address-miner/bin/goldmund.bin

https://github.com/sora-xor/community-resources/goldmund-address-miner/bin/goldmund.exe.sha256.txt

https://github.com/sora-xor/community-resources/goldmund-address-miner/bin/goldmund.bin.sha256.txt

https://github.com/sora-xor/community-resources/goldmund-address-miner/doc/win/goldmund-win-compile-doc.md

https://github.com/sora-xor/community-resources/goldmund-address-miner/doc/lin/goldmund-lin-compile-doc.md

https://github.com/sora-xor/community-resources/goldmund-address-miner/src/win/

https://github.com/sora-xor/community-resources/goldmund-address-miner/src/lin/

https://github.com/sora-xor/community-resources/goldmund-address-miner/doc/wiki-how-to-use-goldmund-address-miner.md

Note that while out of scope at this stage these may be considered in future proposals or their maintainers may include it:
- WebAssembly for polkadot.js.org
- Integration into sora desktop
- Integration into Polkaswap Web
- Fearlesswallet integration
- Soralution integration (e.g. for merchants)
- Other substrate networks than sora
- Expansion with BTC, ETH, ... address miners

Also out of scope at this stage but somewhat in mind for next release or included if very easily implemented:

- Leatspeak search-range expansion flag
- Set string search-space start position
- Expand the search-space to the entire string
- More than 12 words (15, 18, 21, and 24)
  
**Project Due Date**

September 14th, 2021. 20:00 GMT+0

Or 2 weeks from the time at which proposal is accepted if that is after the 28th of August.
  
**Budget Amount**

   18 XOR
  
**Late Delivery Penalty**
  
Up to 3 days too late: 1 XOR
Up to 7 days too late: 3 XOR
Up to 14 days too late: 9 XOR
Up to 21 days too late: 15 XOR
Later than 21 days too late: 18 XOR
