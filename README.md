# Crop Classification Pipeline

A comprehensive machine learning pipeline designed to classify agricultural crops from satellite imagery data. This project automates the complex process of matching geospatial labels with corresponding time-series satellite imagery and preparing them for predictive modeling.

## Project Overview
This project addresses the challenge of agricultural remote sensing by creating a robust data ingestion, cleaning, and feature engineering pipeline. It utilizes `geopandas` for label handling and `h5py`/`rasterio` for processing multi-temporal satellite data.

### Key Functionality
* **Geospatial Data Matching:** Automatically links ground-truth `labels.geojson` data with the correct imagery files (e.g., `.h5` or `.tif`) by indexing and matching unique identifiers.
* **Advanced Feature Engineering:** * Processes raw time-series arrays into mean and standard deviation features, capturing annual agricultural patterns.
    * Performs spatial masking to isolate spectral signatures within specific crop field boundaries.
* **Robust Data Cleaning:** Implements automatic handling of "No Data" values (e.g., -9999) and applies mean imputation to ensure high-quality training input.

## Prerequisites
To run this project, ensure your environment includes:
* `geopandas`
* `pandas`
* `numpy`
* `rasterio`
* `h5py`
* `tqdm`
* `matplotlib`
* `seaborn`
* `scikit-learn`

## Getting Started

1.  **Repository Setup:** Ensure your project directory structure follows the format expected by the loader:
    ```text
    /your-project-root
    ├── labels.geojson
    ├── features/
    │   └── ... (.h5 or .tif files)
    └── finalcpstneprjt.ipynb
    ```
2.  **Data Ingestion:** The project uses a recursive scanning approach to locate imagery files, allowing for flexible storage locations within your project directory.
3.  **Run Pipeline:** Execute the notebook sequentially. The pipeline includes built-in progress tracking (`tqdm`) to handle large datasets effectively.

## Pipeline Workflow
The pipeline is modularized into three main stages:
* **Indexing:** A deep search (`os.walk`) identifies all available feature files.
* **Extraction:** The system iterates through labels, performs file lookups based on index/dataset metadata, and extracts relevant spectral/temporal data.
* **Integration:** Final features and labels are merged into a clean dataset ready for machine learning evaluation (e.g., Random Forest, Multi-Layer Perceptron, Gaussian Mixture Models).

## Results
The current pipeline successfully builds and evaluates several models to classify crops versus non-crops, generating metrics such as the Area Under the Receiver Operating Characteristic Curve (ROC AUC). 

## Contributing
This project is part of my capstone work. Feedback on the feature engineering approach or the data matching logic is welcome!
