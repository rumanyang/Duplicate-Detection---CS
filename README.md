# Duplicate-Detection---CS
**Project Overview**

This project implements a scalable solution for detecting duplicate product listings across multiple web shops using Locality Sensitive Hashing (LSH). The implementation focuses on optimizing the efficiency of duplicate detection while maintaining reasonable accuracy by reducing the number of necessary comparisons between products.

**Dataset**

Dataset: TVs-all-merged.json
Contains 1,624 television product descriptions from four web shops:

- Amazon.com
- Newegg.com
- Best-Buy.com
- TheNerds.net

Each product contains:
- Header information (shop, title, modelID)
- Key-value pairs (brand, resolution, refresh rate, etc.)

**Algorithm Structure**

Custom LSH implementation for efficient product comparison
Product representation using TF-IDF, OneHotEncoding, and StandardScaler
Bootstrap evaluation with multiple iterations
Agglomerative clustering approach for duplicate detection
Performance evaluation using:

- Pair Quality
- Pair Completeness
- F1-measure
- F1*-measure

**Requirment**

pip install -r requirements.txt



