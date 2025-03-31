# Project 3 Report - Izak Boardman

## Data Description: NFL Big Data Bowl 2019
The NFL hosts an annual Kaggle competition using next-gen stats data. This project utilizes data from the 2019 competition, which includes games from the 2017-2019 seasons.

The dataset is organized into four sets:
- **Players**
- **Games**
- **Plays**
- **Tracking**

Due to the large size of frame-by-frame tracked plays spanning multiple years, the **Players** and **Tracking** datasets were omitted. Full metadata and dataset descriptions can be found in the `proj3_data_preprocess.ipynb` file or the `schema.md` file in this repository.

## Task Description
The theme of the 2025 NFL Big Data Bowl competition focuses on analyzing pre-snap characteristics to predict team trends in plays and scoring patterns. This project aims to predict the **Play Outcome**, a continuous variable ranging from **-100 to 100** representing yards gained or lost on an individual play based on pre-snap features.

### **Why is this useful?**
Accurately predicting yardage gained or lost on a play would be highly valuable for coaches, allowing them to adjust defensive strategies accordingly. However, due to the high variance in yardage, achieving high prediction accuracy proved to be more challenging than expected.

## Preprocessing
- The **Games** and **Plays** datasets were merged using `game_id` as the key.
- **Post-snap features** were removed to prevent data leakage.
- Missing values and outliers were handled by filling them with the **median**.
- A **scikit-learn pipeline** was used for:
  - Standardizing **numerical features**
  - One-hot encoding **categorical features**
- Some features contained **textual data** (e.g., defensive/offensive personnel). Custom utility functions were developed to transform these into multiple features representing individual player counts per play.

### **Data Splitting**
The data was split into training, validation, and test sets:
- **80% Train**
- **10% Validation**
- **10% Test**

All models used the same train-test split, except for neural networks.

### **Neural Network Data Handling**
- Data for neural networks was **batched** using **PyTorch data loaders**.
- Six **random seeds** were used to ensure the data format met the requirements for PyTorch models.

---
For further details on implementation and model performance, refer to the corresponding notebooks and scripts in this repository.

