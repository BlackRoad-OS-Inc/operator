# BlackRoad OS — Technical Architecture

## The Sovereignty Stack

BlackRoad replaces every layer of the modern cloud stack with self-hosted infrastructure.

| Service | Self-Hosted On | Replaces |
|---------|---------------|----------|
| Git (273 repos) | Gitea on Octavia | GitHub ($21/user/mo) |
| AI (52 TOPS) | Ollama on 4 nodes | OpenAI ($20+/mo) |
| Workers (15/15) | workerd on Octavia :9001-9015 | Cloudflare Workers |
| Object Storage | MinIO on Cecilia | AWS S3 / CF R2 |
| DNS | PowerDNS on Lucidia + Gematria | Cloudflare DNS |
| PaaS | Deploy API on Octavia :3500 | Railway / Heroku / Vercel |
| Database | PostgreSQL on 3 nodes | AWS RDS / CF D1 |
| Cache | Redis on Alice | AWS ElastiCache / CF KV |
| TLS Edge | Caddy on Gematria (151 domains) | Cloudflare proxy |
| VPN | WireGuard mesh (12/12 tunnels) | Tailscale ($5/user/mo) |
| Chat | RoundTrip (D1) + chat.blackroad.io | Slack ($8.75/user/mo) |
| CI/CD | Gitea Actions + act_runner | GitHub Actions |
| Search | FTS5 + Workers AI | Algolia ($50+/mo) |
| Monitoring | Grafana fork (RoadMap) | Datadog |

**Only external dependencies:** Stripe (card processing), GoDaddy (domain registrar).

## Hardware Fleet

| Node | Device | IP | Role | Key Services |
|------|--------|----|------|-------------|
| Alice | Raspberry Pi 5 | 192.168.4.49 | Gateway | nginx (37 sites), Pi-hole, PostgreSQL, Qdrant, Redis |
| Cecilia | Raspberry Pi 5 | 192.168.4.96 | Inference | Ollama (16 models), MinIO (4 buckets), PostgreSQL, InfluxDB, Hailo-8 (26 TOPS) |
| Octavia | Raspberry Pi 5 | 192.168.4.101 | Platform | Gitea (273 repos), 1TB NVMe, NATS, Docker Swarm, 15 Workers, Hailo-8 (26 TOPS) |
| Aria | Raspberry Pi 5 | 192.168.4.98 | Monitoring | Headscale, Cloudflared, nginx, InfluxDB, Portainer |
| Lucidia | Raspberry Pi 5 | 192.168.4.38 | Apps | 530+ nginx web apps, PowerDNS, Ollama (6 models), GitHub Actions runners |
| Gematria | DO Droplet | NYC3 | Edge | Caddy (151 domains), Ollama (6 models), PowerDNS (ns1), WireGuard hub |
| Anastasia | DO Droplet | NYC1 | Backup | Caddy, WireGuard |

**Compute:** 2x Hailo-8 = 52 TOPS across Cecilia + Octavia
**Network:** Full WireGuard mesh, 12/12 SSH connections, 18 Cloudflare tunnels
**Cost:** $38/month total

## Road Fleet (Sovereign Forks)

12 open-source dependencies forked into Gitea with road names (2.7GB+):

| Road Name | Upstream | Purpose |
|-----------|----------|---------|
| RoadCode | Gitea | Git hosting |
| TollBooth | WireGuard | VPN mesh |
| PitStop | Pi-hole | DNS filtering |
| Passenger | Ollama | AI inference |
| OneWay | Caddy | TLS edge |
| RearView | Qdrant | Vector search |
| Curb | MinIO | Object storage |
| RoundAbout | Headscale | Mesh coordinator |
| CarPool | NATS | Pub/sub messaging |
| OverPass | n8n | Workflow automation |
| BackRoad | Portainer | Container management |
| RoadMap | Grafana | Monitoring |
| GuardRail | Uptime Kuma | Uptime monitoring |

## Network Architecture

```
Internet
    |
    v
Gematria (Caddy TLS, 151 domains, NYC3)
    |
    v (WireGuard tunnel)
    |
    +---> Alice (192.168.4.49) -- Gateway, DNS, DB, Cache, Vector
    +---> Cecilia (192.168.4.96) -- AI Inference, Object Storage
    +---> Octavia (192.168.4.101) -- Git, Workers, PaaS, NATS
    +---> Aria (192.168.4.98) -- Monitoring, Mesh
    +---> Lucidia (192.168.4.38) -- Apps, DNS, CI/CD
    |
    v (failover)
Anastasia (NYC1)
```

All nodes connected via WireGuard mesh. Traffic enters through Gematria's Caddy reverse proxy with auto-TLS (Let's Encrypt), routes through WireGuard to the Pi fleet on the local network.

## Four Infrastructure Rules

1. **Sovereign Computing** — Three layers: CF edge (cache/CDN), your compute (Pi fleet), failover (DO droplets). No single provider can kill us.
2. **Subdomain-Oriented Architecture** — One subdomain = one service. DNS is the router. No monolithic routing tables.
3. **Project = Boundary** — Each deployment is isolated. No shared mega-project.
4. **Isolation is Intentional** — Each agent owns ONE domain. No agent modifies another's domain without approval.

## Service Architecture

| Service | Port | Domain |
|---------|------|--------|
| Web | 3000 | blackroad.io |
| Prism Console | 3001 | prism.blackroad.io |
| Operator | 3002 | ops.blackroad.io |
| API Gateway | 3003 | api.blackroad.io |
| Gitea | 3100 | git.blackroad.io |
| RoundTrip | 8094 | roundtrip.blackroad.io |
| Deploy API | 3500 | deploy.blackroad.io |
| Workers | 9001-9015 | Various subdomains |

Stack: Next.js 14 + TypeScript (web), Python/FastAPI (APIs), Rust (performance), SQLite/PostgreSQL (data).

## Memory System

BlackRoad's memory system is a 156K+ entry knowledge base across 228 SQLite databases (1.5GB total, 1.3M rows).

11-tier compression: 2048 tokens -> 1024 -> 512 -> 256 -> 128 -> 64 -> 32 -> 16 -> 8 -> 4 -> 2 tokens (permanent).

9 memory scripts: journal + chain, codex (solutions/patterns), infinite todos, task marketplace, TIL broadcast, FTS5 indexer, security/audit, collaboration, product registry.

## BlackBox Protocol

Multi-network mesh for censorship-resistant communication:
- **Tor** hidden services live on 3 Pis (reachable globally without public IP)
- **IPFS** for content-addressed storage
- **BitTorrent** DHT for peer discovery
- **WebRTC** for browser-to-browser
- **Bitcoin** OP_RETURN for immutable timestamps

Ternary routing: 1=arrived, 0=waiting, -1=already answered (cancel pending).
Math foundation: n/(1+1/n)^n = n/e + 1/(2e) + O(1/n). The 1/(2e) is the irreducible latency floor.

## AI Infrastructure

- **29 Ollama models** across fleet
- **63 custom Modelfile definitions** (proprietary, production-optimized)
- **50 AI skills** across 6 modules (agentic, generation, orchestration, knowledge, multimodal, frontier)
- **RAG system:** Qdrant on Alice + nomic-embed-text on Cecilia, 32,297 code chunks
- **Model Server v2:** 108 models cataloged (20 live, 9 YOLO on Hailo-8)
- **NATS mesh:** v2.12.3 on Octavia, 4/5 nodes connected, pub/sub agent coordination

### NVIDIA Benchmark Results

BlackRoad's Pi cluster with dual Hailo-8 beats NVIDIA on power efficiency:
- YOLOv8s: 64 FPS/Watt vs NVIDIA Jetson's 4 FPS/Watt (16x better)
- YOLOv6n: 164 FPS/Watt (24x better)
- 5-year TCO: $2,133 vs $67,102 for A100 (31x cheaper)
- 160 concurrent services vs 0 for GPU-only systems

## Cloudflare Resources (Transitioning to Self-Hosted)

- 95+ Pages projects
- 7 D1 databases
- 40+ KV namespaces
- 6 R2 buckets
- Multiple Workers (auth, chat, portal, index, images, api, resume, analytics, prism)

Migration path: D1 -> PostgreSQL, KV -> Redis, R2 -> MinIO, Workers -> workerd, Pages -> nginx.
