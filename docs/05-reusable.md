---
layout: default
title: "05 - Reusable"
parent: Workshop Modules
nav_order: 5
description: "FAIR Reusability, provenance, research software, licensing, and reproducible biomedical workflows."
---

# Can Someone Build on Your Research?

> Could another scientist use your data, code, and documentation to evaluate your results, understand their limitations, and responsibly pursue a new research question?

In our previous module, we explored **Interoperability**: how research objects 
can be represented and linked so different people and computational systems 
can exchange and interpret them. 

**Reusability** asks what someone needs to *understand the origin, meaning, limitations, and conditions of use* 
of those research objects before building upon them.

FAIR does not certify that data are correct or suitable for every analysis. 
Rich documentation helps researchers *assess* fitness for reuse; scientific 
validation remains essential. 

<p align="center">
  <img
    src="{{ '/assets/05_Reusable_SubPrinciples.png' | relative_url }}"
    alt="Reusable Sub-principles"
    style="width: 100%; height: auto;"
  /><br>
</p>

**Think of R1 as the overarching goal:** supply rich, accurate context for reuse. 
The three sub-principles emphasize particularly important aspects of that context. 
R1 is also primarily about instituting good documentation practicies throughout the research data lifecycle. 
Good documentation must describe the *actual* data, methods, decisions, and conditions of reuse.

### F2 and R1 Similarity

<p align="center">
  <img
    src="{{ '/assets/05_Reusable_F2_vs_R1_Shopping.png' | relative_url }}"
    alt="F2 vs R1 Shopping Analogy"
    style="width: 100%; height: auto;"
  /><br>
</p>

The Core Distinction: **Discovery vs. Trust**. To put it simply, 

- F2 is for the Search Engine (Discovery): F2 asks, "What metadata does a 
catalog or search engine need so a human or machine can find this dataset in the first place?"
- R1 is for the Scientist (Context & Trust): Once you have found and downloaded 
the dataset, R1 asks, "What metadata does a researcher need to actually understand, 
trust, and integrate this data into a new analysis?"


### A useful distinction: reproducibility vs. reusability

- **Reproducibility:** Can someone recreate a reported result using the specified inputs, code, and environment?
- **Reusability:** Can someone understand the research object and determine whether and how it can be used for a different purpose?

These overlap, but they are not identical. A fully documented workflow may still 
require controlled-access inputs; a runnable script may still be scientifically 
inappropriate for a new cohort.

<p align="center">
  <img
    src="{{ '/assets/05_Reusable_Reusability_Replicability_Reproducibility.png' | relative_url }}"
    alt="Compare Reusability_Replicability_Reproducibility"
    style="width: 100%; height: auto;"
  /><br>
</p>


## Research software is a research object, too

Biomedical research increasingly depends on scripts, notebooks, pipelines, 
packages, and computational environments. The ARDC webinar explicitly extends 
its discussion beyond datasets to **FAIR software** and points to the 
[FAIR principles for research software](https://doi.org/10.3233/DS-190026).

Software is not just another static data file: it executes, has dependencies, 
changes over time, and may behave differently across environments. 
The broader [FAIR4RS principles](https://doi.org/10.15497/RDA00068) 
adapt FAIR thinking specifically to research software.

### <span style="color: green;">Standardizing code and data management practices as part of a lab manual</span>

Imagine a lab manual that establishes these shared practices.
Here is an example of a lab manual that is a living document of software approach in an Epidemiology lab: [Jade Benjamin-Chung, Stanford](https://github.com/jadebc/lab-manual)

Essentially standard practice empowers research workflows to live beyond the immediate data use.


| Lab practice | How it supports reuse |
|:--|:--|
| Consistent folder layout: `data/raw/`, `data/processed/`, `scripts/`, `results/` | Makes inputs, code, and outputs easier to locate and distinguish. |
| `README.md` describing the study, files, and execution steps | Gives a new lab member the context to understand the analysis. |
| `environment.yml`, `requirements.txt`, or a lockfile | Documents software dependencies and versions. |
| Git version control and tagged releases | Helps identify exactly which code produced a result. |
| Standard variable names and data dictionaries | Reduces ambiguity when data are reused by another project. |
| Explicit handling of missing values and QC exclusions | Prevents hidden analytical assumptions. |
| Tests, validation checks, and expected outputs | Helps detect errors and assess whether the workflow still behaves as intended. |
| Instructions for permitted sharing and sensitive-data handling | Makes responsible reuse possible without exposing restricted data. |

A lab manual is not itself a FAIR practice. However, it is a tool that makes reusable practices repeatable across projects and people.

### Reusable Computational Research Workflows

Research studies typically accumulate folders containing analysis scripts, outputs, and possibly raw data files making up the study generation workflow.
Workflows account for the bulk of the research output and therefore is considered a useful avenue for FAIRification.

A more reusable project might look like:

```
0-run-project.sh
0-config.R
0-functions/
    0-base-functions.R
    0-plot-functions.R
    ...
1 - Data-Management/
    0-prep-data.sh
    1-prep-cdph-fluseas.R
    2-prep-absentee.R
    ...
2 - Analysis/
    0-run-analysis.sh
    1 - Absentee-Mean/
        1-absentee-mean-primary.R
        2-absentee-mean-negative-control.R
        ...
    2 - Absentee-Positivity-Check/
    3 - Absentee-P1/
    4 - Absentee-P2/
3 - Figures/
    0-run-figures.sh
    ...
4 - Tables/
    0-run-tables.sh
    ...
5 - Results/
    1 - Absentee-Mean/
        1-absentee-mean-primary.RDS
        2-absentee-mean-negative-control.RDS
    ...
.gitignore
.Rproj

```
Borrowed from [Jade Benjamin Chung Lab Manual Chapter 7](https://jadebc.github.io/lab-manual/code-repositories.html)

**Ultimately, FAIR has the power to boost reusability in research workflows.**


<p align="center">
  <img
    src="{{ '/assets/05_Reusable_FAIR_Software_Workflows.png' | relative_url }}"
    alt="FAIR_Software_Workflows"
    style="width: 100%; height: auto;"
  /><br>
</p>

Adapted from [Jade Benjamin Chung Lab Manual Chapter 4](https://jadebc.github.io/lab-manual/reproducibility.html)

## Provenance: the research object's history

**Provenance** is the documented history of where a research object came from 
and how it was generated, processed, and changed. 

A useful analogy is **a laboratory chain-of-custody and experimental notebook for digital research**. 
If a result changes, you want to know which input, processing step, parameter, 
or software version might explain the difference.

### Example: from raw sequencing data to a result


<p align="center">
  <img
    src="{{ '/assets/05_Reusable_FASTQ_Provenance.png' | relative_url }}"
    alt="FAIR_Software_Workflows"
    style="width: 100%; height: auto;"
  /><br>
</p>


To make this workflow reusable, record:

- **Inputs:** identifiers, file versions, reference genome/build, sample identifiers.
- **Activities:** processing steps, methods, parameters, exclusions, and QC decisions.
- **Agents:** people, instruments, scripts, software tools, or services responsible for steps.
- **Outputs:** generated files, their versions, and links back to inputs.
- **Timing:** when data were generated and when processing occurred.

### Going one level deeper: W3C PROV

W3C PROV provides concepts for expressing provenance in structured, machine-interpretable form (usually written by an algorithm (e.g., python package `prov`):

For example, `normalized_counts.csv` **wasGeneratedBy** a normalization activity, 
which **used** `counts.tsv` and **wasAssociatedWith** an analysis pipeline.

<p align="center">
  <img
    src="{{ '/assets/05_Reusable_W3C_Prov_Model.png' | relative_url }}"
    alt="The W3C Prov model"
    style="width: 100%; height: auto;"
  /><br>
</p>

You do *not* need to implement PROV to begin recording provenance. 
A well-maintained workflow, run manifest, 
or analysis log can already make an enormous difference.

### Why Provenance Matters for AI

AI systems depend on data, but the quality and suitability of their outputs 
depend heavily on the origins, processing history, and context of those data. 
Without provenance, an AI system may analyze a dataset without knowing how it 
was generated, whether it was transformed, what assumptions were made, or 
whether it is appropriate for a particular scientific question.


<p align="center">
  <img
    src="{{ '/assets/05_Reusable_AI_Provenance.jpg' | relative_url }}"
    alt="Data Provenance in AI "
    style="width: 100%; height: auto;"
  /><br>
</p>


**Provenance supports trustworthy AI in several important ways:**

<u>Data quality and reliability:</u> Knowing where training or input data originated, 
how they were collected, and what quality-control procedures were applied helps 
researchers assess whether the data are suitable for an AI application.

<u>Transparency and explainability:</u> Documenting datasets, model versions, 
preprocessing steps, and computational workflows makes it easier to trace how 
an AI-generated result was produced. This supports auditing and scientific 
interpretation, although provenance alone does not explain a model's internal 
decision-making.

<u>Bias detection and generalizability:</u> Information about study populations, 
sampling methods, and data-processing decisions helps researchers identify 
potential sources of bias and assess whether a model may perform differently 
across patient populations or research settings.

<u>Reproducibility and accountability:</u> Recording training datasets, model versions, 
software environments, parameters, and evaluation procedures allows researchers 
to investigate unexpected results, reproduce analyses where feasible, and identify 
where errors may have occurred.

<u>Responsible data reuse:</u> Provenance can help researchers determine whether 
data were obtained and processed under conditions compatible with their intended 
use. This is particularly important for sensitive biomedical and clinical data, 
where consent, privacy, and data-use restrictions must be respected.


Read more in ["A large-scale audit of dataset licensing and attribution in AI"](https://www.nature.com/articles/s42256-024-00878-8)

Learn more at [MIT Data Provenance in AI Project](https://www.dataprovenance.org/about) 

## Licensing and permissions: what am I allowed to do?

**R1.1** is about making usage conditions clear. A publicly visible GitHub repository 
is **not automatically licensed for unrestricted reuse**. Conversely, controlled-access data may have explicit permitted uses even though the data are not public.

Distinguish these questions:

1. **Can I access it?** Authentication, approvals, or access mechanisms.
2. **May I reuse or redistribute it?** Licenses, consent, contracts, institutional policies, and data-use agreements.
3. **Is it scientifically appropriate to use?** Study design, limitations, quality, and suitability for the new question.


<p align="center">
  <img
    src="{{ '/assets/05_Reusable_Licensing.png' | relative_url }}"
    alt="Reusable Licensing "
    style="width: 100%; height: auto;"
  /><br>
</p>


If a repository contains a script and no license, is it safe to assume you can 
redistribute a modified copy? **No.** Ask for clarification or seek an 
appropriate license before redistributing.

## Community standards: why R1.3 matters

**R1.3** asks whether research objects follow standards relevant to their 
scientific community. This is not a demand that every discipline use the same 
file format or reporting checklist. Instead, the community agrees on the 
information needed to interpret and compare its research.

Examples to explore:

- **MIAME** — Minimum Information About a Microarray Experiment: [FGED Society](https://www.fged.org/projects/miame/).
- **MINSEQE** — Minimum Information about a high-throughput Nucleotide SeQuencing Experiment: [FGED Society](https://www.fged.org/projects/minseqe/).
- **BioSample metadata** — sample descriptors and attributes: [NCBI BioSample](https://www.ncbi.nlm.nih.gov/biosample/).
- **FAIRsharing** — find standards, repositories, and policies: [fairsharing.org](https://fairsharing.org/).

A good rule is to **choose standards based on the assay and research question**. 
For example, a bulk RNA-seq experiment, a clinical registry, and a microscopy 
study have different requirements.

### Discussion

Would a new researcher know which reference genome was used? Which samples were 
excluded? Whether a clinical response variable was assessed at diagnosis or after 
treatment? Community standards help prevent those details from being silently omitted.

## How journals and open science advance reuse

Journals increasingly encourage or require clearer data availability statements, 
code availability, reporting standards, and repository deposition. Requirements 
vary by journal, article type, data sensitivity, and year; always consult the 
current author instructions.

| Publisher or journal resource | Reuse-related practice to explore |
|:--|:--|
| [Nature Portfolio research data policies](https://www.nature.com/nature-portfolio/editorial-policies/reporting-standards) | Data availability and reporting expectations. |
| [PLOS data availability policy](https://journals.plos.org/plosone/s/data-availability) | Data availability statements and underlying data access. |
| [eLife author guide](https://elifesciences.org/inside-elife/author-guide) | Research transparency and author guidance. |
| [Scientific Data](https://www.nature.com/sdata/) | Data descriptors and documentation supporting discovery and reuse. |
| [FAIRsharing](https://fairsharing.org/) | Discovery of community standards, repositories, and policies. |

**A useful nuance:** A data availability statement saying “available upon reasonable request” 
does not, by itself, guarantee timely access or adequate documentation. A repository record, 
persistent identifier, metadata, and clearly defined access procedure are often stronger.

### FAIR and open science: overlapping, not identical

**Open science** promotes practices such as sharing research outputs, 
transparent methods, collaborative development, and open access where
appropriate.The overlap between Open and FAIR is substantial: version-controlled code, documented methods, 
persistent identifiers, transparent provenance, and clear reuse terms help both. 
But **FAIR does not require all data to be open**, especially for pediatric and 
clinical research.

## The Turing Way: practical guidance for everyday research

[**The Turing Way**](https://book.the-turing-way.org/) is an open, 
community-developed handbook for reproducible, ethical, collaborative research. 
It is an excellent follow-up resource because it translates abstract principles 
into day-to-day workflows.

St. Jude Biohackaton Team 20 created an AI and Reproducible Research Assistant grounded on the Turing Way. 
The assistnat perfoms a diagnostic of your research workflows, allowing for targeted guidance on improvement.

St. Jude AI and Data Learning Assistant in Action: https://github.com/stjude-biohackathon/KIDS26-Team20

To learn more about the Turing Way, start with:

- [The Turing Way — Reproducible Research](https://book.the-turing-way.org/reproducible-research/reproducible-research.html)
- [The Turing Way — Research Data Management](https://book.the-turing-way.org/reproducible-research/rdm/rdm.html)
- [The Turing Way — Version Control](https://book.the-turing-way.org/reproducible-research/vcs/vcs.html)
- [The Turing Way — Licensing](https://book.the-turing-way.org/reproducible-research/licensing/licensing.html)

These are resources for further exploration; page locations may change as the handbook evolves.

### Bringing it back to our lab manual

The most useful FAIR practice may be the one that your lab can adopt *consistently*: 
a shared README template, a coding style guide, required environment files, a naming 
convention, a review checklist, or a procedure for recording provenance. 
**Good habits become powerful when they are part of the normal research workflow rather than an extra step at publication.**

## Activity (optional): make our leukemia dataset reusable (5 minutes)

Return to the synthetic dataset from [Module 1]({{ '/docs/01-reuse-challenge.html' | relative_url }}). 
Imagine another research team wants to examine whether expression values are associated with treatment response.


1. **R1 — Context:** What three pieces of information are missing that would most affect whether the data are suitable for a new analysis?
2. **R1.1 — Rights:** What reuse or access conditions would you need to clarify before sharing the data?
3. **R1.2 — Provenance:** Sketch a plausible *hypothetical* processing chain for `val`. Which steps and versions would need to be confirmed with the original researchers?
4. **R1.3 — Standards:** Which data dictionary fields, assay standards, or clinical response definitions should be documented?
5. **Software:** Name two files or practices that would help someone rerun the original analysis.

*Do not invent facts about the dataset.* Label unknowns explicitly, and distinguish a proposed metadata field from a verified value.

## Key takeaways

- **R1**: Describe research objects with rich, accurate, and relevant information that supports informed reuse.
- **R1.1**: Clearly document licenses, permissions, and data-use restrictions so others understand how research objects may be reused.
- **R1.2**: Maintain detailed provenance, including data origins, processing steps, methods, software versions, and analytical decisions.
- **R1.3:** Follow domain-relevant community standards for data, metadata, methods, and reporting.
- Reproducible workflows enable reuse. Standardized practices and automated workflows make research easier to reproduce, maintain, and adapt.
- Reusability begins at the start of research. Documentation, provenance, and good software practices should be incorporated throughout the research lifecycle.

## Reflection

> What is one practice your research group could adopt *this month* to make future datasets or analyses easier to reuse? 
Examples: create a README template; capture environment files; tag analysis releases; add data dictionaries; 
document QC exclusions; record access conditions; or incorporate these practices into a lab manual.

## References

- Wilkinson, M. D. et al. (2016). [The FAIR Guiding Principles for scientific data management and stewardship](https://doi.org/10.1038/sdata.2016.18). *Scientific Data*.
- Liffers, M. [ARDC FAIR Data 101 — Reusable, Webinar 8](https://ardc.edu.au/) (slides supplied for this workshop; sections on provenance, software, licensing, and versioning informed this lesson).
- [W3C PROV Primer](https://www.w3.org/TR/prov-primer/).
- Lamprecht, A.-L. et al. [Towards FAIR principles for research software](https://doi.org/10.3233/DS-190026).
- Barker, M. et al. [FAIR Principles for Research Software (FAIR4RS)](https://doi.org/10.15497/RDA00068).
- [The Turing Way](https://book.the-turing-way.org/).

---

[← Interoperable]({{ '/docs/04-interoperable.html' | relative_url }}) · [Next: FAIR and AI →]({{ '/docs/06-ai.html' | relative_url }})
