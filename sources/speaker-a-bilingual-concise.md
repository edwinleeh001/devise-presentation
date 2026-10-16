# DeViSE · 讲者 A / Speaker A

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
