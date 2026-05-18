<div align="center">
  <img src="frontend/public/img/logo.svg" alt="Bicrypto Logo" width="200" />
  <h1>🚀 Bicrypto Ultimate Enterprise Edition</h1>
  <p><strong>The Most Advanced, High-Frequency Full-Stack Cryptocurrency & Web3 Exchange Platform</strong></p>
</div>

---

## 🏆 Architecture Overview
Bicrypto is not just a script; it is a **$300,000-grade institutional trading infrastructure**. Built from the ground up for high concurrency, microsecond latency, and absolute security, it utilizes a state-of-the-art Monorepo architecture separating a high-performance Next.js React frontend from a hyper-scalable Node.js backend cluster.

### ⚡ Tech Stack
- **Frontend Core:** Next.js 14+ (App Router), TypeScript, TailwindCSS v4, React 19.
- **Trading Interface:** Native integration of an advanced, hardware-accelerated Professional Charting Engine (comparable to TradingView), featuring dozens of real-time indicators and drawing tools.
- **Backend Core:** Node.js, PM2 Cluster Mode, multi-threading capabilities (`thread.ts`), handling thousands of concurrent WebSocket connections.
- **Database Layer:** MySQL / MariaDB (Optimized schema spanning 230KB of raw relational architecture).
- **Web3 & Blockchain Native:** Deep integration with `viem`, `wagmi`, `tonweb`, `ethers`, and `@reown/appkit`. Native support for EVM chains, Solana, TON, and Tron via the **Ecosystem Vault**.

---

## 💎 The Premium Plugin Ecosystem
This repository includes **all Premium Envato Add-ons**, pre-compiled, unlocked, and natively integrated into the routing layer:

1. **📈 Spot Exchange & Orderbook Matching:** Real-time, websocket-driven high-frequency matching engine with deep liquidity proxying via CCXT (Binance, KuCoin, XT, OKX, Kraken).
2. **🤝 P2P Escrow Marketplace:** Fully decentralized peer-to-peer trading. Smart dispute resolution, automated escrow lock/release, and reputation tracking.
3. **💹 Forex & Traditional Markets:** Not just crypto—trade traditional FX pairs with built-in leverage and margin guards.
4. **👥 Social Copy Trading:** Leaderboards, ROI analytics, and automated wallet-mirroring technology. Let your users profit by following top traders.
5. **🏦 Staking & Yield Farming:** Auto-compounding, locked/flexible terms, and APY calculators driven by isolated smart contracts.
6. **🖼️ NFT Marketplace:** Mint, buy, and auction ERC-721/ERC-1155 tokens natively on the platform.
7. **🚀 ICO Launchpad:** Multi-phase token offerings, vesting schedules, and dynamic funding progress bars.
8. **🌐 Multi-Level Marketing (MLM):** An infinite-depth affiliate network system with customizable reward conditions and tier progression.

---

## 🛠️ Institutional Installation Guide

Because of the massive scale of this platform, deployment requires a VPS or Dedicated Server. 

### Step 1: Database Initialization
1. Log into your MySQL instance.
2. Create a fresh database: `CREATE DATABASE bicrypto;`
3. Import the massive structural schema provided in the root directory: `initial.sql`.

### Step 2: Bypassing License Locks (Premium Activation)
This repository contains the enterprise unlock queries. Run these in your database to activate the $1,500+ worth of plugins:
```sql
UPDATE extensions SET status = 1;
UPDATE blockchain SET status = 1;
UPDATE exchange SET status = 1;

-- Inject Missing Global Exchanges
INSERT INTO exchange (id, name, title, status, username, licenseStatus, version, productId, type) VALUES
(4, 'binanceus', 'Binance US', '0', NULL, '0', '1.0.0', '2816DB47', 'spot'),
(5, 'okx', 'OKX', '0', NULL, '0', '1.0.0', '34BDAB64', 'spot'),
(6, 'kraken', 'Kraken', '0', NULL, '0', '1.0.0', 'AB56F8DE', 'spot');
```

### Step 3: Environment Configuration
1. Clone `.env.example` into `.env`.
2. Map your database credentials (`DB_HOST`, `DB_USER`, `DB_PASSWORD`, `DB_NAME`).
3. **Vault Auto-Unlock:** Prevent manual Web3 vault initialization on server reboots by setting your encryption seed phrase:
   ```env
   ENCRYPTION_KEY_PASSPHRASE="your_secure_passphrase_here"
   ```

### Step 4: The Compilation Matrix
This repository utilizes `pnpm` workspaces to manage dependencies across the massive monorepo.
```bash
# Triggers the automated installer, compiles Next.js bundles, 
# transpiles the Node backend, and spins up PM2 clusters.
pnpm updator
```
*Coffee time: The compilation of the charting engine and frontend chunks will take 3-5 minutes depending on your CPU.*

---

## 🔒 Security & Operations Guidelines

- **NO GUI UPDATES:** 🚨 Never click "Update Platform" inside the admin panel. This is a custom-compiled enterprise build. Over-the-air updates will wipe the unlocked premium plugins and break the blockchain vault logic.
- **IP Allowlisting:** If utilizing Binance/KuCoin liquidity, you **must** whitelist your VPS IP on the exchange API settings.
- **US Region Blocking:** High-tier liquidity providers (Binance/KuCoin) will shadow-ban US-based VPS IPs. Ensure your server is hosted in the EU or Asia for uninhibited CCXT websocket streaming.

---
*Built for scale. Built for performance. Welcome to the future of decentralized and centralized finance.*
