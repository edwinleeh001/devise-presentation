# DeViSE - Speaker B

English script by slide · Slides 10-19 · Budget 15:00

## Roles and timing

**This script is for Speaker B: Evaluation, results and critical discussion.** A covers slides 1-9; B covers slides 10-19. Slide 20 is the shared reference page.

**Your timer runs from 00:00 to 15:00: target 14:30, with 00:30 contingency.** The rehearsal talk clock is 15:00-30:00. A may hand over earlier; B resets the personal timer on taking over. There is no need to wait until 15:00.

- Chinese and English are alternative versions. Choose one delivery language for both speakers; do not deliver both versions back to back.
- The 20 seconds of video, audience responses, applicable 45-second ranking / 20-second candidate demonstrations, pauses and spoken handover are included. Play each clip once; do not read its recorded narration aloud.
- Brackets contain unspoken operating cues. Take one brief audience response per question. Speak the prepared explanation during a demonstration; do not add extra presets.
- Estimates use 110 English words or 200 equivalent Chinese units per minute, with additional allowance for foreign terms and digits in Chinese. Rehearse against the cumulative slide deadlines.
- If still speaking at 14:30, A goes straight to the handover and B goes straight to the three takeaways. Skip extra responses, do not replay clips, and stop by your own 15:00. Slide 20 and Q&A follow both timed parts.

| Slide and title | Your clock | Talk clock | Video |
|---|---|---|---:|
| 10. Read the protocol before the headline result | 00:00-01:25 | 15:00-16:25 | 0s |
| 11. Exact labels and reasonable mistakes | 01:25-02:45 | 16:25-17:45 | 0s |
| 12. Comparable accuracy, different error structure | 02:45-04:10 | 17:45-19:10 | 0s |
| 13. A larger label universe is a harder test | 04:10-06:30 | 19:10-21:30 | 20s |
| 14. Semantic quality has a boundary | 06:30-07:35 | 21:30-22:35 | 0s |
| 15. Candidate sets can reverse a comparison | 07:35-08:45 | 22:35-23:45 | 0s |
| 16. What the evidence does not establish | 08:45-10:40 | 23:45-25:40 | 0s |
| 17. Connect to ProtoNet without conflating the tasks | 10:40-11:50 | 25:40-26:50 | 0s |
| 18. An extensible label vocabulary | 11:50-12:50 | 26:50-27:50 | 0s |
| 19. Three claims to take away | 12:50-14:30 | 27:50-29:30 | 0s |

**Your 14:30-15:00 window is contingency, already inside the 15-minute limit.**

## 10. Read the protocol before the headline result

**Run of show: your clock 00:00-01:25; talk clock 15:00-16:25.** Speaker B. Includes 0s video, 5s activity and 4s pauses/changeover.

Thank you. We now know how the model works. I’ll focus on what the experiments actually establish. Before looking at the headline numbers, let’s check how they were obtained.

For the main seen-class evaluation, the authors split the original ImageNet validation set: five thousand images for model selection, and forty-five thousand for reporting results. This is not the hidden competition test set. The supplement also specifies a single center crop and the same evaluation procedure for the softmax baseline.

The zero-shot experiments reuse the five-hundred-dimensional model without further tuning. Table four, however, uses a different dataset year and class split. We cannot treat its percentages as directly comparable with Table two.

**Brief audience check:** Why do Tables two and four answer different experimental questions?

Once the protocol is clear, the next question is what counts as a successful prediction.

Source: Supplement §A.1, p.1; main paper pp.6–8

## 11. Exact labels and reasonable mistakes

**Run of show: your clock 01:25-02:45; talk clock 16:25-17:45.** Speaker B. Includes 0s video, 8s activity and 4s pauses/changeover.

Suppose the true label is one bird species, but the model predicts a related bird. Exact-label accuracy still counts that as wrong. A hierarchical metric can give credit for being semantically close.

The acceptable set expands around the true label in the taxonomy until it contains at least k labels. Since a whole neighborhood is added at once, the set may contain more than k.

So hierarchical precision answers a different question from exact-label accuracy. It also depends on the taxonomy. At k equals one, only the exact label is acceptable, so the metrics agree once we express them in the same units.

**Brief audience check:** Does a higher hierarchical score necessarily mean more exact species predictions?

Let’s use that distinction to read the seen-class results.

Source: Main §4, pp.4–5; Supplement §A.3, pp.2–3

## 12. Comparable accuracy, different error structure

**Run of show: your clock 02:45-04:10; talk clock 17:45-19:10.** Speaker B. Includes 0s video, 8s activity and 4s pauses/changeover.

On the familiar thousand classes, the result is quite balanced. At top one, softmax scores fifty-five point six percent, compared with fifty-four point nine for the thousand-dimensional DeViSE model. At top five, they are almost tied: seventy-eight point five versus seventy-eight point four percent.

Some hierarchical scores improve, which suggests a difference in the structure of the errors, rather than a clear win on exact-label accuracy.

The random-embedding baseline helps us ask whether the text-derived geometry is useful. It keeps the general architecture but removes the meaningful organization of the labels. That is useful evidence, though it does not control every possible training difference.

**Brief audience check:** Which baseline tests the value of meaningful label geometry?

So much for familiar classes. The more distinctive test is whether the model can name classes without their training images.

Source: Table 1, p.5

## 13. A larger label universe is a harder test

**Run of show: your clock 04:10-06:30; talk clock 19:10-21:30.** Speaker B. Includes 20s video, 10s activity and 4s pauses/changeover.

![Original paper Figure 2 - Frome et al., NIPS 2013](../media/originals/devise-figure-2.png)

[Open original paper page 6](./devise-nips2013.pdf#page=6)

**Before playback — say:**

Figure 2 gives us selected examples from that zero-shot test. Watch for a correct prediction, a plausible miss, and a case where the baseline does better.

**Playback cue — Figure 2 · English · 20 seconds:**

Play the English Figure 2 video once; resume after it finishes.

[Play video (20 seconds)](../media/devise-figure-2-en.mp4)

[Subtitles](../media/devise-figure-2-en.srt)

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

**Run of show: your clock 06:30-07:35; talk clock 21:30-22:35.** Speaker B. Includes 0s video, 5s activity and 4s pauses/changeover.

The hierarchical results also depend on the setting. In the two-hop task at k equals two, softmax has the higher score. With the full label set at k equals twenty, DeViSE plus one thousand does better.

That supports a conditional claim about semantic generalization, rather than a claim that DeViSE wins everywhere. WordNet has a specific role here: it is used to evaluate semantic closeness, not to train these label embeddings.

**Brief audience check:** Where is WordNet used here: training the embeddings, or evaluating their predictions?

Table four gives us another example of why the comparison setting matters.

Source: Table 3, p.7; Supplement §A.3

## 15. Candidate sets can reverse a comparison

**Run of show: your clock 07:35-08:45; talk clock 22:35-23:45.** Speaker B. Includes 0s video, 5s activity and 4s pauses/changeover.

Table four uses a separate split: eight hundred seen classes and two hundred unseen classes. With only the two hundred unseen labels as candidates, DeViSE trails Mensink’s method. With all thousand labels competing, the ordering reverses.

One setting requires an unseen answer; the other makes seen and unseen labels compete. We also need the paper’s caveat: Rohrbach’s result uses a different unseen-class set.

**Brief audience check:** Why can the ranking of two methods reverse when seen labels are allowed to compete?

Across these tables, the lesson is consistent. The candidate set is part of the task, not a minor reporting detail. That brings us to the model’s broader limits.

Source: Table 4, p.7; split description pp.7–8

## 16. What the evidence does not establish

**Run of show: your clock 08:45-10:40; talk clock 23:45-25:40.** Speaker B. Includes 0s video, 12s activity and 4s pauses/changeover.

We can now answer the opening question, with some qualifications. DeViSE can rank a label without labeled training images from that class, provided a suitable semantic representation is available.

It still needs a candidate vocabulary. It is not freely generating a description of the image. Meaning can also be ambiguous: “crane” may refer to a bird or a machine, while the language model provides one vector for that word.

There is also a gap between a plausible result and reliable recognition. Accuracy is low on the largest label set, and seen classes can attract predictions away from unseen ones.

One useful follow-up experiment would hold the test images and candidate count fixed while changing how similar the seen candidates are to the true unseen labels. That could help separate semantic competition from simply having more candidates. It would be a new experiment, not a result established here.

**Brief audience check:** What would you hold fixed to distinguish semantic competition from candidate-set size?

These limits also help us compare DeViSE with a method we already know: ProtoNet.

Source: Main §4.2–5, pp.6–8; Supplement §A.2

## 17. Connect to ProtoNet without conflating the tasks

**Run of show: your clock 10:40-11:50; talk clock 25:40-26:50.** Speaker B. Includes 0s video, 5s activity and 4s pauses/changeover.

Both DeViSE and ProtoNet compare an image representation with class representations. The key difference is where those class representations come from.

ProtoNet builds a prototype by averaging embeddings of a few labeled support images for a new class. DeViSE takes the class representation from a language model instead. It therefore uses a different resource when those support images are unavailable.

The connection is conceptual. Their accuracies are not directly comparable because the datasets and supervision differ.

**Brief audience check:** Without support images, where does each method obtain its class representation?

The shared idea is a flexible representation of a class. What could that flexibility offer in practice?

Source: DeViSE §3.3; Snell et al. (2017), §2

## 18. An extensible label vocabulary

**Run of show: your clock 11:50-12:50; talk clock 26:50-27:50.** Speaker B. Includes 0s video, 5s activity and 4s pauses/changeover.

A shared embedding model could support different label vocabularies. One application might use broad categories such as car and pedestrian; another might need more specific vehicle names. Suitable text embeddings could let the same visual mapping rank either set.

That flexibility is attractive, but adding a word does not guarantee recognition. A practical system would still need domain-specific evaluation, a defined candidate set, and a way to handle ambiguity or genuinely unknown inputs.

**Brief audience check:** Would adding a new word guarantee reliable recognition?

These are possibilities, not demonstrated deployments. Let me close with three takeaways.

Source: §5, p.8: proposed applications, not deployment evidence

## 19. Three claims to take away

**Run of show: your clock 12:50-14:30; talk clock 27:50-29:30.** Speaker B. Includes 0s video, 5s activity and 4s pauses/changeover.

First, language gives visual recognition a source of class structure beyond the image training labels.

Second, DeViSE learns to connect those representations through a ranking objective: the correct label should score above its competitors.

Third, the evaluation setting is essential to interpreting the result. In the two-hop example, changing only the candidates takes hit at five from eighteen point one to seven point nine percent. The semantic bridge is useful, but its success is conditional.

So the answer is yes: meaningful label representations can enable recognition of some visually unseen classes. Success still depends on the candidate vocabulary.

**Brief audience check:** What condition needs to accompany the claim that DeViSE recognizes unseen classes?

Thank you. We’re happy to take your questions.

Source: Frome et al. (2013), p.8

## 20. Sources, evidence and reproducibility

**Reference only - outside the timed talk.** Shared by both speakers; do not read it item by item.

[Reference slide — outside the timed talk. Do not read this slide aloud; use it during the separate Q&A.]

The original paper, official supplement, reading guide, and video assets are available in the downloads. Reported results are attributed to the paper; the interactive calculations are teaching examples. No original ImageNet training run is reproduced here.

**Reference prompt:** Which evidence comes from the paper, and which from the teaching examples?

Source: Frome et al. (2013), p.1

## Q&A preparation - backup, outside your 15 minutes

Start Q&A after both timed parts. These are suggested lead answers; the other speaker may add detail.

### 8. What exactly does 18.1% mean?

Flat hit@5 for DeViSE-0 on the 1,589-label 2-hop unseen candidate set. It is neither top-1 nor the full-21K result.

Source: Table 2, p.6

### 9. Is WordNet absent from the whole study?

No. Learned text embeddings do not require the curated hierarchy as their training target, but evaluation uses the ImageNet/WordNet hierarchy.

Source: §2; Supplement §A.3

### 10. Does DeViSE beat softmax on every metric?

No. Softmax is better at seen-class top-1 and at some hierarchical settings. Always specify metric and candidate set.

Source: Tables 1 and 3

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

