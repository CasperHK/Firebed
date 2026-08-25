# 🔥 Firebed

> **Lightning-fast, ultra-lightweight open-source incident management & postmortem platform.**

Firebed is a high-performance incident logging, real-time timeline tracking, and postmortem system built for engineering teams who demand zero friction during active outages. 

Powered by **Rust (Salvo)** on the backend and **Qwik** on the frontend, Firebed delivers instant sub-millisecond responses, sub-10MB memory usage, and zero-hydration instant UI load times—packaged into a single self-contained binary.

---

## ✨ Features

- ⚡ **Zero-Hydration UI**: Built with Qwik for instantaneous load times when every second counts during a P0 outage.
- 🚀 **Blazing Fast Backend**: Rust + Salvo framework handling high-concurrency webhook bursts effortlessly.
- ⏱️ **Real-Time Timelines**: Track incident progression, system status changes, and operator actions as they happen.
- 📝 **Markdown Postmortems**: Standardized postmortem templates with root-cause analysis (5 Whys) and actionable tracking.
- 🔌 **Extensible Webhooks**: Out-of-the-box integration readiness for Prometheus, Grafana, Sentry, and Datadog.
- 📦 **Single-Binary Deployment**: Static assets are embedded directly into the compiled Rust binary. No external Node.js server required.

---

## 🏗️ Tech Stack

- **Backend**: Rust, [Salvo Web Framework](https://salvo.rs/), SQLx, Tokio
- **Frontend**: [Qwik City](https://qwik.dev/), TailwindCSS
- **Database**: PostgreSQL
- **Deployment**: Docker / Single Executable Binary

---

## 📁 Repository Structure

```text
firebed/
├── backend/                  # Rust + Salvo API Service
│   ├── Cargo.toml
│   └── src/
│       ├── main.rs           # Embedded static server & API router
│       ├── api/              # Rest API & Webhook Handlers
│       └── models/           # SQLx Models & DB Migration
└── frontend/                 # Qwik Dashboard
    ├── package.json
    └── src/
        ├── routes/           # Qwik City Pages
        └── components/       # Reusable UI Components

```

---

## 🚀 Quick Start (Local Development)

### Prerequisites

* [Rust](https://www.rust-lang.org/) (v1.75+)
* [Node.js](https://nodejs.org/) (v18+) & `pnpm` / `npm`
* [PostgreSQL](https://www.postgresql.org/)

### 1. Clone the Repository

```bash
git clone [https://github.com/your-username/firebed.git](https://github.com/your-username/firebed.git)
cd firebed

```

### 2. Build the Frontend

```bash
cd frontend
pnpm install
pnpm build
cd ..

```

### 3. Run the Backend Server

```bash
cd backend
# Set up database URL
export DATABASE_URL="postgres://postgres:postgres@localhost:5432/firebed"

# Run migrations and start Salvo API
cargo run

```

Access the Firebed dashboard at **`http://127.0.0.1:5800`**.

---

## 🐳 Docker Deployment

Run Firebed with a single Docker command:

```bash
docker run -d \
  --name firebed \
  -p 5800:5800 \
  -e DATABASE_URL="postgres://user:pass@host.docker.internal:5432/firebed" \
  ghcr.io/your-username/firebed:latest

```

---

## 🤖 AI Agent & MCP Integration

Firebed includes native Model Context Protocol (MCP) and REST endpoints designed for autonomous AI agents (such as Claude, ChatGPT, or custom LLM ops tools) to manage incidents end-to-end. AI agents can safely query, create, update, or resolve incident records and append timeline events using structured JSON schemas. To ensure operational safety:

- **RBAC & Scoped Tokens**: Agents operate under dedicated service accounts with strict role-based access control (RBAC), limiting write/delete permissions to authorized scopes.
- **Audit Logging & Rollbacks**: Every AI-initiated modification (add, edit, soft-delete) is immutably logged in the system timeline with step-level provenance, allowing human responders to review or revert any action instantly.
- **Human-in-the-Loop Safeguards**: Destructive actions (e.g., hard-deleting records or closing critical P0 incidents) require explicit confirmation flags or human approval in the dashboard.

---

## 🤝 Contributing

Contributions, issues, and feature requests are welcome! Feel free to check the [issues page](https://www.google.com/search?q=https://github.com/your-username/firebed/issues).

1. Fork the Project
2. Create your Feature Branch (`git checkout -b feature/AmazingFeature`)
3. Commit your Changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the Branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

---

## 📄 License

Distributed under the MIT License. See `LICENSE` for more information.
