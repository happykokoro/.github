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

**Deep technology studio — quantitative trading, blockchain infrastructure, AI-native development tools, and multi-chain staking.**

One founder. Twelve products. 65+ Rust crates, 20 Anchor programs, 1118 tests, 98 MCP tools, 250+ technologies — all self-hosted on a single VPS, proxied through Cloudflare.

[tech.happykokoro.com](https://tech.happykokoro.com) · [happykokoro.com](https://happykokoro.com)

---

### Product Portfolio

| Status      | Project                    | Stack                                                 | Description                                                                                                                                                             |
| ----------- | -------------------------- | ----------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 🟢 Live     | **Kokoro Alpha Lab**       | Rust · Next.js · Redis · PostgreSQL · Solana          | Quantitative alpha framework — 65+ crates, 20+ alpha factors, IMM/RBPF prediction models, smart-money wallet clustering, MEV-protected Jito execution, 1118 tests       |
| 🟢 Live     | **Pipeline Kokoro**        | Rust · TypeScript · React · MCP                       | Automated dev pipeline engine — orchestrates Claude Code agents through 5-phase workflows, visual pipeline designer, 18 skill modules, 20 MCP tools                     |
| 🟢 Live     | **Kokoro MM**              | Rust · Next.js · PostgreSQL · Redis                   | Polymarket AMM SaaS — automated market making for binary prediction markets, 18 crates, 472 tests, 49 API endpoints                                                     |
| 🟢 Live     | **Kokoro Staking**         | Rust · TypeScript · Next.js · PostgreSQL · Redis      | Multi-chain staking aggregator — ETH, SOL, ATOM, DOT, AVAX, SUI, validator monitoring, restaking optimizer, tax reports                                                 |
| 🟢 Deployed | **Kokoro Liquidation Bot** | Rust · Tokio · Ethers                                 | Multi-chain DeFi liquidation engine — 6 EVM chains + Solana, 8 crates, flash loan execution, 28 tests                                                                   |
| 🔵 Built    | **Kokoro Protocol**        | Rust · Anchor · Solana · TypeScript                   | Fully on-chain DeFi protocol — 20 Anchor programs, 11 game types: prediction markets, lending, leveraged positions, yield vaults, AMM DEX, DAO governance, VRF fairness |
| 🔵 Built    | **Kokoro Pay**             | Rust · Next.js · Solana · PostgreSQL                  | Crypto payment gateway — USDC/SOL monitoring, automated license activation, multi-tenant SaaS, AES-GCM encrypted storage                                                |
| 🟡 Dev      | **Kokoro Agent Platform**  | Rust · TypeScript · React · MCP · Docker              | Hosted AI development agent platform — multi-agent orchestration, visual pipeline designer, team collaboration, subscription tiers                                      |
| 🟡 Dev      | **MCP Marketplace**        | TypeScript · MCP SDK · Zod · Next.js · Stripe         | Marketplace for packaged MCP tool servers — themed packs for trading, blockchain, DevOps, one-command install                                                           |
| 🟠 Stopped  | **Kokoro Polymarket Bot**  | Rust · Python                                         | Polymarket trading bot — 6-step pipeline (Scan/Research/Predict/Risk/Execute/Compound), strategy replacement pending                                                    |
| ⚪ Planned  | **Kokoro Stack**           | Docker · Nginx · Shell · Go                           | One-click self-hosted infrastructure kit — 12+ pre-configured services, auto SSL, backup scripts                                                                        |
| ⚪ Planned  | **Kokoro Validator**       | Rust · TypeScript · Next.js · PostgreSQL · Prometheus | B2B validator monitoring SaaS — multi-chain fleet management, SLA tracking, slashing alerts, white-label option                                                         |

### Ecosystem Services

| Service                       | Stack                               | Description                                                                                                                                                                                                |
| ----------------------------- | ----------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **kokoro-alpha-lab-frontend** | Next.js 16 · React 19 · Tailwind v4 | Real-time trading dashboard — TradingView charts, factor analytics, canvas strategy builder, Kalman overlays, Solana wallet integration, 6 charting libraries (D3, Recharts, Plotly, Chart.js, React Flow) |
| **lab-mcp**                   | TypeScript · MCP SDK · Zod          | MCP server exposing 98 tools for AI-native interaction with the Alpha Lab — signals, factors, backtests, engine control, Polymarket, admin, artifacts, quant tools                                         |
| **kokoro-wallet-monitor**     | Rust · Tokio · Solana               | Standalone wallet monitoring — real-time swap detection, Louvain graph clustering, Redis Streams output                                                                                                    |
| **kokoro-pricing-service**    | Rust · Axum · Solana                | Multi-DEX pricing aggregation — Jupiter, Raydium, Orca with order flow imbalance metrics                                                                                                                   |
| **kokoro-pay**                | Rust · Next.js · Solana             | Cryptocurrency payment gateway — USDC/SOL payment monitoring, automated license activation, multi-tenant SaaS                                                                                              |

### Developer Tools

| Project             | Stack                           | Description                                                                                                                                                                                           |
| ------------------- | ------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **agent-orchestra** | Rust · Python FastAPI · SQLite  | Multi-agent orchestrator — parallel Claude Code agents in isolated git worktrees, GM pipeline (launch → wait → analyze → merge → build → test), human-in-the-loop approval gates, real-time dashboard |
| **claude-init**     | Python (zero deps)              | CLI tool for bootstrapping Claude Code projects — detects language/framework, generates CLAUDE.md, settings, agents, skills, and commands                                                             |
| **ai-roundtable**   | FastAPI · React/TS · Claude API | Multi-agent AI debate system — 5 specialized agents + arbitrator discuss software design, generate SRS/SDD/TestPlan/ADR documents                                                                     |

### Websites & Games

| Project           | Stack                               | Description                                                                                         | Live                                                     |
| ----------------- | ----------------------------------- | --------------------------------------------------------------------------------------------------- | -------------------------------------------------------- |
| **happykokoro**   | Next.js 15 · Payload CMS 3 · SQLite | Personal portfolio & blog with layout builder, draft preview, SEO, Lexical rich text, and dark mode | [happykokoro.com](https://happykokoro.com)               |
| **kokoro-tech**   | Next.js 16 · Tailwind v4            | Kokoro Tech company website — projects, services, technology stack, capabilities showcase           | [tech.happykokoro.com](https://tech.happykokoro.com)     |
| **Chaincards**    | React · Vite                        | D20 roguelike deckbuilder — 3 heroes, 13-node maps, shops, boss fights                              | [game02.happykokoro.com](https://game02.happykokoro.com) |
| **d20-card-game** | Phaser 3 · Vanilla JS               | Browser card-battle game — all textures procedurally generated, zero image assets                   | [game01.happykokoro.com](https://game01.happykokoro.com) |

### Self-Hosted Infrastructure

3 servers across DigitalOcean and AWS, managed with Docker Compose, PM2, Nginx, and systemd.

#### DigitalOcean SGP1 — Main Services

| Spec        | Value                                       |
| ----------- | ------------------------------------------- |
| **Region**  | Singapore (SGP1)                            |
| **IP**      | 167.172.70.15                               |
| **Specs**   | 2 vCPU / 4 GB RAM / 120 GB SSD              |
| **OS**      | Ubuntu                                      |
| **Purpose** | Web services, dashboards, self-hosted tools |
| **Proxy**   | Cloudflare                                  |

| Service            | Purpose                          | URL                                                            |
| ------------------ | -------------------------------- | -------------------------------------------------------------- |
| Homepage Dashboard | Service status overview          | [dash.happykokoro.com](https://dash.happykokoro.com)           |
| Umami              | Privacy-respecting web analytics | [analytics.happykokoro.com](https://analytics.happykokoro.com) |
| Uptime Kuma        | Uptime monitoring & alerts       | [status.happykokoro.com](https://status.happykokoro.com)       |
| Grafana            | Prometheus metrics dashboards    | [grafana.happykokoro.com](https://grafana.happykokoro.com)     |
| Gitea              | Self-hosted Git server           | [git.happykokoro.com](https://git.happykokoro.com)             |
| PrivateBin         | Encrypted paste service          | [paste.happykokoro.com](https://paste.happykokoro.com)         |
| Excalidraw         | Collaborative whiteboard         | [draw.happykokoro.com](https://draw.happykokoro.com)           |
| Shlink             | URL shortener                    | [link.happykokoro.com](https://link.happykokoro.com)           |
| Linkding           | Bookmark manager                 | [bookmarks.happykokoro.com](https://bookmarks.happykokoro.com) |
| Syncthing          | File synchronization             | [sync.happykokoro.com](https://sync.happykokoro.com)           |

#### AWS Ireland (eu-west-1) — Trading Bots & MM

| Spec         | Value                                                |
| ------------ | ---------------------------------------------------- |
| **Region**   | Ireland (eu-west-1)                                  |
| **Instance** | t3.medium / 2 vCPU / 4 GB RAM                        |
| **Storage**  | 25 GB gp3 EBS (20 GB free)                           |
| **OS**       | Ubuntu 24.04 LTS                                     |
| **Purpose**  | Polymarket trading bot, MM platform, liquidation bot |

| Service                    | Description                                                                            |
| -------------------------- | -------------------------------------------------------------------------------------- |
| **kokoro-mm**              | Polymarket AMM SaaS — automated market making for binary prediction markets            |
| **kokoro-liquidation-bot** | Multi-chain DeFi liquidation engine — 6 EVM chains + Solana, port 4400                 |
| **polybot** (v5.1)         | Symmetric volatility harvesting bot — BTC/ETH/SOL/XRP, 5-min binary options (STOPPED)  |
| **tick-collector**         | Real-time WebSocket tick collector — price changes, trades, order book diffs (systemd) |

| Repo | [anescaper/My-First-Bot](https://github.com/anescaper/My-First-Bot) |
| ---- | ------------------------------------------------------------------- |

#### AWS London (eu-west-2) — Data & Analysis

| Spec         | Value                            |
| ------------ | -------------------------------- |
| **Region**   | London (eu-west-2)               |
| **Instance** | t3.medium / 2 vCPU / 4 GB RAM    |
| **Storage**  | 30 GB gp3 EBS (12 GB free)       |
| **OS**       | Ubuntu 24.04 LTS                 |
| **Purpose**  | Market data storage and analysis |

| Service       | Description                                                                                                 |
| ------------- | ----------------------------------------------------------------------------------------------------------- |
| **tick-data** | 7 GB SQLite DB — 800K+ price ticks, 1.6M+ order book diffs, 656 rounds across BTC/ETH/SOL/XRP 5-min markets |

### Tech Stack

```
Languages      Rust · TypeScript · Go · Java · PHP · Python · JavaScript · Kotlin · C/C++ · Dart · C# · SQL · Shell
Frontend       Next.js 16 · React 19 · Vite · Tailwind v4 · Radix UI · Framer Motion · Electron · Three.js
Backend        Axum · Actix · Tokio · Gin · Echo · NestJS · Hono · Express · Fastify · FastAPI · Spring
PHP            Laravel · Symfony · ThinkPHP · WordPress · WooCommerce · Drupal · FilamentPHP
Mobile         React Native · Flutter · Expo · Swift/SwiftUI · Kotlin Mobile
Desktop        Tauri · Electron · electron-builder
Blockchain     Solana SDK · Anchor 0.30 · SPL Token · Jupiter · Raydium · Orca · Jito MEV · Go-Ethereum · Polymarket
ZK/Crypto      SNARKs · STARKs · Circom · Noir · zkSync · StarkNet · Polygon zkEVM · MPC
Cloud-Native   Kubernetes · Helm · Istio · Linkerd · Cilium · ArgoCD · Terraform · Envoy · Consul · Vault
Cloud          AWS · GCP · Azure · Alibaba Cloud · DigitalOcean · Cloudflare · Vercel
Enterprise     Spring Ecosystem · Nacos · Sentinel · Seata · Dubbo · Quarkus · GraalVM Native
Databases      PostgreSQL · Redis · MySQL · MongoDB · Elasticsearch · SQLite · SQLx
Search         Elasticsearch · Meilisearch · Typesense · Algolia · OpenSearch
Messaging      Kafka · NATS · RabbitMQ · RocketMQ · Redis Streams
AI/ML          Claude API · MCP Protocol (98 tools) · Claude Code SDK · LangChain · LlamaIndex · Deepgram
MLOps          pgvector · Qdrant · Pinecone · Weaviate · Milvus · RAG pipelines
Staking        Solana Validator · ETH Beacon · Marinade · Jito StakePool · Lido · Stratum · RPC Nodes
WASM/Edge      wasm-pack · wasm-bindgen · wasmtime · Cloudflare Workers · Fastly Compute · Deno Deploy
Quant          nalgebra · ndarray · statrs · rustfft · petgraph · good_lp
Game           Phaser 3 · WebGL/WebGPU · Godot · Unity · Bevy (Rust)
Real-Time      WebRTC · LiveKit · MediaSoup · Socket.io · HLS/DASH
Visualization  TradingView · Recharts · D3.js · Plotly · Chart.js · React Flow
DevOps         Docker · GitHub Actions · Nginx · PM2 · Certbot · SOPS · Harbor
Monitoring     Prometheus · Grafana · OpenTelemetry · Jaeger · SkyWalking · Loki · ELK · Uptime Kuma · Umami
SRE            k6 · Locust · LitmusChaos · Chaos Mesh · SLO/SLI tracking
Low-Code       Retool · Appsmith · n8n · Temporal · Directus
Security       JWT · Argon2 · AES-GCM · ChaCha20 · HMAC · TOTP/2FA · cargo-audit
Testing        cargo test · Vitest · Playwright · pytest · Anchor test · Testing Library
```

---

<sub>12 products · 250+ technologies · 65+ crates · 20 programs · 1118 tests · 98 MCP tools · 28 service categories · 12+ self-hosted apps</sub>
<br/>
<sub>Hosted on DigitalOcean SGP1 · Proxied through Cloudflare · Managed with Docker Compose + PM2</sub>
