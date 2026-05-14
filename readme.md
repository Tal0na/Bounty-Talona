# 🎯 Bounty Hunter

> *Track. Capture. Collect. Repeat.*

![Version](https://img.shields.io/badge/version-1.0.0-red?style=flat-square)
![License](https://img.shields.io/badge/license-MIT-gray?style=flat-square)
![Node](https://img.shields.io/badge/node-20%2B-green?style=flat-square)
![Status](https://img.shields.io/badge/status-active-brightgreen?style=flat-square)

**Bounty Hunter** is a high-performance task tracking system built for teams that get things done. Assign bounties to issues, track hunters, and close targets — all from the command line or a slick dashboard. No fluff. Just targets and outcomes.

---

## 📋 Table of Contents

- [🎯 Bounty Hunter](#-bounty-hunter)
  - [📋 Table of Contents](#-table-of-contents)
  - [⚡ Features](#-features)
  - [🛠 Tech Stack](#-tech-stack)
  - [🚀 Getting Started](#-getting-started)
    - [Prerequisites](#prerequisites)
    - [Installation](#installation)
  - [⚙️ Configuration](#️-configuration)
  - [🔫 Usage](#-usage)
    - [CLI Commands](#cli-commands)
    - [Dashboard](#dashboard)
  - [📡 API Reference](#-api-reference)
    - [Bounties](#bounties)
    - [Hunters](#hunters)
  - [🤝 Contributing](#-contributing)
  - [📄 License](#-license)

---

## ⚡ Features

- 🎯 **Target Tracking** — Pin bounties to tasks, bugs, or milestones with live status updates
- 🧑‍💼 **Hunter Profiles** — Each agent has stats, history, and a reputation score
- 🔔 **Real-time Alerts** — Webhook and email notifications when bounties are claimed
- 📊 **Analytics Dashboard** — Visual breakdown of open, active, and completed bounties
- 🔐 **Role-based Access** — Admin, Hunter, and Observer permission tiers
- 🌐 **REST API** — Fully documented endpoints for third-party integrations
- 🐳 **Docker Ready** — One-command containerized deployment

---

## 🛠 Tech Stack

| Layer     | Technology           |
| --------- | -------------------- |
| Runtime   | Node.js 20+          |
| Framework | Express / Fastify    |
| Database  | PostgreSQL + Prisma  |
| Cache     | Redis                |
| Auth      | JWT + OAuth 2.0      |
| Frontend  | React + Tailwind CSS |
| Deploy    | Docker / Railway     |

---

## 🚀 Getting Started

### Prerequisites

- Node.js `>= 20.0.0`
- PostgreSQL `>= 15`
- Redis `>= 7`

### Installation

```bash
# Clone the repo
git clone https://github.com/talona/bounty-hunter.git
cd bounty-hunter

# Install dependencies
npm install

# Copy environment variables
cp .env.example .env

# Run database migrations
npm run db:migrate

# Start the development server
npm run dev
```

The app will be running at **http://localhost:3000**.

---

## ⚙️ Configuration

Edit your `.env` file with the following variables:

```env
# App
PORT=3000
NODE_ENV=development

# Database
DATABASE_URL=postgresql://user:password@localhost:5432/bountyhunter

# Redis
REDIS_URL=redis://localhost:6379

# Auth
JWT_SECRET=your_super_secret_key
JWT_EXPIRES_IN=7d

# Webhooks (optional)
WEBHOOK_URL=https://your-endpoint.com/hooks
```

---

## 🔫 Usage

### CLI Commands

```bash
# List all open bounties
npm run cli -- list

# Create a new bounty
npm run cli -- create --title "Fix auth bug" --deadline 2024-12-31

# Claim a bounty
npm run cli -- claim --id BH-042 --hunter @johndoe

# Mark bounty as completed
npm run cli -- complete --id BH-042
```

### Dashboard

Access the web dashboard at `http://localhost:3000/dashboard` to manage bounties visually.

---

## 📡 API Reference

### Bounties

| Method | Endpoint            | Description         |
| ------ | ------------------- | ------------------- |
| GET    | `/api/bounties`     | List all bounties   |
| POST   | `/api/bounties`     | Create a new bounty |
| GET    | `/api/bounties/:id` | Get bounty details  |
| PATCH  | `/api/bounties/:id` | Update a bounty     |
| DELETE | `/api/bounties/:id` | Delete a bounty     |

### Hunters

| Method | Endpoint             | Description        |
| ------ | -------------------- | ------------------ |
| GET    | `/api/hunters`       | List all hunters   |
| GET    | `/api/hunters/:id`   | Get hunter profile |
| POST   | `/api/hunters/claim` | Claim a bounty     |

**Example request:**

```bash
curl -X POST http://localhost:3000/api/bounties \
  -H "Authorization: Bearer <token>" \
  -H "Content-Type: application/json" \
  -d '{"title": "Fix login bug", "deadline": "2024-12-01"}'
```

---

## 🤝 Contributing

Contributions are welcome — the more hunters, the better.

```bash
# Fork the repo, then:
git checkout -b feature/your-feature
git commit -m "feat: add your feature"
git push origin feature/your-feature
# Open a Pull Request
```

Please follow the [Conventional Commits](https://www.conventionalcommits.org/) standard and make sure all tests pass before submitting.

```bash
npm run test
npm run lint
```

---

## 📄 License

MIT © [talona](https://github.com/talona)

---

<div align="center">
  <sub>Built with ☕ and a no-mercy policy toward open bugs.</sub>
</div>
