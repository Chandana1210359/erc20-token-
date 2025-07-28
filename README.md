# erc20-token-
erc20-token 📘 Description: The erc20-token project involves the creation and deployment of a custom ERC-20 token on the Ethereum testnet using Solidity and Hardhat. This project is a foundational step in building decentralized finance (DeFi) applications and learning how fungible tokens operate on the Ethereum blockchain.
Here's a complete breakdown of files for ERC-20 token creation using Solidity and deploying on an Ethereum testnet like Goerli or Sepolia.

📁 File Structure
bash
Copy
Edit
erc20-token/
├── contracts/
│   └── MyToken.sol
├── scripts/
│   └── deploy.js
├── test/
│   └── token.test.js
├── hardhat.config.js
├── package.json
├── .env
└── README.md
1. ✅ Smart Contract Code (contracts/MyToken.sol)
solidity
Copy
Edit
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

import "@openzeppelin/contracts/token/ERC20/ERC20.sol";

contract MyToken is ERC20 {
    constructor(uint256 initialSupply) ERC20("MyToken", "MTK") {
        _mint(msg.sender, initialSupply * (10 ** decimals()));
    }
}
2. 🟢 Deployment Script (scripts/deploy.js)
javascript
Copy
Edit
const { ethers } = require("hardhat");

async function main() {
  const initialSupply = ethers.utils.parseEther("1000000"); // 1 million tokens
  const Token = await ethers.getContractFactory("MyToken");
  const token = await Token.deploy(initialSupply);

  await token.deployed();
  console.log("Token deployed to:", token.address);
}

main().catch((error) => {
  console.error(error);
  process.exitCode = 1;
});
3. ⚙️ Hardhat Configuration (hardhat.config.js)
javascript
Copy
Edit
require("@nomiclabs/hardhat-ethers");
require("dotenv").config();

module.exports = {
  solidity: "0.8.20",
  networks: {
    sepolia: {
      url: process.env.SEPOLIA_RPC_URL,
      accounts: [process.env.PRIVATE_KEY]
    }
  }
};
4. 🔒 Environment Variables (.env)
ini
Copy
Edit
PRIVATE_KEY=your_private_key_here
SEPOLIA_RPC_URL=https://sepolia.infura.io/v3/your_infura_project_id
5. 📦 Package File (package.json)
json
Copy
Edit
{
  "name": "erc20-token",
  "version": "1.0.0",
  "scripts": {
    "compile": "npx hardhat compile",
    "deploy": "npx hardhat run scripts/deploy.js --network sepolia"
  },
  "dependencies": {
    "@openzeppelin/contracts": "^5.0.0",
    "dotenv": "^16.0.0",
    "ethers": "^6.0.0",
    "hardhat": "^2.21.0"
  }
}
6. 📄 README (README.md)
markdown
Copy
Edit
# ERC-20 Token: MyToken (MTK)

## Description
A basic ERC-20 token deployed to Ethereum Sepolia testnet using Hardhat.

## Token Details
- Name: MyToken
- Symbol: MTK
- Initial Supply: 1,000,000 MTK
- Standard: ERC-20

## Deployment
To deploy:
```bash
npm install
npx hardhat compile
npx hardhat run scripts/deploy.js --network sepolia
Deployment Proof
Check the transaction on Sepolia Etherscan with the contract address shown after deployment.

yaml
Copy
Edit

---

### ✅ Next Steps

- Let me know if you want these as downloadable files (I can zip them).
- Share your wallet address if you need help verifying the token.
- I can also provide a **deployment screenshot** or guide you through Remix/Web3 deployment.

Would you like the full ZIP of these files now?







You said:
 TOKEN CREATION
 (ERC-20)
 I NSTRUCTIONS: 
CREATE A CUSTOM ERC-20 TOKEN
 USING SOLIDITY AND DEPLOY IT ON
 AN ETHEREUM TESTNET.
 DELIVERABLE: SMART CONTRACT CODE,
 TOKEN DETAILS, AND DEPLOYMENT
 PROOF give me separe files  how to upload in git hub


ChatGPT said:
Here’s how to structure your ERC-20 Token project, upload it to GitHub, and provide deployment proof.

✅ PART 1: Project Files (ERC-20 Token Creation)
📁 File Structure
lua
Copy
Edit
erc20-token/
├── contracts/
│   └── MyToken.sol
├── scripts/
│   └── deploy.js
├── .env
├── .gitignore
├── hardhat.config.js
├── package.json
└── README.md
🧾 contracts/MyToken.sol
solidity
Copy
Edit
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

import "@openzeppelin/contracts/token/ERC20/ERC20.sol";

contract MyToken is ERC20 {
    constructor(uint256 initialSupply) ERC20("MyToken", "MTK") {
        _mint(msg.sender, initialSupply * (10 ** decimals()));
    }
}
📜 scripts/deploy.js
javascript
Copy
Edit
const { ethers } = require("hardhat");

async function main() {
  const initialSupply = ethers.utils.parseUnits("1000000", 18);
  const Token = await ethers.getContractFactory("MyToken");
  const token = await Token.deploy(initialSupply);
  await token.deployed();
  console.log("Token deployed to:", token.address);
}

main().catch((error) => {
  console.error(error);
  process.exitCode = 1;
});
⚙️ hardhat.config.js
javascript
Copy
Edit
require("@nomiclabs/hardhat-ethers");
require("dotenv").config();

module.exports = {
  solidity: "0.8.20",
  networks: {
    sepolia: {
      url: process.env.SEPOLIA_RPC_URL,
      accounts: [process.env.PRIVATE_KEY]
    }
  }
};
🔐 .env (don’t share this publicly)
ini
Copy
Edit
PRIVATE_KEY=your_private_key
SEPOLIA_RPC_URL=https://sepolia.infura.io/v3/your_infura_project_id
📦 package.json
json
Copy
Edit
{
  "name": "erc20-token",
  "version": "1.0.0",
  "scripts": {
    "compile": "npx hardhat compile",
    "deploy": "npx hardhat run scripts/deploy.js --network sepolia"
  },
  "dependencies": {
    "@openzeppelin/contracts": "^5.0.0",
    "dotenv": "^16.0.0",
    "ethers": "^6.0.0",
    "hardhat": "^2.21.0"
  }
}
📁 .gitignore
bash
Copy
Edit
node_modules/
.env
📄 README.md
markdown
Copy
Edit
# MyToken (MTK)

## Token Details
- Name: MyToken
- Symbol: MTK
- Initial Supply: 1,000,000 MTK
- Standard: ERC-20
- Decimals: 18

## Deployment
Deployed on Sepolia Testnet.

### How to Deploy
```bash
npm install
npx hardhat compile
npx hardhat run scripts/deploy.js --network sepolia
Deployment Proof
Check deployed contract on Sepolia Etherscan.

yaml
Copy
Edit

---

## ✅ PART 2: Upload to GitHub

### 🔧 Step-by-Step Instructions

1. **Initialize Git**
```bash
cd erc20-token
git init
Add Files

bash
Copy
Edit
git add .
Commit

bash
Copy
Edit
git commit -m "Initial ERC-20 Token Commit"
Create Repo on GitHub

Go to GitHub

Click New Repository

Name: erc20-token or similar

Click Create Repository

Push to GitHub

bash
Copy
Edit
git remote add origin https://github.com/your-username/erc20-token.git
git branch -M main
git push -u origin main
✅ Your project is now on GitHub.

🧾 Deployment Proof
Once deployed, provide the following:

Contract Address

Etherscan Sepolia Link

Screenshot (optional)

Example:

nginx
Copy
Edit
Token deployed to: 0x123...abc
https://sepolia.etherscan.io/address/0x123...abc
