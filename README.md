# sparse-attention
自适应的稀疏注意力，主要方法是在第一个Transformer层近似一个低秩的注意力分数矩阵，以此为依据构造掩码矩阵

### 2024.07.22：
#### 效果（163M的smallGPT2，数据集为Wikitext-103，指标为困惑度）
![image](https://github.com/user-attachments/assets/a1064b1d-1fef-4ab5-bd37-199468d90e5c)


Longformer、BigBird、Reformer、Routing Transformer

# 稀疏注意力研究：
### Transformer-XL
其实并不是稀疏的，但比较早的注意力魔改，注意力结合RNN，下文可以获取上文信息，但上文无法获取下文信息。上下文交互不完全。
![image](https://github.com/user-attachments/assets/086c2458-b6ad-4804-a062-f4656d28b641)
### Longformer
经典稀疏注意力，但稀疏位置是人为固定的，且解释性较差
![image](https://github.com/user-attachments/assets/374d9394-d09d-47e0-a934-fa1af1d1a7e4)

# NLP常用的数据集

整理了NLP方向数据集，实际使用时请根据需要：

## 阅读理解

|  数据集名称   | 简介 | 
|  ----  | ----- | 
|  [SQuAD](https://rajpurkar.github.io/SQuAD-explorer/) | 斯坦福问答数据集，包括SQuAD1.1和SQuAD2.0|
|  [DuReader-yesno](https://aistudio.baidu.com/aistudio/competition/detail/49) | 千言数据集：阅读理解，判断答案极性|
|  [DuReader-robust](https://aistudio.baidu.com/aistudio/competition/detail/49) | 千言数据集：阅读理解，答案原文抽取
|  [CMRC2018](http://hfl-rc.com/cmrc2018/) | 第二届“讯飞杯”中文机器阅读理解评测数据集|
|  [DRCD](https://github.com/DRCKnowledgeTeam/DRCD) | 台達閱讀理解資料集|
|  [TriviaQA](http://nlp.cs.washington.edu/triviaqa/) | Washington大学问答数据集|
|  [C3](https://dataset.org/c3/) | 阅读理解单选题 |


## 文本分类

| 数据集名称  | 简介 | 
| ----  | --------- | 
|  [CoLA](https://nyu-mll.github.io/CoLA/) | 单句分类任务，二分类，判断句子是否合法| 
|  [SST-2](https://nlp.stanford.edu/sentiment/index.html) | 单句分类任务，二分类，判断句子情感极性| 
|  [MRPC](https://microsoft.com/en-us/download/details.aspx?id=52398) | 句对匹配任务，二分类，判断句子对是否是相同意思| 
|  [STSB](http://ixa2.si.ehu.es/stswiki/index.php/STSbenchmark) | 计算句子对相似性，分数为1~5| 
|  [QQP](https://data.quora.com/First-Quora-Dataset-Release-Question-Pairs) | 判定句子对是否等效，等效、不等效两种情况，二分类任务| 
|  [MNLI](http://www.nyu.edu/projects/bowman/multinli/) | 句子对，一个前提，一个是假设。前提和假设的关系有三种情况：蕴含（entailment），矛盾（contradiction），中立（neutral）。句子对三分类问题|
|  [QNLI](https://rajpurkar.github.io/SQuAD-explorer/) | 判断问题（question）和句子（sentence）是否蕴含，蕴含和不蕴含，二分类| 
|  [RTE](https://aclweb.org/aclwiki/Recognizing_Textual_Entailment) | 判断句对是否蕴含，句子1和句子2是否互为蕴含，二分类任务| 
|  [WNLI](https://cs.nyu.edu/faculty/davise/papers/WinogradSchemas/WS.html) | 判断句子对是否相关，相关或不相关，二分类任务|
|  [LCQMC](http://icrc.hitsz.edu.cn/Article/show/171.html) | A Large-scale Chinese Question Matching Corpus 语义匹配数据集|
|  [ChnSentiCorp](https://github.com/SophonPlus/ChineseNlpCorpus/blob/master/datasets/ChnSentiCorp_htl_all/intro.ipynb) | 中文评论情感分析语料| 
|  [COTE-DP](https://aistudio.baidu.com/aistudio/competition/detail/50/?isFromLuge=1) | 中文观点抽取语料  |
|  [SE-ABSA16_PHNS](https://aistudio.baidu.com/aistudio/competition/detail/50/?isFromLuge=1) | 中文评价对象级情感分析语料|
|  [AFQMC](https://github.com/CLUEbenchmark/CLUE) | 蚂蚁金融语义相似度数据集，1表示句子1和句子2的含义类似，0表示含义不同|
|  [TNEWS](https://github.com/CLUEbenchmark/CLUE) | 今日头条中文新闻（短文本）分类，共15类| 
|  [IFLYTEK](https://github.com/CLUEbenchmark/CLUE) | 长文本分类，共119个类别| 
|  [OCNLI](https://github.com/cluebenchmark/OCNLI) | 原生中文自然语言推理数据集，句子对三分类问题| 
|  [CMNLI ](https://github.com/CLUEbenchmark/CLUE) | 中文语言推理任务，判断sentence1和sentence2的关系：蕴含（entailment），矛盾（contradiction），中立（neutral）。句子对三分类问题 | 
|  [CLUEWSC2020](https://github.com/CLUEbenchmark/CLUE) | WSC Winograd模式挑战中文版，代词消歧任务，二分类任务| 
|  [CSL](https://github.com/P01son6415/CSL) | 论文关键词识别，判断关键词是否全部为真实关键词，二分类任务 | 
|  [EPRSTMT](https://github.com/CLUEbenchmark/FewCLUE/tree/main/datasets)  | FewCLUE 评测中的电商产品评论情感分析数据集，Positive、Negative 情感 2 分类任务| 
|  [CSLDCP](https://github.com/CLUEbenchmark/FewCLUE/tree/main/datasets)  | FewCLUE 评测中的中文科学文献学科分类数据集，根据文献的中文摘要判断文献类别，共 67 类别。| 
|  [TNEWSF](https://github.com/CLUEbenchmark/FewCLUE/tree/main/datasets)  | FewCLUE 评测中的今日头条中文新闻（短文本）分类，共15类 | 
|  [IFLYTEK](https://github.com/CLUEbenchmark/FewCLUE/tree/main/datasets)  | FewCLUE 评测中的长文本分类任务，共 119 个类别 | 
|  [OCNLIF](https://github.com/CLUEbenchmark/FewCLUE/tree/main/datasets)  | FewCLUE 评测中的中文自然语言推理数据集，句子对三分类问题 | 
|  [BUSTM](https://github.com/CLUEbenchmark/FewCLUE/tree/main/datasets)  | FewCLUE 评测中对话短文本语义匹配数据集, 2 分类任务 | 
|  [CHIDF](https://github.com/CLUEbenchmark/FewCLUE/tree/main/datasets)  | FewCLUE 评测中的成语阅读理解填空, 根据文本内容从候选 7 个成语中预测正确的成语 | 
|  [CSLF](https://github.com/CLUEbenchmark/FewCLUE/tree/main/datasets)  | FewCLUE 评测中的论文关键词识别，判断关键词是否全部为真实关键词，二分类任务 | 
|  [CLUEWSCF](https://github.com/CLUEbenchmark/FewCLUE/tree/main/datasets)  | FewCLUE 评测中的 WSC Winograd 模式挑战中文版，代词消歧任务，二分类任务 | 
| [THUCNews](https://github.com/gaussic/text-classification-cnn-rnn#%E6%95%B0%E6%8D%AE%E9%9B%86) |  THUCNews中文新闻类别分类 | 
| [HYP](https://pan.webis.de/semeval19/semeval19-web/) | 英文政治新闻情感分类语料  | 
|  [XNLI](https://github.com/facebookresearch/XNLI) | 15种语言自然语言推理数据集，三分类任务. | 
|  [XNLI_CN](https://github.com/facebookresearch/XNLI) | 中文自然语言推理数据集（XNLI的子集），三分类任务. | 

## 文本匹配

|  数据集名称   | 简介 | 
|  ----  | --------- | 
| [CAIL2019-SCM](https://github.com/china-ai-law-challenge/CAIL2019/tree/master/scm) | 相似法律案例匹配  | 

## 序列标注

|  数据集名称   | 简介 | 
|  ----  | --------- | 
|  [MSRA_NER](https://github.com/lemonhu/NER-BERT-pytorch/tree/master/data/msra) | MSRA 命名实体识别数据集| 
|  [People's Daily](https://github.com/OYE93/Chinese-NLP-Corpus/tree/master/NER/People's%20Daily) | 人民日报命名实体识别数据集| 
|  [CoNLL-2002](https://www.aclweb.org/anthology/W02-2024/) | 西班牙语和荷兰语实体识别数据集| 


## 机器翻译

| 数据集名称  | 简介 | 
| ----  | --------- |
|  [IWSLT15](https://workshop2015.iwslt.org/) | IWSLT'15 English-Vietnamese data 英语-越南语翻译数据集|
|  [WMT14ENDE](http://www.statmt.org/wmt14/translation-task.html) | WMT14 EN-DE 经过BPE分词的英语-德语翻译数据集| 

## 机器同传

| 数据集名称  | 简介 | 
| ----  | --------- | 
|  [BSTC](https://aistudio.baidu.com/aistudio/competition/detail/44/) | 千言数据集：机器同传，包括transcription_translation和asr |

## 对话系统

| 数据集名称  | 简介 | 
| ----  | --------- | 
|  [DuConv](https://aistudio.baidu.com/aistudio/competition/detail/48/) | 千言数据集：开放域对话，中文知识型对话数据集 | 
## 文本生成

| 数据集名称  | 简介 | 
| ----  | --------- | 
|  [Poetry](https://github.com/chinese-poetry/chinese-poetry) | 中文诗歌古典文集数据| 
|  [Couplet](https://github.com/v-zich/couplet-clean-dataset) | 中文对联数据集| 
|  [DuReaderQG](https://github.com/PaddlePaddle/Research/tree/master/NLP/DuReader-Robust-BASELINE) | 基于DuReader的问题生成数据集| 
|  [AdvertiseGen](https://github.com/ZhihongShao/Planning-based-Hierarchical-Variational-Model) | 中文文案生成数据集|
|  [LCSTS_new](https://aclanthology.org/D15-1229.pdf) | 中文摘要生成数据集| 
|  [CNN/Dailymail](https://github.com/abisee/cnn-dailymail) | 英文摘要生成数据集| 


## 语料库

| 数据集名称  | 简介 | 
| ----  | --------- | 
|  [PTB](http://www.fit.vutbr.cz/~imikolov/rnnlm/) | Penn Treebank Dataset | 
|  [Yahoo Answer 100k](https://arxiv.org/pdf/1702.08139.pdf)  | 从Yahoo Answer采样100K| 
