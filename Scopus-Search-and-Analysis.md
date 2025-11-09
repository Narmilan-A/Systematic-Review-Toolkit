# 🔎 Scopus Search, Export & Summary Analysis (CSV / RIS / BibTeX)

This page shows how to **search Scopus by keywords**, **export results** (CSV, RIS, BibTeX), and **summarise/visualise** the corpus. It complements the Rayyan/Paperpile/SciSpace workflow and provides a reproducible summary similar to **Scopus “Analyze search results”.**

---

## 1) Build a robust Scopus query

Scopus supports Boolean and fielded queries. Examples (adjust to your domain):

```text
(TITLE-ABS-KEY("Antarctic*" OR "polar region*" OR "sub-Antarctic"))
AND (TITLE-ABS-KEY(UAV OR "unmanned aerial vehicle" OR drone*))
AND (TITLE-ABS-KEY("vegetation" OR "moss" OR "lichen"))
AND (PUBYEAR > 2000)
AND (LIMIT-TO(DOCTYPE, "ar") OR LIMIT-TO(DOCTYPE, "re"))
AND (EXCLUDE(PUBSTAGE, "aip"))
```

Tips
- Use `TITLE-ABS-KEY()` for topic searches.
- Include synonyms (e.g., `UAV`, `drone*`, `"unmanned aerial vehicle"`).
- Limit years, languages, document types as needed.
- Save the query in Scopus for re-use and provenance.

---

## 2) Export from Scopus (CSV, RIS, BibTeX)

After running your query:
1. Click **Export**.
2. Choose **CSV**, **RIS**, or **BibTeX** (you can export multiple formats).
3. Include fields: **Authors, Title, Year, Source title, Author keywords, Index keywords, Abstract, Affiliations, Cited by, DOI, Author IDs, Funding, Correspondence Address**.
4. Save files into this repo, e.g. `data/exports/scopus/`.

> **Note:** CSV is best for quick analysis. RIS/BibTeX are helpful for Paperpile/Rayyan imports and reproducibility.

---

## 3) Built‑in Scopus “Analyze search results” (quick visual)

Scopus has a native analysis dashboard:
- Click **Analyze search results** → See **Documents by year**, **Source**, **Author**, **Affiliation**, **Country/territory**, **Funding sponsor**, and **Subject area**.
- You can **export tables/figures** from this view. Save screenshots or CSVs into `data/scopus_analysis/` for archiving.

---

## 4) Reproducible local summary (this repo)

Use the provided helper script to **replicate Scopus summaries locally** and create figures/tables for your manuscript.

### A. File layout
```
Systematic-Review-Toolkit/
├── data/
│   ├── exports/
│   │   └── scopus/
│   │       ├── results_YYYYMMDD.csv
│   │       ├── results_YYYYMMDD.ris
│   │       └── results_YYYYMMDD.bib
│   └── scopus_analysis/        # ← outputs saved here
├── tools/
│   └── scopus_summary_analysis.py
└── Scopus-Search-and-Analysis.md
```

### B. Run the analysis
1. Place one or more **Scopus CSV** files under `data/exports/scopus/`.
2. Run the script (in a Python 3 environment with `pandas` and `matplotlib`):
   ```bash
   python tools/scopus_summary_analysis.py        --inputs data/exports/scopus/*.csv        --outdir data/scopus_analysis
   ```
3. Outputs created:
   - `summary_by_year.csv` (+ `summary_by_year.png`)
   - `top_sources.csv` (+ `top_sources.png`)
   - `top_authors.csv` (+ `top_authors.png`)
   - `top_affiliations.csv` (+ `top_affiliations.png`)
   - `top_countries.csv` (+ `top_countries.png`)  *(parsed from affiliation country when available)*
   - `top_keywords.csv` (+ `top_keywords.png`) *(from **Author Keywords** + **Index Keywords**) *

> The script is **fault‑tolerant** with varying Scopus CSV schemas; see inline comments if you need to adapt field names.

---

## 5) Notes on RIS / BibTeX
- Use **RIS** / **BibTeX** for reference managers (Rayyan/Paperpile). If you must analyse these formats locally, convert them to CSV (e.g., `bibtexparser`, `rispy`, or via Zotero export to CSV).
- Keep **original exports** unchanged for provenance, and store **converted/cleaned** versions separately.

---

## 6) Suggested Reporting (Methods snippet)
> “We queried Scopus on DATE using the following Boolean string: [QUERY]. We exported results in CSV/RIS/BibTeX with full fields (Authors, Year, Source, Keywords, Abstracts, Affiliations, DOIs, Citations). We reproduced Scopus’ ‘Analyze search results’ locally using a Python script (pandas/matplotlib) to summarise documents by year, source, authors, affiliations, countries, and keywords. Scripts and outputs are archived under `data/scopus_analysis/` to ensure reproducibility.”

---

## 7) Next steps
- Feed the CSV into **Rayyan** for screening.
- Import RIS/Bib files into **Paperpile** for PDF acquisition.
- Use **SciSpace** for QA/keyword extraction & full‑text review.
- Generate **VOSviewer** maps from the same corpus.

