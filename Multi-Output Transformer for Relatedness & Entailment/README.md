# Multi-Output Transformer for Relatedness & Entailment

## Overview
本專案以 **BERT-base-uncased multi-output（dual-head）** 作為基線，針對同一組句子配對（Sentence A / Sentence B）同時進行：
- **語意相關度回歸**（Semantic Relatedness Regression；以 Test Pearson 評估）
- **文本蘊含三分類**（Textual Entailment Classification；以 Test Accuracy 評估）

我透過三組實驗驗證多輸出學習的互補效果、不同 backbone 的差異，以及效能瓶頸是否來自類別不平衡或任務衝突（task conflict）。

> 資料來源與切分：本專案使用 Hugging Face `sem_eval_2014_task_1` 載入資料（train/validation/test 依資料集既定切分）。
> 本 repo 不包含原始資料檔，執行 notebook 時會自動下載。
---

## Files
- `Multi-Output Transformer for Relatedness & Entailment ... .ipynb`  
  主程式 Notebook（**包含所有實驗**）：資料載入、tokenization、模型訓練與評估，涵蓋  
  **(A) multi-output vs 單任務**、**(B) BERT/RoBERTa/GPT-2 比較**、**(C) Weighted CE Ablation**，並附錯誤分析。

- `Multi-Output Transformer for Relatedness & Entailment ... .pdf`  
  專案報告：整理方法、實驗設計與結果討論。

- `requirements.txt`  
  執行所需套件清單（建議使用虛擬環境安裝）。

---

## Experiments Summary
**(A) Multi-output vs Single-task（BERT-base）**  
- Multi-output 在分類上明顯提升（0.8910 vs 0.8567），回歸表現小幅下降（0.8900 vs 0.8945），顯示共享訓練帶來輕微干擾。

**(B) Backbone Comparison（BERT vs RoBERTa vs GPT-2）**  
- RoBERTa 整體最佳（0.9063/0.8947），BERT 次之（0.8900/0.8910），GPT-2 較弱（0.7074/0.7668）。

**(C) Weighted CE Ablation（分類 head 加權）**  
- 加權後整體下降（0.8778/0.8502），顯示主要瓶頸更偏向 **task conflict** 而非單純類別不平衡。

---
## How to Run
1. 建議建立虛擬環境並安裝套件(requirements.txt)
2. 執行 Notebook(Multi-Output Transformer for Relatedness & Entailment ... .ipynb)
**Checkpoints（最佳模型權重）**
由於 `.ckpt` 檔案較大，本 repo 不直接附上。請下載[[點此下載模型權重 (Google Drive)](你的網址)](https://drive.google.com/drive/folders/1To5HiXPBCOgDJ-aDEKDm7lRgAYjJGCpQ?usp=drive_link)

