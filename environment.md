# 运行环境说明

主要运行文件：

```text
part1_bag_of_words.ipynb
```

推荐运行平台：

```text
Kaggle Notebook
```

## 1. 为什么用 Kaggle Notebook

Kaggle Notebook 是 Kaggle 提供的云端 Jupyter Notebook 环境。

也就是说，你在网页里写代码、运行代码，但真正执行代码的是 Kaggle 的云端机器。

这就是老师说的“使用 Kaggle 算力”的意思。

这个项目的 Part 1 使用的是：

```text
Bag-of-Words + RandomForestClassifier
```

CPU 就可以运行，不需要 GPU。

GPU 更适合后续训练 Word2Vec、深度学习模型或 embedding 相关任务。

## 2. Python 环境

推荐 Python 版本：

```text
Python 3.9 或更高
```

需要的库：

```text
pandas
numpy
beautifulsoup4
scikit-learn
```

Kaggle Notebook 一般已经预装这些库，所以在 Kaggle 上通常不需要手动安装。

如果在本地运行，可以安装：

```bash
pip install pandas numpy beautifulsoup4 scikit-learn
```

## 3. Kaggle 数据

需要的数据文件来自 Kaggle 竞赛：

```text
word2vec-nlp-tutorial
```

竞赛链接：

<https://www.kaggle.com/c/word2vec-nlp-tutorial>

需要的文件：

```text
labeledTrainData.tsv
testData.tsv
```

`labeledTrainData.tsv` 是训练集，有情感标签。

`testData.tsv` 是测试集，没有情感标签，需要模型预测。

## 4. Kaggle Notebook 数据路径

在 Kaggle Notebook 右侧点击 `Add data`，添加这个 competition dataset 后，数据通常会出现在：

```text
/kaggle/input/word2vec-nlp-tutorial
```

Notebook 里默认使用这个路径：

```python
INPUT_DIR = Path("/kaggle/input/word2vec-nlp-tutorial")
```

如果 Kaggle 显示的路径不一样，需要把 Notebook 里的 `INPUT_DIR` 改成实际路径。

## 5. 运行方式

在 Kaggle Notebook 中打开：

```text
part1_bag_of_words.ipynb
```

然后从上到下运行每个单元格。

运行完成后，会生成：

```text
Bag_of_Words_model.csv
```

这个 CSV 可以上传到 Kaggle 竞赛页面提交。

## 6. 本地运行提醒

如果本地运行，需要自己下载 Kaggle 数据。

Kaggle 数据通常不能匿名下载，需要：

1. 登录 Kaggle。
2. 接受竞赛规则。
3. 使用网页下载，或配置 Kaggle API。

本地数据目录可以放成：

```text
data/
├── labeledTrainData.tsv
└── testData.tsv
```

然后把 Notebook 中的数据路径改成：

```python
INPUT_DIR = Path("data")
```

## 7. 不上传的数据

不建议把 Kaggle 原始数据上传到 GitHub。

原因是：

```text
数据属于 Kaggle competition dataset
下载和使用需要遵守竞赛规则
```

GitHub 中只上传 Notebook、README 和环境说明即可。
