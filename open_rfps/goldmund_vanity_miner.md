**Proposal Due Date**

September 14, 2021. 20:00 GMT+0

**Proposal Overview**

The Goldmund Vanity Miner utility lets you input a desired address pattern and outputs mined public key addresses that start with cnPATTERN 

Additionally it gives you the 12 word mnemonics for backup and portability purposes.

Today it's already possible to generate/mine vanity substrate addresses with the subkey utility but without the mnemonics for easy backup and portability here: 

https://github.com/paritytech/substrate/tree/013c1ee167354a08283fb69915fda56a62fee943/bin/utils/subkey

Or on the web here: https://polkadot.js.org/apps/?rpc=wss%3A%2F%2Fws.sora2.soramitsu.co.jp#/accounts/vanity

**Proposal Goals (list with explanations where possible)**

The SORA community has access to an open-source utility under Apache License 2.0 to mine for special public keys to their liking.

Executables are compiled for easy access and the compilation guides together with a simple wiki-page explaining their use is part of the deliverables.

**Scope of Work (describe the scope of work in as much detail as possible)**

Most work has been done already by writing a c-code wrapper and getting to know the Rust toolchain.

It's not really a big deal - which is why I wondered why it has been ommited from the subkey development in the first place.

I don't think it's enought to submit a pull request or issue to subkey vanity generator because this proposal also includes offline binaries with a guide.

The rest of the scope of work is outlined in this document. Specifically within "Evaluation Metrics and Criteria" and "Submission Method"

**Current Roadblocks and Barriers to Success**

I have developed a multithreaded c code wrapper "quick and dirty" that compiles into .bin binaries.
But it has to be ported to Rust for later use in WebAssembly Web, Apps (destop+mobile).
Also a proper documentation is important.

It's possible to do without the mnemonic today but it's too much for most users to install rust, subkey, ... 
Also not everyone wants to trust a polkadot.js.org online website access to generate their secret keys. 
Trusted offline binaries with SHA256 hashes to them, wiki guide, clear source code and compile guides are the way to go in my opinion.

I will have to learn Rust. But I don't see this as a roadblock.

I would need 2 weeks but it could be done faster for sure. 

I set the date to 14. September, such that there is time to vote on the proposal first and discuss if necessary.

**Evaluation Metrics and Criteria (definition of done should be as clear as possible)**

Rust crate / source code should be compilable into .exe and .bin by following the compile docs and the SHA256 hash should match.

Linux terminal or Windows cmd executables should output values in the following format: 

Public Key:   cn...
Private Key:  0x...
Seed:         bla1 bla2 bla3 ... bla12

And do so when called in the following way (example search string here is 'VAL' - note that the search string is limitted to start with one of R,S,T,U,V,W,X:

cmd:
.\goldmund.exe VAL \<ENTER\>

terminal:
.\goldmund.bin VAL \<ENTER\>

**Submission Requirements**

Fulfill evaluation metrics and criteria.

Pull requests to paths as outlined within Submission Method done before Due Date.

**Submission Method (which folder on GitHub to submit a proposal to)**

Scope of work includes 
- Rust crate / source code,
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
- Set string search-space start position at 4 instead of 3. (cn[R,S,T,U,V,W xor X]<start_here> instead of cn<start_here_with_R,S,T,U,V,W xor X>)
- Expand the search-space to the entire string (not just the beginning after cn<here> or cnX<here> or cn_FIXED_LENGTH_<here> but cn[_ANYWHERE_])
- More than 12 words (15, 18, 21, and 24)
