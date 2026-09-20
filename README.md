# stress-dw-legacy

> **⚠️ Superseded** (2026-09-20). This repository is the original university course project for *Base de Datos II* (Database II) at UCC, built with the Hefesto methodology and written in Spanish. It is preserved as-is as the reference the later audit was run against. Its ETL log has entries on 6, 8 and 9 November 2025, and its last commit is dated 13 November 2025 (UTC-3). The tag [`legacy-original`](https://github.com/CarpinetiOctavio/stress-dw-legacy/tree/legacy-original) marks its exact original state (`f2308d2`); this README is the only file added since (`git diff --stat legacy-original..main`). Original repository: [OctavioCarpineti/DW_DB2](https://github.com/OctavioCarpineti/DW_DB2).
>
> It has been superseded by [`stress-dw`](https://github.com/CarpinetiOctavio/stress-dw), a rebuild from scratch on a corrected written specification, not a continuation of this codebase. See [ADR-0000](https://github.com/CarpinetiOctavio/stress-dw/blob/main/docs/decisions/0000-rebuild-from-scratch-instead-of-continuing-legacy.md) for the reasoning and [ADR-0001](https://github.com/CarpinetiOctavio/stress-dw/blob/main/docs/decisions/0001-position-as-portfolio-project.md) for the project's positioning.
>
> **Known limitations** (evidence and status for each are in the ADRs above):
>
> - **Dataset provenance is undocumented by its source.** The data comes from a Kaggle dataset ([bhavikjikadara/mental-health-dataset](https://www.kaggle.com/datasets/bhavikjikadara/mental-health-dataset)) whose metadata states only "I collected this dataset from the internet", with no collection methodology or temporal coverage. Only 7 of its 17 columns have a description. The "2014–2016" label used in this repository derives from the `Timestamp` values, not from any declared coverage. The report also names the source as the "Mental Health in Tech Survey", which contradicts its own occupation categories (students, housewives, etc.).
> - **The report reads two variables differently from the uploader's descriptions.** It reads `treatment` as "currently in treatment" (the description reads "Have you sought treatment for a mental health condition?") and `mental_health_interview` as "participated in a mental-health interview" (the description reads "Would you bring up a mental health issue with a potential employer in an interview?").
> - **Specification defects.** The `Dim_Sintomas` dimension has a grain inconsistency (fan-out), established at the level of the documented schema; quantification against the database is pending. The fact table stores pre-aggregated percentages without numerators or denominators, and the report's sample query averages them without weighting.
> - **Indicators 14–16 do not measure what their names claim** ("unrecognized symptoms", "resources without treatment", "postponement"), as established against the report's own text.
> - **The figures in the report are this project's own outputs and were not independently reproduced.** They should not be read as findings about any population.

## Data

The repository includes the raw input CSV used by the pipeline. The record counts in the ETL log match those of the Kaggle file; byte-level identity is pending verification. The uploader declares the data as CC BY 4.0; no rights over the data are claimed here.

## Contents

The repository is kept for reference and is not maintained or intended to be run.

- `Informe DW/`: the project report (Spanish).
- `python/`: the six ETL scripts.
- `sql/`: database and table creation scripts.
- `config/`, `data/`, `CSV procesado/`, `logs/`: configuration, input and output data, and ETL logs.