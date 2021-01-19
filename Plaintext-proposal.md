# Plaintext proposal

## First steps

Check out [first steps](README.md) before proceeding to further instructions.

## Deployment on mainnet

The ABI output of plaintext proposals factory is available at `./releases/plaintext_proposal_factory/plaintext-factory.json`.

```javascript
// ABI of the plaintext proposals factory
plaintextFactoryAbi = JSON.parse('ABI_HERE');
// Initialize plaintext proposal factory context
plaintextFactory = web3.ftm.contract(plaintextFactoryAbi).at('0xc9f5aa2c93ae9e89a77dc60e7e3cfff1234e4287');
// Create proposal, transfering proposal fee during this operation
// The call will revert if proposal verification fails
// Check out proposal parameters description at https://github.com/Fantom-foundation/fantom-govern/wiki/Proposal-parameters
// Check out parameters limitations at ./Fantom-proposal-templates.md . Plaintext proposal corresponds to template 1.
name = "Proposal name" // Proposal title. ASCII charecters only.
description = "Proposal description" // Proposal description. ASCII charecters only.
options =  ["Option 0", "Option 1", "Option 2"] // List of options to choose from. Do not add options which stand for disagreement with the proposal, because it should be expressed by downvoting every option. Each option has to be not longer than 32 charecters. ASCII charecters only. Cannot be empty.
minVotes = 550000000000000000 // Minimum voting turnout for the proposal to get resolved. The ratio has 18 decimals.
minAgreement = 550000000000000000 // Minimum acceptable ratio of agreement for an option. It's guaranteed not to win otherwise. The ratio has 18 decimals.
votingStartDelay = 3600 // voting starts after this period has passed since proposal creation (seconds)
minVotingDuration = 864000 // voting may end after this time period has passed since proposal voting start (seconds)
maxVotingDuration = 2592000 // voting ends after this time period has passed since proposal voting start (seconds)
proposalFee = web3.toWei('100', 'ftm');
plaintextFactory.create(name, description, options, minVotes, minAgreement, votingStartDelay, minVotingDuration, maxVotingDuration, {from: '0xAccount', value: proposalFee});
```
