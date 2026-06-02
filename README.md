<div align="center">

# 🤖 Social Media Account Seller Bot

### Fully Automated Telegram Marketplace for Social Media Accounts

![Python](https://img.shields.io/badge/Python-3.10+-3776AB?style=for-the-badge&logo=python&logoColor=white)
![Telegram](https://img.shields.io/badge/Telegram-Bot-26A5E4?style=for-the-badge&logo=telegram&logoColor=white)
![Google Sheets](https://img.shields.io/badge/Google_Sheets-Inventory-34A853?style=for-the-badge&logo=googlesheets&logoColor=white)
![Crypto](https://img.shields.io/badge/Crypto-Payments-F7931A?style=for-the-badge&logo=bitcoin&logoColor=white)

<br/>

**A production-ready Telegram bot for selling social media accounts across TikTok, Facebook, Instagram, and Email — with crypto payments, Google Sheets inventory, auto-delivery, and a full admin dashboard.**

<br/>

| 🎵 TikTok | 📘 Facebook | 📸 Instagram | 📧 Email |
|:---------:|:-----------:|:------------:|:--------:|
| ✅ | ✅ | ✅ | ✅ |

<br/>

### 💬 [Purchase on Telegram → @Blackwolfisme](https://t.me/Blackwolfisme)

**One-time fee · No subscriptions · No revenue share · Lifetime updates**

---

</div>

## ⚡ What Is This?

A **complete, ready-to-deploy Telegram bot** that automates the selling and delivery of social media accounts. Your customers interact with a polished Telegram interface to browse, search, purchase, and receive account credentials — all automatically.

**You provide the accounts → The bot handles everything else.**

```
Customer Journey:
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

  /start → /categories → /getdata ACC001 → /buy ACC001
     ↓          ↓              ↓                ↓
  Welcome    Browse by      Enhanced         Confirm →
  + Menu     Platform       Preview          Deduct Credits →
             (TikTok,     (hidden fields     Deliver Credentials →
             Facebook,     as 🔒 ********)   Auto-Delete (60s) →
             Instagram,                      Mark SOLD in Sheet →
             Email)                          Delete Row from Sheet
```

---

## 🏗 Architecture

```
┌──────────────┐     ┌──────────────┐     ┌──────────────┐
│   Telegram   │◄───►│   Bot Core   │◄───►│   Database   │
│   (Users)    │     │  (aiogram 3) │     │   (SQLite)   │
└──────────────┘     └──────┬───────┘     └──────────────┘
                            │
                     ┌──────┴───────┐
                     │ Google Sheets│
                     │  (gspread)   │
                     └──────────────┘
                       Read + Write
```

- **aiogram 3.x** — Async Telegram bot framework
- **SQLite (WAL)** — Users, balances, purchases, transactions
- **Google Sheets** — Product inventory (read via CSV, write via service account)
- **gspread** — Marks items sold, clears credentials, deletes rows after purchase

---

## ✨ Key Features

| Category | Feature |
|----------|---------|
| 🏪 **Marketplace** | 4 platforms · category browsing · paginated listings · platform-specific emojis |
| 🔍 **Search** | 9-filter builder · natural language `/quick` search · search history |
| 💰 **Payments** | 6 credit packages ($5–$199) · 4 crypto methods (USDT, BTC, ETH, SOL) |
| 🛒 **Purchase** | Auto-delivery · credential auto-delete · re-download anytime · double-sell prevention |
| 📊 **Google Sheets** | Live inventory · auto-mark SOLD · clear credentials · delete rows · demo data tool |
| 🔐 **Security** | 4-tier roles · invite codes · atomic locks · masked previews · auto-backup credits |
| 👤 **Admin** | Dashboard · deposit approve/reject · user management · broadcast · CSV exports |
| 🛡 **Reliability** | Credit preservation · auto-restore from backup · session conflict resolution · local CSV fallback |

> 📖 **Full feature breakdown →** [FEATURES.md](FEATURES.md)

---

## 📸 How It Works

### For Buyers

```
1. /start              → Welcome screen with balance
2. /categories         → Browse TikTok, Facebook, Instagram, Email
3. /getdata ACC001     → Rich preview with hidden fields (🔒 ********)
4. /buy ACC001         → Confirm purchase → Credentials delivered
5. /download ACC001    → Re-download credentials anytime
```

### For You (Admin)

```
1. Add accounts to Google Sheet (or use demo_data.py --upload)
2. Start the bot (python bot.py)
3. Approve deposits from /admin panel
4. Purchased rows auto-delete from sheet + credentials auto-delivered
5. Check /stats for revenue, sales, and user metrics
```

---

## 📋 Commands Reference

### User Commands

| Command | Description |
|---------|-------------|
| `/start` | Launch the bot and view main menu |
| `/redeem CODE` | Activate account with invite code |
| `/browse` | View all available accounts |
| `/categories` | Browse by platform |
| `/newsearch` | Interactive 9-filter search builder |
| `/quick QUERY` | Natural language search |
| `/getdata ID` | Enhanced account preview (sensitive fields masked) |
| `/buy ID` | Purchase an account |
| `/download ID` | Re-download purchased credentials |
| `/deposit` | Buy credits with cryptocurrency |
| `/profile` | View balance and account info |
| `/orders` | View purchase history |

### Admin Commands

| Command | Description |
|---------|-------------|
| `/admin` | Open admin dashboard |
| `/stats` | Real-time statistics |
| `/pending` | Review pending deposits |
| `/gencode Role` | Generate invite codes |
| `/addbalance UID AMT` | Adjust user balance |
| `/broadcast MSG` | Send announcement to all users |
| `/refresh` | Force-reload inventory from Google Sheet |
| `/syncsheet` | Sync sold items to Google Sheet |
| `/export_payments` | Download payment log as CSV |

---

## 📊 Google Sheet Structure

Your inventory is a Google Sheet with 16 columns:

| Column | Visibility | Description |
|--------|-----------|-------------|
| ID | 🟢 Public | Unique identifier (ACC001) |
| Platform | 🟢 Public | TikTok, Facebook, Instagram, Email |
| Title | 🟢 Public | Descriptive account name |
| Price | 🟢 Public | Price in credits |
| Status | 🟢 Public | available / sold |
| Category | 🟢 Public | Fitness, Fashion, Gaming, etc. |
| Region | 🟢 Public | USA, EU, Asia |
| Followers | 🟢 Public | Follower count |
| Account Age | 🟢 Public | How old the account is |
| Verification | 🟢 Public | Verified / Unverified |
| Gender | 🟢 Public | Male / Female |
| **Name** | 🔒 Hidden | Login username — revealed after purchase |
| **Password** | 🔒 Hidden | Password — revealed after purchase |
| **Email** | 🔒 Hidden | Linked email — revealed after purchase |
| **Recovery** | 🔒 Hidden | Recovery info — revealed after purchase |
| **2FA** | 🔒 Hidden | Two-factor auth status — revealed after purchase |
| **2FA Code** | 🔒 Hidden | 2FA secret key / backup codes — revealed after purchase |

> Includes `demo_data.py` — upload 12 sample accounts with one command:
> ```bash
> python demo_data.py --upload
> ```

---

## 🔧 Quick Setup

```bash
# 1. Clone and install
git clone https://github.com/YOUR_USERNAME/social-seller-bot.git
cd social-seller-bot
pip install -r requirements.txt

# 2. Configure
cp .env.example .env
# Edit .env with your bot token, sheet ID, admin ID, wallet addresses

# 3. Add credentials.json for Google Sheets write-back (optional)
# See docs/SETUP_GUIDE.md for service account setup

# 4. Load demo data (optional)
python demo_data.py --upload

# 5. Run
python bot.py
```

> 📘 **Full step-by-step guide →** [docs/SETUP_GUIDE.md](docs/SETUP_GUIDE.md)

---

## 📁 Project Structure

```
SocialSellerBot/
├── bot.py                  # Main entry point
├── requirements.txt        # Python dependencies
├── .env.example            # Configuration template
├── credentials.json        # Google Sheets service account (you provide)
├── demo_data.py            # Demo data generator + uploader
├── Dockerfile              # Docker support
├── docker-compose.yml      # Docker Compose
│
├── config/                 # Settings loader
├── core/                   # Core logic
│   ├── database.py         #   SQLite + backup/restore + migrations
│   ├── sheets.py           #   Google Sheets reader (CSV)
│   ├── sheet_writer.py     #   Google Sheets writer (gspread)
│   └── cache.py            #   Product cache with TTL
│
├── handlers/               # Telegram command handlers
│   ├── start.py            #   /start, onboarding
│   ├── browse.py           #   /browse, /categories
│   ├── search.py           #   /newsearch, /quick
│   ├── purchase.py         #   /getdata, /buy, /download
│   ├── payment.py          #   /deposit, /paid
│   ├── profile.py          #   /profile, /orders
│   └── admin.py            #   Admin dashboard
│
├── docs/                   # Full documentation
│   ├── SETUP_GUIDE.md      #   Step-by-step beginner guide
│   ├── google-sheets-setup.md
│   ├── configuration.md
│   └── deployment.md
│
├── bot_data/               # Runtime data (auto-created)
│   ├── bot.db              #   SQLite database
│   └── user_data_backup.json  # Auto-backup (credit preservation)
│
├── scripts/                # Shell scripts
├── models/                 # Data models
├── utils/                  # Formatting, pagination, security
└── tests/                  # Test suite
```

---

## 💬 Purchase

<div align="center">

### Ready to launch your automated account marketplace?

| | Details |
|-|---------|
| 💬 **Contact** | [@Blackwolfisme on Telegram](https://t.me/Blackwolfisme) |
| 💰 **Pricing** | One-time fee — no subscriptions, no recurring charges, no revenue share |
| 📦 **Includes** | Full source code, documentation, setup assistance, and lifetime updates |
| ⏱ **Response** | Typically within a few hours |

<br/>

### [📩 DM @Blackwolfisme on Telegram →](https://t.me/Blackwolfisme)

</div>

---

<div align="center">

**Built with ❤️ using Python & aiogram 3**

*Powering automated social media account marketplaces across TikTok, Facebook, Instagram, and Email.*

</div>
