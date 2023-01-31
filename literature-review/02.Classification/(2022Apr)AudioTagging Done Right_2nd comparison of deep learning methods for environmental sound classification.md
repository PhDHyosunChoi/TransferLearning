citation key: liAudioTaggingDoneRight2022

## Summary & Tagging
- After its sweeping success in vision and language tasks, pure #attention-based neural architectures (e.g. DeiT) [1] are emerging to the top of audio tagging ( #AT) leaderboards [2].
- In this work, we perform extensive experiments on AudioSet [4] which is the largest weakly-labeled sound event dataset available, we also did analysis based on the data quality and efficiency. 
- We compare a few state-of-the-art baselines on the #AT task, and study the performance and efficiency of 2 major categories of neural architectures: **CNN variants and attention-based variants.** We also closely examine their optimization procedures.

## 1. Introduction
- Recently, after seeing tremendous success in language tasks[5], the ML community has been exploring a variety of methods for deploying attention-based architectures, e.g. #Vision-Transformers ( #ViT) [6]
- Recently, #AST (a kind of #Attention)[2] and #PSLA [7] improved the SOTA performance of the #AT task3 on the AudioSet benchmark by leveraging a suite of improvements including #DeiT[1] ( distilled ViT) architecture, ImageNet pretraining, data augmentations, and ensemble.
- Audio signals, 1D continuous by nature, require different processing than vision (2D) or language input sequences (discrete). #Environmental-sounds, compared to well-studied human speech, do not require language model, but are more diverse and span a wide range of frequencies. 
- Thus, the same techniques which worked well on speech are not guaranteed to work out of the box [8]. Plus, the lack of well-defined strongly-labeled data makes environment sounds recognition task not only more challenging but also understudied so far.
- CNNs [9, 10] and its variant CRNNs [11] have become the de-facto architecture for acoustic event recognition tasks, and have dominated the AudioTagging leaderboard until the rise of ViT [2]. The major difference between convolutional models and #attention-based networks (e.g. ViTs) are the locality inductive biases. In a nutshell, convolutional neural network sweeps through every consecutive pixel with its learned kernel, which is perfect for learning local features[3], but cannot see beyond its receptive field; whereas ViT networks skip through, attend in between the patches to build global correlations, and sometimes not even rely on the positional information.
- We train 4 variants of transformer networks including #CNN+ #Transformer, Vision Transformer ( #ViT), #Transformer, and #Conformer (a kind of #Attention )on the task of Audio Tagging, compare them with #ResNet, #CRNN control group.
- In between these 6 architectures, we perform analysis on the largest available dataset: Google AudioSet [4].
- Our experiments suggest that pretraining is not always necessary, LR scheduling & data augmentation are always helpful.
## 2. AT Background & Related Works

- **AudioSet** [4] contains 2,042,985 10-second YouTube video clips, summing up to 5,800 hours annotated with 527 types of sound events (weak label4).
- **AudioTagging Benchmark**
	Here, we do not include multi-modal or ensembled models, which would introduce tremendous extra variability, making fair comparison almost impossible.


Abbreviation:
	- #mAP: mean average precision