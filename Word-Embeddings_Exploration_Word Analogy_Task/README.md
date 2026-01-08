# Word Embeddings Exploration (Word Analogy Task)

## Overview
本專案旨在探討 **word embeddings（詞向量）** 在語義與語法關係上的表現，並以 **Word Analogy Task** 作為主要評估方式。  
我以 Word2Vec（並視情況加入 GloVe 對照）建立詞向量表示，透過類比推理題型 `a:b :: c:?` 檢驗模型是否能捕捉「國家—首都」、「比較級—原級」、「動詞時態轉換」等關係。

> **資料來源說明**：本專案使用的訓練語料與評估資料集並非由我自行蒐集，而是由學長姐事先整理提供；因此本 repo 不包含原始訓練資料檔案。  
> 本專案的重點放在 **embedding 訓練流程、類比評估方法、與不同設定的比較分析**。

---

## Files
- `NLP_Word_Embeddings.ipynb`  
  主程式 Notebook：包含資料讀取、詞向量訓練/載入、analogy 推理、與結果統計分析。
- `Word-Embeddings-Exploration- Word2Vec & GloVe Implementation.pdf`  
  專案報告：整理方法、實驗設計與結果討論。
- `requirements.txt`  
  執行 Notebook 所需套件清單（建議使用虛擬環境安裝）。

---

## Experiments Summary
本專案以 **Google Word Analogy Dataset** 作為評估基準，採用 **Word2Vec (Skip-gram)** 訓練詞向量，並設計三組對照實驗，系統性比較「語料規模」、「語料領域」與「類比推理 scoring」對模型表現的影響。

**1) Wikipedia 抽樣比例比較（5% vs 10% vs 20%）** 觀察語料規模（5%→20%）對 analogy 準確率的邊際收益。

**2) 訓練語料庫比較（Wikipedia Wiki20 vs News Crawl News25）：** 比較知識導向（Wikipedia）與時事/日常語境導向（News Crawl）對語義/語法任務的影響。

**3) 類比推理算法比較（3CosAdd vs 3CosMul）：** 比較傳統 3CosAdd 與 3CosMul 在 analogy 任務的差異，特別關注語法型子題。


---

## How to Run
### 1) 建立環境與安裝依賴
```bash
pip install -r requirements.txt
