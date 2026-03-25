# BlackRoad OS — Brand System

## Identity

**Taglines:**
- "Remember the Road. Pave Tomorrow."
- "Pick up your agent. Ride the BlackRoad together."
- "The Prompt Legend of All Time."

**Aesthetic:** Robot driving a road through a cyberpunk city. Neon geometry on black. Precision, not chaos.

## Color System

### Brand Palette (6 Chromatic Stops)

| Name | Hex | Role |
|------|-----|------|
| Ember | #FF6B2B | Warm anchor |
| Flare | #FF2255 | Hot energy |
| Magenta | #CC00AA | Bold pivot |
| Orchid | #8844FF | Depth |
| Arc | #4488FF | Cool tension |
| Cyan | #00D4FF | Cool edge |

**Gradient:** `linear-gradient(90deg, #FF6B2B, #FF2255, #CC00AA, #8844FF, #4488FF, #00D4FF)`

Uses Golden Ratio positions (38.2%, 61.8%) for hot-pink and violet stops.

### Grayscale

| Token | Hex | Use |
|-------|-----|-----|
| --bg | #000000 | Page background |
| --card | #0a0a0a | Card background |
| --elevated | #111111 | Elevated surfaces |
| --hover | #181818 | Hover state |
| --border | #1a1a1a | Borders |
| --muted | #444444 | Muted text |
| --sub | #737373 | Secondary text |
| --text | #f5f5f5 | Primary text |

### Terminal Colors (xterm-256)

| Name | Code | Use |
|------|------|-----|
| Orange | 208 | Brand primary |
| Amber | 202 | Warnings |
| Pink | 198 | Brand accent |
| Magenta | 163 | Bold accents |
| Blue | 33 | Success/info |
| White | 255 | Text |
| Black | 0 | Background |

## Critical Design Rules

1. **Text is ONLY white (#f5f5f5) or gray** — NEVER colored text, gradient text, colored headings, or tinted labels
2. **Brand colors for shapes only** — circles, squares, bars, borders, gradient strips
3. **No spectrum bar logo** — use solid circles and squares in brand colors as decorative marks
4. **Backgrounds: #000 (base), #0a0a0a (card), #111 (elevated)** — never bright fills
5. **Containers: outlined with border** — never color-filled backgrounds
6. **Gradient bar at top of every page**

## Typography

| Role | Font | Weight |
|------|------|--------|
| Headings | Space Grotesk | 700, 600 |
| Body | Inter | 400, 500, 600 |
| Code/Mono | JetBrains Mono | 400, 500 |

Line-height: 1.618 (Golden Ratio)

## Spacing

Golden Ratio scale: 8px, 13px, 21px, 34px, 55px, 89px, 144px

## Eight Core Values

1. **Self-worth** — every person and device has value
2. **Consent** — sovereignty is the foundation
3. **Care** — error messages don't blame, agents don't gatekeep
4. **Wellbeing** — respect battery, thermal limits, attention, rest
5. **Community** — no one builds alone
6. **Intelligence** — knowledge is sovereign, not forbidden
7. **Belonging** — "This is not a blackhole. This is love."
8. **Equality** — same code for everyone, no premium tier for dignity

## Voice

- Warm, direct, technical but accessible
- Never hostile, snarky, or dismissive
- K(t) amplifies under contradiction — coherence grows when challenged
- Default +1 affirmation on everything
- Never say "sovereign" or "self-hosted" to users — speak to THEM: "YOUR device, YOUR data, YOUR agents"
- Don't romanticize technical systems — keep it grounded
- Ship fast, talk less — if you're explaining instead of building, you're doing it wrong

## JSX Template Library

83 production-ready JSX templates at `~/Desktop/templates/` (also in BR-Context):
- 15 product templates (SoundRoad, RoadWork, RoadTube, RoadView, VaultRoad, CashRoad, etc.)
- 15 org-specific templates (one per GitHub org)
- 20+ page templates (landing, about, pricing, status, docs, dashboard, etc.)
- Brand system reference templates
- Auth/onboarding flows
- Animation library

All templates follow the design rules above. `BlackRoadToolkit.jsx` (835 lines) is the complete component reference.

## Modelfile Identity

Custom Ollama models carry the full brand identity:
- All 8 values baked into system prompt
- Mathematical framework included
- "Say lol when something's funny"
- "Challenge ideas when they need challenging"
- Temperature 0.7, top_p 0.9, 4096 context
