# Artemis 🚀

[![npm version](https://img.shields.io/npm/v/artemis-cli?color=cb3837&logo=npm)](https://www.npmjs.com/package/artemis-cli)
[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](#license)
[![Node](https://img.shields.io/badge/node-%3E%3D18-43853d?logo=node.js&logoColor=white)](https://nodejs.org)

> **One command. Your entire local dev stack on Kubernetes — no YAML, no config, no setup docs.**

Artemis is a CLI that deploys production-grade dev infrastructure — **Postgres, Redis, MongoDB, MySQL, MinIO, Prometheus, Grafana, RabbitMQ** — to your local Kubernetes cluster with a single command. It pulls the images, deploys everything in parallel, wires up port-forwarding, and hands you **copy-paste connection strings the moment it's done**.

No `helm install`. No 12 YAML files. No "first, create a namespace…". You run it, pick your services, and start coding.

> *"I stopped keeping a folder of docker-compose files. Now I just run `npx artemis-cli` and pick what I need."*

<p align="center">
  <img src="https://raw.githubusercontent.com/krishpinto/artemis-cli/main/web/public/artemis-logo.png" alt="Artemis" width="160">
</p>

---

## Quick Start

```bash
npx artemis-cli
```

- Launches an interactive terminal UI
- Detects your available Kubernetes clusters
- Lets you pick which services to deploy
- Pulls images and deploys everything in parallel
- Prints working connection strings the moment it's done

---

## Prerequisites

- [Docker Desktop](https://www.docker.com/products/docker-desktop/) with Kubernetes enabled
  - Docker Desktop → **Settings → Kubernetes → Enable Kubernetes → Apply**
- Node.js 18+

That's it.

---

## Commands

```bash
npx artemis-cli            # launch the TUI and deploy services
npx artemis-cli status     # see what's running + connection strings
npx artemis-cli connect    # port-forward all services to localhost
npx artemis-cli ui         # open the Mission Control web dashboard
npx artemis-cli down       # tear everything down
```

Or install globally for shorter commands:

```bash
npm install -g artemis-cli

artemis            # launch the TUI
artemis status
artemis connect
artemis ui
artemis down
```

---

## Mission Control (Web UI)

Run `artemis ui` to open a local dashboard at `http://localhost:4000`:

- **Dashboard** — live status of every deployed service with connection strings
- **PostgreSQL** — browse tables and run SQL queries in the browser
- **Redis** — browse keys, view values by type, add and delete keys
- **MongoDB** — browse collections and inspect documents as JSON
- **Docs** — copy-paste connection snippets for Node.js, Python, Prisma, Mongoose

---

## Services

| Service      | Description                        | Port  |
|--------------|------------------------------------|-------|
| PostgreSQL   | Relational database                | 5432  |
| Redis        | In-memory cache / message broker   | 6379  |
| MongoDB      | Document database                  | 27017 |
| MySQL        | Relational database                | 3306  |
| MinIO        | S3-compatible object storage       | 9000  |
| Prometheus   | Metrics collection                 | 9090  |
| Grafana      | Metrics dashboards                 | 3000  |
| RabbitMQ     | Message queue                      | 5672  |

---

## How it works

1. You pick services from the interactive menu
2. Artemis pulls the Docker images locally (parallel, fast)
3. Deploys them as Kubernetes workloads with persistent storage
4. Exposes each service on a fixed port via NodePort + port-forwarding
5. Prints connection strings — ready to paste into your app

Every service uses `imagePullPolicy: IfNotPresent`, so once an image is pulled, redeploys are instant.

---

## Built with

- [Ink](https://github.com/vadimdemedes/ink) — React for CLIs
- [@kubernetes/client-node](https://github.com/kubernetes-client/javascript) — Kubernetes JS client
- [Next.js](https://nextjs.org/) — Mission Control web dashboard
- [esbuild](https://esbuild.github.io/) — bundler

---

## License

MIT © [Krish Pinto](https://github.com/krishpinto)
