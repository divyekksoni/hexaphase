# References & Credits

Hexaphase is an original framework by Divyek Soni, but it stands on the work of others. This page credits the ideas Hexaphase builds on and lists sources for further reading.

If Hexaphase builds on your work and you are not listed, or you know a source others should read, please [open an issue](https://github.com/divyekksoni/hexaphase/issues).

---

## Software process foundations

| Source | What Hexaphase takes from it |
|---|---|
| Royce, W. W. (1970). *Managing the Development of Large Software Systems.* Proceedings of IEEE WESCON. | The classic phase-based lifecycle behind the six numbered phases |
| Beck, K. et al. (2001). *Manifesto for Agile Software Development.* https://agilemanifesto.org | Working in short cycles and going back to earlier phases when needed |
| Schwaber, K. & Sutherland, J. (2020). *The Scrum Guide.* https://scrumguides.org | A short framework definition maintained by its authors, with clear roles and events |
| Nygard, M. (2011). *Documenting Architecture Decisions.* https://cognitect.com/blog/2011/11/15/documenting-architecture-decisions | Decision records, the basis of the Decisions Log in `project-health.md` |

## AI-assisted development

| Source | Relevance |
|---|---|
| Karpathy, A. (2025, February). Post introducing the term "vibe coding" on X. | Names the improvised, prompt-driven style of AI development that Hexaphase adds structure to |
| AGENTS.md, an open format for AI agent instruction files. https://agents.md | Related convention. Hexaphase's `ai-instructions.md` plays the same role in a tool-agnostic way |
| `CLAUDE.md` (Claude Code) and `GEMINI.md` (Gemini CLI) context files | Tool-specific pointer files that Hexaphase uses to load `ai-instructions.md` |

## Research methodology

| Source | Relevance |
|---|---|
| Baltes, S., Angermeir, F., Arora, C., Muñoz Barón, M., Chen, C., Böhme, L., Calefato, F., Ernst, N., Falessi, D., Fitzgerald, B., Fucci, D., He, J., Treude, C., Kalinowski, M., Lambiase, S., Russo, D., Lungu, M., Martinez Montes, C., Prechelt, L., Ralph, P., van Tonder, R. & Wagner, S. (2026). *Guidelines for Empirical Studies in Software Engineering involving Large Language Models.* Empirical Software Engineering (accepted manuscript). [PDF](https://assets.empirical-software.engineering/pdf/emse26-llm-guidelines.pdf) | The Hexaphase evaluation follows these guidelines for reporting the model and configuration, system and prompt design (including agent context files), session traces, repeated runs, and limitations |

## Related approaches

Other structured methods for AI-assisted development. They are listed for comparison and further reading, not as dependencies.

| Approach | Focus |
|---|---|
| GitHub Spec Kit. https://github.com/github/spec-kit | Spec-driven development workflow |
| AWS AI-Driven Development Lifecycle (AI-DLC) | Enterprise lifecycle methodology for AI-driven development |
| BMAD Method | Multi-agent role personas for AI development |

---

## Citing Hexaphase

To credit Hexaphase itself, see [Attribution](README.md#attribution) or use [CITATION.cff](CITATION.cff) (GitHub's "Cite this repository" button).
