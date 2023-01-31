citation key: koikeAudioAudioBetter2020

## Summary & Taggging
- #heart #sound #classification
- It is known that transfer learning methods can help extract higher representations automatically from the heart sounds without any human domain knowledge. However, most existing studies are based on models pre-trained on images, which may not fully represent the characteristics inherited from audio.
- we propose a novel transfer learning model pre-trained on large scale audio data for a heart sound classification task.
- #PhysioNet #CinC Challenge Dataset
## 1. Introduction
- The components of a heart sound include the first (S1) and the second sound (S2) as normal sounds, while the third and the fourth heart sounds, i. e., S3 and S4, often correspond to murmurs, and ejection clicks, usually refer to some disease, or anomaly [3].
- In recent feature extraction approaches, wavelet analysis, time-frequency analysis using short time fourlier transform (STFT), unsupervised learning and other methods are often found [4]. 
- As a classifier, hidden Markov model ( #HMM), #k-nearest neighbour, support vector machines, random forest, #multi-layer perceptron, deep neural network, convolutional neural network, recurrent neural network, and other #classifiers have been used in previous research [4].
- Motivated by the success of transfer learning (TL) in computer vision [5], natural language processing [6], and speech recognition [7], TL-based methods are now proving another paradigm for extracting higher representations from heart sound without any human expert domain knowledge [8].
- most existing #TL-based models are pre-trained on images, such as ImageNet [9] rather than on audio data. To explore the TL capacity of a most recently released deep model pre-trained on large scale audio data, such as the Large-Scale #Pretrained Audio Neural Networks (PANNs) for audio pattern recognition [10], we introduce PANNs for the heart sound classification task. Our hypothesis is that the deep model pre-trained on audio may catch more inherited characteristics from heart sounds than models pre-trained on images.
- The main contribution of this work: 
	- First, we introduce a novel deep learning model pre-trained on large scale audio data into the paradigm of TL for heart sound classification. it is the first time an audio based pre-trained TL model is used for heart sound classification. 
	- Second, we investigate and compare the proposed models with other state-of-the-art TL models on their capacity to extract higher representations from heart sound. Third, we compare two popular inputs, the spectrogram and the Log Mel spectrogram, for their performance on the interpretation of the heart status.
## 2. Materials and Methods
A. Dataset
	the open-access heart sound database, PhysioNet CinC Challenge database [11]
B. Transfer Learning from Images
- On this background, TL is commonly used with CNNs pre-trained on large datasets like ImageNet.
- several available pre-trained models for image tasks:
	- VGG [12], MobileNet [13], ResNet [14], and ResNeXt [15]. In the ImageNet 2014 challenge, VGG at that time with 16 ˜ 19 convolutional layers.
	- Residual blocks are composed of two pathways: via the convolutional layer, and via direct input as a shortcut. The shortcut path takes no extra parameters and matrix calculation, making backpropagation easier at the same time.
	- ResNets, MobileNet-v1(Depthwise convolution and poinwise convolution by 1x1 filters [13])
	- Inverted residual blocks(=bottleneck layers) added in MobileNet-v2
	- ResNet
	- ResNeXt[15] : weakly-supervised fashion with ImageNet1K synsets, followed by fine-tuning on ImageNet1K dataset.
C. Transfer Learning from Audio: PANNs
- To provide a generalised model in the audio pattern recognition field, large-scale pre-trained audio neural networks (PANNs) were proposed [10].
- binary cross-entory(= #log-loss)
![[(2020IEEE)Audio for Audio is Better? An Investigation on Transfer Learning Models for Heart Sound Classification_equation(1).png]]

(Figure1)![[(2020IEEE)Audio for Audio is Better? An Investigation on Transfer Learning Models for Heart Sound Classification_figure(1).png]]


## 4. Discussion
- The proposed #PANNs-based model could extract the most efficient higher representations in recognising heart sounds (see Table II).
- MobileNet-based model
- ResNeXt-50, ResNeXt101, and ResNeXt-101+WSL,
- This suggests that, deep models pre-trained by audio (e. g., PANNs) may extract more useful characteristics inherited in audio data than models pre-trained on images for the heart sound classification task. Further, **Log Mel spectrograms** outperformed the ‘normal’ spectrograms. This result is consistent with the observation that human hearing is sensitive to sounds in the mel scale frequency [21].
## 5. Conclusion
- In this study, we proposed a novel transfer learning model for heart sound classification pre-trained on large scale audio data for heart sound classification.
- We can conclude that deep learning models pre-trained on audio may help more in extracting higher representations from heart sounds than the models pre-trained on images.