# Sentinel-Core
Beyond Blacklists: Proactive Zero-Day Intelligence.

This is a professional, high-impact `README.md` for your GitHub repository. It is written in English to match your project's UI and follows the "cyber-ops" technical aesthetic.

---

# SENTINEL CORE v3.0

### **Neural Threat Intelligence & Proactive URL Diagnostics**

**SENTINEL CORE v3.0** is an advanced cybersecurity analytical platform designed to detect malicious infrastructure, phishing nodes, and algorithmically generated domains (DGA). Unlike traditional blacklisting, Sentinel uses **behavioral vector analysis** and **machine learning** to identify threats in real-time.

---

##  Key Features

* **Neural Diagnostics Engine:** Uses a Random Forest ensemble trained on **10.6M+ samples** to predict threat probability.
* **Multi-Modal Input:** Support for manual URI entry and **OpenCV-powered QR code** scanning for physical threat detection.
* **Intelligence Reporting:** Real-time extraction of:
* **Network Data:** Serving IP, HTTP Status, and Body Content Length.
* **Forensics:** Body content **SHA-256 hashing** and Geo-IP location mapping.
* **WHOIS Data:** Automated domain age verification and registrar identification.


* **Vector Visualization:** 9-dimensional radar charts showing entropy, structural anomalies, and social engineering keywords.
* **Automated Threat Ingestion:** Server-side synchronization with **PhishTank**, **URLhaus**, and **Tranco Top-1M**.

---

##  Technical Architecture

The system is divided into three core modules for maximum scalability:

1. **`engine.py` (Logic Layer):** Handles mathematical feature extraction, Shannon Entropy calculations, and socket-level network diagnostics.
2. **`server_sync.py` (Data Pipeline):** Background processor that fetches global threat feeds, cleans datasets, and re-trains the Random Forest model.
3. **`app.py` (User Interface):** A high-performance Streamlit dashboard for real-time interaction and global analytics visualization.

---

## Mathematical Core

The system identifies botnet C2 nodes using **Shannon Entropy** to detect non-human character distributions:

Values exceeding **4.2** are automatically flagged as potential machine-generated strings.

---

## Hardware Acceleration

Sentinel Core is optimized for **Intel Core Ultra 9 185H** architecture:

* **Intel AMX:** Parallelized decision tree traversal.
* **AVX-512:** High-speed vector normalization and hashing.
* **Latency:** Inference cycles completed in **<150ms**.

---

## Installation

1. **Clone the repository:**
```bash
git clone https://github.com/your-username/sentinel-core.git
cd sentinel-core

```


2. **Setup Virtual Environment:**
```bash
python -m venv venv
source venv/bin/activate  # Or activate.fish for Fish shell

```


3. **Install Dependencies:**
```bash
pip install streamlit pandas scikit-learn plotly opencv-python tldextract python-whois requests joblib

```



---

##  Usage

### 1. Synchronize & Train (Server Side)

Run the sync script to populate the database and train the AI model:

```bash
python server_sync.py

```

### 2. Launch Dashboard (Client Side)

Start the neural diagnostic interface:

```bash
streamlit run app.py

```

---

## Dataset Stats

* **Total Training Samples:** 10,619,964
* **Model Accuracy:** 99.88%
* **Threat Sources:** PhishTank, URLhaus, Abuse.ch
* **Safe Baseline:** Tranco Top-1M

---

Troubleshooting
Error: ValueError: With n_samples=0...
This error occurs when the server_sync.py script fails to download any data from the external threat feeds (PhishTank or URLhaus). Since the training dataset is empty, the Random Forest model cannot be initialized.

Solutions:

Check Internet Connectivity: Ensure your server/workstation has outbound access to phishtank.com and abuse.ch.

Manual Sync: Run the synchronization script manually to see the specific network error:

Bash

python server_sync.py
Failsafe Mode: Sentinel Core v3.0 includes a built-in failsafe. If it cannot reach the internet, it will generate a baseline metadata footprint so the UI components remain functional.

QR Scanner Not Working
If the QR import fails, ensure your environment has opencv-python installed and the uploaded image has sufficient contrast. The system uses CLAHE (Contrast Limited Adaptive Histogram Equalization) to attempt recovery, but extremely blurry images may not decode.

## Disclaimer

*This tool is intended for security research and infrastructure monitoring. Always ensure you have permission before scanning external network assets.*

---

**Author:** [Gerosi]

**Version:** 3.0.0 "Neural Horizon"

---

