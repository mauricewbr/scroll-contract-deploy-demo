# Scroll Contract Deployment Demo

This is a Scaling Ethereum 2023 hackathon repository. The intention behind it was to get familiar with the Scroll documentation and deploy a trivial code sample. A Scroll [example](https://github.com/scroll-tech/scroll-contract-deploy-demo) has been used for educational purposes.

The following documentation belongs to the original example's README.


## Prerequisites

- Network setup: https://guide.scroll.io/user-guide/setup


## Deploy with Hardhat

1. If you haven't already, install [nodejs](https://nodejs.org/en/download/) and [yarn](https://classic.yarnpkg.com/lang/en/docs/install).
2. Run `yarn install` to install dependencies.
3. Create a `.env` file following the example `.env.example` in the root directory. Change `PRIVATE_KEY` to your own account private key in the `.env`.
4. Run `yarn compile` to compile the contract.
5. Run `yarn deploy:scrollTestnet` to deploy the contract on the Scroll Alpha Testnet.
6. Run `yarn test` for hardhat tests.


## Deploy with Foundry

1. Install Foundry.
    ```shell
    curl -L https://foundry.paradigm.xyz | bash
    foundryup
    ```
2. Build the project.
    ```
    forge build
    ```
3. Deploy the contract.
    ```
    forge create --rpc-url https://alpha-rpc.scroll.io/l2 \
      --value <lock_amount> \
      --constructor-args <unlock_time> \
      --private-key <your_private_key> \
      --legacy \
      contracts/Lock.sol:Lock
    ```
  - `<lock_amount>` is the amount of `ETH` to be locked in the contract. Try setting this to some small amount, like `0.0000001ether`.
  - `<unlock_time>` is the Unix timestamp after which the funds locked in the contract will become available for withdrawal. Try setting this to some Unix timestamp in the future, like `1696118400` (this Unix timestamp corresponds to October 1, 2023).
  
  For example:
  ```
  forge create --rpc-url https://alpha-rpc.scroll.io/l2 --value 0.00000000002ether --constructor-args 1696118400 --private-key 0xabc123abc123abc123abc123abc123abc123abc123abc123abc123abc123abc1 --legacy contracts/Lock.sol:Lock
  ```
  
## Support

Join our Discord: https://scroll.io/
