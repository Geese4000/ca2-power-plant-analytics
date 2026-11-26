# Data access instructions

The raw dataset is **not committed** to this repository. Follow these steps to obtain it and run the notebook.

## Dataset

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

Note: WRI states this project is no longer actively maintained, so v1.30 is the final release.

## How to get the data

1. Go to https://datasets.wri.org/datasets/global-power-plant-database
2. Download the **v1.3.0** ZIP file.
3. Unzip it. It contains:
   - `global_power_plant_database.csv` (the data)
   - `README.txt` (official column definitions)
   - `RELEASE_NOTES.txt`
   - `A_Global_Database_of_Power_Plants.pdf` (methodology)
   - `Estimating_Power_Plant_Generation_in_the_Global_Power_Plant_Database.pdf` (how WRI's generation estimates were built)
4. Create a folder called `data/` in the root of this repository and place `global_power_plant_database.csv` inside it:

```
data/global_power_plant_database.csv
```

The `data/` folder is listed in `.gitignore`, so the file will not be committed.

## Citation

Global Energy Observatory, Google, KTH Royal Institute of Technology in Stockholm, Enipedia, World Resources Institute. 2019. *Global Power Plant Database* (v1.3.0). Published on Resource Watch and Google Earth Engine. https://datasets.wri.org/datasets/global-power-plant-database

Data by World Resources Institute and partners, licensed under CC BY 4.0.

DATA_PATH = "../data/global_power_plant_database.csv"
EMBER_PATH = "../data/release_generation_yearly_global.csv"
EIA_PATH = "../data/eia8602017/3_1_Generator_Y2017.xlsx"


raw = pd.read_csv(DATA_PATH, low_memory=False)
assert raw.shape == (34936, 36), f"Unexpected shape: {raw.shape} - check data_instructions/README.md"

# Supporting datasets (2.1): national electricity statistics and US generator records
ember_raw = pd.read_csv(EMBER_PATH)
eia_raw = pd.read_excel(EIA_PATH, sheet_name=["Operable", "Retired and Canceled"], header=1)
print(f"Ember rows: {len(ember_raw):,} | EIA-860 generators: operable {len(eia_raw['Operable']):,}, "
      f"retired or canceled {len(eia_raw['Retired and Canceled']):,}")

df = raw.copy() # work on a copy; `raw` is never modified
df.head()

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
3. From each zip, copy the `EIA923_Schedules_2_3_4_5_M_12_…` file into `data/eia923/`.

EIA-923 contains each plant's actual generation, so it is **never used as a model input** (that would leak the answer). It is used only in 6.1, to check estimates for later years against what plants really produced.


data/eia923/EIA923_Schedules_2_3_4_5_M_12_2020_Final_Revision.xlsx   (one file per year, 2020-2025)