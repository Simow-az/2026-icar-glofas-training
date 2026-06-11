CEMS Flood Training – Copilot Instructions
Project Context

This repository contains Jupyter notebooks used for official CEMS Flood training workshops delivered through the ECMWF training programme.

The notebooks are intended to be published through a JupyterBook and used during hands-on training sessions.

The training focuses on:

EWDS (Early Warning Data Store)
GloFAS reanalysis
GloFAS forecasts
Flood forecasting workflows
Hydrological data analysis
Ensemble forecasting
Threshold calculation
Flood signal quantification
Visualisation of hydrological products
Target Audience

The notebooks must be suitable for:

River Basin Agencies
Hydrologists
Water Resources Engineers
Humanitarian organisations
Disaster Risk Reduction practitioners
Civil Protection authorities
Researchers
PhD students
Environmental scientists
Climate scientists
Water management experts

Assume participants have basic Python knowledge but are not expert programmers.

General Principles

When generating code:

Prioritise readability over optimisation.
Use clear variable names.
Explain every important step.
Avoid unnecessary complexity.
Write production-quality examples.
Include comments throughout the code.
Use British English.
Follow ECMWF and Copernicus terminology.

The notebooks must teach concepts, not only provide code.

Notebook Structure

Each notebook should follow this structure:

1. Title

Provide a descriptive title.

Example:

# Accessing GloFAS Reanalysis Data from EWDS
2. Learning Objectives

Include a section such as:

## Learning Objectives

By the end of this notebook you will be able to:

- Access GloFAS datasets from EWDS
- Download data using the CDS API
- Open NetCDF files with xarray
- Calculate hydrological indicators
- Produce basic visualisations
3. Required Libraries

Explicitly show imports.

Use primarily:

import cdsapi
import xarray as xr
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import cartopy.crs as ccrs
import geopandas as gpd

Only introduce additional libraries when necessary.

4. Step-by-Step Workflow

For each operation:

Explain the purpose.
Show the code.
Explain the output.
Interpret the result.

Never jump directly to complex code.

5. Visualisation

Every notebook should contain meaningful visualisations whenever possible.

Prefer:

time series
hydrographs
anomaly plots
maps
ensemble visualisations
boxplots
exceedance plots

Always label:

axes
units
legends
titles
6. Exercises

Include practical exercises at the end.

Example:

## Exercise

Calculate monthly Q90 thresholds for a different station.

Hints:

- Group data by month.
- Calculate the 90th percentile.
- Plot the results.
Training Topics
EWDS Introduction

Explain:

what EWDS is
relationship with CDS
authentication
datasets available
GloFAS Reanalysis

Include examples for:

downloading reanalysis
opening NetCDF data
selecting locations
extracting time series
calculating monthly averages
anomaly analysis
Threshold Calculation

Include examples for:

Q10
Q90
monthly thresholds
exceedance detection
flood signal quantification

Use transparent calculations and explain methodology.

GloFAS Forecasts

Include examples for:

downloading forecasts
understanding ensemble members
looping through ensemble members
extracting regional information
near real-time workflows
Ensemble Analysis

When plotting forecasts:

Include:

ensemble hydrographs
ensemble spread
boxplots
median
percentiles

Explain forecast uncertainty.

Flood Signal Quantification

Include examples for:

threshold exceedance
return period concepts
anomaly calculation
event identification

Explain hydrological interpretation.

Code Style

Always:

# Load dataset
ds = xr.open_dataset(file)

# Extract discharge
discharge = ds["dis24"]

# Convert to dataframe
df = discharge.to_dataframe()

Avoid:

x = ds["dis24"].to_dataframe()

unless already explained.

Plot Style

Use:

fig, ax = plt.subplots(figsize=(10, 5))

Always include:

ax.set_title(...)
ax.set_xlabel(...)
ax.set_ylabel(...)
ax.grid(True)
Teaching Philosophy

The notebooks are educational material, not research scripts.

Every code block should answer:

What are we doing?
Why are we doing it?
What does the output mean?
How is it relevant for flood forecasting?

If code becomes complex, break it into smaller sections and explain each step.

Preferred Output

When asked to create a notebook section:

Generate:

Markdown explanation
Python code cell
Interpretation of results
Optional exercise

rather than code alone.

## Earthkit Preference

Whenever possible, use ECMWF **earthkit** packages as the preferred tools for data access, inspection, conversion, and visualisation.

Prefer earthkit for:

* accessing ECMWF/Copernicus datasets
* reading GRIB, NetCDF, Zarr, GeoTIFF, CSV, BUFR, CoverageJSON and GeoJSON data
* converting data to familiar Python objects such as xarray datasets, pandas dataframes and NumPy arrays
* quick geospatial visualisation
* map-based examples
* format-agnostic workflows

Use the following packages where appropriate:

```python
import earthkit.data as ekd
import earthkit.maps as ekm
```

Use `earthkit.data` as the first option for loading and inspecting data. Convert to `xarray`, `pandas`, or `numpy` only when this makes the teaching workflow clearer.

Example style:

```python
import earthkit.data as ekd

data = ekd.from_source("file", "example.grib")
ds = data.to_xarray()
```

For maps, prefer `earthkit.maps` when it simplifies the workflow:

```python
import earthkit.maps as ekm

ekm.quickplot(data)
```

When earthkit is not suitable, fall back to standard scientific Python libraries such as:

```python
import xarray as xr
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
```

Do not force earthkit if a simpler `xarray` or `pandas` solution is clearer for beginners.

When generating notebooks, explain why earthkit is useful:

* it reduces boilerplate code
* it supports multiple data formats
* it integrates with xarray, pandas and NumPy
* it is designed for meteorological, climate and hydrological workflows
* it is suitable for ECMWF/Copernicus training material

If documentation or repository links are provided by the user, follow those references as the main source of truth.
earthkit documentation : https://earthkit.readthedocs.io/en/stable/
some old notebooks from previous conferences but use it only for inspiration , make better :
https://github.com/Simow-az/2025-wmo-workshop-training-glofas-seasonal-V1
