# MESA Ablation

To assess the loss of research capability, we removed MESA's research knowledge
layer. This layer covered literature search and interpretation, hypothesis
formulation, strategy generation, procedures for executing strategies and
recording results in a structured form, and evidence-grounded manuscript writing.
We also revised `workflow.md` and related skill guides to remove instructions
for the ablated steps.

## Repository tree

![Repository tree with deleted paths in red, modified paths in blue, and unchanged paths in green](assets/ablation-tree.svg)

## Original workflow with the cuts marked

```mermaid
flowchart TB
    accTitle: Original MESA workflow with ablation cuts
    accDescr: The original workflow links project setup, literature, strategies, recipes, execution management, and manuscript preparation. Cross-ended connections mark dependencies removed by ablation.

    Root["workflow.md<br/>Research entry point"]:::rewritten
    Setup["initialize-mesa<br/>Environment setup"]:::retained
    Startup["initialize-project / start-research<br/>project_profile.md"]:::removed
    Literature["SKILL/literature<br/>Search · download · PDF extraction"]:::removed
    Strategy["SKILL/strategy<br/>Generate · prioritize · select"]:::removed
    Recipe["generate-explicit-calculation-recipe<br/>P procedures · C recipes"]:::removed
    Dispatch["plan-recipe-execution<br/>execution_plan.json · worker delegation"]:::removed
    Tools["Modeling · UMA/VASP · analysis"]:::retained
    Raw["Structures · calculation files · logs"]:::retained
    Records["E/C/P management<br/>Manifests · diagnosis · repair"]:::removed
    Evidence["Manuscript preparation<br/>Evidence digests · figure mapping · citations"]:::removed
    Writing["Manuscript writing<br/>Prose · DOCX · Supporting Information"]:::retained
    Outcome["classify-strategy-outcome<br/>next_run"]:::removed
    Update["update-strategies-from-manuscript<br/>Revised strategy queue"]:::removed

    Root --> Setup
    Root --x Startup
    Startup -- "if evidence is missing" --x Literature
    Startup -- "if a strategy already exists" --x Strategy
    Literature --x Strategy
    Strategy --x Recipe
    Recipe --x Dispatch
    Dispatch --x Tools
    Tools --> Raw
    Raw --x Records
    Records --x Evidence
    Evidence --x Writing
    Records --x Outcome
    Outcome -- "next-run context" --x Recipe
    Writing --x Update
    Update -- "revised queue" --x Strategy

    classDef removed fill:#fce9eb,stroke:#a83249,color:#68172b,stroke-width:2px;
    classDef retained fill:#e4f4ec,stroke:#2d7559,color:#174333;
    classDef rewritten fill:#eaf0ff,stroke:#4865a9,color:#20396d,stroke-width:2px;
```

## Direct tool use in ablation

```mermaid
flowchart TB
    accTitle: Direct tool use after ablation
    accDescr: The task enters a short workflow that preserves environment setup and direct modeling, calculation, analysis, and manuscript writing skills.

    Task["Task brief<br/>Claim · inputs · backend · budget"]
    Root["workflow.md<br/>Direct skill use"]:::rewritten
    Setup["initialize-mesa<br/>Environment setup"]:::retained
    Model["SKILL/modeling<br/>Structures and adsorbates"]:::retained
    Calculation["SKILL/calculation<br/>UMA or VASP"]:::retained
    Raw["Raw outputs<br/>Structures · energies · logs"]
    Analysis["SKILL/analysis and SKILL/figure<br/>Analysis · tables · plots"]:::retained
    Writing["SKILL/manuscript<br/>Writing · figures · references"]:::retained

    Task --> Root
    Root --> Setup
    Root --> Model
    Model --> Calculation --> Raw
    Raw --> Analysis --> Writing
    Raw --> Writing

    classDef retained fill:#e4f4ec,stroke:#2d7559,color:#174333;
    classDef rewritten fill:#eaf0ff,stroke:#4865a9,color:#20396d,stroke-width:2px;
```
