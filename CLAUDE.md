# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

**EcoLens** — an academic data science project for NUS DSS5201 analyzing global plastic pollution corporate accountability using the "Break Free From Plastic" 2019–2020 dataset. The core research question identifies "Local Giants": companies that rank in a country's top plastic polluters but are invisible in global Top 10 rankings.

## Environment Setup

```bash
cd src
python3.12 -m venv venv-dss5201
source venv-dss5201/bin/activate
pip install -r requirements.txt
```

## Running the Project

```bash
# Launch notebook
source src/venv-dss5201/bin/activate
jupyter notebook src/DSS5201_Group_Project.ipynb

# Or run notebook non-interactively
jupyter nbconvert --to notebook --execute src/DSS5201_Group_Project.ipynb
```

## Architecture

All analysis lives in a single notebook: `src/DSS5201_Group_Project.ipynb`. The data pipeline flows as:

1. **Load & Clean** — `data/plastics.csv` (13,380 raw → 9,720 clean records). Removes Grand Total/Unbranded aggregates, standardizes country names, fills plastic-type columns with 0 for NaN.
2. **Enrich** — Maps 63 countries to 6 continents via `pycountry_convert`.
3. **Score** — Computes a "Climate Impact Score" as a weighted sum of plastic counts using per-type CO₂e emission factors (PET: 2.32, HDPE: 1.89, LDPE: 2.11, PP: 1.95, PS: 3.41, PVC: 2.45, Other: 2.22 kg CO₂e/kg).
4. **Visualize** — Matplotlib/Seaborn charts targeting three visualization outputs: Asia Top 10, Local Giants analysis, and 2019 vs. 2020 trend comparison.

### Key Dataset Columns

- Plastic types: `empty`, `hdpe`, `ldpe`, `o` (other), `pet`, `pp`, `ps`, `pvc`
- Identifiers: `parent_company`, `country`, `year`
- Derived: `continent`, `climate_impact_score`
