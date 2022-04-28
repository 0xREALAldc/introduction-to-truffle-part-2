# introduction-to-truffle-part-2
Project to get familiarized with Ganache UI, Ganache CLI and truffle console

To run the project we can use the ganache in truffle console, Ganache UI or Ganache CLI.

## Truffle Console
Only run `truffle develop` and you will be provided with a local blockchain, but all in console mode.

As we will already be in the console, we can omit the `truffle` command and just run the line below to migrate the contracts to the blockchain:
```
migrate
```

## Ganache UI
You will need to download [Ganache](https://trufflesuite.com/ganache/). 

Then after oppening we will need to create a workspace, where you will be presented with a file picker where you can select the **truffle-config.js** file of the project.

After this, you'll be able to see in the visual UI in the tabs the blocks, transactions, contracts and so on.

To be able to migrate our contract to the Ganache UI, we also need to change some settings in your `truffle-config.js` file. 
We will add the section for the network, like this below: 
```
development: {
     host: "127.0.0.1",     // Localhost (default: none)
     port: 8545,            // Standard Ethereum port (default: none)
     network_id: "*",       // Any network (default: none)
    },
```
To **Migrate** the contracts using Ganache UI we will specify our network:
```
truffle migrate --network development
```

To interact with the contract, we will use the truffle console but in the **development** network that is used by Ganache UI
```
truffle console --network development
```

## Ganache CLI
Ganache CLI is the standalone version of the simulation blockchain built into truffle, it is for folks who are comfortable with the command line and desires full control of thier development blockchain.

To use it we will need to have **npm** and **node** intalled and also install **ganache** with the command below:
```
npm install ganache --global
```

To start the CLI we will use only the command `ganache` and it will provide us with a blockchain as the other options.

To migrate the contracts to the Ganache CLI blockchain is similar to the UI option, only we will need to change the **port** configuration in our **truffle-config.js** file to **8545** instead of **7545**.

After, we run the command below to migrate the contracts
```
truffle migrate --network development
```

## Interacting with the contract 

We will declare a variable with the instance of the contract that we want to interact
```
let storage = await SimpleStorage.deployed()
```

Then we can use the `storage` object to call the methods that the contract has, like the `set` 
```
storage.set(42)
```

To retrieve the value stored in the blockchain we can use the `get` method of the contract that was declared
```
(await storage.get()).toNumber()
```

The comands for the interaction with the contract is the same if you use **truffle develop**, **Ganache UI** or **Ganache CLI**.

All references to the Consensys Blockchain Bootcamp.
