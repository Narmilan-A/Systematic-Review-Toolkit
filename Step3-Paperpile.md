# 📄 Step 3 – Paperpile PDF Management and Organisation

**Paperpile** ([https://paperpile.com](https://paperpile.com)) is a cloud-based reference manager that simplifies **PDF organization**, **reference syncing**, and **collaborative access** through Google Drive integration.  
In this step, you will import screened references (from Rayyan), download full-text PDFs, and prepare them for subsequent analysis with **SciSpace Copilot**.
<img width="979" height="620" alt="image" src="https://github.com/user-attachments/assets/08885756-d37d-4b4e-a699-6a61246d78cf" />

---

## 🎯 Objectives
- Centralise all references and PDFs in a single, searchable workspace.  
- Ensure seamless integration between **Rayyan**, **Paperpile**, **Google Drive**, and **SciSpace**.  
- Maintain consistent file naming, metadata, and version control.

---

## 🧩 Step 1 – Import References
1. Export the final screened references from **Rayyan** as a `.RIS` or `.BibTeX` file.  
2. Open **Paperpile** via the Chrome extension or web interface.  
3. Click **Import → File** and select your exported `.RIS` / `.BibTeX` file.  
4. Verify that all metadata (title, authors, DOI, journal, etc.) have imported correctly.

> 💡 *Tip:* Keep your Rayyan export files archived in `data/exports/rayyan/` for provenance and reproducibility.

---

## ☁️ Step 2 – Integrate With Google Drive
- Enable automatic syncing in **Settings → Storage → Google Drive**.  
- Paperpile will create a dedicated folder:  
  `My Drive/Paperpile/`  
- PDFs are automatically organised by **year**, **topic**, or **collection**.  
- You can also share folders with collaborators for co-review or annotation.

> 🔒 *Note:* Ensure your Google Drive has adequate storage space, especially for large systematic review datasets.

---

## 🏛️ Step 3 – Enable University Proxy Access
- Navigate to **Settings → Library Access → Proxy Settings**.  
- Add your university’s proxy or use the built-in list (e.g., “University of Wollongong Library Proxy”).  
- This ensures full-text access to **subscription-based** journals directly through Paperpile.

> 🎓 *Example:* When you click *View PDF*, Paperpile will automatically route through your university’s proxy and download the institutional copy.

---

## 📥 Step 4 – Retrieve Full-Text PDFs
- Use **Paperpile’s built-in PDF finder**, which connects to:
  - CrossRef
  - arXiv
  - Publisher APIs  
- For missing files, manually upload PDFs from your local downloads.  
- Use legal open-access alternatives like **Unpaywall** (built-in) to locate free versions.

> ⚠️ *Avoid unauthorised sources (e.g., Library Genesis) unless explicitly permitted by institutional policy.*

---

## 📦 Step 5 – Export and Organise PDFs for Analysis
- Use **Google Drive Sync** or **Bulk Export** to create a local backup.  
- Rename files consistently (e.g., `Author_Year_Title.pdf`).  
- Store the exported PDFs in:  
  `data/paperpile_pdfs/`  
- These files can now be uploaded to **SciSpace Copilot** for AI-assisted full-text analysis.

> 🧠 *Recommendation:* Tag references by inclusion status (e.g., “Included for extraction”) to streamline downstream processing.

---

## 📘 Output Checklist
| Task | Output | Folder |
|------|---------|---------|
| Import references | Paperpile library with metadata | – |
| PDF synchronisation | Google Drive auto-sync folder | `My Drive/Paperpile/` |
| Proxy access | Institutional login | – |
| Full-text retrieval | Complete set of PDFs | `data/paperpile_pdfs/` |
| Prepared dataset | Ready for SciSpace upload | `data/paperpile_pdfs/` |

---

**Next Step → [Step 4 – SciSpace Extraction](./Step4-SciSpace-Extraction.md)**
