# 🚀 Great Trading eXperience - GTX

## 🌎 Overview

GTX is a decentralized finance (DeFi) protocol designed to enable permissionless **spot trading**, with plans to expand into perpetual markets in the future. Addressing inefficiencies in Automated Market Makers (AMMs) and centralized exchanges, GTX provides an order book-based, permissionless trading experience that is **fair, efficient, and scalable**.

---

## ❌ Problems with Traditional AMMs

- **🔄 Inefficient Capital Utilization** – AMMs require deep liquidity to minimize slippage, leading to inefficient capital allocation.
- **💰 High Impermanent Loss** – Liquidity providers often suffer from impermanent loss due to volatile price movements.
- **📉 Price Manipulation** – AMMs are vulnerable to front-running and sandwich attacks, harming traders.
- **🚧 Restricted Market Listings** – Centralized exchanges limit listings, making it difficult for emerging assets to gain liquidity.

---

## ✅ GTX Solution for Spot Trading

GTX introduces a **Central Limit Order Book (CLOB)-based DEX** with:

1. **🌐 Decentralized Market Creation** – Anyone can list a spot trading pair without permission.
2. **📊 Efficient Order Book Trading** – CLOB enables traders to set limit orders and achieve fair price execution.
3. **🤖 AMM-Free Model** – Eliminates impermanent loss risks by relying on direct peer-to-peer trading.
4. **📡 Oracle-Free Spot Trading** – Uses an order book mechanism to ensure transparent and decentralized price discovery.

---

## 🔥 Key Features

- **💱 Spot Trading** – Fully decentralized CLOB-based exchange.
- **🚀 Permissionless Market Creation** – No gatekeepers—anyone can list a new market.
- **🔍 Fair and Transparent Pricing** – No reliance on external oracles for spot trades.
- **📈 Optimized Liquidity Utilization** – Capital-efficient trading mechanism compared to AMMs.
- **⚡ High-Frequency Trading Ready** – Supports traders placing orders with minimal delay.
- **🛑 No Liquidity Providers (LPs) Needed** – Orders are matched peer-to-peer, removing LP dependency.

---

## 🏗️ System Architecture

![CLOB DEX Architecture](../diagram.png)

The CLOB DEX system consists of four main components:
- **GTXRouter**: Entry point for all user interactions
- **PoolManager**: Manages trading pairs and pool deployments
- **OrderBook**: Handles order placement and matching using RB-Tree
- **BalanceManager**: Manages token deposits, withdrawals, and locks

## 🔄 How It Works

1. **👨‍💻 Traders** place buy/sell orders on the decentralized order book.
2. **📊 Order Matching** occurs through a fair and efficient matching engine.
3. **💰 Protocol** earns trading fees when orders are matched in the order book.
4. **🔄 Settlement** happens directly on-chain, ensuring security and transparency.

---

## 🏗️ More Details

### 💎 Core Features

#### 🔄 Advanced Order Types
- 📊 Limit Orders with precision pricing
- ⚡ Instant Market Orders
- 🎯 Smart order routing

#### ⚙️ High-Performance Engine
- 🏃‍♂️ O(log n) matching algorithm
- 📈 Price-time priority execution
- 🔍 Real-time order book updates
- 🔒 Atomic settlements

### 🏗️ Architecture Highlights

#### 🌳 Red-Black Tree Price Levels
- O(log n) operations for inserting/removing price levels
- Quick access to best bid/ask prices
- Ordered iteration through price levels

#### 📜 Order Queues
- Double-linked list for order storage at each price level
- FIFO (First In, First Out) execution within same price level
- Efficient order removal and updates

#### 🗃️ Data Storage Optimization
- **Order Packing**: Compact order storage using bit manipulation
  - Side (1 bytes) | Price (64 bytes) | OrderId (48 bytes)
- **Active Order Tracking**: Per-user order tracking using EnumerableSet
- **Price Level Management**: Automatic cleanup of empty price levels

### 🔑 Key Data Structures
```solidity
// Price Tree Mapping
mapping(Side => RBTree.Tree) private priceTrees;

// Order Queues at Each Price Level
mapping(Side => mapping(Price => OrderQueueLib.OrderQueue)) private orderQueues;

// User's Active Orders
mapping(address => EnumerableSet.UintSet) private activeUserOrders;
```

### 👀 View Functions
- Get best bid/ask prices
- View order queue status at any price level
- Retrieve user's active orders
- Get next best price levels with volumes

### ⛽ Gas Optimization Techniques
#### Efficient Storage
- Minimal storage operations
- Packed order data
- Optimized mappings

#### Smart Data Structures
- Red-Black Tree for price levels (O(log n) operations)
- Double-linked lists for order management
- EnumerableSet for tracking active orders

#### Memory Management
- Strategic use of memory vs storage
- Optimized array operations
- Efficient event emission

### 🔒 Security Features
#### Access Control
- Order cancellation restricted to order owner
- Reentrancy protection on all state-modifying functions

#### Input Validation
- Price and quantity validation
- Order existence checks
- Price level integrity checks

#### State Management
- Atomic operations
- Consistent state updates
- Automatic cleanup of empty states

---

## 🔑 Contract Addresses

### 📜 Deployed Contracts on RiseLabs Testnet

- **OrderBook Contract**
  - **Address:** `0x92D8387421fe5205051C82E4a6473E0aC5cc636b`
  - [View on Explorer](https://testnet-explorer.riselabs.xyz/address/0x92D8387421fe5205051C82E4a6473E0aC5cc636b)

- **BalanceManager Contract**
  - **Address:** `0xf997fBd9747841513d26d895072a7f35e5125cfc`
  - [View on Explorer](https://testnet-explorer.riselabs.xyz/address/0xf997fBd9747841513d26d895072a7f35e5125cfc)

- **PoolManager Contract**
  - **Address:** `0x2A61148905eA1cf87f352249DD92215C8eA0fdD5`
  - [View on Explorer](https://testnet-explorer.riselabs.xyz/address/0x2A61148905eA1cf87f352249DD92215C8eA0fdD5)

- **GTXRouter Contract**
  - **Address:** `0xe0eCBC144f924bD5bA7C7D9b373795EFA2F3589B`
  - [View on Explorer](https://testnet-explorer.riselabs.xyz/address/0xe0eCBC144f924bD5bA7C7D9b373795EFA2F3589B)

### 🪙 Mock Token Addresses

- **Mock USDC Contract**: [0x02950119C4CCD1993f7938A55B8Ab8384C3CcE4F](https://testnet-explorer.riselabs.xyz/address/0x02950119C4CCD1993f7938A55B8Ab8384C3CcE4F)
- **Mock WETH Contract**: [0xb2e9Eabb827b78e2aC66bE17327603778D117d18](https://testnet-explorer.riselabs.xyz/address/0xb2e9Eabb827b78e2aC66bE17327603778D117d18)
- **Mock WBTC Contract**: [0xc2CC2835219A55a27c5184EaAcD9b8fCceF00F85](https://testnet-explorer.riselabs.xyz/address/0xc2CC2835219A55a27c5184EaAcD9b8fCceF00F85)
- **Mock Chainlink Contract**: [0x24b1ca69816247Ef9666277714FADA8B1F2D901E](https://testnet-explorer.riselabs.xyz/address/0x24b1ca69816247Ef9666277714FADA8B1F2D901E)
- **Mock PEPE Contract**: [0x7FB2a815Fa88c2096960999EC8371BccDF147874](https://testnet-explorer.riselabs.xyz/address/0x7FB2a815Fa88c2096960999EC8371BccDF147874)

---

## 📜 License

GTX is open-source under the MIT License.

