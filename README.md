# AI-Driven Login Anomaly Detection System

An unsupervised machine learning system built using **Scikit-Learn** and **Pandas** to baseline authentication logs and proactively flag potential brute-force and credential-stuffing attacks. 

Developed as a self-directed summer upskilling initiative to bridge the gap between Data Science and Security Analytics (SecOps).

---

## Tech Stack & Architecture
* **Language:** Python 3.13
* **Libraries:** Pandas, NumPy, Scikit-Learn, Seaborn, Matplotlib
* **Environment:** Jupyter Notebook / VS Code (Anaconda Base Environment)
* **Algorithm:** Isolation Forest (Unsupervised Anomaly Detection)

---

## Project Overview & Security Context
Traditional Security Information and Event Management (SIEM) systems rely on rigid, static thresholds (e.g., *alert if failed logins > 5*). Attackers bypass this by executing slow, distributed brute-force attacks. 

This system solves that problem by using **behavioral baselining**. Instead of looking at a single metric, it analyzes multi-dimensional patterns (login hour velocity, aggregate failed attempts, and IP diversity) to spot stealthy malicious outliers without needing historical attack labels.

---

##  Feature Engineering Pipeline
Raw system logs are processed and aggregated using Pandas into three core behavioral features:
1. `failed_attempts`: Total count of authentication failures.
2. `login_hour`: The average time of day the activity took place (to detect anomalous midnight spikes).
3. `distinct_ip_count`: The distribution of unique IP addresses attempting access.

---

##  Key Insights & Results
* **Imbalanced Data Handling:** Since malicious attacks make up a fraction of total network traffic, an **Isolation Forest** model was chosen due to its native strength in isolating anomalies in unsupervised, heavily imbalanced data.
* **Early Threat Identification:** The model successfully separates routine human errors (e.g., a user forgetting their password during business hours) from structural brute-force patterns (high-frequency attempts at 3 AM).
* **SOC Analyst Impact:** Reduces alert fatigue by generating a continuous `anomaly_score`, allowing security teams to prioritize high-risk indicators of compromise (IoCs) for immediate firewall blocking.

---

##  How to Run locally
1. Clone this repository or open the folder in **GitHub Desktop**.
2. Install dependencies:
   ```bash
   pip install pandas numpy scikit-learn matplotlib seaborn
