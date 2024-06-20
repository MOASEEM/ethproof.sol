//Project Description

//Public Variables:

Define public variables to store the token name (tokenName), token abbreviation (tokenAbbrv), and the total supply of the token (totalSupply).

//Mapping for Balances:

Use a mapping to keep track of the balance of each address. This mapping will have the address as the key and the balance (an unsigned integer) as the value.

//Mint Function:

Create a mint function that takes two parameters: an address (_address) and a value (_value). This function will increase the totalSupply by the given value and also increase the balance of 
the specified address by the same value.


//Burn Function:

Implement a burn function that also takes two parameters: an address (_address) and a value (_value). This function will first check if the address has a balance greater than or equal to the 
value to be burned. If the check passes, it will decrease the totalSupply by the value and also decrease the balance of the specified address by the same value.

//Conditionals in Burn Function:

Ensure the burn function includes conditionals to prevent burning more tokens than the address owns. This is done using a require statement to check the balance before proceeding with the 
burn operation.






// SPDX-License-Identifier: MIT
pragma solidity ^0.8.26;

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
string public myTokenName="MO.ASIM";
string public myTokenAbbr="ASIM";
uint public totalSupply=0;
    // mapping variable here
mapping (address => uint) public balance;
    // mint function
function mint(address _address, uint _value) public
{
    totalSupply += _value;
    balance[_address] += _value;
}
    // burn function
function burn(address _address, uint _value) public
{
/* It first checks if the _address has a balance greater than or equal to _value to prevent underflow.
If the check passes, totalSupply is decreased by _value.
The balance of _address is decreased by _value.
*/
    if (balance[_address] >=_value){
    totalSupply -= _value;
    balance[_address] -= _value;
}
}
}
