# Academic Paper Skills for VS Code Copilot / GitHub Copilot CLI

A port of [academic-paper-skills](https://github.com/yourusername/academic-paper-skills) (originally built for Claude Code) adapted for **GitHub Copilot CLI** and the **VS Code Agent window**.

These skills transform your research ideas into submission-ready manuscripts through structured workflows with quality checkpoints — now usable directly inside VS Code.

## What's Different from the Original

| | Original (Claude Code) | This repo (VS Code / Copilot CLI) |
|--|--|--|
| **Skill location** | `~/.claude/skills/` | `~/.claude/skills/` (same!) |
| **Invocation** | Description-based auto-detect | `/paper-strategist` or `/paper-composer` slash commands + auto-detect |
| **Web search tools** | Exa MCP, Tavily MCP | `web_fetch` + `bash curl` |
| **Script paths** | Relative (`scripts/gap_analysis.py`) | Absolute (`~/.claude/skills/.../scripts/gap_analysis.py`) |
| **Target agent** | Claude Code terminal | VS Code Agent chat window / Copilot CLI |

## Features

- **End-to-End Pipeline**: From initial idea to polished manuscript
- **Evidence-Based Gap Identification**: Every research gap backed by 3-5 citations
- **Platform-Specific Style Learning**: Analyze 8-10 sample papers to extract writing standards
- **Reviewer Simulation**: 7-dimension, 35-point assessment system
- **Quality Assurance**: 3 validation gates + 2 Python verification scripts
- **Preprint Platform Support**: PhilArchive, arXiv, PhilSci-Archive, PsyArXiv, and more

## Two-Skill Workflow

```
┌─────────────────────────────────────────────────────────────┐
│              ACADEMIC-PAPER-STRATEGIST                      │
│  /paper-strategist                                          │
│  Phase 1: Platform Analysis → Target venue + style guide    │
│  Phase 2: Theoretical Framework → Literature + gap analysis │
│  Phase 3: Outline Optimization → Reviewer-assessed outline  │
└─────────────────────────┬───────────────────────────────────┘
                          ↓
                   [Detailed Outline]
                          ↓
┌─────────────────────────┴───────────────────────────────────┐
│               ACADEMIC-PAPER-COMPOSER                       │
│  /paper-composer                                            │
│  Phase 1: Foundation → Style guide + chapter planning       │
│  Phase 2: Systematic Writing → Draft with quality checks    │
│  Phase 3: Polish → Final evaluation + submission prep       │
└─────────────────────────────────────────────────────────────┘
```

## Installation

### Prerequisites
- [GitHub Copilot CLI](https://docs.github.com/en/copilot/how-tos/use-copilot-agents/use-copilot-cli) installed and configured, **or** VS Code with GitHub Copilot Chat extension
- Python 3.8+ (for verification scripts)

### Setup

1. Clone this repository:
```bash
git clone https://github.com/simonpatino/academic-paper-skills-vscode.git
```

2. Copy skills to your Copilot skills directory:
```bash
cp -r strategist ~/.claude/skills/academic-paper-strategist
cp -r composer ~/.claude/skills/academic-paper-composer
```

3. Restart GitHub Copilot CLI (or reload VS Code) to load the skills.

4. Verify installation:
```
/skills
```
You should see `academic-paper-strategist` and `academic-paper-composer` listed.

## Quick Start

### Planning a Paper (Strategist)

```
You: /paper-strategist
     I want to plan a paper on how AI makes people more independent at work

Copilot: [Activates academic-paper-strategist]
         Let me guide you through the three phases...
```

Or just describe it — the skill auto-activates:
```
You: Plan a paper on mortality and consciousness
```

### Evaluating an Existing Paper (Composer)

```
You: /paper-composer evaluate my current paper
     @file:my_paper.tex

Copilot: [Activates academic-paper-composer]
         Running 7-dimension quality assessment...
```

### Writing from Outline (Composer)

```
You: /paper-composer
     Write the paper from this outline: [your outline]

Copilot: [Activates academic-paper-composer]
         Starting Phase 4: Systematic Writing...
```

## How to Provide Your Paper

| Format | How |
|--------|-----|
| **LaTeX (`.tex`)** | `@file:yourpaper.tex` — best option, full structure visible |
| **Markdown (`.md`)** | `@file:yourpaper.md` — works perfectly |
| **Plain text** | Paste directly in chat |
| **PDF** | Convert first: `pdftotext paper.pdf paper.txt`, then `@file:paper.txt` |

## Directory Structure

```
academic-paper-skills-vscode/
├── strategist/
│   ├── SKILL.md                    # Main skill definition (VS Code adapted)
│   ├── references/
│   │   ├── quality_standards.md    # Evaluation criteria
│   │   └── search_strategy.md      # Literature search guide
│   └── scripts/
│       ├── evaluate_samples.py     # Sample paper analyzer
│       └── gap_analysis.py         # Research gap validator
├── composer/
│   ├── SKILL.md                    # Main skill definition (VS Code adapted)
│   ├── references/
│   │   ├── section_guides.md       # Section-by-section guidance
│   │   └── writing_standards.md    # Academic writing principles
│   └── scripts/
│       ├── chapter_quality_check.py    # Per-chapter validation
│       └── final_evaluation.py         # Full manuscript assessment
└── examples/
    ├── consciousness-paper.md      # Example: Philosophy of mind
    └── ai-ethics-paper.md          # Example: AI ethics
```

## Quality Standards

### Reviewer Simulation (7 Dimensions)

| Dimension | Weight | Criteria |
|-----------|--------|----------|
| Originality | 5 pts | Novel contribution to field |
| Argumentation | 5 pts | Logical coherence, evidence support |
| Literature | 5 pts | Comprehensive, current coverage |
| Methodology | 5 pts | Appropriate, rigorous approach |
| Clarity | 5 pts | Accessible, well-structured writing |
| Impact | 5 pts | Potential influence on field |
| Technical | 5 pts | Accuracy, proper citations |

**Threshold**: Outlines scoring ≥28/35 proceed to writing phase.

## VS Code Agent Tips

- Use `@file:yourpaper.tex` to attach your paper for evaluation
- Use `#` to reference GitHub issues if you're tracking paper revisions there
- Skills auto-activate from natural language — no slash command required
- The Python scripts run via `bash` tool — make sure Python 3.8+ is on your PATH

## Use Cases

- **PhD students**: Transform dissertation chapters into publishable papers
- **Independent researchers**: Professional-grade paper planning without institutional support
- **Interdisciplinary work**: Navigate multiple platform requirements
- **Preprint submission**: Prepare manuscripts for PhilArchive, arXiv, etc.
- **Paper review**: Score your draft before submitting to peer review

## Contributing

Contributions are welcome! See [CONTRIBUTING.md](CONTRIBUTING.md) for guidelines.

If you add support for other platforms (Overleaf export, Semantic Scholar, etc.) or improve the scripts, please open a PR.

## Credits

This is a VS Code / Copilot CLI adaptation of the original [academic-paper-skills](https://github.com/yourusername/academic-paper-skills) by **Li Shixiong** (ORCID: [0009-0008-2001-2865](https://orcid.org/0009-0008-2001-2865)), which was built for Claude Code.

Adaptation by **Simón Patiño** — porting to GitHub Copilot CLI / VS Code Agent.

## License

MIT License — see [LICENSE](LICENSE) for details.
