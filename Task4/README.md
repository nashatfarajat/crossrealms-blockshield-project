# Honeypot Traffic Analysis and AI Engine

## Project Description
This project focuses on **developing an AI engine for detecting malicious activity** from honeypot network traffic. The workflow includes parsing raw PCAP files, extracting flow-level features, labeling data, and training a machine learning model to identify malicious patterns effectively.

## Feature Extraction Using Scapy
Raw PCAP files are parsed using **Scapy** to generate **flow-level features** suitable for AI modeling. Key steps include:

- **Packet Parsing:** Reading TCP/UDP packets and extracting source/destination IPs and ports.  
- **Flow Construction:** Grouping packets into flows based on the 5-tuple (src IP, dst IP, src port, dst port, protocol).  
- **Feature Computation:** Calculating flow statistics, including:
  - Total packets and bytes in forward and backward directions
  - Min, max, mean, and standard deviation of packet lengths
  - Inter-arrival times (IAT) and flow duration
  - TCP flag counts (SYN, ACK, FIN, etc.)
  - Bulk transfer statistics (bytes/packets per burst)
  - Idle and active time metrics
- **Data Output:** Structured **pandas DataFrame** ready for machine learning.

## Labeling Approaches
Labeling is essential for supervised AI model training:

1. **Clustering-Based Labels**  
   - Applied **K-Means clustering** (k=4) on selected flow features  
   - Clusters interpreted based on traffic behavior (benign vs potentially malicious)  
   - Produced initial labels to train the AI engine  

2. **Pre-Trained Model Labels**  
   - Used a **pre-trained model** from CIC-IDS-2017  
   - Automatically assigned labels, but results were highly imbalanced and less suitable for ML training  

## Building the AI Engine
The AI engine is built around a **Random Forest classifier** trained on the cluster-based labels:

- **Training and Evaluation:**  
  - 5-fold cross-validation  
  - Mean accuracy: 0.996  
  - Precision: 0.9957, Recall: 0.9957, F1 Score: 0.9956  
- Both false positives and false negatives are very low, indicating strong model performance.  

The engine learns patterns in flow-level features and cluster-based labels, enabling **detection of benign and malicious traffic** effectively.  

## Outcomes & Recommendations
- The AI engine demonstrates that flow-level features and preliminary labels can guide effective ML-based intrusion detection.  
- Using **larger and fully labeled datasets** would improve robustness and model generalization.  
- Some clusters could be interpreted more accurately, enhancing label quality for future training.  

## Files
- `pcap parsing & building a model.ipynb` – Notebook containing feature extraction, labeling, and AI engine training.  
- `Parsing Honeypot Traffic and Developing the AI Engine - report.pdf` – Detailed project report including methodology, results, and conclusions.
