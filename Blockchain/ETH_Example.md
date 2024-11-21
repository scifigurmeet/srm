# Building a Simple Voting System on Ethereum (Local Development)

## What We're Building
A basic voting system where:
- Each person can vote once
- Votes are permanent and transparent
- Anyone can check results
- Multiple proposals supported

## Setup Instructions

### 1. Install Required Software
```bash
# Install Node.js from nodejs.org first, then:
mkdir voting-system
cd voting-system
npm init -y
npm install --save-dev hardhat @nomicfoundation/hardhat-toolbox
npx hardhat init
```

### 2. Project Structure
```
voting-system/
├── contracts/          # Smart contracts
├── scripts/           # Deployment scripts
├── test/             # Test files
└── hardhat.config.js  # Configuration
```

### 3. Contract Code
Create `contracts/SimpleVoting.sol`:
```solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.20;

contract SimpleVoting {
    struct Proposal {
        string description;
        uint voteCount;
    }
    
    Proposal[] public proposals;
    mapping(address => bool) public hasVoted;
    event VoteCast(address voter, uint proposalId);

    constructor(string[] memory _proposalDescriptions) {
        for (uint i = 0; i < _proposalDescriptions.length; i++) {
            proposals.push(Proposal({
                description: _proposalDescriptions[i],
                voteCount: 0
            }));
        }
    }

    function vote(uint proposalId) public {
        require(proposalId < proposals.length, "Invalid proposal ID");
        require(!hasVoted[msg.sender], "Already voted");

        proposals[proposalId].voteCount++;
        hasVoted[msg.sender] = true;
        
        emit VoteCast(msg.sender, proposalId);
    }

    function getWinner() public view returns (uint, string memory, uint) {
        uint winningVoteCount = 0;
        uint winningProposal = 0;
        
        for (uint i = 0; i < proposals.length; i++) {
            if (proposals[i].voteCount > winningVoteCount) {
                winningVoteCount = proposals[i].voteCount;
                winningProposal = i;
            }
        }
        
        return (
            winningProposal,
            proposals[winningProposal].description,
            winningVoteCount
        );
    }
}
```

### 4. Test File
Create `test/SimpleVoting.test.js`:
```javascript
const { expect } = require("chai");

describe("SimpleVoting", function () {
  let voting;
  let owner;
  let addr1;
  let addr2;

  beforeEach(async function () {
    [owner, addr1, addr2] = await ethers.getSigners();
    
    const SimpleVoting = await ethers.getContractFactory("SimpleVoting");
    voting = await SimpleVoting.deploy(["Proposal A", "Proposal B"]);
    await voting.deployed();
  });

  it("Should allow voting and get winner", async function () {
    await voting.connect(addr1).vote(0);
    await voting.connect(addr2).vote(1);
    
    const [id, desc, count] = await voting.getWinner();
    expect(count).to.equal(1);
  });

  it("Should prevent double voting", async function () {
    await voting.connect(addr1).vote(0);
    await expect(
      voting.connect(addr1).vote(1)
    ).to.be.revertedWith("Already voted");
  });
});
```

### 5. Deploy Script
Create `scripts/deploy.js`:
```javascript
async function main() {
  const proposals = ["Proposal A", "Proposal B"];
  const SimpleVoting = await ethers.getContractFactory("SimpleVoting");
  const voting = await SimpleVoting.deploy(proposals);

  await voting.deployed();
  console.log("Voting contract deployed to:", voting.address);
}

main().catch((error) => {
  console.error(error);
  process.exitCode = 1;
});
```

## Understanding the Code

### Key Components

1. **Struct Proposal**
   - `description`: Name/details of the proposal
   - `voteCount`: Number of votes received

2. **State Variables**
   - `proposals[]`: Array storing all proposals
   - `hasVoted`: Maps addresses to voting status

3. **Functions**
   - `constructor`: Creates initial proposals
   - `vote`: Records a vote
   - `getWinner`: Returns winning proposal

### How It Works

1. **Deployment**
   - Contract deploys with list of proposals
   - Each proposal starts with 0 votes

2. **Voting Process**
   - User calls `vote` with proposal ID
   - Contract checks:
     - Proposal exists
     - User hasn't voted before
   - Updates vote count and user status

3. **Getting Results**
   - `getWinner` loops through proposals
   - Returns ID, description, and votes of winner

## Running Locally

1. Start local blockchain:
```bash
npx hardhat node
```

2. Run tests:
```bash
npx hardhat test
```

3. Deploy:
```bash
npx hardhat run scripts/deploy.js --network localhost
```

4. Interact (Hardhat Console):
```bash
npx hardhat console --network localhost

// Get contract
const SimpleVoting = await ethers.getContractFactory("SimpleVoting");
const voting = await SimpleVoting.deploy(["A", "B"]);

// Vote
await voting.vote(0);

// Check winner
const winner = await voting.getWinner();
console.log(winner);
```

## Security Considerations

1. **Immutability**
   - Votes cannot be changed
   - Results are permanent

2. **Transparency**
   - All votes are public
   - Results viewable by anyone

3. **Limitations**
   - No vote delegation
   - Simple majority wins
   - No vote weight system

## Next Steps

1. Add vote weights
2. Implement time limits
3. Add proposal creation
4. Enable vote delegation
