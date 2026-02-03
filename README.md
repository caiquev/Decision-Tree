# 🪐 Clone Army Failure Analysis | War Analytics

![Project Status](https://img.shields.io/badge/Status-Complete-green)
![Python](https://img.shields.io/badge/Python-3.8%2B-blue)
![Library](https://img.shields.io/badge/Library-Scikit--Learn-orange)

## 📜 Context
The Republic fights for its survival. Led by Jedi Generals, the Clone Army faces the Separatist forces. The droids are numerous, and battles have seen better days. Recently, soldiers have been failing on the battlefield without a known cause.

The **Jedi High Council** has authorized the **War Analytics** team (the Old Republic's BI unit) to investigate. Based on biometric data documented by the generals, we must provide insights capable of staunching the bleeding and maintaining the galaxy under the command of the Galactic Senate.

## 🎯 Objective
The goal of this project is to build an **interpretable Machine Learning model** to identify the root causes of Clone Trooper failure. Unlike black-box models, we require clear decision rules that the Kaminoan cloners can implement immediately to filter out defective units before deployment.

## 🛠️ Technologies Used
* **Python**
* **Pandas:** Data manipulation and cleaning.
* **Scikit-Learn:**
    * `DecisionTreeClassifier`: For interpretable modeling.
    * `OrdinalEncoder` & `LabelEncoder`: For handling categorical biometric data.
* **Matplotlib:** For visualizing the decision logic.

## 📂 Dataset
The dataset consists of biometric and demographic data of Clone Troopers. 

| Feature (English) | Feature (Original PT-BR) | Type | Description |
| :--- | :--- | :--- | :--- |
| **shoulder_width** | Distância Ombro a ombro | Categorical | Physical measurement |
| **skull_size** | Tamanho do crânio | Categorical | Physical measurement |
| **feet_size** | Tamanho dos pés | Categorical | Physical measurement |
| **mass_kg** | Massa(em kilos) | Numerical | Weight of the unit |
| **height_cm** | Estatura(cm) | Numerical | Height of the unit |
| **lifespan_months** | Tempo de existência | Numerical | Age of the clone |
| **status** | Status | **Target** | Class (Apto/Defective) |

## 🚀 Methodology

1.  **Data Ingestion:** Loaded raw `.parquet` data containing clone specifications.
2.  **Preprocessing:** * Renamed columns from Portuguese to English for international standardization.
    * Applied **Ordinal Encoding** to categorical features (Skull, Feet, Shoulder) to preserve size hierarchy.
    * Applied **Label Encoding** to the target variable (`Status`).
3.  **Modeling:** Trained a **Decision Tree Classifier**. A tree was chosen specifically for its ability to produce visual, human-readable rules for the Jedi Council.
4.  **Analysis:** Visualized the tree structure to extract thresholds for Quality Control.

## 💡 Key Insights (The "90% Rule")

Analysis of the Decision Tree (Depth=3) revealed that physiological anomalies are the primary predictors of failure.

* **The Mass Threshold:** The most critical factor is `mass_kg`. Clones with **Mass > 83.405 kg** are overwhelmingly classified as **Fit (Apto)**.
* **Secondary Filter:** For clones below this weight, `height_cm` becomes the deciding factor.
* **Conclusion:** Approximately **90%** of battlefield failures can be prevented by strictly monitoring these two variables during the growth acceleration phase.

## 📊 Visualization
<img width="640" height="659" alt="output" src="https://github.com/user-attachments/assets/4de5c6dc-682a-410e-9833-f3a2bbe5469d" />

> The decision tree plot reveals the exact branching logic used to classify the clones.

---
*May the Force be with your data.*
