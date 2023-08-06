# account-abstraction-workshop
Account Abstraction Workshop

# Components

## Bundler

Sends UserOperations as regular Ethereum transactions. Supports additional [ERC4337 RCP methods](https://eips.ethereum.org/EIPS/eip-4337#rpc-methods-eth-namespace).

- [Config](bundler/packages/bundler/localconfig/bundler.config.json)
- [BundleServer.handleMethod](bundler/packages/bundler/src/BundlerServer.ts#L155)
- [MempoolManager.addUserOp](bundler/packages/bundler/src/modules/MempoolManager.ts#L40)
- [BundleManager.createBundle](bundler/packages/bundler/src/modules/BundleManager.ts#L147)
- [ValidationManager.validateUserOp](bundler/packages/bundler/src/modules/ValidationManager.ts#L168)
- [BundleManager.sendBundle](bundler/packages/bundler/src/modules/BundleManager.ts#L78)
- [ReputationManager.hourlyCron](bundler/packages/bundler/src/modules/ReputationManager.ts#L67)


## Smart Contract Account

Has execute and eth handling methods. Has a single signer that can send requests through the EntryPoint

- [SimpleAccount](account-abstraction/contracts/samples/SimpleAccount.sol#L21)

## SDK

Creates and sends UserOperation to a bundler

- [BaseAccountAPI.createUnsignedUserOp](bundler/packages/sdk/src/BaseAccountAPI.ts#L232)
- [ERC4337EthersSigner.sendTransaction](bundler/packages/sdk/src/ERC4337EthersSigner.ts#L27)
- [HttpRpcClient.sendUserOpToBundler](bundler/packages/sdk/src/HttpRpcClient.ts#L41)
- [ERC4337EthersProvider.constructUserOpTransactionResponse](bundler/packages/sdk/src/ERC4337EthersProvider.ts#L92)

## Wallet

Implements the UI that uses the SDK to send a UserOperation to the bundler

- [Config](trampoline/src/exconfig.ts)
- [KeyringService.createUnsignedUserOp](trampoline/src/pages/Background/services/keyring.ts#L384)

## Paymaster

Pays for UserOperations (optional)

# Exercises

## Setup all components on your local environment

Start a hardhat node

```
cd bundler
yarn
yarn hardhat-node
```

Start a bundler

```
cd bundler
yarn
yarn preprocess
DEBUG=* yarn run bundler --unsafe
```

Deploy the EntryPoint and the SimpleAccountFactory

```
cd account-abstraction
yarn
yarn deploy --network dev
```

## Deploy a SimpleAccount

Fund the SmartAccount with ETH so that it can pay for its deployment

```
cd trampoline
# this is Hardhat's Account #1
cast send YOUR_SIMPLE_ACCOUNT_ADDRESS --value 1000000000000000000 --rpc-url http://127.0.0.1:8545/ --private-key 0x59c6995e998f97a5a0044966f0945389dc9e86dae88c7a8412f4603b6b78690d
yarn
yarn start
```

Deploy the account

Transfer some ETH to another address

## Deploy a Paymaster

```
```

## Create a SimpleAccount on Goerli

## Create a 2-out-of-3 multisig on Goerli

