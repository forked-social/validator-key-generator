# About this Repo

This repo contains a simple tool used to generate a validator's BLS public key and
voting authorization given a BIP 39 seed phrase and a forked-social public key.

The BIP 39 seed phrase is a seed phrase that will be used by a validator node to 
sign blocks for PoS consensus. This does not need to be the same seed phrase used
for your public key. You will supply this value as the `pos-validator-seed` flag 
when running your node. Note that the seed phrase must have NO BIP39 passphrase —
the tool (and the validator's BLS keystore) derives the key from the seed phrase
alone, so do not use a phrase that was generated with an extra passphrase.

The public key is the public key that will be used when registering your validator.
On this fork, public keys are FS1-encoded (54 characters) on fork mainnet, e.g.
`FS13vrbSsSRefiNeoJK5uHMKgCwzJJ3NMCFdEKpui7qPX4X7xSLSko`, or tFS-encoded
(54 characters) on fork testnet — not the upstream `BC1…`/`tBCK…` shapes.

## Registering your validator

The fork explorer at https://explorer.forked.social will host the validator
registration hub if/when it goes live. On this fork, registration can also be
automated end-to-end with the `backend/scripts/pos/validator_bootstrap` script,
which registers your validator against the fork network directly.

# Run
Use the command below and replace `<SEED_PHRASE>` and `<PUBLIC_KEY>` with your values.
```bash
go run main.go --bls-seed-phrase="<SEED_PHRASE>" --deso-public-key="<PUBLIC_KEY>"
```

### Example
```bash
go run main.go --bls-seed-phrase="category ignore around vibrant delay cargo apart truly rabbit blue master cash" --deso-public-key="FS13vrbSsSRefiNeoJK5uHMKgCwzJJ3NMCFdEKpui7qPX4X7xSLSko"
```
