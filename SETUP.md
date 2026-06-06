# Setup Instructions

## Requirements

- Python 3.x with Jupyter installed (`pip install notebook`)
- R 3.6+ installed on your machine
- IR kernel for Jupyter (`install.packages('IRkernel')` in R, then `IRkernel::installspec()`)

## R Packages Required

All packages used are from base R, no additional installs needed.

## Data Setup

1. Go to https://www.kaggle.com/datasets/dansbecker/nba-shot-logs
2. Download the dataset (free Kaggle account required)
3. Place the following files into the `data/` folder:
   - `Shot_data_clean.csv`
   - `Players_clean.csv`

## Running the Notebook

```bash
jupyter notebook nba_data_analysis.ipynb
```

Select **Kernel > Restart & Run All** to execute all cells from scratch.

## Expected Runtime

Approximately 2–4 minutes on a standard laptop. The Monte Carlo section (10,000 permutations) is the most computationally intensive step.
