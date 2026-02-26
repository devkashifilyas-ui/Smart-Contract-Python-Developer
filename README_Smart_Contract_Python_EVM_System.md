
# Smart Contract + Python EVM System

Production-grade EVM smart contract architecture with Python backend services for staking, token issuance, reward distribution, and Merkle-based airdrops.

---

## Overview

This repository demonstrates a full-stack Web3 system including:

- ERC20 Token Contract
- Staking Vault Contract
- Merkle Distributor (Airdrop) Contract
- Gas optimization and fuzz testing setup (Foundry)
- Python backend services using Web3.py
- FastAPI endpoints for orchestration
- Event indexing and monitoring architecture

This is structured as a production-ready foundation, not a toy demo.

---

## Architecture

### On-Chain Layer (Solidity)

Contracts:

1. Token.sol
2. StakingVault.sol
3. MerkleDistributor.sol

Key features:
- Stake / Unstake
- Reward calculation
- Claim rewards
- CEI (Checks-Effects-Interactions) pattern
- Custom errors
- Reentrancy protection
- Gas-efficient bitmap tracking

Testing Framework:
- Foundry (forge test, fuzz tests, gas snapshots)
- Reentrancy tests
- Invariant testing

---

### Off-Chain Layer (Python)

Services built with:

- Python
- Web3.py
- FastAPI
- PostgreSQL

Modules:

- merkle_service.py
  - CSV ingestion
  - Merkle tree generation
  - Proof generation
- event_indexer.py
  - WebSocket listener
  - On-chain event parsing
  - Idempotent database writes
- distribution_service.py
  - Automated reward distribution workflows
  - Monitoring and logging

Secrets are handled via environment variables or vault systems. No private keys stored in code.

---

## Gas Optimization

- forge snapshot analysis
- Storage packing
- Custom errors instead of require strings
- Efficient bitmap usage for airdrops
- Minimal state writes

---

## Security Design

- Reentrancy protection
- CEI pattern enforcement
- Custom errors for clarity
- Strict input validation
- Off-chain monitoring for anomaly detection

Designed for audit readiness.

---

## Deployment Flow

1. Deploy contracts to testnet
2. Verify on Etherscan
3. Run backend services
4. Configure environment variables
5. Begin indexing and monitoring
6. Promote to mainnet after validation

---

## Project Structure

contracts/
    Token.sol
    StakingVault.sol
    MerkleDistributor.sol

backend/
    merkle_service.py
    event_indexer.py
    distribution_service.py
    main.py

tests/
    StakingVault.t.sol
    MerkleDistributor.t.sol

---

## MVP Execution Plan

Week 1
- Contract architecture
- Full test coverage
- Testnet deployment

Week 2
- Python backend services
- Merkle generator
- Event indexing
- REST API integration

Week 3
- Integration hardening
- Gas optimization pass
- Deployment scripts
- Documentation and handoff

---

## Tech Stack

- Solidity
- Foundry
- Hardhat (optional deployment scripts)
- Python
- Web3.py
- FastAPI
- PostgreSQL
- AWS / Docker (deployment)

---

## Designed For

- Token issuance platforms
- Staking protocols
- Reward distribution systems
- Airdrop automation platforms
- Production-grade EVM infrastructure
