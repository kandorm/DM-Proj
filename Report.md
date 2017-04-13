# Report

## 数据预处理与可视化

### 新闻数据的读入与建立数据框对象

* 此部分使用XML包
* 核心部分为用xpathSApply解析XML文件，提取需要的数据


* 数据框（缺失数据用NA填充）
  * 文件名
  * 年
  * 月
  * 日
  * 分类（多个分类之间用“/”分隔，整体为字符串）
  * 全文（数据框中全文未进行预处理）
* 生成的数据框保存到“dataframe.csv"中

### 对新闻全文进行预处理

* 此部分使用NLP、tm包
* 核心部分为建立语料库Corpus以及用tm_map进行预处理
* 处理内容
  * 标点符号
  * 停用词
  * 数字
  * 空白字符
  * 将大写转换为小写
  * 词干化处理
* 预处理的全文存储在新生成的'Pre'文件夹下，按照dataframe中文件顺序分别为1.txt到500.txt

### 将每一篇新闻的全文表示成 BagOfWords 向量。

* 此时新闻全文为预处理后全文
* 核心部分为```TermDocumentMatrix(reuters)``` 建立BOW向量
* 由于生成的矩阵过大，生成的文件很难打开，如果希望看到结果建议运行玩代码后执行```View(m)``` ，此处放如部分截图![2017-04-13 11-07-53屏幕截图](/home/kandorm/图片/2017-04-13 11-07-53屏幕截图.png)

### 单词在所有新闻中出现的次数

* 出现次数超过100的词
  * 根据生成的BOW向量，取出现次数大于100的单词
  * 将次数大于100的单词存储在’wordfilter.csv‘中
* 给出出 现 次 数 最 多 的 100 个 词 并 对 这 些 词 画 出 “ 云 图 ”
  * 此部分使用RColorBrewer、wordcloud包

  * 生成的云图为’wordcloud.png‘

    ![wordcloud](/home/kandorm/RProjects/DM_Proj1/wordcloud.png)

### 单词长度的分布情况

* 单词长度的分布
  * 此部分使用ggplot2包

![wordlength_histogram](/home/kandorm/RProjects/DM_Proj1/wordlength_histogram.png)

### 每一类别下新闻数量的分布情况

* 每一类别下的新闻数量
  * 此部分使用ggplot2包

![classify_histogram](/home/kandorm/RProjects/DM_Proj1/classify_histogram.png)

### 每个月新闻数量的分布情况

* 每个月新闻数量的分布情况
  * 此部分使用ggplot2包

![month_histogram](/home/kandorm/RProjects/DM_Proj1/month_histogram.png)

## 新闻相似度计算

