# Copernicus Emergency Management Service GloFAS tutorials

This Jupyter Book collects practical notebook tutorials for working with **Global Flood Awareness System (GloFAS)** data.
The focus is on small, reusable workflows that help you move from a first CDS request to exploratory analysis in Python.

The tutorials are aimed at learners who want to understand how to:

- access public GloFAS historical and forecast products;
- inspect river discharge data with `xarray`;
- turn raw hydrographs into simple flood-awareness indicators.

::::{grid} 1 1 2 2

:::{card}
:header: Historical workflow
:link: ./tutorials/access-glofas-historical-data
Prepare a compact historical download request and plot daily discharge time series.
:::

:::{card}
:header: Forecast workflow
:link: ./tutorials/analyse-glofas-forecast-signal
Work with forecast lead times and ensemble-style indicators for flood awareness.
:::

:::{card}
:header: Notebook template
:link: ./reference/template-notebook
Reuse the house notebook structure when you draft additional GloFAS lessons.
:::

:::{card}
:header: Best practices
:link: ./reference/best-practices
Check the writing and review guidance before extending the book further.
:::

::::

:::{note}
This documentation is organised using the [Diátaxis framework](./explanation/diataxis.md).
The new notebooks live in the tutorial layer because they provide guided, learning-oriented walkthroughs.
:::
