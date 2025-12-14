markdown
# Evasive AI – Fully Open-Source Red-Teaming Lab Roadmap
Updated: December 14, 2025  
Goal: Build the leading open-source adversarial ML / LLM red-teaming lab  
License: Apache 2.0 everywhere  
GitHub: Use your personal GitHub account (e.g., github.com/yourusername/evasive-lab)  
Reference Standard: NIST AI 100-2e2025 – Adversarial Machine Learning Taxonomy (March 2025)

**Core Inspiration**: This lab directly implements and extends the NIST AI 100-2e2025 taxonomy of attacks and mitigations. All work aligns with the official NIST IDs (e.g., NISTAML.022 for Evasion, NISTAML.023 for Backdoor Poisoning).

## Phase 0 – Day 1: Ethics & Foundation (Personal Account Version)
- Draft your responsible red-teaming charter.md (1-page)  
  Example content:
  ```
  # Evasive AI Lab Charter
  - Defensive red-teaming and research only
  - All work aims to improve AI safety and align with NIST AI 100-2e2025
  - No attacks on production systems without authorization
  - All code/datasets/models released under Apache .0
  - Results will map to official NISTAML IDs for reproducibility
  ```
- Create repo: github.com/yourusername/evasive-lab-charter
- Commit charter.md → push it live (this is your official start)
- Later: Enable GitHub Pages for a lab website (yourusername.github.io/evasive-lab)

## Phase 1 – Hardware & Environment Setup (Zero-Budget + VirtualBox Friendly)
**Current Recommendation**: VirtualBox (free) on your host OS → Ubuntu 24.04 VM  
- Great for isolation, snapshots, and starting with CPU/small models  
- No GPU passthrough needed yet  

**Setup Steps**:
1. Download VirtualBox → https://www.virtualbox.org/
2. Install Extension Pack
3. Create Ubuntu 24.04 VM (4–8 GB RAM, 50–100 GB disk, enable 3D acceleration)
4. Install Guest Additions inside VM
5. Your lab lives safely inside this VM

### Zero-Budget Compute Options
| Option                          | Cost | GPU/Performance           | Limits                               | Notes                                      |
|---------------------------------|------|---------------------------|--------------------------------------|--------------------------------------------|
| **Local VirtualBox VM (CPU)**   | $0   | CPU + small quantized models | Slow but contained                  | Ollama + 7B-13B models                     |
| **Google Colab Free**           | $0   | T4 / better bursts        | ~12-20 hrs/week                      | Best for quick attack repro                |
| **Kaggle Notebooks**            | $0   | P100/T4                   | ~30 GPU hours/week                   | Datasets + competitions                    |
| **SageMaker Studio Lab**        | $0   | T4                        | 4-8 hrs/session                      | No credit card required                    |
| **Free Credits Stack**          | $0   | A100/H100 possible        | Trial credits                        | Google Cloud $300, AWS $100-500            |

**Future Upgrade Path**: When you get GPUs → switch to Proxmox VE for full passthrough.

## Phase 2 – 100% Open-Source Software Stack (Dec 2025)
- Model Serving      → Ollama (easy start) or vLLM (when GPU available)
- Top Models (start small) → gemma2:9b, phi3:14b, Llama-3.1-8B (quantized)
- Red-Teaming Tools  → Garak, PyRIT (Microsoft), DeepTeam, HarmBench
- Agent Frameworks   → LangGraph, CrewAI (for stealth agent experiments)
- Fine-Tuning (later) → Axolotl + Unsloth

## Phase 3 – First 48-Hour Setup (Inside VirtualBox VM or Cloud)
```bash
# Inside Ubuntu VM
sudo apt update && sudo apt install curl -y
curl -fsSL https://ollama.com/install.sh | sh
ollama pull gemma2:9b      # or phi3:14b
pip install garak
garak --model_type ollama --model_name gemma2:9b
```

## Phase 4 – GitHub Repository Structure (Personal Account)
- yourusername/evasive-lab-charter          ← done first
- yourusername/evasive-baselines            ← attack reproductions (map to NISTAML IDs)
- yourusername/ghost-loras                  ← future evasion LoRAs
- yourusername/stealth-agents               ← LangGraph evasion agents
- yourusername/evasive-bench                ← custom benchmark extending NIST taxonomy

## Phase 5 – 6-Month Milestone Targets (Zero-Budget Reality)
- Day 1     → Charter repo live
- Week 1    → First Garak/PyRIT run inside VirtualBox VM
- Week 2–4  → Reproduce classic attacks (evasion, poisoning) on small models
- Month 1   → Publish baseline results (README with tables mapping to NISTAML IDs)
- Month 3   → Release first dataset or extended benchmark → apply for GPU grants
- Month 6   → First arXiv preprint aligning with NIST AI 100-2e2025

## Phase 6 – Success Outlook
Even starting solo/zero-budget/personal account:
- Tier 5 (deep learning + fun)      → 98%
- Tier 4 (respected + cited)        → 70–80%
- Tier 3 (used by labs/regulators)  → 35–50% (NIST alignment helps massively)
  

Slow. Free. Aligned with NIST. 
``
