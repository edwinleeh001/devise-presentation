# DeViSE — COMP6710 · Li Hu

30-minute independent presentation + 10-minute Q&A. The plan includes interaction and inspection; rehearse timing. English website with independently switchable Chinese notes.

Primary evidence: Frome et al., NIPS 2013, pp.1–9, plus official supplement pp.1–3. AI-assisted organization, translation and implementation. Toy computations are not an ImageNet reproduction.

## Key learning outcomes / 重点知识

1. Explain what is and is not “unseen”. / 区分视觉未见类与可用语义信息。
2. Trace image → visual features → projection → label ranking. / 解释跨模态信息流。
3. Compute a hinge term and its gradient. / 手算排序损失与梯度。
4. Separate candidate sets from test image sets. / 区分候选标签与测试图像。
5. Interpret Tables 1–4 under their own protocols. / 按各自协议解释实验。
6. State limits without claiming universal superiority. / 说明边界，不夸大结论。

## 1. Can a model name what it has never seen? / 模型能认出从未见过的类别吗？

- A fixed 1,000-way softmax cannot output a category outside its label set. / 固定的 1,000 类 softmax 无法输出类别表以外的名称。
- New visual categories are expensive to annotate; their names already occur in text. / 为新类别标注图片成本很高，但它们的名称已经出现在文本中。
- The goal is both novel-class recognition and semantically reasonable mistakes. / 目标既是识别新类别，也是让错误在语义上更合理。

Source: Frome et al. (2013), p.1

## 2. Zero images is not zero information / 没有训练图片，不等于没有信息

- Seen classes S: labeled images train the visual mapping. / 已见类别 S：使用带标签图像训练视觉映射。
- Unseen classes U: no labeled training images; text embeddings remain available. / 未见类别 U：没有该类标注训练图像，但有类别词向量。
- At test time, the candidate set can be U or S ∪ U. / 测试候选类别可以是 U，也可以是 S ∪ U。

Source: Frome et al. (2013), p.2

## 3. The missing link between images and words / 连接图像与词语的研究缺口

- Softmax: strong closed-set prediction, but a fixed output vocabulary. / Softmax：闭集识别强，但输出词表固定。
- WSABIE: joint embeddings and ranking, but labels were limited to image training classes. / WSABIE：联合嵌入与排序，但类别局限于图像训练标签。
- Earlier cross-modal zero-shot work operated at a much smaller scale and used different objectives. / 更早的跨模态零样本研究规模更小，训练目标也不同。

Source: Frome et al. (2013), p.2

## 4. Two pretrained models. One semantic interface. / 两个预训练模型，一个语义接口

- Image x → visual feature v(x) ∈ ℝ⁴⁰⁹⁶ → projection Mv(x) ∈ ℝᵈ. / 图像 x → 4,096 维视觉特征 v(x) → d 维投影 Mv(x)。
- Label y → pretrained, unit-normalized text embedding tᵧ. / 标签 y → 预训练并单位归一化的文本向量 tᵧ。
- Score each candidate with tᵧ · Mv(x), where d is 500 or 1,000. / 以 tᵧ · Mv(x) 为候选标签打分，d 为 500 或 1,000。

Source: Frome et al. (2013), p.3

## 5. Where the semantic structure comes from / 语义结构从哪里来

![Original paper Figure 1 — Frome et al., NIPS 2013](../media/originals/devise-figure-1.png)

[Open original paper page 3](./devise-nips2013.pdf#page=3)

- Figure 1A: arrows mean parameter initialization; Figure 1B: label embeddings, not projected test images. / Figure 1A 的箭头表示参数初始化；Figure 1B 显示标签嵌入，不是测试图像投影。
- Skip-gram: predict nearby terms from a source term. / Skip-gram：用一个词预测上下文中的邻近词。
- Training corpus: 5.7 million Wikipedia documents, 5.4 billion words; approximately 155,000 terms. / 文本训练集：570 万篇维基百科文档、54 亿词，词表约 15.5 万项。
- Semantically related terms tend to have similar vectors; this need not imply identical visual appearance. / 语义相关词通常向量相近，但不一定具有相同视觉外观。

Source: Original Figure 1 and §3.1–3.3, p.3

## 6. Learn an ordering, not just a destination / 不仅靠近正确标签，还要排在错误标签之前

- sᵧ = tᵧMv(x); a negative term contributes max(0, m − sᵧ + sⱼ). / sᵧ = tᵧMv(x)；一个负标签的损失为 max(0, m − sᵧ + sⱼ)。
- The paper uses m = 0.1 and truncates after the first margin-violating negative. / 论文使用 m = 0.1，并在遇到第一个违反间隔的负标签后截断求和。
- A correct top-1 label can still have positive loss if its lead is too small. / 即使 top-1 预测正确，领先幅度不够时，损失仍可能大于零。

Source: Frome et al. (2013), p.4

## 7. What changes during training? / 训练时哪些参数会更新？

- Pretrain the visual model and the skip-gram model separately. / 分别预训练视觉模型和 Skip-gram 模型。
- First optimize projection M with visual and text representations fixed. / 先固定视觉和文本表示，只优化投影 M。
- Later backpropagate into the visual network; the paper reports a 1–3 percentage-point gain. / 之后反向传播到视觉网络；论文报告准确率提高 1–3 个百分点。

Source: Frome et al. (2013), p.4

## 8. Inspect one ranking update / 逐步检查一次排序更新

- Synthetic 2D vectors; fixed visual feature and fixed unit label vectors. / 合成二维向量；视觉特征和单位标签向量固定。
- For an active pair, ∂L/∂M = (tⱼ − tᵧ)ᵀvᵀ. / 当排序约束激活时，∂L/∂M = (tⱼ − tᵧ)ᵀvᵀ。
- Only the teaching projection is updated; no image model is trained here. / 只更新教学投影矩阵；这里没有训练图像模型。

Source: Teaching derivation from Eq.1, p.4; computed toy, not a reported experiment

## 9. The candidate vocabulary changes the answer / 候选词表会改变答案

- DeViSE-0: rank unseen labels only. / DeViSE-0：仅对未见标签排序。
- DeViSE+1K: rank unseen labels together with the 1,000 training labels. / DeViSE+1K：未见标签与 1,000 个训练标签共同排序。
- Identical trained model; different output candidates. / 训练好的模型相同，改变的是输出候选集合。

Source: Frome et al. (2013), p.6

## 10. Read the protocol before the headline result / 先读实验协议，再读结果

- Seen-class evaluation: 50K ILSVRC 2012 validation images split into 5K validation and 45K held-out test. / 已见类评估：将 ILSVRC 2012 的 5 万验证图像拆为 5 千调参与 4.5 万测试。
- Zero-shot: reuse the 500-D model without extra tuning; evaluate unseen ImageNet 2011 labels. / 零样本：复用 500 维模型，不额外调参，测试 ImageNet 2011 未见类别。
- Table 4 is a separate ImageNet 2010 800-seen / 200-unseen protocol. / Table 4 单独采用 ImageNet 2010 的 800 已见类／200 未见类协议。

Source: Supplement §A.1, p.1; main paper pp.6–8

## 11. Exact labels and reasonable mistakes / 正确标签与合理错误是两种指标

- Flat hit@k: is the exact true label anywhere in the top k? / Flat hit@k：真实标签是否出现在前 k 个预测中？
- Hierarchical precision@k: what fraction of top-k predictions belong to a hierarchy-derived acceptable set? / 层级 precision@k：前 k 个预测中，有多少属于层级结构定义的可接受集合？
- The acceptable set grows by graph radius until it contains at least k labels; it may contain many more. / 可接受集合按图半径扩展直到至少有 k 个标签，实际数量可能远大于 k。

Source: Main §4, pp.4–5; Supplement §A.3, pp.2–3

## 12. Comparable accuracy, different error structure / 准确率接近，错误结构不同

- Flat hit@1: softmax 55.6%; DeViSE-1000D 54.9%. / Flat hit@1：softmax 55.6%，DeViSE-1000D 54.9%。
- Flat hit@5: 78.5% versus 78.4%; performance is close, not an outright win. / Flat hit@5：78.5% 对 78.4%；表现接近，不是全面胜出。
- Random embeddings test whether semantic structure matters beyond the shared architecture. / 随机嵌入基线用于检验：除共享架构外，语义结构是否有贡献。

Source: Table 1, p.5

## 13. A larger label universe is a harder test / 候选标签越多，测试越困难

![Original paper Figure 2 — Frome et al., NIPS 2013](../media/originals/devise-figure-2.png)

[Open original paper page 6](./devise-nips2013.pdf#page=6)

- Figure 2: exact hits in A–D; both models miss E; softmax is more nearly correct in F. Selected qualitative cases are not an aggregate metric. / Figure 2：A–D 命中准确标签；E 两者均未命中；F 的 softmax 更接近。选取的定性案例不是总体指标。
- 2-hop unseen-only hit@5 is 18.1%; with seen labels included it is 7.9%. / 2-hop 未见类候选 hit@5 为 18.1%；加入已见类后为 7.9%。
- Across 20,841 unseen labels, unseen-only hit@1 is 0.8% and hit@5 is 2.5%. / 20,841 个未见标签下，未见候选 hit@1 为 0.8%，hit@5 为 2.5%。
- These are reported paper results, not measurements from the classroom demo. / 这些是论文报告结果，不是课堂示例的测量结果。

Source: Original Figure 2 and Table 2, p.6; §4.2 reading, p.7

## 14. Semantic quality has a boundary / 语义改善也有边界

- On 2-hop hierarchical precision@2, softmax is 0.236 versus 0.204 for DeViSE+1K. / 2-hop 层级 precision@2：softmax 0.236，DeViSE+1K 0.204。
- For the full 21K setting at k=20: 0.065 versus 0.101, favoring DeViSE+1K. / 全 21K 设置 k=20：0.065 对 0.101，DeViSE+1K 更高。
- WordNet is used for evaluation even though the semantic training space comes from text. / 语义训练空间来自文本，但评估仍使用 WordNet 层级。

Source: Table 3, p.7; Supplement §A.3

## 15. Candidate sets can reverse a comparison / 候选集合可以改变方法排名

- With 200 candidate labels: DeViSE 31.8%, Mensink et al. 35.7% hit@5. / 200 个候选标签：DeViSE 31.8%，Mensink 等 35.7% hit@5。
- With 1,000 candidates: DeViSE 9.0%, Mensink et al. 1.9%. / 1,000 个候选标签：DeViSE 9.0%，Mensink 等 1.9%。
- Rohrbach et al. used a different set of 200 zero-shot classes; treat the comparison cautiously. / Rohrbach 等使用不同的 200 个未见类，比较需谨慎。

Source: Table 4, p.7; split description pp.7–8

## 16. What the evidence does not establish / 证据还没有证明什么

- Language similarity may not match visual similarity; polysemous labels share a single term vector. / 语言相似不一定对应视觉相似；多义标签可能共享同一个词向量。
- Low absolute hit@1 on large label sets and seen-class bias remain. / 大词表下 top-1 绝对准确率低，已见类偏置仍存在。
- No claim of free-form caption generation, modern open-world reliability, or state-of-the-art performance today. / 不能据此宣称自由文本描述、现代开放世界可靠性，或当今最优性能。

Source: Main §4.2–5, pp.6–8; Supplement §A.2

## 17. Connect to ProtoNet without conflating the tasks / 与 ProtoNet 建立联系，但不混淆任务

- ProtoNet: a new class prototype is the mean of labeled support-image embeddings. / ProtoNet：新类原型来自标注支持图像嵌入的均值。
- DeViSE: a new class representation is supplied by its text embedding. / DeViSE：新类表示由文本嵌入提供。
- Few-shot support images and zero-shot semantic side information are different assumptions. / 少样本支持图像与零样本语义信息是不同资源假设。

Source: DeViSE §3.3; Snell et al. (2017), §2

## 18. An extensible label vocabulary / 可以扩展的标签词表

- Potential use: coarse or fine-grained image tagging from the same trained projection. / 潜在用途：同一个投影支持粗粒度或细粒度图像标签。
- Requirement: available label embeddings and visual-semantic compatibility. / 前提：有标签嵌入，并且视觉与语义能够对应。
- The paper proposes this flexibility; it does not document a deployed commercial product. / 论文提出这种灵活性，但没有报告已部署商业产品。

Source: §5, p.8: proposed applications, not deployment evidence

## 19. Three claims to take away / 带走三个结论

- Contribution: a scalable visual-semantic model that can rank unseen labels. / 贡献：可扩展的视觉语义模型，能够对未见标签排序。
- Evidence: near-parity on seen-class hit@5, useful semantic errors, conditional zero-shot transfer. / 证据：已见类 hit@5 接近基线，语义错误更合理，并有条件地实现零样本迁移。
- Boundary: new labels are not new knowledge from nothing; semantic resources and evaluation choices matter. / 边界：新标签不是凭空产生的新知识；语义资源与评估选择非常重要。

Source: Frome et al. (2013), p.8

## 20. Sources, evidence and reproducibility / 来源、证据与可复算说明

- Primary source: supplied NIPS 2013 paper, nine pages; official supplement, three pages. / 主要来源：你提供的 NIPS 2013 原文 9 页；官方补充材料 3 页。
- Tables are transcribed from the PDF; the paper page’s abstract differs from the supplied PDF, so exact claims use the tables. / 表格按 PDF 转录；出版网页摘要与提供 PDF 存在措辞差异，精确数值以表格为准。
- AI-assisted organization, translation and coding; presenter should verify understanding and rehearse timing. / 使用 AI 辅助整理、翻译和编码；演讲者应核验理解并计时排练。

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

