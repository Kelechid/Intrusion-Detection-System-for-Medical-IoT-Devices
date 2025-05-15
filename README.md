# Intrusion-Detection-System-for-Medical-IoT-Devices
Intrusion Detection System for Medical IoT Devices Using Machine Learning and Cryptography 

IoT Intrusion Detection System (IDS) using Machine Learning

This project implements a machine learning-based Intrusion Detection System (IDS) for IoT networks. It focuses on detecting malicious traffic as either normal or intrusion, and includes supervised and unsupervised learning models capable of identifying known and zero-day attacks.
🔍 Project Objective

To develop a reliable IDS that:

    Classifies IoT traffic as either 'normal' or 'intrusion'

    Detects new/unknown (zero-day) attacks using unsupervised techniques

    Can be tested in real or simulated environments like Node-RED or virtual testbeds

📦 Dataset

We used the CICIoMT2024 dataset (CSV format) containing multiple files representing different attack types and benign traffic.

    Data Merge: All CSV files were combined.

    Label Mapping:

        All attack types → intrusion

        Benign data → normal

⚙️ Preprocessing

    Standardization: Applied StandardScaler to numeric features

    Label Encoding: 'normal' → 0, 'intrusion' → 1

    Feature Selection: Removed non-numeric and non-relevant features

    Train/Test Split: Dataset split for both model training and unseen evaluation

🧠 Models Used
✅ Supervised Model (Binary Classification)

    Recurrent Neural Network (RNN) (using LSTM layers)

    Trained to classify traffic as normal (0) or intrusion (1)

    Achieved ~99.6% accuracy on test data

🔄 Unsupervised Models (Anomaly Detection)

    Recurrent Autoencoder

        Learns only from normal traffic

        Flags high reconstruction error as anomaly/intrusion

    Isolation Forest

        Tree-based anomaly detection

        Performs poorly due to imbalance and high-dimensional data

📊 Evaluation Summary
Model	Accuracy	Precision	   Recall	                    F1-score
RNN Classifier	99.6%	1.00 / 0.93 (class-wise)	1.00 / 0.91	Excellent
Autoencoder   	99.0%	1.00 / 0.88	1.00              / 0.82	Strong
Isolation Forest	2.0%	Very poor	0.00 on intrusions	Not effective
🧪 Practical Testing Options

You can test this IDS in real-time using:

    Node-RED + MQTT devices: Connect simulated or real IoT sensors, send traffic, classify using model in real time.

    PCAP Replays: Use tcpreplay with converted flow CSVs (via CICFlowMeter).

    Virtual Testbeds: Cooja (Contiki), GNS3, or containerized IoT devices.

    Kali Linux: Generate test intrusions using nmap, slowloris, hping3.

📁 Folder Structure

├── data/
│   ├── train/
│   ├── test/
├── models/
│   ├── rnn_model.h5
│   ├── autoencoder.h5
├── notebooks/
│   ├── preprocessing.ipynb
│   ├── rnn_training.ipynb
│   ├── autoencoder_training.ipynb
├── src/
│   ├── utils.py
│   ├── predict.py
├── README.md

🚀 Future Work

    Integrate model into real-time stream processing

    Add explainable AI (XAI) methods for prediction transparency

    Deploy model on edge devices (e.g., Raspberry Pi)

🤝 Contributors

    Lead Developer: David Kelechi Anosike

    Tools Used: Python, TensorFlow, Pandas, Scikit-learn, Node-RED, Kali Linux, CICFlowMeter
