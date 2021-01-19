## First steps

### Attach to your node 
Attach to a running node. You may need to specify your specific configuration.

```
lachesis attach
```

### Loading the Governance

```js
abi = JSON.parse('GOVERNANCE_ABI_OUTPUT');
// Note: define variable sfcc (instead of sfc) to avoid clashing with the sfc namespace introduced in go-lachesis v0.7.0-rc1.
gov = web3.ftm.contract(abi).at("0x7c3b85a71e4fce1209a81d67f1af46b5a068770e");
```

The current Governance release is `0.0.1-rc2`. The ABI output available at `./releases/governance/gov-abi-0.0.1-rc2.json`.

### Checking loading Governance has worked

```js
// Sanity check
gov.proposalFee(); // if everything is all right, will return a non-zero value
```

### Unlocking account

```js
personal.unlockAccount(YOUR_ADDRESS, "password", 60);
```

## Governance contract operations

**Note**: All references to "self-voters" refer to "validators".

https://github.com/Fantom-foundation/fantom-govern/wiki/Governance-calls-reference
