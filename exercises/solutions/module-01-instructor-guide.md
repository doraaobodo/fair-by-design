---
layout: default
title: "Module 1 - Instructor Guide"
nav_exclude: true
search_exclude: true
---

# Instructor guide: Data Reuse Challenge

**Suggested timing:** 2 minutes scenario; 3 minutes independent inspection; 3 minutes whole-room discussion; 2 minutes FAIR debrief.

## What participants may notice

- **Findable:** No descriptive dataset title, authors/contacts, identifier, repository record, study description, or discovery metadata. The filename is not a reliable version identifier.
- **Accessible:** The collaborator supplied a file, but there is no documented access process, authentication/authorization policy, or durable access location. Do not imply that pediatric clinical data should be made public.
- **Interoperable:** `PtID`, `dx`, `resp`, `sample`, `gene`, `val`, `day`, and `grp` lack definitions. `ALL`/`AML` are not explained; `resp` uses 0/1/2 with no codebook; `val` has no units, normalization method, or assay type. The meaning of `day` and `grp` is unknown.
- **Reusable:** Missing study protocol, data dictionary, sampling/measurement methods, provenance, quality-control notes, transformation history, version, reuse permissions, and missing-value conventions. The synthetic example also lacks evidence that records are comparable.
