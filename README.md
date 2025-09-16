# 🔐 7-Stage GCN with Edge-IIoTset + W&B  

An end-to-end pipeline for **IoT/IIoT anomaly detection** using a novel **7-Stage Graph Neural Network (GCN + GAT + Autoencoder)** architecture. This project integrates **Weights & Biases (W&B)** for experiment tracking and uses the **Edge-IIoTset dataset** for evaluation.  

---

## 📌 Features  
- ✅ 7-Stage GCN + GAT + Autoencoder hybrid model  
- ✅ Handles **imbalanced datasets** using SMOTE  
- ✅ Graph construction via **KNN (cosine similarity)**  
- ✅ Integrated with **W&B** for tracking & visualizations  
- ✅ Includes t-SNE embeddings, ROC/PR curves, loss/accuracy plots  
- ✅ Early stopping + learning rate scheduler  
- ✅ Final model saved as `.pt` for reuse  

---

## 🧠 7 Stages of the Model  
1. **SF-GCN** – Graph Convolution for spatial feature extraction  
2. **DS-GAT** – Attention layer for dynamic structural learning  
3. **Encoder** – Dimensionality reduction  
4. **Decoder** – Reconstruction for anomaly scoring  
5. **RCA-1 & RCA-2** – Residual Contextual Aggregation  
6. **FE** – Final graph feature extractor  
7. **Classifier** – Binary anomaly classifier  

---

## 📂 Dataset: Edge-IIoTset  

We use the **Edge-IIoTset Cyber-Security Dataset**:  
- [📥 Kaggle Dataset Link](https://www.kaggle.com/datasets/mohamedamineferrag/edgeiiotset-cyber-security-dataset-of-iot-iiot)  

Preprocessing includes:  
- Dropping redundant features  
- One-hot encoding categorical columns  
- Balancing with SMOTE  

---

## ⚡ Getting Started  

### 🔹 Run on Google Colab  

1. Clone this repo or copy the notebook.  
2. Install dependencies:  

```bash
python 
!pip install -q torch-scatter torch-sparse torch-geometric imbalanced-learn matplotlib seaborn wandb
Upload your kaggle.json to access the dataset.
```

Run the training script — logs and visualizations will sync to W&B.

# 📊 Experiment Tracking with W&B

This project logs automatically to Weights & Biases:

Training loss and accuracy curves

Confusion matrix

ROC & PR curves

Reconstruction error histograms

t-SNE visualizations at each stage

To enable logging, log in with:
``` python
import wandb
wandb.login()
```

# 📈 Results

Binary anomaly detection (Normal vs Attack)

# Achieves high precision, recall, and F1 on Edge-IIoTset
<img width="326" height="112" alt="image" src="https://github.com/user-attachments/assets/5779468d-5cf0-438b-a99c-48addcefe6e5" />


# t-SNE plots show progressive feature separation across stages

<img width="404" height="293" alt="image" src="https://github.com/user-attachments/assets/c3c8fd0f-166c-4205-9111-ca81feac2b9c" 
<img width="476" height="306" alt="image" src="https://github.com/user-attachments/assets/53f09791-178f-45c0-b1bf-5b7348d208fa" />
<img width="453" height="301" alt="image" src="https://github.com/user-attachments/assets/2b699632-fcdb-482d-8e09-45862bf5e56a" />
<img width="463" height="296" alt="image" src="https://github.com/user-attachments/assets/50f43f77-4d34-4ceb-bc0e-06d745ac5565" />
<img width="520" height="299" alt="image" src="https://github.com/user-attachments/assets/cb476770-c7fa-4230-b9fa-c2416a6aef54" />


# 💾 Saving & Loading the Model

Save after training:
```
torch.save(model.state_dict(), "7stage_model.pt")
```

Reload later:
```
model = SevenStageGCN(input_dim)
model.load_state_dict(torch.load("7stage_model.pt"))
model.eval()
```

👨‍💻 Author

Saravanan Palani(Assistant Professor VIT )
Harsha Raj Kumar(M.S. Computer Science @ Vanderbilt University)
Suhani Panda(Btech CSE @ VIT )
Sanjana B(Btech CSE @ VIT )
Research focus: AI, Graph Neural Networks, Anomaly Detection
