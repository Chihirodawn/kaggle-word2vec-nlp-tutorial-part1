# 运行环境说明

这个仓库对应 Kaggle `Bag of Words Meets Bags of Popcorn` 教程的四个部分。

主要运行文件：

```text
part1_bag_of_words.ipynb
part2_word_vectors.ipynb
part3_more_fun_with_word_vectors.ipynb
part4_comparing_methods.ipynb
```

推荐运行平台：

```text
Kaggle Notebook
```

## 1. 为什么用 Kaggle Notebook

Kaggle Notebook 是 Kaggle 提供的云端 Jupyter Notebook 环境。

代码写在网页里，实际执行在 Kaggle 的云端机器上。

这个项目大部分内容 CPU 就可以运行。

Part 2 和 Part 3 会训练 Word2Vec，计算量比 Part 1 大一些，但仍然不强制需要 GPU。

如果 Kaggle 账号暂时无法通过身份验证，GPU 用不了也不影响完成这个教程。

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
gensim
nltk
```

Kaggle Notebook 一般已经预装大部分库。

如果在本地运行，可以安装：

```bash
pip install pandas numpy beautifulsoup4 scikit-learn gensim nltk
```

`nltk` 在 notebook 里只是优先用于英文句子切分。

如果本地没有 NLTK 的 `punkt` 数据，notebook 会自动退回到简单正则切句，不会因此停止运行。

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
unlabeledTrainData.tsv
```

`labeledTrainData.tsv` 是有标签训练集。

`testData.tsv` 是测试集，没有情感标签，需要模型预测。

`unlabeledTrainData.tsv` 是没有标签的额外评论，主要用于训练 Word2Vec。

## 4. Kaggle Notebook 数据路径

在 Kaggle Notebook 右侧点击 `Add data`，添加这个 competition dataset 后，数据通常会出现在：

```text
/kaggle/input/word2vec-nlp-tutorial
```

这些 notebook 会自动查找：

```text
/kaggle/input/word2vec-nlp-tutorial
/kaggle/input
data
.
```

所以一般不需要手动修改路径。

如果仍然报找不到文件，说明 Kaggle Notebook 还没有正确添加 competition dataset。

## 5. 建议运行顺序

建议按顺序运行：

```text
1. part1_bag_of_words.ipynb
2. part2_word_vectors.ipynb
3. part3_more_fun_with_word_vectors.ipynb
4. part4_comparing_methods.ipynb
```

Part 2 会训练并保存：

```text
300features_40minwords_10context.model
```

Part 3 会优先加载这个模型。

如果没有找到模型，Part 3 会自动重新训练一个 Word2Vec 模型。

Part 4 用本地验证集比较 Bag-of-Words 和 Word2Vec 平均向量方法。

## 6. 输出文件

Part 1 会生成：

```text
Bag_of_Words_model.csv
```

Part 3 的平均词向量方法会生成：

```text
Word2Vec_AverageVectors.csv
```

Part 3 的 Bag of Centroids 方法会生成：

```text
BagOfCentroids.csv
```

这些 CSV 可以在 Kaggle 竞赛页面提交。

## 7. 关于 Part 3 的 KMeans

Part 3 里有 Bag of Centroids 方法。

它需要对所有词向量做 KMeans 聚类，原教程也提到这一步可能很慢。

为了更贴近 Kaggle 原教程，我把这部分开关设成：

```python
RUN_BAG_OF_CENTROIDS = True
```

如果只是快速演示，想跳过这一步，可以把它改成：

```python
RUN_BAG_OF_CENTROIDS = False
```

## 8. 本地运行提醒

如果本地运行，需要自己下载 Kaggle 数据。

Kaggle 数据通常不能匿名下载，需要：

1. 登录 Kaggle。
2. 接受竞赛规则。
3. 使用网页下载，或配置 Kaggle API。

本地数据目录可以放成：

```text
data/
├── labeledTrainData.tsv
├── testData.tsv
└── unlabeledTrainData.tsv
```

也可以直接放 `.tsv.zip`，notebook 会自动读取 zip 里的 TSV。

## 9. 不上传的数据

不建议把 Kaggle 原始数据上传到 GitHub。

原因是：

```text
数据属于 Kaggle competition dataset
下载和使用需要遵守竞赛规则
```

GitHub 中只上传 notebook、环境说明和必要的忽略规则即可。
