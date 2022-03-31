# Gem Farm 💎
_by Gemworks_

Gem Farm is a collection of on-chain Solana programs for NFT ("gem" 💎) staking.

It consists of:

- Gem Bank 🏦 - responsible for storing NFTs, lets you configure which mints are/not allowed into the vaults
- Gem Farm 🧑‍🌾 - responsible for issuing rewards, lets you configure fixed/variable rates, lock up periods, fees, rarities & more

Gem Bank is used under the hood by Gem Farm.

# Official deployment 🚀

Both programs are now officially deployed across all 3 networks (mainnet, devnet, testnet):
```
bank: bankHHdqMuaaST4qQk6mkzxGeKPHWmqdgor6Gs8r88m
farm: farmL4xeBFVXJqtfxCzU9b28QACM7E2W2ctT6epAjvE
```

You can interact with them using this [front-end](https://www.gemfarm.gg/) (or build your own).

# Deploy your own version 🛠

- `git clone` the repo 
- Make sure you have `solana-cli` installed, keypair configured, and at least 10 sol on devnet beforehand
- Update path to your keypair in `Anchor.toml` that begins with `wallet =`
- Run `anchor build` to build the programs
- We need to update the program IDs:
    - Run `solana-keygen pubkey ./target/deploy/gem_bank-keypair.json` - insert the new Bank prog ID in the following locations:
        - `./Anchor.toml`
        - `./programs/gem_bank/src/lib.rs`
        - `./src/index.ts` (replace GEM_BANK_PROG_ID)
    - And `solana-keygen pubkey ./target/deploy/gem_farm-keypair.json` - insert the new Farm prog ID in the following locations:
        - `./Anchor.toml`
        - `./programs/gem_farm/src/lib.rs`
        - `./src/index.ts` (replace GEM_FARM_PROG_ID)
- Run `anchor build` to build one more time
- Run `anchor deploy --provider.cluster devnet` to deploy to devnet
- Now copy the IDLs into the apps:
    - `cp ./target/idl/gem_bank.json ./app/gem-bank/public`
    - `cp ./target/idl/gem_bank.json ./app/gem-farm/public`
    - `cp ./target/idl/gem_farm.json ./app/gem-farm/public`
- alternatively you can run the script I prepared `./scripts/cp_idl.sh`
- (!) IMPORTANT - run `yarn` inside the root of the repo
- finally start the apps!
    - eg cd into `app/gem-bank` and run yarn && yarn serve
- don't forget to open Chrome's console with `CMD+SHIFT+I` to get feedback from the app when you click buttons. It currently doesn't have a notifications system

Note that deploying your own version will cost you ~20 SOL.

# Debug cryptic errors ⚠️

If you get a cryptic error back that looks something like this: 
```
Transaction failed 0x1798
``` 
The steps to take are as follows:
- translate the 0x number into decimal (eg using [this](https://www.rapidtables.com/convert/number/hex-to-decimal.html?x=0x66)) - eg 0x1798 becomes 6040
- if the number is 6XXX, this is a custom error from the app. Go to errors.rs found [here](https://github.com/gemworks/gem-farm/blob/main/lib/gem_common/src/errors.rs) and find the error numbered 40 (the remainder of the decimal)
- any other number besides 6XXX means an anchor error - go [here](https://github.com/project-serum/anchor/blob/master/lang/src/error.rs) to decipher it

# Docs ✏️

Extensive documentation is available [here](https://docs.gemworks.gg/).

The answer you're looking for is probably there. Pls don't DM with random questions.

# License 🧾

MIT
Contribution: 2021-09-20 20:00

Contribution: 2021-09-20 20:01

Contribution: 2021-09-21 20:00

Contribution: 2021-09-21 20:01

Contribution: 2021-09-21 20:02

Contribution: 2021-09-21 20:03

Contribution: 2021-09-21 20:04

Contribution: 2021-09-21 20:05

Contribution: 2021-09-21 20:06

Contribution: 2021-09-21 20:07

Contribution: 2021-09-23 20:00

Contribution: 2021-09-23 20:01

Contribution: 2021-09-23 20:02

Contribution: 2021-09-23 20:03

Contribution: 2021-09-23 20:04

Contribution: 2021-09-23 20:05

Contribution: 2021-09-23 20:06

Contribution: 2021-09-23 20:07

Contribution: 2021-09-24 20:00

Contribution: 2021-09-29 20:00

Contribution: 2021-09-30 20:00

Contribution: 2021-09-30 20:01

Contribution: 2021-10-02 20:00

Contribution: 2021-10-02 20:01

Contribution: 2021-10-02 20:02

Contribution: 2021-10-02 20:03

Contribution: 2021-10-02 20:04

Contribution: 2021-10-03 20:00

Contribution: 2021-10-03 20:01

Contribution: 2021-10-06 20:00

Contribution: 2021-10-06 20:01

Contribution: 2021-10-06 20:02

Contribution: 2021-10-06 20:03

Contribution: 2021-10-06 20:04

Contribution: 2021-10-06 20:05

Contribution: 2021-10-06 20:06

Contribution: 2021-10-06 20:07

Contribution: 2021-10-06 20:08

Contribution: 2021-10-08 20:00

Contribution: 2021-10-08 20:01

Contribution: 2021-10-08 20:02

Contribution: 2021-10-08 20:03

Contribution: 2021-10-08 20:04

Contribution: 2021-10-08 20:05

Contribution: 2021-10-08 20:06

Contribution: 2021-10-08 20:07

Contribution: 2021-10-08 20:08

Contribution: 2021-10-10 20:00

Contribution: 2021-10-10 20:01

Contribution: 2021-10-10 20:02

Contribution: 2021-10-10 20:03

Contribution: 2021-10-10 20:04

Contribution: 2021-10-10 20:05

Contribution: 2021-10-10 20:06

Contribution: 2021-10-10 20:07

Contribution: 2021-10-10 20:08

Contribution: 2021-10-12 20:00

Contribution: 2021-10-12 20:01

Contribution: 2021-10-12 20:02

Contribution: 2021-10-12 20:03

Contribution: 2021-10-12 20:04

Contribution: 2021-10-13 20:00

Contribution: 2021-10-13 20:01

Contribution: 2021-10-14 20:00

Contribution: 2021-10-14 20:01

Contribution: 2021-10-14 20:02

Contribution: 2021-10-14 20:03

Contribution: 2021-10-16 20:00

Contribution: 2021-10-16 20:01

Contribution: 2021-10-16 20:02

Contribution: 2021-10-16 20:03

Contribution: 2021-10-16 20:04

Contribution: 2021-10-16 20:05

Contribution: 2021-10-16 20:06

Contribution: 2021-10-19 20:00

Contribution: 2021-10-19 20:01

