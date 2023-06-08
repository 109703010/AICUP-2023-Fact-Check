# AICUP-2023-Fact-Check
## 運行環境
請以 colab 開啟，並在 編輯>筆記本設定 中設定

執行階段類型： Python 3 硬體加速器： GPU

### Part 0
執行 `%pip install -r requirements.txt` 以安裝需要的函式庫
### Part 1
執行
```
%pip install -U ckiptagger[tf,gdown]
data_utils.download_data_gdown("./")
```
以下載 ckip 斷詞、 POS 及 NER 所需資源

## 資料
data 1~4 分別為 Document Retrieval 中的
- 1：拉高 Precision
- 2：分段取值
- 3：拉高 Recall
- 4：Cosine Similarity

### Document Retrieval

- `data/hanlp_con_result.pkl` - NPs的輸出結果
- `data/train_doc5.jsonl` - 找到的Document

請手動更改 `data/train_doc5.jsonl` 為 `data/train_doc5_data{ID}.jsonl`

### Sentence Retrieval
- `data/train_doc5_sent5_data{ID}_{MODEL_PARA}.jsonl` - 找到的相關證據句

## 訓練
- `checkpoint/sent/*` 儲存 Sentence Retrieval 的模型
- `checkpoint/claim/*` 儲存 Claim Verification 的模型

## 重現最優模型
### 下載儲存的模型
請至
https://drive.google.com/drive/folders/1YROgftReHRzOV8TWCyQfqeixE9c0VET7
開啟Model資料夾

### 輸出結果
`data/` 資料夾即為最佳模型所使用／產生的資料

### Part 1

請選擇 `full_pipeline_data4.ipynb` 並執行

Part 2, 3 的 `Use_Data_From_Part_1` 填入 4 以利資料讀取

### Part 2
超參數設定如下：
```
# 模型設定
NUM_EPOCHS: 20
LR: 1e-05
TRAIN_BATCH_SIZE: 64
TEST_BATCH_SIZE
TOP_N: 5

# 擴增資料集設定
SENT_SEPERATE: "yes"
COMMA: "yes"
PERIOD: "no"
RANDOM_CHOOSE: "yes"

# 篩選閾值
PROB_LIMIT: 0.75

Testing_or_not: "no"
```

### Part 3
模型設定如下：
```
NUM_EPOCHS:20
TRAIN_BATCH_SIZE: 24
TEST_BATCH_SIZE: 24
LR: 1e-05
MAX_SEQ_LEN: 256
EVIDENCE_TOPK: 5
```