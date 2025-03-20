# 第23章 评估大型语言模型性能的指标

## 1. 传统机器学习 vs. 大型语言模型
- **传统机器学习**：通过训练和验证数据集评估模型性能，计算准确率等简单指标。
- **大型语言模型**：输出非确定性，语言评估更具挑战性。

## 2. ROUGE 和 BLEU 指标
- **ROUGE**（Recall-Oriented Understudy for Gisting Evaluation）：
  - 用于评估自动生成摘要的质量。
  - 通过比较生成摘要与人工参考摘要来计算。
- **BLEU**（Bilingual Evaluation Understudy）：
  - 用于评估机器翻译文本的质量。
  - 通过比较生成翻译与人工参考翻译来计算。

## 3. ROUGE 指标详解
- **ROUGE-1**：
  - 计算生成句子与参考句子中匹配的 unigram（单个词）数量。
  - 召回率 = 匹配的 unigram 数量 / 参考句子中的 unigram 数量。
  - 精确率 = 匹配的 unigram 数量 / 生成句子中的 unigram 数量。
  - F1 分数 = 召回率和精确率的调和平均数。
  - **示例**：
    - 参考句子：`It is cold outside`
    - 生成句子：`It is very cold outside`
    - ROUGE-1 召回率 = 4/4 = 1.0
    - ROUGE-1 精确率 = 4/5 = 0.8
    - F1 分数 = 2 * (1.0 * 0.8) / (1.0 + 0.8) ≈ 0.89
- **ROUGE-2**：
  - 计算生成句子与参考句子中匹配的 bigram（两个词）数量。
  - 召回率、精确率和 F1 分数的计算方法与 ROUGE-1 类似。
  - **示例**：
    - 参考句子：`It is cold outside`
    - 生成句子：`It is very cold outside`
    - ROUGE-2 召回率 = 2/3 ≈ 0.67
    - ROUGE-2 精确率 = 2/4 = 0.5
    - F1 分数 = 2 * (0.67 * 0.5) / (0.67 + 0.5) ≈ 0.57
- **ROUGE-L**：
  - 计算生成句子与参考句子中最长公共子序列（LCS）的长度。
  - 使用 LCS 长度计算召回率、精确率和 F1 分数。
  - **示例**：
    - 参考句子：`It is cold outside`
    - 生成句子：`It is very cold outside`
    - LCS = `It is cold outside`（长度为 4）
    - ROUGE-L 召回率 = 2/4 = 0.5
    - ROUGE-L 精确率 = 2/5 = 0.4
    - F1 分数 = 2 * (0.5 * 0.4) / (0.5 + 0.4) ≈ 0.44

## 4. BLEU 指标详解
- **BLEU 分数**：
  - 计算生成翻译与参考翻译中匹配的 n-gram 数量。
  - 通过计算多个 n-gram 大小的平均精确率来量化翻译质量。
  - BLEU 分数越接近 1，生成翻译与参考翻译越接近。
  - **示例**：
    - 参考句子：`I am very happy to say that I am drinking a warm cup of tea`
    - 生成句子：`I am very happy that I am drinking a cup of tea`
    - BLEU 分数 = 0.495

## 5. 注意事项
- **ROUGE 和 BLEU 的局限性**：
  - 简单的 ROUGE 和 BLEU 分数可能导致生成质量较差的句子得分较高。
    - **示例**：
      - 参考句子：`It is cold outside`
      - 生成句子：`cold cold cold cold`
      - ROUGE-1 精确率 = 4/4 = 1.0（尽管句子无意义）
  - 需要结合其他评估基准进行综合评估。
- **适用场景**：
  - ROUGE 适用于摘要任务的诊断评估。
  - BLEU 适用于翻译任务的诊断评估。

## 6. 总结
- **ROUGE 和 BLEU** 是评估大型语言模型性能的简单指标，计算成本较低。
- **综合评估**：需要结合其他评估基准进行综合评估，以全面了解模型性能。
