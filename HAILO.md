# BlackRoad OS — Hailo-8 AI Acceleration

## Overview

BlackRoad OS runs 2x Hailo-8 M.2 AI accelerators across the Pi fleet, providing 52 TOPS of neural compute for $38/month total infrastructure. This replaces cloud AI inference (OpenAI, Anthropic, Google) with sovereign, local-first processing.

## Hardware

| Node | Hailo-8 | TOPS | Interface | Case |
|------|---------|------|-----------|------|
| Cecilia | Yes | 26 | M.2 PCIe Gen3 | Pironman 5-MAX |
| Octavia | Yes | 26 | M.2 PCIe Gen3 | Pironman 5-MAX |
| **Total** | **2 chips** | **52 TOPS** | | |

Device path: `/dev/hailo0` on both nodes (verified 2026-03-25)

## Hailo-8 Specs

- **Performance:** 26 TOPS (INT8) per chip
- **Power:** ~2.5W typical, ~8.25W max (3+ TOPS/W efficiency)
- **Memory:** Fully integrated on-chip (no external DRAM)
- **Architecture:** Dataflow/tensor-centric (not von Neumann)
- **Interface:** PCIe Gen3 x2/x4, M.2 2280 B+M key
- **Size:** Smaller than a penny
- **Temperature:** Industrial range (-40C to 85C)
- **Price:** ~$215/module

## Why Hailo-8 (Not GPU)

| Metric | Hailo-8 (BlackRoad) | NVIDIA Jetson Orin Nano | NVIDIA A100 |
|--------|-------------------|----------------------|-------------|
| TOPS | 26 per chip | 40 | 624 (FP8) |
| Power | 2.5W | 15W | 300W |
| TOPS/W | 10.4 | 2.7 | 2.1 |
| Cost | $215 | $500 | $15,000+ |
| $/TOPS | $8.27 | $12.50 | $24.04 |
| Form factor | M.2 module | SOM | PCIe card |

BlackRoad's benchmarks (from BLACKROAD_VS_NVIDIA_BENCHMARK_RESULTS.md):
- YOLOv8s: **64 FPS/Watt** vs Jetson's 4 FPS/Watt (16x better)
- YOLOv6n: **164 FPS/Watt** (24x better than Jetson)
- 5-year TCO: **$2,133** vs $67,102 for A100 (31x cheaper)
- Concurrent services: **160** vs 0 for GPU-only

## How It Works in BlackRoad

```
User query / sensor input
    |
    v
Ollama (model selection + tokenization)
    |
    v
Hailo-8 NPU (matrix math, tensor operations)
    |
    v
Result (< 20ms latency for vision, ~100ms for small LLMs)
```

### Model Pipeline

1. **Compile:** Convert ONNX/TensorFlow model via Hailo Dataflow Compiler -> HEF binary
2. **Load:** HailoRT streams data over PCIe to the chip
3. **Infer:** Dataflow architecture runs entire neural graph in hardware
4. **Return:** Results back to Ollama/application

### Multi-Model Capability

One Hailo-8 handles 8-12+ simultaneous video streams (YOLOv8 object detection). Both chips together support the full BlackRoad agent fleet:
- Vision models (YOLO, face recognition, object detection)
- Embedding models (nomic-embed-text for RAG)
- Small LLMs (quantized to INT8)
- Audio models (wake word, STT)

## Integration Points

### With Ollama
Ollama routes inference to Hailo-8 via hailo-ollama (C++ HailoRT backend). Models load once, persist in chip memory.

### With RoadHome (Smart Home)
Hailo-8 powers real-time vision: person detection, face recognition, object tracking — all locally, no cloud cameras.

### With the Macro-Quantum Stack
The Hailo-8's dataflow architecture is a tensor processor that evolves probability fields (state spaces) in parallel. In BlackRoad's quantum computing framework, it serves as the "state evolution engine."

## Current Status (2026-03-25)

- Cecilia: Hailo-8 confirmed (`/dev/hailo0`), online, booting from NVMe
- Octavia: Hailo-8 confirmed (`/dev/hailo0`), 34.5C, running 7 Docker containers
- Both PCIe bridges verified via `lspci`:
  - ASMedia ASM1182e 2-Port PCIe switch
  - Hailo Technologies Ltd. Hailo-8 AI Processor (rev 01)

## What's Next: Hailo-10H

Hailo's next-gen chip (Hailo-10H) adds GenAI focus:
- Optimized for LLM inference (larger context, better FP16)
- Expected 40+ TOPS
- Same M.2 form factor
- Drop-in upgrade for Pironman cases

When available, upgrading Cecilia + Octavia to Hailo-10H would give BlackRoad 80+ TOPS of LLM-optimized inference.
