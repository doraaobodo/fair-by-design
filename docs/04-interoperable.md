---
layout: default
title: "04 - Interoperable"
parent: Workshop Modules
nav_order: 4
description: "Understand FAIR interoperability through NCBI BioProject, BioSample, and SRA, shared identifiers, vocabularies, RDF, and knowledge graphs."
---

# Helping Research Data Speak the Same Language

> Data are interoperable when different systems and researchers can exchange information and understand what it means.

<p align="center">
  <img
    src="{{ '/assets/04_Interoperable_SubPrinciples.png' | relative_url }}"
    alt="Interoperable Sub-principles"
    style="width: 100%; height: auto; cursor: zoom-in; object-fit: contain; background-color: #000;"
    onclick="document.fullscreenElement ? document.exitFullscreen() : this.requestFullscreen()"
  /><br>
</p>

**Remember:** I1 is about a common way to express information; I2 is about shared meanings for terms; I3 is about meaningful links between research objects. All three work together.

## Sharing words is not the same as sharing meaning

Interoperability operates via several different layers:

<p align="center">
  <img
    src="{{ '/assets/04_Interoperable_Layers_of_Interoperability.png' | relative_url }}"
    alt="Interoperability Layers"
    style="width: 100%; height: auto; cursor: zoom-in; object-fit: contain; background-color: #000;"
    onclick="document.fullscreenElement ? document.exitFullscreen() : this.requestFullscreen()"
  /><br>
</p>

## Controlled vocabularies and ontologies: agreeing on meaning

Suppose one dataset records `ALL`, another records `acute lymphoblastic leukemia`, and a third uses a standardized disease concept identifier. A human may recognize the relationship, but software needs explicit rules or mappings to know whether the terms mean the same thing in context.

- A **controlled vocabulary** provides an agreed set of terms or codes.
- An **ontology** goes further by defining concepts and relationships among them (for example, that one disease category is a subtype of another).
- A **term identifier** makes a concept easier to reference consistently even when labels or synonyms vary.

Biomedical examples include [NCBI Taxonomy](https://www.ncbi.nlm.nih.gov/taxonomy) for organisms, [Gene Ontology](https://geneontology.org/) for gene-function concepts, and [Disease Ontology](https://disease-ontology.org/) for disease concepts. Choose standards appropriate to the research domain and verify that a term precisely matches what was measured.

Would you map `resp = 1` to a standard response term before knowing the original coding definition? **No.** A standard cannot rescue an undocumented or incorrect assumption.

## 4. A familiar example: NCBI BioProject + BioSample + SRA

NCBI resources provide a practical example of connected research records. They store **different, complementary information**:

<p align="center">
  <img
    src="{{ '/assets/04_Interoperable_Bioproject_with_Interop.jpg' | relative_url }}"
    alt="Interoperability Bioproject"
    style="width: 100%; height: auto; cursor: zoom-in; object-fit: contain; background-color: #000;"
    onclick="document.fullscreenElement ? document.exitFullscreen() : this.requestFullscreen()"
  /><br>
</p>

1. **The 3-Pillar Ecosystem (Top Row — Principle I3 in Action):**
   * BioProject (`PRJNAxxxxxx`) acts as the central metadata hub ("The Why & Who") rather than a raw file bin.
   * It uses **qualified links** (`I3`) to connect administrative context to physical specimens in **BioSample** (`SAMNxxxxxx`, "The What") and experimental outputs in **SRA / GenBank / GEO** ("The Output").
2. **Project Hierarchy (Bottom Left — Structured Grouping):**
   * Large consortia or multi-omics studies use **Umbrella Projects** to group multiple **Primary Projects** without duplicating raw sequence submissions.
3. **The 5 Core Schema Blocks (Bottom Right — Principles I1 & I2):**
   * **Formal Schema (`I1`):** Under the hood, NCBI enforces strict XML schemas (`Core.xsd` and `Submission.xsd`) so automated pipelines can ingest and validate submissions reliably.
   * **Controlled Matrix (`I2`):** Inside the **Project Type** block, users cannot type free text. They must select valid combinations from controlled vocabularies:
     * *Sample Scope:* `Monoisolate` vs. `Environment`
     * *Material:* `Genome` vs. `Transcriptome`
     * *Capture:* `Whole` vs. `Targeted`
     * *Method:* `Sequencing` vs. `Array`
     * *Objective:* `Assembly` vs. `Raw Reads`
   * **Target Organism (`I2`):** Standardized via **NCBI Taxonomy IDs** rather than informal species nicknames.
   * **Links & Cross-References (`I3`):** Explicitly binds the project to **PubMed IDs (`PMID`)**, **DOIs**, parent Umbrella accessions, and downstream data records.

**Try it:** Browse [NCBI BioProject](https://www.ncbi.nlm.nih.gov/bioproject/), [NCBI BioSample](https://www.ncbi.nlm.nih.gov/biosample/), and [NCBI SRA](https://www.ncbi.nlm.nih.gov/sra). Search for a public study and follow its linked records. Look for the project accession, sample accession, experiment accession, and run accession.

### What makes this useful?

- A sequencing run becomes more interpretable when linked to the sample and its attributes.
- A sample becomes easier to contextualize when linked to the project that collected it.
- Stable accession identifiers allow researchers and software to connect records without relying on filenames alone.
- Consistent metadata and defined relationships help prevent incorrect joins across projects, samples, and experiments.

**Important distinction:** Cross-references are a major *step toward* interoperability, especially I3, but links alone do not guarantee full semantic interoperability. The meaning and structure of the linked records must also be clear.


## Interoperability with Machines

At the heart of FAIR interoperability is **machine-actionability**—the capacity of computational systems to find, access, parse, and combine data **without a human first reading a README file or manually reformatting columns**. 

While a human can easily guess that `"Part of PRJNA12345"` written in a spreadsheet note means a sample belongs to a project, a script cannot reliably act on free text. To make data machine-actionable across different databases, we structure it as a **knowledge graph** using **RDF**.

### What is a Knowledge Graph?
A **knowledge graph** is a network of **things (entities) and meaningful arrows (relationships)**. Unlike a flat spreadsheet where connections are hidden inside rows and columns, a graph makes every relationship explicit.

The arrows are just as important as the things: `is part of`, `was derived from`, and `is described by` tell a computer completely different rules about how data can be combined.

### What is RDF?
**RDF (Resource Description Framework)** is the W3C standard grammar used to build knowledge graphs on the web. Instead of tables, RDF stores facts as simple, three-part statements called **triples**:

**Subject → Predicate → Object**

```text
Sample SAMN...    -- is part of -->     Project PRJNA...
Experiment SRX... -- uses sample -->    Sample SAMN...
Run SRR...        -- is produced by --> Experiment SRX...
```

### How Machines Read RDF (URIs in Action)
To prevent ambiguity (for example, distinguishing *mouse* the rodent from *mouse* the computer device), RDF replaces plain words with globally unique web addresses called **URIs** (Uniform Resource Identifiers). 

When two separate labs use the exact same URI for a concept or relationship, a computer can automatically merge their datasets together.

Here is how that same BioProject relationship looks in **Turtle** (a human-friendly RDF syntax):

```turtle
@prefix ex:   <https://example.org> .
@prefix obo:  <http://obolibrary.org> .

ex:Sample_SAMN001
    obo:BFO_0000050  ex:Project_PRJNA001 .   # BFO_0000050 = "part of" in the Basic Formal Ontology
```

*(Note: `ex:Sample_SAMN001` and `ex:Project_PRJNA001` above are **illustrative fictional identifiers** used to demonstrate Turtle syntax, whereas `obo:BFO_0000050` is a real, machine-resolvable ontology term for "part of".)*

### Human-Readable vs. Machine-Actionable

| Feature | Human-Readable (Flat File) | Machine-Actionable (RDF / Graph) |
| :--- | :--- | :--- |
| **Format** | Free-text notes or unannotated CSV | Structured triples (Turtle, JSON-LD, RDF/XML) |
| **Identifier** | `"E. coli"` | `http://obolibrary.orgNCBITaxon_562` |
| **Relationship** | Implicit (two columns side-by-side) | Explicit predicate URI (`part of`, `derived from`) |
| **Integration** | Manual merging in R/Python | Automated querying across federated databases |

### Do I Need RDF to Make My Data Interoperable?
**Not always.** You do not need to convert every lab spreadsheet into RDF to practice good FAIR data management. 

### Good Example of a Knowledge Graph

**PrimeKG (Precision Medicine Knowledge Graph)**

- What it is: A large-scale multimodal knowledge graph developed at Harvard 
Medical School, integrating 20 biomedical resources to map 17,080 diseases 
across more than 4 million relationships.
- How it works: It connects ten distinct biological scales—from molecular 
perturbations and pathways up to anatomical regions, phenotypes, and approved 
drugs. Crucially, it includes explicit relationship edges for drug indications, 
contraindications, and off-label uses.

<p align="center" markdown="1">
  <img
    src="{{ '/assets/04_Interoperable_PRIMEKG.jpg' | relative_url }}"
    alt="PRIMEKG Figure 2"
    style="width: 100%; height: auto; cursor: zoom-in; object-fit: contain; background-color: #000;"
    onclick="document.fullscreenElement ? document.exitFullscreen() : this.requestFullscreen()"
  /><br>
  <em>PrimeKG (<a href="https://pmc.ncbi.nlm.nih.gov/articles/PMC9893183/">PMID: 36732524</a>)   
  Components. (a) Shown are 20 primary data resources curated to 
  develop PrimeKG. The colors highlight which data records are used to uniquely 
  identify each node type. For example, GO is colored by biological processes, 
  cellular components, and molecular functions because GO terms are the unique 
  identifiers used to define nodes for these three node types. (b) Primary 
  resources are colored by each node type for which they possess information. 
  For example, GO provides links from biological processes, cellular components, 
  and molecular functions to genes. As a result, we add the fourth color to 
  represent the gene/protein class. (c) Illustrated is the process of harmonizing 
  these primary data records to extract relationships between node types. 
  (d) The left side illustrates PrimeKG, and the right side shows all the textual 
  sources of clinical information on drugs and diseases. The node type legend 
  is consistent across the figure. Abbreviations - MF: molecular function, 
  BP: biological process, CC: cellular component, PPI: protein-protein 
  interactions, DO: disease ontology, MONDO: MONDO disease ontology, 
  Entrez: Entrez gene, GO: gene ontology, UMLS: unified medical language 
  system, HPO: human phenotype ontology, CTD: comparative toxicogenomics 
  database, SIDER: side effect resource. </em>
</p>


**Do I Need RDF to Make My Data Interoperable?** Not always. You do not need to 
convert every lab spreadsheet into RDF to practice good FAIR data management.
For most day-to-day research projects, starting with tabular data paired with a 
clear data dictionary, persistent identifiers (DOIs, ORCIDs, NCBI accessions), 
and standardized ontology terms gets you 80% of the way there. RDF and knowledge 
graphs become essential when you are integrating large, messy, heterogeneous 
datasets across multiple institutions or domains at scale.

<!-- 
## Activity (optional): Make our dataset more interoperable (6 minutes)

Return to [`final_data_v2_REALLYFINAL.csv`]({{ '/exercises/data/final_data_v2_REALLYFINAL.csv' | relative_url }}).

**Scenario:** A second team has a dataset with fields `subject_id`, `diagnosis`, `response_category`, `gene_symbol`, `expression_value`, and `collection_day`. They want to combine it with our dataset.

**### Part A - Mapping two datasets(3 minutes):**

1. Choose **two columns** in our original dataset (such as `dx` and `resp`). For each, propose a clearer field name and state **what information you must confirm before mapping it**.
2. Suggest one shared identifier or controlled vocabulary that could help the datasets communicate.
3. Describe one relationship that should be recorded explicitly, such as `sample S01 belongs to participant P01` or `expression measurement was generated from sample S01`.

**### Part B — Discussion (3 minutes):**

- Which changes improve *technical* interoperability? Which improve *semantic* interoperability?
- Why is it dangerous to assume that matching variable names imply matching meanings?
- How would you represent the sample-to-participant relationship so software can use it safely?
-->

## Knowledge Check

<p align="center">
  <img
    src="{{ '/assets/04_Interoperable_Sticky_Note_Task.png' | relative_url }}"
    alt="Interoperability Sticky Note Task/ KNowledge Check True of False"
    style="width: 100%; height: auto; cursor: zoom-in; object-fit: contain; background-color: #000;"
    onclick="document.fullscreenElement ? document.exitFullscreen() : this.requestFullscreen()"
  /><br>
</p>

## Key takeaways

- **I1:** Agree on how information is represented.
- **I2:** Agree on what terms mean.
- **I3:** Describe how research objects are related.
- NCBI's connected BioProject, BioSample, and SRA records show why identifiers and meaningful cross-references are useful.
- **Interoperability is incremental.** You can start with a documented schema, data dictionary, and consistent identifiers before adopting advanced linked-data technologies.

## Further reading

- [Wilkinson et al. (2016), The FAIR Guiding Principles](https://doi.org/10.1038/sdata.2016.18)
- [NCBI BioProject](https://www.ncbi.nlm.nih.gov/bioproject/)
- [NCBI BioSample](https://www.ncbi.nlm.nih.gov/biosample/)
- [NCBI SRA](https://www.ncbi.nlm.nih.gov/sra)
- [W3C RDF 1.1 Primer](https://www.w3.org/TR/rdf11-primer/)
- [FAIRsharing](https://fairsharing.org/)

Knowledge Check Answer Key: 0,0,1,0,1,1
---

[← Findable and Accessible]({{ '/docs/03-findable-accessible.html' | relative_url }}) | [Next: Reusable and Reproducible →]({{ '/docs/05-reusable.html' | relative_url }})
