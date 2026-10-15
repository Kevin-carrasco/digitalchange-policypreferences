# [Working title] Percepciones del cambio tecnológico y preferencias de política social de los trabajadores en 27 países de la OCDE

Replication materials and writing environment for a manuscript in preparation.
The paper is written in Quarto and the analyses run in R.

**Status:** data preparation and exploratory analysis.

## Overview

The study examines whether perceived technological threat to one's own job
(egotropic, Q25) and expectations about the effects of artificial intelligence
on the country (sociotropic, Q26) shape the relative support for three policy
responses to digitalisation (Q27): social investment, compensation and closure.
It uses the 2024 OECD *Risks That Matter* (RTM) survey and estimates multilevel
linear models (`lme4::lmer`) with random intercepts, and random slopes for the
egotropic threat, by country. Four country-level indicators (Gini, log GDP per
capita, unemployment rate and public social expenditure, standardised across the
27 countries) enter as level-2 predictors and moderators.

## Data

| Source | File | Notes |
|---|---|---|
| OECD Risks That Matter 2024 | `input/original/OECD_RTM_2024.dta` | Main analytic source |
| World Bank / OECD indicators | retrieved via `WDI` in `procesamiento/` | Gini, GDP per capita, unemployment, social expenditure |

Raw RTM microdata are not redistributed in this repository. They are obtained
directly from the OECD under its access conditions and must be placed in
`input/original/` with the file names above before running the pipeline. The
questionnaires are included for documentation:
`OECD_Risks_That_Matter_2024_Core_Questionnaire.pdf` and
`..._Background_Questionnaire.pdf`.

**Analytic sample.** Respondents who are employed or temporarily absent from
work (`s10` = 1, 4, 5), the only ones administered the Q25 battery. Job seekers
and those not seeking work (`s10` = 2, 3) enter an extension that uses the
sociotropic expectations only.

## Repository structure

```
tech-anxiety-repertoires/
├── paper.qmd                  # Main manuscript
├── 01-introduction.qmd        # Manuscript sections, included from paper.qmd
├── 03-methods.qmd
├── 04-results.qmd
├── 05-discussion.qmd
├── 06-conclusion.qmd
├── 07-appendix.qmd
├── references.qmd
├── title.tex                  # Quarto/LaTeX title partial (authblk)
│
├── procesamiento/
│   ├── procesamiento.qmd      # Data preparation: recoding, scales, country data
│   └── analysis.qmd           # Exploratory analysis and models
│
├── input/
│   ├── original/              # Raw RTM microdata (not versioned; see Data)
│   ├── proc/                  # Processed objects written by procesamiento.qmd
│   │   ├── data.RData         # Individual-level analytic file
│   │   ├── country_data.RData # Country-level means
│   │   ├── digitalization.RData # Q25 items
│   │   ├── expectations.RData   # Q26 items
│   │   └── policies.RData       # Q27 items
│   ├── bib/                   # tech-anxiety.bib, sage-harvard.csl, apa6.csl
│   └── css/                   # Styles for HTML output
│
└── output/
    └── figures/               # Figures written by the analysis
```

## Funding

Millennium Nucleus on the Evolution of Work (M-NEW), NCS2024_021.

## Contact

Kevin Carrasco, Millennium Nucleus on the Evolution of Work (M-NEW),
Universidad de Chile. kevin.carrasco@uchile.cl
ORCID: [0000-0002-9348-8361](https://orcid.org/0000-0002-9348-8361)
