# Local LLMs for Agentic Quality Engineering — Research

Can open-source models running on a desktop GPU replace cloud LLMs in enterprise QE automation pipelines?

This repository contains the findings from a practitioner-led experiment testing four open-weight models against Claude Sonnet 4.6 across a six-agent Playwright test automation pipeline.

## The Experiment

**Hardware:** RTX 5060 Ti (16 GB VRAM), AMD Ryzen 7 9700X, 64 GB DDR5, Windows 11 Pro

**Models tested:**
- Devstral Small 2 (24B dense) — 57% on 9-dimension scorecard
- Qwen3.6-35B-A3B (35B MoE, 3B active) — Explorer test only
- Gemma 4 26B-A4B (26B MoE, 4B active) — 54% on 9-dimension scorecard
- Ornith-1.0-9B (9B dense, self-scaffolding RL) — 74% on 9-dimension scorecard

**Pipeline:** Enrichment → Explorer → Builder → Executor → Reviewer → Healer

**Evaluation:** Custom 9-dimension quality scorecard measuring locator quality, wait strategy, test architecture, code quality, maintainability, security, and scenario-to-code fidelity.

## Key Findings

1. **Training methodology beats model size.** Ornith-1.0-9B (9B, 5 GB VRAM) scored 74% — outperforming two models 3× its size (Devstral 24B at 57%, Gemma 4 26B at 54%).

2. **Instruction delivery architecture is an independent variable.** Same model, same scenario: flat instruction files → 5/24 Explorer steps. Skills-based progressive disclosure → 24/24 steps. No benchmark measures this.

3. **Local models hallucinate with confidence.** One model fabricated a Shadow DOM explanation for why it couldn't click a button. Another generated locator files from an unrelated logistics application. More dangerous than failing silently.

## Documents

| Document | Description |
|----------|-------------|
| [Whitepaper (PDF)](whitepaper/Local_LLMs_for_Agentic_QE_Whitepaper_v3.0.pdf) | Full research paper — methodology, results, analysis, and recommendations |
| [LinkedIn Carousel (PDF)](carousel/linkedin-carousel-local-llm-qe.pdf) | 7-slide visual summary of key findings |

## Related

- **[Agentic QE Framework v2](https://github.com/sreevsr/agentic-qe-framework-v2)** — The six-agent Playwright test automation framework used in this experiment
- **[Smart Test Designer](https://github.com/sreevsr/smart-test-designer)** — RAG-powered test scenario generation pipeline

## Author

**Srinidhi Sreevatsa (Srinidhi VSR)**
QE Consultant & Architect · 20+ years in Enterprise Quality Engineering

- LinkedIn: [linkedin.com/in/srinidhi-sreevatsa-tnarasipura](https://linkedin.com/in/srinidhi-sreevatsa-tnarasipura)
- GitHub: [github.com/sreevsr](https://github.com/sreevsr)
- Email: srinidhi.ts@gmail.com

## License

This work is licensed under [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/). You are free to share and adapt this material for any purpose, provided you give appropriate credit.
