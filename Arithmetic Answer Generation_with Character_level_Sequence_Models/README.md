# Arithmetic Answer Generation (Character-level LSTM/GRU/Seq2Seq)

## Overview
本專案將算式視為字元序列輸入（例如 `12+34=`），模型需在 `=` 後逐字生成答案，直到輸出 `<eos>` 結束。

## Files
- `LSTM.ipynb`：LSTM baseline 訓練與評估
- `Experiment.ipynb`：對照實驗整理（GRU、distribution shift、label noise、no grad clipping、Seq2Seq 等）
- `arithmetic_train.csv` / `arithmetic_eval.csv`：訓練/驗證資料（pieces）
- `requirements.txt`：環境依賴

## Experiments Summary
- LSTM vs GRU（記憶機制差異）
- Distribution shift：混入三位數造成泛化下降
- Label noise：teacher forcing 下錯誤標籤影響明顯
- Gradient clipping：移除後訓練不穩、loss spike
- Seq2Seq + input reversal：negative result（反轉輸入不一定適用於運算生成）

## How to Run
建議使用 Jupyter / VS Code / Colab 開啟 notebook 執行。
