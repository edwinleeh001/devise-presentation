# DeViSE — COMP6710 · Li Hu

30-minute independent presentation + 10-minute Q&A. The English run of show targets 28 minutes, including three 20-second videos, audience checks, demonstrations and changeovers, with 2 minutes of contingency inside the 30-minute limit. Timing is estimated at 110 spoken words per minute; rehearse the delivery. Stage cues and recorded narration are not extra presenter speech. Speaker notes switch independently between Chinese and English.

Primary evidence: Frome et al., NIPS 2013, pp.1–9, plus official supplement pp.1–3. AI-assisted organization, translation and implementation. Toy computations are not an ImageNet reproduction.

## Delivery and time control

Target: **28:00**, with a **2:00 contingency** inside the **30:00 hard limit**. Separate Q&A starts after the timed talk.

- Planning pace: 110 spoken words per minute; 2,398 words including all audience-check wording.
- Videos: overview, Figure 1 and Figure 2, played once each: **60 seconds total**. Recorded narration is already inside those 60 seconds and is not counted again as presenter speech.
- Activities and audience wait time: 176 seconds, including the 45-second ranking demo and 20-second candidate toggle.
- Pauses and changeovers: 76 seconds, plus the slack within the rounded chapter windows.
- This is a planning estimate, not a measured live delivery. Rehearse against the cumulative deadlines below. Cap audience responses; do not wait indefinitely. Do not read stage directions, table headings or recorded narration aloud.
- If behind, skip the optional slide-rule, extra demo presets and additional audience replies. Do not replay videos. If you reach 28:00 before closing, go straight to the three takeaways and stop by 30:00.

| Chapter | Window | Video | Activity |
|---|---|---:|---:|
| 1. Can a model name what it has never seen? | 00:00–01:05 | 0s | 5s |
| 2. Zero images is not zero information | 01:05–02:20 | 0s | 5s |
| 3. The missing link between images and words | 02:20–03:35 | 0s | 5s |
| 4. Two pretrained models. One semantic interface. | 03:35–05:15 | 20s | 5s |
| 5. Where the semantic structure comes from | 05:15–07:30 | 20s | 8s |
| 6. Learn an ordering, not just a destination | 07:30–09:10 | 0s | 10s |
| 7. What changes during training? | 09:10–10:25 | 0s | 5s |
| 8. Inspect one ranking update | 10:25–12:25 | 0s | 45s |
| 9. The candidate vocabulary changes the answer | 12:25–13:50 | 0s | 20s |
| 10. Read the protocol before the headline result | 13:50–15:05 | 0s | 5s |
| 11. Exact labels and reasonable mistakes | 15:05–16:25 | 0s | 8s |
| 12. Comparable accuracy, different error structure | 16:25–17:50 | 0s | 8s |
| 13. A larger label universe is a harder test | 17:50–20:10 | 20s | 10s |
| 14. Semantic quality has a boundary | 20:10–21:15 | 0s | 5s |
| 15. Candidate sets can reverse a comparison | 21:15–22:25 | 0s | 5s |
| 16. What the evidence does not establish | 22:25–24:20 | 0s | 12s |
| 17. Connect to ProtoNet without conflating the tasks | 24:20–25:30 | 0s | 5s |
| 18. An extensible label vocabulary | 25:30–26:30 | 0s | 5s |
| 19. Three claims to take away | 26:30–28:00 | 0s | 5s |

**28:00–30:00: contingency only.** Reference slide and Q&A are outside the scripted run of show.

## 1. Can a model name what it has never seen? / 模型能认出从未见过的类别吗？ · 1 min

DeViSE transfers semantic knowledge from text into visual recognition.

### English speaking script

**Run of show: 00:00–01:05.** 5 seconds for activity; 4 seconds for pauses/changeover.

Hello everyone. Today I’ll discuss DeViSE: connecting visual recognition with meaning learned from language.

Let me start with a question. Suppose a classifier has learned to recognize dogs, but its output layer has no label for a shark. Could it ever call an image a shark? Recognizing a new photograph is one thing; recognizing a new category is another.

**Brief audience check:** Could a fixed softmax layer predict a label that is absent from its outputs?

DeViSE tries to bridge that gap using text. To understand how, we first need to be clear about what “unseen” means.

### 中文演讲稿

先区分“新图片”和“新类别”。普通分类器能识别另一张狗的照片，因为训练类别中有狗；但它的输出层没有的新标签，无法直接输出。DeViSE 想知道，能否让文本知识为新类别提供表示。这是 Area 2 的迁移与零样本学习问题。模型并不是凭空获得知识：它看过相关类别的图片，也通过文本接触过新类别名称。整场展示都要保留这个区分。

**互动问题:** 如果输出层没有“鲨鱼”，固定 softmax 能预测它吗？

Source: Frome et al. (2013), p.1

## 2. Zero images is not zero information / 没有训练图片，不等于没有信息 · 1.5 min

Seen and unseen refer to visual training categories, not to the language vocabulary.

### English speaking script

**Run of show: 01:05–02:20.** 5 seconds for activity; 4 seconds for pauses/changeover.

In this paper, an unseen class has no labeled training images available to the visual model. That does not mean the system knows nothing about it. Its name can still appear in the language model’s text.

For example, the visual model may see some shark species, while text supplies a vector for another. The aim is to transfer useful structure across that gap.

There are also two separate sets to keep track of: the images being tested, and the labels allowed as answers. Adding familiar labels to the answer list does not change the test images.

**Brief audience check:** What information is still available for an unseen class?

With that setting in mind, what was missing from the earlier approaches?

### 中文演讲稿

假设训练类别中有虎鲨、牛鲨，但测试类别的图片没有用于训练。语言模型仍可能有该类别的词向量，视觉网络则把图片投影到同一个语义坐标系。这与 ProtoNet 不同：ProtoNet 通常拿到每个新类的少量标注支持图像，求出均值原型；DeViSE 使用文本提供的类别表示。还要区分测试图片集合和候选标签集合：允许预测已见标签，不等于把已见类图片混入零样本测试集。

**互动问题:** 未见类别仍然有哪些可用信息？

Source: Frome et al. (2013), p.2

## 3. The missing link between images and words / 连接图像与词语的研究缺口 · 1.5 min

A label is more informative than an arbitrary output index.

### English speaking script

**Run of show: 02:20–03:35.** 5 seconds for activity; 4 seconds for pauses/changeover.

The building blocks were already there: convolutional networks could learn useful visual features, and language models could place related words near one another. The challenge was to connect them in a way that worked across a much larger vocabulary.

That is the paper’s contribution: strong pretrained visual features, text-derived label representations, and a ranking objective, brought together at ImageNet scale. The authors train on a thousand visual classes and investigate transfer to roughly twenty thousand additional labels.

Several design choices changed together, so we should judge the full method rather than attribute every improvement to scale.

**Brief audience check:** What does a semantic label representation add that a larger softmax does not?

Let’s now follow the information through the model.

### 中文演讲稿

这篇论文并不是分别发明了词向量、卷积网络或零样本学习。其贡献是结合预训练视觉特征、从无标注文本学习的语义空间以及排序目标，并扩大到 ImageNet 规模。论文讨论的 Socher 系统涉及 8 个已见类和 2 个未见类；DeViSE 考察 1,000 个已见类以及约两万个未见标签。这是作者对研究缺口的定位，不能据此把提升完全归因于规模，因为网络、文本表示和损失函数也变了。

**互动问题:** 语义标签解决了哪一个“只扩大 softmax”难以解决的问题？

Source: Frome et al. (2013), p.2

## 4. Two pretrained models. One semantic interface. / 两个预训练模型，一个语义接口 · 2 min

Replace the visual softmax head with a learned linear projection into the text space.

### English speaking script

**Run of show: 03:35–05:15.** 20 seconds of video included. 5 seconds for activity; 4 seconds for pauses/changeover.

**Before playback — say:**

Here’s the idea in twenty seconds. Watch how the image moves from visual features into a space shared with label meanings. We’ll then return to the authors’ original diagram to examine the details.

**Playback cue — DeViSE overview · English · 20 seconds:**

Play the English overview once. Let its narration finish before speaking again.

[Play the overview English video (20 seconds)](../media/devise-20s-en.mp4)

[English subtitles](../media/devise-20s-en.srt)

**Video narration — recorded, do not read over it:**

Can a model recognize classes it's never trained on? DeViSE learns word embeddings and visual features. Then it maps images into a shared space, so the correct labels score higher. It can even predict unseen classes, if their word embeddings are available.

**After playback — say:**

The key move is to replace a fixed list of output classes with a comparison between an image vector and candidate label vectors. Text supplies the label representations; training images teach the visual mapping. A new label can enter that comparison if its embedding is available. That gives us a route to zero-shot recognition, although it does not guarantee a correct prediction.

**Brief audience check:** Which component connects the visual features to the label space?

**Transition to Figure 1 — say:**

That was the overview. Now let’s use the original Figure 1 to see where the two representations come from and what is actually learned.

### 中文演讲稿

先用原文 Figure 1 解释信息流，再讲损失。左边是视觉识别预训练网络，右边从文本学习词向量，中间去掉视觉 softmax，学习从视觉特征到语言空间的变换。这个投影是跨模态的桥梁，并不执行 ProtoNet 的支持样本均值运算。词向量给出语义空间中的目标位置，训练图片教会投影如何靠近合适的目标。t-SNE 图只展示语义邻域，不是分类器真正使用的低维坐标。

**互动问题:** 哪个组件连接视觉表示和语言表示？

Source: Frome et al. (2013), p.3

## 5. Where the semantic structure comes from / 语义结构从哪里来 · 2.5 min

Read the original Figure 1: pretrained visual and language models meet through a learned transformation.

![Original paper Figure 1 — Frome et al., NIPS 2013](../media/originals/devise-figure-1.png)

[Open original paper page 3](./devise-nips2013.pdf#page=3)

### English speaking script

**Run of show: 05:15–07:30.** 20 seconds of video included. 8 seconds for activity; 4 seconds for pauses/changeover.

**Before playback — say:**

Figure 1 has two panels. In this short clip, follow the two pretrained models into the joint system, then look at the colored neighborhoods in panel B.

**Playback cue — Figure 1 · English · 20 seconds:**

Play the English Figure 1 video once; resume after it finishes.

[Play Figure 1 English video (20 seconds)](../media/devise-figure-1-en.mp4)

[English subtitles](../media/devise-figure-1-en.srt)

**Video narration — recorded, do not read over it:**

How does DeViSE connect vision and language? It combines a pretrained visual network with fixed word embeddings. A learned projection aligns images with label vectors. Panel B shows semantic neighborhoods among labels, not image predictions.

**After playback — say:**

Panel A shows the architecture. The arrows into the middle indicate parameter initialization. The visual softmax is removed, and a learned projection maps visual features into the label space. The visual features have four thousand and ninety-six dimensions; the paper uses label embeddings with five hundred or a thousand dimensions.

Panel B shows something different: text-derived label embeddings, visualized with t-SNE. Related labels form neighborhoods before image training aligns the two modalities. These dots are labels, not test-image predictions. Their two-dimensional distances are not classification scores.

The word vectors are normalized and kept fixed. The projection is learned first, and the visual network is fine-tuned later. Let’s check those roles before moving on.

**Brief audience check:** In panel B, are the dots labels or test images? Are the plotted distances prediction scores?

**Transition to the ranking loss — say:**

So we have our reference space. How do we teach an image to prefer the correct label over a competing one? That is the job of the ranking loss.

### 中文演讲稿

**播放前 · 演讲者说：**

我们已经看过整体流程。现在回到作者的原始 Figure 1。接下来这段 20 秒视频里，请留意视觉网络和词向量怎样接入联合模型，再想一想 B 图里的彩色点代表什么。

**播放提示 · Figure 1 · 中文 · 20 秒：**

播放本章的中文视频，让录制旁白完整播放；视频结束后再继续讲解。

[播放 Figure 1 中文视频（20 秒）](../media/devise-figure-1-zh.mp4)

[下载中文字幕](../media/devise-figure-1-zh.srt)

**视频旁白 · 已录制，请勿重复朗读：**

DeViSE 如何连接视觉与语言？ 它结合预训练视觉网络，与固定的词向量。 学习一个投影，让图像对齐标签向量。 B 图展示标签之间的语义邻域，不是图像预测结果。

**播放后 · 演讲者说：**

好，这张图给了我们两条线索：A 图解释模型架构，B 图展示文本提供的语义结构。指向联合模型的箭头表示参数初始化。视觉 softmax 被移除，词向量保持固定；先学习投影，再微调视觉网络。视觉特征有 4,096 维，标签嵌入有 500 或 1,000 维。

注意，B 图中的点是标签词向量。二维距离用于可视化，不是预测分数；真正的排序发生在高维嵌入空间。继续之前，我们先确认一下这个区别。

**互动问题:** 哪个面板展示模型架构，哪个展示语义邻域？二维距离是预测分数吗？

**衔接排序损失 · 演讲者说：**

到这里，我们知道了标签向量从哪里来。下一个问题是：图像怎样学会把正确标签排在竞争标签前面？这就引出了接下来的排序损失。

Source: Original Figure 1 and §3.1–3.3, p.3

## 6. Learn an ordering, not just a destination / 不仅靠近正确标签，还要排在错误标签之前 · 2 min

The correct label should outscore a wrong label by a margin.

### English speaking script

**Run of show: 07:30–09:10.** 10 seconds for activity; 4 seconds for pauses/changeover.

The objective is about an ordering. We want the correct label to score higher than a competing label by at least a small margin.

Read the hinge term as: the margin, minus the correct score, plus the competing score. If the correct label is already far enough ahead, the loss is zero. Otherwise, that pair produces a learning signal.

For our quick calculation, the margin is point one, the correct score is point six, and the competing score is point five five. The loss is point zero five. The correct label leads, but not by enough.

Equation one is written as a sum. In practice, the algorithm samples competing labels and stops at the first margin violation, rather than checking every label on every update.

**Brief audience check:** Why is the loss positive even though the correct label already scores higher?

That explains the objective. Next, let’s identify which parts of the model it changes.

### 中文演讲稿

逐项解释：要求的间隔，减去正确标签分数，加上竞争标签分数。若正确标签已经领先至少一个间隔，这项损失为零；否则产生学习信号。公式写成求和，但实际算法随机检查负标签，在第一个违反间隔的标签处截断，因此不能说每次都遍历所有类别更新。作者称 L2 目标的准确率约为排序模型的一半，但正文没有完整对照表，应将它标为作者报告的观察，而不是普遍定理。

可选补充：语义滑尺装置用三个指定的单位标签向量说明点积。改变查询方向，观察分数游标和读数。这里的分数是可复算教学值；原始 Figure 2 并未列出数值分数。

**互动问题:** m=0.1、sᵧ=0.60、sⱼ=0.55 时，损失是多少？

Source: Frome et al. (2013), p.4

## 7. What changes during training? / 训练时哪些参数会更新？ · 1.5 min

The visual backbone is frozen first, then fine-tuned.

### English speaking script

**Run of show: 09:10–10:25.** 5 seconds for activity; 4 seconds for pauses/changeover.

Pretraining gives the model a starting point; it does not mean that every component stays frozen.

The authors first train the projection matrix, M. They then fine-tune the visual network while keeping the language embeddings fixed. The paper uses asynchronous stochastic gradient descent with Adagrad learning rates.

Our teaching example is deliberately smaller. We freeze a two-dimensional visual feature and update only M using plain gradient descent. That lets us inspect the effect of one ranking constraint without pretending to reproduce the full ImageNet training run.

**Brief audience check:** Does the visual network stay frozen throughout training?

With that simplification clear, let’s walk through one update and see whether the score gap changes as expected.

### 中文演讲稿

先区分初始化和联合训练。两个预训练模型提供良好起点，不意味着整个系统永久冻结。首先只训练 M，后来微调视觉层；语言表示仍作为固定的参照空间。原论文使用异步随机梯度下降和 Adagrad。课堂例子则刻意固定二维视觉特征，用普通梯度下降更新 M，以便核对排序损失的更新。它不复现原文的分布式优化或 ImageNet 训练。

**互动问题:** “DeViSE 只训练一个线性层”是完整描述吗？

Source: Frome et al. (2013), p.4

## 8. Inspect one ranking update / 逐步检查一次排序更新 · 2.5 min

Predict the effect, change the margin or learning rate, and inspect the exact arithmetic.

### English speaking script

**Run of show: 10:25–12:25.** 45 seconds for activity; 4 seconds for pauses/changeover.

Here is our small, computed example. The image feature and label vectors are fixed; only the projection changes. Before I advance it, predict what will happen to the gap between the correct and competing scores.

[Demo cue — 45 seconds, including the audience response. Use margin 0.1 and learning rate 0.1; advance once, inspect the gap, rewind, then try learning rate zero. Skip extra presets and the optional slide-rule.]

After that active update, the gap increases and the loss falls. Rewinding restores the same state. Setting the learning rate to zero leaves the model unchanged, which confirms that the update drives the result.

This is one constraint in a toy problem. It does not show that every real training example improves on every step. And these similarity scores are not probabilities.

**Brief audience check:** After an active update, what should happen to the correct-label score gap?

We’ve now seen how a score changes during learning. What happens if the scores stay fixed, but the available answers change?

### 中文演讲稿

先让同学预测：一次激活的排序更新会不会提高正确标签分数？从间隔 0.1、学习率 0.1 开始，前进一步，读出分数差和损失；再后退，证明状态可复现。把学习率设为零，观察不学习的边界情况；增大间隔，原来满足要求的标签对可能再次产生损失。这是孤立的单样本问题，不证明真实多类神经网络的所有样本损失或测试准确率都会单调改善。最后强调点积分数不等于概率。

**互动问题:** 预测：激活约束的一次更新后，正确标签的领先幅度会增大吗？

Source: Teaching derivation from Eq.1, p.4; computed toy, not a reported experiment

## 9. The candidate vocabulary changes the answer / 候选词表会改变答案 · 1.5 min

The same projected image can yield different top predictions under different candidate sets.

### English speaking script

**Run of show: 12:25–13:50.** 20 seconds for activity; 4 seconds for pauses/changeover.

Let’s keep the image vector fixed and change only the candidate list. With unseen labels alone, the unseen shark label wins. Allow a nearby seen shark label to compete, and that familiar label can take first place.

[Demo cue — 20 seconds, including the audience response. Toggle seen candidates once; keep the query angle unchanged.]

Nothing was retrained. DeViSE zero and DeViSE plus one thousand describe different candidate sets for the same trained model. Both settings still test unseen-class images.

With unit-length labels and a fixed nonzero query, dot product and cosine rankings agree. Their numeric values and fixed-margin losses need not.

**Brief audience check:** When I add seen labels to the candidates, have the model weights changed?

This sensitivity to the answer list is why the evaluation protocol comes next.

### 中文演讲稿

保持查询角度不变，切换候选集合。只允许未见标签时，一个未见鲨鱼标签获胜；加入已见标签后，方向更近的已见鲨鱼可能排第一。这里没有重新训练，所以两种 DeViSE 不是分别训练的模型。原文测试图片仍来自未见类。对于固定非零查询、单位长度标签向量，点积与余弦排序一致，但数值和固定间隔损失并不相同。界面上的数字是相似度分数，不是校准概率。

**互动问题:** 加入已见标签时，模型权重改变了吗？

Source: Frome et al. (2013), p.6

## 10. Read the protocol before the headline result / 先读实验协议，再读结果 · 1.5 min

Separate seen-class recognition, zero-shot label expansion, and the 800/200 comparison.

### English speaking script

**Run of show: 13:50–15:05.** 5 seconds for activity; 4 seconds for pauses/changeover.

Before looking at the headline numbers, let’s check how they were obtained.

For the main seen-class evaluation, the authors split the original ImageNet validation set: five thousand images for model selection, and forty-five thousand for reporting results. This is not the hidden competition test set. The supplement also specifies a single center crop and the same evaluation procedure for the softmax baseline.

The zero-shot experiments reuse the five-hundred-dimensional model without further tuning. Table four, however, uses a different dataset year and class split. We cannot treat its percentages as directly comparable with Table two.

**Brief audience check:** Why do Tables two and four answer different experimental questions?

Once the protocol is clear, the next question is what counts as a successful prediction.

### 中文演讲稿

补充材料说明：主要已见类测试集来自原 ImageNet 验证集，并不是竞赛隐藏测试集。5 千图像用于模型选择，4.5 万图像用于报告结果；零样本实验直接复用 500 维模型，不另行调参。Table 4 改变了数据年份和类别划分，因此不能把它和 Table 2 的百分比当作同一任务直接比较。测试时使用单次中心裁剪，softmax 基线也采用相同评估方式。

**互动问题:** 为什么不能直接比较 Table 4 和 Table 2 的百分比？

Source: Supplement §A.1, p.1; main paper pp.6–8

## 11. Exact labels and reasonable mistakes / 正确标签与合理错误是两种指标 · 1.5 min

Flat hit@k and hierarchical precision@k answer different questions.

### English speaking script

**Run of show: 15:05–16:25.** 8 seconds for activity; 4 seconds for pauses/changeover.

Suppose the true label is one bird species, but the model predicts a related bird. Exact-label accuracy still counts that as wrong. A hierarchical metric can give credit for being semantically close.

The acceptable set expands around the true label in the taxonomy until it contains at least k labels. Since a whole neighborhood is added at once, the set may contain more than k.

So hierarchical precision answers a different question from exact-label accuracy. It also depends on the taxonomy. At k equals one, only the exact label is acceptable, so the metrics agree once we express them in the same units.

**Brief audience check:** Does a higher hierarchical score necessarily mean more exact species predictions?

Let’s use that distinction to read the seen-class results.

### 中文演讲稿

用具体例子说明：把一种鸟认成另一种相关鸟，在 flat hit@1 下仍然错误；层级指标可以给语义邻居一定奖励。补充材料的规则是围绕真实标签按层级距离扩展，直到集合大小至少达到 k。由于每次加入整个半径上的节点，集合可能远大于 k，所以它不等于普通分类准确率，数值也依赖标签层级。k=1 时集合只含真实标签，两者在百分比与小数转换后一致。

**互动问题:** 层级分数更高，是否必然意味着精确物种预测更多？

Source: Main §4, pp.4–5; Supplement §A.3, pp.2–3

## 12. Comparable accuracy, different error structure / 准确率接近，错误结构不同 · 1.5 min

On seen classes, DeViSE is not uniformly better than softmax.

### English speaking script

**Run of show: 16:25–17:50.** 8 seconds for activity; 4 seconds for pauses/changeover.

On the familiar thousand classes, the result is quite balanced. At top one, softmax scores fifty-five point six percent, compared with fifty-four point nine for the thousand-dimensional DeViSE model. At top five, they are almost tied: seventy-eight point five versus seventy-eight point four percent.

Some hierarchical scores improve, which suggests a difference in the structure of the errors, rather than a clear win on exact-label accuracy.

The random-embedding baseline helps us ask whether the text-derived geometry is useful. It keeps the general architecture but removes the meaningful organization of the labels. That is useful evidence, though it does not control every possible training difference.

**Brief audience check:** Which baseline tests the value of meaningful label geometry?

So much for familiar classes. The more distinctive test is whether the model can name classes without their training images.

### 中文演讲稿

不要把细致的结果压缩成“全面胜出”。top-1 下 softmax 更高；top-5 下 1,000 维 DeViSE 几乎持平，而某些层级指标有所改善。随机嵌入基线保留模型形式、移除文本语义组织，有助于检验语义几何的作用，但并不控制全部训练差异，因此应说它支持语义结构有帮助，而不是绝对因果证明。500 维和 1,000 维也并非在每个指标上随维度单调改善。

**互动问题:** 哪个基线针对“词语语义结构是否有用”这一问题？

Source: Table 1, p.5

## 13. A larger label universe is a harder test / 候选标签越多，测试越困难 · 2.5 min

Use the original Figure 2 to inspect successes and failures, then read Table 2 under its stated candidate set.

![Original paper Figure 2 — Frome et al., NIPS 2013](../media/originals/devise-figure-2.png)

[Open original paper page 6](./devise-nips2013.pdf#page=6)

### English speaking script

**Run of show: 17:50–20:10.** 20 seconds of video included. 10 seconds for activity; 4 seconds for pauses/changeover.

**Before playback — say:**

Figure 2 gives us selected examples from that zero-shot test. Watch for a correct prediction, a plausible miss, and a case where the baseline does better.

**Playback cue — Figure 2 · English · 20 seconds:**

Play the English Figure 2 video once; resume after it finishes.

[Play Figure 2 English video (20 seconds)](../media/devise-figure-2-en.mp4)

[English subtitles](../media/devise-figure-2-en.srt)

**Video narration — recorded, do not read over it:**

Can DeViSE recognize unseen classes? Here, the correct lens label ranks fourth. But both models miss the salad bar. For the spacecraft, softmax gives more relevant suggestions. They show strengths and limits, not overall accuracy.

**After playback — say:**

The lens label ranks fourth. Both models miss the exact salad-bar label, and the authors judge softmax’s spacecraft suggestions more nearly correct. These examples show useful transfer, along with its limits.

Both systems were trained on ImageNet’s thousand classes. DeViSE searches the larger label vocabulary; softmax can only output its training labels. In example D, a plausible pineapple-fruit prediction is different from the specific pineapple-plant synset. Let’s check what counts as an exact match.

**Brief audience check:** Which example challenges the claim that DeViSE always wins? Can a plausible label still be an exact-label miss?

**Transition to Table 2 and the next chapter — say:**

Selected examples cannot tell us overall accuracy. Table two can. For two-hop hit at five, unseen-only candidates give eighteen point one percent. Adding a thousand seen candidates lowers that to seven point nine. Same model, different candidate set. With twenty thousand eight hundred and forty-one unseen labels, hit at one is point eight percent, and hit at five is two point five. Next, let’s ask how reasonable the remaining errors are.

### 中文演讲稿

**播放前 · 演讲者说：**

我们已经看过模型怎样给标签排序。现在看看作者的真实案例。接下来这段 20 秒视频里，请留意一次准确命中、一次合理但未命中的预测，以及一个基线更好的反例。

**播放提示 · Figure 2 · 中文 · 20 秒：**

播放本章的中文视频，让录制旁白完整播放；视频结束后再继续讲解。

[播放 Figure 2 中文视频（20 秒）](../media/devise-figure-2-zh.mp4)

[下载中文字幕](../media/devise-figure-2-zh.srt)

**视频旁白 · 已录制，请勿重复朗读：**

模型能识别未见类别吗？ 镜头的正确标签，排第四。 沙拉吧，两个模型都没命中。 而飞船，softmax 的预测更相关。 案例展示优点与局限，不代表总体准确率。

**播放后 · 演讲者说：**

刚才最后一个例子值得记住。镜头的准确标签排第 4，但沙拉吧，两个模型都没命中。到了航天器，作者认为 softmax 更接近正确答案。这说明迁移有价值，也有边界，不能保证 DeViSE 每次都赢。

两者都在 ImageNet 1K 训练。DeViSE+1K 搜索 2011 年的 21K 标签集；softmax 只能输出 1K 训练标签。原图给排名，没有数值置信度。D 图还要区分：合理的水果预测，不等于准确的菠萝植株同义词集。我们先确认什么算未命中。

**互动问题:** 哪个例子反驳“DeViSE 总是更好”？合理标签仍可能是准确标签未命中吗？

**衔接 Table 2 与下一章 · 演讲者说：**

接下来，从精选案例转到 Table 2。2-hop 的 hit@5，只考虑未见候选时是 18.1%；加入 1,000 个已见候选后，降到 7.9%。模型相同，候选集合不同。全部 20,841 个未见标签下，hit@1 是 0.8%，hit@5 是 2.5%。每个数字都要带上候选集合与 k。下一章，我们再用层级精度讨论：错误标签是否仍可能在语义上合理。

Source: Original Figure 2 and Table 2, p.6; §4.2 reading, p.7

## 14. Semantic quality has a boundary / 语义改善也有边界 · 1 min

A hierarchical gain is useful evidence, but it is not universal superiority.

### English speaking script

**Run of show: 20:10–21:15.** 5 seconds for activity; 4 seconds for pauses/changeover.

The hierarchical results also depend on the setting. In the two-hop task at k equals two, softmax has the higher score. With the full label set at k equals twenty, DeViSE plus one thousand does better.

That supports a conditional claim about semantic generalization, rather than a claim that DeViSE wins everywhere. WordNet has a specific role here: it is used to evaluate semantic closeness, not to train these label embeddings.

**Brief audience check:** Where is WordNet used here: training the embeddings, or evaluating their predictions?

Table four gives us another example of why the comparison setting matters.

### 中文演讲稿

先指出反例：最容易的 2-hop、k=2 设置中，softmax 的层级分数更高；更大词表、k=20 时，DeViSE+1K 更高。这支持有条件的语义泛化结论，而不是普遍领先。还要明确层级的角色：DeViSE 不依赖人工层级来训练标签嵌入，但评估使用它定义哪些错误可以得到语义奖励。

**互动问题:** WordNet 层级用于嵌入训练、评估，还是两者？

Source: Table 3, p.7; Supplement §A.3

## 15. Candidate sets can reverse a comparison / 候选集合可以改变方法排名 · 1 min

Table 4 evaluates a separate 800/200 split on ImageNet 2010.

### English speaking script

**Run of show: 21:15–22:25.** 5 seconds for activity; 4 seconds for pauses/changeover.

Table four uses a separate split: eight hundred seen classes and two hundred unseen classes. With only the two hundred unseen labels as candidates, DeViSE trails Mensink’s method. With all thousand labels competing, the ordering reverses.

One setting requires an unseen answer; the other makes seen and unseen labels compete. We also need the paper’s caveat: Rohrbach’s result uses a different unseen-class set.

**Brief audience check:** Why can the ranking of two methods reverse when seen labels are allowed to compete?

Across these tables, the lesson is consistent. The candidate set is part of the task, not a minor reporting detail. That brings us to the model’s broader limits.

### 中文演讲稿

用这张表强化实验分析：只在 200 类中选时，DeViSE 低于 Mensink；加入已见类后，它保留了更多性能，方法排名反转。评估协议决定科学问题：事先知道答案一定是未见类，与必须在熟悉和陌生类别之间选择，是不同任务。同时保留论文提醒：Rohrbach 的未见类别集合不同。

**互动问题:** 为什么一种方法在 200 候选下领先，在 1,000 候选下却落后？

Source: Table 4, p.7; split description pp.7–8

## 16. What the evidence does not establish / 证据还没有证明什么 · 2 min

Zero-shot capability is conditional on useful semantic representations and a specified label vocabulary.

### English speaking script

**Run of show: 22:25–24:20.** 12 seconds for activity; 4 seconds for pauses/changeover.

We can now answer the opening question, with some qualifications. DeViSE can rank a label without labeled training images from that class, provided a suitable semantic representation is available.

It still needs a candidate vocabulary. It is not freely generating a description of the image. Meaning can also be ambiguous: “crane” may refer to a bird or a machine, while the language model provides one vector for that word.

There is also a gap between a plausible result and reliable recognition. Accuracy is low on the largest label set, and seen classes can attract predictions away from unseen ones.

One useful follow-up experiment would hold the test images and candidate count fixed while changing how similar the seen candidates are to the true unseen labels. That could help separate semantic competition from simply having more candidates. It would be a new experiment, not a result established here.

**Brief audience check:** What would you hold fixed to distinguish semantic competition from candidate-set size?

These limits also help us compare DeViSE with a method we already know: ProtoNet.

### 中文演讲稿

回到开场问题，并给出条件：只要有有效标签嵌入，模型可以对没有训练图片的新类排序。但它仍使用给定候选词表，并不是生成式图片描述器。补充材料明确讨论多义词：crane 可以是鸟或机械，语言模型却只有一个词向量。后续可以检验词义区分表示以及已见／未见分数校准。这些是建议实验，不是原论文或教学示例已经证明的结果。

**互动问题:** 如何设计实验，把已见类偏置与候选集合大小的影响分开？

Source: Main §4.2–5, pp.6–8; Supplement §A.2

## 17. Connect to ProtoNet without conflating the tasks / 与 ProtoNet 建立联系，但不混淆任务 · 1 min

Both use an embedding space; the source of each class representation is different.

### English speaking script

**Run of show: 24:20–25:30.** 5 seconds for activity; 4 seconds for pauses/changeover.

Both DeViSE and ProtoNet compare an image representation with class representations. The key difference is where those class representations come from.

ProtoNet builds a prototype by averaging embeddings of a few labeled support images for a new class. DeViSE takes the class representation from a language model instead. It therefore uses a different resource when those support images are unavailable.

The connection is conceptual. Their accuracies are not directly comparable because the datasets and supervision differ.

**Brief audience check:** Without support images, where does each method obtain its class representation?

The shared idea is a flexible representation of a class. What could that flexibility offer in practice?

### 中文演讲稿

利用你已有的 ProtoNet 基础：两者都比较图像表示和类别表示。关键问题是类别表示从哪里来。ProtoNet 在测试时从少量标注支持图像构建原型；DeViSE 从预训练语言模型获得表示，因此不需要这些支持图像。不能拿两篇论文的准确率直接判断谁更好，因为数据集、候选集合和监督假设不同。联系是概念上的，实验协议仍须分开。

**互动问题:** 如果没有支持图像，ProtoNet 的原型从哪里来？

Source: DeViSE §3.3; Snell et al. (2017), §2

## 18. An extensible label vocabulary / 可以扩展的标签词表 · 1 min

A useful application idea is to change the labels without retraining a separate output unit for each one.

### English speaking script

**Run of show: 25:30–26:30.** 5 seconds for activity; 4 seconds for pauses/changeover.

A shared embedding model could support different label vocabularies. One application might use broad categories such as car and pedestrian; another might need more specific vehicle names. Suitable text embeddings could let the same visual mapping rank either set.

That flexibility is attractive, but adding a word does not guarantee recognition. A practical system would still need domain-specific evaluation, a defined candidate set, and a way to handle ambiguity or genuinely unknown inputs.

**Brief audience check:** Would adding a new word guarantee reliable recognition?

These are possibilities, not demonstrated deployments. Let me close with three takeaways.

### 中文演讲稿

将应用描述为有条件的可能性，而不是已部署事实。一个系统可能使用“汽车、行人”等粗标签，另一个可能使用具体车型；如果有合适词向量，共享模型可对不同词表排序。类别经常变化时，这很有吸引力。但大候选集绝对准确率较低，不能假设它直接满足生产可靠性。实际应用还需要领域评估、未知或模糊标签处理以及明确的候选集合。

**互动问题:** 加入任意新词，是否就保证可靠识别？

Source: §5, p.8: proposed applications, not deployment evidence

## 19. Three claims to take away / 带走三个结论 · 1 min

Text supplies class structure; ranking aligns modalities; protocol determines the meaning of success.

### English speaking script

**Run of show: 26:30–28:00.** 5 seconds for activity; 4 seconds for pauses/changeover.

First, language gives visual recognition a source of class structure beyond the image training labels.

Second, DeViSE learns to connect those representations through a ranking objective: the correct label should score above its competitors.

Third, the evaluation setting is essential to interpreting the result. In the two-hop example, changing only the candidates takes hit at five from eighteen point one to seven point nine percent. The semantic bridge is useful, but its success is conditional.

So the answer is yes: meaningful label representations can enable recognition of some visually unseen classes. Success still depends on the candidate vocabulary.

**Brief audience check:** What condition needs to accompany the claim that DeViSE recognizes unseen classes?

Thank you. I’m happy to take questions.

### 中文演讲稿

最后用一句话重述：文本学习的语义能否让视觉分类器超出图像训练标签？在论文假设下可以，但性能有明确限制。结尾同时给出贡献、一个精确结果和一个局限。例如 2-hop 未见候选 hit@5 为 18.1%，加入已见标签降至 7.9%。这个对比连接了方法与证据，说明仔细阅读评估协议和理解模型图同样重要。邀请同学围绕损失、候选集合或语义指标提问。

**互动问题:** 用一句话解释 DeViSE，并带上一个限制条件。

Source: Frome et al. (2013), p.8

## 20. Sources, evidence and reproducibility / 来源、证据与可复算说明 · 0 min

Reported results, teaching computations, and proposed extensions are kept distinct.

### English speaking script

**Reference only — outside the timed talk.**

[Reference slide — outside the timed talk. Do not read this slide aloud; use it during the separate Q&A.]

The original paper, official supplement, reading guide, and video assets are available in the downloads. Reported results are attributed to the paper; the interactive calculations are teaching examples. No original ImageNet training run is reproduced here.

**Audience prompt:** Which evidence comes from the paper, and which from the teaching examples?

### 中文演讲稿

可以打开本地原文核验依据。可下载讲稿和阅读指南与网页共享内容来源。数值示例是确定性的合成计算；没有原论文训练过程或预训练 DeViSE 检查点。30 分钟安排包含提问和交互，请自行排练，不要假设逐字朗读一定恰好 30 分钟。

**互动问题:** 哪些结论来自论文，哪些只是教学示例？

Source: Frome et al. (2013), p.1

## Q&A / 答辩准备

### 1. Why is this zero-shot if text includes the class name? / 文本出现过类名，为什么仍是零样本？

Zero-shot is defined relative to visual training examples for those classes. Semantic side information is explicitly available.

零样本相对于这些类别的视觉训练样本定义；语义辅助信息是明确允许的。

Source: §4.2, p.6

### 2. Are word embeddings updated in the reported joint training? / 原文联合训练会更新词向量吗？

They are held fixed. A footnote discusses possible joint language training as an extension, not the reported procedure.

原文固定词向量。脚注讨论同时训练语言模型的可能性，不是已报告流程。

Source: §3.3, p.4, footnote 5

### 3. Is the visual backbone always frozen? / 视觉骨干一直冻结吗？

No. M is trained first; the visual network is fine-tuned later.

不是。先训练 M，再微调视觉网络。

Source: §3.3, p.4

### 4. Why ranking loss rather than L2? / 为什么用排序损失而不是 L2？

Prediction is based on label ordering. The hinge explicitly penalizes wrong labels that score too close to or above the correct one. The paper reports poorer L2 results, not a universal guarantee.

预测依赖排序。Hinge 明确惩罚过于接近或超过正确标签的错误标签。论文报告 L2 较差，但不构成普遍保证。

Source: §3.3, p.4

### 5. Are dot product and cosine identical? / 点积和余弦完全相同吗？

For unit label vectors and a fixed nonzero query, they induce the same ranking. Their values differ by query norm; fixed-margin losses need not be identical.

单位标签向量与固定非零查询下，排序相同；数值相差查询模长，固定间隔损失不一定相同。

Source: §3.3 + algebraic deduction

### 6. Is the displayed similarity a probability? / 相似度分数是概率吗？

No. The toy and paper objective use dot-product scores. No probability calibration is established.

不是。教学例子和论文目标使用点积分数，没有建立概率校准。

Source: Eq.1, p.4

### 7. Are DeViSE-0 and DeViSE+1K different trained models? / DeViSE-0 和 +1K 是不同训练模型吗？

No. They are the same trained model evaluated with different candidate label sets.

不是。是同一个训练模型，候选标签集合不同。

Source: Table 2 caption, p.6

### 8. What exactly does 18.1% mean? / 18.1% 究竟指什么？

Flat hit@5 for DeViSE-0 on the 1,589-label 2-hop unseen candidate set. It is neither top-1 nor the full-21K result.

DeViSE-0 在 1,589 个 2-hop 未见候选上的 flat hit@5；不是 top-1，也不是全 21K 结果。

Source: Table 2, p.6

### 9. Is WordNet absent from the whole study? / 整个研究都没有使用 WordNet 吗？

No. Learned text embeddings do not require the curated hierarchy as their training target, but evaluation uses the ImageNet/WordNet hierarchy.

不是。文本嵌入训练不以人工层级为目标，但评估使用 ImageNet/WordNet 层级。

Source: §2; Supplement §A.3

### 10. Does DeViSE beat softmax on every metric? / DeViSE 每个指标都超过 softmax 吗？

No. Softmax is better at seen-class top-1 and at some hierarchical settings. Always specify metric and candidate set.

不是。已见类 top-1 和一些层级设置中 softmax 更好。必须同时说明指标和候选集合。

Source: Tables 1 and 3

### 11. What does the random embedding baseline control? / 随机嵌入基线控制什么？

It removes learned semantic label structure while retaining the embedding-based model form. It supports, but does not perfectly isolate, the value of text semantics.

它移除学习到的标签语义结构、保留嵌入模型形式，支持语义有效，但不完美隔离全部混杂因素。

Source: §4 and Table 1

### 12. How is this different from ProtoNet? / 它与 ProtoNet 有何不同？

DeViSE gets a class vector from text; ProtoNet normally computes it from labeled support images. The resource assumptions and objectives differ.

DeViSE 从文本获得类别向量；ProtoNet 通常从标注支持图像求均值。资源假设和目标不同。

Source: DeViSE §3; Snell et al. §2

### 13. What happens with ambiguous labels? / 多义标签怎么办？

A single term vector may represent multiple ImageNet synsets. The supplement expands terms to synsets, removes duplicates, and truncates the ranked list. This does not resolve word senses in the embedding itself.

同一个词向量可能对应多个 synset。补充材料将词展开为 synset、去重并截取排名，但这并未在嵌入中真正区分词义。

Source: Supplement §A.2

### 14. Can we compare Table 2 and Table 4 directly? / 能直接比较 Table 2 和 Table 4 吗？

No. Table 4 uses ImageNet 2010 with an 800/200 class split; Table 2 uses the 2012-trained model and 2011 unseen labels.

不能。Table 4 是 ImageNet 2010 的 800/200 类划分；Table 2 使用 2012 训练模型和 2011 未见类。

Source: Supplement §A.1

### 15. What would you improve? / 你会如何改进？

Test sense-aware embeddings, candidate-set calibration, and controlled domain shifts. These are proposed follow-ups, not measured results here.

可检验词义区分嵌入、候选集合校准和受控域偏移。这是建议研究，不是已测结果。

Source: Presenter proposals

