# Filling the Gaps in Global Power Plant Data

A CRISP-DM data analytics project (CA2, DBMS71008 Data Analytics, Munster Technological University).

**Author:** Philip Dawson-Gariepy · **Lecturer:** Andrew Shields · **Repository:** https://github.com/Geese4000/ca2-power-plant-analytics

## Questions

Many power plants worldwide do not report how much electricity they generate, which makes national generation and emissions estimates harder. Using each plant's characteristics (fuel type, capacity, age, location), national electricity statistics and, for US plants, equipment records, this project answers two questions for every plant:

1. **How much electricity did it produce in 2017?** (regression on the plant's **capacity factor**, how hard it runs relative to its maximum)
2. **What role does it play: low use, mid, or high (baseload)?** (classification)

For both, it measures how far the answers can be trusted, including for countries where no plants report. The notebook also includes a function, `estimate_plant`, that estimates the capacity factor, yearly generation and role of any plant from its basic details, under the conditions of any year from 2015 to 2025.

## Data

| Dataset | Used for | Licence |
| --- | --- | --- |
| [Global Power Plant Database v1.3.0](https://datasets.wri.org/datasets/global-power-plant-database) (World Resources Institute and partners) | The plants: one row per plant (34,936 plants, 36 columns) | CC BY 4.0 |
| [Ember Yearly Electricity Data](https://ember-energy.org/data/yearly-electricity-data/) | Each country's national capacity factor and generation share for each fuel | CC BY 4.0 |
| [EIA-860, 2017](https://www.eia.gov/electricity/data/eia860/) (U.S. Energy Information Administration) | Technology and status of US plants | Public domain |
| [EIA-923, 2020–2025](https://www.eia.gov/electricity/data/eia923/) (U.S. Energy Information Administration) | Checking estimates for later years only, never a model input | Public domain |

The data is **not included** in this repository. See the [data access instructions](data_instructions/README.md) for how to download each file and where to place it.

## Repository structure

```
ca2-power-plant-analytics/
├── notebooks/
│   └── power_plant_capacity_factor.ipynb   # the full CRISP-DM analysis (Phases 1-6)
├── figures/                                # figures saved by the notebook (Figures 1-13)
├── data_instructions/
│   └── README.md                           # how to download the data
├── data/                                   # downloaded data and outputs (not committed)
├── requirements.txt
└── README.md
```

## Setup

Requires Python 3.10 or later.

```bash
# 1. Clone the repository
git clone https://github.com/Geese4000/ca2-power-plant-analytics.git
cd ca2-power-plant-analytics

# 2. Create and activate a virtual environment
python -m venv .venv
# Windows:      .venv\Scripts\activate
# macOS/Linux:  source .venv/bin/activate

# 3. Install dependencies
pip install -r requirements.txt
```

Then download the four data sources described in the [data access instructions](data_instructions/README.md) and place them in `data/`.

## Running the notebook

Open `notebooks/power_plant_capacity_factor.ipynb` in Jupyter or VS Code and run all cells from the top (**Restart & Run All**). A full run takes about 10–15 minutes; the slowest steps are the SVM tuning and the leave-one-country-out tests. A fixed random seed (42) makes every result reproducible.

## Outputs

Running the notebook saves, in `data/processed/` (not committed):
- `plant_answers_2017.csv`: one row per plant with 2017 generation, capacity factor, role, source/confidence label, and a flag where the two answers disagree.
- `prepared_train.csv`, `prepared_test.csv`, `prepared_scenario_B.csv`: the prepared modelling sets.

Figures are saved in `figures/`.

## Project status

All six CRISP-DM phases are complete in the notebook. Still to come: the Reflection, the Responsible AI Collaboration Statement and the 4-page paper.

## Data citations

- Global Energy Observatory, Google, KTH Royal Institute of Technology in Stockholm, Enipedia, and World Resources Institute, *Global Power Plant Database*, version 1.3.0, World Resources Institute, Jun. 2021. [Dataset]. Available: https://datasets.wri.org/dataset/globalpowerplantdatabase (accessed Oct. 9, 2026).
- Ember, "Yearly electricity data," Ember, London, U.K., 2026. [Dataset]. Available: https://ember-energy.org/data/yearly-electricity-data/ (accessed Nov. 24, 2026).
- U.S. Energy Information Administration, "Form EIA-860 detailed data, 2017," EIA, Washington, DC, USA, Sep. 2018. [Dataset]. Available: https://www.eia.gov/electricity/data/eia860/ (accessed Nov. 24, 2026).
- U.S. Energy Information Administration, "Form EIA-923 detailed data, 2020–2025," EIA, Washington, DC, USA. [Dataset]. Available: https://www.eia.gov/electricity/data/eia923/ (accessed Nov. 25, 2026).