# 🦞 OpenClaw Manager

**One-click installer & management GUI for [OpenClaw](https://github.com/miaoxworld/OpenClawInstaller)** — the open-source AI assistant framework.

Built with **Tauri 2.0 + React 18 + TypeScript + Rust** for native performance on every desktop platform.

![Platform](https://img.shields.io/badge/platform-macOS%20|%20Windows%20|%20Linux-blue)
![Tauri](https://img.shields.io/badge/Tauri-2.0-orange)
![React](https://img.shields.io/badge/React-18-61DAFB)
![Rust](https://img.shields.io/badge/Rust-1.70+-red)

---

## ✨ Features & Usage Guide

### 🚀 One-Click Setup Wizard
Skip the terminal entirely. The built-in setup wizard automatically detects your environment, installs Node.js and OpenClaw, and initializes everything — all from the GUI.

**How to Use:**
1.  Launch OpenClaw Manager.
2.  If prerequisites are missing, the **Setup Wizard** will appear.
3.  Click **Install Prerequisites** to automatically install Node.js (via NVM) and Git.
4.  Click **Install OpenClaw** to clone and set up the core framework.
5.  Follow the guided steps until the dashboard appears.

### 📊 Dashboard & Service Control
Real-time monitoring and full lifecycle management of the OpenClaw service.

**Features:**
- Live service status (port, PID, memory usage, uptime)
- **Start / Stop / Restart / Kill All** actions
- Real-time log viewer with auto-refresh
- **Web Control UI**: Direct chat interface with your agents (served at `http://localhost:18789`)

**How to Use:**
- **Start Service:** Click the **Start** button in the dashboard top-right corner.
- **View Logs:** Check the "Live Logs" card for immediate output or go to the **Logs** tab for history.
- **Control UI:** Once the service is running, open `http://localhost:18789` to chat with your agents directly.
- **System Check:** Use the "System Requirements" card to verify your environment health.

### 🤖 AI Model Configuration
Flexible multi-provider AI configuration. Connect to the most powerful models or run local LLMs.

**Supported Providers:**
- **Google Gemini** (New! ✨): Gemini 3 Pro, Gemini 3 Flash
- **Anthropic**: Claude 3.5 Sonnet, Opus
- **OpenAI**: GPT-4o, GPT-4o-mini
- **DeepSeek**: DeepSeek V3, R1
- **Moonshot, Z.AI (GLM), Qwen, MiniMax, Venice, OpenRouter**
- **Ollama**: Local model support
- **Custom**: Connect to any OpenAI-compatible endpoint

**How to Use:**
1.  Go to **Settings > AI Config**.
2.  Click **Add AI Provider**.
3.  Select a provider (e.g., **Google Gemini**) or choose **Custom**.
4.  Enter your API Key (optional for Ollama).
5.  Select your preferred models (recommended models are pre-selected).
6.  Click **Save**.
7.  (Optional) Set a model as **Primary** to be used as the default for all agents.

### 🧩 MCP Management
Full [Model Context Protocol](https://modelcontextprotocol.io/) server management with integrated **mcporter** support.

**How to Use:**
1.  Go to the **MCP** tab.
2.  Click **Add MCP Server**.
3.  Choose **Stdio** (local command) or **SSE** (remote URL).
4.  Enter the command/URL and arguments.
5.  Toggle the switch to **Enable**.
6.  Changes are automatically synced to `~/.mcporter/mcporter.json` for OpenClaw to use.

### 📚 Skills Management
Browse, install, and manage OpenClaw skills via **ClawHub**.

**How to Use:**
1.  Go to the **Skills** tab.
2.  Browse the registry for available skills (e.g., specialized coding, research, or creative writing skills).
3.  Click **Install** on a skill card to add it to your OpenClaw instance.
4.  Installed skills are immediately available to your agents.

### 📱 Message Channels
Connect OpenClaw to multiple messaging platforms for omnichannel AI.

**Supported Channels:**
- **Telegram**, **Feishu**, **Discord**, **Slack**, **WhatsApp**, + more via plugins.

**How to Use (Telegram Example):**
1.  Go to **Settings > Channels**.
2.  Select **Telegram**.
3.  Enter your **Bot Token** (from BotFather).
4.  Configure **Allowed Groups** and **Allowed Users** for security.
5.  Enable the channel and click **Save**.

### 🤖 Multi-Agent Routing
Run multiple specialized AI agents with intelligent message routing and nested subagent orchestration.

**Features:**
- **Agent Creation**: Create specialized agents (e.g., Coder, Researcher).
- **Subagents**: Nest agents to create complex workflows.
- **Personality Editor**: Edit `SOUL.md` directly in the app.

**How to Use:**
1.  Go to **Settings > Agents**.
2.  Click **Create Agent**.
3.  Choose a template or start from blank.
4.  Define the agent's **Personality** in the built-in editor.
5.  Configure **Subagents** if this agent needs to delegate tasks.
6.  Use the **Routing Test** tool to verify which agent handles specific user queries.

### 📋 Application Logs
Built-in structured log viewer.

**How to Use:**
1.  Go to the **Logs** tab.
2.  Use the filters to show only **Error** or **Warning** logs.
3.  Click on a log entry to expand details.
4.  Use **Export Logs** to save them for troubleshooting/reporting issues.

### 🔄 Auto-Update
Automatic update detection for OpenClaw.

**How to Use:**
- When a new version is available, a banner will appear at the top of the app.
- Click **Update Now** to automatically download and install the latest version.

---

## 📁 Project Structure

```
openclaw-manager/
├── src-tauri/                 # Rust Backend
│   ├── src/
│   │   ├── main.rs            # Entry point
│   │   ├── commands/          # Backend logic (config, install, service, etc.)
│   │   ├── models/            # Data structures
│   │   └── utils/             # Helpers
│   ├── Cargo.toml
│   └── tauri.conf.json
│
├── src/                       # React Frontend
│   ├── components/            # UI Components (Dashboard, Settings, specific features)
│   ├── hooks/                 # Custom Hooks
│   ├── lib/                   # API bindings
│   ├── stores/                # State management (Zustand)
│   └── styles/                # Tailwind CSS
│
├── package.json
└── vite.config.ts
```

---

## 🛠️ Tech Stack

| Layer | Technology | Purpose |
|-------|------------|---------|
| Frontend | React 18 | UI framework |
| State | Zustand | Lightweight reactive state |
| Styling | TailwindCSS | Utility-first CSS |
| Animation | Framer Motion | Smooth transitions & micro-interactions |
| Backend | Rust | High-performance system operations |
| Desktop | Tauri 2.0 | Native cross-platform shell |

---

## 🚀 Quick Start (Development)

### Prerequisites

| Tool | Version | Download |
|------|---------|----------|
| **Node.js** | >= 18.0 | [nodejs.org](https://nodejs.org/) |
| **Rust** | >= 1.70 | [rustup.rs](https://rustup.rs/) |
| **pnpm** or npm | Latest | Comes with Node.js |

### Clone & Run

```bash
git clone https://github.com/MrFadiAi/openclaw-one-click-installer.git
cd openclaw-one-click-installer

npm install          # Install dependencies
npm run tauri:dev    # Launch in development mode (hot-reload)
```

> **Note:** First build compiles all Rust dependencies and takes **3–5 minutes**. Subsequent runs are much faster.

### Build Release

```bash
npm run tauri:build
```

Output in `src-tauri/target/release/bundle/`:

| Platform | Formats |
|----------|---------|
| macOS | `.dmg`, `.app` |
| Windows | `.msi`, `.exe` |
| Linux | `.deb`, `.AppImage` |

---

---

## 🆕 Changelog

### v0.0.13
- **Fixed Service Stop**: The "Stop" button now reliably terminates the OpenClaw process (including force kill fallback), preventing zombie processes and Bonjour naming conflicts.
- **Fixed Service Restart**: The "Restart" button now utilizes the robust stop logic to ensure clean restarts.
- **Fixed Telegram `/restart`**: Implemented a **Service Supervisor** that automatically revives the gateway when it is restarted via Telegram command.
- **Fixed Supervisor Crash**: Resolved an `EBADF` crash on Windows by detaching stdio for the supervised background process.
- **Config Cleanup**: Removed invalid keys (`timezone`, `logLevel`) from `openclaw.json` to pass doctor checks.

---

## 🤝 Contributing

1. Fork the project
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

---

## 📄 License

MIT License — See [LICENSE](LICENSE) for details.

---

**Made with ❤️ by the OpenClaw Community**
 
