# Wind Power Time Series Preprocessing and Gap Analysis

## Overview

This repository contains the data preprocessing pipeline and datasets used for wind power forecasting studies in two Brazilian regions:

* **Serra, Espírito Santo (ES)** – 15-minute resolution
* **Santa Vitória do Palmar, Rio Grande do Sul (RS)** – hourly resolution

The main contribution of this repository is a reproducible pipeline for transforming raw wind power and meteorological data into structured, gap-aware time series datasets suitable for machine learning applications.

---

## Motivation

Wind power datasets collected in real-world scenarios often contain:

* missing timestamps
* inconsistent measurements
* irregular temporal resolution

These issues directly impact the performance and reliability of forecasting models.

This project addresses these challenges by providing:

* a standardized preprocessing pipeline
* explicit missing data characterization
* datasets ready for supervised learning

---

## Repository Structure

```
.
├── wind_power_preprocessing_pipeline.ipynb
├── data/
│   ├── raw/
│   ├── cleaned/
│   ├── reindexed/
├── outputs/
│   ├── dfes_reindexed.xlsx
│   ├── dfrs_reindexed.xlsx
└── README.md
```

---

## Data Description

The datasets combine:

* **Simulated wind power** (from turbine mathematical models)
* **Real meteorological data** (weather stations)

### Main variables:

* `data_hora` → unified timestamp
* `potencia_gerada` → simulated wind power
* `vento_velocidade` → wind speed
* `gap_row` → indicates missing timestamps
* `missing_<col>` → missing value indicators
* `gap_len` → duration of missing data sequences

---

## Preprocessing Pipeline

The notebook implements the following steps:

### 1. Data Cleaning

* removal of duplicate records
* filtering of inconsistent data
  (e.g., zero power above cut-in wind speed)

### 2. Timestamp Construction

* merging date and time columns
* sorting and temporal alignment

### 3. Reindexing

* creation of a complete and continuous time index
* standardization of frequency (15min / 1h)

### 4. Missing Data Engineering

* detection of missing timestamps
* creation of binary flags
* gap length computation

---

## Outputs

Final datasets:

* `dfes_reindexed.xlsx`
* `dfrs_reindexed.xlsx`

These datasets were used as input for all machine learning models developed in this study.

---

## Use Cases

This repository can be used for:

* wind power forecasting
* time series modeling
* missing data analysis and imputation
* benchmarking ML models in renewable energy

---

## Reproducibility

To reproduce the datasets:

1. Place input files (`dfes.xlsx`, `dfrs.xlsx`) in the project directory
2. Run the notebook:

   ```
   DATA_IN_BRIEF_data_preprocessing_and_gap_characterization_pipeline.ipynb
   ```
3. Generated outputs will be saved automatically

---

## Requirements

* Python 3.x
* pandas
* numpy

---

## Related Work

This repository supports research in:

* renewable energy forecasting
* time series preprocessing
* machine learning applied to wind power

---

## License

This project is available under the MIT License.

For dataset usage, consider citing the corresponding publication (if available).

---

## Author

Bruna Ruppruela
MSc in Artificial Intelligence

---

