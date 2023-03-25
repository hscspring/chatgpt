
## 使用

### 准备数据

每一行一个json，必须包含`prompt`和`completion`两个字段。示例如下：

```bash
{"prompt": "问题：你是谁？\n", "completion": "不告诉你。"},
```

### 正常微调

```python
# 微调
from hchg.sft import GlmLora
data_path = "/path/to/json_data/"
model_id = "THUDM/chatglm-6b"
device = "cuda:0"
model = GlmLora(model_id, device=device)
model.load_data(data_path).tune_with(device)

# 推理
from hchg.sft import GlmLora
model_id = "THUDM/chatglm-6b"
device = "cuda:0"
model = GlmLora(model_id, device=device)
model.load_pretrained("/path/to/lora_pt").eval()
inp = "你是谁？"
model.chat(inp)
```

### 量化微调




## 数据集

法律问答，共3.6w条，筛选后（取最佳答案）18238条。

来自：https://github.com/SophonPlus/ChineseNlpCorpus/blob/master/datasets/lawzhidao/intro.ipynb