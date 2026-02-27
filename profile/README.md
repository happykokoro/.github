```
 ██╗  ██╗ █████╗ ██████╗ ██████╗ ██╗   ██╗
 ██║  ██║██╔══██╗██╔══██╗██╔══██╗╚██╗ ██╔╝
 ███████║███████║██████╔╝██████╔╝ ╚████╔╝
 ██╔══██║██╔══██║██╔═══╝ ██╔═══╝   ╚██╔╝
 ██║  ██║██║  ██║██║     ██║        ██║
 ╚═╝  ╚═╝╚═╝  ╚═╝╚═╝     ╚═╝        ╚═╝

 ██╗  ██╗ ██████╗ ██╗  ██╗ ██████╗ ██████╗  ██████╗
 ██║ ██╔╝██╔═══██╗██║ ██╔╝██╔═══██╗██╔══██╗██╔═══██╗
 █████╔╝ ██║   ██║█████╔╝ ██║   ██║██████╔╝██║   ██║
 ██╔═██╗ ██║   ██║██╔═██╗ ██║   ██║██╔══██╗██║   ██║
 ██║  ██╗╚██████╔╝██║  ██╗╚██████╔╝██║  ██║╚██████╔╝
 ╚═╝  ╚═╝ ╚═════╝ ╚═╝  ╚═╝ ╚═════╝ ╚═╝  ╚═╝ ╚═════╝
```

**Personal projects, games, and tools — all self-hosted on a single VPS.**

Everything runs on one DigitalOcean droplet (2 vCPU · 4 GB RAM · 120 GB disk · SGP1), proxied through Cloudflare, managed with Docker Compose and PM2.

---

### 🌐 Websites & Apps

| Project | Stack | Description | Live |
|---------|-------|-------------|------|
| **happykokoro** | Next.js · Payload CMS · SQLite | Personal site & blog with layout builder, draft preview, SEO, and dark mode | [happykokoro.com](https://happykokoro.com) |
| **d20-card-game** | Phaser 3 · Vanilla JS | Browser card-battle game — all textures procedurally generated, zero image assets | [game01.happykokoro.com](https://game01.happykokoro.com) |
| **Chaincards** | React · Vite | D20 roguelike deckbuilder with 3 heroes, 13-node maps, shops, and boss fights | [game02.happykokoro.com](https://game02.happykokoro.com) |
| **ai-roundtable** | FastAPI · React/TS · Claude API | Multi-agent AI debate system — 6 specialized agents discuss software design decisions | [roundtable.happykokoro.com](https://roundtable.happykokoro.com) |
| **kokoro-alpha-lab** | Rust · Next.js · Redis · Solana | Quantitative alpha framework for Solana — 11-factor signal pipeline, prediction engine, risk management, and MEV-protected execution (28 CIL crates, 709 tests) | [alpha.happykokoro.com](https://alpha.happykokoro.com) |

### 🛠️ Developer Tools

| Project | Stack | Description |
|---------|-------|-------------|
| **agent-orchestra** | Rust · Python FastAPI · SQLite | Multi-agent orchestrator — launches parallel Claude Code agents in isolated git worktrees with a real-time dashboard |
| **lab-mcp** | TypeScript · MCP SDK · Zod | MCP server exposing 50+ tools for kokoro-alpha-lab (lab, engine, data, artifacts, admin) |

### 🏗️ Infrastructure

| Project | Description |
|---------|-------------|
| **kokoro-services** | Docker Compose config, Nginx reverse-proxy rules, and runbooks for all self-hosted services |
| **kokoro-alpha-lab-frontend** | Next.js dashboard — TradingView charts, Kalman overlays, Pyth oracle feeds, Solana wallet integration |

**Self-hosted services** managed via `kokoro-services`:

| Service | Purpose | URL |
|---------|---------|-----|
| Homepage Dashboard | Landing / status overview | [dash.happykokoro.com](https://dash.happykokoro.com) |
| Umami | Privacy-friendly analytics | [analytics.happykokoro.com](https://analytics.happykokoro.com) |
| Uptime Kuma | Uptime monitoring & alerts | [status.happykokoro.com](https://status.happykokoro.com) |
| Netdata | Real-time system metrics | [monitor.happykokoro.com](https://monitor.happykokoro.com) |
| Gitea | Self-hosted Git server | [git.happykokoro.com](https://git.happykokoro.com) |
| PrivateBin | Encrypted paste service | [paste.happykokoro.com](https://paste.happykokoro.com) |
| Excalidraw | Collaborative whiteboard | [draw.happykokoro.com](https://draw.happykokoro.com) |
| Shlink | URL shortener | [link.happykokoro.com](https://link.happykokoro.com) |
| Linkding | Bookmark manager | [bookmarks.happykokoro.com](https://bookmarks.happykokoro.com) |
| Syncthing | File synchronization | [sync.happykokoro.com](https://sync.happykokoro.com) |

### Tech Stack

```
Languages    Rust · TypeScript · Python · JavaScript
Frontend     Next.js · React · Vite · Phaser 3 · TailwindCSS
Backend      FastAPI · Payload CMS · Actix/Tokio
Data         PostgreSQL · SQLite · Redis
Infra        Docker Compose · Nginx · PM2 · Cloudflare
AI/ML        Claude API · MCP Protocol · Multi-agent systems
```

---

<sub>Hosted on DigitalOcean SGP1 &middot; Proxied through Cloudflare &middot; Managed with Docker Compose + PM2</sub>
