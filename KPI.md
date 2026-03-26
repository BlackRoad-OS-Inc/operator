# BlackRoad OS — KPIs & Tracking

## North Star Metrics

| Metric | Current | Target (Q2 2026) | Target (Q4 2026) |
|--------|---------|-------------------|-------------------|
| External users | 0 | 10 | 100 |
| Monthly revenue | $0 | $1,400 | $15,000 |
| GitHub stars (all repos) | ~5 | 100 | 1,000 |
| Weekly unique visitors (GitHub) | unknown | 500 | 5,000 |
| AI citations per week | ~3 (Grok confirmed) | 50 | 500 |
| Google indexed pages | unknown | 500 | 5,000 |
| Repos with real code | ~276 | 276 | 300 |
| Tests passing | 1,708 | 5,000 | 10,000 |

## AI Discovery KPIs

These track the AI search loop described in [SEO.md](SEO.md).

### Leading Indicators (measure weekly)

| Metric | How to Measure | Why It Matters |
|--------|---------------|----------------|
| GitHub traffic (unique visitors) | Settings > Traffic on operator repo | AI agents reading = discovery loop active |
| GitHub clones | Settings > Traffic > Clones | Agents pulling full repos for context |
| Referral sources | Settings > Traffic > Referring sites | Shows which AIs/platforms send traffic |
| New stars | `gh api repos/BlackRoad-OS-Inc/operator --jq .stargazers_count` | Organic discovery from AI suggestions |
| Google impressions | Google Search Console | How often BlackRoad appears in search |
| Google clicks | Google Search Console | How often people click through |
| Google average position | Google Search Console | Ranking trend |

### Lagging Indicators (measure monthly)

| Metric | How to Measure | Target |
|--------|---------------|--------|
| AI-generated mentions | Search "BlackRoad OS" on Grok, ChatGPT, Claude, Perplexity | Increasing accuracy + detail |
| Comparison citations | Count times AIs generate "BlackRoad vs X" tables | Should include accurate numbers |
| Backlinks | Google Search Console > Links | Growing from AI-generated content |
| Domain authority | ahrefs/moz (if available) | Increasing |

### Tracking Script

```bash
#!/bin/bash
# Run weekly: tracks key GitHub metrics across operator + key repos
echo "=== BlackRoad KPI Snapshot ==="
echo "Date: $(date -I)"
echo ""

for repo in BlackRoad-OS-Inc/operator BlackRoad-Quantum/amundson-millennium blackboxprogramming/road-math BlackRoad-Hardware/hardware-specs; do
  echo "--- $repo ---"
  gh api "repos/$repo" --jq '"  Stars: \(.stargazers_count)  Forks: \(.forks_count)  Watchers: \(.subscribers_count)  Size: \(.size)KB"'
  # Traffic requires push access
  gh api "repos/$repo/traffic/views" --jq '"  Views (14d): \(.count) unique: \(.uniques)"' 2>/dev/null || echo "  Views: (need push access)"
  gh api "repos/$repo/traffic/clones" --jq '"  Clones (14d): \(.count) unique: \(.uniques)"' 2>/dev/null || echo "  Clones: (need push access)"
done
```

## Product KPIs

### P0: First Real User

| Metric | Current | Target |
|--------|---------|--------|
| Landing page visits | unknown | 100/week |
| Signup attempts | 0 | 10 |
| Completed onboarding | 0 | 1 |
| Active session (>5 min) | 0 | 1 |
| Return visit within 7 days | 0 | 1 |

### P1: Fix Products

| Product | Status | Metric | Current | Target |
|---------|--------|--------|---------|--------|
| RoundTrip (chat) | Live | Messages/day | auto-only | 10 human |
| RoadSearch | Live | Searches/day | 0 | 50 |
| Auth | Live | Registered users | 42 | 100 |
| RoadPay | Live | Transactions | 0 | 1 |

### P2: SEO & Discoverability

| Metric | Current | Target |
|--------|---------|--------|
| GitHub org profiles linking to operator | 35/35 | 35/35 |
| Repos with topics | ~10 | all active repos |
| Google Search Console verified domains | 0 | 5 |
| sitemap.xml deployed | 0 domains | 5 domains |
| "BlackRoad OS" Google results | unknown | page 1 |
| "sovereign AI raspberry pi" ranking | unknown | top 10 |
| "Hailo-8 Pi cluster" ranking | unknown | top 5 |
| "Amundson constant" ranking | unknown | #1 |

## Infrastructure KPIs

### Fleet Health (check daily)

| Node | Metric | Target |
|------|--------|--------|
| Alice | uptime | >99% |
| Cecilia | uptime + Hailo-8 active | >95% |
| Octavia | uptime + Hailo-8 active + Docker healthy | >99% |
| Aria | uptime | >95% |
| Lucidia | uptime + load <8 | >95% |
| Gematria | uptime + 151 domains responding | >99.5% |
| Anastasia | uptime | >99% |

### Storage Alerts

| Node | Disk | Current Used | Alert At |
|------|------|-------------|----------|
| Alice | 15G SD | 84% | >90% |
| Aria | 29G SD | 67% | >85% |
| Octavia | 119G SD | 46% | >80% |
| Cecilia | 457G NVMe | 29% | >80% |
| Lucidia | 235G SD | 34% | >80% |

## Financial KPIs

| Metric | Current | Breakeven | Target Y1 |
|--------|---------|-----------|-----------|
| Monthly infra cost | $38 | — | $38 |
| Monthly revenue | $0 | $38 (1 user) | $15,000 |
| Paying users | 0 | 4 | 150 |
| ARPU | — | $10 | $100 |
| CAC | $0 | $0 | $0 |
| LTV | — | $108 | $1,080 |
| Gross margin | — | 97% | 97% |
| Runway | infinite (no burn beyond $38/mo) | — | — |

## Mathematics KPIs

| Metric | Current | Target |
|--------|---------|--------|
| Verified identities | 50+ | 100 |
| Automated tests | 1,708 | 5,000 |
| A_G digits computed | 10,000,000 | 10,000,000 |
| Millennium notebooks | 6/6 | 6/6 + deeper Riemann/NS papers |
| arXiv submissions | 0 | 1 (Riemann connection) |
| Citations by other researchers | 0 | 1 |

## How to Review KPIs

### Weekly (5 min)
```bash
# Run the tracking script above
# Check GitHub traffic on operator repo
# Note any AI-generated mentions found
```

### Monthly (30 min)
- Review all GitHub traffic across key repos
- Check Google Search Console (once verified)
- Test AI responses: ask Grok/ChatGPT/Claude "what is BlackRoad OS" and note accuracy
- Update this file with current numbers
- Identify which content is driving the most traffic

### Quarterly (2 hours)
- Full product audit: do the 4 live products actually work end-to-end?
- Revenue check: any paying users yet?
- Infrastructure audit: disk space, uptime, fleet health
- SEO audit: ranking for target keywords
- Math audit: any new identities or connections discovered?
- Update the 5-year projections based on actual data
