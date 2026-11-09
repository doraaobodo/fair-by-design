# FAIR by Design workshop

A two-hour, Markdown-first workshop on FAIR biomedical research workflows.

## Website

This repository is configured for GitHub Pages with Jekyll and Just the Docs.

1. Create a public GitHub repository named `fair-by-design`.
2. Upload all files, including `_config.yml` and the `docs/` folder, to the repository root.
3. Replace `USERNAME` in `_config.yml` and `index.md` with your GitHub username or organization.
4. Set `url: "https://USERNAME.github.io"` and `baseurl: "/fair-by-design"` in `_config.yml` (for a project site).
5. In repository **Settings → Pages**, select **Deploy from a branch**, branch `main`, folder `/(root)`.
6. Wait for GitHub Pages to publish, then visit `https://USERNAME.github.io/fair-by-design/`.

## FAIR practices

- **Findable:** Descriptive README, searchable website, repository topics, and a versioned DOI after Zenodo archiving.
- **Accessible:** Public HTML and Markdown over HTTPS. Never publish patient-identifiable or confidential data.
- **Interoperable:** Markdown and YAML; standard citation metadata.
- **Reusable:** CC BY 4.0 license, source history, release tags, and attribution.

## Versioning and archival

After reviewing the materials, create a tagged GitHub release (e.g. `v1.0.0`) and archive it through Zenodo to obtain a DOI. Update `CITATION.cff` with the DOI and version. GitHub Pages URLs are not guaranteed persistent identifiers.

## Attribution

Workshop material template prepared for KIDS26. Replace placeholder author details in `CITATION.cff` before publishing.
