# Zindi Agriculture - Advanced Spatial Feature Engineering

## Project Overview

This project implements advanced spatial feature engineering techniques for the [Zindi Côte d'Ivoire Byte-Sized Agriculture Challenge](https://zindi.africa/competitions/cote-divoire-byte-sized-agriculture-challenge). The goal is to classify agricultural fields into three crop types (Cocoa, Palm, and Rubber) using satellite imagery data and geospatial information.

The solution focuses on extracting powerful spatial contextual features that capture the relationships between neighboring agricultural fields, significantly improving classification performance.

## Key Innovations

### 1. Spatial Neighborhood Analysis
This approach treats each field in its geographical context rather than as an isolated entity:

- Uses KD-trees for efficient spatial querying of neighboring fields
- Calculates statistical aggregations from neighboring fields (area, perimeter, compactness)
- Captures crop type distributions in the spatial neighborhood
- Creates diversity and entropy measures to quantify spatial complexity

### 2. Feature Engineering Pipeline

The pipeline follows these steps:
1. **Basic Geometric Features**: Calculating area, perimeter, compactness, and other shape-based metrics
2. **Spatial Context Features**: Analyzing the neighborhood of each field within a configurable radius
3. **Derived Features**: Creating advanced features like crop diversity scores and similarity metrics
4. **Robust Encoding**: Properly handling categorical variables and missing values

### 3. Random Forest Model

A Random Forest classifier with hyperparameter tuning is used for prediction:
- Implements cross-validation to find optimal parameters
- Evaluates model performance with proper validation
- Identifies the most important predictive features
- Creates predictions for submission

## Repository Structure

```
data/
├── sample_train.csv         # Training data with features
├── train.geojson            # Training data with geometries
├── test.geojson             # Test data with geometries
├── SampleSubmission.csv     # Submission template
├── simple.ipynb             # Main notebook with all code
├── README.md                # This file
notebook/
├── automated-feature-engineering-with-gemini-flash.ipynb  # Additional experimentation
├── ByteSizedAgriStarterNotebook.ipynb                      # Initial starter notebook
├── c-te-d-ivoire-byte-sized-agriculture-challenge-sta.ipynb # Competition starter notebook
super_advanced_data/
├── confusion_matrix.png     # Visualization of model performance
├── feature_importances.png  # Top features by importance
├── random_forest_model.pkl  # Saved model file
├── super_advanced_submission.csv # Final predictions
```

## How to Run

1. Install the required dependencies:
```
pip install pandas numpy matplotlib seaborn geopandas scikit-learn rtree
```

2. Run the notebook `simple.ipynb` which contains the complete end-to-end pipeline:
   - Data loading and preprocessing
   - Feature engineering (geometric and spatial neighborhood features)
   - Model training with hyperparameter tuning
   - Prediction and submission file generation

## Results

The solution achieves strong performance by leveraging spatial context:

- High prediction accuracy across all three crop types
- Most important features are related to spatial neighborhood characteristics
- The model successfully captures the spatial patterns in crop distribution

## Reproducing the Results

For reproducibility, the notebook uses:
- Fixed random seed (42)
- Comprehensive logging throughout the pipeline
- Saved model file for consistent predictions
- Clearly documented hyperparameters

## Competition Submission

The final predictions are saved in `super_advanced_data/super_advanced_submission.csv`, which follows the required format for submission to the Zindi competition.

## Key Insights

1. Spatial context is crucial for accurate crop type prediction
2. Neighboring field characteristics provide strong signals for classification
3. Crop diversity and distribution patterns in the neighborhood are highly predictive
4. Geometric features alone are insufficient for optimal performance

## Acknowledgments

- Zindi Africa for hosting the competition
- The competition organizers for providing the dataset
- The geospatial data science community for inspiration on spatial feature engineering techniques