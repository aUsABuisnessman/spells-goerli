**:warning: THIS REPO IS NOW CONSIDERED DEPRECATED! :warning:**

Read more about it in this [post](https://forum.makerdao.com/t/public-announcement-goerli-testnet-deprecation-and-upcoming-changes/23962/2).

# spells-goerli

![Build Status](https://github.com/makerdao/spells-goerli/actions/workflows/.github/workflows/tests.yaml/badge.svg?branch=master)

Staging repo for MakerDAO's Goerli executive spells.

## Instructions

### Getting Started

```bash
$ git clone git@github.com:makerdao/spells-goerli.git
$ dapp update
```

### Build

```bash
$ make
```

### Test (DappTools without Optimizations)

Set `ETH_RPC_URL` to a Goerli node.

```bash
$ export ETH_RPC_URL=<Goerli URL>
$ make test
```

### Test (Forge without Optimizations)

#### Prerequisites
1. [Install](https://www.rust-lang.org/tools/install) Rust.
2. [Install](https://github.com/gakonst/foundry#forge) Forge.

#### Operation
Set `ETH_RPC_URL` to a Goerli node.

```bash
$ export ETH_RPC_URL=<Goerli URL>
$ make test-forge
```

### Deploy

Set `ETH_RPC_URL` to a Goerli node and ensure `ETH_GAS_LIMIT` is set to a high enough number to deploy the contract.

```bash
$ export ETH_RPC_URL=<Goerli URL>
$ export ETH_GAS_LIMIT=8000000
$ export ETH_GAS_PRICE=$(seth --to-wei 3 "gwei")
$ make deploy
```

### Cast to tenderly

1. Create Tenderly account (no trial period needed atm) https://dashboard.tenderly.co/register
    - Note down `TENDERLY_USER` and `TENDERLY_PROJECT` values
2. Create Tenderly access token https://dashboard.tenderly.co/account/authorization
    - Note down `TENDERLY_ACCESS_KEY` values
3. Export env vars specified above or create `scripts/cast-on-tenderly/.env` file with them
4. Execute `make cast-on-tenderly spell=0x...`, with the address of the spell that hasn't been casted yet
    - The execution should finish with `successfully casted`
5. Open the `publicly sharable transaction url` printed into the console (it should require no credentials)
