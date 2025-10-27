# Fund Me Smart Contract

This project demonstrates a decentralized funding contract built with Solidity and deployed using Foundry. It's designed to showcase key concepts in smart contract development, testing, and deployment.

## Table of Contents
- [Fund Me Smart Contract](#fund-me-smart-contract)
  - [Table of Contents](#table-of-contents)
  - [About The Project](#about-the-project)
  - [Features](#features)
  - [Technology Stack](#technology-stack)
  - [Getting Started](#getting-started)
    - [Prerequisites](#prerequisites)
    - [Installation](#installation)
  - [Usage](#usage)
    - [Building the Project](#building-the-project)
    - [Testing](#testing)
    - [Deployment](#deployment)
      - [Local Deployment](#local-deployment)
      - [Testnet Deployment](#testnet-deployment)
  - [Security Considerations](#security-considerations)
  - [Key Concepts Covered](#key-concepts-covered)
  - [Contributing](#contributing)
  - [License](#license)
  - [Contact](#contact)

## About The Project

The Fund Me project is a smart contract that allows users to send ETH to a contract owner. The contract has a minimum funding threshold of $50 USD (converted from ETH using real-time Chainlink price feeds). Only the contract owner can withdraw the funds.

This project is ideal for demonstrating Solidity development best practices, testing methodologies, and deployment strategies using Foundry.

## Features

- **Minimum Funding Threshold**: Users must send at least $50 USD worth of ETH to fund the contract
- **Chainlink Integration**: Uses Chainlink price feeds to convert ETH to USD in real-time
- **Owner Withdrawal**: Only the contract owner can withdraw all funds
- **Secure Withdrawal Patterns**: Implements both standard and gas-optimized withdrawal functions
- **Fallback and Receive Functions**: Handles direct ETH transfers to the contract
- **Comprehensive Testing**: Includes unit tests and integration tests

## Technology Stack

- [Solidity](https://soliditylang.org/) - Smart contract language
- [Foundry](https://getfoundry.sh/) - Ethereum development toolkit
  - Forge: Testing and building
  - Cast: CLI interactions
  - Anvil: Local Ethereum node
- [Chainlink](https://chain.link/) - Decentralized oracle network for price feeds

## Getting Started

### Prerequisites

1. Install Foundry:
   ```bash
   curl -L https://foundry.paradigm.xyz | bash
   foundryup
   ```

2. Install Git (if not already installed)

### Installation

1. Clone the repository:
   ```bash
   git clone https://github.com/your-username/foundry-fund-me.git
   cd foundry-fund-me
   ```

2. Install dependencies:
   ```bash
   forge install
   ```

## Usage

### Building the Project

```bash
forge build
```

### Testing

Run all tests:
```bash
forge test
```

Run tests with gas reports:
```bash
forge test --gas-report
```

### Deployment

#### Local Deployment

1. Start a local Ethereum node:
   ```bash
   anvil
   ```

2. Deploy the contract:
   ```bash
   forge script script/DeployFundMe.s.sol:DeployFundMe --rpc-url http://127.0.0.1:8545 --private-key 0xac0974bec39a17e36ba4a6b4d238ff944bacb478cbed5efcae784d7bf4f2ff80 --broadcast
   ```

#### Testnet Deployment

1. Set up environment variables in a `.env` file:
   ```env
   SEPOLIA_RPC_URL=https://sepolia.infura.io/v3/YOUR_INFURA_PROJECT_ID
   PRIVATE_KEY=your_wallet_private_key
   ETHERSCAN_API_KEY=your_etherscan_api_key
   ```

2. Deploy to Sepolia testnet:
   ```bash
   forge script script/DeployFundMe.s.sol:DeployFundMe --rpc-url $SEPOLIA_RPC_URL --private-key $PRIVATE_KEY --broadcast --verify --etherscan-api-key $ETHERSCAN_API_KEY
   ```
   Use keystore is best:
   ```bash
   forge script script/DeployFundMe.s.sol:DeployFundMe --rpc-url $SEPOLIA_RPC_URL --account xxx --sender xxx --broadcast --verify --etherscan-api-key $ETHERSCAN_API_KEY
   ```

## Security Considerations

- **Reentrancy Protection**: Withdrawal functions use the Checks-Effects-Interactions pattern
- **Access Control**: Only the contract owner can withdraw funds
- **Input Validation**: Minimum funding amount is enforced using Chainlink price feeds
- **Overflow Protection**: Solidity 0.8.x provides built-in overflow protection

## Key Concepts Covered

1. Solidity mappings and arrays
2. Immutable variables
3. Libraries and imports
4. Modifiers
5. Error handling with custom errors
6. Chainlink integration
7. Fallback and receive functions
8. Testing with Foundry
9. Scripting deployments
10. Gas optimization techniques

## Contributing

Contributions are what make the open source community such an amazing place to learn, inspire, and create. Any contributions you make are greatly appreciated.

1. Fork the Project
2. Create your Feature Branch (`git checkout -b feature/AmazingFeature`)
3. Commit your Changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the Branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

## License

Distributed under the MIT License. See `LICENSE` for more information.