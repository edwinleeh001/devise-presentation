# DeViSE · 讲者 B / Speaker B

演示第 10-19 页 · 每人上限 15:00（含视频、演示与交接）。逐段英文后接中文；现场只读一种语言。页码指网页演示，不是打印页。

以下是个人累计时段，可提前结束；14:30 后只作收束，15:00 前结束。B 接棒后将个人计时归零。

## 演示第 10 页 / Slide 10 · 先读实验协议，再读结果

个人累计 00:00-01:25

**[Slide 10]** Thank you. We’ve seen the method; now let’s ask what the experiments actually establish. First, we need the protocol. For seen-class evaluation, the authors split the original ImageNet validation set into 5,000 images for model selection and 45,000 for reporting results. This is not the hidden competition test set.

**[演示第 10 页]** 谢谢。方法已经介绍过了，下面看实验究竟支持哪些结论。首先看协议：在已见类别评估中，原始 ImageNet 验证集被分为 5,000 张调参图像和 45,000 张结果报告图像，并非竞赛隐藏测试集。

**[Slide 10]** The supplement specifies a single center crop and the same procedure for softmax. Zero-shot evaluation reuses the 500-dimensional model without extra tuning. Table 4 uses a different dataset year and class split, so we cannot compare its percentages directly with Table 2.

**[演示第 10 页]** 补充材料说明使用单个中心裁剪，softmax 采用相同流程。零样本评估直接复用 500 维模型，不额外调参。Table 4 使用不同年份的数据集和类别划分，因此不能把它的百分比与 Table 2 直接比较。

依据 / Source: Supplement §A.1, p.1; main paper pp.6–8

## 演示第 11 页 / Slide 11 · 正确标签与合理错误是两种指标

个人累计 01:25-02:45

**[Slide 11]** Flat hit at k checks whether the exact true label appears among the top k predictions. A related but incorrect bird name still counts as a miss. Hierarchical precision instead asks what fraction of those predictions falls inside a hierarchy-derived acceptable set around the true label.

**[演示第 11 页]** Flat hit@k 检查前 k 个预测中有没有准确的真实标签。相关但不正确的鸟类名称仍算错误。层级精度则检查这些预测中，有多少落在真实标签周围、由层级结构定义的可接受集合内。

**[Slide 11]** That set expands until it contains at least k labels, and may contain more. So hierarchical precision measures a different kind of correctness. A higher score does not necessarily mean more exact species names. We need both metrics to understand the results.

**[演示第 11 页]** 这个集合会扩展到至少包含 k 个标签，也可能更多。因此，层级精度衡量的是另一种正确性；分数更高，不一定表示预测对了更多准确物种名称。理解结果需要同时看这两种指标。

依据 / Source: Main §4, pp.4–5; Supplement §A.3, pp.2–3

## 演示第 12 页 / Slide 12 · 准确率接近，错误结构不同

个人累计 02:45-04:10

**[Slide 12]** On the thousand familiar classes, DeViSE is close to softmax, rather than uniformly better. Softmax reaches 55.6 percent at top one, compared with 54.9 percent for the thousand-dimensional DeViSE model. At top five, they are nearly tied: 78.5 versus 78.4 percent.

**[演示第 12 页]** 在熟悉的一千个类别上，DeViSE 接近 softmax，并非全面更好。Top-1 中，softmax 为 55.6%，千维 DeViSE 为 54.9%；Top-5 几乎持平，分别为 78.5% 和 78.4%。

**[Slide 12]** Some hierarchical scores improve, suggesting a difference in the kinds of mistakes. The random-embedding baseline also helps test the value of learned semantic structure. The larger question, though, is whether the model can transfer beyond those thousand training classes.

**[演示第 12 页]** 部分层级指标有所提升，说明错误类型可能不同。随机嵌入基线也帮助检验学习到的语义结构有什么价值。更关键的问题是：模型能否迁移到这一千个训练类别之外？

依据 / Source: Table 1, p.5

## 演示第 13 页 / Slide 13 · 候选标签越多，测试越困难

个人累计 04:10-06:30

**[Slide 13]** Figure 2 gives selected examples of zero-shot predictions. Watch for a correct label, a shared failure, and a case where the baseline does better.

**[演示第 13 页]** Figure 2 给出一些零样本预测案例。请留意一次正确预测、一次共同失败，以及一个基线更好的例子。

**[Slide 13 / 演示第 13 页 · 操作提示]** Play the Figure 2 video once, in the delivery language. Resume after 20 seconds.

按演讲语言播放一次 Figure 2 视频，20 秒后继续。

[English video](../media/devise-figure-2-en.mp4) · [中文视频](../media/devise-figure-2-zh.mp4)

**[Slide 13]** The correct lens label ranks fourth. Both models miss the exact salad-bar label, and the authors judge softmax’s spacecraft suggestions more nearly correct. These cases show strengths and limits, not overall accuracy. DeViSE searches a larger vocabulary; softmax can only output its training labels.

**[演示第 13 页]** 正确镜头标签排在第四位。两个模型都没命中准确的沙拉吧标签，而作者认为 softmax 的航天器预测更接近。案例展示能力与局限，不代表总体准确率。DeViSE 搜索更大的词表，softmax 只能输出训练标签。

**[Slide 13]** Table 2 gives the aggregate picture. For two-hop hit at five, unseen-only candidates yield 18.1 percent. Adding seen candidates lowers it to 7.9 percent. With 20,841 unseen labels, unseen-only hit at one is 0.8 percent and hit at five is 2.5 percent. The candidate set clearly matters.

**[演示第 13 页]** Table 2 才给出总体结果。2-hop 的 hit@5 在仅有未见候选时为 18.1%，加入已见候选后降至 7.9%。在 20,841 个未见标签下，仅未见候选的 hit@1 为 0.8%，hit@5 为 2.5%。候选集合显然很重要。

依据 / Source: Original Figure 2 and Table 2, p.6; §4.2 reading, p.7

## 演示第 14 页 / Slide 14 · 语义改善也有边界

个人累计 06:30-07:35

**[Slide 14]** The hierarchical results are conditional too. At two-hop precision at two, softmax scores 0.236, above 0.204 for DeViSE+1K. In the full label setting at k equals twenty, DeViSE+1K scores 0.101, above softmax’s 0.065. The winner depends on the setting.

**[演示第 14 页]** 层级结果也如此。2-hop 的 precision@2 中，softmax 为 0.236，高于 DeViSE+1K 的 0.204；全标签设置的 k=20 中，DeViSE+1K 为 0.101，高于 softmax 的 0.065。优劣取决于设置。

**[Slide 14]** WordNet is used to evaluate semantic closeness, even though text supplies the training embeddings. The evidence supports useful semantic transfer, not a claim that DeViSE wins everywhere. Table 4 reinforces the importance of the comparison protocol.

**[演示第 14 页]** 训练嵌入来自文本，但语义评估仍使用 WordNet。证据支持有价值的语义迁移，不支持“DeViSE 在所有设置都获胜”。Table 4 会进一步说明比较协议的重要性。

依据 / Source: Table 3, p.7; Supplement §A.3

## 演示第 15 页 / Slide 15 · 候选集合可以改变方法排名

个人累计 07:35-08:45

**[Slide 15]** Table 4 uses a separate 800-seen, 200-unseen split. With only 200 candidate labels, DeViSE reaches 31.8 percent hit at five, below Mensink’s 35.7 percent. With all one thousand labels allowed, DeViSE reaches 9.0 percent, above Mensink’s 1.9 percent.

**[演示第 15 页]** Table 4 使用独立的 800 已见类、200 未见类划分。只有 200 个候选标签时，DeViSE 的 hit@5 为 31.8%，低于 Mensink 的 35.7%；允许全部一千个标签时，DeViSE 为 9.0%，高于 Mensink 的 1.9%。

**[Slide 15]** The comparison reverses because the available answers change. Rohrbach also used a different unseen-class set, which limits a direct comparison. The lesson is simple: the candidate set is part of the task, so it must accompany the reported percentage.

**[演示第 15 页]** 可选答案改变，方法排名也会反转。Rohrbach 还使用了不同的未见类别集合，不能严格直接比较。结论很清楚：候选集合是任务的一部分，报告百分比时必须一起说明。

依据 / Source: Table 4, p.7; split description pp.7–8

## 演示第 16 页 / Slide 16 · 证据还没有证明什么

个人累计 08:45-10:40

**[Slide 16]** DeViSE can rank a label without having seen its training images, provided a suitable semantic representation is available. But language similarity does not always match visual similarity. A word such as crane can refer to a bird or a machine, while one embedding may mix those meanings.

**[演示第 16 页]** 只要有合适的语义表示，DeViSE 可以对没有视觉训练样本的标签排序。但语言相似不总是视觉相似。例如 crane 可以表示鸟或机器，一个嵌入可能混合这两种含义。

**[Slide 16]** Accuracy at top one is also low on very large vocabularies, and seen classes can attract predictions away from unseen ones. A controlled experiment using identical unseen labels with and without seen candidates could test that effect more directly. This is a proposed follow-up, not a result established here.

**[演示第 16 页]** 在大词表上，Top-1 准确率仍然较低；已见类别也可能把预测从未见类别吸引走。可以固定未见标签，只改变是否加入已见候选，进行受控实验来进一步检验。这是后续研究建议，并非这里已经证明的结果。

依据 / Source: Main §4.2–5, pp.6–8; Supplement §A.2

## 演示第 17 页 / Slide 17 · 与 ProtoNet 建立联系，但不混淆任务

个人累计 10:40-11:50

**[Slide 17]** Both DeViSE and ProtoNet use an embedding space, but their class representations come from different resources. ProtoNet averages labeled support-image embeddings to build a new class prototype. DeViSE obtains the class representation from language, without labeled images of that unseen class.

**[演示第 17 页]** DeViSE 和 ProtoNet 都使用嵌入空间，但类别表示来自不同资源。ProtoNet 平均标注支持图像的嵌入，形成新类原型；DeViSE 从语言中取得类别表示，不需要该未见类别的标注图像。

**[Slide 17]** This shared idea is useful, but the supervision assumptions differ. We should compare how the representations are supplied, rather than treat their reported accuracies as directly interchangeable.

**[演示第 17 页]** 两者的共同思路有启发性，但监督假设不同。更合适的比较是类别表示怎样获得，而不是直接拿它们的准确率互相替代。

依据 / Source: DeViSE §3.3; Snell et al. (2017), §2

## 演示第 18 页 / Slide 18 · 可以扩展的标签词表

个人累计 11:50-12:50

**[Slide 18]** An appealing application is a vocabulary that can change without adding a separately trained output unit for every label. The same visual mapping might support broad labels, such as car, or more specific vehicle categories, provided suitable text embeddings exist.

**[演示第 18 页]** 一个有吸引力的应用是灵活改变词表，不必为每个标签单独训练一个输出单元。同一视觉映射可以支持汽车这样的粗粒度标签，也可能支持更具体的车型，前提是有合适的文本嵌入。

**[Slide 18]** That is a possibility suggested by the method, not evidence of a deployed system. The paper does not establish reliable open-world recognition or unrestricted image captioning. Let me close with three points.

**[演示第 18 页]** 这是方法带来的潜在用途，不是已经部署的证据。论文没有证明可靠的开放世界识别，也没有实现不受限制的图像描述。最后总结三个要点。

依据 / Source: §5, p.8: proposed applications, not deployment evidence

## 演示第 19 页 / Slide 19 · 带走三个结论

个人累计 12:50-14:30

**[Slide 19]** First, language supplies class structure beyond the image training labels. Second, a ranking objective aligns images with that semantic space. Third, the evaluation protocol determines how we should interpret success: changing only the candidate set can substantially change the result.

**[演示第 19 页]** 第一，语言提供图像训练标签之外的类别结构。第二，排序目标让图像与语义空间对齐。第三，评估协议决定怎样理解成功：只改变候选集合，结果也可能明显改变。

**[Slide 19]** So DeViSE shows that meaningful label representations can support recognition of some visually unseen classes. Its success is useful but conditional, depending on the semantic resources and available candidates. Thank you. We’re happy to take your questions.

**[演示第 19 页]** 因此，DeViSE 说明有意义的标签表示能够帮助识别部分视觉上未见的类别。这种迁移有价值，但有条件，取决于语义资源和候选标签。谢谢大家，接下来我们一起回答问题。

依据 / Source: Frome et al. (2013), p.8

演示第 20 页 / Slide 20：共用参考资料，无需逐项朗读，问答另计。 Sources and Q&A follow the timed talk.
