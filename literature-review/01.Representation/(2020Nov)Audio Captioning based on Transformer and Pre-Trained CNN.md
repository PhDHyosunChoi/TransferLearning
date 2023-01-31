citation key: chenAudioCaptioningBased2020b
## Summary & Tagging
- #Automated #audio #captioning is the task that generates text description of a piece of audio. This paper proposes a solution of automated audio captioning based on a combination of pre-trained CNN layers and a #sequence-to-sequence architecture based on #Transformer. The pre-trained CNN layers are adopted from a CNN based neural network for acoustic event tagging, which makes the latent variable resulted more efficient on generating captions. Transformer #decoder is used in the sequence-to-sequence architecture as a consequence of comparing the performance of the more classical LSTM layers.
- SPIDEr score
- label smoothing

## 1.Introduction
- Automated audio captioning is a #multimodal translation task where the model outputs a textual description given an audio signal. With growing attention [1–6], the 2020 edition of #DCASE (Detection and Classification of Acoustic Scenes and Events) data challenge has introduced a task of automated audio captioning. 
- The basic tasks of #automated #audio #captioning is acoustic event tagging and acoustic scenes identification. Besides, the automated audio captioning systems should also establish mappings between natural language and detected acoustic events.
- Similar to image captioning [7–11], audio captioning requires to extract feature representations of input space and map into natural language space. For audio captioning, effective audio feature extraction methods [2] can extract accurate audio features, which makes the generated description more relevant to the audio. As the data available in the audio captioning task is limited, direct training from scratch in an end-to-end manner may not enough to train an effective feature extractor. Thus, A method of pre-training feature extraction network is introduced in audio captioning models. Meanwhile, it is essential to describe the audio information with accurate and fluent text in audio captioning task, which needs to establish a effective mapping between language and acoustic features. In natural language processing, Transformer [12] is a excellent language modeling architecture proposed in recent years. For better mapping the relationship between language and audio features, Transformer is introduced to replace the traditional decoder with #LSTM layers in sequence-to-sequence architecture.
- In this paper, a sequence-to-sequence model1 is proposed to be trained using only caption annotation. The proposed model consists of a 10-layer CNN [13] encoder and a Transformer [12] decoder for feature extraction and natural language generation.
- First, we propose a CNN-Transformer model for audio captioning and achieves better results than the CNN-LSTM model [7]. Second, we design some selection rules to get the right words from the captions and set up a multi-label classification task to pre-train the CNN encoder. Third, we find that Label smoothing [14] and SpecAugment [15] can improve our model performance and avoid over-fitting effectively.
## 2. Related Works
- Drossos et al. [3] : One of the first approach to automated audio captioning, which used a GRU-based encoderdecoder architecture. 
- In [1, 6], the task of audio captioning in specific scenes was explored. 
- In DASE 2019, Ikawa et all. [5] introduced a conditional sequence-to-sequence model to control the information of the output sentences. 
- In [2], a model with top-down multi-scale encoder and aligned-semantic attention was proposed to address the problem of audio captioning for sound in the wild, and a large-scale dataset named AudioCaps was contributed. 
- Recently, the dataset Clotho [4] was released and adopted in DCASE 2020 audio captioning challenge.
## 3. Proposed Model
- The proposed model is a typical sequence-to-sequence system with the introduction of Transformer layers in the decoder part and more classical CNN layers in the encoder. 
- The CNN layers, which is known as pre-trained CNN layers, in the encoder of the system are adopted in a separate audio tagging system([Hyosun: the later part, decoder], which mapping acoustic features with acoustic events extracted from the caption text in the training dataset.
3.1. Encoder
- The CNN used here is for #feature #extraction of input #spectrogram.
3.2. Decoder
- The decoder used in the proposed model is a standard Transformer [12] consist of multi-head self-attention on text sequence and multi-head encoder-decoder attention on extracted feature sequence.
- The reason for choosing the Transformer model as the decoder is because of its state-of-the-art performance on natural language processing and the non-recurrence computing of its structure which helps prevent gradient vanishing or exploding.
3.3. Word prediction
- Cross-entropy loss: 
- Dec : Decoder
- N: the vocabulary size
- For prediction, the sof tmax function is used to turn the output into word probability. In the inference stage, the current prediction is related to the prediction results of the previous steps.
## 6. Conclusion
- This paper proposes a CNN-Transformer model with a pretraining stage introduced.
- The pre-training method improves the feature extraction and language modeling capability of the model and greatly improve the performance.
- Transformer has better language modeling ability than LSTM in this task. The experiments also verified the effectiveness of #SpecAugment and #Label-smoothing introduced in the proposed model.
