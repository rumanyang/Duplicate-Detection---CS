# Duplicate-Detection---CS
### **Project Overview**

This project implements a scalable solution for detecting duplicate product listings across multiple web shops using Locality Sensitive Hashing (LSH). The implementation focuses on optimizing the efficiency of duplicate detection while maintaining reasonable accuracy.

### **Dataset**

Dataset: TVs-all-merged.json

Contains 1,624 television product descriptions from four web shops:

- Amazon.com
- Newegg.com
- Best-Buy.com
- TheNerds.net

Each product contains:
- Header information (shop, title, modelID)
- Key-value pairs (brand, resolution, refresh rate, etc.)

### **Setup**

1. Install Dependencies
Ensure Python 3.8 or later is installed, then run:
```bash
pip install -r requirements.txt 
```
2. Download the Dataset

```bash
file_path = "/content/TVs-all-merged.json"
with open(file_path, 'r', encoding='utf-8') as file:
    data = json.load(file)
```

### **Algorithm Structure**

1. Product representation using TF-IDF, OneHotEncoding, and StandardScaler
```bash
final_features = np.hstack([title_tfidf, brand_vectors, resolution_scaled])
```

2. Principal Component Analysis (PCA) to reduce the size of final_features
```bash
final_features_pca = pca.fit_transform(final_features)
```

3. Custom LSH implementation for efficient product comparison
```bash
generate_candidates(final_features_pca, b)
is_duplicate(pair, combined_features, similarity_threshold=0.7)
```

4. Agglomerative clustering approach with Bootstrap evaluation
```bash
evaluate_clustering_with_bootstrap(generated_features, labels, num_bootstraps=5, distance_threshold=thresholds)
```

5. Transitivity check
```bash
resolve_transitivity(candidate_pairs)
```

6. Performance evaluation
```bash
evaluate_performance(b, thresholds,similarity)
```

7. Visualization

### **Evaluation Metrics**

1. **Pair Quality**
Measures how many predicted duplicates are correct:
Pair Quality = True Positives / (True Positives + False Positives)

2. **Pair Completeness**
Measures how many actual duplicates were found:
Pair Completeness = True Positives / (True Positives + False Negatives)

3. **F1-Measure**
Combines Pair Quality and Pair Completeness:
F1 = 2 * (Pair Quality * Pair Completeness) / (Pair Quality + Pair Completeness)

4. **F1 star(*)-Measure**
Combines Pair Quality, Pair Completeness, and Fractions of comparison:
F1 = 3 * (Pair Quality * Pair Completeness * Fractions of comparison) / (Pair Quality + Pair Completeness + Fractions of comparison)

Each metric is evaluated across five bootstrapped datasets for robustness.

### **Key Features**

**Scalable Duplicate Detection**: Optimized using LSH to reduce the computational complexity of pairwise comparisons.

**Flexible Representation**: Utilizes features derived from product titles and key-value pairs, avoiding reliance on modelID.

**Robust Evaluation**: Employs bootstrapping with out-of-sample testing and calculates F1-measures for rigorous evaluation.


### **Acknowledgments**

- Based on the research paper assignment from Erasmus Rotterdam University
- Dataset provided by Dr.Frasincar et al.



