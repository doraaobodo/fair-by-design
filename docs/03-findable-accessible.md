---
layout: default
title: "03 - Findable and Accessible"
parent: Workshop Modules
nav_order: 3
description: "Findable data, metadata, persistent identifiers, and a guided biomedical dataset exercise."
---

# Findable: Can someone discover your research data?

> Data cannot be reused if potential users cannot discover that it exists. Findability depends on stable identifiers, rich metadata, explicit connections between metadata and data, and searchable registration.


<p align="center">
  <img
    src="{{ '/assets/03_Findable_and_Accessible_Findable_SubPrinciples.png' | relative_url }}"
    alt="Infographic explaining F1 through F4."
    style="width: 100%; height: auto; cursor: zoom-in; object-fit: contain; background-color: #000;"
    onclick="document.fullscreenElement ? document.exitFullscreen() : this.requestFullscreen()"
  /><br>
</p>
  
**Important distinction:** F1 in the original 2016 publication specifies a *globally unique and persistent identifier*. 
Some implementation guidance additionally emphasizes that identifiers should be resolvable, 
meaning that the identifier can be used to retrieve data. 
For example a DOI is resolvable because pasting it into a browser directs you 
straight to the research object (publication, etc.) The stronger wording is very 
useful in practice, but it is not a verbatim quote of F1.

## Metadata is like a library catalog record

Imagine a library filled with books but no catalog. The books exist, yet finding the one relevant to your question could take hours. A useful catalog record tells you the title, author, topic, edition, and where the book is held.

<p align="center">
  <img
    src="{{ '/assets/03_Findable_and_Accessible_Bookshelf_to_Catalog_Record.png' | relative_url }}"
    alt="Book to Library Catalog."
    style="width: 100%; height: auto; cursor: zoom-in; object-fit: contain; background-color: #000;"
    onclick="document.fullscreenElement ? document.exitFullscreen() : this.requestFullscreen()"
  /><br>
  <em>Books in a Library are cataloged to make them findable.  </em>
</p>

**For Findable and Accessible research data:**

- **Dataset** = the book or research object itself.
- **Metadata** = the catalog description that explains what it is.
- **Persistent identifier** = a stable reference to the object or its landing page.
- **Searchable repository/catalog** = the discovery system where that description can be found.

A catalog can describe a rare book even if access is restricted. Likewise, 
a biomedical dataset can have public, non-sensitive metadata while its 
patient-level data remain access-controlled.

**Nugget:** If a dataset is stored safely on a private drive but no one knows it exists, is it Findable?

## What is metadata?

**Metadata is structured information about a research object.** It helps people 
discover, interpret, manage, connect, and appropriately reuse that object. 
The ARDC *Findable #2* webinar describes metadata as structured data about data, 
a primary discovery tool, human-readable and machine-actionable when well organized, 
and often structured using schemas.

Metadata can describe datasets, files, specimens, software, analytical workflows, 
publications, and more. 

**Metadata is not merely a README.** A README can be useful human-readable 
documentation, while a structured metadata record supports consistent 
indexing and machine processing.

### Types of metadata

Jenn Riley's *Understanding Metadata* (2017), distinguishes descriptive, 
structural, and administrative metadata. 

<p align="center">
  <img
    src="{{ '/assets/03_Findable_and_Accessible_Metadata_Types.png' | relative_url }}"
    alt="Metadata Types."
    style="width: 100%; height: auto; cursor: zoom-in; object-fit: contain; background-color: #000;"
    onclick="document.fullscreenElement ? document.exitFullscreen() : this.requestFullscreen()"
  /><br>
  </p>

**Caution:** THESE CATEGORIES ARE NOT MUTUALLY EXCLUSIVE. A DOI, for example, may appear in descriptive and technical contexts.

### Metadata at different levels

A dataset may need metadata at several levels:

<p align="center">
  <img
    src="{{ '/assets/03_Findable_and_Accessible_Metadata_Levels.png' | relative_url }}"
    alt="Metadata Levels."
    style="width: 100%; height: auto; cursor: zoom-in; object-fit: contain; background-color: #000;"
    onclick="document.fullscreenElement ? document.exitFullscreen() : this.requestFullscreen()"
  /><br>
  </p>

**Example:** A catalog record might say that a dataset contains synthetic leukemia gene-expression and response variables. A separate data dictionary is still needed to explain whether `resp = 1` means response or non-response and what `val = 8.2` measures. Do not infer these meanings from the filename or column names.

## From metadata fields to metadata schemas

A **metadata schema** specifies which fields exist, what they mean, and often how their values are represented. Shared schemas make records more consistent and easier for discovery services to index.

For biomedical research, the most appropriate schema or minimum-information checklist depends on the data type and repository. **No one schema covers all biomedical research.** Browse [FAIRsharing](https://fairsharing.org/) to explore standards, databases, and policies relevant to your domain.


<p align="center">
  <img
    src="{{ '/assets/03_Findable_and_Accessible_Bioproject_schema.jpg' | relative_url }}"
    alt="BioProject Schema."
    style="width: 100%; height: auto; cursor: zoom-in; object-fit: contain; background-color: #000;"
    onclick="document.fullscreenElement ? document.exitFullscreen() : this.requestFullscreen()"
  /><br>
  </p>


### Human-readable versus structured metadata

A human-readable description:

> Synthetic study of gene expression and treatment response in fictional pediatric leukemia records. Variables include `PtID`, `dx`, `resp`, `sample`, `gene`, `val`, `day`, and `grp`. Definitions are incomplete.

A simple structured metadata record (YAML file):

```yaml
title: "Synthetic pediatric leukemia expression and response teaching dataset"
resource_type: "Dataset"
creators:
  - name: "FAIR by Design workshop team"
description: >
  Fictional teaching data for identifying metadata gaps in
  a biomedical research dataset. Not suitable for clinical inference.
keywords:
  - synthetic data
  - leukemia
  - gene expression
  - FAIR training
version: "0.1"
identifier: "NOT_ASSIGNED"
access: "Public teaching dataset; no patient data"
files:
  - "final_data_v2_REALLYFINAL.csv"
```

This record is **better than a bare CSV**, but it does not yet satisfy every Findable requirement. In particular, the identifier is a placeholder, several variable definitions remain unknown, and the record is not automatically registered in a searchable catalog simply because it appears in a Markdown lesson.

## Persistent identifiers and discovery platforms

A **Digital Object Identifier (DOI)** is a persistent identifier commonly used for publications, datasets, software, and other research objects. A DOI resolves to a landing page where descriptive metadata and access information can be maintained. A DOI does **not** by itself guarantee that the data will remain available forever.

- **[Zenodo](https://zenodo.org/):** A general-purpose repository that can archive research outputs and issue DOIs for deposited records.
- **[Dryad](https://datadryad.org/):** A curated repository for research datasets, with publication and citation support.
- **[GEO](https://www.ncbi.nlm.nih.gov/geo/):** A domain repository for functional genomics datasets; records use GEO accession identifiers.
- **[ENA](https://www.ebi.ac.uk/ena/browser/home):** A nucleotide-sequence archive with accession-based discovery.
- **[re3data](https://www.re3data.org/):** A registry to help researchers locate suitable research data repositories.
- **[PubMed](https://pubmed.ncbi.nlm.nih.gov/):** Primarily a literature discovery index, not a general-purpose dataset repository.


> **How they work together:** Research object → descriptive metadata record → identifier and landing page → registration/indexing → search and discovery. The underlying files may be public or controlled-access depending on the project.

> **Think about F3:** If a metadata record has its own identifier, how does it explicitly identify the dataset it describes? Make that relationship clear in the metadata rather than relying only on a human-readable sentence.


>**NOTE:** [NLM Data Sharing Resources.](https://www.nlm.nih.gov/NIHbmic/domain_specific_repositories.html) A repository of repositories!

## 6. Activity: Make our dataset more Findable (8 minutes)

<p align="center">
  <img
    src="{{ '/assets/03_Findable_and Accessible_Sticky_Note_Task.png' | relative_url }}"
    alt="Interoperability Layers"
    style="width: 100%; height: auto; cursor: zoom-in; object-fit: contain; background-color: #000;"
    onclick="document.fullscreenElement ? document.exitFullscreen() : this.requestFullscreen()"
  /><br>
</p>


### Part A — Think, Pair, Share: Draft a catalog record (4 minutes)

Propose values for the following fields:

| Metadata field | Your proposed entry |
|:--|:--|
| Descriptive title | |
| Dataset description and purpose | |
| Creator or responsible team | |
| Keywords (3–5) | |
| Data type and file format | |
| Version and date | |
| Identifier or identifier plan | |
| Where this record should be indexed | |
| Access conditions | |
| Missing information requiring clarification | |

### Part B — Discussion (4 minutes)

1. Which three metadata fields most improved your ability to discover this dataset?
2. What can you fill in confidently, and what must remain unknown?
3. What is the difference between placing the CSV on GitHub and registering a dataset in a searchable repository?
4. How would your record help someone search for this dataset without exposing sensitive patient information?

**Optional stretch:** Look up one suitable repository for your own type of research using [re3data](https://www.re3data.org/) or [FAIRsharing](https://fairsharing.org/). What metadata does it require?

## Key takeaways

- **F1:** Use globally unique and persistent identifiers.
- **F2:** Describe research objects with rich, useful metadata at appropriate levels.
- **F3:** Explicitly connect metadata records to the objects they describe.
- **F4:** Register or index records in searchable discovery systems.
- Metadata quality is contextual: what counts as *rich* depends on the research question, data type, and likely users.
- **Findable does not mean openly downloadable.** Public, non-sensitive metadata can describe controlled-access research data.

## References and attribution

- Wilkinson, M. D., et al. (2016). [The FAIR Guiding Principles for scientific data management and stewardship](https://doi.org/10.1038/sdata.2016.18). *Scientific Data*, 3, 160018.
- Stokes, L. (Australian Research Data Commons). *Findable #2: FAIR Data 101 virtual course, Webinar 2*. Workshop source slides provided by the instructor; source marked CC BY 4.0. Concepts adapted and attributed, not reproduced verbatim.
- Riley, J. (2017). [Understanding Metadata: What is metadata, and what is it for?](https://www.niso.org/publications/understanding-metadata-2017). NISO.
- [DataCite Metadata Schema](https://schema.datacite.org/)
- [FAIRsharing](https://fairsharing.org/) · [re3data](https://www.re3data.org/) · [Zenodo](https://zenodo.org/) · [Dryad](https://datadryad.org/)

---

**Next:** [Interoperable — Making data understandable across systems]({{ '/docs/04-interoperable.html' | relative_url }})
