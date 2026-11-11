---
layout: default
title: "02 - FAIR Foundations"
parent: Workshop Modules
nav_order: 2
description: "A 15-minute introduction to FAIR principles, responsible access, and machine-actionability."
---

# Module 2 — FAIR Foundations


## The problem FAIR addresses

In Module 1, you could open a CSV file, but could you confidently interpret it? The missing definitions for `resp`, `val`, and `day` show that a readable file is not necessarily a reusable research object.

In 2016, Wilkinson and colleagues introduced the **FAIR Guiding Principles** to improve the ability of people **and machines** to find and reuse scientific research objects. FAIR describes desired properties, not a mandatory software stack or a single technical standard.

---

<embed src="{{ '/docs/FAIR_Research_Data_Workshop.pdf' | relative_url }}" width="100%" height="600px" type="application/pdf" />

Alternatively, [Download the PDF]({{ '/assets/slides.pdf' | relative_url }})

---
## The four FAIR principles

| Principle | Core idea | Example from our fictional dataset |
|:--|:--|:--|
| **F — Findable** | Data and metadata have persistent identifiers, rich descriptions, and can be discovered through searchable resources. | Give the dataset a stable identifier and searchable description including study design and data types. |
| **A — Accessible** | Data or metadata can be retrieved through defined, standardized methods; authentication and authorization can be required. | Publish an access-request procedure while retaining sensitive records in a controlled environment. |
| **I — Interoperable** | Data and metadata use shared representations, vocabularies, and meaningful links to other research objects. | Define `dx` using a documented disease terminology; state what `resp` codes mean. |
| **R — Reusable** | Data and metadata provide sufficient context, provenance, use conditions, and community-standard descriptions. | Document how `val` was measured and processed, what `NA` means, and which uses are permitted. |

### Look back at the dataset

Our example file includes `PtID`, `dx`, `resp`, `sample`, `gene`, `val`, `day`, and `grp`. These labels may seem familiar, but they do not communicate all the information necessary for safe interpretation or integration.

**Quick audience prompt:** 
Which FAIR dimension would you address first? There is no single correct answer: the dimensions are related, but improvements can be incremental.
 Which missing piece of information in the leukemia dataset would you ask its creator for first?


Consider two distinct objects:

1. **Public metadata record:** title, summary, data types, identifier, steward, and access instructions.
2. **Controlled-access dataset:** sensitive records provided only to approved users under appropriate conditions.

**Discuss:** What information about our fictional leukemia dataset could be safely described in a public catalog without exposing individual-level records?

**Important:** Use only synthetic data in this workshop. FAIR practices do not override privacy, consent, institutional policy, or other applicable restrictions.

## FAIR for machines and AI

FAIR emphasizes **machine-actionability**: the extent to which software can discover, evaluate, and appropriately use a digital research object based on explicit, structured information.

For responsible automated use, a research object may need:

- Explicit variable definitions and permitted values
- Structured, machine-readable metadata
- Stable identifiers and relationships among datasets, code, and methods
- Provenance, units, processing information, and use restrictions

**Think–pair–share (1 minute):** If an AI agent were asked to identify genes associated with better treatment response, what should it check **before** analyzing this CSV?

## Knowledge check

**True or false?**

1. A CSV file is automatically FAIR because most tools can read it.
2. FAIR requires patient-level data to be publicly downloadable.
3. FAIR applies to workflows and software as well as datasets.
4. Machine-readable and scientifically interpretable mean the same thing.

Discuss the answers before opening the next module.

## Key takeaways

- FAIR is **Findable, Accessible, Interoperable, and Reusable**.
- FAIR describes **guiding principles**, not a specific file format or platform.
- **FAIR is not the same as open**; controlled access can be appropriate.
- Human and machine reuse both depend on meaningful metadata and context.
- FAIRness can improve **incrementally**, throughout the research lifecycle.

## Read more

- Wilkinson, M. D., et al. (2016). [The FAIR Guiding Principles for scientific data management and stewardship](https://doi.org/10.1038/sdata.2016.18). *Scientific Data*, 3, 160018.
- GOFair Foundation. [The FAIR Guiding Principles](https://www.gofair.foundation/fair-principles)

<!-- - [FAIR Cookbook](https://faircookbook.elixir-europe.org/)
- [FAIRsharing](https://fairsharing.org/) -->


[← Module 1: Data Reuse Challenge]({{ '/docs/01-reuse-challenge.html/' | relative_url }}) | [Next: Findable and Accessible →]({{ '/docs/03-findable-accessible.html' | relative_url }})
