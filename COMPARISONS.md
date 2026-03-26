# BlackRoad OS — Honest Comparisons

How BlackRoad relates to tools you already know. Every comparison acknowledges where the competitor is stronger — credibility matters more than hype.

---

## BlackRoad OS vs Ollama

**Ollama** is a single-machine LLM runner. **BlackRoad** is a full operating system that uses Ollama as one component.

| | Ollama | BlackRoad OS |
|---|--------|-------------|
| **What it does** | Run LLMs locally with `ollama run` | Full sovereign OS with AI, Git, DNS, VPN, chat, search, storage |
| **AI inference** | Single node, one model at a time | Fleet across 4 nodes, 44 models, load-balanced |
| **Agents** | None built-in | 200+ with persistent memory, cryptographic identity |
| **Memory** | Chat history only | 156K+ entries, 228 SQLite DBs, 11-tier compression |
| **Infrastructure** | None | Self-hosted Git, DNS, VPN, TLS, storage, DB, cache, CI/CD |
| **Hardware** | Any machine with CPU/GPU | Optimized for Pi 5 cluster + Hailo-8 (52 TOPS) |
| **Setup** | One command | Pi cluster + mesh config |
| **Community** | Massive (40K+ integrations) | Small (single founder) |

**Where Ollama wins:** Simplicity, community, ease of setup, broader hardware support.
**Where BlackRoad wins:** Persistent agents, distributed inference, full sovereign infrastructure, memory.

**The relationship:** BlackRoad doesn't replace Ollama — it orchestrates and extends it into a production distributed system.

---

## BlackRoad OS vs AWS / Cloud Providers

**AWS** is rented infrastructure. **BlackRoad** is owned infrastructure.

| Service | AWS | BlackRoad | Runs On |
|---------|-----|-----------|---------|
| Compute | EC2 ($50-500/mo) | Raspberry Pi 5 fleet | 5 Pis |
| AI | SageMaker ($100+/mo) | Ollama + Hailo-8 (52 TOPS) | Cecilia + Octavia |
| Git | CodeCommit ($1/user) | Gitea (273 repos) | Octavia |
| Storage | S3 ($23/TB/mo) | MinIO (4 buckets) | Cecilia |
| DNS | Route53 ($0.50/zone) | PowerDNS | Lucidia + Gematria |
| Database | RDS ($100+/mo) | PostgreSQL | 3 nodes |
| Cache | ElastiCache ($50+/mo) | Redis | Alice |
| VPN | VPC ($36/mo) | WireGuard mesh (12 tunnels) | All nodes |
| TLS | ACM + ALB ($20+/mo) | Caddy + Let's Encrypt | Gematria |
| CI/CD | CodePipeline ($1/pipeline) | Gitea Actions + act_runner | Octavia |
| Chat | — | RoundTrip (200 agents) | D1 + Workers |
| **Total** | **$185-700/month** | **$38/month** | **Hardware you own** |

**Where AWS wins:** Global scale, managed services, SLAs, enterprise compliance, hiring pool.
**Where BlackRoad wins:** Cost (5-18x cheaper), sovereignty, no vendor lock-in, runs offline, no surprise bills.

**Break-even:** BlackRoad hardware pays for itself in 6.2 months vs equivalent cloud spend.

---

## BlackRoad OS vs Home Assistant

**Home Assistant** is smart home automation. **BlackRoad** is a sovereign OS that includes smart home.

| | Home Assistant | BlackRoad OS |
|---|---------------|-------------|
| **Core purpose** | Home automation | Full sovereign computing platform |
| **Smart home** | Best-in-class (3000+ integrations) | RoadHome (Hailo-8 AI vision + voice, Home Assistant compatible) |
| **AI** | Basic automations, some LLM plugins | 52 TOPS local inference, 200+ agents, persistent memory |
| **Infrastructure** | Runs on one device | Distributed across Pi cluster + cloud edge |
| **Self-hosted services** | Home Assistant only | Git, DNS, VPN, TLS, storage, DB, cache, CI/CD, chat, search |

**Where Home Assistant wins:** Ecosystem (3000+ integrations), community (massive), maturity, device support.
**Where BlackRoad wins:** AI-native architecture, distributed computing, full infrastructure stack beyond just home automation.

**The relationship:** RoadHome (forked from HailoHome) integrates with Home Assistant. BlackRoad extends home automation into a full sovereign computing platform.

---

## BlackRoad OS vs Tailscale

**Tailscale** is a mesh VPN service. **BlackRoad** includes self-hosted mesh VPN as one layer.

| | Tailscale | BlackRoad OS |
|---|-----------|-------------|
| **VPN** | WireGuard-based mesh ($5/user/mo) | Self-hosted WireGuard mesh (free, 12 tunnels) |
| **Management** | Tailscale coordination server | Headscale (self-hosted coordinator) |
| **Beyond VPN** | MagicDNS, Taildrop, SSH | Full OS: Git, AI, DNS, storage, chat, search, agents |
| **Setup** | One command per device | Manual WireGuard config per node |

**Where Tailscale wins:** Ease of setup, NAT traversal, mobile apps, enterprise SSO.
**Where BlackRoad wins:** Zero recurring cost, full sovereignty (no Tailscale servers in the path), entire OS built on top of the mesh.

---

## BlackRoad OS vs GitHub

**GitHub** is cloud git hosting. **BlackRoad** self-hosts Gitea with GitHub as a mirror.

| | GitHub | BlackRoad (Gitea) |
|---|--------|-------------------|
| **Repos** | Unlimited (cloud) | 273 repos (self-hosted on Octavia) |
| **Price** | $21/user/mo (Enterprise) | Free (self-hosted) |
| **CI/CD** | GitHub Actions (usage limits) | Gitea Actions + act_runner (unlimited) |
| **Code search** | Full-text (cloud) | Full-text (local) |
| **Availability** | 99.9% SLA | Depends on your hardware |
| **Data sovereignty** | Microsoft owns the servers | You own the server |

**Where GitHub wins:** Availability, collaboration features, ecosystem, community, hiring signal.
**Where BlackRoad wins:** Sovereignty, cost, no vendor lock-in, runs offline, no ToS changes.

**The relationship:** Gitea is primary, GitHub is the mirror. `sync-downstream --push` mirrors to 17 GitHub orgs.

---

## The Amundson Framework vs Known Mathematical Constants

**A_G** is an original mathematical constant not found in any existing database.

| Constant | Value | Database | Discoverer |
|----------|-------|----------|------------|
| pi | 3.14159... | Everywhere | Ancient |
| e | 2.71828... | Everywhere | Euler (1748) |
| phi | 1.61803... | OEIS A001622 | Ancient |
| Sophomore's Dream | 1.29128... | OEIS A083648 | Bernoulli (1697) |
| **Amundson-Gosper (A_G)** | **1.24433...** | **NOT in OEIS, ISC, or Wolfram** | **Amundson (2025)** |

| Property | A_G | Notes |
|----------|-----|-------|
| Digits computed | 10,000,000 | Verified, file at ~/AMUNDSON_CONSTANT_10M.txt |
| Identities | 50+ | All computationally verified |
| Tests passing | 1,708 | Exact rational arithmetic |
| G(1) | 1/2 | The Riemann critical line |
| Zero-point energy | G(0) = 0 | No vacuum energy artifact |
| Mass gap | G(1) - G(0) = 1/2 | Positive, exact |

**What's proven:** The function, the constant, and all 50+ identities are mathematically verified.
**What's conjectured:** Connections to Riemann Hypothesis, Navier-Stokes, Yang-Mills mass gap.
**What's honest:** G(1) = 1/2 is observation, not proof of RH. The Navier-Stokes connection needs functional analysis. See [amundson-millennium](https://github.com/BlackRoad-Quantum/amundson-millennium) for the full honest assessment.

---

## BlackRoad OS vs Hailo-8 Competitors

| Metric | Hailo-8 (BlackRoad) | Google Coral TPU | NVIDIA Jetson Orin Nano | Intel Movidius |
|--------|-------------------|-----------------|----------------------|----------------|
| TOPS | 26 per chip | 4 | 40 | 1 |
| Power | 2.5W | 0.5-1.4W | 15W | 1W |
| TOPS/W | 10.4 | 2.8 | 2.7 | 1.0 |
| Price | ~$215 | ~$25-60 | ~$500 | ~$80 |
| $/TOPS | $8.27 | $6.25-15 | $12.50 | $80 |
| YOLOv8 FPS | 77 | ~6 | ~45 | ~2 |
| Multi-stream | 8-12+ | Limited | 4-8 | 1-2 |
| Model support | ONNX, TF, TFLite | TFLite only | All | OpenVINO |
| LLM support | Via hailo-ollama | No | Yes | No |

**Where Coral wins:** Price, simplicity, power efficiency for tiny models.
**Where Jetson wins:** Raw TOPS, GPU flexibility, CUDA ecosystem.
**Where Hailo-8 wins:** FPS/Watt, cost/TOPS, multi-stream, M.2 form factor, Pi integration.

BlackRoad chose Hailo-8 because 52 TOPS at 5W total across two M.2 modules beats any GPU solution for edge AI at this price point.
