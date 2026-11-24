# DNA Assembly & Smart Dilution Calculator

**Live App (GitHub Pages):** https://zhuojin05.github.io/dna-assembly-calculator/

A zero-dependency, single-file browser workbench for planning homologous DNA assemblies (**In-Fusion HD**, **NEBuilder HiFi**, **Gibson Assembly**, or custom cloning master mixes). Runs 100% locally via `index.html` (or on GitHub Pages) with no backend, build step, or internet connection required.

## Key Features

- **Flexible Reaction & Kit Scaling**
  - Built-in presets for **5X In-Fusion** (standard 1/5 vol or half-reaction 1/10 vol), **2X NEBuilder HiFi** (1/2 vol), **2X Gibson Master Mix**, or any custom premix volume and ratio (`Auto Ratio` / `Fixed Vol`).
  - Mass-first vector calculation: enter target linearized vector mass (`ng`) and stock concentration (`ng/µL`) to compute exact vector pipetting volume and remaining insert budget.
  - Per-reaction vector overrides (global summary by default, expandable per card) plus customizable premix name, incubation notes, and dilution excess percentage (`⚙ Options`).

- **Constrained Smart Dilution Solver**
  - Solves stoichiometric DNA masses ($M_{\text{insert}} = M_{\text{vector}} \times \text{Ratio} \times L_{\text{insert}} / L_{\text{vector}}$) across `1:1` through `1:100`.
  - Automatically avoids sub-pipettable raw volumes ($< V_{\min}$) without overflowing the available reaction volume budget when paired with large or low-concentration fragments.
  - Interactive 1-click fixes for trace water remainders (`Omit H₂O`, `Set 1:6`, or `Exact 0.00 µL H₂O`).

- **SnapGene `.dna` Cloning History & Cleaved Vector Importer**
  - Client-side binary `.dna` and XZ/LZMA2 `HistoryTree` parser extracts **restriction-cleaved vector size** (subtracting excised MCS/stuffer sequences), PCR fragment lengths, primer pairs, and exact $5'\to 3'$ homology overlaps into each reaction card.
  - Also parses GenBank (`.gb`/`.gbk`) and FASTA files into the Fragment & Vector Library.

- **NanoDrop Auto-Matching & Bench Checklists**
  - Import NanoDrop CSV/TSV exports or paste directly from spreadsheet tables (`Cmd+V` / `Ctrl+V`) with $A_{260}/A_{280}$ and $A_{260}/A_{230}$ purity indicators.
  - Generates **Table 1 (Master Intermediate Dilution Prep Checklist)** aggregating shared dilutions with configurable dead-volume excess, and **Table 2 (Bench Pipetting Matrix)** in recommended pipetting order.
  - Export full protocols as **ELN Markdown**, **CSV**, or **JSON workspace backups**.

## Quick Start

1. **Offline / Local:** Download or clone this repository and double-click `index.html` in any modern browser (Chrome, Edge, Safari, Firefox).
2. **GitHub Pages:** Enable GitHub Pages from the repository root (`index.html`), and open the published URL.
3. Click **`⚡ Load Demo`** in the empty workspace to inspect a 3-construct sample workflow (`EGFP`, `mCherry`, and `pET-28a(+)`), or drop your own `.dna` and NanoDrop files directly.

## License

Released under the [MIT License](LICENSE).
