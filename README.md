# Estimating Power Plant Capacity Factors

A CRISP-DM data analytics project (CA2, Data Analytics, Munster Technological University).

## Question

Many power plants worlwide do not report how much electricity they generate, which makes national generation and emissions estimates harder. This project asks whether a plant's characteristics (fuel type, capacity, age, location) can estimate its **cpacity factor**, how hard it runs relative to its maximum, well enough to fill those gaps credibly.

## Dataset

[Global Power Plant Database v1.3.0](https://datasets.wri.org/datasets/global-power-plant-database), published by the World Resources Institute and partners under CC BY 4.0. One row = one power plant (34,936 plants, 36 columns).

The data is **not included** in this repository. See [data access instructions](data_instructions\README.md).

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