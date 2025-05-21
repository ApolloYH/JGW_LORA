# 🪶 甲骨文多模态识别与释义 LoRA 微调项目

## 📚 项目简介

本项目旨在通过多模态大模型（Qwen2-VL-2B）对甲骨文图片及其释义进行 LoRA 微调，实现甲骨文图片的自动释义。项目涵盖了数据准备、图片生成、数据格式转换、模型下载与训练、推理验证等完整流程。

## 🗂️ 目录结构

```
📁 .
├── 📓 aistudio.ipynb           # 主项目流程 Jupyter Notebook
├── 📁 data/                    # 数据与字体文件目录
│   ├── 🅰️ AYJGW.DvV-wIBv.ttf   # 甲骨文字体库
│   ├── 📄 jgw_detail_ay_1530.jsonl   # 甲骨文释义数据集1
│   ├── 📄 jgw_detail_vl_web_725.jsonl# 甲骨文释义数据集2
│   ├── 🖼️ jgw_vl_total/        # 生成的甲骨文图片
│   ├── 📄 data_vl.json         # 训练用多模态对话格式数据
│   ├── 📄 data_vl_train.json   # 训练集
│   ├── 📄 data_vl_test.json    # 测试集
├── 📁 output/                  # LoRA 微调输出目录
│   └── Qwen2-VL-2B/
```

## 🛠️ 环境依赖

- 🐍 Python 3.9+
- 🔥 torch
- 🤗 transformers
- 📚 datasets
- 🪶 peft
- 🏷️ modelscope
- 🖼️ pillow
- 📊 matplotlib

建议使用 `pip` 安装依赖：

```bash
pip install -r requirements.txt
```

## 🗃️ 数据准备

1. 📦 **数据集与字体**  
   - 甲骨文字体包和释义数据集已放在 `data/` 目录下。
   - 字体文件：`AYJGW.DvV-wIBv.ttf`
   - 释义数据集：`jgw_detail_ay_1530.jsonl`、`jgw_detail_vl_web_725.jsonl`

2. 🖼️ **甲骨文图片生成**  
   - 通过 PIL 加载字体，将所有甲骨文字符 ID 转为图片，保存在 `data/jgw_vl_total/`。

3. 🔄 **多模态训练数据格式转换**  
   - 将图片路径与释义整理为多模态对话格式，生成 `data_vl.json`，并拆分为训练集和测试集。

## 🧑‍💻 模型微调流程

1. ⬇️ **模型下载与加载**  
   - 使用 `modelscope` 下载 Qwen2-VL-2B-Instruct 模型，并用 Transformers 加载。

2. 🧹 **数据预处理**  
   - 编写 `process_func` 函数，将多模态对话数据转为模型输入格式。

3. 🪄 **LoRA 配置与训练**  
   - 配置 LoRA 参数，使用 `Trainer` 进行微调训练，输出权重保存在 `output/Qwen2-VL-2B/`。

4. 🧪 **推理与验证**  
   - 加载微调后的模型，对测试集图片进行释义验证。

## 📝 主要代码流程

- 🖼️ 甲骨文图片生成与保存
- 🔄 多模态对话数据构建
- 🤖 Qwen2-VL-2B 模型下载与加载
- 🪄 LoRA 微调训练
- 🧪 推理验证

## 🔗 参考

- [Qwen2-VL-2B 官方文档](https://chat.qwenlm.ai/)
- [ModelScope](https://modelscope.cn/)
- [self-llm](https://github.com/datawhalechina/self-llm/blob/master/models/Qwen2-VL/04-Qwen2-VL-2B%20Lora%20%E5%BE%AE%E8%B0%83.md)

## 🙏 致谢

感谢开源社区和甲骨文相关数据集的贡献者。

---

如需详细代码和流程，请参考 `lora_jgw.ipynb`。如有问题欢迎提 issue 或交流！
