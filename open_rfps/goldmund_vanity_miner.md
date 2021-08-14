**Proposal Due Date**

September 14, 2021. 20:00 GMT+0

**Proposal Overview**

Today it's possible to generate/mine vanity substrate addresses with the subkey utility here: 
https://github.com/paritytech/substrate/tree/013c1ee167354a08283fb69915fda56a62fee943/bin/utils/subkey
Or on the web here: https://polkadot.js.org/apps/?rpc=wss%3A%2F%2Fws.sora2.soramitsu.co.jp#/accounts/vanity
But it will only give you the public key + secret and you will not have the 12 mnemonic words for easy backup.

The Goldmund Vanity Miner utility lets you input a desired address pattern and gives you the 12 words to that account.

**Proposal Goals (list with explanations where possible)**



**Scope of Work (describe the scope of work in as much detail as possible)**




**Current Roadblocks and Barriers to Success**



**Evaluation Metrics and Criteria (definition of done should be as clear as possible)**

Calling executable from cmd in this way: goldmund.exe VAL <ENTER>
  
Should produce this output:
  



**Submission Requirements**



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

Note that while out of scope at this stage these may be considered in future proposals or their maintainers may include it:
- WebAssembly for polkadot.js.org
- Integration into sora desktop
- Integration into Polkaswap Web
- Fearlesswallet integration
- Soralution integration (e.g. for merchants)
- Other substrate networks than sora
- Expansion with BTC, ETH, ... address miners

Also out of scope at this stage but somewhat in mind for next release:
- Leatspeak
- Set string search-space start position
- Include flag for string search-space start position at cnX<this_position> instead of cn<this_position>
- Expand the search-space to the entire string (not just the beginning after cn<here> or cnX<here> or cn_FIXED_LENGTH_<here> but cn[_ANYWHERE_])
