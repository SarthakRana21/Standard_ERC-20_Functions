# Standard_ERC-20_Functions

If your contract is ERC-20-compliant, it would include the following standard methods:

- **name()**: Returns the name of the token (which you are testing in your example).
- **symbol()**: Returns the symbol of the token (e.g., "TM21").
- **decimals()**: Returns the number of decimals the token uses.
- **totalSupply()**: Returns the total supply of the token.
- **balanceOf(address)**: Returns the balance of the specified address.
- **transfer(to, amount)**: Transfers tokens from the caller to another address.
- **approve(spender, amount)**: Approves an address to spend tokens on behalf of the caller.
- **allowance(owner, spender)**: Returns the amount of tokens that the spender is allowed to transfer from the owner's balance.

## Example in Action

Here is an example of how these ERC-20 functions can be used:

```solidity
pragma solidity ^0.8.6;

import "@openzeppelin/contracts/token/ERC20/ERC20.sol";

contract MyToken is ERC20 {
    constructor(uint256 initialSupply) ERC20("MyToken", "MTK") {
        _mint(msg.sender, initialSupply);
    }
}

// Example usage:

// Deploy the token contract with an initial supply of 1000 tokens.
MyToken myToken = new MyToken(1000 * 10 ** 18);

// Get the name of the token
string memory tokenName = myToken.name(); // Returns "MyToken"

// Get the symbol of the token
string memory tokenSymbol = myToken.symbol(); // Returns "MTK"

// Get the decimals of the token
uint8 tokenDecimals = myToken.decimals(); // Returns 18

// Get the total supply of the token
uint256 totalSupply = myToken.totalSupply(); // Returns 1000 * 10 ** 18

// Get the balance of the deployer's address
uint256 balance = myToken.balanceOf(msg.sender); // Returns the deployer's balance

// Transfer tokens to another address
myToken.transfer(address(0x123...), 100 * 10 ** 18); // Transfers 100 tokens

// Approve a spender to transfer tokens on behalf of the caller
myToken.approve(address(0x456...), 50 * 10 ** 18); // Approves spender to transfer 50 tokens

// Check allowance for a spender
uint256 allowance = myToken.allowance(msg.sender, address(0x456...)); // Returns 50 tokens
```
If you wonder how to get all the functions for your contract? use this code snippet while running test:

```javascript
console.log("Contract functions: ", Object.keys(token.functions));
```
