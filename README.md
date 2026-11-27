<p align="center">
  <picture>
    <source media="(prefers-color-scheme: dark)" srcset="assets/readme/logo-dark.png">
    <img src="assets/2d.png" width="343" alt="MESA">
  </picture>
</p>

# MESA tool-only baseline

> [!WARNING]
> This repository is the MESA ablation baseline. MESA's research knowledge
> layer has been removed to assess the resulting loss of research capability.
> See [ablation_diagram.md](ablation_diagram.md) for the removed steps and the
> remaining tool paths.

This branch provides Codex skills for computational catalysis modeling, UMA and
VASP calculations, result analysis, plotting, and manuscript writing.

## Setup

From the checkout, ask Codex to run `initialize-mesa`. The skill checks runtimes,
helps install missing dependencies, and links the available skills into Codex.
Use an isolated `CODEX_HOME` when running this checkout alongside full MESA.
See [dependency setup](DEPENDENCY/README.md) for runtime and API-key details.

## Run

Give Codex the scientific question, supplied inputs, calculation backend,
execution limits, and requested output directory. See [workflow.md](workflow.md)
for basic tool use and [SKILL/](SKILL/) for the available skills.

## Citation

The MESA paper is in preparation. A citation will be added here on publication.
