# DeViSE — complete English speaking script

Li Hu · COMP6710 · Frome et al., NIPS 2013

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

## 1. Can a model name what it has never seen?

### English speaking script

**Run of show: 00:00–01:05.** 5 seconds for activity; 4 seconds for pauses/changeover.

Hello everyone. Today I’ll discuss DeViSE: connecting visual recognition with meaning learned from language.

Let me start with a question. Suppose a classifier has learned to recognize dogs, but its output layer has no label for a shark. Could it ever call an image a shark? Recognizing a new photograph is one thing; recognizing a new category is another.

**Brief audience check:** Could a fixed softmax layer predict a label that is absent from its outputs?

DeViSE tries to bridge that gap using text. To understand how, we first need to be clear about what “unseen” means.

Source: Frome et al. (2013), p.1

## 2. Zero images is not zero information

### English speaking script

**Run of show: 01:05–02:20.** 5 seconds for activity; 4 seconds for pauses/changeover.

In this paper, an unseen class has no labeled training images available to the visual model. That does not mean the system knows nothing about it. Its name can still appear in the language model’s text.

For example, the visual model may see some shark species, while text supplies a vector for another. The aim is to transfer useful structure across that gap.

There are also two separate sets to keep track of: the images being tested, and the labels allowed as answers. Adding familiar labels to the answer list does not change the test images.

**Brief audience check:** What information is still available for an unseen class?

With that setting in mind, what was missing from the earlier approaches?

Source: Frome et al. (2013), p.2

## 3. The missing link between images and words

### English speaking script

**Run of show: 02:20–03:35.** 5 seconds for activity; 4 seconds for pauses/changeover.

The building blocks were already there: convolutional networks could learn useful visual features, and language models could place related words near one another. The challenge was to connect them in a way that worked across a much larger vocabulary.

That is the paper’s contribution: strong pretrained visual features, text-derived label representations, and a ranking objective, brought together at ImageNet scale. The authors train on a thousand visual classes and investigate transfer to roughly twenty thousand additional labels.

Several design choices changed together, so we should judge the full method rather than attribute every improvement to scale.

**Brief audience check:** What does a semantic label representation add that a larger softmax does not?

Let’s now follow the information through the model.

Source: Frome et al. (2013), p.2

## 4. Two pretrained models. One semantic interface.

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

Source: Frome et al. (2013), p.3

## 5. Where the semantic structure comes from

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

Source: Original Figure 1 and §3.1–3.3, p.3

## 6. Learn an ordering, not just a destination

### English speaking script

**Run of show: 07:30–09:10.** 10 seconds for activity; 4 seconds for pauses/changeover.

The objective is about an ordering. We want the correct label to score higher than a competing label by at least a small margin.

Read the hinge term as: the margin, minus the correct score, plus the competing score. If the correct label is already far enough ahead, the loss is zero. Otherwise, that pair produces a learning signal.

For our quick calculation, the margin is point one, the correct score is point six, and the competing score is point five five. The loss is point zero five. The correct label leads, but not by enough.

Equation one is written as a sum. In practice, the algorithm samples competing labels and stops at the first margin violation, rather than checking every label on every update.

**Brief audience check:** Why is the loss positive even though the correct label already scores higher?

That explains the objective. Next, let’s identify which parts of the model it changes.

Source: Frome et al. (2013), p.4

## 7. What changes during training?

### English speaking script

**Run of show: 09:10–10:25.** 5 seconds for activity; 4 seconds for pauses/changeover.

Pretraining gives the model a starting point; it does not mean that every component stays frozen.

The authors first train the projection matrix, M. They then fine-tune the visual network while keeping the language embeddings fixed. The paper uses asynchronous stochastic gradient descent with Adagrad learning rates.

Our teaching example is deliberately smaller. We freeze a two-dimensional visual feature and update only M using plain gradient descent. That lets us inspect the effect of one ranking constraint without pretending to reproduce the full ImageNet training run.

**Brief audience check:** Does the visual network stay frozen throughout training?

With that simplification clear, let’s walk through one update and see whether the score gap changes as expected.

Source: Frome et al. (2013), p.4

## 8. Inspect one ranking update

### English speaking script

**Run of show: 10:25–12:25.** 45 seconds for activity; 4 seconds for pauses/changeover.

Here is our small, computed example. The image feature and label vectors are fixed; only the projection changes. Before I advance it, predict what will happen to the gap between the correct and competing scores.

[Demo cue — 45 seconds, including the audience response. Use margin 0.1 and learning rate 0.1; advance once, inspect the gap, rewind, then try learning rate zero. Skip extra presets and the optional slide-rule.]

After that active update, the gap increases and the loss falls. Rewinding restores the same state. Setting the learning rate to zero leaves the model unchanged, which confirms that the update drives the result.

This is one constraint in a toy problem. It does not show that every real training example improves on every step. And these similarity scores are not probabilities.

**Brief audience check:** After an active update, what should happen to the correct-label score gap?

We’ve now seen how a score changes during learning. What happens if the scores stay fixed, but the available answers change?

Source: Teaching derivation from Eq.1, p.4; computed toy, not a reported experiment

## 9. The candidate vocabulary changes the answer

### English speaking script

**Run of show: 12:25–13:50.** 20 seconds for activity; 4 seconds for pauses/changeover.

Let’s keep the image vector fixed and change only the candidate list. With unseen labels alone, the unseen shark label wins. Allow a nearby seen shark label to compete, and that familiar label can take first place.

[Demo cue — 20 seconds, including the audience response. Toggle seen candidates once; keep the query angle unchanged.]

Nothing was retrained. DeViSE zero and DeViSE plus one thousand describe different candidate sets for the same trained model. Both settings still test unseen-class images.

With unit-length labels and a fixed nonzero query, dot product and cosine rankings agree. Their numeric values and fixed-margin losses need not.

**Brief audience check:** When I add seen labels to the candidates, have the model weights changed?

This sensitivity to the answer list is why the evaluation protocol comes next.

Source: Frome et al. (2013), p.6

## 10. Read the protocol before the headline result

### English speaking script

**Run of show: 13:50–15:05.** 5 seconds for activity; 4 seconds for pauses/changeover.

Before looking at the headline numbers, let’s check how they were obtained.

For the main seen-class evaluation, the authors split the original ImageNet validation set: five thousand images for model selection, and forty-five thousand for reporting results. This is not the hidden competition test set. The supplement also specifies a single center crop and the same evaluation procedure for the softmax baseline.

The zero-shot experiments reuse the five-hundred-dimensional model without further tuning. Table four, however, uses a different dataset year and class split. We cannot treat its percentages as directly comparable with Table two.

**Brief audience check:** Why do Tables two and four answer different experimental questions?

Once the protocol is clear, the next question is what counts as a successful prediction.

Source: Supplement §A.1, p.1; main paper pp.6–8

## 11. Exact labels and reasonable mistakes

### English speaking script

**Run of show: 15:05–16:25.** 8 seconds for activity; 4 seconds for pauses/changeover.

Suppose the true label is one bird species, but the model predicts a related bird. Exact-label accuracy still counts that as wrong. A hierarchical metric can give credit for being semantically close.

The acceptable set expands around the true label in the taxonomy until it contains at least k labels. Since a whole neighborhood is added at once, the set may contain more than k.

So hierarchical precision answers a different question from exact-label accuracy. It also depends on the taxonomy. At k equals one, only the exact label is acceptable, so the metrics agree once we express them in the same units.

**Brief audience check:** Does a higher hierarchical score necessarily mean more exact species predictions?

Let’s use that distinction to read the seen-class results.

Source: Main §4, pp.4–5; Supplement §A.3, pp.2–3

## 12. Comparable accuracy, different error structure

### English speaking script

**Run of show: 16:25–17:50.** 8 seconds for activity; 4 seconds for pauses/changeover.

On the familiar thousand classes, the result is quite balanced. At top one, softmax scores fifty-five point six percent, compared with fifty-four point nine for the thousand-dimensional DeViSE model. At top five, they are almost tied: seventy-eight point five versus seventy-eight point four percent.

Some hierarchical scores improve, which suggests a difference in the structure of the errors, rather than a clear win on exact-label accuracy.

The random-embedding baseline helps us ask whether the text-derived geometry is useful. It keeps the general architecture but removes the meaningful organization of the labels. That is useful evidence, though it does not control every possible training difference.

**Brief audience check:** Which baseline tests the value of meaningful label geometry?

So much for familiar classes. The more distinctive test is whether the model can name classes without their training images.

Source: Table 1, p.5

## 13. A larger label universe is a harder test

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

Source: Original Figure 2 and Table 2, p.6; §4.2 reading, p.7

## 14. Semantic quality has a boundary

### English speaking script

**Run of show: 20:10–21:15.** 5 seconds for activity; 4 seconds for pauses/changeover.

The hierarchical results also depend on the setting. In the two-hop task at k equals two, softmax has the higher score. With the full label set at k equals twenty, DeViSE plus one thousand does better.

That supports a conditional claim about semantic generalization, rather than a claim that DeViSE wins everywhere. WordNet has a specific role here: it is used to evaluate semantic closeness, not to train these label embeddings.

**Brief audience check:** Where is WordNet used here: training the embeddings, or evaluating their predictions?

Table four gives us another example of why the comparison setting matters.

Source: Table 3, p.7; Supplement §A.3

## 15. Candidate sets can reverse a comparison

### English speaking script

**Run of show: 21:15–22:25.** 5 seconds for activity; 4 seconds for pauses/changeover.

Table four uses a separate split: eight hundred seen classes and two hundred unseen classes. With only the two hundred unseen labels as candidates, DeViSE trails Mensink’s method. With all thousand labels competing, the ordering reverses.

One setting requires an unseen answer; the other makes seen and unseen labels compete. We also need the paper’s caveat: Rohrbach’s result uses a different unseen-class set.

**Brief audience check:** Why can the ranking of two methods reverse when seen labels are allowed to compete?

Across these tables, the lesson is consistent. The candidate set is part of the task, not a minor reporting detail. That brings us to the model’s broader limits.

Source: Table 4, p.7; split description pp.7–8

## 16. What the evidence does not establish

### English speaking script

**Run of show: 22:25–24:20.** 12 seconds for activity; 4 seconds for pauses/changeover.

We can now answer the opening question, with some qualifications. DeViSE can rank a label without labeled training images from that class, provided a suitable semantic representation is available.

It still needs a candidate vocabulary. It is not freely generating a description of the image. Meaning can also be ambiguous: “crane” may refer to a bird or a machine, while the language model provides one vector for that word.

There is also a gap between a plausible result and reliable recognition. Accuracy is low on the largest label set, and seen classes can attract predictions away from unseen ones.

One useful follow-up experiment would hold the test images and candidate count fixed while changing how similar the seen candidates are to the true unseen labels. That could help separate semantic competition from simply having more candidates. It would be a new experiment, not a result established here.

**Brief audience check:** What would you hold fixed to distinguish semantic competition from candidate-set size?

These limits also help us compare DeViSE with a method we already know: ProtoNet.

Source: Main §4.2–5, pp.6–8; Supplement §A.2

## 17. Connect to ProtoNet without conflating the tasks

### English speaking script

**Run of show: 24:20–25:30.** 5 seconds for activity; 4 seconds for pauses/changeover.

Both DeViSE and ProtoNet compare an image representation with class representations. The key difference is where those class representations come from.

ProtoNet builds a prototype by averaging embeddings of a few labeled support images for a new class. DeViSE takes the class representation from a language model instead. It therefore uses a different resource when those support images are unavailable.

The connection is conceptual. Their accuracies are not directly comparable because the datasets and supervision differ.

**Brief audience check:** Without support images, where does each method obtain its class representation?

The shared idea is a flexible representation of a class. What could that flexibility offer in practice?

Source: DeViSE §3.3; Snell et al. (2017), §2

## 18. An extensible label vocabulary

### English speaking script

**Run of show: 25:30–26:30.** 5 seconds for activity; 4 seconds for pauses/changeover.

A shared embedding model could support different label vocabularies. One application might use broad categories such as car and pedestrian; another might need more specific vehicle names. Suitable text embeddings could let the same visual mapping rank either set.

That flexibility is attractive, but adding a word does not guarantee recognition. A practical system would still need domain-specific evaluation, a defined candidate set, and a way to handle ambiguity or genuinely unknown inputs.

**Brief audience check:** Would adding a new word guarantee reliable recognition?

These are possibilities, not demonstrated deployments. Let me close with three takeaways.

Source: §5, p.8: proposed applications, not deployment evidence

## 19. Three claims to take away

### English speaking script

**Run of show: 26:30–28:00.** 5 seconds for activity; 4 seconds for pauses/changeover.

First, language gives visual recognition a source of class structure beyond the image training labels.

Second, DeViSE learns to connect those representations through a ranking objective: the correct label should score above its competitors.

Third, the evaluation setting is essential to interpreting the result. In the two-hop example, changing only the candidates takes hit at five from eighteen point one to seven point nine percent. The semantic bridge is useful, but its success is conditional.

So the answer is yes: meaningful label representations can enable recognition of some visually unseen classes. Success still depends on the candidate vocabulary.

**Brief audience check:** What condition needs to accompany the claim that DeViSE recognizes unseen classes?

Thank you. I’m happy to take questions.

Source: Frome et al. (2013), p.8

## 20. Sources, evidence and reproducibility

### English speaking script

**Reference only — outside the timed talk.**

[Reference slide — outside the timed talk. Do not read this slide aloud; use it during the separate Q&A.]

The original paper, official supplement, reading guide, and video assets are available in the downloads. Reported results are attributed to the paper; the interactive calculations are teaching examples. No original ImageNet training run is reproduced here.

**Audience prompt:** Which evidence comes from the paper, and which from the teaching examples?

Source: Frome et al. (2013), p.1

## Q&A preparation — backup, outside the timed talk

### 1. Why is this zero-shot if text includes the class name?

Zero-shot is defined relative to visual training examples for those classes. Semantic side information is explicitly available.

Source: §4.2, p.6

### 2. Are word embeddings updated in the reported joint training?

They are held fixed. A footnote discusses possible joint language training as an extension, not the reported procedure.

Source: §3.3, p.4, footnote 5

### 3. Is the visual backbone always frozen?

No. M is trained first; the visual network is fine-tuned later.

Source: §3.3, p.4

### 4. Why ranking loss rather than L2?

Prediction is based on label ordering. The hinge explicitly penalizes wrong labels that score too close to or above the correct one. The paper reports poorer L2 results, not a universal guarantee.

Source: §3.3, p.4

### 5. Are dot product and cosine identical?

For unit label vectors and a fixed nonzero query, they induce the same ranking. Their values differ by query norm; fixed-margin losses need not be identical.

Source: §3.3 + algebraic deduction

### 6. Is the displayed similarity a probability?

No. The toy and paper objective use dot-product scores. No probability calibration is established.

Source: Eq.1, p.4

### 7. Are DeViSE-0 and DeViSE+1K different trained models?

No. They are the same trained model evaluated with different candidate label sets.

Source: Table 2 caption, p.6

### 8. What exactly does 18.1% mean?

Flat hit@5 for DeViSE-0 on the 1,589-label 2-hop unseen candidate set. It is neither top-1 nor the full-21K result.

Source: Table 2, p.6

### 9. Is WordNet absent from the whole study?

No. Learned text embeddings do not require the curated hierarchy as their training target, but evaluation uses the ImageNet/WordNet hierarchy.

Source: §2; Supplement §A.3

### 10. Does DeViSE beat softmax on every metric?

No. Softmax is better at seen-class top-1 and at some hierarchical settings. Always specify metric and candidate set.

Source: Tables 1 and 3

### 11. What does the random embedding baseline control?

It removes learned semantic label structure while retaining the embedding-based model form. It supports, but does not perfectly isolate, the value of text semantics.

Source: §4 and Table 1

### 12. How is this different from ProtoNet?

DeViSE gets a class vector from text; ProtoNet normally computes it from labeled support images. The resource assumptions and objectives differ.

Source: DeViSE §3; Snell et al. §2

### 13. What happens with ambiguous labels?

A single term vector may represent multiple ImageNet synsets. The supplement expands terms to synsets, removes duplicates, and truncates the ranked list. This does not resolve word senses in the embedding itself.

Source: Supplement §A.2

### 14. Can we compare Table 2 and Table 4 directly?

No. Table 4 uses ImageNet 2010 with an 800/200 class split; Table 2 uses the 2012-trained model and 2011 unseen labels.

Source: Supplement §A.1

### 15. What would you improve?

Test sense-aware embeddings, candidate-set calibration, and controlled domain shifts. These are proposed follow-ups, not measured results here.

Source: Presenter proposals

