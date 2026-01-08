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
本專案主要實驗與比較方向包含：

1. **Embedding 模型比較**
   - Word2Vec（Skip-gram / CBOW 依作業設定）
   - （可選）GloVe 作為對照

2. **推理策略比較**
   - **3CosAdd**：常見的向量算式 `b - a + c`
   - **3CosMul**：以乘法形式平衡相似度（在部分類別可能更穩定）

3. **語料/參數設定影響（依 notebook 實作為準）**
   - 比較不同語料來源或資料規模對 analogy accuracy 的影響
   - 觀察超參數（如 `vector_size / window / min_count / negative / epochs`）對結果的變化

> 結果以 **accuracy** 為主，並可依 analogy 的 category / subcategory 進行分群統計與比較。

---

## How to Run
### 1) 建立環境與安裝依賴
```bash
pip install -r requirements.txt
