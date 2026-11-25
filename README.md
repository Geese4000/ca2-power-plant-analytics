# Estimating Power Plant Capacity Factors

A CRISP-DM data analytics project (CA2, Data Analytics, Munster Technological University).

## Questions

Many power plants worldwide do not report how much electricity they generate, which makes national generation and emissions estimates harder. Using each plant's characteristics (fuel type, capacity, age, location), national electricity statistics and, for US plants, equipment records, this project answers two questions for every plant:

1. **How much electricity did it produce in 2017?** (regression on the plant's **capacity factor**, how hard it runs relative to its maximum)
2. **What role does it play: low use, mid, or high (baseload)?** (classification)

For both, it measures how far the answers can be trusted, including for countries where no plants report.

## Dataset

[Global Power Plant Database v1.3.0](https://datasets.wri.org/datasets/global-power-plant-database), published by the World Resources Institute and partners under CC BY 4.0. One row = one power plant (34,936 plants, 36 columns).

The data is **not included** in this repository. See [data access instructions](data_instructions\README.md).

Two supporting datasets are joined to it: Ember's Yearly Electricity Data (national generation and capacity by fuel, CC BY 4.0) and the US Energy Information Administration's EIA-860 generator data for 2017 (public domain).

## Outputs

Running the notebook saves, in `data/processed/` (not committed):
- `plant_answers_2017.csv`: one row per plant with 2017 generation, capacity factor, role, source/confidence label, and a flag where the two answers disagree.
- `prepared_train.csv`, `prepared_test.csv`, `prepared_scenario_B.csv`: the prepared modelling sets.

Figures are saved in `figures/`.

## Setup

Requires Python 3.10 or later.

```bash
# 1. Clone the repository
git clone <repo_url>
cd <repo-folder>

# 2. Create and activate a virtual environment
python -m venv .venv
# Windows:      .venv\Scripts\activate
# macOS/Linux:  source .venv/bin/activate

# 3. Install dependencies
pip install -r requirements.txt
```

Then download the dataset and place it at `data/global_power_plant_database.csv` (see [data
access instructions](data_instructions\README.md)).

## Data citation

Global Energy Observatory, Google, KTH Royal Institute of Technology in Stockholm, Enipedia, and World Resources Institute, *Global Power Plant Database*, version 1.3.0, World Resources Institute, Jun. 2021. [Dataset]. Available: https://datasets.wri.org/dataset/globalpowerplantdatabase (accessed Oct. 9, 2026).