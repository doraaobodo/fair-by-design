---
layout: default
title: "01 - Data Reuse Challenge"
parent: Workshop Modules
nav_order: 1
description: "A ten-minute interactive exercise on the barriers to biomedical data reuse."
---

## The Data Reuse Challenge

**Can you reuse this dataset?**

**Scenario:** You are studying whether gene-expression patterns are associated 
with treatment response in a clinical trial. A collaborator sends you a CSV 
file from a previous study and a short README. Assess whether these records are 
adequate to support a new analysis. 

Open the [CSV]({{ '/exercises/data/final_data_v2_REALLYFINAL.csv' | relative_url }}) and 
[README.txt]({{ '/exercises/data/README.txt' | relative_url }}) files. Try to answer:

1. What does each column mean, and what units or coding conventions are used?
2. Which samples or observations can legitimately be compared?
3. What does `resp` mean, and when was it measured?
4. Can you trace the origin of the measurements and the processing steps?
5. Are you permitted to share, analyze, or combine these records with other datasets?
6. Would you use this dataset in a publication-quality analysis today? Why or why not?

**Note** If the links open in your browser, you can use **Save As** to download them. 

---

## Discussion

Share one thing you **can** infer and one thing you **cannot safely infer** from 
the files. Which missing information would you ask the collaborator to provide?

**Key Point 1: Data can be technically readable but scientifically uninterpretable.**

It is obvious someone sub-coded the data. Without a data dictionary, we cannot confidently interpret these values.

An incorrect assumption could reverse the interpretation of an association 
between gene expression and treatment response, potentially leading to an 
invalid scientific conclusion.

For example, the meaning of `resp` (treatment response): {0,1,2}

* Does 0 mean no response, complete response, or missing information?
* Does 1 mean partial response, treatment success, or something else?
* Does 2 indicate disease progression, a different response category, or an unknown value?

Other important ambiguities include the meaning of `val`, the timing represented 
by `day`, and whether `grp` represents a treatment group, experimental batch, or
patient subgroup.


**Key Point 2: Computational systems can process data without understanding its scientific meaning**

A computational agent could successfully load the CSV and complete an analysis 
while making incorrect assumptions about what the data represents.

Imagine an AI agent is asked: "Identify genes associated with 
improved treatment response in this dataset." The agent reads the CSV, assumes 
`resp = 2` represents the best outcome, and ranks genes accordingly.

What if resp = 2 actually represents disease progression?


The AI Agent also requires a data dictionary! Perhaps even more than the human.


**Key Point 3: This data contains patient-level data. FAIR principle of** 
**'Accessible' means data should be as open as appropriate and as restricted as** 
**necessary, with clear and consistent access mechanisms.**

A dataset can be FAIR without being openly accessible to everyone.

For example, a research team could publish a publicly accessible dataset record containing:
- A descriptive title and summary of the research.
- Information about the study design and data types.
- Non-sensitive metadata describing available variables.
- The name of the responsible institution or data steward.
- Instructions for requesting access.
- Eligibility criteria and applicable data-use restrictions.
- Information about the required approval process.

The underlying patient-level data could remain in a secure, controlled-access 
environment.A researcher could discover that the dataset exists, understand its 
general contents, and determine how to request access without being able to 
download sensitive patient information.

---

### Connection to FAIR


| FAIR dimension | Question raised by this example |
|---|---|
| **Findable** | Could a new researcher discover and identify this dataset? |
| **Accessible** | Is there a clear, appropriate process for retrieving the dataset and its metadata? |
| **Interoperable** | Are field definitions, units, identifiers, and vocabularies clear enough to integrate with other data? |
| **Reusable** | Are provenance, methods, usage conditions, and documentation sufficient for responsible reuse? |

**Key takeaway:** A file can be downloadable and still be difficult or inappropriate to reuse. 
FAIR is about improving the ability of people and machines to find, access, 
interpret, and reuse research objects appropriately. 

**Next:** [FAIR Foundations]({{ '/docs/02-fair-foundations.html' | relative_url }})


TODO:
Change up scenario
Add color/pictures to the md file.