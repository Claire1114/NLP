# NLP Portfolio 

收錄NLP相關兩個專案，涵蓋：
- **詞向量（Word Embeddings）**：Word2Vec / GloVe 與 word analogy 任務評估
- **序列生成（Sequence Generation）**：以字元層級 RNN/LSTM/GRU 生成算式答案，並系統性做 ablation / robustness 實驗
- **多輸出學習（Multi-output Learning）**：句對任務同時做語意回歸 + 蘊含分類（BERT/RoBERTa/GPT-2）


---

## Project 1 — Word Embeddings Exploration (Word Analogy Task)
📁 Folder: `Word-Embeddings_Exploration_Word Analogy_Task/`

**重點內容**
- 訓練/比較詞向量（Word2Vec，並可包含 GloVe 對照）
- 使用 Word Analogy task 評估語義/語法關係
- 比較不同語料與資料規模對表現的影響

➡️ 詳細方法、實驗設定與結果請見該資料夾內 README / 報告。

---

## Project 2 — Arithmetic Answer Generation (Character-level LSTM/GRU/Seq2Seq)
📁 Folder: `Arithmetic Answer Generation_with Character_level_Sequence_Models/`

**重點內容**
- 將「算式 → 答案」視為字元層級序列生成（輸入如 `12+34=`，輸出生成答案直到 `<eos>`）
- 2-layer LSTM baseline，並做對照/消融：LSTM vs GRU、distribution shift、label noise、no gradient clipping、Seq2Seq + input reversal（negative result）

➡️ 詳細方法、實驗設定與結果請見該資料夾內 README / 報告。

---

## Project 3 — Multi-output Sentence Pair Learning (BERT / RoBERTa / GPT-2)
📁 Folder: `Multi-Output Transformer for Relatedness & Entailment/`

**重點內容**
- 以 **BERT-base-uncased multi-output（dual-head）** 作為基線，同時進行：  
  - **語意相關度回歸**
  - **文本蘊含三分類**
- 三組實驗：  
  - **(A) Multi-output vs 單任務**：分類提升（0.89 vs 0.86），回歸略下降（0.89 vs 0.89）  
  - **(B) Backbone 比較**：RoBERTa 最佳（0.91/0.89），BERT 次之（0.89/0.89），GPT-2 較弱（0.71/0.77）  
  - **(C) Weighted CE 消融**：整體下降（回歸0.88/分類0.85），支持主要瓶頸偏向 **task conflict**
- 包含錯誤分析與改進方向（反義詞/語意階層/句構混淆 → 資料增強、強模型、衝突緩解）

➡️ 詳細方法、實驗設定與結果請見該資料夾內 README / 報告。
