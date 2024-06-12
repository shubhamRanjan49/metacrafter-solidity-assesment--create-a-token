
ETH-PROOF-Beginner-EVM-Course

## Description

This is a README file so that other can understand this code more clearly.
Requirements:-
The contract has public variables to store details about the token:
Token Name,
Token Abbreviation,
Total Supply.
The contract includes a mapping to keep track of the balance of each address.
The contract has a mint function that:
Increases the total supply by the specified value.
Increases the balance of the specified address by the specified value.
The contract has a burn function that:
akes an address and a value as parameters.
Decreases the total supply by the specified value.
Decreases the balance of the specified address by the specified value.
Ensures that the balance of the address is greater than or equal to the value to be burned.

## Getting Started

To run this program, you can use Remix, an online Solidity IDE. To get started, go to the Remix website at https://remix.ethereum.org/.
Once you are on the Remix website, create a new file by clicking on the "+" icon in the left-hand sidebar. Save the file with a .sol extension (e.g., MyToken.sol). Copy and paste the following code into the file:

### Executing program


```
// SPDX-License-Identifier: MIT
// it is a special identifier used in Solidity source files to specify the license under which the contract code is released.
pragma solidity 0.8.18;
//This pragma directive specifies the version of the Solidity compiler
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
contract candidateToken {
//Store public variables for coin details (Token Name, Token Abbrv., Total Supply).

    
    string public tokenName = "Arcana";
    string public tokenAbbrv = "trinity";
    uint public totalSupply = 0;

// Map addresses to balances (address => uint).


    mapping(address => uint) public balances;

    event Mint(address indexed to, uint value);
    event Burn(address indexed from, uint value);

//Implement mint and burn functions to adjust total supply and balances, with the burn function
//checking for sufficient balance before burning.
    
    function mint (address _address, uint _value) public{
        totalSupply += _value;
        balances[_address] += _value;
    }

    
     function burn (address _address, uint _value) public{
         if (balances[_address] >= _value){
        totalSupply -= _value;
        balances[_address] -= _value;
    }
     }
}


```
* To compile the code, click on the "Solidity Compiler" tab in the left-hand sidebar or you can simply click ctrl+S in windows as it is the shortcut for compiling this code or you can click cmd+S if you have mac os . Make sure the "Compiler" option is set to "0.8.18" (or another compatible version), and then click on the "Compile Mytoken.sol" button.
* Once the code is compiled, you can deploy the contract by clicking on the "Deploy & Run Transactions" tab in the left-hand sidebar. Select the "mytoken" contract from the dropdown menu, and then you have to put the values of tokenAbbrv , totaSupply and tokenName and then click on the "Deploy" button.





## License

This project is licensed under the [MIT] License.
