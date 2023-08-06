# account-abstraction-workshop
Account Abstraction Workshop

# Components

## Bundler

Sends UserOperations as regular Ethereum transactions


## Smart Account

Has execute and eth handling methods. Has a single signer that can send requests through the EntryPoint

## SDK

Creates and sends UserOperation to a bundler

## Wallet

Implements the SDK


## Paymaster

Optionally pays for UserOperations

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
yarn run bundler --unsafe
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

