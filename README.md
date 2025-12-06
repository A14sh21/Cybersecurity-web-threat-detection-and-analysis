# Cybersecurity Web Threat Detection And Analysis

## Overview
This project focuses on detecting and analyzing suspicious web-traffic behavior using AWS CloudWatch logs as the primary data source. It combines Python-based preprocessing and machine learning with Tableau dashboarding to uncover potential cyberattacks. Through feature engineering, anomaly detection, clustering, and visual analytics, this project identifies malicious IPs, unusual session behaviors, abnormal traffic volumes, and protocol misuse patterns.

## Tech Stack
1. Python — pandas, numpy, scikit-learn
2. Machine Learning — Isolation Forest, DBSCAN
3. Visualization — Tableau (Interactive dashboard)
4. Environment — Jupyter Notebook
5. Dataset — AWS CloudWatch web traffic logs (283 records, 16 fields)

## Key Features
1. Data Preprocessing & Feature Engineering
Converted timestamps into session duration
Created new features: total_bytes_transferred, bytes_in/out ratios
Label-encoded categorical protocol fields
Handled duplicates & ensured dataset integrity

2. Anomaly Detection (Isolation Forest)
Trained on standardized features
Flagged 10% of sessions as anomalous
Identified abnormal bytes_in / bytes_out spikes, suspicious ports & response codes

3. Unsupervised Clustering (DBSCAN)
Validated outliers detected by Isolation Forest
Helped isolate “noise” traffic resembling cyberattacks
Highlighted unusual data clusters outside normal user behavior

4. Tableau Dashboard
Includes interactive visualizations:
High-risk IP addresses
Country-wise traffic origins
Time-series spikes in bytes_in & bytes_out
Anomaly markers across sessions

5. Dashboard Link:
https://public.tableau.com/views/CybersecurityWebThreatDetectionandAnalysis/Dashboard1

## Results
1. Identified IPs generating 28–29 repeated connections and were flagged as suspicious
2. Country code 2 contributed 2.65 GB of traffic which are possible data exfiltration
3. Sharp time-series spikes linked to coordinated attacks
4. Isolation Forest and DBSCAN validated overlapping anomaly points
5. TCP traffic (Protocol 6) dominated, common in port-scanning attacks

## Limitations
1. Encoded categorical fields lacked full metadata
2. No internal system logs were analyzed, only external traffic analyzed
3. Static log analysis (not real-time)
4. No threat intelligence APIs to verify bad IPs

## Future Enhancements
Real-time streaming via Kafka/Kinesis
Neural network–based anomaly detection
Threat intelligence integration (AbuseIPDB, VirusTotal)
Geo-mapping for IP origin tracking
Automated alerting and mitigation workflow
