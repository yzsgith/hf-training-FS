# 项目目录结构说明

`my-bert-sentiment-model/` # 项目根目录
├── `configs/` # 存放配置文件
│ └── `training_args.yaml` # 或 .json，定义训练超参数
├── `data/` # 数据目录
│ ├── `raw/` # 原始数据
│ ├── `processed/` # 预处理后的数据
│ └── `dataset_script.py` # 自定义数据集加载脚本（如果需要）
├── `models/` # 模型存储目录
│ ├── `my_finetuned_model/` # 最终训练好的模型（由 trainer 保存）
│ │ ├── `config.json` # 模型架构配置
│ │ ├── `pytorch_model.bin` # 或 model.safetensors
│ │ ├── `tokenizer.json` # 分词器文件
│ │ ├── `vocab.txt` # 词汇表
│ │ ├── `tokenizer_config.json` # 分词器配置
│ │ └── `special_tokens_map.json`
│ └── `checkpoint-500/` # 训练过程中的检查点
├── `scripts/` # 实用脚本
│ ├── `train.py` # 主训练脚本
│ ├── `preprocess.py` # 数据预处理脚本
│ └── `predict.py` # 使用模型进行预测的脚本
├── `outputs/` # 训练输出（如日志、评估结果）
│ ├── `logs/` # 训练日志（TensorBoard 或文本日志）
│ └── `predictions/` # 模型预测输出
├── `requirements.txt` # Python 依赖包列表
├── `README.md` # 项目说明文档
└── `.gitignore` # Git 忽略文件规则

---

## 自动化创建脚本示例

以下 Python 代码示例演示了如何根据上述结构自动创建文件和目录。

```python
from typing import List
import os

def creatFilesOrDirectorys(pathNames: List[str]) -> None:
    """
    
# 定义需要创建的路径列表
configsName = [f"configs/{name}" for name in ["training_args.yaml"]]
dataName = [f"data/{name}" for name in ["raw/", "processed/", "dataset_script.py"]]
modelsName = [f"models/my_finetuned_model/{name}" for name in ["config.json", "pytorch_model.bin", "tokenizer.json", "vocab.txt", "tokenizer_config.json", "special_tokens_map.json"]] + ["models/checkpoint-500/"]
scriptsName = [f"scripts/{name}" for name in ["train.py", "preprocess.py", "predict.py"]]
outputsName = [f"outputs/{name}" for name in ["logs/", "predictions/"]]
rootFilesName = [name for name in ["requirements.txt", "README.md", ".gitignore"]]

# 合并所有路径
all_paths_to_create = configsName + dataName + modelsName + scriptsName + outputsName + rootFilesName

# 打印将要创建的内容（用于调试）
print("将要创建以下文件和目录:")
for item in all_paths_to_create:
    print(f"  - {item}")

# 执行创建操作
# creatFilesOrDirectorys(all_paths_to_create)
# print("所有文件和目录已创建完成！")
