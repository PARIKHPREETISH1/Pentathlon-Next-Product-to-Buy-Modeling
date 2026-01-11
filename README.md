# Pentathlon – Next Product to Buy (NPTB) Modeling

## 📌 Project Overview
This project focuses on solving a real-world customer analytics problem from the Kellogg School of Management’s *Pentathlon* case. The objective is to predict the **next product category a customer is most likely to purchase** and determine whether sending a promotional email (or no message) maximizes expected profit.

Using randomized email assignment data, we model customer purchase behavior to enable **personalized marketing decisions** at scale.

---

## 🎯 Business Problem
Pentathlon faced a challenge in allocating limited promotional email capacity across multiple product departments. Sending too many emails increased unsubscribe rates, while sending too few reduced short-term revenue.

The key question:
> *Which product-specific promotional message (or no message) should be sent to each individual customer to maximize expected profit?*

---

## 🧠 Objectives
- Predict customer purchase probability across multiple product categories
- Estimate expected profit considering conversion, order size, and cost of goods sold (COGS)
- Compare personalized targeting vs. uniform and random email strategies
- Recommend a scalable, data-driven email allocation policy

---

## 📊 Dataset Overview
The dataset consists of ~600,000 customer–email observations and includes:

### Customer Attributes
- Age bucket
- Gender
- Income
- Education level (neighborhood-level)
- Number of children (neighborhood-level)

### Behavioral Features
- Department-wise purchase frequency over the past year

### Outcome Variables
- Purchase indicator (binary)
- Order size (conditional on purchase)

Customers were randomly assigned to receive:
- One of six department-specific promotional emails, or
- No email (control group)

This randomized setup enables causal inference and fair model comparison :contentReference[oaicite:0]{index=0}

---

## 🔍 Exploratory Data Analysis (EDA)
Key insights:
- Higher historical purchase frequency strongly predicts future purchases
- Customer response varies significantly by product category
- Promotional emails increase conversion probability but impact profit differently across segments

---

## 🤖 Modeling Approach
We implemented and tuned four machine learning models:

- **Logistic Regression** – Baseline and interpretable benchmark  
- **Random Forest** – Captures non-linear interactions  
- **Neural Network (MLP)** – Learns complex patterns in customer behavior  
- **XGBoost** – Best-performing model with strong generalization  

Each model was tuned using at least two hyperparameters and evaluated on a held-out test set.

---

## 📈 Model Performance (AUC)
| Model | AUC |
|-----|-----|
| Logistic Regression | 0.68 |
| Random Forest | 0.73 |
| Neural Network | 0.72 |
| **XGBoost** | **0.76** |

XGBoost delivered the strongest predictive performance for purchase probability and profit optimization.

---

## 💰 Profit Optimization Framework
For each customer, we:
1. Predicted purchase probability for each message type
2. Estimated expected order size
3. Calculated expected profit using a 60% COGS assumption
4. Selected the message (or no-message) with the highest expected profit

This enabled **fully personalized email targeting**.

---

## 📌 Key Results
- Personalized message assignment significantly outperformed:
  - Sending the same message to all customers
  - Random message assignment (status quo)
  - Sending no emails
- Expected profit gains scaled meaningfully for large email campaigns (e.g., 5M customers)
- Data-driven targeting resolved inter-department conflicts over email allocation

---

## 🧭 Strategic Recommendation
We propose a **monthly, analytics-driven email allocation policy** where:
- Each customer receives emails from the top two profit-maximizing departments
- Models are retrained monthly using recent data
- No-message remains a valid option to avoid over-emailing

---

## 🛠 Tools & Skills Used
- Python (Pandas, NumPy, Scikit-learn, XGBoost)
- Machine Learning & Hyperparameter Tuning
- Customer Analytics & Profit Modeling
- Experimental Design & Causal Reasoning
- Business Strategy & Decision Optimization

---

## 👥 Team
Team 39  
Aman Sharma  
Harsh Jasrapuria  
Sanjit Kangovi  
Preetish Parikh

---

## 📎 Files
- Jupyter Notebook: Model implementation and evaluation
- Presentation Deck: Business insights and recommendations
- Case Reference: Kellogg School of Management – Pentathlon Case :contentReference[oaicite:1]{index=1}
