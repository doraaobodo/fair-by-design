---
layout: default
title: "02 - FAIR Foundations"
parent: Workshop Modules
nav_order: 2
description: "An introduction to FAIR principles."
---

# Module 2 — FAIR Foundations


## The problem FAIR addresses

In Module 1, you could safely read and access the CSV data, but could you 
confidently interpret it for further analysis? The missing definitions
for `resp`, `val`, and `day` show that data used in research are not 
always reusable research objects.

Wilkinson and colleagues introduced the **FAIR Guiding Principles** to 
improve the ability of people **and machines** to find and reuse scientific 
research objects. Importantly, FAIR describes *desired* properties, 
not a mandatory standard.

---

<embed src="{{ '/docs/FAIR_Research_Data_Workshop.pdf' | relative_url }}" width="100%" height="600px" type="application/pdf" />

Alternatively, [View/Download PDF in new tab]({{ '/docs/FAIR_Research_Data_Workshop.pdf' | relative_url }})

---
### Looking back at the dataset

res.csv:
| PtID | dx | resp | sample | gene | val | day | grp |
| :--- | :--- | :---: | :--- | :--- | :---: | :---: | :---: |
| P01 | ALL | 1 | S01 | GATA3 | 8.2 | 0 | A |
| P02 | ALL | 0 | S02 | GATA3 | 3.7 | 7 | B |
| P03 | AML | 1 | S03 | GATA3 | NA | 0 | A |
| P04 | ALL | 2 | S04 | STAT5A | 12.1 | 14 | B |
| P05 | AML | 0 | S05 | STAT5A | 5.4 | 7 | A |
| P06 | ALL | 1 | S06 | GATA3 | 6.0 | 14 | B |
| P07 | ALL | | S07 | STAT5A | 9.3 | 0 | A |
| P08 | AML | 1 | S08 | GATA3 | 4.8 | 7 | B |

README.txt
```
# Study data

File: `final_data_v2_REALLYFINAL.csv`

Contains study samples and expression values. Some values may be missing. 

This is the latest file we used for analysis.

Contact the original team if you have questions.
```

Download [CSV]({{ '/exercises/data/final_data_v2_REALLYFINAL.csv' | relative_url }}) 
(also available [here])(https://github.com/doraaobodo/fair-by-design/blob/main/exercises/data/final_data_v2_REALLYFINAL.csv) 
and [README.txt]({{ '/exercises/data/README.txt' | relative_url }}). 


| Principle | Core idea | How to address in dataset |
|:--|:--|:--|
| **F — Findable** | Data and metadata have persistent identifiers, rich descriptions, and can be discovered through searchable resources. | Give the dataset a stable identifier and searchable description including study design and data types. |
| **A — Accessible** | Data or metadata can be retrieved through defined, standardized methods; authentication and authorization can be required. | Publish an access-request procedure while retaining sensitive records in a controlled environment. |
| **I — Interoperable** | Data and metadata use shared representations, vocabularies, and meaningful links to other research objects. | Define `dx` using a documented disease terminology; state what `resp` codes mean. |
| **R — Reusable** | Data and metadata provide sufficient context, provenance, use conditions, and community-standard descriptions. | Document how `val` was measured and processed, what `NA` means, and which uses are permitted. |


## Knowledge check

<p align="center">
  <img
    src="{{ '/assets/02_FAIR_Foundations_Sticky_Note_Task.png' | relative_url }}"
    alt="FAIR Foundations Sticky Note Task."
    style="width: 100%; height: auto; cursor: zoom-in; object-fit: contain; background-color: #000;"
    onclick="document.fullscreenElement ? document.exitFullscreen() : this.requestFullscreen()"
  /><br>
</p>

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
