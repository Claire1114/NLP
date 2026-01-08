# NLP Portfolio 

收錄NLP相關兩個專案，涵蓋：
- **詞向量（Word Embeddings）**：Word2Vec / GloVe 與 word analogy 任務評估
- **序列生成（Sequence Generation）**：以字元層級 RNN/LSTM/GRU 生成算式答案，並系統性做 ablation / robustness 實驗

---

## Projects

### 1) Word Embeddings Exploration: Word Analogy Task
**重點：** 使用 Google Word Analogy Dataset 評估 Word2Vec (Skip-gram) 的語義/語法捕捉能力，並設計三組對照實驗：  
(1) Wikipedia 不同抽樣比例（5%/10%/20%）  
(2) Wikipedia vs News Crawl 語料差異  
(3) 類比推理 scoring：3CosAdd vs 3CosMul :contentReference[oaicite:0]{index=0}

- Word2Vec 訓練設定（節錄）：`vector_size=300`, `window=5`, `min_count=2`, `sg=1`, `negative=5`, `epochs=10` :contentReference[oaicite:1]{index=1}  
- 語料比較：Wiki20（約 6.7 億 tokens）vs News25（約 7.2 億 tokens） :contentReference[oaicite:2]{index=2}  
- 3CosMul 對 3CosAdd：整體 accuracy 66.31% → 67.29%，在多個 syntactic 子類別提升較明顯 :contentReference[oaicite:3]{index=3}

📁 Project folder: `projects/word-embeddings-analogy/`

---

### 2) Arithmetic Answer Generation with Character-level Sequence Models (LSTM/GRU/Seq2Seq)
**重點：** 將「算式 → 答案」視為字元層級序列生成：輸入如 `12+34=`，模型需在 `=` 後逐字生成答案並在 `<eos>` 停止 :contentReference[oaicite:4]{index=4}  
我以 2-layer LSTM 為 baseline，並設計五組實驗觀察記憶機制、分佈漂移、label noise、訓練穩定性與 input reversal 的影響 :contentReference[oaicite:5]{index=5}

- 原始 Arithmetic dataset：Train 2,369,250 pieces / Eval 263,250 pieces；每筆為 2–3 個運算元、每個數字在 [0,50) :contentReference[oaicite:6]{index=6}  
- Baseline 超參數（節錄）：`batch_size=64`, `epochs=10`, `embed_dim=256`, `hidden_dim=256`, `Adam(lr=0.001)`, `grad_clip=1` :contentReference[oaicite:7]{index=7}  
- LSTM vs GRU：最終 LSTM validation accuracy 0.8927，GRU 0.7366 :contentReference[oaicite:8]{index=8}  
- 不使用 gradient clipping：觀察到 loss 在特定 epoch 暴衝、validation 收斂不穩，最終 accuracy 0.4678 :contentReference[oaicite:9]{index=9}  
- Seq2Seq + input reversal：loss 可下降但 accuracy 僅 0.1157（推測「整段反轉」破壞算式結構對齊） :contentReference[oaicite:10]{index=10}  

📁 Project folder: `projects/arithmetic-answer-generation/`

---

## Reproducibility (How to Run)

> Each project has its own environment. Please install dependencies per project.

Example:
```bash
cd projects/arithmetic-answer-generation
pip install -r requirements.txt
python -m src.train
python -m src.evaluate
