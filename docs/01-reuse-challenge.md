---
layout: default
title: "01 - Data Reuse Challenge"
parent: Workshop Modules
nav_order: 1
description: "A ten-minute interactive exercise on the barriers to biomedical data reuse."
---

## The Data Reuse Challenge


> **Scenario:** You are studying whether gene-expression patterns are associated 
with treatment response in a clinical trial. A collaborator sends you a CSV 
file from a previous study and a short README. Assess whether these records are 
adequate to support a new analysis. Review the contents of each file.

<p align="center">
  <img
    src="{{ '/assets/01_Data_Reuse_Challenge_Sticky_Note_Task.png' | relative_url }}"
    alt="Data Reuse Challenge Sticky Note Task."
    style="width: 100%; height: auto; cursor: zoom-in; object-fit: contain; background-color: #000;"
    onclick="document.fullscreenElement ? document.exitFullscreen() : this.requestFullscreen()"
  /><br>
</p>


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

README.txt: 

```
# Study data

File: `final_data_v2_REALLYFINAL.csv`

Contains study samples and expression values. Some values may be missing. 

This is the latest file we used for analysis.

Contact the original team if you have questions.
```

Download [CSV]({{ '/exercises/data/final_data_v2_REALLYFINAL.csv' | relative_url }}) 
(also available [here](https://github.com/doraaobodo/fair-by-design/blob/main/exercises/data/final_data_v2_REALLYFINAL.csv)) 
and [README.txt]({{ '/exercises/data/README.txt' | relative_url }}). 

---

## Discussion

**Data can be technically readable but scientifically uninterpretable.**

<p align="center">
  <img
    src="{{ '/assets/01_Data_Reuse_Challenge_Readable_not_equal_to_Interpretable.png' | relative_url }}"
    alt="Readable does not equal Interpretable"
    style="width: 100%; height: auto; cursor: zoom-in; object-fit: contain; background-color: #000;"
    onclick="document.fullscreenElement ? document.exitFullscreen() : this.requestFullscreen()"
  /><br>
</p>

There are some things one *can* infer and *cannot safely infer* from 
the files. Without a data dictionary, we cannot confidently interpret the values.

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


Similarly, an AI agent also requires a data dictionary! Perhaps even more than the human.
An agent could successfully load the CSV and complete an analysis 
while making incorrect assumptions about what the data represents.

Imagine an AI agent is asked: "Identify genes associated with 
improved treatment response in this dataset." The agent reads the CSV, assumes 
`resp = 2` represents the best outcome, and ranks genes accordingly.

What if `resp = 2` actually represents disease progression?

---

### Connection to FAIR Guiding Principles

<p align="center">
  <img
    src="{{ '/assets/01_Data_Reuse_Challenge_FAIR_Connection.png' | relative_url }}"
    alt="Data Reuse challenge connection to FAIR."
    style="width: 100%; height: auto; cursor: zoom-in; object-fit: contain; background-color: #000;"
    onclick="document.fullscreenElement ? document.exitFullscreen() : this.requestFullscreen()"
  /><br>
</p>

**Key takeaway:**  
FAIR is about improving the ability of people and machines to find, access, 
interpret, and reuse research objects appropriately. 

---

[← Home]({{ '/docs/index.html/' | relative_url }}) | [Next: FAIR Foundations →]({{ '/docs/02-fair-foundations.html' | relative_url }})
