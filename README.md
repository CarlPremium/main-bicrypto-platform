# Bicrypto - Enterprise Cryptocurrency Exchange Platform

Welcome to the Bicrypto Enterprise platform. This repository contains the complete, production-ready source code for a highly sophisticated, multi-featured cryptocurrency exchange platform built with **Next.js** (Frontend) and **Node.js/Express** (Backend).

## 🌟 Key Features
This platform includes all premium integrations natively:
- **Spot Trading & Orderbooks:** High-frequency websocket matching engine.
- **Web3 Ecosystem Vault:** Multi-chain wallet support (Solana, TON, Tron, EVM).
- **P2P Marketplace:** Peer-to-peer trading with escrow.
- **Forex & Copy Trading:** Trade traditional markets and mirror top traders.
- **Staking & Yield Farming:** Automated token staking pools.
- **NFT Marketplace & ICO Launchpad:** Buy, sell, and launch digital assets.
- **Multi-Level Marketing (MLM):** Built-in affiliate and referral systems.

---

## 🛠 Prerequisites
Before you begin, ensure your server meets the following requirements:
- **Node.js** (v18 or higher recommended)
- **pnpm** (Package manager, install via `npm install -g pnpm`)
- **MySQL / MariaDB** (For the main database)
- **PM2** (For process management, install via `npm install -g pm2`)

---

## 🚀 Installation & Setup Guide

### 1. Database Initialization
You must set up the database before starting the application services.
1. Log into your MySQL server (via CLI, phpMyAdmin, or your preferred client).
2. Create a new empty database: `CREATE DATABASE bicrypto;`
3. Import the `initial.sql` file located in the root directory into your new database. This file contains the complete schema and default configurations.

### 2. Environment Variables
1. Copy the `.env.example` file and rename it to `.env`.
2. Open the `.env` file and fill in your database credentials:
   ```env
   DB_HOST=localhost
   DB_USER=root
   DB_PASSWORD=your_password
   DB_NAME=bicrypto
   ```
3. *(Optional but Recommended)* To auto-unlock the Ecosystem Vault on server restart, add your vault passphrase:
   ```env
   ENCRYPTION_KEY_PASSPHRASE="your_secret_passphrase"
   ```

### 3. Unlock Premium Addons (Database Tweaks)
To activate the included premium plugins, execute the following SQL commands in your database:
- **Activate Extensions:** `UPDATE extensions SET status = 1;`
- **Activate Blockchains:** `UPDATE blockchain SET status = 1;`
- **Activate Exchanges:** `UPDATE exchange SET status = 1;`
- **Missing Exchanges Fix:** 
  ```sql
  INSERT INTO exchange (id, name, title, status, username, licenseStatus, version, productId, type) VALUES
  (4, 'binanceus', 'Binance US', '0', NULL, '0', '1.0.0', '2816DB47', 'spot'),
  (5, 'okx', 'OKX', '0', NULL, '0', '1.0.0', '34BDAB64', 'spot'),
  (6, 'kraken', 'Kraken', '0', NULL, '0', '1.0.0', 'AB56F8DE', 'spot');
  ```

### 4. Build and Run the Platform
Open your terminal in the project's root directory and run the automatic builder and updater script:

```bash
pnpm updator
```
*Note: This command will install all dependencies, build the Next.js frontend, compile the Node.js backend, and start the services using PM2. Please wait until the process completes entirely. It may take several minutes.*

---

## ⚠️ Important Warnings & Troubleshooting

> [!WARNING]
> **DO NOT CLICK ANY "UPDATE" BUTTONS IN THE ADMIN PANEL.**
> Triggering an update through the web admin panel will overwrite your activated addons and potentially break the installation.

> [!IMPORTANT]
> **Exchange API Connections**
> If you experience deposit or withdrawal errors with Binance, KuCoin, or XT:
> 1. Ensure your API keys have **Trades**, **Currencies**, and **Withdrawals** explicitly enabled.
> 2. Ensure you have **whitelisted your VPS IP address** on the exchange.
> 3. Do NOT use a US-based IP address for your VPS unless you are a US resident using Binance.US. Global exchanges block connections from US IP addresses.

> [!NOTE]
> **Ecosystem Vault Initialization**
> If you do not set the `ENCRYPTION_KEY_PASSPHRASE` in your `.env`, you must manually unlock the vault every time the server restarts by navigating to `yourwebsite.com/admin/ext/ecosystem` and entering your mnemonic phrase.
