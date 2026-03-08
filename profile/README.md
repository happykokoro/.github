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

**Deep technology studio — quantitative trading, blockchain infrastructure, and AI-native development tools.**

One founder. Three flagship products. 84 Rust crates, 18 Anchor programs, 1032 tests, 98 MCP tools, 5 production services — all self-hosted on a single VPS, proxied through Cloudflare.

[tech.happykokoro.com](https://tech.happykokoro.com) · [happykokoro.com](https://happykokoro.com)

---

### Flagship Products

| Project              | Stack                                        | Description                                                                                                                                                                                                                                                                  | Live                                                         |
| -------------------- | -------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------ |
| **Kokoro Alpha Lab** | Rust · Next.js · Redis · PostgreSQL · Solana | Quantitative alpha framework — 84 CIL crates, 20+ pluggable alpha factors, IMM/RBPF prediction models, Kalman/Fourier/Wavelet/Hilbert signal processing, smart-money wallet clustering, MEV-protected Jito execution, cross-DEX arbitrage (Jupiter/Raydium/Orca), 1032 tests | [alpha.happykokoro.com](https://alpha.happykokoro.com)       |
| **Pipeline Kokoro**  | Rust · TypeScript · React · MCP              | Automated dev pipeline engine — orchestrates parallel Claude Code agents through structured 5-phase workflows (plan → execute → audit → assemble → report), visual pipeline designer with React Flow, 18 skill modules, git worktree isolation, 20 MCP tools                 | [pipeline.happykokoro.com](https://pipeline.happykokoro.com) |
| **Kokoro Protocol**  | Rust · Anchor · Solana · TypeScript          | Fully on-chain DeFi protocol — 18 composable Anchor programs: prediction markets, lending, leveraged positions, yield vaults, constant-product AMM DEX, on-chain governance (DAO), VRF-verified fairness, SPL token integration                                              | —                                                            |

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

Everything runs on one DigitalOcean droplet (2 vCPU · 4 GB RAM · 120 GB disk · SGP1), managed with Docker Compose, PM2, and Nginx.

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

### Tech Stack

```
Languages      Rust · TypeScript · Go · Java · PHP · Python · JavaScript · Kotlin · C/C++ · Dart · C# · SQL · Shell
Frontend       Next.js 16 · React 19 · Vite · Tailwind v4 · Radix UI · Framer Motion · Electron · Three.js
Backend        Axum · Actix · Tokio · Gin · Echo · NestJS · Hono · Express · Fastify · FastAPI · Spring Boot 3
PHP            Laravel · Symfony · ThinkPHP · WordPress · WooCommerce · Drupal · FilamentPHP
Mobile         React Native · Flutter · Expo · Swift/SwiftUI · Kotlin Mobile
Desktop        Tauri · Electron · electron-builder
Blockchain     Solana SDK · Anchor 0.30 · SPL Token · Jupiter · Raydium · Orca · Jito MEV · Go-Ethereum · Polymarket
ZK/Crypto      SNARKs · STARKs · Circom · Noir · zkSync · StarkNet · Polygon zkEVM · MPC
Cloud-Native   Kubernetes · Helm · Istio · Linkerd · Cilium · ArgoCD · Terraform · Envoy · Consul · Vault
Cloud          AWS · GCP · Azure · Alibaba Cloud · DigitalOcean · Cloudflare · Vercel
Enterprise     Spring Cloud Alibaba · Nacos · Sentinel · Seata · Dubbo · Quarkus · GraalVM Native
Databases      PostgreSQL · Redis · MySQL · MongoDB · Elasticsearch · SQLite · SQLx
Search         Elasticsearch · Meilisearch · Typesense · Algolia · OpenSearch
Messaging      Kafka · NATS · RabbitMQ · RocketMQ · Redis Streams
AI/ML          Claude API · MCP Protocol (98 tools) · Claude Code SDK · LangChain · LlamaIndex · Deepgram
MLOps          pgvector · Qdrant · Pinecone · Weaviate · Milvus · RAG pipelines
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

<sub>250+ technologies · 84 crates · 18 programs · 1032 tests · 20+ factors · 98 MCP tools · 5 services · 12+ self-hosted apps</sub>
<br/>
<sub>Hosted on DigitalOcean SGP1 · Proxied through Cloudflare · Managed with Docker Compose + PM2</sub>
