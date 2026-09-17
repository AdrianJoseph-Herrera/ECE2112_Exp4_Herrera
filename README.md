# ECE 2112: Advanced Computer Programming and Algorithms
## Experiment 4: Data Wrangling and Data Visualization

![Python](https://img.shields.io/badge/Python-3.x-blue.svg)
![Pandas](https://img.shields.io/badge/Pandas-Data%20Analysis-150458.svg)
![Matplotlib](https://img.shields.io/badge/Matplotlib-Visualization-orange.svg)
![Seaborn](https://img.shields.io/badge/Seaborn-Statistical%20Plots-green.svg)

---

### 📌 Project Overview
This repository contains the complete implementation and documentation for **Experiment 4: Data Wrangling and Data Visualization** in ECE 2112. The project focuses on importing, feature engineering, conditional filtering, and visualizing student performance data from an ECE Board Exam dataset using Python's core data science stack (`pandas`, `matplotlib`, and `seaborn`).

### 🎯 Intended Learning Outcomes
1. Filter tabular data using explicit categorical and numerical conditions via boolean indexing.
2. Construct focused DataFrames by selecting relevant features while keeping the original source dataset unaltered.
3. Summarize numerical relationships across categorical variables using grouped aggregations (`.groupby()`).
4. Present data comparisons through clean, well-labeled, and scale-consistent visualizations.
5. Provide objective, sample-specific statistical interpretations that adhere to non-causal analysis guidelines.

---

### 📂 Repository Structure

```text
.
├── ECE2112_PA4.ipynb      # Complete Jupyter Notebook containing code, plots, and markdown
├── board2.xlsx            # Source Excel dataset containing student exam marks
└── README.md              # Project documentation and summary
```

---

### 🛠️ Environment & Dependencies

This project requires **Python 3.8+** along with the following packages:

* `pandas` - Data manipulation and feature computation
* `matplotlib` - Figure layout management and plotting engine
* `seaborn` - High-level statistical visualizations
* `openpyxl` - Excel file reading support

To install all dependencies locally, run:

```bash
pip install pandas matplotlib seaborn openpyxl
```

---

### 🚀 Getting Started & Execution

1. **Clone this repository:**
   ```bash
   git clone [https://github.com/YOUR_USERNAME/ECE2112-Experiment-4.git](https://github.com/YOUR_USERNAME/ECE2112-Experiment-4.git)
   cd ECE2112-Experiment-4
   ```

2. **Verify Dataset Placement:**
   Ensure `board2.xlsx` is present in the working directory alongside `ECE2112_PA4.ipynb`.

3. **Launch the Notebook:**
   Open the workspace in Jupyter Notebook, VS Code, Google Colab, or any mobile Jupyter client (e.g., Juno):
   ```bash
   jupyter notebook ECE2112_PA4.ipynb
   ```

4. **Run All Cells:**
   Execute cells sequentially from top to bottom.

---

### 📊 Programming Problems & Implementation Details

#### **Feature Engineering (Data Preprocessing)**
The source Excel file `board2.xlsx` includes individual subject marks (`Math`, `Electronics`, `GEAS`, `Communication`) but omits the combined average. The notebook programmatically derives the `Average` column prior to filtering:
```python
df_raw['Average'] = df_raw[['Math', 'Electronics', 'GEAS', 'Communication']].mean(axis=1)
```

#### **Problem A: Visayas Communication DataFrame (`VisComm`)**
* **Filters:** Students whose `Hometown` is **Visayas** AND `Track` is **Communication**.
* **Retained Columns:** `Name`, `Gender`, `Math`, `Electronics`, `Average` (in exact order).
* **Output:** Displays the filtered DataFrame (`5 rows`) and calculates total row count dynamically.

#### **Problem B: Visayas Female DataFrame (`VisFemale`)**
* **Filters:** Students whose `Hometown` is **Visayas** AND `Gender` is **Female**.
* **Retained Columns:** `Name`, `Track`, `GEAS`, `Electronics`, `Average` (in exact order).
* **Output:** Displays the complete `VisFemale` DataFrame (`6 rows`), followed by a secondary conditional view displaying students with an `Average >= 60` (`4 rows`) without mutating or overwriting `VisFemale`.

#### **Problem C: Category-Average Visualization & Analysis**
* **Summaries:** Computes sample group means using Pandas `.groupby()` for `Track`, `Gender`, and `Hometown`.
* **Visualization:** Generates a single 3-panel figure using Seaborn bar plots with shared Y-axis scaling (`sharey=True`), custom color palettes, and inline data value annotations on top of each bar.
* **Key Results:**
  * **Track:** Communication achieved the highest mean average (**67.98**).
  * **Gender:** Male students achieved the highest mean average (**67.18**).
  * **Hometown:** Luzon achieved the highest mean average (**68.08**).

---

### 📜 Methodological Note & Interpretation Rule
All conclusions drawn in this project describe the observed sample dataset exclusively. Observed variations in group means represent descriptive metrics of the sample and do not imply or establish causal relationships between demographic characteristics and academic performance.
