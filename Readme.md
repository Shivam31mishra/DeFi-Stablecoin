# 🪙 Decentralized Stablecoin (DSC) Engine

![Solidity](https://img.shields.io/badge/Solidity-%23363636.svg?style=for-the-badge&logo=solidity&logoColor=white)
![Foundry](https://img.shields.io/badge/Foundry-white.svg?style=for-the-badge) 
![Chainlink](https://img.shields.io/badge/Chainlink-2A5ADA.svg?style=for-the-badge&logo=Chainlink&logoColor=white)

A robust, full-stack Decentralized Finance (DeFi) application featuring an algorithmic, exogenous, and heavily overcollateralized stablecoin. This project demonstrates core smart contract engineering, risk management, and local blockchain interactions.

> **🖥️ Frontend Repository:** https://github.com/BhupinderrSingh/DeFi-Frontend

## 📖 About the Project

The DSC Engine is a Collateralized Debt Position (CDP) system. It allows users to deposit crypto assets (WETH and WBTC) as collateral to mint a custom stablecoin (DSC) pegged to the US Dollar. 

To ensure the stablecoin never loses its peg, the system enforces strict overcollateralization. If the value of a user's collateral drops below the required threshold due to market volatility, the protocol incentivizes external liquidators to pay off the debt and claim the collateral at a discount, ensuring the system remains solvent.

### ✨ Key Features
* **Algorithmic Minting & Burning:** Strict access controls ensure DSC can only be minted when backed by sufficient collateral.
* **Chainlink Price Feeds:** Integrates decentralized oracles to fetch real-time USD conversion rates for WETH and WBTC.
* **Health Factor Mechanics:** A dynamic risk-assessment algorithm that continuously monitors user positions.
* **Incentivized Liquidations:** A self-healing protocol mechanism that rewards users for liquidating underwater positions.

## 🧮 The Core Math (Health Factor)

The stability of the entire protocol relies on the Health Factor. If a user's Health Factor drops below `1.0`, they are eligible for liquidation.

$$Health Factor = \frac{Total Collateral Value (in USD) \times Liquidation Threshold}{Total Debt Minted}$$

*Note: The current liquidation threshold is set to 50%, meaning collateral is only trusted at half its current market value to account for crypto volatility.*

## 🛠️ Tech Stack
* **Smart Contracts:** Solidity
* **Development Framework:** Foundry (Forge, Anvil, Cast)
* **Token Standards:** ERC-20 (OpenZeppelin)
* **Oracles:** Chainlink Data Feeds
* **UI/Frontend:** Next.js & Scaffold-ETH (Hosted in a separate repository)

## 🚀 Getting Started (Local Development)

### Prerequisites
You must have [Git](https://git-scm.com/) and [Foundry](https://getfoundry.sh/) installed on your machine.

### Installation
Clone the repository and install the required dependencies:
```bash
git clone [https://github.com/BhupinderrSingh/DeFi-Stablecoin.git](https://github.com/BhupinderrSingh/DeFi-Stablecoin.git)
cd DeFi-Stablecoin
make install
```

### Quickstart Command
This project includes a custom Makefile for streamlined execution. To build the contracts, spin up a local Anvil node, and deploy the engine in one go, simply run:
```bash
make deploy
```

### Manual Testing & Execution
To run the extensive Foundry test suite:
```bash
make test
```
To view test coverage:
```bash
make coverage
```

### 🔒 Security & Architecture
* DecentralizedStableCoin.sol: The ERC-20 token contract. It is governed by an Ownable modifier where the DSCEngine acts as the sole owner.

* DSCEngine.sol: The core logic contract handling deposits, withdrawals, minting, burning, and liquidations. It never holds funds directly but manages the internal accounting and security checks.

### 🤝 Acknowledgments
Developed as a comprehensive demonstration of advanced Web3 engineering, secure smart contract architecture, and full-stack dApp integration. 