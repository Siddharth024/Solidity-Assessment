# MyToken Smart Contract

This repository contains the source code for the MyToken smart contract, which is an implementation of a simple ERC-20 like token on the Ethereum blockchain.

## Description

The MyToken contract allows users to mint and burn tokens. The contract keeps track of the total supply of tokens, and the balances of individual addresses.

## Requirements

The contract fulfills the following requirements:

1. *Public Variables:*
   - tokenName: A string representing the name of the token.
   - tokenAbbrv: A string representing the abbreviation of the token.
   - totalSupply: A uint representing the total supply of the token.

2. *Mapping:*
   - balances: A mapping of addresses to their respective token balances.

3. *Mint Function:*
   - Takes two parameters: an address and a value.
   - Increases the total supply by the given value.
   - Increases the balance of the given address by the given value.

4. *Burn Function:*
   - Takes two parameters: an address and a value.
   - Decreases the total supply by the given value.
   - Decreases the balance of the given address by the given value.
   - Ensures that the balance of the given address is greater than or equal to the value to be burned.

## Smart Contract Code

solidity
// SPDX-License-Identifier: MIT
pragma solidity 0.8.18;

contract MyToken {

    // Public variables here
    string public tokenName = "MIDAIMING";
    string public tokenAbbrv = "MID";
    uint public totalSupply = 0;

    // Mapping variable here
    mapping(address => uint) public balances;

    // Mint function
    function mint(address _address, uint _value) public {
        totalSupply += _value;
        balances[_address] += _value;
    }

    // Burn function
    function burn(address _address, uint _value) public {
        if (balances[_address] >= _value) {
            totalSupply -= _value;
            balances[_address] -= _value;
        }
    }
}


## Usage

### Deployment

To deploy the MyToken contract, follow these steps:

1. Install the necessary development tools, such as [Remix](https://remix.ethereum.org/), [Truffle](https://www.trufflesuite.com/truffle), or [Hardhat](https://hardhat.org/).

2. Copy the smart contract code into your development environment.

3. Compile the contract.

4. Deploy the contract to your preferred Ethereum network (e.g., Ethereum mainnet, Ropsten, Rinkeby).

### Interacting with the Contract

Once deployed, you can interact with the MyToken contract using the following functions:

- mint(address _address, uint _value): Mints _value tokens and assigns them to _address.

- burn(address _address, uint _value): Burns _value tokens from _address, reducing the total supply.

### Example

Here is an example of how you might interact with the contract:

solidity
// Assuming the contract is deployed and we have the contract address

// Minting 100 tokens to address 0x123...
myToken.mint(0x123, 100);

// Burning 50 tokens from address 0x123...
myToken.burn(0x123, 50);

