# DeViSE - 精简双人中英对照讲稿

每段先英文、后中文；演示页码与网页展示一致。现场选择一种语言朗读，每人上限 15 分钟，含视频和演示。

## DeViSE · 讲者 A / Speaker A

演示第 1-9 页 · 每人上限 15:00（含视频、演示与交接）。逐段英文后接中文；现场只读一种语言。页码指网页演示，不是打印页。

以下是个人累计时段，可提前结束；14:30 后只作收束，15:00 前结束。最后一段交接给 B。

## 演示第 1 页 / Slide 1 · 模型能认出从未见过的类别吗？

个人累计 00:00-01:15

**[Slide 1]** Hello everyone. Today we’ll introduce DeViSE, a model that connects image recognition with meaning learned from language. I’ll explain how it works, and my co-presenter will discuss the experiments and their limits.

**[演示第 1 页]** 大家好，今天我们介绍 DeViSE：一个把图像识别与语言语义连接起来的模型。我先解释它怎样工作，再由我的搭档介绍实验及其局限。

**[Slide 1]** Here’s the starting question. If a classifier has no output for a shark, can it ever name one? Recognizing a new photograph is different from recognizing a new category. DeViSE uses language to help bridge that gap.

**[演示第 1 页]** 先想一个问题：如果分类器的输出里根本没有鲨鱼这个类别，它还能认出鲨鱼吗？识别一张新照片，与识别一个新类别不同。DeViSE 尝试借助语言跨过这道鸿沟。

依据 / Source: Frome et al. (2013), p.1

## 演示第 2 页 / Slide 2 · 没有训练图片，不等于没有信息

个人累计 01:15-02:30

**[Slide 2]** An unseen class has no labeled training images available to the visual model. But its name can still occur in text, so a word embedding may already be available. Zero-shot learning here means no visual training examples for that class, not no information at all.

**[演示第 2 页]** 未见类别没有可供视觉模型训练的标注图片，但它的名称仍可能出现在文本中，因此已有词向量。这里的零样本是指没有该类视觉训练样本，并不是什么信息都没有。

**[Slide 2]** Keep two sets separate: the images being tested, and the labels allowed as answers. Adding seen labels to the candidate list changes the competition, even when the test images stay the same. That distinction will matter in the results.

**[演示第 2 页]** 还要区分两个集合：被测试的图像，以及允许作为答案的候选标签。即使测试图像不变，加入已见标签也会改变竞争。这一点会影响后面的实验结果。

依据 / Source: Frome et al. (2013), p.2

## 演示第 3 页 / Slide 3 · 连接图像与词语的研究缺口

个人累计 02:30-03:45

**[Slide 3]** The building blocks already existed. Convolutional networks learned visual features, while language models placed related words near one another. A fixed softmax classifier, however, could only choose among its training labels.

**[演示第 3 页]** 相关基础已经存在：卷积网络学习视觉特征，语言模型把相关词放在相近位置。但固定的 softmax 分类器只能从训练标签里选择答案。

**[Slide 3]** DeViSE combines pretrained visual features, text-derived label vectors, and a ranking objective. It trains on a thousand visual classes and investigates transfer to roughly twenty thousand additional labels. The contribution is this combination at ImageNet scale. Let’s follow the information through the model.

**[演示第 3 页]** DeViSE 将预训练视觉特征、来自文本的标签向量和排序目标结合起来。它在一千个视觉类别上训练，并研究向约两万个额外标签迁移。其贡献是在 ImageNet 规模上实现这一组合。下面沿着信息流看模型。

依据 / Source: Frome et al. (2013), p.2

## 演示第 4 页 / Slide 4 · 两个预训练模型，一个语义接口

个人累计 03:45-05:25

**[Slide 4]** This short video gives the overview. Watch how an image moves from visual features into a space shared with label meanings.

**[演示第 4 页]** 这段短视频先给出总览。请留意图像怎样从视觉特征进入与标签含义共享的空间。

**[Slide 4 / 演示第 4 页 · 操作提示]** Play the overview once, in the delivery language. Resume after the narration ends.

按演讲语言播放一次总览视频，20 秒；旁白结束后继续。

[English video](../media/devise-20s-en.mp4) · [中文视频](../media/devise-20s-zh.mp4)

**[Slide 4]** Instead of predicting through a fixed softmax head, the image passes through a learned linear projection. We then compare the projected image with candidate label vectors. A new label can enter this comparison if its text embedding is available, although that does not guarantee a correct prediction. Now let’s look at the authors’ original diagram.

**[演示第 4 页]** 模型用可学习的线性投影替代固定的 softmax 分类头，再将图像投影与候选标签向量比较。只要有文本嵌入，新标签就能参加比较，但这不保证预测正确。接着看作者的原始架构图。

依据 / Source: Frome et al. (2013), p.3

## 演示第 5 页 / Slide 5 · 语义结构从哪里来

个人累计 05:25-07:40

**[Slide 5]** Figure 1 shows where the two representations come from. Follow the pretrained models into the joint system, then look at panel B.

**[演示第 5 页]** Figure 1 展示两种表示的来源。先看两个预训练模型怎样组成联合系统，再看 B 面板。

**[Slide 5 / 演示第 5 页 · 操作提示]** Play the Figure 1 video once, in the delivery language. Resume after 20 seconds.

按演讲语言播放一次 Figure 1 视频，20 秒后继续。

[English video](../media/devise-figure-1-en.mp4) · [中文视频](../media/devise-figure-1-zh.mp4)

**[Slide 5]** In panel A, the arrows mean parameter initialization. The visual softmax is removed, and a learned projection maps the 4,096-dimensional visual features into a label space with 500 or 1,000 dimensions. Panel B is a t-SNE view of text-label embeddings. These dots are labels, not test images, and their plotted distances are not prediction scores.

**[演示第 5 页]** A 面板的箭头表示参数初始化。视觉 softmax 被移除，学习得到的投影将 4,096 维视觉特征映射到 500 或 1,000 维标签空间。B 面板是文本标签嵌入的 t-SNE 图；这些点是标签，不是测试图像，图中距离也不是预测分数。

**[Slide 5]** The word vectors are normalized and kept fixed. The projection is learned first; the visual network is fine-tuned later. So the semantic reference space stays fixed while images learn to align with it. The next question is how that alignment is trained.

**[演示第 5 页]** 词向量经过归一化并保持固定。先学习投影，再微调视觉网络。也就是说，语义参照空间固定，图像学习与它对齐。接下来要看怎样训练这种对齐。

依据 / Source: Original Figure 1 and §3.1–3.3, p.3

## 演示第 6 页 / Slide 6 · 不仅靠近正确标签，还要排在错误标签之前

个人累计 07:40-09:20

**[Slide 6]** The ranking loss asks the correct label to score above a competing label by a margin. Read the hinge term as: margin, minus the correct score, plus the competing score. If the correct label is already far enough ahead, the loss is zero.

**[演示第 6 页]** 排序损失要求正确标签的得分至少比竞争标签高出一个间隔。铰链项可以读成：间隔减去正确分数，再加上竞争分数。如果正确标签领先得足够多，损失就是零。

**[Slide 6]** For example, with a margin of 0.1, a correct score of 0.6 and a competing score of 0.55, the loss is 0.05. The correct label leads, but not by enough. In practice, training samples competing labels and stops at the first margin violation, rather than checking every label on every update.

**[演示第 6 页]** 例如，间隔为 0.1，正确分数为 0.6，竞争分数为 0.55，损失就是 0.05。正确标签虽然领先，但还不够。实际训练通过采样寻找竞争标签，在首个违反间隔的标签处停止，而不是每次更新都检查全部标签。

依据 / Source: Frome et al. (2013), p.4

## 演示第 7 页 / Slide 7 · 训练时哪些参数会更新？

个人累计 09:20-10:35

**[Slide 7]** Training happens in stages. First, the visual classifier and skip-gram model are pretrained separately. Then we freeze both representations and learn the projection matrix, M. Finally, the visual network is fine-tuned while the text vectors stay fixed.

**[演示第 7 页]** 训练分阶段进行。首先分别预训练视觉分类器与 Skip-gram 模型；接着固定两种表示，学习投影矩阵 M；最后微调视觉网络，文本向量始终保持固定。

**[Slide 7]** The paper reports a further one-to-three percentage-point gain from visual fine-tuning. It also uses stochastic gradient descent with Adagrad. For our explanation, the main point is which parameters change at each stage. Let’s make one update concrete with a small example.

**[演示第 7 页]** 论文报告视觉微调进一步带来一到三个百分点的提升，并采用带 Adagrad 的随机梯度下降。这里重点是分清每个阶段更新哪些参数。下面用一个小例子具体看一次更新。

依据 / Source: Frome et al. (2013), p.4

## 演示第 8 页 / Slide 8 · 逐步检查一次排序更新

个人累计 10:35-12:35

**[Slide 8]** This is a two-dimensional teaching example. The image feature and label vectors are fixed; only the projection changes. The correct label starts below its competitor, so the margin is not met. After an update, the correct-label score gap increases.

**[演示第 8 页]** 这是一个二维教学示例。图像特征与标签向量固定，只改变投影。初始时正确标签落后于竞争标签，间隔尚未满足；更新之后，正确标签的领先幅度增大。

**[Slide 8 / 演示第 8 页 · 操作提示]** Use the default example. Advance once, then play the remaining steps. Keep the demonstration within 45 seconds, including the following explanation.

使用默认示例，先前进一步，再播放剩余步骤。演示连同下面的讲解共限 45 秒。

**[Slide 8]** Notice the connection between the update and the loss: once the margin is satisfied, this pair produces no further learning signal. This demonstrates one ranking constraint, not full ImageNet training. Next, we’ll keep the model fixed and change something else: the candidate list.

**[演示第 8 页]** 注意更新与损失的关系：满足间隔后，这个标签对就不再产生学习信号。它演示的是一条排序约束，不是完整的 ImageNet 训练。接下来固定模型，改变另一个因素：候选列表。

依据 / Source: Teaching derivation from Eq.1, p.4; computed toy, not a reported experiment

## 演示第 9 页 / Slide 9 · 候选词表会改变答案

个人累计 12:35-14:30

**[Slide 9]** With unseen labels alone, the unseen shark label wins in this example. Add a nearby seen shark label, and that familiar label can take first place. We have changed the available answers, not retrained the model.

**[演示第 9 页]** 在这个例子里，只允许未见标签时，未见的鲨鱼标签获胜；加入一个相近的已见鲨鱼标签后，第一名可能改变。我们改变的是可选答案，没有重新训练模型。

**[Slide 9 / 演示第 9 页 · 操作提示]** Toggle seen candidates once. Keep the image/query unchanged. Allow at most 20 seconds for the demonstration and explanation.

只切换一次已见候选，保持图像或查询不变；演示和讲解共限 20 秒。

**[Slide 9]** DeViSE-0 and DeViSE+1K therefore describe different candidate sets for the same trained model; both test unseen-class images. With unit-length labels and a fixed nonzero query, dot product and cosine give the same ranking, though their values need not match.

**[演示第 9 页]** 因此，DeViSE-0 与 DeViSE+1K 表示同一个模型使用不同候选集合，两者都测试未见类别图像。标签为单位长度、查询固定且非零时，点积与余弦的排序一致，但数值不一定相同。

**[Slide 9]** That covers how DeViSE makes predictions. I’ll now hand over to my co-presenter to examine the evidence and the conditions behind those results.

**[演示第 9 页]** 以上就是 DeViSE 怎样做出预测。下面交给我的搭档，继续分析实验证据，以及这些结果成立的条件。

依据 / Source: Frome et al. (2013), p.6

演示第 20 页 / Slide 20：共用参考资料，无需逐项朗读，问答另计。 Sources and Q&A follow the timed talk.


## DeViSE · 讲者 B / Speaker B

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


