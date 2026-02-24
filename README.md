# Project #2: Automation of Concrete Mix Design

**Client:** Nebraska Department of Transportation (NDOT)  
**Group K:** Mina Awad, Nick Meier, Owen Betts  
**Course:** CIVE 202 — Civil Engineering Analysis II  
**University of Nebraska-Omaha**  
**Date:** February 24, 2026

---

## Project Summary

This project automates the NDOT Concrete Mix Design Excel workbook by translating all calculations from the Mix Design tab into a Python-based system. The program collects 16 user-defined design parameters via sequential input prompts, executes the full calculation chain, and produces a formatted weight chart for one cubic yard of concrete. Four realistic mix scenarios are included for verification and validation.

---

## Repository Contents

| File | Description |
|------|-------------|
| `Project_2_Group_K.ipynb` | Jupyter Notebook with all functions, user input prompts, and 4 scenario runs |
| `Project2__group_K_SOW.docx` | Scope of Work document |
| `Project2_GanttChart_updated.xlsx` | Gantt Chart showing project schedule and task assignments |
| `Project2_FlowDiagram.pdf` | Flow diagram of the Excel-to-Python conversion process |
| `Annotated_Code_Document.docx` | Line-by-line code explanation (ACD) |
| `Technical_Report.docx` | Written technical report with Introduction, Methods, Results & Discussion, References |
| `Mix_Scenarios_Documentation.docx` | Research documentation for the four concrete mix scenarios |
| `README.md` | This file — project summary and user guide |

---

## User Guide: Sequential Input Prompts

When you run the integrated mix design cell in the Jupyter Notebook, the program will prompt you to enter 16 design parameters in the following order. Enter each value and press Enter to proceed.

### Step 1 — Project Information
| Prompt | Example Input | Notes |
|--------|---------------|-------|
| `Enter project number:` | `404222` | Integer project ID |
| `Enter class of concrete:` | `Class 47B` | Text description |

### Step 2 — Cementitious Material Weights
| Prompt | Example Input | Units |
|--------|---------------|-------|
| `Enter weight of cement, A (lb/yd³):` | `600.0` | lb/yd³ |
| `Enter weight of fly ash, B (lb/yd³):` | `0.0` | lb/yd³ |
| `Enter weight of silica fume, C (lb/yd³):` | `0.0` | lb/yd³ |
| `Enter weight of other SCM, D (lb/yd³):` | `0.0` | lb/yd³ |

### Step 3 — Design Parameters
| Prompt | Example Input | Units |
|--------|---------------|-------|
| `Enter water-cement ratio, E:` | `0.42` | Dimensionless |
| `Enter target air content, F (%):` | `6.0` | Percent |

### Step 4 — Aggregate Proportions
| Prompt | Example Input | Units |
|--------|---------------|-------|
| `Enter fine aggregate percentage, G (%):` | `40.0` | Percent |
| `Enter coarse aggregate percentage, H (%):` | `55.0` | Percent |
| `Enter other aggregate percentage, I (%):` | `5.0` | Percent |

> **Note:** G + H + I should sum to 100%.

### Step 5 — Specific Gravities
| Prompt | Example Input | Units |
|--------|---------------|-------|
| `Enter specific gravity of cement, J:` | `3.15` | Dimensionless |
| `Enter specific gravity of fly ash, K:` | `2.30` | Dimensionless |
| `Enter specific gravity of silica fume, L:` | `2.20` | Dimensionless |
| `Enter specific gravity of other SCM, M:` | `2.60` | Dimensionless |
| `Enter specific gravity of fine aggregate, N:` | `2.63` | Dimensionless |
| `Enter specific gravity of coarse aggregate, O:` | `2.65` | Dimensionless |
| `Enter specific gravity of other aggregate, P:` | `2.60` | Dimensionless |

> **Tip:** If a material is not used in your mix (e.g., no fly ash), enter `0.0` for its weight. You must still enter a specific gravity value — any valid number (e.g., `2.30`) is acceptable since the volume will be zero.

### Output
After all inputs are entered, the program will display:
1. **Intermediate calculations** — all volumes (R through X) in ft³
2. **Volume verification** — confirms R+S+T+U+V+W+X = 27.000 ft³
3. **Final weight chart** — all component weights and total weight in lb/yd³

---

## Four Verification Scenarios

| Scenario | Description | Cement (lb) | W/C Ratio | Air (%) | Source |
|----------|-------------|-------------|-----------|---------|--------|
| 1 | NDOT Class 47B — Standard Pavement | 600 | 0.42 | 6.0 | NDOT Std. Specs (2017) |
| 2 | NDOT Class 47BR — Bridge Deck | 658 | 0.40 | 6.0 | NDOT Std. Specs (2017) |
| 3 | Fly Ash Replacement — Sustainable Pavement | 480 + 120 FA | 0.44 | 6.5 | ACI 211.1 / NDOT Guidelines |
| 4 | High-Performance — Silica Fume | 650 + 50 FA + 40 SF | 0.35 | 5.5 | ACI 211.1 / NDOT Guidelines |

---

## How to Run

1. Open `Project_2_Group_K.ipynb` in Jupyter Notebook or JupyterLab
2. Run all cells in Part 1 to define constants and functions
3. Run the Part 2 cell for the interactive input workflow, or skip to Part 3 to view the four pre-defined scenario results
4. Part 4 generates the comparison table and verification summary

**Requirements:** Python 3.x with `pandas` and `numpy` installed.

---

## References

- ACI Committee 211. (2009). *Standard practice for selecting proportions for normal, heavyweight, and mass concrete* (ACI 211.1-91). American Concrete Institute.
- NDOT. (2017). *Standard specifications for highway construction*. Nebraska Department of Transportation. https://dot.nebraska.gov/media/g4qp4y0d/2017-specbook.pdf
- NDOT. (2024). *Concrete mix design submittal spreadsheet*. Nebraska Department of Transportation. https://dot.nebraska.gov/media/jp3paote/mix-design-submittal.xlsx
- NDOT. (2024b). *Optimized aggregate gradations for Portland cement concrete mix designs evaluation*. Nebraska Department of Transportation. https://dot.nebraska.gov/media/3isfdv45/final-report-p336.pdf
