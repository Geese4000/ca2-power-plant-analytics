# Data access instructions

The data files are **not committed** to this repository. Follow these steps to obtain them and run the notebook.

## Main dataset: Global Power Plant Database

| Item | Detail |
| --- | --- |
| Name | Global Power Plant Database |
| Version | v1.3.0 (released June 2021) |
| Publisher | World Resources Institute (WRI) and partners |
| Source | https://datasets.wri.org/datasets/global-power-plant-database |
| Licence | Creative Commons Attribution 4.0 International (CC BY 4.0) |
| File used | `global_power_plant_database.csv` |
| Size | 34,936 rows (one per power plant), 36 columns, ~12 MB |
| Accessed | 2026-10-09 |

Note: WRI states this project is no longer actively maintained, so v1.3.0 is the final release.

1. Go to https://datasets.wri.org/datasets/global-power-plant-database
2. Download the **v1.3.0** ZIP file.
3. Unzip it. It contains `global_power_plant_database.csv` (the data), `README.txt` (official column definitions), `RELEASE_NOTES.txt`, `A_Global_Database_of_Power_Plants.pdf` (methodology) and `Estimating_Power_Plant_Generation_in_the_Global_Power_Plant_Database.pdf` (how WRI's generation estimates were built).
4. Place `global_power_plant_database.csv` in a folder called `data/` in the root of this repository.

## Supporting datasets

### Ember: Yearly Electricity Data

| Item | Detail |
| --- | --- |
| Name | Yearly Electricity Data (global) |
| Publisher | Ember |
| Source | https://ember-energy.org/data/yearly-electricity-data/ |
| Licence | Creative Commons Attribution 4.0 International (CC BY 4.0) |
| File used | `release_generation_yearly_global.csv` |
| Size | 104,169 rows, 24 columns (download of 24 Nov 2026) |
| Accessed | 2026-11-24 |

Ember updates this file twice a month, so a later download may contain slightly revised figures.

1. Go to https://ember-energy.org/data/yearly-electricity-data/
2. Download the **global** yearly CSV (not the Europe-only file).
3. Place it at `data/release_generation_yearly_global.csv`.

### EIA-860: US generator data, 2017

| Item | Detail |
| --- | --- |
| Name | Form EIA-860 detailed data, 2017 |
| Publisher | U.S. Energy Information Administration (EIA) |
| Source | https://www.eia.gov/electricity/data/eia860/ |
| Licence | US government work, public domain |
| File used | `3_1_Generator_Y2017.xlsx` (from `eia8602017.zip`) |
| Accessed | 2026-11-24 |

1. Go to https://www.eia.gov/electricity/data/eia860/
2. Download the **2017** ZIP file (`eia8602017.zip`).
3. Unzip it into `data/eia8602017/`.

### EIA-923: US plant generation, 2020–2025 (for checking only)

| Item | Detail |
| --- | --- |
| Name | Form EIA-923 detailed data, 2020–2025 |
| Publisher | U.S. Energy Information Administration (EIA) |
| Source | https://www.eia.gov/electricity/data/eia923/ |
| Licence | US government work, public domain |
| Files used | `EIA923_Schedules_2_3_4_5_M_12_<year>_Final….xlsx` for 2020 to 2025 |
| Accessed | 2026-11-25 |

1. Go to https://www.eia.gov/electricity/data/eia923/
2. Download the zip for each year from 2020 to 2025.
3. From each zip, copy the `EIA923_Schedules_2_3_4_5_M_12_…` file **directly** into `data/eia923/` (no subfolders).

EIA-923 contains each plant's actual generation, so it is **never used as a model input** (that would leak the answer). It is used only in 6.1, to check estimates for later years against what plants really produced.

## Final folder layout

```
data/global_power_plant_database.csv
data/release_generation_yearly_global.csv
data/eia8602017/3_1_Generator_Y2017.xlsx
data/eia923/EIA923_Schedules_2_3_4_5_M_12_2020_Final_Revision.xlsx   (one file per year, 2020-2025)
```

The `data/` folder is listed in `.gitignore`, so none of these files are committed. Running the notebook also creates `data/processed/` (see the main README).

## Citations

See the References section of the notebook ([3], [6], [7], [8]). The power plant database and Ember data are licensed under CC BY 4.0 and must be credited when reused.