# Kaggle Word2Vec NLP Tutorial Part 1：Bag-of-Words

这个项目是 Kaggle `word2vec-nlp-tutorial` 里的 Part 1 练习。

页面链接：

<https://www.kaggle.com/c/word2vec-nlp-tutorial/overview/part-1-for-beginners-bag-of-words>

虽然竞赛名字里有 Word2Vec，但 Part 1 实际做的是早期 NLP 中非常经典的 Bag-of-Words 方法。

简单来说，这个任务是根据电影评论文本判断情感：

```text
1 = 正面评论
0 = 负面评论
```

## 文件说明

这个仓库只保留最核心的 3 个文件：

```text
README.md
environment.md
part1_bag_of_words.ipynb
```

`README.md` 是项目说明。

`environment.md` 说明运行环境、Kaggle Notebook 使用方式和数据获取方式。

`part1_bag_of_words.ipynb` 是主要代码文件，推荐直接在 Kaggle Notebook 或 Jupyter Notebook 中运行。

## 这个项目做了什么

整体流程是：

```text
读取电影评论数据
清洗文本
把文本转换成 Bag-of-Words 词频向量
训练随机森林分类器
预测测试集评论情感
生成 Kaggle 提交 CSV
```

早期 NLP 的核心思路是先把文本变成数字特征，再交给机器学习模型。

这里用的是 `CountVectorizer`。它会统计每条评论里常见词出现了多少次。

例如：

```text
good movie good
```

可能会被转换成类似：

```text
good: 2
movie: 1
bad: 0
```

模型并不是像人一样真正理解评论，而是从训练数据里学习哪些词更常出现在正面评论，哪些词更常出现在负面评论。

## 主要代码逻辑

Notebook 中主要包含这些步骤：

1. 导入 Python 库。
2. 读取 `labeledTrainData.tsv` 和 `testData.tsv`。
3. 用 BeautifulSoup 去掉 HTML 标签。
4. 用正则表达式去掉非英文字母字符。
5. 转小写、分词、去停用词。
6. 用 `CountVectorizer` 构建 Bag-of-Words 特征。
7. 用 `RandomForestClassifier` 训练模型。
8. 对测试集预测正负面。
9. 生成 `Bag_of_Words_model.csv`。

## Kaggle 上怎么运行

推荐在 Kaggle Notebook 中运行 `part1_bag_of_words.ipynb`。

Kaggle Notebook 本质上是云端 Jupyter Notebook。代码不是在本地电脑跑，而是在 Kaggle 提供的云端环境中运行。

运行步骤：

1. 登录 Kaggle。
2. 打开竞赛页面：<https://www.kaggle.com/c/word2vec-nlp-tutorial>
3. 接受竞赛规则。
4. 新建 Notebook。
5. 在右侧 `Add data` 添加 `word2vec-nlp-tutorial` 数据。
6. 上传或复制 `part1_bag_of_words.ipynb`。
7. 从上到下运行所有单元格。

Part 1 不需要 GPU，CPU 就可以完成。

## 输出

Notebook 运行完成后，会生成：

```text
Bag_of_Words_model.csv
```

这个文件可以提交到 Kaggle。

提交格式大概是：

```text
id,sentiment
123_4,1
567_8,0
```

## 学习重点

这次作业重点不是追求最高分，而是理解早期 NLP 的基本工作流：

```text
文本清洗
词袋模型
文本向量化
传统机器学习分类
Kaggle Notebook 运行和提交
```

后续的 Word2Vec、Embedding 和大模型，本质上也是在解决“如何把文本表示成更有语义的向量”这个问题。
