<div align="center">

# 🚀 MrLeechBot Deployment Guide

A simple Telegram Leech Bot for deploying on **Heroku** or **VPS** using Docker.

---

## 🌐 Deployment Options

* [Heroku CLI Deployment](#-deploy-on-heroku)
* [VPS Deployment](#-deploy-on-vps)
* [Environment Variables](#-environment-variables)

---

</div>

---

## 💜 Deploy on Heroku

### ✅ Prerequisites

* [Git](https://git-scm.com/downloads)
* [Heroku CLI](https://devcenter.heroku.com/articles/heroku-cli#install-the-heroku-cli)

### 🛠️ Installation Steps

#### 1. Clone the Repository

```bash
git clone https://github.com/sathishk-dev/mrleechbot.git && cd mrleechbot
```

#### 2. Install Heroku CLI

Ubuntu/Debian:

```bash
curl https://cli-assets.heroku.com/install-ubuntu.sh | sh
```

Termux/Other Linux:

```bash
curl https://cli-assets.heroku.com/install.sh | sh
```

npm (not recommended):

```bash
npm install -g heroku
```

#### 3. Login to Heroku

```bash
heroku login        # Opens browser
# or
heroku login -i     # Terminal login (use API key as password)
```

#### 4. Create Heroku App

```bash
heroku create --region us --stack container APP_NAME
```

* `--region us` or `eu`
* Replace `APP_NAME` with your unique name or leave it blank to auto-generate

#### 5. Set Environment Config

Edit your environment file:

```bash
nano config.env
```

🧪 Example:

```env
BOT_TOKEN=""
TELEGRAM_API=""
TELEGRAM_HASH=""
OWNER_ID=""
DATABASE_URL=""
BASE_URL=""
SET_COMMANDS="True"
UPSTREAM_REPO="https://github.com/sathishk-dev/mrleechbot.git"
UPSTREAM_BRANCH="hk_skmlx"
```

📌 Save with `CTRL + X`, press `Y`, then `Enter`.

#### 6. Connect Git & Deploy

```bash
git add . -f
git commit -m "Heroku Setup"
heroku git:remote -a APP_NAME
git push heroku main -f
```

#### 7. Logs

```bash
heroku logs -a APP_NAME -t
```

---

## 🚩 Deploy on VPS

### ✅ Prerequisites

* Git, Docker installed on your VPS

### 🛠️ Steps

```bash
git clone https://github.com/sathishk-dev/mrleechbot.git
cd mrleechbot
pico config.env   # Or use nano/vim to edit the file
```

📃 Fill in the required values in `config.env`:

```env
BOT_TOKEN=""
TELEGRAM_API=""
TELEGRAM_HASH=""
OWNER_ID=""
DATABASE_URL=""
UPSTREAM_REPO=""
UPSTREAM_BRANCH=""
```

### 🌟 Build and Run Docker

```bash
sudo docker build . -t wzml && sudo docker run -p 8080:8080 wzml
```

Your bot is now up and running ❤️

---

## 🔢 Environment Variables

| Variable          | Description                                                                    |
| ----------------- | ------------------------------------------------------------------------------ |
| `BOT_TOKEN`       | Telegram bot token from [BotFather](https://t.me/BotFather)                    |
| `OWNER_ID`        | Your Telegram user ID                                                          |
| `TELEGRAM_API`    | API ID from [my.telegram.org](https://my.telegram.org)                         |
| `TELEGRAM_HASH`   | API hash from [my.telegram.org](https://my.telegram.org)                       |
| `DATABASE_URL`    | MongoDB URI                                                                    |
| `BASE_URL`        | URL where the bot is hosted (for Heroku use `https://your-app.herokuapp.com/`) |
| `UPSTREAM_REPO`   | Git repo for updates                                                           |
| `UPSTREAM_BRANCH` | Branch name for auto updates                                                   |
| `SET_COMMANDS`    | Set to `True` to auto set bot commands                                         |

---

## 📖 License

This project is licensed under [MIT License](LICENSE).

---

<div align="center">
  Made with ❤️ by Sathish Kumar
</div>
