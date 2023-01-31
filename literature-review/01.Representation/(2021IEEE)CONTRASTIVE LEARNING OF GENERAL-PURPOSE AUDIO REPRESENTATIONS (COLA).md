citation key: saeedContrastiveLearningGeneralPurpose2021a
## Summary & Tagging

**COLA**
- Our approach is based on contrastive learning: it learns a representation which assigns high similarity to audio segments extracted from the same recording while assigning lower similarity to segments from different recordings. We build on top of recent advances in contrastive learning for computer vision and reinforcement learning to design a lightweight, easy-toimplement self-supervised model of audio.
- We show that despite its simplicity, our method significantly outperforms previous self-supervised systems.
## 1. Introduction
- Self-supervised pre-training has recently emerged as a successful technique to leverage unlabeled data to learn representations beneficial to supervised problems.
- Discriminative Pre-Training (DPT) is particularly effective. This approach learns a representation from pairs of similar inputs from unlabeled data, exploiting e.g. temporal consistency [5, 4, 6] or data augmentation [7] and trains a model to recognize similar elements among negative distractors. In contrast with generative encoder-decoder approaches [8, 9, 10, 11, 12], DPT is computationally efficient as it avoids input reconstruction entirely.
- Amidst DPT models for audio, [6] used a metric learning approach with a triplet loss to minimize the distance between embeddings of anchor and positive pairs and maximize it among the negatives. The instance generation is achieved through noise injection, shifting along time-frequency dimensions, and extracting samples in temporally close neighborhoods.
- Through utilizing a triplet loss as an unsupervised objective, a similar approach to learn audio representations (i.e. AUDIO2VEC) along with another “pretext” task of estimating temporal distance between audio segments.
- Despite recent progress, most work on learning representations of audio focuses on speech tasks [17, 18, 19] (with the exception of [6, 16]) and ignores other audio tasks such as acoustic scene detection or animal vocalizations.
- Moreover, triplet-based objectives heavily rely on the mining of negative samples, and the quality of learned features can vary significantly with the sample generation scheme.
- COLA (COntrastive Learning for Audio), a simple contrastive learning framework to learn general-purpose representations of sounds beyond speech. We build upon recent advances in contrastive learning [2] for computer vision (SIMCLR [7], MOCO [20]) and reinforcement learning (CURL [21]). We generate similar pairs by simply sampling segments from the same audio clip, which avoids exploring augmentation strategies entirely unlike SIMCLR, MOCO, CURL and others [22].
- triplet-based approaches [6,13]
- We demonstrate the effectiveness of COLA over challenging and diverse downstream tasks, including speech, music, acoustic scenes, and animal sounds.
- These experiments demonstrate that COLA offers a simple, easy-to-implement method to learn general-purpose audio representations without supervision.
## 4. Conclusions
- Linear Evaluation Protocol
- baseline for future work in self-supervised learning for audio.


