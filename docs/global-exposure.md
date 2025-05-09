# Exposure datasets

**Exposure datasets** refer to a variety of datasets that can be used to represent the value that is exposed to suffer damage and losses from natural hazards.
This section presents some of the most common and recent type of data and indicators used for this purpose.

```{seealso}
Exposure datasets developed by WB disaster risk projects have been placed in a special collection of the WB Development Data Hub: [Risk Data Library Collection: **EXPOSURE**](https://datacatalog.worldbank.org/search?fq=(identification%2Fcollection_code%2Fany(col:col%20eq%20%27RDL%27))&q=exposure).
```

Below is a quick link to openly-licensed datasets that are used by the CCDR standard screening tool.

```{table}
:name: exp_datasets

| **Name** | **Developer** | **Metric** | **Resolution** | **Update frequency** |
|---:|:---:|:---:|:---:|:---:|
| [Global Human Settlement Layer](https://ghsl.jrc.ec.europa.eu/download.php) | EU-JRC | Population count | 100 m | Annual |
| [World Settlement Footprints](https://download.geoservice.dlr.de/WSF2019) | DLR | Presence of built-up | 10 m | Annual |
| [WorldCover](https://esa-worldcover.org/en/data-access) | ESA | Land cover classes | 10 m | Annual |
```

### EU-JRC Global Human Settlement Layer

The Global Human Settlement population model [GHS-POP,  [Schiavina et al. 2022](https://doi.org/10.2905/D6D86A90-4351-4508-99C1-CB074B022C4A)] offers 100 meters global population data projected over built-up land cover. It is similar to [WorldPop](https://www.worldpop.org) in terms of approach, but the reliability is generally better, and the errors are contained.
Note that high-resolution population mapping relies on census projections distributed in proportion to built-up density obtained from remote sensing data. This can induce model errors, particularly in mountainous and forest environments, resulting in an overestimation of natural hazard risk in those areas. The dataset is downloaded as regular tiles from the global map.

```{figure} images/JRC_GHSL.png
---
width: 600
align: center
---
Population count per 100 m grid over for New Dehli as obtained from EU-JRC GHSL 2020.
```

### DLR World Settlment Footprint

Built-up assets include houses, commercial and industrial buildings, infrastructures, facilities, and others. Data from 2019 World Settlement Footprint (WSF) is used for this current analysis. This is a high-resolution (10m) remotely sensed dataset which indicates whether each cell is primarily built up, excluding roads.

```{figure} images/DLR_WSF.jpg
---
width: 600
align: center
---
Built-up land cover information at 10 m resolution for Cambodia as obtained from DLR WSF 2019 and resampled into 100 m built-up density grid.
```

### ESA World Cover

The 2020 WorldCover dataset at 10m resolution from the European Space Agency can be used to identify specific types, e.g. agricultural land.

```{figure} images/ESA_WC.jpg
---
width: 600
align: center
---
Land cover information at 10 m resolution over Senegal as obtained from ESA WorldCover 2020.
```

### Additional datasets

For a more granular analysis of agricultural impacts, additional exposure datasets can be considered.

| **Name** | **Developer** | **Metric** | **Resolution** | **Last update** |
|---:|:---:|:---:|:---:|:---:|
| [Global Agro-Ecological Zones (GAEZ)](https://gaez.fao.org/) | FAO | The GAEZ v4 spatial data cover six themes: (1) Land and Water Resources, (2) Agro-climatic Resources, (3) Agro-climatic Potential Yield, (4) Suitability and Attainable Yield, (5) Actual Yields and Production, and (6) Yield and Production Gaps | 1 km | 2010 |
| [Gridded Livestock of the World (GLW)](https://www.fao.org/livestock-systems/global-distributions/en/) | FAO | Global distributions of cattle, buffaloes, sheep, goats, horses, pigs, chickens and ducks | 10 km | 2015 |
