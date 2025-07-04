# 🛍️ Telegram Price Tracker Bot

This bot monitors product prices from popular websites (Kaspi.kz, Intertop.kz, Wildberries.ru) and notifies users via Telegram if the price changes.

---

## ✨ Features

- ✅ Track products from:
  - [Kaspi.kz](https://kaspi.kz/)
  - [Intertop.kz](https://intertop.kz/)
  - [Wildberries Global](https://global.wildberries.ru/)
- ✅ Get hourly or 5-minute updates on price changes
- ✅ Automatically stores products and their prices in SQLite
- ✅ Sends Telegram messages when:
  - Price changes
  - Product fails to parse
  - Price stays the same (optional notification)

---

## 🧰 Technologies Used

- Python 3.11+
- [python-telegram-bot](https://github.com/python-telegram-bot/python-telegram-bot)
- [Selenium](https://www.selenium.dev/)
- [BeautifulSoup](https://www.crummy.com/software/BeautifulSoup/)
- [APScheduler](https://apscheduler.readthedocs.io/)
- [FastAPI](https://fastapi.tiangolo.com/) *(optional, for REST API access)*
- SQLite3

---

## 🛠️ Setup & Usage

### 1. Clone the repo
```bash
git clone https://github.com/yourusername/telegram-price-tracker.git
cd telegram-price-tracker

### 2. Requirement
python-telegram-bot==20.7
apscheduler==3.10.4
selenium==4.16.0
beautifulsoup4==4.12.3
fastapi==0.110.0
uvicorn==0.29.0

### 3. Telegram Bot Token
Edit bot.py
BOT_TOKEN = "your_telegram_bot_token_here"

### 4. Run The Telegram Bot
python bot.py

### 5. (Optional) Run the FastAPI server 
python -m uvicorn api.main:app --reload
Visit http://127.0.0.1:8000/docs for Swagger UI.

How It Works

    User sends /start to the bot.

    User chooses a site (Kaspi / Intertop / Wildberries).

    User sends the product link.

    Bot scrapes price and title, stores in database.

    Every 5 minutes, the bot checks all tracked links:

        If price changed → sends update to user

        If not changed → optional message

        If failed to parse → sends error to user


telegram_bot/
├── bot.py               # Telegram bot logic
├── api/
│   ├── main.py          # FastAPI app
│   ├── db.py            # SQLite database helper
│   ├── kaspi.py         # Kaspi parser
│   ├── intertop.py      # Intertop parser
│   └── wildberries.py   # Wildberries parser
├── products.db          # SQLite DB file
└── README.md

