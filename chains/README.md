# Directory Layout

**We accept all blockchains which have 10+ independent validators.**

- Submit configs for mainnet or testnet , go to [nodexemperor/explorer.nodex.one/tree/master/chains/mainnet](https://github.com/nodexemperor/explorer.nodex.one/tree/master/chains/mainnet)

## Sample of mainnet config
- `quasar.json`
```json
{
    "chain_name": "quasar",
    "api": [
        {"provider": "kjnodes.com 🦄", "address": "https://quasar.api.kjnodes.com"},
        {"provider": "polkachu.com", "address": "https://quasar-api.polkachu.com"}
    ],
    "rpc": [
        {"provider": "kjnodes.com 🦄", "address": "https://quasar.rpc.kjnodes.com"},
        {"provider": "polkachu.com", "address": "https://quasar-rpc.polkachu.com"}
    ],
    "sdk_version": "0.45.16",
    "coin_type": "118",
    "min_tx_fee": "5000",
    "addr_prefix": "quasar",
    "logo": "/logos/quasar.png",
    "keplr_features": ["ibc-transfer", "ibc-go"],
    "theme_color": "#7a87f9",
    "assets": [{
        "base": "uqsr",
        "symbol": "QSR",
        "exponent": "6",
        "coingecko_id": "quasar-2",
        "logo": "/logos/quasar.png"
    }]
}

```

## Sample of testnet config
- `quasar-testnet.json`
```json
{
    "chain_name": "quasar-testnet",
    "registry_name": "quasart",
    "api": [
        {"provider": "kjnodes.com 🦄", "address": "https://quasar-testnet.api.kjnodes.com"},
        {"provider": "polkachu.com", "address": "https://quasar-testnet.rpc.kjnodes.com"}
    ],
    "rpc": [
        {"provider": "kjnodes.com 🦄", "address": "https://quasar-testnet.rpc.kjnodes.com"},
        {"provider": "polkachu.com", "address": "https://quasar-testnet-rpc.polkachu.com"}
    ],
    "sdk_version": "0.45.16",
    "coin_type": "118",
    "min_tx_fee": "5000",
    "addr_prefix": "quasar",
    "logo": "/logos/quasar.png",
    "keplr_features": ["ibc-transfer", "ibc-go"],
    "theme_color": "#7a87f9",
    "assets": [{
        "base": "uqsr",
        "symbol": "QSR",
        "exponent": "6",
        "coingecko_id": "quasar-2",
        "logo": "/logos/quasar.png"
    }]
}
```

- **chain_name** the name to identify the chain on ping.pub, would be better to use the same one as registry
- **api** the rest api endpoint.(make sure that CORS is enabled: `Allow-Control-Allow-Origin: *`)
- **rpc** the rpc endpoint, make sure that the port is added. rpc endpoint is only used for state sync. it's optional.
- **assets** Native Assets on blockchain. 

Endpoint providers will be listed in the "Popular" tab of the staking.

## Token Unit conversion

We have two methods to load token metadata for token unit conversion:

### Loading from a REST endpoint (recommended).
   
you can define the metadata in the `bank` -> `metadata` section of the blockchain's genesis file. if you don't define, the `[]` will return.

```json
{
  "name": "atom",
  "description": "The native staking token of the Cosmos Hub.",
  "denom_units": [
    {
      "denom": "uatom",
      "exponent": 0,
      "aliases": [
        "microatom"
      ],
    },
    {
      "denom": "matom",
      "exponent": 3,
      "aliases": [
        "milliatom"
      ]
    },
    {
      "denom": "atom",
      "exponent": 6,
    }
  ],
  "base": "uatom",
  "display": "atom",
}
```
you can see more details here:
https://github.com/cosmos/cosmos-sdk/blob/main/docs/architecture/adr-024-coin-metadata.md

### Loading from Cosmos Registry:

https://github.com/cosmos/chain-registry

## Test 

please add these check points in comments with your PR, and adding your test result by clicking the checkbox of each line
```
Test Result:
- [ ] Connect wallet, check if address is correct? 
- [ ] Transfer
- [ ] Delegate
- [ ] Redelegate
- [ ] Unbond
- [ ] withdraw Validator's Commission
- [ ] withdraw Rewards
```
Test is very important for us and our users. 
