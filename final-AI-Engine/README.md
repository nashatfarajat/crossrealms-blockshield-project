# BlockShield AI Integration

**Final AI Engine – CrossRealms Internship Project**  
Author: *Nashat Alfarajat, BlockShield AI Development Team*

---

## 📌 Overview
This repo contains the AI pipeline developed for the **BlockShield Project** during my internship with CrossRealms.  
The goal was to transform raw PCAP captures into structured flow features, apply clustering for pseudo-labeling, and train a supervised model for intrusion detection.

---

## 🔑 Features
- **Flow extraction** from PCAPs using Scapy (CICFlowMeter-style).  
- **88 statistical & protocol-level features** per flow.  
- **K-Means clustering (k=4)** for pseudo-labels (silhouette = 0.96).  
- **Random Forest classifier** trained with SMOTE to handle imbalance.  
- **Scalable pipeline** ready for higher-quality or labeled PCAPs.  

---

## ▶️ Usage
This project was developed and tested **locally on Jupyter Notebook**.  
To reproduce the work:  
1. Clone the repository.  
2. Open the notebook file (`.ipynb`) in Jupyter.  
3. Run the cells in order to parse PCAPs, extract features, cluster, and train the model.  

---

## 📊 Results
- ~244k packets → ~70k flows extracted.  
- K-Means produced 4 clusters (active vs. background traffic).  
- Random Forest achieved **>99% accuracy** on cluster-based labels.  

---

## 🏁 Conclusion
Even with noisy honeypot data, the project successfully delivered a **working AI pipeline** for BlockShield.  
It provides a reusable foundation for future intrusion detection research once higher-quality or labeled datasets are available.  

---
