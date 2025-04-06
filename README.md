# 🛍️ Product Matching

## 📄 Project Description

This project focuses on building a product matching system for an online catalog. The goal is to find the top-5 most similar items for a given product using vector-based similarity search.

## 📂 Input Data

- `base.csv` — Dataset containing all products. Each product has a unique ID (e.g., `4207931-base`) and 72 features.
- `train.csv` — Training dataset containing indices of the most similar (matching) products.
- `validation.csv` — Validation dataset used to test the final algorithm. Contains products for which similar items must be found in `base.csv`.
- `validation_answer.csv` — Labeled validation dataset with correct product matches.

> All datasets are provided in both full and reduced versions.

---

## 🎯 Objective

- Develop an algorithm that suggests the **5 most similar products** from `df_base` for each product in `df_valid`.
- Evaluate the quality of the algorithm using the **accuracy@5** metric.

---

## 🧩 Workflow Plan

1. Load the reduced dataset
2. Evaluate FAISS on raw (unprocessed) data
3. Data preprocessing
4. Clustering
5. Nearest neighbor search  
   - Test different inter-cluster distance metrics  
   - Use both FAISS CPU and GPU
6. Evaluate algorithm performance on the validation set
7. Feature selection (important features)
8. Nearest neighbor search + quality evaluation
9. Split clusters into subclusters
10. Final evaluation on the validation set
11. Test the final algorithm on the **full dataset**

---

## ✅ Final Results

An algorithm was successfully developed that finds the **top-5 similar products** for each item in `validation.csv`.

- **Final accuracy@5: 78.2%** on the validation set  
- Built using **FAISS** with the `IndexFlatL2` index  
- Key configuration:

  - Data scaled using **RobustScaler** (resistant to outliers)
  - Features with abnormal distributions removed
  - Number of clusters: **156**
  - `nprobe = 180`

---

## 🔧 Possible Improvements

- Further divide clusters into **subclusters**
- Test alternative distance metrics:
  - **Manhattan distance**
  - **Cosine similarity**
  - and others

