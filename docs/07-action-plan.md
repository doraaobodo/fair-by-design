
---
layout: default
title: "07 - FAIR Action Plan and Resources"
parent: Workshop Modules
nav_order: 7
description: "Frequently asked questions, the FAIR Cookbook, and practical steps for incorporating FAIR into research workflows."
---

# FAIR Action Plan and Resources

**Duration:** 10 minutes  
**Format:** Guided resource exploration, open discussion, and individual action planning.

Throughout this workshop, we have explored how the FAIR Guiding Principles can improve research data management, stewardship, and reuse.

The goal is not to make every research object perfectly FAIR overnight. Instead, we want to identify achievable improvements that can be incorporated into our everyday research practices.

> **FAIR is not a destination or a checklist to complete once. It is an ongoing approach to making research more discoverable, accessible, interoperable, and reusable.**

---

## 1. Frequently Asked Questions (FAQs)

### Does FAIR mean that all my research data must be publicly available?

**No.** FAIR does not require unrestricted access to research data.

Sensitive biomedical and clinical datasets can be FAIR while remaining in controlled-access environments. Publicly discoverable metadata can describe the dataset, its contents, and the process for requesting authorized access.

### Do I need to implement all the FAIR principles at once?

**No.** FAIR implementation can be incremental.

You can begin by improving documentation, establishing naming conventions, maintaining a data dictionary, or recording software versions.

Small, consistent improvements can make research objects substantially easier to understand and reuse.

### Do I need to know RDF, ontologies, or knowledge graphs to make my data FAIR?

**Not necessarily.**

These technologies can support interoperability, particularly when integrating information across systems.

However, you can begin by adopting established community standards, using consistent identifiers, documenting variable definitions, and selecting appropriate metadata schemas.

### Does putting my data or code on GitHub make it FAIR?

**Not automatically.**

GitHub supports version control, collaboration, and documentation, but FAIR also requires attention to metadata, persistent identification, access conditions, interoperability, and reuse permissions.

For appropriate research outputs, archiving a tagged release in a repository such as Zenodo can provide a persistent identifier and a more durable citation record.

### What if my research involves sensitive patient data?

Start by understanding the applicable institutional policies, consent requirements, data-use restrictions, and approved access mechanisms.

FAIR practices can improve metadata, documentation, provenance, and discoverability without exposing protected information.

Never deposit patient-level or otherwise restricted research data in a public repository without appropriate authorization.

### How do FAIR and Open Science relate?

FAIR and Open Science are complementary, but they are not synonymous.

Open Science encourages transparency, collaboration, and the sharing of research outputs where appropriate.

FAIR provides principles for making those outputs discoverable, accessible under defined conditions, interoperable, and reusable.

A research object can be FAIR without being openly available, and an openly available object is not necessarily FAIR.

---

## 2. The FAIR Cookbook: From Principles to Practice

The [FAIR Cookbook](https://faircookbook.elixir-europe.org/) is a community-developed resource containing practical recipes for implementing FAIR practices, particularly in the life sciences.

It helps researchers move from understanding FAIR principles to identifying concrete implementation approaches.

### Explore the FAIR Cookbook

**Website:** [https://faircookbook.elixir-europe.org/](https://faircookbook.elixir-europe.org/)

During the workshop, we will explore how to navigate the Cookbook and identify resources relevant to our research workflows.

### Suggested walkthrough

1. Open the FAIR Cookbook homepage.
2. Explore the available topics and recipes.
3. Identify a recipe relevant to a challenge in your research.
4. Review the recommended practices, tools, and implementation steps.
5. Consider what would be required to adopt the approach in your own research environment.

### Example: Improving Research Metadata

Imagine that your lab has multiple datasets stored across shared drives, but the files have inconsistent names and incomplete documentation.

You might use the FAIR Cookbook to investigate approaches for:

- Developing a data management plan.
- Selecting appropriate metadata standards.
- Using persistent identifiers.
- Improving dataset documentation.
- Establishing data stewardship and preservation practices.

**Discussion question:**

> Which FAIR practice could you realistically begin implementing in your own research this month?

---

## 3. Your FAIR Action Plan

FAIRification does not have to begin with a large institutional initiative.

It can start with a single dataset, script, workflow, or research project.

### Step 1: Identify a research object

Choose something you currently work with:

- A dataset or collection of research files.
- An analysis script or computational workflow.
- A research software repository.
- A laboratory protocol or documentation resource.

### Step 2: Identify one FAIR-related challenge

Consider the following questions:

| FAIR dimension | Question to ask |
|:---|:---|
| **Findable** | Can someone unfamiliar with this project discover and identify the research object? |
| **Accessible** | Are the access mechanisms and restrictions clearly documented? |
| **Interoperable** | Are the formats, variable definitions, and relationships sufficiently standardized? |
| **Reusable** | Are the methods, provenance, software, and reuse conditions documented? |

### Step 3: Choose an achievable improvement

Examples include:

- Create or update a README.
- Develop a data dictionary.
- Establish consistent file-naming conventions.
- Document software versions and dependencies.
- Introduce Git version control for analysis scripts.
- Record data processing steps and quality-control decisions.
- Identify a suitable metadata standard or repository.
- Clarify access and reuse conditions.

### Step 4: Make a commitment

Complete the following:

**Research object:** ___________________________

**FAIR challenge:** ___________________________

**One improvement I will make:** ___________________________

**Who or what do I need to help me?** ___________________________

**When will I implement it?** ___________________________

**How will I know it is complete?** ___________________________

---

## 4. Getting Started: A Practical FAIR Checklist

Use this checklist as a starting point for your own research workflows.

### Findable

- [ ] Give research objects descriptive, consistent names.
- [ ] Create useful metadata and documentation.
- [ ] Identify an appropriate repository or discovery system.
- [ ] Use persistent identifiers where appropriate.

### Accessible

- [ ] Document where research objects are stored.
- [ ] Clarify access permissions and restrictions.
- [ ] Provide instructions for requesting access when needed.

### Interoperable

- [ ] Use documented, widely supported file formats where appropriate.
- [ ] Define variables, units, and categorical values.
- [ ] Adopt relevant community standards and controlled vocabularies.
- [ ] Document relationships between research objects.

### Reusable

- [ ] Maintain a README and data dictionary.
- [ ] Document methods, provenance, and processing decisions.
- [ ] Record software versions and dependencies.
- [ ] Use version control for research code.
- [ ] Clarify licensing and data-use conditions.
- [ ] Follow relevant community standards.

**Remember:** This checklist is a starting point, not a formal FAIR assessment or certification.

---

## 5. Resources for Continued Learning

| Resource | How it can help |
|:---|:---|
| [FAIR Cookbook](https://faircookbook.elixir-europe.org/) | Practical recipes for implementing FAIR practices in the life sciences |
| [The Turing Way](https://book.the-turing-way.org/) | Reproducible, ethical, collaborative, and open research practices |
| [FAIRsharing](https://fairsharing.org/) | Discover metadata standards, databases, and data policies |
| [re3data](https://www.re3data.org/) | Find research data repositories |
| [DataCite](https://datacite.org/) | Persistent identifiers and metadata for research outputs |
| [Zenodo](https://zenodo.org/) | Archive and cite suitable research outputs |
| [Dryad](https://datadryad.org/) | Publish and discover research datasets |
| [GO FAIR](https://www.go-fair.org/) | Guidance and resources for FAIR implementation |

---

## Final Reflection

Think back to the synthetic leukemia dataset we explored at the beginning of the workshop.

We started with a file that could be opened and analyzed but lacked much of the context needed for responsible scientific interpretation.

Throughout the workshop, we explored how metadata, persistent identifiers, standardized terminology, provenance, documentation, and clear reuse conditions can make research objects more FAIR.

**The most important takeaway is that FAIR begins with everyday research practices.**

You do not need to solve every data management challenge immediately. Start with one achievable improvement, make it part of your workflow, and build from there.

> **FAIR by Design: Make your research easier to find, understand, connect, and reuse — from the beginning.**

---

[← Previous: Reusable]({{ '/docs/05-reusable.html' | relative_url }})
