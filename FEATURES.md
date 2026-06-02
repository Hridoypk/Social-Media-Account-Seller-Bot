<div align="center">

# ✨ Features — Social Media Account Seller Bot

**Complete feature breakdown of every capability built into the bot.**

---

</div>

## 🏪 Multi-Platform Marketplace

Sell accounts from **four major social media platforms** through a single, unified Telegram bot interface.

| Platform | Emoji | Supported Metadata |
|----------|-------|-------------------|
| **TikTok** | 🎵 | Followers, Account Age, Region, Verification, Gender, Category |
| **Facebook** | 📘 | Followers, Account Age, Region, Verification, Gender, Category |
| **Instagram** | 📸 | Followers, Account Age, Region, Verification, Gender, Category |
| **Email** | 📧 | Account Age, Region, Verification, Gender, Provider (Gmail/Outlook/Yahoo) |

### Browsing Experience

- **Inline keyboard navigation** — Tap buttons instead of typing commands (Browse, Search, Deposit, Profile, Help)
- **🔥 Hot Deals on welcome** — 3 cheapest accounts shown right on the `/start` screen
- **Platform-specific emojis** — Each platform gets its own visual identity (🎵 📘 📸 📧)
- **Category filtering** — Browse by niche: Fitness, Fashion, Gaming, Business, Travel, Food, etc.
- **Paginated listings** — 5 items per page with inline navigation buttons
- **Rich product cards** — Each listing shows ID, price, region, followers, account age, and category
- **Verified badges** — ✅ shown next to verified accounts
- **Cache age indicator** — "Updated 2m ago" shown at the bottom of browse results
- **Product ID validation** — Invalid IDs like `/buy hello!` show clear error messages before hitting the database

---

## 🔍 Advanced Search Engine

### Interactive 9-Filter Search Builder (`/newsearch`)

Build complex queries using an interactive inline keyboard. Each filter has predefined options:

| # | Filter | Options |
|---|--------|---------|
| 1 | 📱 Platform | TikTok, Facebook, Instagram, Email |
| 2 | 📍 Region | USA, EU, UK, Asia, Middle East, Africa, South America |
| 3 | 📅 Account Age | 0-6 months, 6-12 months, 1-2 years, 2-5 years, 5+ years |
| 4 | 👥 Followers | 0-1k, 1k-10k, 10k-50k, 50k-100k, 100k+ |
| 5 | 💰 Price Range | $0-10, $10-25, $25-50, $50-100, $100+ |
| 6 | ✅ Verification | Verified only, Unverified only |
| 7 | 📂 Category | Fitness, Tech, Fashion, Gaming, Business, Lifestyle |
| 8 | ⚧ Gender | Male, Female |
| 9 | 👤 Name | Free-text keyword search |

### Natural Language Quick Search (`/quick`)

```
/quick TikTok, USA, Verified
/quick Instagram, 50k followers, Fashion
/quick Facebook, EU, Business
/quick Email, Gmail, 5 years
```

### Search History

- Last **20 searches** saved per user
- Accessible via `/history`
- One-tap re-run previous searches

---

## 💰 Integrated Payment System

### 6 Credit Packages

| Package | Credits | Price | Per Credit | Savings |
|---------|---------|-------|------------|---------|
| 🟠 **Trial** | 5 | $5 | $1.00 | — |
| 🟡 **Starter** | 15 | $12 | $0.80 | 20% off |
| 🟢 **Standard** | 35 | $25 | $0.71 | 29% off |
| 🔵 **Pro** | 80 | $50 | $0.63 | 37% off |
| 💎 **Premium** | 200 | $99 | $0.50 | 50% off |
| 🔥 **Enterprise** | 500 | $199 | $0.40 | 60% off |

### 4 Cryptocurrency Payment Methods

| Currency | Network | Icon |
|----------|---------|------|
| **USDT** | TRC-20 (Tron) | 💵 |
| **Bitcoin** | BTC | ₿ |
| **Ethereum** | ERC-20 | ⟠ |
| **Solana** | SOL | ◎ |

### Payment Flow

```
/deposit → Select Package → Choose Crypto → Copy Wallet Address
    → Send Payment → Submit TX Hash → Admin Approves → Credits Added
```

- **Admin-verified** — Every deposit manually reviewed for fraud prevention
- **Unique payment IDs** — `PAY-XXXXXXXX` format for tracking
- **Transaction history** — Full audit trail with timestamps

---

## 🛒 Purchase Pipeline

The complete automated flow from purchase to delivery:

```
Step 1: Buyer clicks "Confirm Purchase"
    ↓
Step 2: Bot force-refreshes cache from Google Sheet (prevents stale purchases)
    ↓
Step 3: Bot fetches FULL row data via gspread (including hidden credentials)
    ↓
Step 4: Credits deducted atomically (asyncio.Lock prevents race conditions)
    ↓
Step 5: Purchase recorded in database with credentials_json
    ↓
Step 6: Google Sheet updated → Status = "sold", credentials = "[SOLD]"
    ↓
Step 7: Row DELETED from Google Sheet entirely
    ↓
Step 8: Credentials delivered to buyer (auto-delete after 60 seconds)
    ↓
Step 9: Cache refreshed → product disappears from listings
    ↓
Step 10: Admin notified of sale
    ↓
Step 11: "What Next?" buttons shown (Browse More, Re-Download, Orders, Menu)
```

### Smart Balance Shortfall

When a user can't afford a product, the bot shows:
- Exact amount needed: "You need $5.00 more"
- Inline "💰 Buy Credits" button for instant deposit
- Alternative "Browse Other" button

### Anti-Double-Sell Protection (3 Layers)

| Layer | Mechanism |
|-------|-----------|
| 1. **Database** | `sold_products` table checked before every purchase |
| 2. **Atomic Lock** | `asyncio.Lock` prevents concurrent credit deductions |
| 3. **Cache Refresh** | Force-refresh from Google Sheet right before buying |

### Re-Download

```
/download           → List all purchased accounts
/download ACC001    → Re-send credentials (auto-deletes after 60s)
```

Credentials are stored permanently in the database, so even after the Google Sheet row is deleted, buyers can always re-download.

---

## 📊 Google Sheets Integration

### Dual-Mode Operation

| Mode | How It Works | When |
|------|-------------|------|
| **Read-Only** | Reads inventory via public CSV URL | Always (no setup needed) |
| **Read + Write** | Also marks sold, clears credentials, deletes rows | With `credentials.json` |

### 17-Column Structure

**Public Fields (visible before purchase):**

| Column | Description |
|--------|-------------|
| ID | Unique identifier (ACC001) |
| Platform | TikTok, Facebook, Instagram, Email |
| Title | Descriptive account name |
| Price | Price in credits |
| Status | available / sold |
| Category | Niche (Fitness, Fashion, etc.) |
| Region | USA, EU, Asia |
| Followers | Follower count |
| Account Age | 6+ months, 2 years, etc. |
| Verification | Verified / Unverified |
| Gender | Male / Female |

**Hidden Fields (🔒 revealed only after purchase):**

| Column | Description |
|--------|-------------|
| Name | Account login username |
| Password | Account password |
| Email | Linked email address |
| Recovery | Recovery phone/email |
| 2FA | Two-factor authentication status |
| 2FA Code | 2FA secret key or backup codes |

### Demo Data Tool

```bash
python demo_data.py --upload       # Upload 12 sample accounts to Google Sheet
python demo_data.py --output csv   # Generate CSV for manual import
python demo_data.py --json         # View as JSON
```

---

## 🔐 Security Features

### 4-Tier Role System

| Role | Access Level |
|------|-------------|
| **Guest** | View bot info only. Must redeem invite code to unlock features. |
| **Member** | Search, preview, purchase accounts, view orders |
| **VIP** | Priority access, extended search history, reduced cooldowns |
| **Admin** | Full control — user management, deposits, settings, broadcast |

### Invite-Only Registration

- Admin generates codes via `/gencode member` or `/gencode vip`
- Single-use codes — one code, one user
- Codes auto-expire after use

### Data Protection

| Feature | How It Works |
|---------|-------------|
| **Masked Previews** | Hidden fields shown as `🔒 ********` until purchased |
| **Auto-Delete** | Credential messages self-destruct after 60 seconds (configurable) |
| **Sheet Redaction** | Name/Password/Email cleared to `[SOLD]` in Google Sheet after sale |
| **Row Deletion** | Entire row removed from sheet after purchase |
| **Credit Preservation** | User balances auto-backed up to JSON on every startup |
| **Auto-Restore** | If database is lost, credits restored from backup automatically |

### Anti-Fraud Measures

- Duplicate transaction ID detection
- Rate limiting on purchases and deposits
- Cooldown periods between transactions
- Maximum pending deposit limits per user
- Admin-verified payments (no automatic crediting)

### Role-Aware `/help` Command

- **Guests** see only 5 basic commands (start, redeem, browse, categories, help)
- **Members** see full shopping commands (13 commands including search, buy, deposit)
- **Admins** see all commands including admin panel (24+ commands)

### Universal `/cancel` Command

- Clean exit from any multi-step flow (search, deposit, purchase)
- Shows "Main Menu" inline button for instant navigation back

---

## 👤 Admin Dashboard

### Real-Time Statistics (`/stats`)

- Total users by role tier
- Active inventory by platform
- Revenue (total deposits, approved, pending)
- Sales metrics (purchases, average order value, top platforms)
- System health (uptime, cache status, database size)

### Deposit Management (`/pending`)

- One-tap **Approve** or **Reject** buttons
- Auto-credit on approval
- Full payment history per user

### User Management

| Command | Action |
|---------|--------|
| `/gencode Role` | Generate invite codes |
| `/setrole UID Role` | Change user role |
| `/addbalance UID AMT` | Adjust user balance |
| `/broadcast MSG` | Send announcement to all users |

### Data & Reporting

| Command | Action |
|---------|--------|
| `/payments UID` | View payment log for a user |
| `/deposit_summary` | Financial summary report |
| `/export_payments` | Download payment log as CSV |
| `/syncsheet` | Sync sold items to Google Sheet |
| `/refresh` | Force-reload inventory data |
| `/backup` | View database and backup status |
| `/auditlog` | View last 20 admin actions with timestamps |

### Admin Audit Log

All admin actions are automatically logged to a database table:

| Action | Logged Details |
|--------|---------------|
| `approve_deposit` | Payment ID, credits added, target user |
| `reject_deposit` | Payment ID, target user |
| `addbalance` | Amount, new balance, target user |
| `setrole` | Old role → new role, target user |
| `gencode` | Code, role |
| `broadcast` | Sent/failed count, message preview |

View via `/auditlog` — shows emoji-coded entries with timestamps.

---

## 🛡 Reliability Features

### Credit Preservation System

User credits are **never lost**, even during updates or database resets:

```
Bot Startup:
  1. Auto-backup all user data to user_data_backup.json
  2. Run schema migrations (add missing columns, no data loss)
  3. If database is empty, auto-restore from backup
  4. Log: "Backup saved: 5 users, total balance $350.00"
```

### Session Conflict Resolution

Automatically handles `TelegramConflictError` when multiple bot instances try to run:

- Clears existing webhooks on startup
- Claims the polling session
- Auto-retries with exponential backoff

### Google Sheets Failover

- Products cached locally with configurable TTL (default: 5 minutes)
- Local CSV backup updated on every successful fetch
- Bot continues working even if Google Sheets is temporarily down

---

## 🚀 Deployment Options

| Method | Best For | Command |
|--------|---------|---------|
| **Terminal** | Development, testing | `python bot.py` |
| **Docker** | Production servers | `docker compose up -d` |
| **Termux** | Android phones | `bash scripts/start.sh` |
| **VPS + systemd** | 24/7 production | `systemctl start sellbot` |

---

<div align="center">

### 💬 [Purchase on Telegram → @Blackwolfisme](https://t.me/Blackwolfisme)

**One-time fee · No subscriptions · No revenue share · Lifetime updates**

</div>
