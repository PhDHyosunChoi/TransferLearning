citation key : niizumiBYOLAudioExploring2022
## Summary & Tagging
- we hypothesize that #representations #effective for general audio tasks should provide multiple aspects of robust #features of the input #sound.
- For serving the diverse needs of tasks such as recognition of emotions or music genres, representations should provide multiple aspects of information, such as local and #global-features.
- we propose a #self-supervised learning method: Bootstrap Your Own #Latent ( #BYOL) for Audio ( #BYOL-A, pronounced ”viola”).
- Whereas the #BYOL-A encoder combines local and global features and calculates their statistics to make the representation provide multi-aspect information. As a result, the learned representations should provide robust and multi-aspect information to serve various needs of diverse tasks.

## 1. Introduction 
- PRE-trained models play a vital role as #feature-extractors in various domains, e.g., #BERT [1] in the #natural-language-processing domain and #ImageNet #pre-trained models [2][4] in the #image-domain.
- In the audio domain: pre-trained models(e.g., VGGish [5]): 
		#heart-sound-classification [6], #Alzheimer’s disease #detection [7], #conservation monitoring [8], #audio #captioning [9], #audio #retrieval [10]
	- #Supervised-Learning[12]-[15]
	- #Unsupervised-Learning [16]-[21]
	- Target Tasks: 
		- sound event recognition ( #SER) [22]-[25]
		- non-semantic speech ( #NOSS): speech command recognition [26], speaker identification [27]
		- #music-tasks (e.g., music genre [28] and instrument [29] classification)
- Our goal is to explore a way to achieve a versatile audio representation that works effectively for various tasks as it is, off-the-shelf, without an extra effort such as #fine-tuning. The applicability of a model increases if it can be used as a frozen feature extractor because the effort for fine-tuning is not negligible, such as a careful learning rate tuning not to break pre-trained valuable features. Thus, if a representation is versatile enough as it is, it is an ultimate goal.
- while multiple information may serve conflicting needs, ignoring slight differences may serve the common needs.
- For serving different needs, multiple features available from different layers of a single model and statistics of these features potentially be helpful. The former study [30] showed that early layers, local features on CNNs, contain relatively ”general” filters, whereas deeper layers, global features, are specific to the pre-training. The studies [31]–[33] even utilized fusing the multilayer features.
- For serving common needs, we want a representation that ignores slight differences in sounds, and #self-supervised learning ( #SSL) frameworks for the image domain can be a good choice. These methods learn representations invariant to augmentations, and we can use audio data augmentations to make a difference in sounds.
- Typical choices are contrastive learning methods such as #SimCLR [36] or #MoCo [37], which learn representations through discriminating augmented positive pairs from augmented negative pairs in an input batch. However, we think Bootstrap Your Own Latent ( #BYOL) [11] can be a better choice because it learns representations invariant to changes created by augmentations, achieving what we seek directly.
- For encoding such representation, our network takes multilayer features and calculates statistics for accommodating multi-aspect information, which serves different needs of tasks.
- As a result, the learned representations should provide multi-aspect robust features of the input sounds and serve various needs of diverse tasks.
## 2. Related Work
### A. Relationship with our previoous work
- We introduced #BYOL-A in our previous work [38].
- In this paper, we redefined our hypothesis to explore pretrained general-purpose audio representations with a broader research scope.
- **Detailed Differences**: We reinterpret BYOL-A to learn representations invariant to the perturbations of sounds made by data augmentations rather than learn representations of specific sounds.
### B. Audio pre-training methods
- Supervised Learning Methods
	- #Self-supervised learning ( #SSL) methods using #masked prediction predominant in the #speech domain [39]-[41]
	- SSL methods using #contrastive-learning [19]-[21], [42]
	- #Cross-modal SSL mothods [16]-[18]
	- Many #supervised-learning models: pre-trained on large-scale datasets mainly for #SER ( #Sound-Event-Recognition) tasks.
		- VGGish[5] pre-trained on YouTube-8M [43] : used as a feature extractor in various application studies[8],[9],[10],[44],[45].
		- Pre-trained Audio Neural Networks (PANNs)[12] models: pre-trained on AudioSet[22] 
		- Pre-trained on both ImageNet and AudioSet show advantages: PSLA[13], ESResNe(X)t-fbsp[14], Audio Spectrogram Transformer(AST) [15] produced state-of-the-art results on #SER .
- Unsupervised Learning
	- For unsupervised learning, self-supervised learning (SSL) methods have been proposed including:
		- COLA[20] for general-purpose audio repreentations
		- Fonseca et al.[21] for SER
		- CLMR [42] for music tasks
		- speech representations, such as TRILL[19], PACE+ [46], Mockingjay [39], Wav2Vec 2.0[40], HuBERT[41]
		- non-speech recognition application studies such as [7] use Wav2Vec 2.0 as a #feature-extractor.
- Cross-modal/multi-modal pre-training methods
	- OpenL3 [17] : pre-trained by using audio-visual correspondence as training signal. 
	- COALA[16]: pre-trained, evalusated on SER and music tasks.
	- SLAM [47]: for speech tasks
- Concurrent works
	- BigSSL[48]
	- Data2vec [49]
	- the method by Wang et al [50]
	- SERAB [51] adopts BYOL-A [38] on speech emotion recognition tasks
	- WavLM[52]
## C. Benchmarks for pre-trained models
- SUPERB[53] : like the standard linear evaluation protocol [36], [54], SUPERB trains lightweight heads on top of the frozen pre-trained model. These tasks are limited to the speech domain; no establish benchmark exists for non-speech audio tasks. Therefore we build a benchmark for evaluating generalpurpose audio representations in this study.
- HARES [50] trains a linear layer head, the same as we do, 
- while HEAR [55] uses a shallow MLP downstream classifier. 
- SERAB [51] also evaluates frozen models in various speech emotion recognition tasks.
## D. Global pooling design choices
- Previous studies have taken various global pooling approaches: VGGish[5] , OpenL3[17], COALA [16] flatten frequency bins, time frames, and channels into a single embedding vector.
- COLA [20], TRILL [19], ESResNe(X)t-fbsp [14], and Fonseca et al. [21] use the global average or max pooling commonly used in image CNNs.
- Other approaches average frequency first and then summarize time. PANNs’ [12] CNN14 model first averages the frequency3. Then, it applies a temporal pooling operation
## E. Bootstrap Your Own Latent (BYOL)
- BYOL [11] is a self-supervised learning algorithm that learns image representations invariant to data augmentations.
- #contrastive-learning methods such as SimCLR [36] and MoCo [37] also learn representations invariant to data augmentations as BYOL does.
- #BYOL consists of two neural networks, referred to as online and target networks.
-  It has been empirically shown that the combination of adding the predictor to the online network and using the moving average of the online network parameters as the target network encourages encoding more and more information within the online projection and avoids collapsed solutions such as constant representations.

## 5. Conclusion
- It has been empirically shown that the combination of adding the predictor to the online network and using the moving average of the online network parameters as the target network encourages encoding more and more information within the online projection and avoids collapsed solutions such as constant representations.
- We found that a large portion of the performance comes from the inductive bias of the BYOLA encoder network architecture, and that the final critical portion resorts to the BYOL framework and BYOL-A audio data augmentations. As a whole, BYOL-A learns to produce effective representations that generalize to various tasks.