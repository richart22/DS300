---

# Fashion Recommendation via Graph Neural Networks and Multimodal Web-Crawled Data

This repository contains the implementation and experimental framework for the project **“Fashion Recommendation via Graph Neural Networks, Hybrid Collaborative Models and Web-Crawled Multimodal Data”**, which investigates the effectiveness of traditional, graph-based, and multimodal recommender systems on a real-world fashion dataset collected from **Uniqlo Vietnam** .

The project focuses on **Top-K fashion recommendation** under sparse interaction settings, emphasizing **Graph Neural Networks (GNNs)**, **multimodal feature fusion**, and **graph contrastive learning**.

---

## 📌 Project Overview

Fashion recommendation poses unique challenges due to its reliance on **visual appearance**, **textual descriptions**, and **user preference patterns**. To address these challenges, this project:

* Crawls real-world fashion product and review data from Uniqlo Vietnam
* Constructs a **user–item interaction graph**
* Evaluates **content-based**, **collaborative filtering**, and **graph-based multimodal models**
* Studies the impact of **text and image embeddings**
* Analyzes robustness using **contrastive learning**

Experimental results demonstrate that **multimodal graph-based models**, particularly **MMGCN** and **LightGCL**, significantly outperform traditional baselines in recommendation accuracy .

---

## 🧠 Models Implemented

### Baseline Models

* **Content-Based Filtering** (text + image embeddings)
* **User-Based Collaborative Filtering**

### Graph-Based Models

* **NGCF** (Neural Graph Collaborative Filtering)
* **LightGCN** (efficient GNN baseline)
* **LightGCL** (Graph Contrastive Learning)
* **MMGCN** (Multimodal Graph Convolutional Network)

All models are trained using **Bayesian Personalized Ranking (BPR) loss** with negative sampling.

---

## 🗂 Dataset Description

The dataset is automatically crawled from **Uniqlo Vietnam** using Selenium and BeautifulSoup and consists of two main components :

### Product Dataset

* **352 products**
* **13 attributes**, including:

  * category, product name, price, material
  * description, washing instructions
  * image URL, product code, rating statistics

### Reviewer Dataset

* **4,457 reviews**
* **13 attributes**, including:

  * rating, review text, review date
  * demographic information (age, gender, height, weight, shoe size)

To handle missing user identifiers, a **cohort-based user construction** strategy is employed, grouping users by shared demographic attributes.

---

## 🔍 Tasks & Evaluation

### Task

* **Top-K recommendation** on implicit feedback data

### Evaluation Metrics

* Recall@K
* Precision@K
* NDCG@K
* MRR@K
  (K = 5, 10)

Training interactions are excluded from candidate sets during evaluation to ensure fairness and realism.

---

## 🔗 Multimodal Feature Extraction

### Text Embeddings

* multilingual-MiniLM-L12-v2
* multilingual-mpnet-base-v2
* stsb-xlm-r-multilingual
* LaBSE
* all-mpnet-base-v2

### Image Embeddings

* CLIP ViT-B/32
* CLIP-LAION-B16
* SigLIP-B16
* EVA02-CLIP-B16
* Swin-Tiny, CvT-13, MaxViT-Tiny

Results show that **CLIP-based image embeddings** and **Sentence-BERT–style multilingual text embeddings** provide the strongest performance gains .

---

## 🧪 Experimental Highlights

* **MMGCN and LightGCL** achieve the best overall performance across all metrics
* Textual features play a more critical role than visual features for basic fashion items
* Graph contrastive learning improves robustness under sparse interaction data
* Content-based models remain competitive in cold-start scenarios

Detailed ablation studies analyze:

* text vs image contribution
* attribute-level text removal
* modality-level performance degradation

---

## 📁 Repository Structure (Suggested)

```text
├── data/
│   ├── products.csv
│   ├── reviews.csv
│   └── processed/
├── preprocessing/
│   ├── crawl_data.py
│   ├── clean_data.py
│   └── build_graph.py
├── models/
│   ├── content_based.py
│   ├── user_based.py
│   ├── lightgcn.py
│   ├── lightgcl.py
│   └── mmgcn.py
├── experiments/
│   ├── train.py
│   ├── evaluate.py
│   └── ablation.py
├── results/
├── README.md
└── requirements.txt
```

---

## 🚀 Future Work

* Expand dataset to include **Vietnamese-specific fashion items** (e.g., *áo dài*)
* Replace cohort-based users with real interaction logs
* Integrate **LLMs** for semantic understanding and explanation generation
* Deploy as a **real-time recommendation system** and evaluate with live user feedback 

---

## 📖 Citation

If you use this code or dataset, please cite:

```
@article{nguyen2024fashiongnn,
  title={Fashion Recommendation via Graph Neural Networks and Multimodal Web-Crawled Data},
  author={Nguyen-Phuc, Mac and Kieu, Qui-Hung and Nguyen, Duy-Liem and Tran, Tri-Duc},
  institution={University of Information Technology - VNUHCM},
  year={2024}
}
```

---

If you want, I can also:

* **Align this README with a specific conference style** (SIGIR / RecSys / CIKM)
* **Refactor it for open-source dataset release**
* **Write a DATASET.md or MODEL_CARD.md** to strengthen reproducibility and reviewer trust
