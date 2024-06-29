# ErrorHandling Smart Contract

A simple overview of the use and purpose of the ErrorHandling smart contract.

## Description

The `ErrorHandling` smart contract demonstrates various error handling mechanisms in Solidity, including `require`, `assert`, and `revert`. The contract includes basic functions for managing a balance, along with functions that intentionally trigger errors for demonstration purposes.

## Getting Started

### Installing

1. **Search Remix**: Go to [remix.ethereum.org](https://remix.ethereum.org/).
2. **Create a File**: Create a new file in Remix and name it `ErrorHandling.sol`.
3. **Copy the Contract Code**: Copy and paste the following Solidity contract code into the `ErrorHandling.sol` file:

```solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

contract ErrorHandling {

    uint256 public balance;

    constructor() {
        balance = 1000;
    }

    function deposit(uint256 amount) public {
        require(amount > 0, "Deposit amount must be greater than zero");
        balance += amount;
    }

    function withdraw(uint256 amount) public {
        require(amount <= balance, "Insufficient balance");
        balance -= amount;
    }

    function resetBalance(uint256 newBalance) public {
        assert(newBalance >= 0);
        balance = newBalance;
    }

    function triggerRevert() public pure {
        revert("This is a forced revert");
    }

    function validateAndRevert(uint256 value) public pure {
        require(value < 100, "Value must be less than 100");
        if (value > 50) {
            revert("Value is greater than 50, transaction reverted");
        }
    }
}
```

### Executing program

1. **Open Remix**:
   - Go to [remix.ethereum.org](https://remix.ethereum.org/).

2. **Create a New File**:
   - On the left panel, under the "File Explorer" tab, click on the "New File" button.
   - Name your file `ErrorHandling.sol`.

3. **Copy the Contract Code**:
   - Copy and paste the provided Solidity contract code into the new file `ErrorHandling.sol`.

4. **Compile the Contract**:
   - Click on the "Solidity Compiler" tab (looks like an "S" in the left sidebar).
   - Ensure the compiler version is set to 0.8.0.
   - Click the "Compile ErrorHandling.sol" button.

5. **Deploy the Contract**:
   - Click on the "Deploy & Run Transactions" tab (looks like a "rocket" in the left sidebar).
   - Ensure the "Environment" is set to "JavaScript VM (London)" for local testing.
   - Click the "Deploy" button.

6. **Interact with the Contract**:
   - After deploying, your contract will appear under "Deployed Contracts" in the same tab.
   - You can expand it to see the available functions and variables.

## Help

For common problems or issues, refer to the following:

- Ensure that you are using the correct Solidity compiler version (0.8.0).
- Verify that the contract code is correctly copied into Remix.
- If you encounter errors during deployment, check for any syntax errors in the contract code.

## Authors

Contributors' names and contact info:

- Ankit Verma

## License

This project is licensed under the MIT License - see the LICENSE.md file for details.
