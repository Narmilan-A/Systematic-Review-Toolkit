# 📊 VOSviewer: Bibliometric Mapping & Network Analysis

VOSviewer is a free desktop tool for building and visualising bibliometric networks from Scopus or Web of Science (WoS) exports. This guide shows how to add **VOSviewer** as the fourth tool in your AI‑assisted systematic‑review workflow, alongside **Rayyan AI**, **Paperpile**, and **SciSpace**.

<img width="3523" height="3157" alt="author_network_all" src="https://github.com/user-attachments/assets/d6456459-a80b-4e64-83c9-5dd22d94a062" />


> ✅ Typical uses: co‑authorship networks, keyword co‑occurrence maps, citation/co‑citation networks, and bibliographic coupling — to reveal hot topics, key authors, and collaboration clusters.

---

## 🚀 Install & Launch

- **Download:** https://www.vosviewer.com/download
- **Requirements:** Java (bundled in most platform-specific downloads).
- **Start:** Open the VOSviewer application (no installation needed for the JAR version).

---

## 📥 What files does VOSviewer need?

Export your final/filtered reference set from **Scopus** or **Web of Science** (after using Rayyan + Paperpile + SciSpace). Recommended formats:

- **Scopus:** `CSV` with citations, authors, affiliations, abstract, and keywords (a.k.a. “CSV (Excel)” export).
- **Web of Science:** `Plain Text` (`.txt`) with Full Record and Cited References.

> Save the raw exports to `data/exports/` in this repository (create folders if needed).

---

## 🧼 Pre‑processing (recommended)

1. **Clean keywords/terms** (singular vs plural, abbreviations) using a **Thesaurus file** (see `templates_vosviewer_thesaurus.txt`).
2. **Remove generic terms** with a **Stoplist** (see `templates_vosviewer_stoplist.csv`).
3. **Deduplicate authors** if obvious variations exist (e.g., “Smith J.” vs “Smith, John”). This is often improved via the thesaurus “equivalent terms” mapping.

> In VOSviewer, you can load the thesaurus during map creation to normalise terms; use stoplist to hide non‑informative words.

---

## 🧭 Quick Workflows

### A) Keyword Co‑occurrence (topics & clusters)
1. **Create > Create a map based on bibliographic data**.
2. **Read data from**: Scopus/WoS export file(s).
3. **Type of analysis**: *Co‑occurrence*; **Unit of analysis**: *All keywords* (or *Author keywords*).
4. Load **Thesaurus** (optional but recommended).
5. **Counting method**: *Full counting* (or *Fractional* if you prefer).
6. **Thresholds**: set minimum occurrences (e.g., 3–5).
7. **Refine**: remove generic/unwanted terms using the **stoplist**.
8. **Finish**: view the map; switch to **Density** or **Cluster** views.

**Outputs to save**:
- `map.txt` and `network.txt` (File ▸ Export ▸ Maps/Network)
- PNG/SVG of the visualisation (File ▸ Export ▸ Visualisation) for figures.
- `items.txt` for term list (useful for appendices).

---

### B) Co‑authorship (collaborations)
1. **Type of analysis**: *Co‑authorship*; **Unit**: *Authors* (or *Organisations* / *Countries*).
2. Set minimum documents/citations per author (e.g., ≥2 docs).
3. Use **fractional counting** to reduce bias from very prolific authors.
4. Inspect clusters for collaboration groups; export figures and tables.

---

### C) Citation / Co‑citation / Bibliographic Coupling
- **Citation**: who cites whom within your set (impact & influence).
- **Co‑citation**: documents cited together (thematic proximity of references).
- **Bibliographic coupling**: documents sharing references (current research fronts).

> Use the same general steps; only the **Type of analysis** changes.

---

## 🎨 Visualisation Tips

- Use **Layout** tab to adjust attraction/repulsion; keep labels readable.
- In **Overlay** visualisation, colour by **Average publication year** to show emerging topics.
- Export both **Cluster** and **Overlay** views for the paper’s figures.

---

## 📦 Recommended Repository Structure

```
Systematic-Review-Toolkit/
├── data/
│   ├── exports/             # Raw Scopus/WoS exports
│   ├── vosviewer/           # VOSviewer outputs
│   │   ├── maps/            # map.txt / network.txt / items.txt
│   │   └── figures/         # exported png/svg
│   └── thesaurus/           # thesaurus & stoplists
├── Rayyan-AI.md
├── Paperpile-Workflow.md
├── SciSpace-Extraction.md
├── VOSviewer-Bibliometrics.md   ← (this file)
└── readme.md
```

---

## 🧩 Thesaurus & Stoplist Templates

- **Thesaurus** (`templates_vosviewer_thesaurus.txt`): two-column file with headers `label,replace_by` to merge variants. Example:
  ```
  label,replace_by
  U A V,UAV
  U.A.V.,UAV
  unmanned aerial vehicle,UAV
  Antarctica,Antarctic
  polar region,Polar regions
  ```

- **Stoplist** (`templates_vosviewer_stoplist.csv`): one term per line to ignore:
  ```
  study
  method
  analysis
  model
  approach
  dataset
  ```

Copy these templates into `data/thesaurus/` and customise for your topic.

---

## 📝 Reporting (Methods section boilerplate)

> “We conducted a bibliometric mapping using VOSviewer (version X.X) on Scopus/Web of Science exports of the screened corpus. Keyword co‑occurrence (minimum occurrences = N; counting method = full/fractional) identified thematic clusters. Co‑authorship and citation analyses were performed to assess collaboration patterns and influence. Thesaurus normalisation and a topic‑specific stoplist were applied to consolidate synonyms and remove generic terms. Visualisations (cluster, density, overlay by average year) were exported for figures; `map.txt`, `network.txt`, and `items.txt` were archived for reproducibility.”

---

## 🧪 Quality Checks

- Do clusters align with your inclusion criteria and research questions?
- Are important terms merged (e.g., “UAV” vs “drone”)?
- Check robustness by varying the **minimum occurrences** threshold.
- Document parameters (thresholds, counting method, date of export) in your manuscript’s Methods/Supplement.

---

## ❓Troubleshooting

- **“No valid records found”**: ensure you used the correct export format and included abstracts/keywords.
- **Garbled characters**: set UTF‑8 when saving/cleaning CSV/TXT; avoid Excel auto‑formatting DOIs.
- **Overcrowded map**: raise the threshold or switch to density view; reduce label size in the Settings panel.

---

### 📎 References
- VOSviewer Manual & Examples: https://www.vosviewer.com/
