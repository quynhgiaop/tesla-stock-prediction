# Tesla Stock Prediction

A time-series project to predict Tesla (TSLA) stock prices.

This project uses **[uv](https://docs.astral.sh/uv/)** to manage Python and packages. uv installs the right Python version and every package for you, so everyone on the team gets exactly the same setup.

> **What's a terminal?**
> - **Windows:** press the Start button, type `powershell`, and open **Windows PowerShell**.
> - **Mac:** press `Cmd + Space`, type `Terminal`, and press Enter.

---

## Setup (first time only)

Type each command in the terminal and press Enter.

**1. Install uv**

Windows (PowerShell):
```
powershell -ExecutionPolicy ByPass -c "irm https://astral.sh/uv/install.ps1 | iex"
```
Mac / Linux:
```
curl -LsSf https://astral.sh/uv/install.sh | sh
```
Then **close the terminal and open a new one**, and check it works:
```
uv --version
```

**2. Go to the project folder**
```
cd path/to/tesla-stock-prediction
```
Tip: type `cd ` (with a space) and drag the folder into the terminal window to fill in the path.

**3. Install everything**
```
uv sync
```
This downloads the correct Python version (you don't need to install Python yourself) and all the packages. It can take a minute the first time.

---

## Running code

Put `uv run` in front of any Python command, for example:
```
uv run python my_script.py
```
You don't need to activate anything. `uv run` always uses the project's own Python and packages.

---

## Using Jupyter notebooks

Start Jupyter from the project folder:
```
uv run jupyter lab
```
It opens in your web browser. Open the `notebooks` folder on the left, then click **File → New → Notebook** to create one (choose the **Python 3** kernel if asked). All the project's packages are already available inside.

To stop Jupyter, go back to the terminal and press `Ctrl + C`.

Tip: before committing, click **Edit → Clear Outputs of All Cells** and save. This keeps the files small and avoids conflicts with teammates.

---

## Getting the data

Before running any other notebook, run **`extract_data.ipynb`** once.

1. Open `extract_data.ipynb`.
2. Run all cells (**Kernel → Restart & Run All**).
3. The dataset is saved to the `data/` folder:

   ```
   data/
   └── tesla_combined.csv
   ```

The dataset contains data for 5 years from 16.11.2026 backwards:

| Column | Source |
|---|---|
| `tsla_close` | Tesla (`TSLA`) |
| `oil_close` | WTI crud
| `lit_close` | Lithium & Battery ETF (`LIT`) |
| `nasdaq_close` | Nasda

> **Note:** You only need to run this once. If the file already exists, the notebook will **not** overwrite it, so everyone works with the same data.

---

## Adding a new package

```
uv add <package-name>
```
For example `uv add scikit-learn`. This installs the package and records it in `pyproject.toml` and `uv.lock`. Commit both files so teammates get it too.

When you pull changes from teammates, run `uv sync` again to get any new packages.

---

## Packages included

| Package | What it's for |
|---|---|
| `pandas` | Working with tables of data |
| `numpy` | Numbers and calculations |
| `matplotlib` | Making charts |
| `yfinance` | Downloading stock prices from Yahoo Finance |
| `jupyterlab` | Writing and running notebooks |

---

## Project files

| File | What it is |
|---|---|
| `pyproject.toml` | The list of packages the project needs |
| `uv.lock` | The exact package versions, so everyone has the same setup. Don't edit by hand. |
| `notebooks/` | Put your Jupyter notebooks here |
| `data/` | Put data files here. Its contents are not saved in git. |
| `.python-version` | The Python version the project uses (3.12) |
| `.venv/` | The project's private Python environment. Created by `uv sync`, not saved in git. |

---

## Common problems

| Problem | Fix |
|---|---|
| `uv: command not found` (or "not recognized") | Close the terminal and open a new one after installing uv. If it still fails, repeat step 1. |
| `No module named ...` | Run `uv sync`, and make sure you start your script with `uv run`. |
| A teammate added a package and your code fails | Run `uv sync`. |
