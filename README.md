# 🚔 Buffalo Crime Incidents: Deep Learning Classification

This repository contains my work for **CSE 676-B: Deep Learning (Summer 2025)**, focused on **predicting and classifying crime incident types** using real-world open data from the **City of Buffalo Police Department**.

The project demonstrates the full ML pipeline: data preprocessing, visualization, feature engineering, and the development of neural network and machine learning models to classify incident types.

---

## 📊 Dataset

- **Source**: [City of Buffalo Open Data – Crime Incidents](https://data.buffalony.gov/Public-Safety/Crime-Incidents/d6g9-xbgu/about_data)  
- **Size**: 322,690 entries, 31 columns  
- **Target Variable**: `incident_type_primary` (22 unique classes)  
- **Attributes**: Incident type, timestamps, location details (zip code, neighborhood, census district), latitude/longitude, and other metadata:contentReference[oaicite:1]{index=1}  

---

## 🛠️ Data Preprocessing

Key preprocessing steps:
- Dropped redundant/high-missing-value columns (`incident_id`, `updated_at`, `case_number`, etc.).  
- Standardized missing values (`UNKNOWN`, `unknown`) to `NaN`.  
- Imputed missing **numerical values** (latitude, longitude) with **median**, and categorical values (zip code, neighborhood) with **mode**.  
- Converted categorical features to numerical (Label Encoding + One-Hot Encoding).  
- Applied MinMax normalization to scale continuous features between `[0, 1]`.  
- Final dataset after transformation: **322,690 rows × 796 features**.  

---

## 📈 Visualizations

Five key insights:
1. **Top 10 crime categories** (bar plot)  
2. **Incidents per day of week** (bar plot)  
3. **Geographical distribution (lat/long scatter)** showing hotspots  
4. **Top 10 zip codes by incident count**  
5. **Heatmap** of incident type frequency vs. day of week:contentReference[oaicite:2]{index=2}  

---

## 🤖 Models

### Neural Network (PyTorch)
- Input dim: 796  
- Output classes: 22  
- Architecture:  
  - Linear(796 → 256), Dropout(0.3)  
  - Linear(256 → 128), Dropout(0.3)  
  - Linear(128 → 22)  
- Parameters: 239,766  
- Loss: CrossEntropyLoss  
- Optimizer: Adam (lr=0.001)  
- Scheduler: ReduceLROnPlateau  

### Training
- Epochs: 50 (early stopping at 35)  
- Batch size: 128  
- Device: CPU  
- Best Validation Accuracy: ~46%  
- Test Accuracy: **46.3%**  

### Metrics
- Strong performance for frequent classes (e.g., *Larceny/Theft*: 0.62 F1).  
- Low recall for rare classes (e.g., *Murder*, *Sexual Assault*).  
- Imbalanced class distribution remains a challenge.  

---

## 📂 Repository Structure

├── data/ # Raw & processed datasets
├── notebooks/ # Jupyter notebooks 
├── results/ # Saved models
├── docs/ # Report
├── requirements.txt # Dependencies
└── README.md # Project documentation


  
  📄 Read the full project report [[here](https://github.com/ujwalwag/Buffalo-Crime-Incidents/blob/main/docs/a0_part2_50560587.pdf)
