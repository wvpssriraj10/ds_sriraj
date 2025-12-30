# ds_analysis

## Project Overview

This project analyzes how market sentiment (Fear vs. Greed) relates to trade behavior, risk exposure, and realized profitability.  
Two raw data sources are combined:
- A **historical trade log** with detailed trade-level information.
- A **fear–greed index** providing daily market sentiment.

The data is cleaned and merged in `notebook_1.ipynb`, engineered features are created (e.g., trade volume, risk score, sentiment encoding), and exploratory analysis plus visualizations are performed in `notebook_2.ipynb`.  
Summary findings and interpretation are documented in `ds_report.pdf`.

## Folder Structure

At the project root:

- `notebook_1.ipynb` — Data loading, cleaning, feature engineering, and creation of `csv_files/processed_data.csv`.
- `notebook_2.ipynb` — Analysis and visualizations based on `processed_data.csv`.
- `fear_greed_index.csv` — Raw sentiment / fear–greed index data.
- `historical_data.csv` — Raw historical trade data.
- `ds_report.pdf` — Written analytical report summarizing the workflow and insights.
- `README.md` — This documentation file.

Subfolders:

- `csv_files/`
  - `processed_data.csv` — Cleaned and engineered dataset produced by `notebook_1.ipynb`.

- `outputs/`
  - `pnl_vs_sentiment.png` — Boxplot of closed PnL by sentiment.
  - `leverage_vs_sentiment.png` — Bar chart of average risk score by sentiment.
  - `volume_vs_sentiment.png` — Line plot of total trade volume by sentiment.

(Plot files are created by running `notebook_2.ipynb`; they may not exist until notebooks are executed.)

## Execution Steps

1. **Set up environment**
   - Ensure you have Python 3.9+ installed.
   - Install required Python packages (see **Dependencies** below).

2. **Run the data preparation notebook**
   - Open `notebook_1.ipynb` in JupyterLab, VS Code, or another Jupyter-compatible environment.
   - Run all cells in order.
   - This will:
     - Load `historical_data.csv` and `fear_greed_index.csv`.
     - Standardize and merge them on date.
     - Engineer features such as `trade_volume`, `profit_flag`, `risk_score`, and numeric `sentiment`.
     - Export `csv_files/processed_data.csv`.

3. **Run the analysis notebook**
   - Open `notebook_2.ipynb`.
   - Run all cells in order.
   - This will:
     - Load `csv_files/processed_data.csv`.
     - Compute grouped statistics by sentiment (mean/median PnL, average risk score, volumes, etc.).
     - Identify high-risk losing trades.
     - Generate plots and save them under `outputs/`.

4. **Review the report**
   - Open `ds_report.pdf` to read a structured summary of the objective, methodology, key observations, and limitations.

## Dependencies

Install the following Python packages in your environment:

- `pandas`
- `matplotlib`
- `numpy` (used indirectly by pandas/matplotlib and recommended)

You can install them via:

```bash
pip install pandas matplotlib numpy
```

If you are using a specific Python executable:

```bash
python -m pip install pandas matplotlib numpy
```

## Reproducibility Instructions

To fully reproduce the analysis and results:

1. **Clone or copy the project folder**
   - Ensure the directory structure is preserved:
     - `ds_analysis/`
       - `csv_files/processed_data.csv` (or generate via `notebook_1.ipynb`)
       - `outputs/` (will be populated by `notebook_2.ipynb`)
       - `fear_greed_index.csv`
       - `historical_data.csv`
       - `notebook_1.ipynb`
       - `notebook_2.ipynb`
       - `ds_report.pdf`
       - `README.md`

2. **Create and activate a clean environment (recommended)**
   - Using `venv`, for example:
   ```bash
   python -m venv .venv
   .venv\Scripts\activate  # Windows
   # source .venv/bin/activate  # Linux/macOS
   ```

3. **Install dependencies**
   - Run:
   ```bash
   pip install pandas matplotlib numpy
   ```

4. **Run notebooks in order**
   - Start Jupyter (e.g., `jupyter lab` or `jupyter notebook`) or use an IDE like VS Code.
   - Execute all cells in `notebook_1.ipynb`.
   - Then execute all cells in `notebook_2.ipynb`.

5. **Verify outputs**
   - Confirm that:
     - `csv_files/processed_data.csv` exists and is non-empty.
     - `outputs/pnl_vs_sentiment.png`, `outputs/leverage_vs_sentiment.png`, and `outputs/volume_vs_sentiment.png` are created.
     - The results and findings correspond to those summarized in `ds_report.pdf`.

Following these steps in a clean environment with the specified dependencies should reproduce the core tables, figures, and analytical conclusions of the project.

