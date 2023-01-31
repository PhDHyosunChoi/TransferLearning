citation key: grollmischAnalyzingPotentialPreTrained2021a
## Summary & Tagging
- Recently, several models for audio classification have been pre-trained in a supervised or self-supervised fashion on large datasets to learn complex #feature #representations, so called #embeddings( #audio-embeddings).
- These embeddings can then be extracted from smaller datasets and used to train subsequent classifiers. 
- In the field of audio event detection (AED) for example, classifiers using these features have achieved high accuracy without the need of additional domain knowledge.
- The embeddings are systematically evaluated by analyzing the influence on classification accuracy of classifier architecture.
- To better understand the impact of the pre-training step, results are also compared with those acquired with models trained from scratch.
- On average, the #OpenL3 #embeddings performed best with a linear #SVM classifier.

## 1. Introduction (inc. Several Abbreviation)
- #MIR : Music Information Retrieval
- musicological analysis: a study of music genre
- annotations: a note by way of explanation or comment added to a tet or diagram
- #TL: #Transfer-Learning
	The main idea behind TL is to pre-train models on tasks where data is abundant, and re-use the knowledge gained during training for tasks where data is limited [3]. 
	- promising training strategy for a variety of research fields : Image Classification [4], Natural Language Processing [5], Environmental Sound Classification (ESC) [6]–[8], and several MIR tasks like genre classification [9] and instrument recognition [10]
- Learned feature representations: also called embeddings
## 2. Pre-Trained Embeddings for Audio
- Initial work on the use of embeddings for audio classification proposed using pre-trained image networks for classification [11], [12] due to the lack of large annotated audio datasets at the time.
- On all the evaluated tasks, the embeddings outperformed a baseline using Mel Frequency Cepstral Coefficients (MFCCs) as input representation. However, performance was still below the state-of-the-art (except for speech/music classification where nearly perfect classification was achieved with all methods).
- **VGGish embeddings**
	- initially proposed in [15] by training a modified VGG model using mel spectrograms as input. 
	- Google later published a trained model1 using a very weakly labeled dataset which was a preliminary version of the YouTube-8M dataset [16]. 
	- Besides having weak labels, the dataset had overlapping tags and events which, while visible in the video, were not necessarily audible. 
	- The problems with overlapping tags and very weak labels were addressed with the release of AudioSet [1] which contains 2 million audio clips with a duration of 10 seconds each. The sound clips were manually labeled, and an ontology of 527 tags of audible events was proposed. 
	- While the labels were correct for the full audio clip, it could still happen that the annotated sounds were not present in some time frames.
- **Kumar embeddings**
	- the authors trained a supervised convolutional neural network (CNN) with mel spectrograms as input on the AudioSet by pooling the embeddings over time for each file. This is referred to as early fusion.
	- A linear Support Vector Machine (SVM) classifier was trained on these embeddings achieving 83.5% accuracy with fine-tuning of the model, and 82.8% without on an ESC task (ESC50 dataset [17]). Global max pooling across time for each of the 1024 embedding dimensions performed better than average pooling. For this reason, global max pooling is used as the early fusion strategy in this work.
- L3Net 
	- an audio embedding model(L3Net) was proposed in [6]. A video with matching or nonmatching audio is fed into two separate CNN branches for video and audio feature extraction. The outputs of both networks are concatenated
	- Late fusion: by summing the class likelihoods over each file, and picking the highest for file-wise prediction. This approach is referred to as #late-fusion.
- **OpenL3 embeddings**
	- were proposed in [8] as an extension to L3-Net. 
	- Different models were trained on the AudioSet in the same self-supervised way as L3-Net to evaluate the impact on classification accuracy of different design choices such as embedding size (512 vs. 6144), input representation (linear magnitude spectrogram, mel spectrograms with 128 and 256 bins), and trained domain (music vs. environmental audio). 
	- The OpenL3 embedding models were compared to VGGish and SoundNet [18] embeddings for various ESC datasets, outperforming both. 
	- On the ESC50 dataset, 79.82% classification accuracy was achieved with a feedforward neural network classifier with two hidden layers (512 and 128 units, respectively), and Rectified Linear Unit (ReLU) activation. 
	- Results show that the domain of the training data does not necessarily need to correspond to the final task domain.

## 5. Conclusions
- From the evaluated embeddings, OpenL3 performed best over all tasks and was on par with the baseline using models trained from scratch. 
- This shows that self-supervised embeddings such as OpenL3 are a promising alternative to pre-training models on large annotated datasets for getting descriptive features. Lowering the amount of training examples changed the performance in favor of pre-trained embeddings. 
- Therefore, embeddings seem to be a good starting point for novel tasks with small datasets, and important for future research. 
- In general, linear SVMs trained on embeddings performed better than non-linear dense models, making them a feasible choice for real-world applications.
- This suggests that noise-like signal are not fully covered in the evaluated embeddings. 
- As future work, retraining one or several layers as well as combining the intermediate activations as reported in [9], [13], [18] can be a possible extension. 
- Furthermore, the impact of capturing embedding changes over time is another interesting direction.