# DeViSE — COMP6710 · Li Hu

30-minute independent presentation + 10-minute Q&A. The plan includes interaction and inspection; rehearse timing. English website with independently switchable Chinese notes.

Primary evidence: Frome et al., NIPS 2013, pp.1–9, plus official supplement pp.1–3. AI-assisted organization, translation and implementation. Toy computations are not an ImageNet reproduction.

## 1. Can a model name what it has never seen? / 模型能认出从未见过的类别吗？ · 1 min

DeViSE transfers semantic knowledge from text into visual recognition.

Start with the difference between recognizing a new photograph and recognizing a new category. A conventional classifier can recognize another photograph of a dog because dog was a training class. It cannot emit a new label that its output layer does not contain. DeViSE asks whether knowledge learned from text can supply a representation of that new label. This is an Area 2 transfer and zero-shot problem. The claim is not that a network creates knowledge from nothing: it has seen training images from related categories and text containing the new category names. Keep this distinction in view throughout the talk.

先区分“新图片”和“新类别”。普通分类器能识别另一张狗的照片，因为训练类别中有狗；但它的输出层没有的新标签，无法直接输出。DeViSE 想知道，能否让文本知识为新类别提供表示。这是 Area 2 的迁移与零样本学习问题。模型并不是凭空获得知识：它看过相关类别的图片，也通过文本接触过新类别名称。整场展示都要保留这个区分。

**Audience prompt / 互动：** If “shark” is absent from the output layer, can a fixed softmax predict it? / 如果输出层没有“鲨鱼”，固定 softmax 能预测它吗？

Source: Frome et al. (2013), p.1

## 2. Zero images is not zero information / 没有训练图片，不等于没有信息 · 1.5 min

Seen and unseen refer to visual training categories, not to the language vocabulary.

Imagine training on tiger shark and bull shark, but testing on a related class whose training photographs were unavailable. The language model has a vector for the unseen label because it encountered that term in text. The visual model projects the image into the same semantic coordinate system. This is different from ProtoNet: ProtoNet normally receives a small labeled support set for each novel class and averages those image embeddings. DeViSE uses a label representation from text instead. Also separate the test image set from the candidate label set. Adding seen labels to the candidates does not add seen images to the zero-shot evaluation.

假设训练类别中有虎鲨、牛鲨，但测试类别的图片没有用于训练。语言模型仍可能有该类别的词向量，视觉网络则把图片投影到同一个语义坐标系。这与 ProtoNet 不同：ProtoNet 通常拿到每个新类的少量标注支持图像，求出均值原型；DeViSE 使用文本提供的类别表示。还要区分测试图片集合和候选标签集合：允许预测已见标签，不等于把已见类图片混入零样本测试集。

**Audience prompt / 互动：** What information is still available for an unseen class? / 未见类别仍然有哪些可用信息？

Source: Frome et al. (2013), p.2

## 3. The missing link between images and words / 连接图像与词语的研究缺口 · 1.5 min

A label is more informative than an arbitrary output index.

The paper does not invent word embeddings, convolutional networks, or zero-shot learning independently. Its contribution is to combine strong pretrained visual features, a semantic space learned from unannotated text, and a ranking objective at ImageNet scale. Explain the comparison precisely: the related Socher system discussed in the paper used eight seen and two unseen categories, whereas DeViSE investigates one thousand seen classes and roughly twenty thousand unseen labels. This is the authors’ positioning of the research gap, not proof that scale is the only cause of better performance. Architecture, language representations, and training objectives also changed.

这篇论文并不是分别发明了词向量、卷积网络或零样本学习。其贡献是结合预训练视觉特征、从无标注文本学习的语义空间以及排序目标，并扩大到 ImageNet 规模。论文讨论的 Socher 系统涉及 8 个已见类和 2 个未见类；DeViSE 考察 1,000 个已见类以及约两万个未见标签。这是作者对研究缺口的定位，不能据此把提升完全归因于规模，因为网络、文本表示和损失函数也变了。

**Audience prompt / 互动：** Which limitation is solved by semantic labels rather than a larger softmax? / 语义标签解决了哪一个“只扩大 softmax”难以解决的问题？

Source: Frome et al. (2013), p.2

## 4. Two pretrained models. One semantic interface. / 两个预训练模型，一个语义接口 · 2 min

Replace the visual softmax head with a learned linear projection into the text space.

Use Figure 1 to explain the information flow before showing the loss. The left network is pretrained for visual recognition. The right model learns word representations from text. The middle system removes the original visual softmax and learns a transformation from visual features to the language embedding space. This transformation is the bridge between modalities. It is not averaging support examples as ProtoNet does. The label vectors supply destinations in semantic space, and the training images teach the projection how to reach appropriate destinations. The t-SNE plot illustrates semantic neighborhoods; it is a visualization, not the actual coordinate system used for classification.

先用原文 Figure 1 解释信息流，再讲损失。左边是视觉识别预训练网络，右边从文本学习词向量，中间去掉视觉 softmax，学习从视觉特征到语言空间的变换。这个投影是跨模态的桥梁，并不执行 ProtoNet 的支持样本均值运算。词向量给出语义空间中的目标位置，训练图片教会投影如何靠近合适的目标。t-SNE 图只展示语义邻域，不是分类器真正使用的低维坐标。

**Audience prompt / 互动：** Which component connects the visual and language representations? / 哪个组件连接视觉表示和语言表示？

Source: Frome et al. (2013), p.3

## 5. Where the semantic structure comes from / 语义结构从哪里来 · 2 min

The text model learns label relations without visual examples for every label.

The semantic space is learned before the joint visual-semantic model. Skip-gram is trained using surrounding words, so labels that occur in related contexts can become neighbors. The paper uses single-word and multi-word terms, not only simple object names. For the joint model, the text vectors are normalized to length one. This matters: a dot-product ranking then depends on alignment with the projected image rather than arbitrary label-vector length. However, semantic proximity is a statistical property of language. It does not guarantee that the objects look similar, nor that two senses of an ambiguous word can be separated. These observations prepare the later discussion of failure cases.

语义空间先于联合模型训练。Skip-gram 使用上下文，因此在相近语境出现的标签可能成为邻居。词表包含单词和多词短语，不只有简单物体名称。联合模型中的词向量被归一化为单位长度，使点积排序不受标签向量任意长度影响，而取决于与图像投影的对齐关系。但语言中的语义接近不保证视觉相似，也无法自动分离一个多义词的不同含义。这为后续局限讨论作铺垫。

**Audience prompt / 互动：** Would “crane” always have one unambiguous visual meaning? / “crane”一定只有一种明确的视觉含义吗？

Source: Frome et al. (2013), p.3

## 6. Learn an ordering, not just a destination / 不仅靠近正确标签，还要排在错误标签之前 · 2 min

The correct label should outscore a wrong label by a margin.

Read the three terms aloud: the required margin, minus the correct-label score, plus the competing-label score. If the correct score already exceeds the wrong score by the margin, this term is zero. Otherwise the model receives a learning signal. Equation 1 is written as a sum, but the practical algorithm samples negatives and stops at the first violation. Do not describe the implementation as summing every label on every update. The authors report that an L2 objective gave about half the ranking model’s accuracy, without a full result table in the main text. Present that as a reported observation, not a universal theorem about ranking losses.

逐项解释：要求的间隔，减去正确标签分数，加上竞争标签分数。若正确标签已经领先至少一个间隔，这项损失为零；否则产生学习信号。公式写成求和，但实际算法随机检查负标签，在第一个违反间隔的标签处截断，因此不能说每次都遍历所有类别更新。作者称 L2 目标的准确率约为排序模型的一半，但正文没有完整对照表，应将它标为作者报告的观察，而不是普遍定理。

**Audience prompt / 互动：** With m = 0.1, sᵧ = 0.60 and sⱼ = 0.55, what is the loss? / m=0.1、sᵧ=0.60、sⱼ=0.55 时，损失是多少？

Source: Frome et al. (2013), p.4

## 7. What changes during training? / 训练时哪些参数会更新？ · 1.5 min

The visual backbone is frozen first, then fine-tuned.

Separate initialization from joint training. The two pretrained models are useful starting points; they do not mean the entire system stays frozen. Initially only M is trained. Later the visual layers are fine-tuned while the language representation remains the reference space. The paper uses asynchronous stochastic gradient descent with Adagrad per-parameter learning rates. Our classroom example deliberately freezes a two-dimensional visual feature and uses plain gradient descent for M. It isolates the ranking update, so its steps are easier to verify. It does not reproduce the distributed optimization or the ImageNet training run.

先区分初始化和联合训练。两个预训练模型提供良好起点，不意味着整个系统永久冻结。首先只训练 M，后来微调视觉层；语言表示仍作为固定的参照空间。原论文使用异步随机梯度下降和 Adagrad。课堂例子则刻意固定二维视觉特征，用普通梯度下降更新 M，以便核对排序损失的更新。它不复现原文的分布式优化或 ImageNet 训练。

**Audience prompt / 互动：** Is “DeViSE only trains a linear layer” a complete description? / “DeViSE 只训练一个线性层”是完整描述吗？

Source: Frome et al. (2013), p.4

## 8. Inspect one ranking update / 逐步检查一次排序更新 · 3 min

Predict the effect, change the margin or learning rate, and inspect the exact arithmetic.

Ask the audience to predict whether a single active-pair update raises the correct score. Begin with margin 0.1 and learning rate 0.1, step once, and read the score gap and loss. Then rewind to prove that the displayed state is reproducible. Set the learning rate to zero to show a case with no learning. Next increase the margin: a pair that was satisfactory can become active again. In this isolated one-example problem, repeated updates can satisfy the constraint. That does not prove that all examples or held-out accuracy improve monotonically in a real multi-class neural network. End by distinguishing a dot-product score from a probability.

先让同学预测：一次激活的排序更新会不会提高正确标签分数？从间隔 0.1、学习率 0.1 开始，前进一步，读出分数差和损失；再后退，证明状态可复现。把学习率设为零，观察不学习的边界情况；增大间隔，原来满足要求的标签对可能再次产生损失。这是孤立的单样本问题，不证明真实多类神经网络的所有样本损失或测试准确率都会单调改善。最后强调点积分数不等于概率。

**Audience prompt / 互动：** Predict: after an active update, does the correct-label score gap rise? / 预测：激活约束的一次更新后，正确标签的领先幅度会增大吗？

Source: Teaching derivation from Eq.1, p.4; computed toy, not a reported experiment

## 9. The candidate vocabulary changes the answer / 候选词表会改变答案 · 1.5 min

The same projected image can yield different top predictions under different candidate sets.

Use the candidate-set toggle while keeping the query angle fixed. The unseen shark label wins when the candidates contain only unseen labels. A nearby seen shark label can win when it is allowed to compete. Nothing was retrained. This explains why the two DeViSE variants must not be described as separately trained systems. In the original evaluation the test photographs still belong to unseen classes. Dot product and cosine give the same ranking for a fixed nonzero query when all label vectors have unit length, but their numeric values and a fixed-margin training loss are not identical. The displayed numbers are similarity scores, not calibrated confidence.

保持查询角度不变，切换候选集合。只允许未见标签时，一个未见鲨鱼标签获胜；加入已见标签后，方向更近的已见鲨鱼可能排第一。这里没有重新训练，所以两种 DeViSE 不是分别训练的模型。原文测试图片仍来自未见类。对于固定非零查询、单位长度标签向量，点积与余弦排序一致，但数值和固定间隔损失并不相同。界面上的数字是相似度分数，不是校准概率。

**Audience prompt / 互动：** When seen labels are added, did the model weights change? / 加入已见标签时，模型权重改变了吗？

Source: Frome et al. (2013), p.6

## 10. Read the protocol before the headline result / 先读实验协议，再读结果 · 1.5 min

Separate seen-class recognition, zero-shot label expansion, and the 800/200 comparison.

The supplement is essential here. It clarifies that the main seen-class test set is held out from the original ImageNet validation set, rather than the hidden competition test set. The authors use five thousand images for model selection and report results on the remaining forty-five thousand. Their zero-shot experiments reuse the five-hundred-dimensional model without additional tuning. The comparison in Table 4 changes the dataset year and class split, so those percentages cannot be placed directly beside Table 2 as if they measured one task. At test time the authors use a single center crop, and compare their softmax baseline under the same evaluation procedure.

补充材料说明：主要已见类测试集来自原 ImageNet 验证集，并不是竞赛隐藏测试集。5 千图像用于模型选择，4.5 万图像用于报告结果；零样本实验直接复用 500 维模型，不另行调参。Table 4 改变了数据年份和类别划分，因此不能把它和 Table 2 的百分比当作同一任务直接比较。测试时使用单次中心裁剪，softmax 基线也采用相同评估方式。

**Audience prompt / 互动：** Why should Table 4 not be compared directly with Table 2? / 为什么不能直接比较 Table 4 和 Table 2 的百分比？

Source: Supplement §A.1, p.1; main paper pp.6–8

## 11. Exact labels and reasonable mistakes / 正确标签与合理错误是两种指标 · 1.5 min

Flat hit@k and hierarchical precision@k answer different questions.

Start with a concrete distinction: predicting a related bird instead of the exact bird species is still wrong for flat hit at one. A hierarchical measure can reward semantic neighbors. The supplement defines an acceptable set by expanding around the true label in the taxonomy until its size reaches at least k. Because an entire radius is added, that set can be much larger than k. Therefore hierarchical precision is not ordinary exact-label accuracy, and its magnitude depends on the taxonomy. At k equals one, the acceptable set contains only the exact label, so the two metrics agree after converting percentage to fraction.

用具体例子说明：把一种鸟认成另一种相关鸟，在 flat hit@1 下仍然错误；层级指标可以给语义邻居一定奖励。补充材料的规则是围绕真实标签按层级距离扩展，直到集合大小至少达到 k。由于每次加入整个半径上的节点，集合可能远大于 k，所以它不等于普通分类准确率，数值也依赖标签层级。k=1 时集合只含真实标签，两者在百分比与小数转换后一致。

**Audience prompt / 互动：** Does a higher hierarchical score necessarily mean more exact species predictions? / 层级分数更高，是否必然意味着精确物种预测更多？

Source: Main §4, pp.4–5; Supplement §A.3, pp.2–3

## 12. Comparable accuracy, different error structure / 准确率接近，错误结构不同 · 2 min

On seen classes, DeViSE is not uniformly better than softmax.

Read the table without turning a nuanced result into a victory slogan. At top one the softmax baseline is better. At top five the thousand-dimensional DeViSE model is almost tied, while some hierarchical scores improve. The random-embedding baseline helps isolate the value of meaningful label geometry: it retains the architecture but discards the text-derived organization. It does not control every possible training difference, so describe the evidence as support for semantic structure rather than a perfect causal proof. Also note that five-hundred and thousand-dimensional embeddings do not show a simple monotonic improvement on every metric. Larger is not automatically better.

不要把细致的结果压缩成“全面胜出”。top-1 下 softmax 更高；top-5 下 1,000 维 DeViSE 几乎持平，而某些层级指标有所改善。随机嵌入基线保留模型形式、移除文本语义组织，有助于检验语义几何的作用，但并不控制全部训练差异，因此应说它支持语义结构有帮助，而不是绝对因果证明。500 维和 1,000 维也并非在每个指标上随维度单调改善。

**Audience prompt / 互动：** Which baseline addresses whether learned word semantics are useful? / 哪个基线针对“词语语义结构是否有用”这一问题？

Source: Table 1, p.5

## 13. A larger label universe is a harder test / 候选标签越多，测试越困难 · 2 min

Read every zero-shot number together with its candidate set and k.

First select two-hop and k equals five. The drop from eighteen point one to seven point nine occurs when one thousand seen labels are added, with the trained model fixed. This is evidence of competition and seen-class bias. Then move to the full unseen label universe and keep k fixed. Accuracy drops again, but both candidate count and semantic distance change, so the table does not isolate one cause. Avoid saying the model achieves eighteen percent accuracy on every zero-shot problem: that value belongs to a specific top-five, two-hop, unseen-only protocol. The raw top-one accuracy on the hardest candidate set remains low.

先选择 2-hop、k=5。固定训练模型，仅加入 1,000 个已见标签，结果从 18.1% 降至 7.9%，体现了候选竞争和已见类偏置。再保持 k 不变，切换到全部未见标签，准确率继续下降，但此时类别数量和语义距离同时变化，无法孤立归因。不能说“模型的零样本准确率是 18%”：那是特定 2-hop、未见候选、top-5 协议下的数值。最困难集合上的 top-1 绝对准确率仍然较低。

**Audience prompt / 互动：** Is 18.1% a top-1 result over all 20,841 unseen labels? / 18.1% 是 20,841 个未见标签上的 top-1 结果吗？

Source: Table 2, p.6; interpretation §4.2, p.7

## 14. Semantic quality has a boundary / 语义改善也有边界 · 1 min

A hierarchical gain is useful evidence, but it is not universal superiority.

Point out a counterexample before making the positive claim. On the easiest two-hop task at k equals two, softmax obtains the higher hierarchical score. On the much broader label set at k equals twenty, DeViSE plus one thousand is higher. This supports a conditional statement about semantic generalization, not universal dominance. A useful question is where the taxonomy enters the system: DeViSE does not require it to learn its label embeddings, but the evaluation uses that structure to decide which wrong labels count as semantically acceptable.

先指出反例：最容易的 2-hop、k=2 设置中，softmax 的层级分数更高；更大词表、k=20 时，DeViSE+1K 更高。这支持有条件的语义泛化结论，而不是普遍领先。还要明确层级的角色：DeViSE 不依赖人工层级来训练标签嵌入，但评估使用它定义哪些错误可以得到语义奖励。

**Audience prompt / 互动：** Where is WordNet used: embedding training, evaluation, or both? / WordNet 层级用于嵌入训练、评估，还是两者？

Source: Table 3, p.7; Supplement §A.3

## 15. Candidate sets can reverse a comparison / 候选集合可以改变方法排名 · 1 min

Table 4 evaluates a separate 800/200 split on ImageNet 2010.

Use this compact table to reinforce experimental reasoning. In the two-hundred-label setting, DeViSE trails Mensink. When the seen labels are allowed to compete, DeViSE retains more performance and the ordering reverses. The main lesson is that an evaluation protocol defines the scientific question. A method that works well when told that the answer must be unseen may behave differently when the system must choose between familiar and unfamiliar classes. Also retain the paper’s caveat that the Rohrbach number comes from a different unseen-class set.

用这张表强化实验分析：只在 200 类中选时，DeViSE 低于 Mensink；加入已见类后，它保留了更多性能，方法排名反转。评估协议决定科学问题：事先知道答案一定是未见类，与必须在熟悉和陌生类别之间选择，是不同任务。同时保留论文提醒：Rohrbach 的未见类别集合不同。

**Audience prompt / 互动：** Why can a method win with 200 candidates but lose with 1,000? / 为什么一种方法在 200 候选下领先，在 1,000 候选下却落后？

Source: Table 4, p.7; split description pp.7–8

## 16. What the evidence does not establish / 证据还没有证明什么 · 2 min

Zero-shot capability is conditional on useful semantic representations and a specified label vocabulary.

Return to the original question and qualify the answer. Yes, the model can rank labels without training images from those categories, provided meaningful label embeddings exist. It is still given a vocabulary of candidates; it is not a generative captioner. Polysemy is a concrete limitation documented in the supplement: crane can refer to a bird or a machine, but the language model has one vector for the term. Proposed follow-up work could test better sense representations and calibrate seen versus unseen scores. Those would be new experiments, not results already established in this paper or in our teaching demo.

回到开场问题，并给出条件：只要有有效标签嵌入，模型可以对没有训练图片的新类排序。但它仍使用给定候选词表，并不是生成式图片描述器。补充材料明确讨论多义词：crane 可以是鸟或机械，语言模型却只有一个词向量。后续可以检验词义区分表示以及已见／未见分数校准。这些是建议实验，不是原论文或教学示例已经证明的结果。

**Audience prompt / 互动：** Design one experiment that isolates seen-class bias from candidate-set size. / 如何设计实验，把已见类偏置与候选集合大小的影响分开？

Source: Main §4.2–5, pp.6–8; Supplement §A.2

## 17. Connect to ProtoNet without conflating the tasks / 与 ProtoNet 建立联系，但不混淆任务 · 1 min

Both use an embedding space; the source of each class representation is different.

Use your existing ProtoNet knowledge as a bridge. Both methods turn classification into comparing an image representation with class representations. The crucial question is where those class representations come from. ProtoNet constructs them from a few labeled images at test time. DeViSE obtains them from a pretrained language model and therefore does not need those support images. Do not claim that one is better by comparing their paper accuracies: the datasets, candidate sets, and supervision assumptions differ. Their connection is conceptual, and their evaluation protocols must remain separate.

利用你已有的 ProtoNet 基础：两者都比较图像表示和类别表示。关键问题是类别表示从哪里来。ProtoNet 在测试时从少量标注支持图像构建原型；DeViSE 从预训练语言模型获得表示，因此不需要这些支持图像。不能拿两篇论文的准确率直接判断谁更好，因为数据集、候选集合和监督假设不同。联系是概念上的，实验协议仍须分开。

**Audience prompt / 互动：** If no support image exists, where would a ProtoNet prototype come from? / 如果没有支持图像，ProtoNet 的原型从哪里来？

Source: DeViSE §3.3; Snell et al. (2017), §2

## 18. An extensible label vocabulary / 可以扩展的标签词表 · 1 min

A useful application idea is to change the labels without retraining a separate output unit for each one.

Describe an application as a conditional possibility rather than an established deployment. One service might use labels such as car and pedestrian; another might use specific vehicle names. A shared embedding model could rank either vocabulary if suitable label vectors exist. This is attractive when categories change over time. Yet the paper’s low absolute performance on the largest candidate set prevents us from assuming production reliability. A real system would need domain-specific evaluation, handling for unknown or ambiguous labels, and a carefully defined candidate set.

将应用描述为有条件的可能性，而不是已部署事实。一个系统可能使用“汽车、行人”等粗标签，另一个可能使用具体车型；如果有合适词向量，共享模型可对不同词表排序。类别经常变化时，这很有吸引力。但大候选集绝对准确率较低，不能假设它直接满足生产可靠性。实际应用还需要领域评估、未知或模糊标签处理以及明确的候选集合。

**Audience prompt / 互动：** Would adding any new word guarantee reliable recognition? / 加入任意新词，是否就保证可靠识别？

Source: §5, p.8: proposed applications, not deployment evidence

## 19. Three claims to take away / 带走三个结论 · 1 min

Text supplies class structure; ranking aligns modalities; protocol determines the meaning of success.

Close by restating the research question in one sentence: can semantics learned from text extend a visual classifier beyond its image training labels? The answer is yes under the paper’s assumptions, with measurable but limited performance. Mention the contribution, one exact empirical example, and one limitation. For example: the two-hop unseen-only hit at five is eighteen point one percent, but it drops to seven point nine when seen labels are also candidates. That concise contrast links the method to the evidence and shows why careful evaluation is as important as the model diagram. Invite questions about the loss, the candidate set, or the semantic metric.

最后用一句话重述：文本学习的语义能否让视觉分类器超出图像训练标签？在论文假设下可以，但性能有明确限制。结尾同时给出贡献、一个精确结果和一个局限。例如 2-hop 未见候选 hit@5 为 18.1%，加入已见标签降至 7.9%。这个对比连接了方法与证据，说明仔细阅读评估协议和理解模型图同样重要。邀请同学围绕损失、候选集合或语义指标提问。

**Audience prompt / 互动：** Explain DeViSE in one sentence, including one limitation. / 用一句话解释 DeViSE，并带上一个限制条件。

Source: Frome et al. (2013), p.8

## 20. Sources, evidence and reproducibility / 来源、证据与可复算说明 · 0 min

Reported results, teaching computations, and proposed extensions are kept distinct.

Use the local source links to inspect the evidence. The downloadable notes and reading guide share the website’s source content. Our numerical demonstrations are deterministic synthetic calculations; no original training run or pretrained DeViSE checkpoint is included. The thirty-minute plan includes audience questions and hands-on inspection, so rehearse instead of assuming that reading the notes verbatim will last exactly thirty minutes.

可以打开本地原文核验依据。可下载讲稿和阅读指南与网页共享内容来源。数值示例是确定性的合成计算；没有原论文训练过程或预训练 DeViSE 检查点。30 分钟安排包含提问和交互，请自行排练，不要假设逐字朗读一定恰好 30 分钟。

**Audience prompt / 互动：** Which claims are from the paper, and which are teaching examples? / 哪些结论来自论文，哪些只是教学示例？

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

