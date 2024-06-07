# Creating a Token
This comprehensive guide empowers you to craft your own token on the Ethereum blockchain using Solidity, the dominant language for Ethereum smart contracts. Dive into the included Solidity code, deployment scripts, and detailed instructions to navigate the setup and deployment process for your unique token.

## Description
This project equips you to build a custom token on the Ethereum blockchain, from crafting the Solidity code to launching it on the network.  It delves into the core principles of smart contracts and token creation, empowering developers to design tokens for diverse use cases like ICOs, dApps, and other innovative blockchain ventures.

## Getting Started

### Executing program
You can use the online Solidity IDE Remix to run this program. Visit the Remix website at https://remix.ethereum.org/ to get started.

Click the "+" symbol in the left-hand sidebar to start a new file once you are on the Remix website. Save the file (MyToken.sol, for example) with the.sol extension. The code below should be copied and pasted into the file:

```solidity
// SPDX-License-Identifier: MIT
pragma solidity 0.8.18;

/*
       REQUIREMENTS
    1. Your contract will have public variables that store the details about your coin (Token Name, Token Abbrv., Total Supply)
    2. Your contract will have a mapping of addresses to balances (address => uint)
    3. You will have a mint function that takes two parameters: an address and a value. 
       The function then increases the total supply by that number and increases the balance 
       of the “sender” address by that amount
    4. Your contract will have a burn function, which works the opposite of the mint function, as it will destroy tokens. 
       It will take an address and value just like the mint functions. It will then deduct the value from the total supply 
       and from the balance of the “sender”.
    5. Lastly, your burn function should have conditionals to make sure the balance of "sender" is greater than or equal 
       to the amount that is supposed to be burned.
*/

contract MyToken {

    // public variables here 
    string public tokenName = "PARAS";
    string public tokenAbbrv = "PRS";
    uint public totalSupply = 0;

    // mapping variable here 
    mapping(address => uint) public balances;

    // mint function
    function mint (address _address, uint _value) public{
      totalSupply += _value;
      balances[_address] += _value;
    }

    // burn function
    function burn (address _address, uint _value) public{
      if (balances[_address] >= _value){
         totalSupply -= _value;
         balances[_address] -= _value;
         
      }
      
    }

}
```

Select the "Solidity Compiler" tab from the sidebar on the left to begin compiling the code. Click "Compile MyToken.sol" after ensuring that the "Compiler" option is set to "0.8.18" (or another compatible version).

Selecting the "Deploy & Run Transactions" tab from the left-hand sidebar will allow you to deploy the contract after the code has been compiled. Click the "Deploy" button after choosing the "MyToken" contract from the dropdown menu.

After the contract is deployed, you can call functions like balanceOf and transfer using Remix's deployed contract interface.

## Authors

Paras
[@Paras](https://parassaini8756@gmail.com)


## License

This project is licensed under the MIT License - see the LICENSE.md file for details
