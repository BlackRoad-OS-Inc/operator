# BlackRoad OS — GitHub Enterprise

## Enterprise

**URL:** https://github.com/enterprises/blackroad-os
**Name:** BlackRoad OS, Inc.
**Orgs:** 34 (as of March 2026)

## Organization Hierarchy

```
github.com/enterprises/blackroad-os
  |
  +-- BlackRoad-OS-Inc          (source of truth, corporate, all domain repos)
  |
  +-- BlackRoad-OS              (coordinator for all sub-orgs, core platform)
  |     |
  |     +-- 14 sub-organizations (below)
  |
  +-- 18 additional orgs (AI partnerships, forks, specialized)
```

## All Organizations (34)

### Corporate (Source of Truth)

| Org | Focus | Key Repos |
|-----|-------|-----------|
| **BlackRoad-OS-Inc** | Enterprise root, operator, memory, domains | operator, blackroad, information, 20 domain repos, 12 sovereign forks |
| **BlackRoad-OS** | Core platform, web, API, agents, docs | blackroad-os-web, blackroad-os-api, packs, agents |

### Product Divisions

| Org | Focus | Description |
|-----|-------|-------------|
| **BlackRoad-AI** | Lucidia, Agents, LLM integrations | AI division — models, inference, agent runtime |
| **BlackRoad-Studio** | Canvas, Video, Writing Studio | Creator tools — design, video editing, writing |
| **BlackRoad-Education** | RoadWork, learning platforms | K-12 tutoring, homework, adaptive learning |
| **BlackRoad-Media** | RoadView, RoadTube, streaming | Content distribution, video, audio |
| **BlackRoad-Interactive** | RoadWorld, Genesis Road, games | 3D engine, metaverse, physics simulation |

### Infrastructure

| Org | Focus | Description |
|-----|-------|-------------|
| **BlackRoad-Cloud** | K8s, Terraform, cloud configs | Infrastructure-as-code, deployment |
| **BlackRoad-Security** | Zero-trust, encryption | Auth, Roadblock, security tools |
| **BlackRoad-Gov** | RoadChain governance, policies | Cece protocol, ledger, policy evaluation |
| **BlackRoad-Hardware** | Edge devices, firmware | Pi fleet, Hailo-8, IoT, hardware prototypes |
| **BlackRoad-Network** | Mesh, VPN, P2P | WireGuard, NATS, BlackBox Protocol |

### Research & Corporate

| Org | Focus | Description |
|-----|-------|-------------|
| **BlackRoad-Labs** | Z-framework, PS-SHA-infinity | Research, quantum, experimental |
| **BlackRoad-Foundation** | Open source, public good | Grants, commons, open infrastructure |
| **BlackRoad-Ventures** | Investments, partnerships | Venture operations, deal flow |
| **BlackRoad-Archive** | Historical preservation | Legacy code, backups, historical data |
| **Blackbox-Enterprises** | Sovereign automation forks | Airbyte, ActivePieces, Huginn, Prefect, Temporal forks |

### Specialized / Partner Orgs

| Org | Focus |
|-----|-------|
| **BlackRoad-Agents** | Agent-specific repos and configs |
| **BlackRoad-Forge** | All forked repos (104 forks) |
| **BlackRoad-Sandbox** | Experimental/testing |
| **BlackRoad-Dev** | Developer tools and SDKs |
| **BlackRoad-App** | Application repos |
| **BlackRoad-Data** | Data science, pipelines |
| **BlackRoad-Quantum** | Quantum computing research |
| **BlackRoad-README** | Centralized documentation |
| **BlackRoad-Tech** | Technical infrastructure |
| **BlackRoad-Com** | Communications |
| **BlackRoad-XYZ** | Miscellaneous |
| **BlackRoad-QI** | Quantum Intelligence |

### AI Partnership Orgs

| Org | Focus |
|-----|-------|
| **BlackRoad-Anthropic** | Anthropic/Claude integration |
| **BlackRoad-OpenAI** | OpenAI/GPT integration |
| **BlackRoad-Google** | Google/Gemini integration |
| **BlackRoad-Alphabet** | Alphabet/DeepMind integration |
| **BlackRoad-Nvidia** | NVIDIA/CUDA integration |
| **BlackRoad-X** | X/Grok integration |
| **BlackRoad-xAI** | xAI integration |

## RoadCode Monorepo Structure

Each sub-org gets a `RoadCode` repo with this structure:

```
BlackRoad-OS-Inc/RoadCode/
  Agents/          # Agent identities, prompts, memory, coordination
  Api/             # API servers, endpoints, middleware
  Archive/         # Backup, DR, historical data
  Cli/             # br command, CLI tools, shell scripts
  Config/          # System config, env templates, secrets management
  Core/            # Kernel, runtime, OS primitives
  Data/            # Databases, migrations, seeds, schemas
  Docs/            # Documentation, guides, papers
  Infrastructure/  # Terraform, Docker, nginx, Caddy, WireGuard
  Models/          # AI models, Modelfiles, training data
  Nodes/           # Per-node configs (Alice, Cecilia, Octavia, Aria, Lucidia, Gematria, Anastasia)
  Runtime/         # Process management, cron, daemons, supervisors
  Scripts/         # Memory system, collectors, deployers, fleet tools
  Services/        # Workers, microservices, background jobs
  System/          # Boot, init, health checks, watchdogs
  Tests/           # Integration, unit, e2e, load testing
  Web/             # Frontend templates, static sites, design system
```

## Repository Scale

- **GitHub:** ~509 repos across 34 orgs (~276 active, ~233 archived)
- **Gitea:** 300 repos across 15 orgs (PRIMARY git host, GitHub is mirror)
- **Total code:** ~6.5 million lines
- **Primary languages:** TypeScript, Python, Shell, HTML, Go, C++, Rust

## Enterprise Configuration

- SHA pinning enabled
- 5 rulesets (branch protection, tag protection, sensitive file blocking, agent config)
- 34 .github repos with standardized SECURITY/COC/CONTRIBUTING/CODEOWNERS/templates
- 4 self-hosted runners: octavia-pi, lucidia-pi (arm64), gematria, anastasia (x64)

## Gitea (Primary Git Host)

- **URL:** Octavia :3100
- **Repos:** 273 across 8 orgs
- **Features:** Full-text code search, custom BlackRoad theme, Gitea Actions + act_runner
- **Sync:** `sync-downstream --push` mirrors operator -> 17 GitHub orgs (47 repos)
