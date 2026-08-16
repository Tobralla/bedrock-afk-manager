<div align="center">

# 🤖 AFK Discord Bot

**Minecraft Bedrock AFK manager for [donutsmp.net](https://donutsmp.net), controlled from Discord and a live web dashboard.**

Keep an arbitrary number of Minecraft accounts online 24/7. Connect, disconnect, and chat with each
bot directly from your Discord server. No console access needed.

![Node.js](https://img.shields.io/badge/Node.js-18+-43853d?logo=node.js&logoColor=white)
![Discord.js](https://img.shields.io/badge/Discord.js-14-5865F2?logo=discord&logoColor=white)
![bedrock-protocol](https://img.shields.io/badge/bedrock--protocol-3.38-62b47a)
![Deploy](https://img.shields.io/badge/deploy-Railway-0b0d0e)

</div>

---

## ✨ Features

| Feature | Description |
|---|---|
| 🎮 **Multi-account AFK** | Run any number of Minecraft Bedrock sessions simultaneously |
| 🟩 **Discord control** | Full bot management through slash commands |
| 📊 **Live dashboard** | Web GUI with real-time status via Server-Sent Events |
| 🔄 **Auto-reconnect** | Per-account toggleable auto-reconnect |
| 🔐 **Microsoft OAuth** | Built-in Microsoft account login flow |
| 💬 **In-game chat** | Send messages and execute `/commands` from Discord |

## 🎮 Slash commands

| Command | Description |
|---|---|
| `/connect <account>` | Start AFK session for an account (label e.g. `alt@outlook.com`) |
| `/disconnect <account>` | Stop the AFK session |
| `/chat <account> <message>` | Send a chat message or `/command` in-game |
| `/status` | Show the status of all active sessions |
| `/reconnect <account> <enabled>` | Toggle auto-reconnect for an account |

## 🚀 Deployment (Railway)

This repo ships with `railway.json` + `nixpacks.toml`, so deploying is one click:

1. Create a new project in [Railway](https://railway.app) and deploy this repository.
2. Set the environment variables below.
3. Run `node register-commands.js` once to register the slash commands.

### Environment variables

| Variable | Required | Description |
|---|---|---|
| `DISCORD_TOKEN` | ✅ (for Discord) | Your Discord bot token |
| `DISCORD_CLIENT_ID` | ✅ (for Discord) | Application ID of your Discord bot |
| `DISCORD_GUILD_ID` | ✅ (for Discord) | Server ID where commands are registered |
| `DISCORD_CHANNEL_ID` | ❌ | Channel for status notifications |
| `PORT` | ❌ | Web dashboard port (defaults to `3000`) |

> Discord features are automatically disabled when `DISCORD_TOKEN` is not set. The web
> dashboard still works without it.

## 💻 Local development

```bash
npm install
npm run dev        # hot-reload via nodemon
npm run start      # production start
```

Create a Discord application at the [Discord Developer Portal](https://discord.com/developers/applications),
invite it to your server, then set the environment variables and register commands:

```bash
npm run register-commands
```

## 📁 Project structure

```
├── server.js               # Express + Discord + Minecraft session manager
├── register-commands.js    # One-time slash command registration
├── public/                 # Web dashboard (HTML/CSS/JS)
├── railway.json            # Railway deploy config
└── nixpacks.toml           # Nixpacks build config
```

## ⚠️ Disclaimer

This project is intended for streaming/tracking Minecraft servers that permit AFK accounts.
Always respect the server and platform rules. The author is not responsible for any misuse.