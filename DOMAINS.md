# BlackRoad OS — Domain Portfolio

## 20 Root Domains

All on Cloudflare nameservers. Registered via GoDaddy.

| Domain | Purpose |
|--------|---------|
| **blackroad.io** | Main site, product hub, all product subdomains |
| **blackroad.company** | Corporate, investor relations |
| **blackroad.me** | Personal identity, profiles |
| **blackroad.network** | Agent mesh, device network |
| **blackroad.systems** | Internal ops, fleet status, infrastructure |
| **blackroadai.com** | AI division marketing |
| **blackroadinc.us** | US corporate entity, legal |
| **blackroadqi.com** | Quantum intelligence |
| **blackroadquantum.com** | Quantum computing |
| **blackroadquantum.info** | Quantum research |
| **blackroadquantum.net** | Quantum network |
| **blackroadquantum.shop** | Quantum products |
| **blackroadquantum.store** | Quantum marketplace |
| **lucidia.earth** | Lucidia AI platform |
| **lucidia.studio** | Creative tools |
| **lucidiaqi.com** | Lucidia quantum |
| **roadchain.io** | Blockchain/ledger |
| **roadcoin.io** | Cryptocurrency |
| **blackboxprogramming.io** | Developer brand (archive/legacy) |
| **aliceqi.com** | Alice agent identity |

## Key Subdomains (blackroad.io)

20 subdomains on the primary domain:

| Subdomain | Service |
|-----------|---------|
| app.blackroad.io | Main web application |
| api.blackroad.io | API gateway |
| chat.blackroad.io | RoundTrip chat |
| search.blackroad.io | RoadView search |
| pay.blackroad.io | RoadPay billing |
| auth.blackroad.io | Authentication |
| status.blackroad.io | System status |
| docs.blackroad.io | Documentation |
| prism.blackroad.io | Prism Console |
| hq.blackroad.io | Pixel HQ metaverse |
| roundtrip.blackroad.io | Agent hub |
| git.blackroad.io | Gitea |
| cdn.blackroad.io | CDN |
| images.blackroad.io | Image assets |
| code.blackroad.io | Code editor |
| start.blackroad.io | Getting started |
| dash.blackroad.io | Dashboard |
| os.blackroad.io | OS interface |
| mail.blackroad.io | Email |
| queue.blackroad.io | Job queue |

## Product Subdomains (14 live on blackroad.io)

chat, search, pay, tutor, social, canvas, cadence, roadcode, video, live, game, book, work, radio

## Additional Subdomain Maps

### blackroad.company (7)
ir, board, hr, legal, careers, press, brand

### blackroad.me (5)
profile, id, vault, keys, sso

### blackroad.network (9)
mesh, dns, vpn, nats, nodes, edge, tor, ipfs, wire

### blackroadai.com (10)
models, inference, rag, train, agents, skills, ollama, deepseek, qwen, vllm

### blackroad.systems (7)
Internal ops subdomains

### Other domains
Each has 3-8 subdomains. Total: **126 subdomains** across all 20 domains.

## DNS Architecture

```
User Request
    |
    v
Cloudflare (DNS + CDN + proxy)
    |
    v
Gematria Caddy (TLS termination, 151 domains)
    |
    v (WireGuard tunnel)
    |
    v
Pi Fleet (nginx on Alice/Lucidia, services on all nodes)
```

Primary nameservers: Cloudflare
Secondary: PowerDNS on Lucidia + Gematria (ns1)

Migration path: Moving from Cloudflare DNS to self-hosted PowerDNS for full sovereignty.
