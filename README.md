# AICUP-2023-Fact-Check
## 運行環境
請以 colab 開啟，並在 編輯>筆記本設定 中設定

執行階段類型： Python 3 硬體加速器： GPU

## 資料
### Document Retrieval
- `data/hanlp_con_result.pkl` - NPs的輸出結果
- `data/train_doc5.jsonl` - 找到的Document

後續資料中的 data 1~4 分別為 Document Retrieval 中的
- 1：拉高 Precision
- 2：分段取值
- 3：拉高 Recall
- 4：Cosine Similarity

### Sentence Retrieval
- `data/train_doc5_sent5_data{ID}_{MODEL_PARA}.jsonl` - 找到的相關證據句

## 訓練
- `checkpoint/sent/*` 儲存 Sentence Retrieval 的模型
- `checkpoint/claim/*` 儲存 Claim Verification 的模型