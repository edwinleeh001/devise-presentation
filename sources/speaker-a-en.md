# DeViSE - Speaker A

English script by slide · Slides 1-9 · Budget 15:00

## Roles and timing

**This script is for Speaker A: Research question, model and inference.** A covers slides 1-9; B covers slides 10-19. Slide 20 is the shared reference page.

**Your timer runs from 00:00 to 15:00: target 14:30, with 00:30 contingency.** The rehearsal talk clock is 00:00-15:00. A may hand over earlier; B resets the personal timer on taking over. There is no need to wait until 15:00.

- Chinese and English are alternative versions. Choose one delivery language for both speakers; do not deliver both versions back to back.
- The 40 seconds of video, audience responses, applicable 45-second ranking / 20-second candidate demonstrations, pauses and spoken handover are included. Play each clip once; do not read its recorded narration aloud.
- Brackets contain unspoken operating cues. Take one brief audience response per question. Speak the prepared explanation during a demonstration; do not add extra presets.
- Estimates use 110 English words or 200 equivalent Chinese units per minute, with additional allowance for foreign terms and digits in Chinese. Rehearse against the cumulative slide deadlines.
- If still speaking at 14:30, A goes straight to the handover and B goes straight to the three takeaways. Skip extra responses, do not replay clips, and stop by your own 15:00. Slide 20 and Q&A follow both timed parts.

| Slide and title | Your clock | Talk clock | Video |
|---|---|---|---:|
| 1. Can a model name what it has never seen? | 00:00-01:15 | 00:00-01:15 | 0s |
| 2. Zero images is not zero information | 01:15-02:30 | 01:15-02:30 | 0s |
| 3. The missing link between images and words | 02:30-03:45 | 02:30-03:45 | 0s |
| 4. Two pretrained models. One semantic interface. | 03:45-05:25 | 03:45-05:25 | 20s |
| 5. Where the semantic structure comes from | 05:25-07:40 | 05:25-07:40 | 20s |
| 6. Learn an ordering, not just a destination | 07:40-09:20 | 07:40-09:20 | 0s |
| 7. What changes during training? | 09:20-10:35 | 09:20-10:35 | 0s |
| 8. Inspect one ranking update | 10:35-12:35 | 10:35-12:35 | 0s |
| 9. The candidate vocabulary changes the answer | 12:35-14:30 | 12:35-14:30 | 0s |

**Your 14:30-15:00 window is contingency, already inside the 15-minute limit.**

## 1. Can a model name what it has never seen?

**Run of show: your clock 00:00-01:15; talk clock 00:00-01:15.** Speaker A. Includes 0s video, 5s activity and 4s pauses/changeover.

Hello everyone. Today we’ll discuss DeViSE: connecting visual recognition with meaning learned from language. I’ll explain the model and how it makes predictions. My co-presenter will examine the evidence and its limits.

Let me start with a question. Suppose a classifier has learned to recognize dogs, but its output layer has no label for a shark. Could it ever call an image a shark? Recognizing a new photograph is one thing; recognizing a new category is another.

**Brief audience check:** Could a fixed softmax layer predict a label that is absent from its outputs?

DeViSE tries to bridge that gap using text. To understand how, we first need to be clear about what “unseen” means.

Source: Frome et al. (2013), p.1

## 2. Zero images is not zero information

**Run of show: your clock 01:15-02:30; talk clock 01:15-02:30.** Speaker A. Includes 0s video, 5s activity and 4s pauses/changeover.

In this paper, an unseen class has no labeled training images available to the visual model. That does not mean the system knows nothing about it. Its name can still appear in the language model’s text.

For example, the visual model may see some shark species, while text supplies a vector for another. The aim is to transfer useful structure across that gap.

There are also two separate sets to keep track of: the images being tested, and the labels allowed as answers. Adding familiar labels to the answer list does not change the test images.

**Brief audience check:** What information is still available for an unseen class?

With that setting in mind, what was missing from the earlier approaches?

Source: Frome et al. (2013), p.2

## 3. The missing link between images and words

**Run of show: your clock 02:30-03:45; talk clock 02:30-03:45.** Speaker A. Includes 0s video, 5s activity and 4s pauses/changeover.

The building blocks were already there: convolutional networks could learn useful visual features, and language models could place related words near one another. The challenge was to connect them in a way that worked across a much larger vocabulary.

That is the paper’s contribution: strong pretrained visual features, text-derived label representations, and a ranking objective, brought together at ImageNet scale. The authors train on a thousand visual classes and investigate transfer to roughly twenty thousand additional labels.

Several design choices changed together, so we should judge the full method rather than attribute every improvement to scale.

**Brief audience check:** What does a semantic label representation add that a larger softmax does not?

Let’s now follow the information through the model.

Source: Frome et al. (2013), p.2

## 4. Two pretrained models. One semantic interface.

**Run of show: your clock 03:45-05:25; talk clock 03:45-05:25.** Speaker A. Includes 20s video, 5s activity and 4s pauses/changeover.

**Before playback — say:**

Here’s the idea in twenty seconds. Watch how the image moves from visual features into a space shared with label meanings. We’ll then return to the authors’ original diagram to examine the details.

**Playback cue — DeViSE overview · English · 20 seconds:**

Play the English overview once. Let its narration finish before speaking again.

[Play video (20 seconds)](../media/devise-20s-en.mp4)

[Subtitles](../media/devise-20s-en.srt)

**Video narration — recorded, do not read over it:**

Can a model recognize classes it's never trained on? DeViSE learns word embeddings and visual features. Then it maps images into a shared space, so the correct labels score higher. It can even predict unseen classes, if their word embeddings are available.

**After playback — say:**

The key move is to replace a fixed list of output classes with a comparison between an image vector and candidate label vectors. Text supplies the label representations; training images teach the visual mapping. A new label can enter that comparison if its embedding is available. That gives us a route to zero-shot recognition, although it does not guarantee a correct prediction.

**Brief audience check:** Which component connects the visual features to the label space?

**Transition to Figure 1 — say:**

That was the overview. Now let’s use the original Figure 1 to see where the two representations come from and what is actually learned.

Source: Frome et al. (2013), p.3

## 5. Where the semantic structure comes from

**Run of show: your clock 05:25-07:40; talk clock 05:25-07:40.** Speaker A. Includes 20s video, 8s activity and 4s pauses/changeover.

![Original paper Figure 1 - Frome et al., NIPS 2013](../media/originals/devise-figure-1.png)

[Open original paper page 3](./devise-nips2013.pdf#page=3)

**Before playback — say:**

Figure 1 has two panels. In this short clip, follow the two pretrained models into the joint system, then look at the colored neighborhoods in panel B.

**Playback cue — Figure 1 · English · 20 seconds:**

Play the English Figure 1 video once; resume after it finishes.

[Play video (20 seconds)](../media/devise-figure-1-en.mp4)

[Subtitles](../media/devise-figure-1-en.srt)

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

**Run of show: your clock 07:40-09:20; talk clock 07:40-09:20.** Speaker A. Includes 0s video, 10s activity and 4s pauses/changeover.

The objective is about an ordering. We want the correct label to score higher than a competing label by at least a small margin.

Read the hinge term as: the margin, minus the correct score, plus the competing score. If the correct label is already far enough ahead, the loss is zero. Otherwise, that pair produces a learning signal.

For our quick calculation, the margin is point one, the correct score is point six, and the competing score is point five five. The loss is point zero five. The correct label leads, but not by enough.

Equation one is written as a sum. In practice, the algorithm samples competing labels and stops at the first margin violation, rather than checking every label on every update.

**Brief audience check:** Why is the loss positive even though the correct label already scores higher?

That explains the objective. Next, let’s identify which parts of the model it changes.

Source: Frome et al. (2013), p.4

## 7. What changes during training?

**Run of show: your clock 09:20-10:35; talk clock 09:20-10:35.** Speaker A. Includes 0s video, 5s activity and 4s pauses/changeover.

Pretraining gives the model a starting point; it does not mean that every component stays frozen.

The authors first train the projection matrix, M. They then fine-tune the visual network while keeping the language embeddings fixed. The paper uses asynchronous stochastic gradient descent with Adagrad learning rates.

Our teaching example is deliberately smaller. We freeze a two-dimensional visual feature and update only M using plain gradient descent. That lets us inspect the effect of one ranking constraint without pretending to reproduce the full ImageNet training run.

**Brief audience check:** Does the visual network stay frozen throughout training?

With that simplification clear, let’s walk through one update and see whether the score gap changes as expected.

Source: Frome et al. (2013), p.4

## 8. Inspect one ranking update

**Run of show: your clock 10:35-12:35; talk clock 10:35-12:35.** Speaker A. Includes 0s video, 45s activity and 4s pauses/changeover.

Here is our small, computed example. The image feature and label vectors are fixed; only the projection changes. Before I advance it, predict what will happen to the gap between the correct and competing scores.

[Demo cue — 45 seconds, including the audience response. Use margin 0.1 and learning rate 0.1; advance once, inspect the gap, rewind, then try learning rate zero. Skip extra presets and the optional slide-rule.]

After that active update, the gap increases and the loss falls. Rewinding restores the same state. Setting the learning rate to zero leaves the model unchanged, which confirms that the update drives the result.

This is one constraint in a toy problem. It does not show that every real training example improves on every step. And these similarity scores are not probabilities.

**Brief audience check:** After an active update, what should happen to the correct-label score gap?

We’ve now seen how a score changes during learning. What happens if the scores stay fixed, but the available answers change?

Source: Teaching derivation from Eq.1, p.4; computed toy, not a reported experiment

## 9. The candidate vocabulary changes the answer

**Run of show: your clock 12:35-14:30; talk clock 12:35-14:30.** Speaker A. Includes 0s video, 20s activity and 4s pauses/changeover.

Let’s keep the image vector fixed and change only the candidate list. With unseen labels alone, the unseen shark label wins. Allow a nearby seen shark label to compete, and that familiar label can take first place.

[Demo cue — 20 seconds, including the audience response. Toggle seen candidates once; keep the query angle unchanged.]

Nothing was retrained. DeViSE zero and DeViSE plus one thousand describe different candidate sets for the same trained model. Both settings still test unseen-class images.

With unit-length labels and a fixed nonzero query, dot product and cosine rankings agree. Their numeric values and fixed-margin losses need not.

**Brief audience check:** When I add seen labels to the candidates, have the model weights changed?

**Handover to Speaker B - say:**

We’ve seen how DeViSE makes a prediction. The next question is how well it works, and under which conditions. I’ll hand over to my co-presenter to examine the evaluation and results.

Source: Frome et al. (2013), p.6

## 20. Sources, evidence and reproducibility

**Reference only - outside the timed talk.** Shared by both speakers; do not read it item by item.

[Reference slide — outside the timed talk. Do not read this slide aloud; use it during the separate Q&A.]

The original paper, official supplement, reading guide, and video assets are available in the downloads. Reported results are attributed to the paper; the interactive calculations are teaching examples. No original ImageNet training run is reproduced here.

**Reference prompt:** Which evidence comes from the paper, and which from the teaching examples?

Source: Frome et al. (2013), p.1

## Q&A preparation - backup, outside your 15 minutes

Start Q&A after both timed parts. These are suggested lead answers; the other speaker may add detail.

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

### 11. What does the random embedding baseline control?

It removes learned semantic label structure while retaining the embedding-based model form. It supports, but does not perfectly isolate, the value of text semantics.

Source: §4 and Table 1

