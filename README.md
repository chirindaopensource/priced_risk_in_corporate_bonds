# **`README.md`**

# Priced Risk in Corporate Bonds: An Empirical Replication Pipeline

<!-- PROJECT SHIELDS -->
[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](https://opensource.org/licenses/MIT)
[![Python Version](https://img.shields.io/badge/python-3.10%2B-blue.svg)](https://www.python.org/)
[![arXiv](https://img.shields.io/badge/arXiv-2604.05699-b31b1b.svg)](https://arxiv.org/abs/2604.05699)
[![Journal](https://img.shields.io/badge/Journal-ArXiv%20Preprint-003366)](https://arxiv.org/abs/2604.05699)
[![Year](https://img.shields.io/badge/Year-2026-purple)](https://github.com/chirindaopensource/priced_risk_in_corporate_bonds)
[![Discipline: FinEcon](https://img.shields.io/badge/Discipline-Financial%20Economics-00529B)](https://github.com/chirindaopensource/priced_risk_in_corporate_bonds)
[![Discipline: MathFin](https://img.shields.io/badge/Discipline-Mathematical%20Finance-00529B)](https://github.com/chirindaopensource/priced_risk_in_corporate_bonds)
[![Discipline: Econometrics](https://img.shields.io/badge/Discipline-Econometrics-00529B)](https://github.com/chirindaopensource/priced_risk_in_corporate_bonds)
[![Data: TRACE](https://img.shields.io/badge/Data-Enhanced%20TRACE%20WRDS-lightgrey)](https://wrds-www.wharton.upenn.edu/)
[![Data: FISD](https://img.shields.io/badge/Data-Mergent%20FISD%20WRDS-lightgrey)](https://wrds-www.wharton.upenn.edu/)
[![Data: French](https://img.shields.io/badge/Data-Kenneth%20French%20Library-lightgrey)](http://mba.tuck.dartmouth.edu/pages/faculty/ken.french/data_library.html)
[![Data: Goyal](https://img.shields.io/badge/Data-Amit%20Goyal%20Data-lightgrey)](https://sites.google.com/view/agoyal145/)
[![Data: VIX](https://img.shields.io/badge/Data-CBOE%20VIX-lightgrey)](https://www.cboe.com/tradable_products/vix/)
[![Method: CSR](https://img.shields.io/badge/Method-Two--Pass%20CSR-orange)](https://github.com/chirindaopensource/priced_risk_in_corporate_bonds)
[![Method: Fama-MacBeth](https://img.shields.io/badge/Method-Fama--MacBeth%20Regression-orange)](https://github.com/chirindaopensource/priced_risk_in_corporate_bonds)
[![Method: Jackknife](https://img.shields.io/badge/Method-Jackknife%20Resampling-orange)](https://github.com/chirindaopensource/priced_risk_in_corporate_bonds)
[![Code style: black](https://img.shields.io/badge/code%20style-black-000000.svg)](https://github.com/psf/black)
[![Pandas](https://img.shields.io/badge/pandas-%23150458.svg?style=flat&logo=pandas&logoColor=white)](https://pandas.pydata.org/)
[![NumPy](https://img.shields.io/badge/numpy-%23013243.svg?style=flat&logo=numpy&logoColor=white)](https://numpy.org/)
[![SciPy](https://img.shields.io/badge/SciPy-%230C55A5.svg?style=flat&logo=scipy&logoColor=white)](https://scipy.org/)
[![Statsmodels](https://img.shields.io/badge/statsmodels-%23000000.svg?style=flat)](https://www.statsmodels.org/)
[![YAML](https://img.shields.io/badge/YAML-%23CB171E.svg?style=flat&logo=yaml&logoColor=white)](https://yaml.org/)
[![Open Source](https://img.shields.io/badge/Open%20Source-%E2%9D%A4-brightgreen)](https://github.com/chirindaopensource/priced_risk_in_corporate_bonds)

**Repository:** `https://github.com/chirindaopensource/priced_risk_in_corporate_bonds`

**Owner:** 2026 Craig Chirinda (Open Source Projects)

## Table of Contents
- [Introduction](#introduction)
- [Theoretical Background](#theoretical-background)
- [Features](#features)
- [Methodology Implemented](#methodology-implemented)
- [Core Components (Notebook Structure)](#core-components-notebook-structure)
- [Key Callable: run_end_to_end_research_pipeline](#key-callable-run_end_to_end_research_pipeline)
- [Prerequisites](#prerequisites)
- [Installation](#installation)
- [Input Data Structure](#input-data-structure)
- [Usage](#usage)
- [Output Structure](#output-structure)
- [Project Structure](#project-structure)
- [Customization](#customization)
- [Contributing](#contributing)
- [Recommended Extensions](#recommended-extensions)
- [License](#license)
- [Citation](#citation)
- [Acknowledgments](#acknowledgments)

## Introduction

This project is an independent, professional-grade implementation of the ideas, methodologies, and experimental protocols from the paper titled **"Priced Risk in Corporate Bonds"** by the authors:
*   **Alexander Dickerson**
*   **Philippe Mueller**
*   **Cesare Robotti**

This repository provides a complete, end-to-end computational framework for replicating the paper's findings. It delivers a highly optimized, mathematically rigorous pipeline that evaluates whether recently proposed multifactor models (such as the Bai, Bali, and Wen four-factor model) genuinely explain the cross-sectional variation in corporate bond expected excess returns. By implementing state-of-the-art econometric techniques—including misspecification-robust standard errors, exact fractional duration adjustments, and jackknife bias-corrected Sharpe ratios—this codebase establishes a definitive protocol for preventing false discoveries in fixed-income asset pricing.

## Theoretical Background

The implemented methods bridge empirical asset pricing with advanced financial econometrics and fixed-income mathematics.

**1. The Bond CAPM vs. Multifactor Models:**
The pipeline evaluates the baseline Capital Asset Pricing Model for bonds (CAPMB), which relies solely on the value-weighted corporate bond market factor (MKTB). It tests this against complex multifactor models that incorporate downside risk (DRF), credit risk (CRF), liquidity risk (LRF), and intermediary capital constraints.

**2. Factor-Mimicking Portfolios:**
To evaluate nontraded macroeconomic risks (e.g., uncertainty, volatility, long-run consumption), the pipeline projects these shocks onto a basis of traded assets. This translates intangible economic variables into tradable portfolios with identical conditional exposures, enabling direct Sharpe ratio comparisons.

**3. Misspecification-Robust Inference:**
Recognizing that all asset pricing models are approximations, the pipeline implements the Kan, Robotti, and Shanken (2013) methodology. It computes standard errors that remain asymptotically valid even when the fundamental beta-pricing restriction is violated, preventing the spurious identification of "priced" factors.

**4. The Generated Regressor Problem:**
When evaluating mimicking portfolios, the portfolio weights are estimated with error. The pipeline implements the Barillas, Kan, Robotti, and Shanken (2020) jackknife procedure to compute bias-adjusted squared Sharpe ratios and robust alphas, mathematically resolving the generated regressor problem.

Below is a diagram which summarizes the proposed approach:

<div align="center">
  <img src="https://github.com/chirindaopensource/priced_risk_in_corporate_bonds/blob/main/priced_risk_in_corporate_bonds_ipo_main.png" alt="Pipeline Architecture" width="100%">
</div>

## Features

-   **End-to-End Automation:** A singular orchestrator function executes the entire research protocol from raw TRACE/FISD ingestion to final LaTeX table generation.
-   **Dick-Nielsen (2014) TRACE Cleaning:** Fully vectorized resolution of intraday message chains (cancellations, corrections, reversals) ensuring pristine daily volume-weighted average prices.
-   **Exact Fixed-Income Mathematics:** Replaces crude approximations with exact fractional period discounting for Macaulay duration and vectorized Newton-Raphson solvers for Yield-to-Maturity (YTM).
-   **Robust Econometrics:** Implements Shanken (1992) EIV corrections, KRS (2013) misspecification-robust standard errors, and Kan-Robotti (2012) exact eigenvalue rank tests for weak identification.
-   **Lossless Archival:** Utilizes a custom `NumpyEncoder` to serialize complex multi-dimensional arrays (e.g., influence functions) to JSON without truncation, ensuring perfect reproducibility.

## Methodology Implemented

1.  **Data Ingestion & Alignment:** Reconciles asynchronous factor frequencies using strict point-in-time `merge_asof` operations to prevent look-ahead bias.
2.  **TRACE Cleansing & Pricing:** Applies trade-level filters and computes daily VWAP.
3.  **Universe Filtering & Return Computation:** Enforces FISD hard filters, assigns month-end prices via dual business-day windows, and computes exact accrued interest.
4.  **Signal & Factor Construction:** Computes bond-level ILLIQ and rolling VaR5. Forms the 32 test portfolios and constructs the replicated BBW factors via independent double-sorts with deterministic jittering.
5.  **Econometric Evaluation:** Executes two-pass cross-sectional regressions (OLS/GLS) and parallel Fama-MacBeth regressions for both beta ($\gamma$) and covariance ($\lambda$) risk premia.
6.  **Mimicking Portfolios & Robustness:** Projects nontraded factors using HAC-robust Wald tests and evaluates them via BKRS jackknife inference.
7.  **Archival & Audit:** Cross-validates sample coverage against the manuscript's benchmarks and serializes all artifacts to disk.

## Core Components (Notebook Structure)

*Note: All orchestrator callables and their constituent helper functions are contained within a singular, comprehensive Jupyter Notebook (`priced_risk_in_corporate_bonds_draft.ipynb`).*

The notebook is structured as a logical Directed Acyclic Graph (DAG):
1.  Configuration and Data Validation (Task 1)
2.  TRACE Cleaning and Price Aggregation (Task 2)
3.  FISD Filtering and Master Panel Construction (Task 3)
4.  Accrued Interest and Return Computation (Tasks 4-5)
5.  Risk Signal and Factor Construction (Tasks 6-9)
6.  Univariate Statistics and Sharpe Ratio Comparisons (Tasks 10-12)
7.  Two-Pass Cross-Sectional Regressions (Tasks 13, 16)
8.  Mimicking Portfolio Projections (Tasks 14-15)
9.  Fama-MacBeth Bond-Level Regressions (Task 17)
10. Robustness Checks, Visualization, and Archival (Tasks 18-19)

## Key Callable: `run_end_to_end_research_pipeline`

The project is designed around a single, top-level user-facing interface function:

-   **`run_end_to_end_research_pipeline`:** This apex orchestrator function runs the entire automated research pipeline. A single call to this function validates the raw DataFrames, cleans the TRACE trades, computes exact bond returns, constructs the risk factors, executes the complex econometric estimations (CSR, Fama-MacBeth, Jackknife Sharpe ratios), generates publication-quality figures and LaTeX tables, and archives the results to disk. It returns a comprehensive dictionary containing all generated artifacts.

## Prerequisites

-   Python 3.10+
-   Core Python dependencies: `numpy`, `pandas`, `scipy`, `statsmodels`, `matplotlib`, `pyyaml`, `faker` (for synthetic testing).

## Installation

1.  **Clone the repository:**
    ```sh
    git clone https://github.com/chirindaopensource/priced_risk_in_corporate_bonds.git
    cd priced_risk_in_corporate_bonds
    ```

2.  **Create and activate a virtual environment (recommended):**
    ```sh
    python -m venv venv
    source venv/bin/activate  # On Windows, use `venv\Scripts\activate`
    ```

3.  **Install Python dependencies:**
    ```sh
    pip install -r requirements.txt
    ```

## Input Data Structure

The pipeline requires 10 primary raw DataFrames (and 2 optional ones for robustness):
1.  **`trace_raw`**: Enhanced TRACE intraday trades.
2.  **`fisd_raw`**: Mergent FISD issue and issuer data.
3.  **`fisd_ratings_raw`**: Historical credit ratings from FISD.
4.  **`ff_raw`**: Fama-French factors (MKTS, SMB, HML, RF).
5.  **`goyal_raw`**: Default and Term factors.
6.  **`hkm_raw`**: Intermediary capital factors (CPTLT, CPTL).
7.  **`macro_raw`**: Macroeconomic uncertainty (UNC) and VIX.
8.  **`lrc_raw`**: Long-run consumption factor (LRC_COND).
9.  **`bbw_original_raw`**: Original BBW factors (for diagnostic comparison).
10. **`treasury_yields_raw`**: U.S. Treasury constant-maturity yields.
11. **`config.yaml`**: The master configuration file defining all methodological parameters.

## Usage

Here is the granular, step-by-step guide to executing the end-to-end pipeline for **"Priced Risk in Corporate Bonds"**. This example demonstrates how to synthetically generate the required high-fidelity TRACE, FISD, and macroeconomic datasets, load the study configuration from a YAML file, and execute the full research pipeline using the `run_end_to_end_research_pipeline` orchestrator.

*Note: It is assumed that all the callables defined in this conversation (including the master orchestrator and its dependencies) are already loaded into memory within a single Jupyter notebook environment. No external `.py` module imports are required for the pipeline functions themselves.*

### **Step 1: Synthetic Data Generation (`raw_bond_data`)**

The first requirement is a high-fidelity synthetic representation of the 10 raw datasets. These datasets must adhere strictly to the schemas defined in the study, encompassing intraday trades, static bond characteristics, credit ratings, and various macroeconomic factors.

**Methodology:**
1.  **Universe Generation:** We define a small, tractable universe of 10 synthetic corporate bonds (CUSIPs) and establish daily and monthly temporal grids spanning the study period (July 2002 to December 2016).
2.  **TRACE Simulation:** We simulate intraday trades with realistic prices (centered around par, $100), institutional-sized volumes ($\ge \$10,000$), and standard settlement flags to ensure they pass the Dick-Nielsen (2014) filters.
3.  **FISD Simulation:** We generate static characteristics (e.g., fixed coupons, standard day-count bases) that satisfy the strict inclusion criteria for plain-vanilla corporate bonds.
4.  **Factor Simulation:** We simulate macroeconomic and traded factors using standard normal distributions calibrated to typical financial stylized facts (e.g., positive equity risk premium, mean-reverting VIX).
5.  **Schema Enforcement:** We explicitly cast all columns to their required types (`datetime64[ns]`, `float64`, `str`) to satisfy the rigorous validation gates of Task 1.

```python
import pandas as pd
import numpy as np
import yaml
import os
from typing import Dict, Any

# Initialize random seed for strict reproducibility
np.random.seed(42)

def generate_synthetic_bond_data(
    start_date: str = "2002-07-01",
    end_date: str = "2016-12-31",
    n_bonds: int = 10
) -> Dict[str, pd.DataFrame]:
    """
    Generates a suite of high-fidelity synthetic DataFrames mimicking TRACE, FISD, 
    and macroeconomic factors for testing the corporate bond asset pricing pipeline.

    Purpose:
        To create mathematically plausible mock datasets that strictly adhere to the 
        schemas required by the Dickerson, Mueller, and Robotti (2023) replication 
        protocol, enabling end-to-end pipeline execution without proprietary WRDS data.

    Inputs:
        start_date (str): The start date of the simulation. Default is "2002-07-01".
        end_date (str): The end date of the simulation. Default is "2016-12-31".
        n_bonds (int): The number of unique synthetic bonds to generate. Default is 10.

    Processes:
        1. Temporal Grid Generation: Creates daily and monthly business calendars.
        2. TRACE Generation: Simulates intraday trades with realistic prices and volumes.
        3. FISD Generation: Simulates static bond characteristics passing all hard filters.
        4. Factor Generation: Simulates equity, macro, and intermediary capital factors.
        5. Schema Enforcement: Casts all columns to exact required dtypes.

    Outputs:
        Dict[str, pd.DataFrame]: A dictionary containing the 10 required raw DataFrames.

    Raises:
        ValueError: If start_date is not strictly before end_date.
    """
    # Validate temporal ordering
    if pd.Timestamp(start_date) >= pd.Timestamp(end_date):
        raise ValueError(f"start_date ({start_date}) must precede end_date ({end_date}).")

    # Generate temporal grids
    # Daily business days for TRACE trades
    dates_daily = pd.date_range(start=start_date, end=end_date, freq='B')
    # Month-end dates for factors and ratings
    dates_monthly = pd.date_range(start=start_date, end=end_date, freq='ME')
    # Generate 9-character synthetic CUSIPs
    cusips = [f"{i:09d}" for i in range(1, n_bonds + 1)]

    # ---------------------------------------------------------
    # 1. TRACE Intraday Trades (trace_raw)
    # ---------------------------------------------------------
    trace_records = []
    for cusip in cusips:
        # Randomly sample 5 trading days per month to ensure sufficient data for ILLIQ
        sampled_dates = np.random.choice(dates_daily, size=len(dates_monthly) * 5, replace=True)
        for dt in sampled_dates:
            trace_records.append({
                "cusip": cusip,
                "trd_exctn_dt": dt,
                "trd_exctn_tm": "12:00:00",
                # Simulate prices around par with small variance
                "rptd_pr": np.random.normal(100.0, 2.0),
                # Simulate institutional volume
                "entrd_vol_qt": np.random.uniform(10000, 1000000),
                "days_to_sttl_ct": "002",
                "wis_fl": "N",
                "lckd_in_ind": "N",
                "sale_cndtn_cd": "None",
                "orig_msg_seq_nb": np.nan,
                "msg_seq_nb": np.random.randint(1, 1000000),
                "trd_rpt_dt": dt,
                "trd_rpt_tm": "12:00:05"
            })
    trace_raw = pd.DataFrame(trace_records)
    trace_raw["trd_exctn_dt"] = pd.to_datetime(trace_raw["trd_exctn_dt"])
    trace_raw["trd_rpt_dt"] = pd.to_datetime(trace_raw["trd_rpt_dt"])

    # ---------------------------------------------------------
    # 2. FISD Issue Data (fisd_raw)
    # ---------------------------------------------------------
    fisd_records = []
    for cusip in cusips:
        fisd_records.append({
            "cusip": cusip,
            "country_domicile": "USA",
            "private_placement": "N",
            "foreign_currency": "N",
            "rule_144a": "N",
            "asset_backed": "N",
            "convertible": "N",
            "coupon_type": "F",
            "interest_frequency": 2,
            "day_count_basis": 1, # 30/360
            "offering_date": pd.Timestamp("2000-01-01"),
            "dated_date": pd.Timestamp("2000-01-01"),
            "coupon": np.random.uniform(3.0, 8.0),
            "maturity": pd.Timestamp("2030-01-01"),
            "amount_outstanding": np.random.uniform(100000, 500000),
            "bond_type": "CDEB",
            "industry_group": np.random.randint(1, 13) # Fama-French 12
        })
    fisd_raw = pd.DataFrame(fisd_records)

    # ---------------------------------------------------------
    # 3. FISD Ratings (fisd_ratings_raw)
    # ---------------------------------------------------------
    ratings_records = []
    for cusip in cusips:
        # Assign a static rating for simplicity in the synthetic data
        ratings_records.append({
            "cusip": cusip,
            "rating_date": pd.Timestamp("2001-01-01"),
            "rating_text": "BBB",
            "rating_numeric": 9.0
        })
    fisd_ratings_raw = pd.DataFrame(ratings_records)

    # ---------------------------------------------------------
    # 4. Fama-French Factors (ff_raw)
    # ---------------------------------------------------------
    n_months = len(dates_monthly)
    ff_raw = pd.DataFrame({
        "date": dates_monthly,
        "Mkt.RF": np.random.normal(0.5, 4.0, n_months),
        "SMB": np.random.normal(0.2, 2.0, n_months),
        "HML": np.random.normal(0.2, 2.0, n_months),
        "RF": np.full(n_months, 0.1) # 0.1% monthly risk-free rate
    })

    # ---------------------------------------------------------
    # 5. Goyal Factors (goyal_raw)
    # ---------------------------------------------------------
    goyal_raw = pd.DataFrame({
        "date": dates_monthly,
        "DEF": np.random.normal(0.1, 1.0, n_months),
        "TERM": np.random.normal(0.1, 1.0, n_months)
    })

    # ---------------------------------------------------------
    # 6. HKM Factors (hkm_raw)
    # ---------------------------------------------------------
    hkm_raw = pd.DataFrame({
        "date": dates_monthly,
        "CPTLT": np.random.normal(0.3, 3.0, n_months),
        "CPTL": np.random.normal(0.0, 1.0, n_months)
    })

    # ---------------------------------------------------------
    # 7. Macro Factors (macro_raw)
    # ---------------------------------------------------------
    macro_raw = pd.DataFrame({
        "date": dates_monthly,
        "UNC": np.cumsum(np.random.normal(0.0, 0.05, n_months)), # Random walk for level
        "VIX": np.random.uniform(10.0, 30.0, n_months)
    })

    # ---------------------------------------------------------
    # 8. Long-Run Consumption (lrc_raw)
    # ---------------------------------------------------------
    dates_quarterly = pd.date_range(start=start_date, end=end_date, freq='QE')
    lrc_raw = pd.DataFrame({
        "date": dates_quarterly,
        "LRC_COND": np.random.normal(0.4, 0.2, len(dates_quarterly))
    })

    # ---------------------------------------------------------
    # 9. Original BBW Factors (bbw_original_raw)
    # ---------------------------------------------------------
    bbw_original_raw = pd.DataFrame({
        "date": dates_monthly,
        "MKTB": np.random.normal(0.4, 2.0, n_months),
        "DRF": np.random.normal(0.6, 3.0, n_months),
        "CRF": np.random.normal(0.5, 3.0, n_months),
        "LRF": np.random.normal(0.3, 1.5, n_months)
    })

    # ---------------------------------------------------------
    # 10. Treasury Yields (treasury_yields_raw)
    # ---------------------------------------------------------
    ty_records = []
    maturities = [1, 3, 6, 12, 24, 36, 60, 84, 120, 240, 360]
    for dt in dates_monthly:
        for mat in maturities:
            ty_records.append({
                "date": dt,
                "maturity_months": mat,
                # Upward sloping yield curve simulation
                "yield": 1.0 + np.log(mat) * 0.5 + np.random.normal(0, 0.1)
            })
    treasury_yields_raw = pd.DataFrame(ty_records)

    # Compile into dictionary
    raw_data_dict = {
        "trace_raw": trace_raw,
        "fisd_raw": fisd_raw,
        "fisd_ratings_raw": fisd_ratings_raw,
        "ff_raw": ff_raw,
        "goyal_raw": goyal_raw,
        "hkm_raw": hkm_raw,
        "macro_raw": macro_raw,
        "lrc_raw": lrc_raw,
        "bbw_original_raw": bbw_original_raw,
        "treasury_yields_raw": treasury_yields_raw
    }

    return raw_data_dict

# Generate the synthetic datasets
raw_bond_data = generate_synthetic_bond_data()

print("Synthetic Data Generation Complete.")
print(f"TRACE Records Generated: {len(raw_bond_data['trace_raw'])}")
print(f"FISD Records Generated: {len(raw_bond_data['fisd_raw'])}")
```

### **Step 2: Loading the Configuration (`config.yaml`)**

The study relies on a deterministic configuration file (`config.yaml`) that defines all methodological parameters, filter thresholds, and econometric settings. We assume this file has been saved in the working directory.

**Methodology:**
1.  **File I/O:** Open `config.yaml` in read mode with explicit UTF-8 encoding.
2.  **Parsing:** Use `yaml.safe_load` to convert the YAML structure into a nested Python dictionary.
3.  **Validation:** Catch file existence errors and parsing errors, raising explicit exceptions to halt execution if the configuration is unavailable.

```python
# Define the function to load the YAML configuration file.
def load_study_configuration(
    # The filesystem path to the YAML configuration file.
    filepath: str = "config.yaml"
) -> Dict[str, Any]:
    """
    Loads the study configuration parameters from a YAML file into a Python dictionary.

    Purpose:
        To ingest the deterministic hyperparameters, data filters, and econometric 
        settings defined in the external configuration file. This ensures strict 
        reproducibility by separating the execution code from the methodological parameters.

    Inputs:
        filepath (str): The relative or absolute path to the YAML configuration file.

    Processes:
        1. File Access: Attempts to open the specified file in read mode.
        2. Parsing: Uses PyYAML's safe_load to parse the YAML structure securely.
        3. Validation: Catches and handles FileNotFoundError and YAMLError.

    Outputs:
        Dict[str, Any]: A nested dictionary containing the complete study configuration.

    Raises:
        TypeError: If filepath is not a string.
        FileNotFoundError: If the config.yaml file does not exist.
        yaml.YAMLError: If the file contains invalid YAML syntax.
    """
    # Validate that the filepath argument is a string.
    if not isinstance(filepath, str):
        # Raise a TypeError if the input is invalid.
        raise TypeError(f"Expected str for filepath, got {type(filepath).__name__}.")

    # Attempt to open and parse the file within a try-except block.
    try:
        # Open the file stream with explicit UTF-8 encoding.
        with open(filepath, "r", encoding="utf-8") as file:
            # Parse the YAML content safely into a Python dictionary.
            config: Dict[str, Any] = yaml.safe_load(file)
        
        # Print a success message to the console.
        print(f"Successfully loaded configuration from {filepath}")
        # Return the parsed configuration dictionary.
        return config

    # Catch the specific error if the file is missing.
    except FileNotFoundError:
        # Raise a descriptive FileNotFoundError.
        raise FileNotFoundError(f"Fatal Error: Configuration file not found at '{filepath}'.")
    # Catch any YAML parsing errors.
    except yaml.YAMLError as e:
        # Raise a descriptive YAMLError.
        raise ValueError(f"Error parsing YAML file '{filepath}': {e}")

# Load the configuration into memory.
# Note: This assumes 'config.yaml' is present in the working directory.
study_config: Dict[str, Any] = load_study_configuration("config.yaml")
```

### **Step 3: Executing the Pipeline (`run_end_to_end_research_pipeline`)**

With the raw data (`raw_bond_data`) and configuration (`study_config`) in memory, we invoke the top-level orchestrator. This function manages the entire lifecycle: TRACE cleaning, FISD filtering, return computation, risk signal generation, factor construction, two-pass cross-sectional regressions, Fama-MacBeth estimations, robustness checks, and final archival packaging.

**Methodology:**
1.  **Function Call:** Pass the individual DataFrames from the `raw_bond_data` dictionary and the `study_config` to `run_end_to_end_research_pipeline`.
2.  **Output Handling:** The function returns a comprehensive dictionary containing all research artifacts. We extract and inspect key outputs such as the factor summary statistics, the cross-sectional regression results, and the path to the archived replication package.

```python
# ==============================================================================
# Execution of the End-to-End Corporate Bond Asset Pricing Pipeline
# ==============================================================================

if __name__ == "__main__":
    # Ensure we have valid inputs before running
    if raw_bond_data and study_config:
        
        print("\nInitiating Priced Risk in Corporate Bonds Pipeline...")
        print("This process will execute Tasks 1 through 19 sequentially.\n")
        
        # Execute the master orchestrator
        # We unpack the raw_bond_data dictionary to pass individual DataFrames
        study_artifacts = run_end_to_end_research_pipeline(
            trace_raw=raw_bond_data["trace_raw"],
            fisd_raw=raw_bond_data["fisd_raw"],
            fisd_ratings_raw=raw_bond_data["fisd_ratings_raw"],
            ff_raw=raw_bond_data["ff_raw"],
            goyal_raw=raw_bond_data["goyal_raw"],
            hkm_raw=raw_bond_data["hkm_raw"],
            macro_raw=raw_bond_data["macro_raw"],
            lrc_raw=raw_bond_data["lrc_raw"],
            bbw_original_raw=raw_bond_data["bbw_original_raw"],
            treasury_yields_raw=raw_bond_data["treasury_yields_raw"],
            config=study_config,
            wrds_raw=None, # Optional alternative database
            ice_raw=None   # Optional alternative database
        )
        
        # ==============================================================================
        # Inspecting the Outputs
        # ==============================================================================
        
        print("\n" + "="*80)
        print("STUDY EXECUTION COMPLETE")
        print("="*80)
        
        # 1. Accessing Factor Summary Statistics (Table 2, Panel A equivalent)
        if "Task_10_Factor_Stats" in study_artifacts:
            print("\n[Factor Summary Statistics (Means, SDs, Alphas, Sharpe Ratios)]")
            # Display the first few rows of the summary table
            print(study_artifacts["Task_10_Factor_Stats"].head())
            
        # 2. Accessing Two-Pass CSR Results for the BBW Model
        if "Task_13_CSR_Traded" in study_artifacts:
            print("\n[Two-Pass Cross-Sectional Regression Results: BBW Model]")
            bbw_results = study_artifacts["Task_13_CSR_Traded"].get("BBW", {})
            if "GLS" in bbw_results:
                print(f"GLS R-squared: {bbw_results['GLS']['R2']:.4f}")
                print(f"GLS R-squared p-value (KRS Test): {bbw_results['GLS']['R2_p_val']:.4f}")
                print("Prices of Covariance Risk (Lambda):")
                print(bbw_results['GLS']['lambda'])
                print("Misspecification-Robust t-statistics (t-stat_m):")
                print(bbw_results['GLS']['t_stat_m_lambda'])

        # 3. Accessing Fama-MacBeth Results
        if "Task_17_Fama_MacBeth" in study_artifacts:
            print("\n[Fama-MacBeth Bond-Level Regression Summary]")
            print(study_artifacts["Task_17_Fama_MacBeth"].head())

        # 4. Printing the Archival Package Path
        print("\n" + "="*80)
        print("REPLICATION PACKAGE ARCHIVED")
        print("="*80)
        if "Replication_Package_Path" in study_artifacts:
            print(f"All figures, LaTeX tables, and serialized data have been saved to:")
            print(f"-> {study_artifacts['Replication_Package_Path']}")
        
    else:
        print("Error: Missing synthetic data or configuration. Cannot proceed.")
```

### **Summary of the Execution Flow**

1.  **Data Ingestion & Harmonization:** The synthetic `raw_bond_data` and `study_config` are passed to the pipeline. The orchestrator validates the schemas, pads CUSIPs, and aligns all external macroeconomic factors to a strict, timezone-naive calendar month-end grid.
2.  **TRACE Cleansing & Pricing:** The pipeline applies the Dick-Nielsen (2014) protocol to resolve message chains (cancellations, corrections, reversals) and computes daily volume-weighted average clean prices.
3.  **Universe Filtering & Return Computation:** FISD hard filters are applied to isolate plain-vanilla corporate bonds. Month-end prices are assigned using dual business-day windows, exact accrued interest is computed, and monthly excess returns are generated.
4.  **Signal & Factor Construction:** Bond-level ILLIQ and rolling VaR5 signals are computed vectorially. The 32 test portfolios are formed using lagged weights, and the four replicated BBW factors (MKTB, DRF, CRF, LRF) are constructed via independent double-sorts with deterministic jittering.
5.  **Econometric Evaluation:** The pipeline computes bias-adjusted squared Sharpe ratios, executes two-pass cross-sectional regressions (OLS/GLS) with Shanken and KRS misspecification-robust standard errors, and runs parallel Fama-MacBeth regressions for both beta and covariance risk premia.
6.  **Mimicking Portfolios & Robustness:** Nontraded factors are projected onto basis assets using HAC-robust Wald tests. The pipeline evaluates these mimicking portfolios using BKRS jackknife inference and executes robustness checks (e.g., exact fractional duration-adjusted returns).
7.  **Archival & Audit:** The pipeline cross-validates sample coverage against the manuscript's benchmarks, generates publication-quality figures and sanitized LaTeX tables, and serializes all artifacts to disk using a custom `NumpyEncoder` for lossless preservation.

## Output Structure

The pipeline returns a comprehensive dictionary containing the following key artifacts:
-   **`Task_10_Factor_Stats`**: A pandas DataFrame summarizing factor means, standard deviations, alphas, and Sharpe ratios.
-   **`Task_13_CSR_Traded`**: A nested dictionary containing OLS and GLS risk premia ($\gamma, \lambda$), $R^2$, and robust t-statistics for traded models.
-   **`Task_16_CSR_Nontraded`**: A nested dictionary containing the equivalent CSR results for nontraded-factor models.
-   **`Task_17_Fama_MacBeth`**: A pandas DataFrame summarizing the bond-level Fama-MacBeth risk premia.
-   **`Table_2_LaTeX`**: A sanitized, publication-ready LaTeX string of the factor summary table.
-   **`Figure_1` & `Figure_2`**: Matplotlib Figure objects for the factor time-series and mean-variance frontier.
-   **`Task_19_Validation_Report`**: A dictionary detailing the sample coverage cross-validation against the manuscript's Table A1.
-   **`Replication_Package_Path`**: A string indicating the absolute path to the serialized archival directory.

## Project Structure

```
priced_risk_in_corporate_bonds/
│
├── priced_risk_in_corporate_bonds_draft.ipynb  # Main implementation notebook containing all callables
├── config.yaml                                 # Master configuration file (Filters, Econometric Settings)
├── requirements.txt                            # Python package dependencies
│
├── priced_risk_replication_package/            # Auto-generated archival directory
│   ├── config/
│   │   └── study_config.json                   # Serialized configuration state
│   ├── data/
│   │   ├── Task_10_Factor_Stats.csv            # Serialized DataFrames
│   │   └── Task_13_CSR_Traded.json             # Serialized nested dictionaries (via NumpyEncoder)
│   ├── figures/
│   │   ├── Figure_1.pdf                        # Vector graphics
│   │   └── Figure_2.pdf
│   └── tables/
│       └── Table_2_Panel_A_LaTeX.tex           # Compiled LaTeX tables
│
├── LICENSE                                     # MIT Project License File
└── README.md                                   # This file
```

## Customization

The pipeline is highly customizable via the `config.yaml` file. Researchers can modify study parameters such as:
-   **Econometric Settings:** Adjust the `nw_lags` parameter to test the sensitivity of the standard errors to different Newey-West lag lengths.
-   **Factor Construction:** Modify the `winsorize_bounds` for the ILLIQ measure or change the `rolling_window_months` for the VaR5 computation.
-   **Robustness Checks:** Toggle `duration_adjusted_returns` to `true` to automatically strip out term-structure risk from the entire cross-sectional evaluation pipeline.

## Contributing

Contributions are welcome. Please fork the repository, create a feature branch, and submit a pull request with a clear description of your changes. Adherence to PEP 8, strict type hinting (`typing` module), and the draconian requirement for line-by-line in-text comments that explain the mathematical or logical purpose of every single line of code is strictly required for all pull requests to maintain the implementation-grade standard of this repository.

## Recommended Extensions

Future extensions, building upon this foundational framework, could include:
-   **Machine Learning Factor Discovery:** Integrating non-linear models (e.g., Random Forests, Neural Networks) to construct characteristic-based factors, evaluating them against the rigorous KRS and BKRS benchmarks established here.
-   **International Bond Markets:** Applying the pipeline to European or Emerging Market corporate bond datasets to test the out-of-sample validity of the bond CAPM dominance.
-   **Alternative Liquidity Proxies:** Implementing and testing newer, high-frequency liquidity measures beyond the Bao-Pan-Wang (2011) ILLIQ metric.

## License

This project is licensed under the MIT License. See the `LICENSE` file for details.

## Citation

If you use this code or the methodology in your research, please cite the original paper:

```bibtex
@misc{dickerson2026priced,
  title={Priced Risk in Corporate Bonds},
  author={Dickerson, Alexander and Mueller, Philippe and Robotti, Cesare},
  howpublished={arXiv preprint arXiv:2604.05699},
  year={2026}
}
```

For the implementation itself, you may cite this repository:
```bibtex
@misc{chirinda2026pricedriskpipeline,
  author = {Chirinda, Craig},
  title = {Priced Risk in Corporate Bonds: An Empirical Replication Pipeline},
  year = {2026},
  publisher = {GitHub},
  howpublished = {\url{https://github.com/chirindaopensource/priced_risk_in_corporate_bonds}}
}
```

## Acknowledgments

-   Credit to **Alexander Dickerson, Philippe Mueller, and Cesare Robotti** for the foundational theoretical framework, the rigorous econometric design, and the exposure of data-construction errors in prior literature.
-   This project is built upon the exceptional tools provided by the open-source community. Sincere thanks to the developers of the scientific Python ecosystem, particularly the **NumPy**, **Pandas**, **SciPy**, and **Statsmodels** contributors.

--

*This README was generated based on the structure and content of the `priced_risk_in_corporate_bonds_draft.ipynb` notebook and follows best practices for research software documentation.*
