# Getting started

# Concepts
  1. git : is a distributed version control system used for tracking changes during software development


  2. GitHub : is a web-based platform that provides hosting for software development projects using git.


  3. Foundry : a platform or ecosystem dedicated to facilitating the creation, deployment, and management of blockchain-based applications or smart contracts.

# Requirements
  1.  git : you'll know you did it right if you can run git --version and you see a responde like "git version x.x.x"

  2. foundry: you´ll know you did it right if you can run forge --version and you se a response like "forge version x.x.x"

# Quickstart

 ```
 git clone https://github.com/artuuro00/foundry-fund-me/blob/master/README.md 
 cd foundry-fund-me-f23
 forge build

 ```

# Usage 
1. Deploy 
   ```
   forge script script/DeployFundMe.s.sol
   ```
   
2. Testing
During this project we´ve made use of three different test folders
   1. Integration: tests how would the interaction  with the contract be if we call it through the bash
   2. Unit : test how the actual functions of the contract work
   3. Mocks : related to eth prices

This is all tested:
```
forge test
```
Or if you only want to run a function:
```
forge test -mt TestFuncionName
``` 
Or if you wann test it in a real testnet:
```
forge test --fork-url $SEPOLIA_RPC_URL
```
- To visualize Test Coverage
```
forge coverage
```

# Deployment to a testnet or mainnet
1. First of all its important to setup all the environment variables
     - .env file that contains $SEPOLIA_RPC_URL and $PRIVATE KEY
         $SEPOLIA_RPC_URL --> Alchemy
         $PRIVATE_KEY --> Metamask
         You can also import your ETHERSCAN_API_KEY if you wanty to verify your contract on Etherscan
     - Private key can be instead encrypted (--cast-wallet <Wallet_NAME>)
    ```
    cast wallet import your-account-name --interactive
    Enter private key:
    Enter password:

    ```
    To see ur wallet list:
    ```
    cast wallet list
    ```

2. Get testnet ETH --> faucets.chain.link
3. Deploy
```
forge script script/DeployFundMe.s.sol --rpc-url $SEPOLIA_RPC_URL --private-key $PRIVATE_KEY --broadcast --verify --etherscan-api-key $ETHERSCAN_API_KEY
```

- Scripts 
   During this project we've made use of three different scripts
     - DeployFundMe.s.sol : deploys FundMe contract 
     - HelperConfig.s.sol : necessary to find priceFeed in the network we're usin
     - Interactions.s.sol: to run instruccions  from the bash
- Estimate gas --> forge snapshot

