# Tools setup

The analytical scripts can be downloaded as:

- [**Jupyter notebooks**](https://github.com/GFDRR/CCDR-tools/tree/main/Top-down/notebooks): user-friendly script that run via browser interface.
Read more about [**Jupyter Notebooks**](https://jupyter-notebook.readthedocs.io/en/stable/notebook.html).
- [**Python code**](https://github.com/GFDRR/CCDR-tools/tree/main/Top-down/parallelization): give the user more control, and has overall better performances making use of parallel processing.

These can be downloaded and exectuted on any windows or linux machine. 
In both cases, the script expects input data to be provided according to some rules.

### Expected directories and input format

The script expects input data folders to be structured as:

```
Work dir/
 - Hazard.ipynb
 - common.py
 - Data/
   - ADM	Administrative unit layer for each country
   - HZD	Hazard layers
   - EXP	Exposure layers - Population (count), Built-up (ratio or binary), Agriculture (ratio or binary)
   - RSK	Output directory
```

- **ADMINISTRATIVE** boundaries are provided as geopackage files named as `ISO`_ADM.gpkg (e.g. `NPL`_ADM.gpkg) made of multiple layers represening different administrative boundary levels.

```
- ISO_ADM
  - ADM0 (country)
  - ADM1 (first-level sub-national division)
  - ADM2 (second-level sub-national division)
  - ADM3 (third-level sub-national division)
  - ...
```

```{figure} images/adm_lvl.jpg
---
align: center
---
Example of sub-national administrative boundaries for Senegal.
```

Each ADM layer should include relative ADMi_CODE and ADMi_NAME across levels to facilitate the summary of results:

  - **ADM0**

  | ISO3166_a2 | ISO3166_a3 | ADM0_CODE | ADM0_NAME | 
  |---|---|---|---|
  | String(2) | String(3) | Integer | String (20) |
 
  - **ADM1**

  | ADM0_CODE | ADM0_NAME | ADM1_CODE | ADM1_NAME | 
  |---|---|---|---|
  | Integer | String (20) | Integer | String(20) |

  - **ADM2**

  | ADM0_CODE | ADM0_NAME | ADM1_CODE | ADM1_NAME | ADM2_CODE | ADM2_NAME | 
  |---|---|---|---|---|---|
  | Integer | String (20) | Integer | String(20) | Integer | String(20) |

  - **ADM3**
  
  | ADM0_CODE | ADM0_NAME | ADM1_CODE | ADM1_NAME | ADM2_CODE | ADM2_NAME | ADM3_CODE | ADM3_NAME | 
  |---|---|---|---|---|---|---|---|
  | Integer | String (20) | Integer | String(20) | Integer | String(20) | Integer | String(20) |

- **HAZARD** layers are expected as raster files (`.tif`) named as `ISO`_HZD_RPi.tif (exampe for Nepal flood, RP100: `NPL_FL_RP100.tif`). Any resolution should work, but using resolution below 90m over large countries could cause very long processing and memory cap issues.

- **EXPOSURE** are expected as raster files (`.tif`) named as `ISO`_EXP.tif (exampe for Nepal flood, RP100: `NPL_FL_RP100.tif`). The same suggestion about resolution applies here.

	- Population from GHSL, 90 m: `ISO`_POP.tif
	- Built-up from World Settlement Footprint or equivalent, 90 m: `ISO`_BUP.tif
	- Agriculture from land cover map, ESA land cover or equivalent, 90 m: `ISO`_AGR.tif

```{caution}
When resampling exposure layers to a lower resolution, it is **strongly recommended** to align the resampled grid to exactly match the hazard grid, or viceversa.
```

<img width=600 src="https://user-images.githubusercontent.com/44863827/157419284-64e16285-6284-45ba-bc9c-01eab713c2f1.png">

```{caution}
All spatial data must use the same CRS, suggested: `EPSG 4326` (WGS 84)
```

<hr>

## Environment and libraries
- The script requires python3 - conda or mamba are encouraged
- Create a new environment named CCDR based on win_env.yml o linux_env.yml depending on your operating system.
  In Anaconda cmd prompt:

	`conda create --name CCDR --file <dir/win_env.yml>`
	
	`activate CCDR`

Edit the `.env` file inside the notebook directories to specify the working directory:

```
# Environment variables for the CCDR Climate and Disasater Risk analysis notebooks

# Fill the below with the location of data files
# Use absolute paths with forward slashes ("/"), and keep the trailing slash
DATA_DIR = ""

# THE ENTRIES BELOW DO NOT NEED TO BE EDITED
# Location to store results of analyses
OUTPUT_DIR = ${DATA_DIR}/RSK/

# Location to store downloaded rasters and other data
# for the analysis notebooks
CACHE_DIR = ${DATA_DIR}/cache/
```

## Run CCDR tool notebooks

### Baseline risk

- Navigate to your working directory: `cd <Your work directory>`
  ```{figure} images/cmd_prompt.png
  ---
  align: center
  ---
  Example of Anaconda cmd prompt
  ```
- Run `jupyter notebook`. The interface should pop up in your browser.
