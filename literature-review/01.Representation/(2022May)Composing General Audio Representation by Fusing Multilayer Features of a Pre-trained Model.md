citation key: niizumiComposingGeneralAudio2022
github: https://github.com/nttcslab/ composing-general-audio-repr
## Summary & Tagging
- Many application studies rely on audio DNN models pre-trained on a large-scale dataset as essential feature extractors
- We propose a simple approach to compose features effective for general-purpose applications, consisting of two steps: 
	- (1) calculating feature vectors along the time frame from middle/late layer outputs.
	- (2) fusing them. This approach improves the utility of frequency and channel information in downstream processes, and combines the effectiveness of middle and late layer features for different tasks.
- In the experiments using VGGish, PANNs’ CNN14, and AST on nine downstream tasks, we first show that each layer output of these models serves different tasks.

## 1. Introduction
- Pre-trained models are essential building blocks as feature extractors to transfer learned representations from large-scale datasets. In the audio domain, we can find many applications using pre-trained models: VGGish [1] pre-trained on YouTube-8M [2] are used in conservation monitoring [3], audio captioning [4], and speech emotion recognition [5]; and PANNs [6] pre-trained on AudioSet [7] are used in heart sound classification [8] and conservation monitoring [9].
- On the other hand, several self-supervised learning models proposed recently show well-balanced performance on general tasks [11] [12] [13]. These models learn general-purpose audio representations and are considered more suitable as feature extractors.
- In our preliminary experiments, the late layer features of supervised pre-trained models, used in the typical applications, performed better than self-supervised pre-trained models on sound event recognition (SER) tasks (e.g., ESC-50 [14], UrbanSound8K [15]), while they performed poorly on other tasks. Surprisingly, however, features from the middle layer performed differently, worse on SER tasks and better on other tasks. Our research question is: Can we put the strength of both features together for general purpose?
- Since the pre-training metric is largedataset classification accuracy, the late layers are considered specialized to the pre-trained dataset domain [10]. In addition, many of the models based on the image domain network [1] [16] are not designed to process time-frequency (TF) audio input effectively for audio downstream use.
- To address the aforementioned problems, we propose a simple approach to calculate general-purpose features by using the outputs from the middle and late layers of a supervised pre-trained model. In addition to the proposed approach for general-purpose feature calculation, our contributions include showing that the effective layers of the supervised pre-trained model are task-dependent and validating in experiments that the performance of these models can be significantly improved by using the proposed approach.
## 2. Related Work
**Feature computation of pre-trained models**
- **VGGish**[1] and **OpenL3**[17] : flatten all axes (frequency, time, and channel) of the convolutional layer output into a single embedding vector. 
- **COLA** [11] and **TRILL** [18] : apply global averaging or max pooling and summarize frequency and time frame axes.
- The problems of these: 
	- The pitch of the voice is considered necessary for the speaker recognition task; thus, frequency-wise information is essential. While voice inflection is vital for speech emotion recognition; thus time-wise information is needed.
	- While flattening preserves all the information, it is difficult to calculate feature statistics (e.g., averaging frequency bins temporally) from flattened vectors. On the other hand, global pooling makes information per frequency or time frame unavailable in the later processes. Both of these issues could impair the utility of the feature vectors in downstream tasks.
**General-purpose audio representations**
- Self-supervised learning models such as COLA [11], BYOL-A [12], and Slowfast NFNets [13] have been proposed for general-purpose or universal audio representations pre-trained on AudioSet without labels.
**Multilevel feature fusion**
- [20] uses the size transformation function to match the feature size of each layer to combine multilayer features. In the audio domain, AudioCaps [21] evaluates various audio features, including combinations of multi-layer outputs for the audio captioning task, but not for other tasks.
## 3. Proposed Approach
- calculating feature vectors along the time frame from layer outputs and fusing middle and late layer feature vectors.
- adjust the number of time frames to a To using maxpool and then flatten the channel and frequency along time. Adjusting the time frame of any layer feature to a To enables subsequent fusion, whereas flattening transforms the channel and frequency into vectors without the information loss that could be caused by averaging or max operations found in conventional methods
## 5. Conclusion
- The proposed approach first calculates feature vectors aligned with the time frame to improve the utility of frequency and channel information in downstream processes.
- In the experiments using VGGish, PANNs’ CNN14, and AST on nine downstream tasks, we showed that each layer output from these models serves different tasks, and showed that the proposed approach significantly improves performance and brings it to a level comparable to that of SOTA models.
- the NOSS tasks
- Our proposed approach provides a simple way to exploit existing supervised pre-trained models as general-purpose audio representations.