# 🎯 Bounty Hunter

> *Track. Capture. Collect. Repeat.*

![Version](https://img.shields.io/badge/version-1.0.0-red?style=flat-square)
![License](https://img.shields.io/badge/license-MIT-gray?style=flat-square)
![Node](https://img.shields.io/badge/node-20%2B-green?style=flat-square)
![Status](https://img.shields.io/badge/status-active-brightgreen?style=flat-square)

**Bounty Hunter** is a high-performance task tracking system built for teams that get things done. Assign bounties to issues, track hunters, and close targets — all from the command line or a slick dashboard. No fluff. Just targets and outcomes.

---

## 📋 Table of Contents

- [Features](#-features)
- [Tech Stack](#-tech-stack)
- [Getting Started](#-getting-started)
- [Configuration](#-configuration)
- [Usage](#-usage)
- [API Reference](#-api-reference)
- [Contributing](#-contributing)
- [License](#-license)

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

## 📅 Changelog

All notable changes to this project are documented here. Format based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/).

### [1.0.0] — 2024-11-20
#### Added
- Initial public release
- Core bounty creation and tracking system
- Hunter profiles with reputation scoring
- REST API with full CRUD for bounties and hunters
- Role-based access control (Admin, Hunter, Observer)
- Real-time webhook notifications
- Analytics dashboard
- Docker support
- CLI interface

### [0.9.0-beta] — 2024-10-05
#### Added
- Beta release for internal testing
- Basic CLI commands (`list`, `claim`, `complete`)
- PostgreSQL integration via Prisma
- JWT authentication

#### Fixed
- Race condition when two hunters claimed the same bounty simultaneously
- Dashboard not loading correctly on Safari

### [0.8.0-alpha] — 2024-08-18
#### Added
- Alpha version — core tracking logic
- Initial database schema
- Basic REST endpoints

#### Known Issues
- No auth layer yet
- Webhook delivery unreliable under high load

---

## 🏷️ Issue Labels

Use these labels to categorize and organize issues in the repository:

| Label              | Color       | Description                                         |
| ------------------ | ----------- | --------------------------------------------------- |
| `bug`              | 🔴 `#d73a4a` | Something isn't working as expected                 |
| `feature`          | 🟣 `#a2eeef` | New feature request or enhancement                  |
| `good first issue` | 🟢 `#7057ff` | Good for newcomers and first-time contributors      |
| `help wanted`      | 🔵 `#008672` | Extra attention or community help needed            |
| `documentation`    | 🟡 `#fef2c0` | Improvements or additions to documentation          |
| `duplicate`        | ⚪ `#cfd3d7` | This issue or PR already exists                     |
| `wontfix`          | ⚫ `#ffffff` | This will not be worked on                          |
| `question`         | 🟤 `#d876e3` | Further information is requested                    |
| `enhancement`      | 🔵 `#84b6eb` | Improvement to an existing feature                  |
| `in progress`      | 🟠 `#e4e669` | Currently being worked on                           |
| `blocked`          | 🔴 `#b60205` | Blocked by another issue or external dependency     |
| `needs review`     | 🟣 `#9936c7` | PR or issue waiting for review                      |
| `breaking change`  | 🔴 `#e11d48` | Introduces a breaking change to the API or behavior |
| `performance`      | 🟢 `#0e8a16` | Related to performance improvements                 |
| `security`         | 🔴 `#ee0701` | Security vulnerability or concern                   |

### Como criar as labels no GitHub

```bash
# Instale o GitHub CLI se ainda não tiver
brew install gh  # macOS
# ou: https://cli.github.com

# Autentique-se
gh auth login

# Crie as labels via script
gh label create "bug"            --color "d73a4a" --description "Something isn't working"
gh label create "feature"        --color "a2eeef" --description "New feature request"
gh label create "good first issue" --color "7057ff" --description "Good for newcomers"
gh label create "help wanted"    --color "008672" --description "Extra attention needed"
gh label create "documentation"  --color "fef2c0" --description "Docs improvements"
gh label create "in progress"    --color "e4e669" --description "Currently being worked on"
gh label create "blocked"        --color "b60205" --description "Blocked by dependency"
gh label create "needs review"   --color "9936c7" --description "Waiting for review"
gh label create "breaking change" --color "e11d48" --description "Introduces breaking change"
gh label create "performance"    --color "0e8a16" --description "Performance improvements"
gh label create "security"       --color "ee0701" --description "Security concern"
```

---

## ❓ FAQ

**Q: Preciso de Redis para rodar o projeto?**
Redis é usado para cache e filas de notificação. Para desenvolvimento local, você pode desabilitá-lo definindo `DISABLE_CACHE=true` no `.env` — o projeto funcionará normalmente, porém sem notificações em tempo real.

---

**Q: Posso usar outro banco de dados além do PostgreSQL?**
Atualmente não. O schema e algumas queries são específicos para PostgreSQL. Suporte a MySQL e SQLite está planejado para a v1.2.0.

---

**Q: Como faço para rodar os testes?**
```bash
npm run test        # todos os testes
npm run test:unit   # apenas testes unitários
npm run test:e2e    # testes end-to-end
```
Os testes E2E requerem um banco PostgreSQL rodando. Recomendamos usar o `docker-compose.test.yml` incluso no projeto.

---

**Q: A API tem rate limiting?**
Sim. Por padrão, o limite é de **100 requisições por minuto** por IP. Você pode ajustar isso via `RATE_LIMIT_MAX` no `.env`.

---

**Q: É possível rodar sem Docker?**
Sim, basta ter Node.js, PostgreSQL e Redis instalados localmente e seguir o guia de instalação manual na seção [Getting Started](#-getting-started).

---

**Q: Como contribuo com o projeto?**
Veja a seção [Contributing](#-contributing) abaixo. Issues com a label `good first issue` são um ótimo ponto de entrada.

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
