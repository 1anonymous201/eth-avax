# Error Handler Smart Contract

This project demonstrates the use of error handling in Solidity using assert, require, and revert statements.

## Description

The errorHandler smart contract allows you to set an age and then check if the age is at least 18 than you are eligible for voting. It includes three different functions (testAssert, testRequire, and testRevert) to demonstrate various error handling mechanisms in Solidity. Additionally, it uses console.log for debugging purposes with Hardhat.

## Getting Started

### Installing

* Clone the repository:
  bash
  git clone https://github.com/yourusername/error-handler.git
  
* Navigate to the project directory:
  bash
  cd error-handler
  
* Install the necessary dependencies:
  bash
  npm install
  

### Executing program

* Compile the smart contract:
  bash
  npx hardhat compile
  
* Deploy the smart contract:
  bash
  npx hardhat run scripts/deploy.js --network <network-name>
  
* Interact with the smart contract using Hardhat Console:
  bash
  npx hardhat console --network <network-name>
  
* Example commands in the Hardhat console:
```
 // Deploy the contract
const VotingEligibility = await ethers.getContractFactory("VotingEligibility");
const votingEligibility = await VotingEligibility.deploy();
await votingEligibility.deployed();

// Set age
await votingEligibility.setAge(25);

// Test assert
await votingEligibility.testAssert();

// Test require
await votingEligibility.testrequire();

// Test revert
await votingEligibility.testrevert();
```

## Smart Contract Code

solidity
```
// SPDX-License-Identifier: MIT
pragma solidity >=0.6.12 <0.9.0;

//import Hardhat console for debugging
import "hardhat/console.sol";

contract VotingEligibility {
  // Declare a public state variable of type uint to store the person's age
  uint public personAge;

  //Function to set the age, taking a uint as an argument
  function setAge(uint _age) public{
    personAge = _age;

    //log the new age setting action
    console.log("age set to:", _age);
    }
  // function using assert to check if personAge is at least 18
  function testAssert() public view {
    assert(personAge >= 18);
    // log if the assertion passes
    console.log("you are eliglible to vote.");
  }
  //function using require to check if personAge is at least 18
  function testrequire() public view {
    require(personAge >= 18, "you must be atleast 18 years old to vote.");
  // log if the requirement passes
  console.log("you are eligible to vote.");
  }
  //function using if-else nd revert to check if personAge is at least 18

  function testrevert() public view {
    if (personAge >= 18 ){
      //log if the condition passes
      console.log("you are eligible to vote. ");
    }
    else {
      //revert with an error message if the condition fails
      revert("you must be at least 18 years old to vote");
    }
  } 
}
```


## Help

For common problems or issues, ensure you have the correct version of Solidity and Hardhat installed. If issues persist, try the following command for more information:
bash
npx hardhat help


## Authors

Contributors names:

- Satya Prakash

## License

This project is licensed under the MIT License - see the LICENSE.md file for details.

