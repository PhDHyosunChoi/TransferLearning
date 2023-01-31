citation key: tsaleraComparisonPreTrainedCNNs2021
## Summary & Tagging
- CNNs were initially designed for image classification and recognition, and, at a second phase, they extended towards sound classification.
- We selected three ‘Image’- and two ‘Sound’-trained CNNs, namely, #GoogLeNet, #SqueezeNet, #ShuffleNet, #VGGish, and #YAMNet, and applied #transfer-learning.
- The processing time needed in terms of sound preprocessing for the preparation of the #scalograms and #spectrograms as well as CNN training. The #UrbanSound8K, #ESC-10, and #Air-Compressor open sound datasets were employed. Using a two-fold criterion based on classification accuracy and time needed.

## 1. Introduction
- Sound is a complex, feature-rich signal, and sound classification has attracted research interest using a rich portfolio of Machine Learning (ML) methodologies and mechanisms.
- Deep learning techniques, and especially CNNs, have achieved significant results in recognition and classification tasks, especially related to image recognition. The application field has been extended to the sound, after transforming the raw sound features and converting the resulting representations (such as the spectrograms and scalograms) into figures.
- Transfer learning techniques are employed, retraining CNNs that have been trained in a specific area so that they can operate in other datasets.
- Contributions: only pointed out (2) and (3) as they looked important :)
	- (2) We successfully used the mechanisms for sound representation and feature extraction so that sound descriptions are fed into the retrained CNNs. 
	- (3) We evaluated the transfer learning upon the selected CNNs, in terms of classification accuracy and resources needed for learning, using three publicly available sound datasets (UrbanSound8K, ESC-10, and Air Compressor).
-  Image-based sound representations (spectrograms and scalograms) were applied in single and sequential representations, and the impact of these differentiations was evaluated. The paper also unveils some of the different parameterization possibilities of the transfer learning process and investigates the impact they have upon classification accuracy, considering specific values. The ‘interoperability’ among algorithms and input formats (namely, spectrograms and scalograms) was verified.
- The late fusion algorithms based on the results retrieved from different CNNs enhanced classification accuracy.

## 2. Sound Classification, CNNs, and Transfer Learning
2.1. Sound Classification
-  Sound recognition is a technically challenging problem due to the complexity and dynamic nature of the signal; but, due to the potential to propel a wide range of applications, sound research is receiving increased interest.
- Outdoor sounds: 
	- environmental [1]
	- urban contexts [2–4]
- Indoor sounds:
	- business
	- residential
	- educational [5,6]
- Human-generated sounds
	- automatic speech recognition ( #ASR)
	- speaker identification ( #SID) [7]
	- music information retrieval ( #MIR) [8]
- Research on noise reduction: using blind source separation (BSS) techniques [9]
- Sound preprocessing includes signal framing. Selecting the frame length is a challenging problem, to both adequately capture the sound of interest and without including other sound types. 
- Sound recognition has been boosted through the availability of sound datasets. Such datasets consist of labeled sound excerpts (typically as discrete files).
- UrbanSound8K [10], ESC-10 [11], Air Compressor [12], and TUT [13] public datasets are often used for the evaluation of classification algorithms.
- A systematic effort, named after #AudioSet #Ontology, to provide a hierarchical collection of sound types (labels), covering a wide range of everyday sounds (632 audio classes). -> Such efforts open the pool of YouTube videos (and audios) with the creation of the YouTube-100M, YouTube-8M (https://research.google.com/youtube8 m/index.html, accessed on 24 June 2021) [14], and AudioSet [15].
- In classic ML techniques, sound features are extracted and used in the algorithms. Features are based on psychoacoustic properties of sounds such as loudness, pitch and timbre, while cepstral features are also widely used, including Mel-Frequency Cepstral Coefficients (MFCC) and their derivatives [16,17]. Feature evaluation methodologies are employed such as Relief-F [18] and Principal Component Analysis (PCA) based [19]. Recently, deep learning techniques were employed [20–23].
- in the former, a pool of values from the time, frequency, and perceptual domains are extracted and fed into the ML algorithms, while, in deep learning, the CNNs are responsible to form their representation in a more opaque way. 
2.2 CNNs
- [2012] AlexNet: in the Imagenet Challenge of 2012
- [2014] VGG family of neural networks: VGG-16, VGG-19
- [2014] GoogleNet (Inception-v1): The best performance in ImageNet Challenge
- [2015] Inception-v2, Inception-v3, ResNet-18
- [2016] SqueezeNet, Xception, Inception-v4(Inception-ResNet-v2), DenseNet, DarkNet19
	- SqueezeNet: the fire moduls squeezes the dimention of the feature map and concatenates the feature maps which is a techniques similar to the inception module[30]. 
	- Xception: the Extreme Inception convolutional neural network
	- Inception-v4)27 layers deep) and the hybrid model, Inception-ResNet-v2(164 layers deep)
	- DenseNet: Dense Concolutional Network [33] 
	- DarkNet19
- [2017] MobileNet(MobileNet-v1), ShuffleNet
- [2018] MobileNet-v2, ShuffleNet-v2, MobileNet-v3, EfficientNets
	- MobileNet-v2: inverted residual structure and shortcut connections between linear bottlenecks [37]
	- ShuffleNet-v2: the float-point operations (FLPOs)[38] 
	- MobileNet-v3: network architectures search (NAS) and NetAdapt algorithm 
	- EfficientNets
- [2020] Sound CNNs(in contrast with Image CNNs), CRNN (a combination of CNN and Recurrent Neural Networks)
	- Sound CNNs (vs. ImageNet)
		- VGGish
		- YAMNet
		- In 2020, the performance of CNNs in image classification inspired the idea of creating new or adapting existing Deep Neural Network architectures to classify audio signals, characterized as ‘Sound’ CNNs (in contrast with the CNN architecture focused on image, to which we refer hereupon as ‘Image’ CNN). VGGish and YAMNet are two characteristics CNNs, with the former being a 24-layer-deep network, based on the VGG, and the latter (YAMNet) being a 28-layer-deep network employing MobileNet-v1 architecture. Training and inference of Sound CNNs are employing sound datasets, after appropriate transformation of the sound signal into an image or set of images.
	- CRNN 
		 In [41], a combination of CNN and Recurrent Neural Networks (CRNN) was proposed for sound event detection (SED). The performance of classification is related to the amount of the annotated data and the imbalance among the classes’ data. This problem is addressed with cost-sensitive settings [42] or using the transfer learning method.
2.3. Tranfer Learning
- Definition: Transfer learning applies knowledge gained from one origin (source) domain to another destination (target) domain to leverage the modeling trained in the origin domain and/or compensate the limited or inadequate data in the destination (target) domain.
- The PASCAL VOC dataset
- To employ transfer learning in sound classification, image-based sound representations are used as the common denominator between the trained networks and the raw data (sounds). Specifically, sound excerpts (after appropriate segmentation) are transformed into images, as spectrograms and scalograms, as a ‘preprocessing’ step. CNNs typically consist of (1) the convolutional and pooling part, responsible for extracting the features, and (2) the classification layer(s) connected with the first part. Considering such functional disengagement, an open question is related to which parts of the trained models will be reused as they are and which will be re-trained according to the destination dataset [45]. There is a wide range of choices.
## 3. Methodology
3.2. Sound Pre-processing
- Sounds, even belonging to the same dataset, may have different characteristics related to the raw signal; these include the sampling frequency, the number of channels, and the duration of the excerpts. These can affect subsequent processing; for example, a stereo signal may provide the double number of time-frequency representations. The sounds are ‘homogenized’ in terms of sampling frequency and the number of channels. Specifically, the same sampling frequency, typically belonging to the lower range of values (e.g., 16 kHz), is applied to all sound excerpts. Stereo (and multi-channel) sound signals are converted to monophonic. The dataset is split into train, validation, and test sets, corresponding to 60%, 20%, and 20% of the files, respectively. 
- The raw signal is transformed into image-based representations. The audio signal is partitioned into 25-ms-long, overlapping, periodic Hanning windows with a hop-length of 10 ms. Short-Time Fourier Transform is computed and the magnitude of the spectral values are passed through 64-band mel frequency filter banks, spanning the range of 125–7500 Hz. The scalograms are produced as the absolute value of the Continuous Wavelet Transform (CWT) coefficients of the sound signal.
- Regarding the transformation into figures, there are two options. (1) The whole sound excerpt is converted into a single image and it is fed into the CNN algorithm for classification and one single decision is inferred. (2) The sound signal is split into segments (of 0.96 ms) and each of these excerpts is transformed into an image. Each segment corresponds to 96 parts at a 10-ms sound excerpt, resulting in a duration of 96 ∗ 10 = 960 ms = 0.96 s. Considering the overlap percentage (at 50%), the hop is calculated at 0.96/2 = 0.48 ms. The audio is described by a 96 × 64 × 1 × K array, where K is the number of spectrograms that depends on the audio’s length and the overlap percentage between consecutive mel spectrograms. The number of spectrograms (K) considered in a sound excerpt can be approached through the following formula:
- Equation : # of spectrograms(=K) = ![[(2021DEC)Comparison of Pre-Trained CNNs for Audio Classification Using Transfer Learning_equation(1).png]]
- where FL is the full length of the sound excerpt, SL is the length of the segment, and OL is the overlapping ratio (which we assume has a positive value). For the three Image CNNs, GoogleNet, SqueezeNet, and ShuffleNet, the scalograms underwent the data augmentation technique for two reasons: (1) to obtain the required image dimensions of the respective network and (2) to avoid overfitting through image transformations, such as reflection, translation, and stretch.
- a classification decision is made for each image (in the case of a single, per sound excerpt) or for each segment (in the case of segmentation). In the latter, the decision for the excerpt is based on fusing the decisions of the individual segments.
## 5. Discussion
- CNN application is extended from image-oriented research (including clustering classification and recognition) to sound research. The common denominator is the conversion of the sound signal into an image so that it is processed by the CNN.
- While the number of layers initially followed an increasing tendency (leveraging the availability of increasing processing and memory resources), more effective designs have been brought forward. 
- Two aspects can be considered in the usage of the CNNs:
	- (1) The relatively low ‘explainability’ of the sound transformation and representations within the CNN, in comparison with the classical ML methods where specific features are extracted, with their contributions being evaluated separately. This aspect is countervailed by the typically higher performance, in terms of classification accuracy, of the CNN architectures. 
	- (2) The resource-consuming nature of the CNN training, when performed from scratch. The learning transfer paradigm is paving the way for even more effective, resource-friendly usage and ubiquitous deployment of CNNs.
- Regarding the transformation of the sound signal into an image, different timefrequency transformations have been employed, namely scalograms (for SqueezeNet, GoogleNet, and ShuffleNet) and spectrograms (VGGish and YAMNet).
- each sound excerpt can be transformed into a single image as in the case of Image CNNs or multiple images (corresponding to sound segments) as in the case of Sound CNNs. The latter allows for a more fine-grained classification evaluation while the homogeneity of the classification results (per segment) can be translated as the confidence level for the classification of the overall sound excerpt.

 ## 6. Conclusions and Future Work
 - Sound classification is an ongoing problem and multiple techniques have been employed in this context, including classical methods based on explicit feature extraction and deep learning techniques (including CNNs). The latter (CNNs) offers better performance requiring increased (computational) resources, as verified with three datasets of different characteristics, in terms of classes and length.
 - The transfer learning paradigm was applied successfully, while it was observed that the re-training configurations can have a severe impact upon the classification accuracy and the computational resources required.
 - The results of the tests performed, using the three datasets, indicate that Sound CNNs achieve better performance (as defined by the weighted combination of classification accuracy and training time) in comparison with Image CNNs. VGGish achieves the highest accuracy, with YAMNet following.
 - In terms of sound representation, equivalent image-based transforms (e.g., scalograms and spectrograms), in the case of already existing constraints and/or preferences, were verified to lead to similar results. Fusion scenarios can also have positive results. 
 - Fusion Scenarios: Fusion can take place with a single classifier, through sound segmentation, independent classifications per segment, or fusion of the results, as pursued with the sound CNNs. Fusion can also take place if multiple classifiers are available, as a majority-based classification.
 - The late fusion scenarios: mixed with alll 5 networks
 - Regarding the three datasets we used, the Air Compressor had the best behavior as it gave the highest classification accuracy for all CNNs. This dataset had a smaller number of classes as well as limited number of audio files.
 