# Chinese Paraphrase from Quora
我们公开的汉语复述数据来自于NLPCC2020论文——《复述平行语料构建及其应用方法研究》<br>

简介
==
本文提出基于翻译引擎的方法迁移英文复述数据到汉语。英文数据引用公开的[Quora](https://data.quora.com/First-Quora-Dataset-Release-Question-Pairs)问答数据集，经过人工评估选择有道翻译和搜狗翻译两个翻译引擎将英文数据迁移到汉语，构建大规模高质量汉语复述数据集。下面对论文中构建的数据集进行说明。<br>

汉语复述数据
==
我们选取Quora问答数据中标签为1的数据，分别经过有道、搜狗翻译引擎将训练集、验证集、测试集进行翻译，经过编辑距离过滤后得到的结果：

1、./Paraphrase from Quora/Youdao
--
        训练集（130660），验证集（4685），测试集（4685）
        示例：
        我怎样才能停止抑郁呢?[制表符]我能做什么来停止抑郁?
2、./Paraphrase from Quora/Sougou
--
        训练集（133069），验证集（4700），测试集（4700）
        示例：
        聪明的人是如何打发时间的？[制表符]聪明人如何度过他们的时间？
3、./Paraphrase from Quora/Annotated/chinese-gold.tsv
--
       在上述得到的两个测试集结果中，采用人工标注的方法筛选出高质量复述，构建复述评测集：
       复述评测集（1130）
汉语复述识别数据
==
选取Quora问答数据中标签为0的部分数据，经过搜狗翻译引擎构建汉语非复述数据，与上述搜狗翻译得到的复述数据的一部分结合构成汉语复述识别数据，应用于复述识别任务，其中输出标签0表示非复述，1表示复述。

./Paraphrase Recognition Data
--
        训练集（98542）：0标签——48554；1标签——49993
        验证集（9700） ：0标签——5000； 1标签——4700
        测试集（9521） ：0标签——4821； 1标签——4700
        示例：
        1[制表符]有哪些类型的媒体？[制表符]有多少种媒体？
        0[制表符]我如何扩大我的词汇量，提高我的英语写作能力？[制表符]我如何提高我的英语写作技能？
