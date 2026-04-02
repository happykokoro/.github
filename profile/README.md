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

One founder. 21 repositories. 150K+ lines of code, 85+ Rust crates, 20 Anchor programs, 8 NAPI addons, 116 MCP tools, 12 exchange adapters — self-hosted across 3 servers, proxied through Cloudflare.

[tech.happykokoro.com](https://tech.happykokoro.com) · [happykokoro.com](https://happykokoro.com) · [mm.happykokoro.com](https://mm.happykokoro.com) · [terminal.happykokoro.com](https://terminal.happykokoro.com)

---

### Product Portfolio

| Status      | Project                    | Stack                                                 | Description                                                                                                                                                                                                                                          |
| ----------- | -------------------------- | ----------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 🟡 Dev      | **Kokoro Terminal**        | TypeScript · Bun · Rust NAPI · WebGL · Solidity       | Professional crypto market data terminal — 9 exchange adapters, orderbook heatmap, footprint, VPVR/TPO/CVD, 8 Rust NAPI compute units, trade execution, AI copilot, backtesting, smart contract vault, Polymarket, strategy marketplace, multi-asset |
| 🟢 Live     | **Kokoro Alpha Lab**       | Rust · Next.js · Redis · PostgreSQL · Solana          | Quantitative alpha framework — 65+ crates, CIL architecture, multi-asset (Solana, Polymarket, equities, forex, options), Copilot + Market Intel APIs, MEV-protected Jito execution                                                                   |
| 🟢 Live     | **Kokoro MM**              | Rust · Next.js · PostgreSQL · Redis · Alloy           | Polymarket AMM SaaS — multi-tenant, 18 crates, 69 API routes, CTF minting, 4 quoting strategies (A-S, signal-skewed, laddered, manual), EIP-712 signing, billing integration                                                                         |
| 🟢 Live     | **Pipeline Kokoro**        | TypeScript · React · MCP                              | Automated dev pipeline engine — orchestrates Claude Code agents through 5-phase workflows, visual pipeline designer, 19 skill modules, 20 MCP tools                                                                                                  |
| 🟢 Live     | **Kokoro Staking**         | Go · Next.js · PostgreSQL · Redis                     | Multi-chain staking aggregator — 17 chain adapters, SIWE auth, validator explorer, portfolio dashboard, ETH/SOL staking execution                                                                                                                    |
| 🟢 Live     | **Kokoro VPN**             | Rust · Axum · WireGuard · Tauri v2 · Terraform        | Self-hosted WireGuard VPN platform — client VPN (hub-and-spoke) + mesh VPN (full-mesh server interconnect), Rust API, CLI tool, Tauri desktop app, firewall ACLs, Prometheus metrics                                                                 |
| 🟢 Deployed | **Kokoro Liquidation Bot** | Rust · Alloy · Foundry · Solidity                     | EVM liquidation bot — 4 protocols (Aave V3, Seamless, Compound V3, Moonwell) across 6 chains, Flashbots MEV protection, on-chain FlashLiquidator contract, mempool oracle                                                                            |
| 🟢 Deployed | **Kokoro Protocol**        | Rust · Anchor · Solana · TypeScript                   | Fully on-chain DeFi protocol — 20 Anchor programs, 11 game types: prediction markets, lending, leveraged positions, yield vaults, AMM DEX, DAO governance, VRF fairness                                                                              |
| 🔵 Built    | **Kokoro Pay**             | Rust · Next.js · Solana · PostgreSQL                  | Crypto payment gateway — USDC/SOL monitoring, automated license activation, multi-tenant SaaS, AES-GCM encrypted storage                                                                                                                             |
| 🔵 Built    | **Kokoro Copy Trader**     | Python · Docker · Redis · Solana                      | Solana copy trading bot — smart-money wallet tracking, automated position mirroring, risk management, paper trading mode                                                                                                                             |
| 🟡 Dev      | **Kokoro Agent Platform**  | Rust · TypeScript · React · MCP · Docker              | Hosted AI development agent platform — multi-agent orchestration, visual pipeline designer, team collaboration, subscription tiers                                                                                                                   |
| 🟡 Dev      | **MCP Marketplace**        | TypeScript · MCP SDK · Zod · Next.js · Stripe         | Marketplace for packaged MCP tool servers — themed packs for trading, blockchain, DevOps, one-command install                                                                                                                                        |
| ⚪ Planned  | **Kokoro Stack**           | Docker · Nginx · Shell · Go                           | One-click self-hosted infrastructure kit — 12+ pre-configured services, auto SSL, backup scripts                                                                                                                                                     |
| ⚪ Planned  | **Kokoro Validator**       | Rust · TypeScript · Next.js · PostgreSQL · Prometheus | B2B validator monitoring SaaS — multi-chain fleet management, SLA tracking, slashing alerts, white-label option                                                                                                                                      |

### Ecosystem Services

| Service                       | Stack                                | Description                                                                                                                                                                                                |
| ----------------------------- | ------------------------------------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **kokoro-alpha-lab-frontend** | Next.js 16 · React 19 · Tailwind v4  | Real-time trading dashboard — TradingView charts, factor analytics, canvas strategy builder, Kalman overlays, Solana wallet integration, 6 charting libraries (D3, Recharts, Plotly, Chart.js, React Flow) |
| **lab-mcp**                   | TypeScript · MCP SDK · Zod           | MCP server exposing 116 tools for AI-native interaction with the Alpha Lab — signals, factors, backtests, engine control, Polymarket, admin, artifacts, quant tools                                        |
| **kokoro-wallet-monitor**     | Rust · Tokio · Solana                | Standalone wallet monitoring — real-time swap detection, Louvain graph clustering, Redis Streams output                                                                                                    |
| **kokoro-pricing-service**    | Rust · Axum · Solana                 | Multi-DEX pricing aggregation — Jupiter, Raydium, Orca with order flow imbalance metrics                                                                                                                   |
| **kokoro-auth**               | TypeScript · Bun · Hono · PostgreSQL | Unified SSO service — RS256 JWT, argon2id, TOTP 2FA, per-product subscriptions, cross-product API keys, OIDC for internal tools                                                                            |
| **kokoro-terminal**           | TypeScript · Bun · Rust NAPI · Hono  | Terminal data + compute backend — data-ingest (12 exchange adapters), api-gateway (40+ REST endpoints, WebSocket hub), 8 sealed Rust NAPI compute units                                                    |
| **kokoro-services**           | Docker Compose · Nginx               | Infrastructure-as-code — Docker service definitions, nginx configs, deployment guides, runbooks for all self-hosted services                                                                               |

### Developer Tools

| Project             | Stack                           | Description                                                                                                                                                                                           |
| ------------------- | ------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **agent-orchestra** | Python FastAPI · SQLite         | Multi-agent orchestrator — parallel Claude Code agents in isolated git worktrees, GM pipeline (launch → wait → analyze → merge → build → test), human-in-the-loop approval gates, real-time dashboard |
| **claude-init**     | Python (zero deps)              | CLI tool for bootstrapping Claude Code projects — detects language/framework, generates CLAUDE.md, settings, agents, skills, and commands                                                             |
| **ai-roundtable**   | FastAPI · React/TS · Claude API | Multi-agent AI debate system — 5 specialized agents + arbitrator discuss software design, generate SRS/SDD/TestPlan/ADR documents                                                                     |

### Websites

| Project         | Stack                               | Description                                                                                         | Live                                                 |
| --------------- | ----------------------------------- | --------------------------------------------------------------------------------------------------- | ---------------------------------------------------- |
| **happykokoro** | Next.js 15 · Payload CMS 3 · SQLite | Personal portfolio & blog with layout builder, draft preview, SEO, Lexical rich text, and dark mode | [happykokoro.com](https://happykokoro.com)           |
| **kokoro-tech** | Next.js 16 · Tailwind v4            | Kokoro Tech company website — projects, services, technology stack, capabilities showcase           | [tech.happykokoro.com](https://tech.happykokoro.com) |

### Self-Hosted Infrastructure

3 servers across DigitalOcean and AWS, managed with Docker Compose, PM2, Nginx, and Caddy.

#### DigitalOcean SGP1 — Main Services & Trading

| Spec        | Value                                                     |
| ----------- | --------------------------------------------------------- |
| **Region**  | Singapore (SGP1)                                          |
| **IP**      | 167.172.70.15                                             |
| **Specs**   | 4 vCPU / 8 GB RAM / 120 GB SSD                            |
| **OS**      | Ubuntu 24.04 LTS                                          |
| **Purpose** | Web services, dashboards, trading bots, self-hosted tools |
| **Proxy**   | Cloudflare                                                |

**Utility Services**

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

**Applications & Trading Bots**

| Service                     | Description                                                                           | URL                                                              |
| --------------------------- | ------------------------------------------------------------------------------------- | ---------------------------------------------------------------- |
| **Kokoro Alpha Lab**        | Quantitative alpha framework — lab, engine, platform, MCP, monitoring (11 containers) | [alpha.happykokoro.com](https://alpha.happykokoro.com)           |
| **Kokoro Liquidation Bot**  | Multi-chain DeFi liquidation engine — port 4400                                       | —                                                                |
| **Kokoro Terminal**         | Market data terminal — data-ingest, api-gateway, 9 exchange WebSocket feeds           | [terminal.happykokoro.com](https://terminal.happykokoro.com)     |
| **Kokoro Auth**             | Unified SSO — authentication, subscriptions, OIDC                                     | — (internal :4050)                                               |
| **Kokoro Protocol Backend** | On-chain protocol backend — Solana RPC integration                                    | [protocol.happykokoro.com](https://protocol.happykokoro.com)     |
| **Kokoro Staking**          | Multi-chain staking aggregator                                                        | [staking.happykokoro.com](https://staking.happykokoro.com)       |
| **Kokoro Tech**             | Company website (static export)                                                       | [tech.happykokoro.com](https://tech.happykokoro.com)             |
| **Pipeline Kokoro**         | AI development pipeline engine                                                        | [pipeline.happykokoro.com](https://pipeline.happykokoro.com)     |
| **AI Roundtable**           | Multi-agent AI debate system                                                          | [roundtable.happykokoro.com](https://roundtable.happykokoro.com) |

#### AWS Ireland (eu-west-1) — Market Making

| Spec         | Value                         |
| ------------ | ----------------------------- |
| **Region**   | Ireland (eu-west-1)           |
| **Instance** | t3.medium / 2 vCPU / 4 GB RAM |
| **Storage**  | 25 GB gp3 EBS (7 GB free)     |
| **OS**       | Ubuntu 24.04 LTS              |
| **Purpose**  | Polymarket AMM platform       |

| Service       | Description                                                 | URL                                              |
| ------------- | ----------------------------------------------------------- | ------------------------------------------------ |
| **kokoro-mm** | Polymarket AMM SaaS — app, PostgreSQL, Redis (3 containers) | [mm.happykokoro.com](https://mm.happykokoro.com) |

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
Blockchain     Solana SDK · Anchor 0.30 · SPL Token · Jupiter · Raydium · Orca · Jito MEV · Alloy · Polymarket
ZK/Crypto      SNARKs · STARKs · Circom · Noir · zkSync · StarkNet · Polygon zkEVM · MPC
Cloud-Native   Kubernetes · Helm · Istio · Linkerd · Cilium · ArgoCD · Terraform · Envoy · Consul · Vault
Cloud          AWS · GCP · Azure · Alibaba Cloud · DigitalOcean · Cloudflare · Vercel
Enterprise     Spring Ecosystem · Nacos · Sentinel · Seata · Dubbo · Quarkus · GraalVM Native
Databases      PostgreSQL · Redis · MySQL · MongoDB · Elasticsearch · SQLite · SQLx
Search         Elasticsearch · Meilisearch · Typesense · Algolia · OpenSearch
Messaging      Kafka · NATS · RabbitMQ · RocketMQ · Redis Streams
AI/ML          Claude API · MCP Protocol (116 tools) · Claude Code SDK · LangChain · LlamaIndex · Deepgram
MLOps          pgvector · Qdrant · Pinecone · Weaviate · Milvus · RAG pipelines
Staking        Solana Validator · ETH Beacon · Marinade · Jito StakePool · Lido · Stratum · RPC Nodes
WASM/Edge      wasm-pack · wasm-bindgen · wasmtime · Cloudflare Workers · Fastly Compute · Deno Deploy
Quant          nalgebra · ndarray · statrs · rustfft · petgraph · good_lp
Game           Phaser 3 · WebGL/WebGPU · Godot · Unity · Bevy (Rust)
Real-Time      WebRTC · LiveKit · MediaSoup · Socket.io · HLS/DASH
Visualization  TradingView · Recharts · D3.js · Plotly · Chart.js · React Flow
DevOps         Docker · GitHub Actions · Nginx · Caddy · PM2 · Certbot · SOPS · Harbor
Monitoring     Prometheus · Grafana · OpenTelemetry · Jaeger · SkyWalking · Loki · ELK · Uptime Kuma · Umami
SRE            k6 · Locust · LitmusChaos · Chaos Mesh · SLO/SLI tracking
Low-Code       Retool · Appsmith · n8n · Temporal · Directus
Security       JWT · Argon2 · AES-GCM · ChaCha20 · HMAC · TOTP/2FA · WireGuard · cargo-audit
Testing        cargo test · Vitest · Playwright · pytest · Anchor test · Testing Library
```

---

<sub>21 repos · 150K+ lines · 85+ crates · 8 NAPI addons · 20 programs · 116 MCP tools · 12 exchanges · 3 Solidity contracts · 30+ containers</sub>
<br/>
<sub>3 servers across DigitalOcean & AWS · Proxied through Cloudflare · Managed with Docker Compose + PM2 + Caddy</sub>
