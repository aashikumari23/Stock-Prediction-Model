#How to use the model
Click on the google collab link we shared and copy it to your drive.
Then run the first code block which will mount google drive
then create a folder take3 in your /content/drive/MyDrive/ 
then also create a folder inside take3/DGLSTM_outputs/
and then upload the files we shared ind_nifty500list_filtered_final.csv and aggregated_sheet.csv in take3 folder too. Then run the next code blocks from top to bottom in sequence and you wont have any problems.
If any problems contact 8660041473

# 📈 Stock Prediction Using LSTM + GAT + DGLSTM

This repository contains the implementation of a hybrid deep learning pipeline that leverages **LSTM**, **DGLSTM-based dynamic graph construction**, and **Graph Attention Networks (GAT)** to predict stock performance and rank the most profitable stocks using **Top-K evaluation metrics**.

## 🚀 Overview

The project aims to predict which stocks are most likely to be profitable in the next time step, using:

- **LSTM**: For learning temporal patterns from historical stock features.
- **DGLSTM**: For generating dynamic graph adjacency matrices based on LSTM embeddings.
- **GAT**: For capturing inter-stock relationships and enhancing embeddings through attention.
- **Top-K Evaluation**: For ranking stocks by predicted returns and comparing with actual outcomes.

---

## 🧠 Methodology

### 1. **LSTM Embeddings**
- Precomputed embeddings from a trained LSTM model capture temporal dependencies in stock price movement.
- Embeddings are L2 normalized before feeding into GAT.

### 2. **Dynamic Graph Construction (DGLSTM)**
- A dynamic graph is created for each split (`train`, `val`, `test`) using similarity among LSTM embeddings.
- Edges are weighted based on similarity scores between stocks.

### 3. **GAT Predictor**
- A Graph Attention Network is applied to the normalized LSTM embeddings and dynamically constructed graph.
- Produces enhanced node embeddings and binary predictions (profitable or not).

### 4. **Training & Validation**
- Uses Binary Cross-Entropy (BCE) Loss.
- Best model checkpoint is saved based on validation loss.
- Final evaluation is conducted on the test set.

### 5. **Top-K Evaluation**
Evaluation metrics:
- **Accuracy**: % of Top-K predicted stocks labeled as profitable.
- **Precision**: Overlap between Top-K predicted vs Top-K actual returns.
- **MRR (Mean Reciprocal Rank)**: Inverse average rank of actual Top-K return stocks in predicted list.
- **IRR (Inverse Return Rank)**: Inverse average rank of predicted Top-K stocks in true return list.
- **MAE**: Mean Absolute Error between predicted score and actual return for Top-K.

---

## 
