<div align="center">

# 🤖 Social Media Account Seller Bot

### What's Included · How It Works · Why This Bot

---

</div>

## 📦 What You Get

A **complete, production-ready Telegram bot** that automates the sale and delivery of social media accounts. Full source code, documentation, and lifetime support included.

### The Product

| Item | Description |
|------|-------------|
| **Complete Source Code** | Python 3.10+ codebase — clean, documented, modular |
| **Full Documentation** | Setup guide, configuration reference, Google Sheets guide, deployment docs |
| **Demo Data Tool** | One command to populate your Google Sheet with 12 realistic sample accounts |
| **Docker Support** | Dockerfile + docker-compose.yml for production deployment |
| **Termux Scripts** | One-click install + start scripts for running on Android |
| **Test Suite** | Database, search, and integration tests |

### What It Does

Your bot becomes an **automated account marketplace** on Telegram:

```
┌─────────────────────────────────────────────────────────────┐
│                                                             │
│   YOU                         YOUR CUSTOMERS                │
│   ───                         ──────────────                │
│                                                             │
│   Add accounts to             Browse → Search → Preview →   │
│   Google Sheet                Purchase → Receive Credentials│
│         │                              │                    │
│         ▼                              ▼                    │
│   ┌───────────┐              ┌───────────────┐              │
│   │  Google    │◄────────────│  Telegram Bot  │             │
│   │  Sheet     │  reads/     │  (automated)   │             │
│   │  (your     │  writes/    │                │             │
│   │  inventory)│  deletes    │  • Sells       │             │
│   └───────────┘              │  • Delivers    │             │
│                              │  • Collects $  │             │
│   Approve deposits           │  • Auto-deletes│             │
│   from /admin panel          └───────────────┘              │
│                                                             │
│   That's it.                 Everything else is automated.  │
│                                                             │
└─────────────────────────────────────────────────────────────┘
```

---

## 🌐 Supported Platforms

Sell accounts from **four platforms** in a single bot:

<table>
<tr>
<td width="25%" align="center">

### 🎵 TikTok

Fitness, Fashion, Gaming, Comedy, Music accounts with verified badges and follower counts

</td>
<td width="25%" align="center">

### 📘 Facebook

Business pages, Marketplace accounts, aged profiles with friends and community history

</td>
<td width="25%" align="center">

### 📸 Instagram

Niche accounts in Fitness, Travel, Food, Fashion with engagement metrics and verification

</td>
<td width="25%" align="center">

### 📧 Email

Gmail, Outlook, Hotmail — aged and PVA (Phone Verified Account) email addresses

</td>
</tr>
</table>

Each account includes: **Login Name**, **Password**, **Linked Email**, **Recovery Info**, **2FA Status**, and **2FA Secret Key/Backup Codes** — all securely hidden until purchase.

---

## 💰 How Payment Works

### Credits System

Customers buy credits, then spend them on accounts:

| Package | Credits | Price | Savings |
|---------|---------|-------|---------|
| 🟠 Trial | 5 | $5 | — |
| 🟡 Starter | 15 | $12 | 20% off |
| 🟢 Standard | 35 | $25 | 29% off |
| 🔵 Pro | 80 | $50 | 37% off |
| 💎 Premium | 200 | $99 | 50% off |
| 🔥 Enterprise | 500 | $199 | 60% off |

### Crypto Payments

Supports **4 cryptocurrencies** — you provide your own wallet addresses:

| Currency | Network |
|----------|---------|
| 💵 USDT | TRC-20 (Tron) |
| ₿ Bitcoin | BTC |
| ⟠ Ethereum | ERC-20 |
| ◎ Solana | SOL |

### Admin-Verified

Every deposit is **manually reviewed** by you before credits are added. No auto-crediting, no fraud risk. One-tap approve/reject buttons in the admin panel.

---

## 🔐 Security Built In

| Feature | What It Does |
|---------|-------------|
| **4-Tier Roles** | Guest → Member → VIP → Admin. Only invited users can buy. |
| **Invite Codes** | Generate single-use codes. Control who accesses your bot. |
| **Masked Previews** | Credentials shown as `🔒 ********` until purchase completes. |
| **Auto-Delete** | Credential messages self-destruct after 60 seconds. |
| **Double-Sell Prevention** | 3-layer locking prevents the same account from being sold twice. |
| **Credit Preservation** | User balances automatically backed up and restored during updates. |
| **Sheet Protection** | Credentials cleared from Google Sheet after sale + row deleted entirely. |
| **Atomic Transactions** | Database locks ensure credits are never lost during concurrent purchases. |

---

## 📊 Admin Dashboard

Everything you need to manage your business from Telegram:

### At a Glance

- **Total users** — By role (Guest, Member, VIP)
- **Active inventory** — Available accounts by platform
- **Revenue** — Total deposits, approved, pending
- **Sales** — Total purchases, average order value

### Key Admin Commands

```
/admin           → Full dashboard
/pending         → Approve/reject deposits (one-tap buttons)
/stats           → Real-time metrics
/addbalance      → Manually adjust user credits
/gencode member  → Generate invite codes
/broadcast       → Send announcement to all users
/export_payments → Download payment data as CSV
```

---

## 🚀 Getting Started

### Requirements

| Need | Free? |
|------|-------|
| Python 3.10+ | ✅ Free |
| Telegram account | ✅ Free |
| Google account (for Sheets) | ✅ Free |
| Crypto wallet addresses | ✅ Free |
| Google Cloud service account (for write-back) | ✅ Free |

### Setup Time: ~15 Minutes

```bash
1. Get bot token from @BotFather on Telegram
2. Create a Google Sheet with the required columns
3. Configure .env with your credentials
4. Run: python bot.py
5. Done — your bot is live!
```

> 📘 **A complete beginner's guide is included** — step-by-step with screenshots, covering every detail from creating the bot token to deploying on a VPS.

### Deployment Options

| Method | Best For |
|--------|---------|
| `python bot.py` | Testing on your PC |
| `docker compose up -d` | Production server |
| Termux on Android | Running from your phone |
| VPS + systemd | 24/7 operation ($3.50/month) |

---

## ❓ Frequently Asked Questions

<details>
<summary><strong>Do I need coding skills?</strong></summary>

No. The bot is ready to run. You just need to configure your `.env` file (copy-paste your bot token, sheet ID, and wallet addresses). A detailed setup guide walks you through every step.

</details>

<details>
<summary><strong>Can I customize the credit packages?</strong></summary>

Yes. The packages, prices, and crypto wallets are all configurable in the `.env` file and settings module. You own the source code — change anything you want.

</details>

<details>
<summary><strong>Can I add more platforms?</strong></summary>

Yes. The platform system is data-driven from the Google Sheet. Add a new `Platform` value (e.g., "Twitter") in the sheet and it will appear automatically. For custom emojis and enhanced formatting, the code is modular and easy to extend.

</details>

<details>
<summary><strong>What happens if my Google Sheet goes down?</strong></summary>

The bot caches all products locally with a configurable TTL (default: 5 minutes). It also creates a local CSV backup on every successful fetch. The bot continues working even if Google Sheets is temporarily unavailable.

</details>

<details>
<summary><strong>Can multiple admins manage the bot?</strong></summary>

Yes. Set `ADMIN_IDS=123456789,987654321` in your `.env` file. All listed users get full admin access.

</details>

<details>
<summary><strong>Will user credits be lost if the bot restarts?</strong></summary>

No. The bot automatically backs up all user data (balances, purchases, sold products) to a JSON file on every startup. If the database is ever lost, credits are automatically restored from the backup.

</details>

<details>
<summary><strong>Can I run this on my phone?</strong></summary>

Yes. Install Termux on Android, then run `bash scripts/install.sh` for one-command setup. Included scripts keep the bot running in the background.

</details>

<details>
<summary><strong>Do I get updates?</strong></summary>

Yes. Lifetime updates are included with your purchase. Bug fixes, new features, and improvements — all free.

</details>

---

## 💬 Purchase

<div align="center">

<br/>

### 💬 Contact [@Blackwolfisme](https://t.me/Blackwolfisme) on Telegram to purchase.

<br/>

| | |
|-|-|
| 💰 **Pricing** | **One-time fee** — no subscriptions, no recurring charges, no revenue share |
| 📦 **Includes** | Full source code + documentation + setup assistance + lifetime updates |
| ⏱ **Response** | Typically within a few hours |
| 🛡 **Support** | Setup help, bug fixes, and guidance included |

<br/>

### [📩 DM @Blackwolfisme on Telegram →](https://t.me/Blackwolfisme)

</div>
