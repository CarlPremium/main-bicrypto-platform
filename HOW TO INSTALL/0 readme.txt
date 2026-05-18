# Bicrypto Installation Guide

**WARNING: DO NOT CLICK ANY "UPDATE" BUTTONS IN THE ADMIN PANEL.**
Updating the platform through the admin panel will overwrite the activated addons and break the installation.

---

## 1. Database Setup & Initialization

Before running the application, you must set up the database using phpMyAdmin or a MySQL client.

1. Create a new MySQL database.
2. Import the `initial.sql` file provided in the root directory into your new database.

---

## 2. Unlocking Features (Manual Database Tweaks)

To activate the premium addons, you need to manually update certain tables in your database:

### A. Activate Extensions
* Table: `extensions`
* Action: Change the `status` column to `1` (instead of 0) for all extensions you want to use.

### B. Activate Blockchains (Solana, TON, Tron, etc.)
* Table: `blockchain`
* Action: Change the `status` column to `1` for the networks you wish to enable.

### C. Activate Exchanges (Binance, KuCoin, XT)
* Table: `exchange`
* Action: Change the `status` column to `1` for the respective exchanges.
* **Missing Exchanges Fix:** Run the following SQL query to insert missing exchange data:
```sql
INSERT INTO exchange (id, name, title, status, username, licenseStatus, version, productId, type) VALUES
(4, 'binanceus', 'Binance US', '0', NULL, '0', '1.0.0', '2816DB47', 'spot'),
(5, 'okx', 'OKX', '0', NULL, '0', '1.0.0', '34BDAB64', 'spot'),
(6, 'kraken', 'Kraken', '0', NULL, '0', '1.0.0', 'AB56F8DE', 'spot');
```

---

## 3. Environment & Build

1. Create your `.env` file by copying `.env.example` and fill in your database credentials.
2. Open your terminal in the root folder (e.g., `public_html`) and run the build updater:
   ```bash
   pnpm updator
   ```
   *Note: Wait until the build is completely finished. If you encounter permission errors, ensure your user has the correct read/write permissions for the `node_modules` folder.*

---

## 4. Post-Installation Configuration

### A. Ecosystem Vault (Web3 Wallets)
Every time the server restarts, the Ecosystem Vault must be unlocked. To avoid doing this manually:
1. Navigate to your admin panel: `yourwebsite.com/admin/ext/ecosystem`
2. Click on "Initiate Vault" and enter your mnemonic phrase.
3. **Best Practice:** Save this phrase in your `.env` file:
   `ENCRYPTION_KEY_PASSPHRASE="YOUR_PASSPHRASE"`
   This ensures the vault automatically unlocks upon server reboots.

### B. Exchange API Setup & Troubleshooting
If you experience deposit or withdrawal errors with Binance, KuCoin, or XT:
1. Ensure your API keys have Trades, Currencies, and Withdrawals explicitly enabled in the exchange's API settings.
2. Ensure you have whitelisted your server's IP address on the exchange.
3. **Important:** Do NOT use a US-based IP address for your VPS unless you are a US resident using Binance.US. Standard Binance, KuCoin, and XT will block connections from US IP addresses.

---
*Support the Developer: If you successfully install and profit from this setup, please consider supporting the original developers on CodeCanyon.*
