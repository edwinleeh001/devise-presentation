# DeViSE — COMP6710 · Li Hu

30-minute independent presentation + 10-minute Q&A. Both language versions target 28 minutes, including three 20-second videos, audience checks, demonstrations and changeovers, with 2 minutes of contingency inside the 30-minute limit. English timing is estimated at 110 spoken words per minute; Chinese timing uses about 200 characters per minute with extra time for foreign terms and digits. Both use the same chapter deadlines; rehearse the delivery. Stage cues and recorded narration are not extra presenter speech. Speaker notes switch independently between Chinese and English.

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

## 讲解与时间控制

目标 **28:00**，另留 **2:00 缓冲**，总计不超过 **30:00**。问答环节在限时演讲之后。

- 与最新版英文稿逐章对齐：论点、例子、数字、限定条件、互动问题和转场保持一致。
- 以每分钟约 200 字估算，并为外文术语和数字加算读音时间。正文和互动问题包含 3,829 个汉字；舞台提示和录制旁白不作为额外演讲文字计时。
- 总览、Figure 1 和 Figure 2 各播放一次，每段 20 秒，合计 **60 秒**。视频播放时不重复朗读旁白。
- 演示及观众等待预留 176 秒，含 45 秒排序演示、20 秒候选切换；停顿和换页另计 76 秒。
- 这是时间规划估算，不是现场实测。按下面的累计节点排练，观众回答保持简短，不无限等待。舞台提示、表头和来源不逐项朗读。
- 若进度落后，跳过可选语义滑尺、额外演示预设和追加回答；不重播视频。若到 28:00 还未收束，直接进入三个结论，并在 30:00 前结束。

| 章节 | 累计时间 | 视频 | 互动或演示 |
|---|---|---:|---:|
| 1. 模型能认出从未见过的类别吗？ | 00:00–01:05 | 0 秒 | 5 秒 |
| 2. 没有训练图片，不等于没有信息 | 01:05–02:20 | 0 秒 | 5 秒 |
| 3. 连接图像与词语的研究缺口 | 02:20–03:35 | 0 秒 | 5 秒 |
| 4. 两个预训练模型，一个语义接口 | 03:35–05:15 | 20 秒 | 5 秒 |
| 5. 语义结构从哪里来 | 05:15–07:30 | 20 秒 | 8 秒 |
| 6. 不仅靠近正确标签，还要排在错误标签之前 | 07:30–09:10 | 0 秒 | 10 秒 |
| 7. 训练时哪些参数会更新？ | 09:10–10:25 | 0 秒 | 5 秒 |
| 8. 逐步检查一次排序更新 | 10:25–12:25 | 0 秒 | 45 秒 |
| 9. 候选词表会改变答案 | 12:25–13:50 | 0 秒 | 20 秒 |
| 10. 先读实验协议，再读结果 | 13:50–15:05 | 0 秒 | 5 秒 |
| 11. 正确标签与合理错误是两种指标 | 15:05–16:25 | 0 秒 | 8 秒 |
| 12. 准确率接近，错误结构不同 | 16:25–17:50 | 0 秒 | 8 秒 |
| 13. 候选标签越多，测试越困难 | 17:50–20:10 | 20 秒 | 10 秒 |
| 14. 语义改善也有边界 | 20:10–21:15 | 0 秒 | 5 秒 |
| 15. 候选集合可以改变方法排名 | 21:15–22:25 | 0 秒 | 5 秒 |
| 16. 证据还没有证明什么 | 22:25–24:20 | 0 秒 | 12 秒 |
| 17. 与 ProtoNet 建立联系，但不混淆任务 | 24:20–25:30 | 0 秒 | 5 秒 |
| 18. 可以扩展的标签词表 | 25:30–26:30 | 0 秒 | 5 秒 |
| 19. 带走三个结论 | 26:30–28:00 | 0 秒 | 5 秒 |

**28:00–30:00 仅作缓冲。** 参考页和问答不计入此流程。

## 1. Can a model name what it has never seen? / 模型能认出从未见过的类别吗？ · 1 min

DeViSE transfers semantic knowledge from text into visual recognition.

### English speaking script

**Run of show: 00:00–01:05.** 5 seconds for activity; 4 seconds for pauses/changeover.

Hello everyone. Today I’ll discuss DeViSE: connecting visual recognition with meaning learned from language.

Let me start with a question. Suppose a classifier has learned to recognize dogs, but its output layer has no label for a shark. Could it ever call an image a shark? Recognizing a new photograph is one thing; recognizing a new category is another.

**Brief audience check:** Could a fixed softmax layer predict a label that is absent from its outputs?

DeViSE tries to bridge that gap using text. To understand how, we first need to be clear about what “unseen” means.

### 中文演讲稿

**流程时间：00:00–01:05。** 互动或演示预留 5 秒；停顿与换页预留 4 秒。

大家好，今天我们讨论 DeViSE：怎样把视觉识别和语言中学到的含义连接起来。

先想一个问题。假设一个分类器学会了认狗，但输出层里根本没有“鲨鱼”这个标签，它还能把一张图片叫作鲨鱼吗？识别一张新照片，和识别一个新类别，是两回事。

**互动问题:** 固定的 softmax 输出层，能预测一个不在输出列表里的标签吗？

DeViSE 尝试借助文本跨过这道鸿沟。要理解它怎么做，我们先得说清楚：“未见”究竟指什么。

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

**流程时间：01:05–02:20。** 互动或演示预留 5 秒；停顿与换页预留 4 秒。

在这篇论文里，未见类别是指视觉模型没有该类的有标注训练图像。这不等于系统对它一无所知；类别名称仍然可能出现在语言模型使用的文本里。

例如，视觉模型见过某些鲨鱼种类，而文本为另一种鲨鱼提供了词向量。目标就是把有用的结构迁移过去。

这里还要分清两个集合：接受测试的图像，和允许作为答案的标签。把已见标签加入候选答案，并不会改变测试图像。

**互动问题:** 对于未见类别，系统还可以获得什么信息？

明确这个设置之后，我们再看，早期方法还缺少哪一环。

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

**流程时间：02:20–03:35。** 互动或演示预留 5 秒；停顿与换页预留 4 秒。

当时，主要的构件已经存在：卷积网络能学习有用的视觉特征，语言模型也能把含义相关的词放在相近的位置。难点是把两者连接起来，并让这种连接适用于大得多的标签词表。

这就是论文的贡献：把预训练视觉特征、从文本得到的标签表示和排序目标结合起来，做到 ImageNet 的规模。作者用一千个视觉类别训练，再研究向大约两万个额外标签迁移。

多项设计同时发生了变化，所以应评价整套方法，不能把所有改善都归因于规模。

**互动问题:** 语义标签表示带来了什么，是单纯扩大 softmax 不能提供的？

接下来，我们沿着信息流看一遍模型。

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

**流程时间：03:35–05:15。** 已含 20 秒视频。互动或演示预留 5 秒；停顿与换页预留 4 秒。

**播放前 · 演讲者说：**

先用二十秒抓住整体思路。请留意图像怎样从视觉特征进入一个与标签含义共享的空间。然后，我们再回到作者的原图，检查具体细节。

**播放提示 · DeViSE 总览 · 中文 · 20 秒：**

播放一次中文总览视频。等录制旁白完整结束，再继续讲解。

[播放总览中文视频（20 秒）](../media/devise-20s-zh.mp4)

[下载中文字幕](../media/devise-20s-zh.srt)

**视频旁白 · 已录制，请勿重复朗读：**

没有斑马训练图，也能认出斑马吗？先用文本学词向量，用图片训练视觉网络。再把图像投影到语义空间，让正确标签得分更高。预测时比较标签得分，也能选择未见类别。前提是，已有它的词向量。

**播放后 · 演讲者说：**

关键的一步，是把固定输出类别的分类，改成图像向量与候选标签向量之间的比较。文本提供标签表示，训练图像教会视觉映射。只要有对应嵌入，新标签就能加入比较。这为零样本识别提供了一条路径，但不保证预测一定正确。

**互动问题:** 哪个部分把视觉特征连接到标签空间？

**衔接 Figure 1 · 演讲者说：**

刚才是整体思路。现在看原始 Figure 1，弄清两种表示从哪里来，以及模型到底学习了什么。

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

**流程时间：05:15–07:30。** 已含 20 秒视频。互动或演示预留 8 秒；停顿与换页预留 4 秒。

**播放前 · 演讲者说：**

Figure 1 有两个面板。接下来这段短片里，请跟着两个预训练模型进入联合系统，再看看 B 图中不同颜色的语义邻域。

**播放提示 · Figure 1 · 中文 · 20 秒：**

播放一次 Figure 1 中文视频，结束后再继续讲解。

[播放 Figure 1 中文视频（20 秒）](../media/devise-figure-1-zh.mp4)

[下载中文字幕](../media/devise-figure-1-zh.srt)

**视频旁白 · 已录制，请勿重复朗读：**

DeViSE 如何连接视觉与语言？ 它结合预训练视觉网络，与固定的词向量。 学习一个投影，让图像对齐标签向量。 B 图展示标签之间的语义邻域，不是图像预测结果。

**播放后 · 演讲者说：**

A 图展示架构。指向中间的箭头表示参数初始化。视觉 softmax 被移除，学习到的投影把视觉特征映射到标签空间。视觉特征有四千零九十六维；论文使用五百维或一千维的标签嵌入。

B 图展示的是另一件事：用 t-SNE 可视化从文本学到的标签嵌入。在图像训练对齐两种模态之前，相关标签就已经形成邻域。这些点是标签，不是测试图像的预测；二维距离也不是分类分数。

词向量归一化后保持固定。先学习投影，再微调视觉网络。继续之前，我们先确认各部分的角色。

**互动问题:** B 图中的点是标签还是测试图像？图上的距离是预测分数吗？

**衔接排序损失 · 演讲者说：**

现在有了参照空间。怎样让图像更偏向正确标签，而不是竞争标签？这就是排序损失要解决的问题。

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

**流程时间：07:30–09:10。** 互动或演示预留 10 秒；停顿与换页预留 4 秒。

这个目标关心的是先后顺序。我们希望正确标签的分数，比竞争标签至少高出一个小的间隔。

把铰链损失这一项读出来，就是：要求的间隔，减去正确标签分数，再加上竞争标签分数。如果正确标签已经充分领先，损失就是零；否则，这一对标签会产生学习信号。

做个简单计算：间隔是零点一，正确分数是零点六，竞争分数是零点五五，损失就是零点零五。正确标签虽然领先，但领先得还不够。

公式一写成求和；实际算法会抽取竞争标签，在第一个违反间隔的标签处停止，而不是每次更新都检查所有标签。

**互动问题:** 正确标签已经得分更高，为什么损失仍然大于零？

目标已经清楚了。接下来看看，它会改变模型的哪些部分。

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

**流程时间：09:10–10:25。** 互动或演示预留 5 秒；停顿与换页预留 4 秒。

预训练给模型一个起点，并不意味着所有部分都保持冻结。

作者先训练投影矩阵 M，再微调视觉网络，同时固定语言嵌入。论文采用异步随机梯度下降，并使用 Adagrad 学习率。

我们的教学示例刻意缩小了问题：固定二维视觉特征，只用普通梯度下降更新 M。这样能单独检查一个排序约束的影响，而不是假装复现完整的 ImageNet 训练。

**互动问题:** 视觉网络在整个训练过程中都保持冻结吗？

明确这个简化之后，我们走一遍更新，看看分数差是否按预期改变。

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

**流程时间：10:25–12:25。** 互动或演示预留 45 秒；停顿与换页预留 4 秒。

现在看这个可计算的小示例。图像特征和标签向量都固定，只有投影发生变化。开始之前，先预测一下：正确分数与竞争分数之间的差距会怎样变化？

[演示提示 · 共 45 秒，含观众回答。间隔和学习率都设为 0.1；前进一步，查看分数差，再倒退，最后试一次零学习率。跳过额外预设和可选语义滑尺。]

这次有效更新后，分数差增大，损失下降。倒退可以恢复相同状态。把学习率设为零，模型就不变，说明结果确实由更新驱动。

这只是教学问题里的一个约束，不能证明真实训练中的每个样本每一步都会改善。这里的相似度分数也不是概率。

**互动问题:** 一次有效更新后，正确标签与竞争标签的分数差应该怎样变化？

我们看过学习怎样改变分数了。那么，如果分数不变，只改变可选答案，会发生什么？

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

**流程时间：12:25–13:50。** 互动或演示预留 20 秒；停顿与换页预留 4 秒。

保持图像向量不变，只改变候选列表。只有未见标签时，未见的鲨鱼标签获胜；让一个相近的已见鲨鱼标签参加竞争，第一名就可能换成这个熟悉标签。

[演示提示 · 共 20 秒，含观众回答。只切换一次“加入已见候选”，保持查询角度不变。]

这里没有重新训练。DeViSE-0 和 DeViSE+1K 表示同一个训练模型使用不同候选集合；两种设置都测试未见类别的图像。

当标签向量为单位长度、查询向量固定且非零时，点积与余弦的排序一致，但数值和固定间隔损失不一定相同。

**互动问题:** 加入已见候选时，模型权重改变了吗？

答案列表会影响结果，所以接下来必须看清评估协议。

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

**流程时间：13:50–15:05。** 互动或演示预留 5 秒；停顿与换页预留 4 秒。

看主要数字前，先确认它们怎么得来。

在主要的已见类别评估中，作者划分了原始 ImageNet 验证集：五千张用于模型选择，四万五千张用于报告结果。这不是竞赛隐藏测试集。补充材料还说明，测试使用单个中心裁剪，softmax 基线采用相同评估流程。

零样本实验直接复用五百维模型，没有进一步调参。但 Table 4 改用了不同年份的数据集和类别划分，不能把它的百分比与 Table 2 当作同一个任务直接比较。

**互动问题:** 为什么 Table 2 和 Table 4 回答的是不同的实验问题？

协议清楚之后，下一个问题是：怎样才算预测成功？

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

**流程时间：15:05–16:25。** 互动或演示预留 8 秒；停顿与换页预留 4 秒。

假设真实标签是一种鸟，模型却预测了相关的另一种鸟。按准确标签评估，这仍然是错的；层级指标则可以给语义相近的答案一定认可。

可接受集合会沿着分类层级，在真实标签周围逐步扩展，直到至少包含 k 个标签。由于每次加入整个邻域，集合大小可能超过 k。

所以，层级精度与准确标签正确率回答的是不同问题，而且依赖分类层级。当 k 等于一时，只有准确标签可接受；换成相同单位后，两种指标一致。

**互动问题:** 层级分数更高，是否一定意味着准确物种预测更多？

带着这个区别，我们来看已见类别的结果。

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

**流程时间：16:25–17:50。** 互动或演示预留 8 秒；停顿与换页预留 4 秒。

熟悉的一千个类别上，结果很接近。Top-1 中，softmax 是百分之五十五点六，一千维 DeViSE 是百分之五十四点九。Top-5 几乎打平：百分之七十八点五，对百分之七十八点四。

部分层级分数有所提高，说明错误的结构可能不同，而不是准确标签正确率有明确的全面优势。

随机嵌入基线帮助我们检查：文本带来的标签几何结构有没有用。它保留大体架构，却去掉标签间有意义的组织。这是有用证据，但没有控制所有可能的训练差异。

**互动问题:** 哪个基线检验有意义的标签几何结构是否有用？

已见类别先看到这里。更有特色的测试是：没有某类的训练图像，模型还能叫出它的名字吗？

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

**流程时间：17:50–20:10。** 已含 20 秒视频。互动或演示预留 10 秒；停顿与换页预留 4 秒。

**播放前 · 演讲者说：**

Figure 2 是作者选取的零样本案例。请留意一次准确预测、一次合理但未命中的预测，以及一个基线更好的例子。

**播放提示 · Figure 2 · 中文 · 20 秒：**

播放一次 Figure 2 中文视频，结束后再继续讲解。

[播放 Figure 2 中文视频（20 秒）](../media/devise-figure-2-zh.mp4)

[下载中文字幕](../media/devise-figure-2-zh.srt)

**视频旁白 · 已录制，请勿重复朗读：**

模型能识别未见类别吗？ 镜头的正确标签，排第四。 沙拉吧，两个模型都没命中。 而飞船，softmax 的预测更相关。 案例展示优点与局限，不代表总体准确率。

**播放后 · 演讲者说：**

镜头的准确标签排在第四。沙拉吧的准确标签两者都没命中；航天器的预测，作者认为 softmax 更接近正确答案。这说明迁移有用，也有局限。

两者都在 ImageNet 一千类上训练。DeViSE 搜索更大的标签词表，softmax 只能输出训练标签。D 图里，合理的菠萝水果预测，不等于特定的菠萝植株同义词集。先确认什么算准确匹配。

**互动问题:** 哪个例子挑战了“DeViSE 总能赢”的说法？合理标签仍可能是准确标签未命中吗？

**衔接 Table 2 与下一章 · 演讲者说：**

精选案例不能给出总体准确率，要看 Table 2。2-hop 的 hit@5，只考虑未见候选时是百分之十八点一；加入一千个已见候选，降到百分之七点九。模型相同，候选集合不同。全部两万零八百四十一个未见标签下，hit@1 是百分之零点八，hit@5 是百分之二点五。接下来，我们再看剩下的错误有多合理。

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

**流程时间：20:10–21:15。** 互动或演示预留 5 秒；停顿与换页预留 4 秒。

层级结果同样取决于设置。在 2-hop、k 等于二的任务中，softmax 分数更高；完整标签集、k 等于二十时，DeViSE+1K 更好。

这支持有条件的语义泛化结论，而不是 DeViSE 处处获胜。WordNet 在这里有明确角色：用于评估语义接近程度，不用于训练这些标签嵌入。

**互动问题:** WordNet 在这里用于训练嵌入，还是评估预测？

Table 4 又提供了一个例子，说明比较设置为什么重要。

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

**流程时间：21:15–22:25。** 互动或演示预留 5 秒；停顿与换页预留 4 秒。

Table 4 采用独立划分：八百个已见类别、两百个未见类别。只让两百个未见标签作为候选时，DeViSE 落后于 Mensink 的方法；一千个标签都参加竞争时，排名反过来了。

一种设置要求答案必须是未见类；另一种让已见与未见标签竞争。还要保留论文的说明：Rohrbach 使用了不同的未见类别集合。

**互动问题:** 为什么允许已见标签竞争，会让两种方法的排名反过来？

综合这些表格，结论是一致的：候选集合是任务的一部分，不是报告时无关紧要的小细节。接下来讨论模型更广泛的局限。

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

**流程时间：22:25–24:20。** 互动或演示预留 12 秒；停顿与换页预留 4 秒。

现在可以回答开场的问题了，但要带上条件：只要有合适的语义表示，DeViSE 就能给没有该类有标注训练图像的标签排序。

它仍然需要候选词表，并不是自由生成图像描述。词义也可能有歧义：crane 可以指鸟，也可以指起重机，但语言模型只为这个词提供一个向量。

合理的结果和可靠的识别之间，还有距离。最大标签集上的准确率偏低，已见类别也可能把预测从未见类别吸引过去。

一个有用的后续实验，是固定测试图像和候选数量，只改变已见候选与真实未见标签的语义相似程度。这样有助于区分语义竞争与单纯候选增多的影响。这是新的实验设想，不是本文已经建立的结果。

**互动问题:** 要区分语义竞争与候选集合大小的影响，你会固定哪些条件？

这些边界也帮助我们把 DeViSE 与熟悉的另一种方法联系起来：ProtoNet。

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

**流程时间：24:20–25:30。** 互动或演示预留 5 秒；停顿与换页预留 4 秒。

DeViSE 和 ProtoNet 都比较图像表示与类别表示。关键区别在于，类别表示从哪里来。

ProtoNet 对新类的少量有标注支持图像求嵌入均值，得到原型；DeViSE 则从语言模型取得类别表示。所以，在没有这些支持图像时，它使用的是另一种信息资源。

这是一种概念上的联系。数据集和监督条件不同，论文里的准确率不能直接比较。

**互动问题:** 没有支持图像时，两种方法分别从哪里取得类别表示？

两者共享的思路，是灵活地表示一个类别。那么，这种灵活性在实际应用中能带来什么？

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

**流程时间：25:30–26:30。** 互动或演示预留 5 秒；停顿与换页预留 4 秒。

共享嵌入模型可以支持不同的标签词表。一个应用可能用汽车、行人等粗粒度标签；另一个可能需要更具体的车型名称。只要文本嵌入合适，同一视觉映射就能为任一词表排序。

这种灵活性很有吸引力，但加一个词，并不保证能识别它。实际系统还需要领域评估、明确的候选集合，以及处理歧义和真正未知输入的方法。

**互动问题:** 加入一个新词，就能保证可靠识别吗？

这些是可能性，不是已展示的部署。最后，用三个结论收束。

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

**流程时间：26:30–28:00。** 互动或演示预留 5 秒；停顿与换页预留 4 秒。

第一，语言为视觉识别提供了图像训练标签之外的类别结构。

第二，DeViSE 用排序目标连接两种表示：正确标签的分数应高于竞争标签。

第三，理解结果必须看评估设置。在 2-hop 例子里，只改变候选集合，hit@5 就从百分之十八点一变成百分之七点九。语义桥梁有用，但成功有条件。

所以，答案是可以：有意义的标签表示，能帮助识别部分视觉上未见的类别；成功仍取决于候选词表。

**互动问题:** 声称 DeViSE 能识别未见类别时，必须补上什么条件？

谢谢大家，欢迎提问。

Source: Frome et al. (2013), p.8

## 20. Sources, evidence and reproducibility / 来源、证据与可复算说明 · 0 min

Reported results, teaching computations, and proposed extensions are kept distinct.

### English speaking script

**Reference only — outside the timed talk.**

[Reference slide — outside the timed talk. Do not read this slide aloud; use it during the separate Q&A.]

The original paper, official supplement, reading guide, and video assets are available in the downloads. Reported results are attributed to the paper; the interactive calculations are teaching examples. No original ImageNet training run is reproduced here.

**Audience prompt:** Which evidence comes from the paper, and which from the teaching examples?

### 中文演讲稿

**参考页，不计入限时演讲。**

[参考页 · 不计入限时演讲。不逐项朗读；留待单独的问答环节使用。]

下载区提供原文、官方补充材料、阅读指南和视频素材。报告结果注明论文来源；互动计算是教学示例。这里没有复现原始 ImageNet 训练。

**互动问题:** 哪些证据来自论文，哪些来自教学示例？

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

