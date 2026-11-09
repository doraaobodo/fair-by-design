# FAIR by Design Workshop

FAIR by Design: Building Findable, Accessible, Interoperable, and Reusable Research Workflows

This repository contains materials used in a 2-hour workshop to teach F.A.I.R. 
Data Management principles at St. Jude Research Children's Hospital's Knowledge 
in Data Science 2026 Symposium (KIDS26) in November, 2026.

## Workshop Introduction

The FAIR Guiding Principles of Findable, Accessible, Interoperable, and Reusable 
were introduced in 2016 to provide a framework for improving data stewardship 
while supporting reproducibility and machine actionability. This workshop will 
introduce the FAIR data principles as defined by Wilkinson et al 
(Sci Data, 2016) to the St. Jude data science community and provide strategies 
for incorporating FAIR principles throughout the research data life cycle. 
Participants will work through a series of facilitated exercises focused on 
the four FAIR dimensions. We will 1) evaluate metadata and discoverability; 
2) consider appropriate access mechanisms for sensitive data; 3) address 
interoperability through standardized terminology, formats, and metadata; and 
4) address reusability through provenance, documentation, data-use information, 
and reproducible workflows. A final activity will examine FAIR from the 
perspective of computational and AI systems and consider what makes research 
objects machine-actionable. Participants will also be introduced to the FAIR 
Cookbook and other practical resources for continuing their FAIRification 
journey.

## Learning Objectives

**By the end**, you will be able to identify and explain the four FAIR principles and 
recognize examples of their application in biomedical research workflows.

**By the end**, you will be able to evaluate a research dataset or computational 
workflow for FAIR-related gaps in metadata, accessibility, interoperability, 
and reusability.

**By the end**, you will be able to assess basic machine-actionability requirements 
and identify at least two changes that would improve the ability of computational 
or AI systems to discover, interpret, or reuse a research object.

## FAIR practices

- **Findable:** Descriptive README, searchable website, repository topics, and a versioned DOI after Zenodo archiving.
- **Accessible:** Public HTML and Markdown over HTTPS. Never publish patient-identifiable or confidential data.
- **Interoperable:** Markdown and YAML; standard citation metadata.
- **Reusable:** CC BY 4.0 license, source history, release tags, and attribution.

## Versioning and archival

GitHub Pages URLs are not guaranteed persistent identifiers.

* After creating materials, create a tagged GitHub release (e.g. `v1.0.0`)
* Archive repo through Zenodo to obtain a DOI. 
* Update `CITATION.cff` with the DOI and version. 

## Attribution

Workshop material template prepared for KIDS26. Replace placeholder author details in `CITATION.cff` before publishing.
