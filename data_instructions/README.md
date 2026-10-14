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
